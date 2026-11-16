# LCA专项练习

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/09/28/lca%E4%B8%93%E9%A1%B9%E7%BB%83%E4%B9%A0/
发布日期：2018-09-28
更新日期：2018-09-28





# LCA专项练习

## 前提提要

由于A,B太水了，就不放了。

前几题先试试用trajan能不能全杀，之后再看在线算法。

## 易错点统计

- 如果两个点相同，那么他们的祖先节点居然会变成0。。可能是我的模板写法有点问题。可以在判断vis[u]=2的时候加上如果u=now也是找到了公共祖先。

- i=fa[j]; 应该是fa[j] = i;

- 如果要加入假设边的话，G[maxn

## C - Distance Queries

### 题意

一棵树，求两点之间最短距离。

### 题解

裸LCA+dfs求距离

### AC代码

```cpp
#include
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
const
struct
int
Query(){}
Query(int
to = a;id = b;
}
};
vector
struct
int
}G[maxn
- 将$v$,$v$两个点之间所有的点包括这两个点的权值全部加$val$

- 将$v$,$v$两个点之间所有的边的权值全部加$val$

### 题解

lca+标记递推

我们定义$add[x][0]$为在$x$点上往后递推的点值，那么对于两个$u,v$来说我们要让这条链上的所有点都加$val$。

```cpp
1
2
3
4
add[u][0
add[v][0
add[x][0
des[x] -= val;
```

其中$x$是他们的LCA，而且为了使得到了他们的LCA不继续增加这个值，我们定义一个数组$des[]$，递推的时候就加上这个数组在递推，就可以使得在LCA的时候不递推到LCA的祖先节点了。

### 树链剖分题解

树链剖分可以处理点权和边权，不过这是我第一次看到一起处理的。

> trick:
> 把点用数组存起来，到边的时候就用孩子节点来表示孩子节点到父亲节点的边。

### ac代码

## G - One and One Story

## H - CD操作

### 题意

一个加一点背景的LCA，往父节点走要+1，从祖先节点到任意子节点也只需要加1。

### 题解

LCA，我用了ST表+RMQ，跑的飞快。

### AC代码

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
111
112
113
114
115
116
117
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
const
int
int
int
struct
int
}G[maxn
LCA专项练习

https://www.cheasim.com/%E4%B8%93%E9%A1%B9%E7%BB%83%E4%B9%A0/2018/09/28/LCA%E4%B8%93%E9%A1%B9%E7%BB%83%E4%B9%A0.html

作者
CheaSim

发布于
2018-09-28

更新于
2018-10-08

许可协议

#[acm](https://www.cheasim.com/tags/acm/)[LCA](https://www.cheasim.com/tags/LCA/)




