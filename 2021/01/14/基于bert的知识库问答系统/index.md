# 基于BERT的知识库问答系统

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2021/01/14/%E5%9F%BA%E4%BA%8Ebert%E7%9A%84%E7%9F%A5%E8%AF%86%E5%BA%93%E9%97%AE%E7%AD%94%E7%B3%BB%E7%BB%9F/
发布日期：2021-01-14
更新日期：2021-01-14

把知识库问答拆成实体识别与属性映射，记录 BERT、CRF 与领域问答的实现思路。




# 毕设复习

由于是基于知识图谱的领域内问答系统，所以分为两个步骤，不是end2end。

- 命名实体识别

- 属性映射步骤

实体识别是为了找到问题中的实体，属性映射是为了找到实体对应在知识库中的属性。输出的结果是一个规则构成的“「实体」的「属性」是「尾实体」”

命名实体识别是通过BERT+CRF。

属性映射分为两步

- 通过规则，在知识库中找到实体的所有属性，之后和原句匹配，匹配成功作为属性输出

- 匹配不成果，将所有属性以“「问题」「属性」”计算分数，取匹配分数最高的作为答案输出。

1.15 搞定 实体属性对齐方面知识点。 之后再搞定面试RNN + 面试5道题 + leetcode10道题。 链表 字符串着重。

#### TODO

- 实体链接没有实现，只是匹配+数据库查询。

## 数据预处理

由于数据本身是一个问答数据，所以我们需要先对数据进行处理，生成三元组对。大概有600w个实体，训练的一个1poch需要5小时。问题数量25000。

```text
	《机械设计基础》这本书的作者是谁？
	机械设计基础 ||| 作者 ||| 杨可桢，程光蕴，李仲生
	杨可桢，程光蕴，李仲生
==================================================
	《高等数学》是哪个出版社出版的？
	高等数学 ||| 出版社 ||| 武汉大学出版社
	武汉大学出版社
==================================================
	《线性代数》这本书的出版时间是什么？
	线性代数 ||| 出版时间 ||| 2013-12-30
	2013-12-30
==================================================
```

我们通过问题

## BERT

代码来自transformers==3.3.1

### input

BERT模型的输入由三部分得到，token embdding, segment embedding, position embedding。

#### token embedding

对于所有文字来说，计算机都是无法理解的，需要转化为浮点向量或者整型向量。BERT采用的是WordPiece tokenization，是一种数据驱动的分词算法，他以char作为最小的粒度，不断地寻找出现最多以char为单位组成的token，之后将word进行分词，分为一个一个的token。比如ing这个会经常出现在英文当中，所以WordPiece 会吧”I am playing the computer games”分为”I am play ##ing the computer games”。为了解决OOV问题。词表中有30522个词。

在WordPiece 分词的基础上，之后会加入4个特殊词汇[CLS],[SEP],[PAD],[UNK]。[CLS]加入到句首，不参与预训练，针对下游任务进行fine-tune。[SEP]作为句尾以及分段标志。[PAD]是填充，使得句子长度一样，方便批处理，[UNK]是表明不在词表当中。将他们转换成one-hot embedding之后，接一个embedding层，将词转化为最初的词向量。

#### segment embedding

segment embedding 仅仅作为区分两个句子来使用。在预训练中，还要使用预测句子是否相邻作为预训练任务之一。在输入时，也会经过一个线性层来形成segment embedding.

#### position embedding

position embedding 纯使用nn.embedding 获得。训练了一个位置词表。$W\in \mathbb{R^{512 \times 768}}$。输入就是[0,1,2,…,len_seq-1]

```python
class
"""Construct the embeddings from word, position and token_type embeddings."""
def
super
self.word_embeddings = nn.Embedding(config.vocab_size, config.hidden_size, padding_idx=config.pad_token_id)
self.position_embeddings = nn.Embedding(config.max_position_embeddings, config.hidden_size)
self.token_type_embeddings = nn.Embedding(config.type_vocab_size, config.hidden_size)

# self.LayerNorm is not snake-cased to stick with TensorFlow model variable name and be able to load
# any TensorFlow checkpoint file
self.LayerNorm = nn.LayerNorm(config.hidden_size, eps=config.layer_norm_eps)
self.dropout = nn.Dropout(config.hidden_dropout_prob)

# position_ids (1, len position emb) is contiguous in memory and exported when serialized
self.register_buffer("position_ids"

def
if
input_shape = input_ids.size()
else
input_shape = inputs_embeds.size()[:-1

seq_length = input_shape[1

if
position_ids = self.position_ids[:, :seq_length]

if
token_type_ids = torch.zeros(input_shape, dtype=torch.long, device=self.position_ids.device)

if
inputs_embeds = self.word_embeddings(input_ids)
position_embeddings = self.position_embeddings(position_ids)
token_type_embeddings = self.token_type_embeddings(token_type_ids)

embeddings = inputs_embeds + position_embeddings + token_type_embeddings
embeddings = self.LayerNorm(embeddings)
embeddings = self.dropout(embeddings)
return
```

