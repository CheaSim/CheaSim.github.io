# ALBERT 更小但是更慢？

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2020/11/18/albert-%E6%9B%B4%E5%B0%8F%E4%BD%86%E6%98%AF%E6%9B%B4%E6%85%A2/
发布日期：2020-11-18
更新日期：2020-11-18





# ALBERT 更小但是更慢？

最近由于参加阅读理解比赛，所以大量测试各种模型，惊奇地发现原本现在阅读理解比赛中SOTA的模型居然是不起眼并且以小模型闻名的ALBERT。这让我对这个“小”模型产生了好奇。从而写一下这份的论文笔记。

## 摘要

模型越大下游效果越强是众所周知的道理，但是由于硬件设备和显存所限，所以模型不能无限制得放大。这篇文章提出了一个全面领先BERT模型的ALBERT，在比BERT-LARGE参数小的情况下超过了它。

## 有何区别

### 1. embedding 参数减少

在从one-hot embedding到hidden size embedding有一个$V \times H$的全连接层，这里使用了一个trick，加了一个hidden layer，从而使得全连接层变成了$V\times E + E\times H$。这样子我们就可以用一个很大的$H$了，比如在xxlarge上就是$H=4096$。

### 2.层间参数共享

很简单，就是原来模型类似于$F(x) = f_n(f_{n-1}(…f_1(x)))$，但是现在变成了$F(x)=f(f(…f(x)))$。我也在想，虽然$f(x)$是一个非线性的，但这种形式是不是可以有函数去拟合$F(x)$，毕竟重复$f(x)$这不能优化吗？ 去压缩ALBERT模型的大小。

### 3. SOP

提出了一个新的self supervised learning 的 objective，既SOP(sentence ordering objectives)。类似于BERT预测两个句子是否是连续的，ALBERT需要预测打乱句子的顺序。

并在在对比中，SOP对于RACE也就是阅读理解任务提高了2.3个点，很哇塞

## 实验

实验部分具体暂且不表。我理解的有几点

- 额外的领域内预训练是有益的，但是领域外可能会有害

- dropout在模型不会over-fit的情况下其实可以忽略，在batch normalization和dropout可能会损害模型的性能。

- hidden size 4096 有可能是ALBERT 性能强的主要原因。

- 虽然层间参数共享，理论上可以无限深，但是实验发现24层并没有12层效果好。特别宽也没有特别好，这都是玄学调参，很难人工判断。

- 按理来说fffff(x) 可能会导致每层之间的输出过于相似，但在这里实验发现，并没有。难道是embed layer就很强了？ 猜测

## 改进点

- 稀疏矩阵优化，attention 魔改

- SOP是否可以泛用。

## 模型解读

### 主类

forward先经过embeddings层再经过encoder层。这里注意，默认输入是用了最后一个隐层所有token的输出再经过一个线性+tanh的操作。

```python
class
config_class = AlbertConfig
load_tf_weights = load_tf_weights_in_albert
base_model_prefix = "albert"
def
super

self.config = config
self.embeddings = AlbertEmbeddings(config)
self.encoder = AlbertTransformer(config)
if
self.pooler = nn.Linear(config.hidden_size, config.hidden_size)
self.pooler_activation = nn.Tanh()
else
self.pooler = None
self.pooler_activation = None

self.init_weights()

def
return

def
self.embeddings.word_embeddings = value

def
old_embeddings = self.embeddings.word_embeddings
new_embeddings = self._get_resized_embeddings(old_embeddings, new_num_tokens)
self.embeddings.word_embeddings = new_embeddings
return

def
"""Prunes heads of the model.
heads_to_prune: dict of {layer_num: list of heads to prune in this layer}
ALBERT has a different architecture in that its layers are shared across groups, which then has inner groups.
If an ALBERT model has 12 hidden layers and 2 hidden groups, with two inner groups, there
is a total of 4 different layers.

These layers are flattened: the indices [0,1] correspond to the two inner groups of the first hidden layer,
while [2,3] correspond to the two inner groups of the second hidden layer.

Any layer with in index other than [0,1,2,3] will result in an error.
See base class PreTrainedModel for more information about head pruning
"""
for
group_idx = int
inner_group_idx = int
self.encoder.albert_layer_groups[group_idx].albert_layers[inner_group_idx].attention.prune_heads(heads)

@add_start_docstrings_to_callable(ALBERT_INPUTS_DOCSTRING.format("batch_size, sequence_length"))
@add_code_sample_docstrings(
tokenizer_class=_TOKENIZER_FOR_DOC,
checkpoint="albert-base-v2"
output_type=BaseModelOutputWithPooling,
config_class=_CONFIG_FOR_DOC,
)
def
self,
input_ids=None
attention_mask=None
token_type_ids=None
position_ids=None
head_mask=None
inputs_embeds=None
output_attentions=None
output_hidden_states=None
return_dict=None

output_attentions = output_attentions if
output_hidden_states = (
output_hidden_states if
)
return_dict = return_dict if

if
raise
elif
input_shape = input_ids.size()
elif
input_shape = inputs_embeds.size()[:-1
else
raise

device = input_ids.device if

if
attention_mask = torch.ones(input_shape, device=device)
if
token_type_ids = torch.zeros(input_shape, dtype=torch.long, device=device)

extended_attention_mask = attention_mask.unsqueeze(1
extended_attention_mask = extended_attention_mask.to(dtype=self.dtype)  # fp16 compatibility
extended_attention_mask = (1.0
head_mask = self.get_head_mask(head_mask, self.config.num_hidden_layers)

embedding_output = self.embeddings(
input_ids, position_ids=position_ids, token_type_ids=token_type_ids, inputs_embeds=inputs_embeds
)
encoder_outputs = self.encoder(
embedding_output,
extended_attention_mask,
head_mask=head_mask,
output_attentions=output_attentions,
output_hidden_states=output_hidden_states,
return_dict=return_dict,
)

sequence_output = encoder_outputs[0

pooled_output = self.pooler_activation(self.pooler(sequence_output[:, 0

if
return

return
last_hidden_state=sequence_output,
pooler_output=pooled_output,
hidden_states=encoder_outputs.hidden_states,
attentions=encoder_outputs.attentions,
)

```

ALBERT 更小但是更慢？

https://www.cheasim.com/%E8%AE%BA%E8%A7%A3/2020/11/18/ALBERT-%E6%9B%B4%E5%B0%8F%E4%BD%86%E6%98%AF%E6%9B%B4%E6%85%A2%EF%BC%9F.html

作者
CheaSim

发布于
2020-11-18

更新于
2020-12-04

许可协议

#[nlp](https://www.cheasim.com/tags/nlp/)[AI](https://www.cheasim.com/tags/AI/)




