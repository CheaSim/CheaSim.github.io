# UNIFIEDQA Crossing Format Boundaries with a Single QA System 读书笔记

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2021/01/20/unifiedqa-crossing-format-boundaries-with-a-single-qa-system-%E8%AF%BB%E4%B9%A6%E7%AC%94%E8%AE%B0/
发布日期：2021-01-20
更新日期：2021-01-20





# UNIFIEDQA: Crossing Format Boundaries with a Single QA System 读书笔记

针对不同形式的QA做了一个整合的工作。对于抽取式、多选式、对错形式的QA数据集，使用了一个单一的模型进行训练，并且测试。

使用的模型是T-5、BART。

## 1. 看过摘要之后，自己提出几个问题

- 这篇文章说跨越了多个QA数据集的鸿沟，怎么跨越的？

- 效果这么好，那原来的模型怎么不去试一试？是模型好，还是多数据集综合训练训得好？

- GPT-3 可以做到这一点吗？

## 2. 对应问题的解答；

### 2.1

对于各种数据集，把他们使用text-to-text的方法输入到模型中。由于是生成模型，所以input和output是一样的。将不同数据集的question，article，option这几项用几个特殊标识串起来，就ok了。

### 2.2

观察了一下文章中的数据集表格做得挺漂亮的。把数据集的基本信息还有比较关键的best published这个。

![image-20201113204535500](https://www.cheasim.com/Users/cheasim/Library/Application Support/typora-user-images/image-20201113204535500.png)

这篇文章把心路过程也写出来了，之前有一个试点实验(pilot study)。就是看在其他格式下数据集上的训练是否也对原始的有效果。这里可以看出确实有效果，在有些数据集上效果还挺明显的。![image-20201113205728295](https://www.cheasim.com/Users/cheasim/Library/Application Support/typora-user-images/image-20201113205728295.png)

### 2.3

没钱，没资源玩GPT。

## 3. 用自己的话阐述文章的核心问题和思路；

核心问题：提出一个大一统的模型，可以处理所有形式的QA dataset。直觉上，所有的QA任务都是针对挖掘原文问题中的语义信息，并且与答案进行逻辑匹配，亦或者是类似于常识推理的在模型原有知识的基础上，对于问题的理解并且回答。

思路：首先判别模型是没法做到了，因为输出的格式不一样，抽取式阅读理解和多选阅读理解输出的东西不一样，虽然可以把多选转化为抽取。。 生成模型就是有着和人一样的无限潜能。之后的pliot study不错，就是简单地试一试额外训练其他形式的数据集，看看对原始数据集是否有增益。

## 4.可能改进的地方；

- 攻击一下，是不是加个同领域预训练也能提高效果。里面试点实验都是准确率比较低的数据集上测试的。低的提高那肯定简单~

- 之前还看到有一篇将所有数据集转化为一种形式的，这两篇是否有共同之处。

- 全是实验，没有对理论的分析或者是啥的。。

- 输入格式是否还可以改进一下？

## 5.自己画一遍文章的流程图；

流程没有创新，就是input自己定义了格式。

## 6.捋一遍算法流程.

UNIFIEDQA Crossing Format Boundaries with a Single QA System 读书笔记

https://www.cheasim.com/uncategorized/2021/01/20/UNIFIEDQA-Crossing-Format-Boundaries-with-a-Single-QA-System-%E8%AF%BB%E4%B9%A6%E7%AC%94%E8%AE%B0.html

作者
CheaSim

发布于
2021-01-20

更新于
2021-03-08

许可协议

#[论解](https://www.cheasim.com/tags/%E8%AE%BA%E8%A7%A3/)[QA](https://www.cheasim.com/tags/QA/)[随性](https://www.cheasim.com/tags/%E9%9A%8F%E6%80%A7/)




