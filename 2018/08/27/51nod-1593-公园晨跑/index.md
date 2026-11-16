# 51Nod-1593 公园晨跑

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/08/27/51nod-1593-%E5%85%AC%E5%9B%AD%E6%99%A8%E8%B7%91/
发布日期：2018-08-27
更新日期：2018-08-27





# 51Nod-1593 公园晨跑

## 题意

给定一个环，环上有$n$个点，每个点有一个权值$h$代表着如果从$i$到$j$的话，你必须加上$2h_i+2h_j$。并且加上他们之间的距离$L$。并且在环上会有一个区间被占用导致只能从另外一个方向走。

## 题解

线段树维护区间最大最小值的坐标和特判相同处理。

首先，面对环和方向性，我们可以把环拆成链式。形成一个$[1,n] \cup [1.n]$的区间对于$X,Y$的查找可以看成两种情况，

- 一种是$X\leq Y$，那么我们寻找的范围就是$[Y+1,X+n-1]$。

- 对于$X>Y$的情况，我们寻找的范围就是$[Y+1,X-1]$。

定义$d[x]$为$x$点到第一个点的距离(线性)。

对于给定的两个点$X,Y$，我们获得的权值是确定的，为$d[Y]-d[X]+2h[X]+2h[Y]$，我们可以将这个算式分为$X$部分和$Y$部分。于是我们就可以将式子转化为

$target = (d[Y]+2h[Y]) - (d[X]-2h[X])$

这个式子求最大值，就是对于每个点求第一部分的最大值和第二部分的最小值。之后由于$X != Y$，所以对于线段树维护的是区间内最大最小值的坐标。当坐标相同时，寻找次一级的最小值或者次一级的最大值。

## AC代码(要加入读入优化)

```cpp
#include
using
#define
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
ll h[maxn],d[maxn],A[maxn],B[maxn];
int
template
bool
char
bool
while
if
else
x = c - '0'
while
x = x * 10
if
return
}
inline
return
}
inline
return
}
inline
return
}
int
void
mmax[rt] = Max(mmax[rt
51Nod-1593 公园晨跑

https://www.cheasim.com/acm/2018/08/27/51Nod-1593-%E5%85%AC%E5%9B%AD%E6%99%A8%E8%B7%91.html

作者
CheaSim

发布于
2018-08-27

更新于
2018-08-27

许可协议

#[线段树](https://www.cheasim.com/tags/%E7%BA%BF%E6%AE%B5%E6%A0%91/)




