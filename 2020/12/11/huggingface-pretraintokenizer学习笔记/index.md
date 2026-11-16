# HuggingFace PretrainTokenizer学习笔记

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2020/12/11/huggingface-pretraintokenizer%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0/
发布日期：2020-12-11
更新日期：2020-12-11





# 笔记

> Transformers==4.0.0
> 由于每次调用bert等模型都需要使用模型的tokenizer，所以写个笔记，方便自己以及后人查阅，（其实看官方文档也可以，但是英文的看着头疼。有错误也请留言吧。

## base : PreTrainedTokenizerBase

作为基类，该类有着所有tokenizer都具有的方法还有属性。

### PreTrainedTokenizer

## 使用multiprocess 加速tokenize

仿照这个就完事了。partial可以固定函数中的参数，简直是专门为多进程准备的。

```python
def
global
tokenizer = tokenizer_for_convert

features = []

threads = min
with
annotate_ = partial(
tokenzier.encode_plus, # batch_encode_plus 不知道为什么不work
max_seq_length=max_seq_length,
doc_stride=doc_stride,
max_query_length=max_query_length,
padding_strategy=padding_strategy,
is_training=is_training,
)
features = list
tqdm(
p.imap(annotate_, examples, chunksize=32
total=len
desc="convert squad examples to features"
disable=not
)
)
```

HuggingFace PretrainTokenizer学习笔记

https://www.cheasim.com/uncategorized/2020/12/11/HuggingFace-PretrainTokenizer%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.html

作者
CheaSim

发布于
2020-12-11

更新于
2020-12-11

许可协议

#[学习笔记](https://www.cheasim.com/tags/%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0/)[tokenizer](https://www.cheasim.com/tags/tokenizer/)




