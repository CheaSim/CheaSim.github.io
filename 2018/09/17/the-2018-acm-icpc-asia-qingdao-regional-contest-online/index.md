# The 2018 ACM-ICPC Asia Qingdao Regional Contest, Online

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/09/17/the-2018-acm-icpc-asia-qingdao-regional-contest-online/
发布日期：2018-09-17
更新日期：2018-09-17





# The 2018 ACM-ICPC Asia Qingdao Regional Contest, Online（青岛网络赛）

## B.Red Black Tree

### 题意

### 题解

### ac代码

## J.Press the Button

### 题意

### 题解

### ac代码

## H Traveling on the Axis

### 题意

BOB走在$[1,n]$的路上，每两个点中间都有一个红绿灯，每一秒钟，

- BOB先观察红绿灯是否绿，绿就走，红就停。

- 红灯变绿，绿灯变红

$t(p,q)$就是$p$走到$q所需要的时间。

问： BOB从 $\sum^{n-1}{p=0} \sum{q=p+1}^nt(p,q)$的时间总和。

### 题解

对于第$i$个单独的红绿灯我们可以证明他对答案的贡献是

​                          $(i)(len-i+1)(t(i))$

我们对于两个灯进行分析。

01 第一个零要2s，第二个一要1s

10 第一个一要1s，第二个零要1s

00 第一个零要2s，第二个一要2s

11 第一个一要1s，第二个一要2s

综上可以发现，

- 该灯初始为0，那么他当头的时候贡献为2，如果不当头那么他的贡献就为1，除非跟前者相同。

- 该灯初始为1，那么他和前一个灯相同时贡献为2，就算变成0了，不在头上的话贡献也为1.

我他妈sb了，不应该看着一段一段的区间，应该把红绿灯作为每一次状态的扩展，从红绿灯这$n$个出发开始计算，不应该考虑一个一个的单位为1的区间。

### AC代码

```cpp
// CSL 代码
#include
using
const
char
typedef
int

int
scanf
while
{
scanf
ll ans = 0
int
for
for
{
if
if
//要跟包含前者的可能，要两个相同才能这么加。
}
printf
}
}
```

```cpp
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
char
int
#ifdef
freopen("h.in"
#endif
int
while
scanf
int
ll ans = 0
if
else
rep(i,1
if
else
if
else
ans += w;
}
printf
}

return
}
```

> reference:
> https://blog.csdn.net/tianyizhicheng/article/details/82728350

The 2018 ACM-ICPC Asia Qingdao Regional Contest, Online

https://www.cheasim.com/acm/2018/09/17/The-2018-ACM-ICPC-Asia-Qingdao-Regional-Contest-Online.html

作者
CheaSim

发布于
2018-09-17

更新于
2018-09-17

许可协议

#[网络赛](https://www.cheasim.com/tags/%E7%BD%91%E7%BB%9C%E8%B5%9B/)[acm](https://www.cheasim.com/tags/acm/)




