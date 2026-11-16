# LCA学习笔记

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/09/25/lca%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0/
发布日期：2018-09-25
更新日期：2018-09-25





# LCA学习笔记

## 祖先的定义

如果学习树结构就会明白除了根节点以外每个节点都有一个父节点，所以我们定义祖先为父节点的父节点，然后我们给出最近公共祖先的定义

> 一棵树祖先中到两个点距离最近的节点。

能够解决LCA问题的方式有很多，所以作为一个ACM选手，肯定是我全都要

## 解决方案

### 欧拉序

树的欧拉序是对树进行dfs的一种序列，他有两条性质

- 在每个节点进和出都加入序列

- 只要到达每一个节点就把他加入序列

那么我们寻找他们的最近公共祖先就可以从第一次出现第一个节点和第一次出现的第二个节点之间节点中深度最大的节点。

#### HDOJ[2586]

```cpp
#include
using
#define
#define
#define
#define
#define
typedef
typedef
const
//head
const
const
int
int
struct
int
}G[maxn
- 任选择一个点作为根节点，从根节点开始

- 遍历该节点的所有子节点，并标记这些子节点$v$已经被访问过

- 如果$v$还有子节点，返回2，否则就进入下一步

- 合并$v$到$u$。

- 寻找与当前点$u$有询问关系的点$v$

- 若是$v$已经被访问过了，则可以确定$u$和$v$的最近公共祖先为$v$被合并的父亲节点$fa[u]$。

```cpp
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35
36
37
38
39
40
41
42
43
44
45
46
47
48
49
50
51
52
53
54
55
56
57
58
59
60
61
62
63
64
65
66
67
68
69
70
71
72
73
74
75
76
77
78
79
80
81
82
83
84
85
86
87
88
89
90
91
92
93
94
95
96
97
98
99
100
101
102
103
104
105
106
107
108
109
110
#include
#include
#include
#include
using
#define
#define
#define
#define
typedef
typedef
const
//head
int
const
struct
int
}G[maxn
- 线段树、树状数组

- ST表

他们均可以有效地解决区间最值问题。

#### 例题[hdoj5044]

使用方法为 RMQ+正负tag

详情见我刷的LCA专题训练。

> Reference:https://blog.csdn.net/czl_233/article/details/78368927
> http://www.cppblog.com/menjitianya/archive/2015/12/10/212447.html
> http://www.cnblogs.com/JVxie/p/4854719.html

LCA学习笔记

https://www.cheasim.com/%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0/2018/09/25/LCA%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.html

作者
CheaSim

发布于
2018-09-25

更新于
2018-09-29

许可协议

#[acm](https://www.cheasim.com/tags/acm/)[学习笔记](https://www.cheasim.com/tags/%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0/)[lca](https://www.cheasim.com/tags/lca/)