### transformer encoder 层

transformer encoder层主要如下图所示

使用一个上面所说的输入，经过Multi-Head Attention，在通过残差连接以及Layer Normalization，之后通过FFN以及又一个残差连接作为输出。

### Multi-Head Attention

BERT使用的是自注意力机制，即用于$Q,K,V$全部源自同一个向量。注意力机制使用了上下文的信息来对每一个token进行表示。计算机通过利用上下文的信息，对每一个token进行理解。比如“冬天到了，天气变冷了。”BERT会根据大量该类的文本，将冬天和冷的语义进行融合。Attention值的计算公式如下

$$Attention(Q,K,V)=softmax(\cfrac{QK^T}{\sqrt{d_k}})V \in \mathbb{R^{len\times d}}$$

其中，$Q,K,V\in \mathbb{R^{d\times k}},Q=xW_q,K=xW_k,V=xW_v$，$d$是隐层维度这里可以注意到，因为softmax是非线性的，所以这里的矩阵变换是没法单纯使用线性变换用$Wx$代替的。

多头在哪里多头。直接将原来的$x$进行转化后切分，详情看下图就懂了。每一个attention生成的维度都不高，拼起来就跟原来一样了。这张图有点问题，其实BERT没有$W^O$，因为$Z_0,…,Z_7$拼起来正好是$Z$。

> BERT 实现中，多头的目的是降低参数的个数，增加表达能力。 类似于CNN多个卷积核？

```python
class
def
super
if
raise
"The hidden size (%d) is not a multiple of the number of attention "
"heads (%d)"
)

self.num_attention_heads = config.num_attention_heads
self.attention_head_size = int
self.all_head_size = self.num_attention_heads * self.attention_head_size

self.query = nn.Linear(config.hidden_size, self.all_head_size)
self.key = nn.Linear(config.hidden_size, self.all_head_size)
self.value = nn.Linear(config.hidden_size, self.all_head_size)

self.dropout = nn.Dropout(config.attention_probs_dropout_prob)

def
new_x_shape = x.size()[:-1
x = x.view(*new_x_shape)
return

def
self,
hidden_states,
attention_mask=None
head_mask=None
encoder_hidden_states=None
encoder_attention_mask=None
output_attentions=False

mixed_query_layer = self.query(hidden_states)

# If this is instantiated as a cross-attention module, the keys
# and values come from an encoder; the attention mask needs to be
# such that the encoder's padding tokens are not attended to.
if
mixed_key_layer = self.key(encoder_hidden_states)
mixed_value_layer = self.value(encoder_hidden_states)
attention_mask = encoder_attention_mask
else
mixed_key_layer = self.key(hidden_states)
mixed_value_layer = self.value(hidden_states)

query_layer = self.transpose_for_scores(mixed_query_layer)
key_layer = self.transpose_for_scores(mixed_key_layer)
value_layer = self.transpose_for_scores(mixed_value_layer)

# Take the dot product between "query" and "key" to get the raw attention scores.
attention_scores = torch.matmul(query_layer, key_layer.transpose(-1
attention_scores = attention_scores / math.sqrt(self.attention_head_size)
if
# Apply the attention mask is (precomputed for all layers in BertModel forward() function) [1,1,1,0,0] -> [0,0,0,-10000,-10000]
attention_scores = attention_scores + attention_mask

# Normalize the attention scores to probabilities.
attention_probs = nn.Softmax(dim=-1

# This is actually dropping out entire tokens to attend to, which might
# seem a bit unusual, but is taken from the original Transformer paper.
attention_probs = self.dropout(attention_probs)

# Mask heads if we want to
if
attention_probs = attention_probs * head_mask

context_layer = torch.matmul(attention_probs, value_layer)

context_layer = context_layer.permute(0
new_context_layer_shape = context_layer.size()[:-2
context_layer = context_layer.view(*new_context_layer_shape)

outputs = (context_layer, attention_probs) if
return
```

