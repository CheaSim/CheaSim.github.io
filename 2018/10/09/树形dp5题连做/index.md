# 树形dp5题连做

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/10/09/%E6%A0%91%E5%BD%A2dp5%E9%A2%98%E8%BF%9E%E5%81%9A/
发布日期：2018-10-09
更新日期：2018-10-09





# 树形dp，3天搞定

## A - Information Disturbing

### 题意

对于一棵树，切断一些边使得每一个叶节点都无法连接到根节点，有两个要求

- 每条边带权重，切掉的边权重和不大于$m$

- 切掉的每条边都不能大于一个$ans$

问$ans$最小是多少？

### 题解

二分+树形dp

+1 ans初始化-1

看别人代码发现了个好东西，链式前项星判断节点是否为叶节点可以这样判断

```cpp
if
该节点是叶节点 //在双向边的时候适用
if
该节点是叶节点 //在单向边的时候适用
```

### ac代码

树形dp5题连做

https://www.cheasim.com/acm/2018/10/09/%E6%A0%91%E5%BD%A2dp5%E9%A2%98%E8%BF%9E%E5%81%9A.html

作者
CheaSim

发布于
2018-10-09

更新于
2018-10-09

许可协议

#[树形dp](https://www.cheasim.com/tags/%E6%A0%91%E5%BD%A2dp/)[专题](https://www.cheasim.com/tags/%E4%B8%93%E9%A2%98/)




