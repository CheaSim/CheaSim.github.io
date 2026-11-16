# Dialogue Relation Extraction with Document-level Heterogeneous Graph Attention Networks 论文解读

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2020/12/03/dialogue-relation-extraction-with-document-level-heterogeneous-graph-attention-networks-%E8%AE%BA%E6%96%87%E8%A7%A3%E8%AF%BB/
发布日期：2020-12-03
更新日期：2020-12-03





# Dialogue Relation Extraction with Document-level Heterogeneous Graph Attention Networks 论文解读

论文传送门，代码传送门

## 任务

从对话数据集中抽取出实体之间的联系。给定一段对话，输出指定两个实体之间的关系，总共有37中不同的关系。

## 模型

针对对话中不同的信息进行embedding，

- utterance ，对话中的话使用LSTM模型进行encode。

- speaker

- argument

- entity-type

- word

由着四种embedding来构建图。之后拼接学到的argument embedding通过分类器输出关系。

Dialogue Relation Extraction with Document-level Heterogeneous Graph Attention Networks 论文解读

https://www.cheasim.com/uncategorized/2020/12/03/Dialogue-Relation-Extraction-with-Document-level-Heterogeneous-Graph-Attention-Networks-%E8%AE%BA%E6%96%87%E8%A7%A3%E8%AF%BB.html

作者
CheaSim

发布于
2020-12-03

更新于
2020-12-11

许可协议

#[论解](https://www.cheasim.com/tags/%E8%AE%BA%E8%A7%A3/)[抽取](https://www.cheasim.com/tags/%E6%8A%BD%E5%8F%96/)