ps: 代码里实现attention_mask使用了加法，因为softmax中针对e^0也会输出1，所以我们要对于忽视的token进行$e^{-inf}$，才能使他在softmax之后的权重为0。

### add and norm

常见的残差网络方式梯度消失，增加模型的训练，打破了网络的对称性，提升了网络的表征能力。

```python
class
def
super
self.dense = nn.Linear(config.hidden_size, config.hidden_size)
self.LayerNorm = nn.LayerNorm(config.hidden_size, eps=config.layer_norm_eps)
self.dropout = nn.Dropout(config.hidden_dropout_prob)

def
hidden_states = self.dense(hidden_states)
hidden_states = self.dropout(hidden_states)
hidden_states = self.LayerNorm(hidden_states + input_tensor)
return
```

### FFN and Add Norm

先经过中间层3072，hidden_size扩大4倍。之后再经过一个缩小了。注意这里最后才有一个dropout。激活函数用的gelu，比relu稍微缓和了一些。

```python
class
def
super
self.dense = nn.Linear(config.hidden_size, config.intermediate_size)
if
self.intermediate_act_fn = ACT2FN[config.hidden_act]
else
self.intermediate_act_fn = config.hidden_act

def
hidden_states = self.dense(hidden_states)
hidden_states = self.intermediate_act_fn(hidden_states)
return

class
def
super
self.dense = nn.Linear(config.intermediate_size, config.hidden_size)
self.LayerNorm = nn.LayerNorm(config.hidden_size, eps=config.layer_norm_eps)
self.dropout = nn.Dropout(config.hidden_dropout_prob)

def
hidden_states = self.dense(hidden_states)
hidden_states = self.dropout(hidden_states)
hidden_states = self.LayerNorm(hidden_states + input_tensor)
return
```

### 最后处理

综上，把这个bert_layer叠个12层就行了。但是在最后输出的时候[CLS]有一个特殊的处理。输出的时候会经过一个线性层+一个tanh激活。

### NER  token classification

在每一个token对应的输出加入一个线性分类层，对应所有的实体类型标签比如B-PER,I-PER。

> https://zhuanlan.zhihu.com/p/109250703
> https://zhuanlan.zhihu.com/p/47282410

## CRF

CRF Conditional Random Field条件随机场。是一种无向图模型，在给定需要标记的观测序列的条件下，计算整一个序列的联合概率。

$\Theta(x_1,…,x_m,s_1,…,s_m) \in \mathbb{R^d}$

由于BERT模型只会针对每一个token而不是一个实体输出标签概率，而较少地考虑到token标签之间的关系。所以我们需要增强模型对于相邻token标签之间关系的理解。比如”杭州是浙江省的省会城市”，“杭”和”州”可能都被识别为地名，但是这里应该识别“杭州”一个整体的地名，就不应该是“杭”-B-LOC，“州”-B-LOC而应该是“杭”-B-LOC，“州”-I-LOC。

CRF的损失函数为$l(\theta)=\cfrac{P_{RealPath}}{P_1+P_2+…+P_N}$

条件随机场为$P(y|x)=\exp[\sum^{SeqLen}_{k=1}\lambda_k \sum^{Cond}_{i=2}t_k(y_{i-1},y_i,x,i)+\sum_l \mu_l \sum_i s_l(y_i,x,i)]$

$t_k$是转移特征函数，$s_l$是状态特征函数。

由于BERT已经产生了状态特征函数，即每一个token的标签概率值，CRF只需要去求转移特征函数，即一个长度为标签个数的转移矩阵即可。

### 优点

- CRF相对于HMM使用了上下文的信息，不单单只依据前一个的状态来预测后一个的状态。

> https://zhuanlan.zhihu.com/p/94457579

基于BERT的知识库问答系统

https://www.cheasim.com/uncategorized/2021/01/14/%E5%9F%BA%E4%BA%8EBERT%E7%9A%84%E7%9F%A5%E8%AF%86%E5%BA%93%E9%97%AE%E7%AD%94%E7%B3%BB%E7%BB%9F.html

作者
CheaSim

发布于
2021-01-14

更新于
2021-03-08

许可协议

#[bert](https://www.cheasim.com/tags/bert/)[crf](https://www.cheasim.com/tags/crf/)[bilstm](https://www.cheasim.com/tags/bilstm/)




