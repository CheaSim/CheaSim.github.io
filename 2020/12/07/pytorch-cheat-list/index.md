# pytorch cheat_list

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2020/12/07/pytorch-cheat-list/
发布日期：2020-12-07
更新日期：2020-12-07





# pytorch 操作小计

> torch==1.7.0

## tensor

### torch.stack

将List[tensor]变成tensor。torch.stack(tensors,dim=0,out=None)Concatenates a sequence of tensors along a new dimension.

```python
b = torch.randn(4
a = torch.stack([b, b], dim = 0
```

### torch.gather

> torch.gather(input, dim, index, *, sparse_grad=False, out=None) → Tensor

英文解释为Gathers values along an axis specified by dim.

看到比较有道理的应用场景是，在变长序列中gather到最后一个或者说倒数第几个元素。一般变长序列为inputs = [[1,2,3,0,0], [2,3,4,5,0]]。这时候想获得最后一个元素就可以。需要注意的点是，输出的tensor和index是相同shape的。

```python
inputs = torch.tensor([[1
[2
index = torch.tensor([[2
last_inputs = torch.gather(inputs, dim=1
"""tensor([[3],
[5]])"""
```

### torch.expand

将tensor扩展维度，自动复制，十分好用。

```python
a = torch.randint(1
#tensor([[3, 1, 1],
#        [1, 2, 4]])
a = a.unsqueeze(2
"""
tensor([[[3, 3, 3],
[1, 1, 1],
[1, 1, 1]],

[[1, 1, 1],
[2, 2, 2],
[4, 4, 4]]])"""
```

### torch.repeat

repeat(*sizes) -> Tensor， 重复复制tensor在指定的维度上。其实有点类似于广播操作了？

```python
x = torch.tensor([1
x.repeat(4
x.repeat(4
```

## torch.nn.functional

### F.softmax

F.softmax(Tensor, dim=None) 对于多维度矩阵就是 einsum(‘ijk -> jk’, a) = torch.ones(a.shape[1:])

```python
import
a = torch.randn(4
a = F.softmax(a, dim = 0
```

## torch.nn

之前一直依赖着huggingface的模型加载from_pretrained，但其实在一般任务场景下，使用torch.load的时候会更多，所以记录一下torch.load方法的使用场景。

### torch.load & torch.save

一般我们将模型的参数保存，而不会去保存整个模型的结构。这里如果需要部分加载参数，可以使用strict=False。这里需要注意加载的是字典dict，不是模型。

```python
#model ... after training
torch.save(model.state_dict(), cached_file_path)
model_state = torch.load(cached_file_path)
model.load_state_dict(model_state, strict=False
```

## 奇淫技巧

### whole word mask

在bert或者其他语言模型中，对一段文本需要先进行tokenize分词操作，而分英文单词的时候，由于OOV问题，会将有些word分成token级别的，比如将trying分成try,##ing。而我们比如在建图或者以word为粒度的时候，就需要将token的输出平均给word了。那么如何操作呢？

```python
encoder_output = encoder_outputs[i]  # [slen, bert_hidden_size]
word_num = 123
word_index=(torch.arange(word_num) + 1
words = pos_id[i].unsqueeze(0
select_metrix = (mention_index == mentions).float
# average word -> mention
word_total_numbers = torch.sum
select_metrix = torch.where(word_total_numbers > 0
x = torch.mm(select_metrix, encoder_output)
```

pytorch cheat_list

https://www.cheasim.com/uncategorized/2020/12/07/pytorch-cheat-list.html

作者
CheaSim

发布于
2020-12-07

更新于
2021-01-06

许可协议

#[AI](https://www.cheasim.com/tags/AI/)[pytorch](https://www.cheasim.com/tags/pytorch/)




