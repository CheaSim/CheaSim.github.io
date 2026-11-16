# 概率dp入门

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/09/10/%E6%A6%82%E7%8E%87dp%E5%85%A5%E9%97%A8/
发布日期：2018-09-10
更新日期：2018-09-10





# 概率dp

概率dp有两种题型，一种是求概率一种是求期望。

来结合一下题目

## Aeroplane chess

### 题意

一个人在一条线上掷骰子，在线上有类似飞行棋的可以直接到达某个点的特殊点，问从$0$到$n$掷骰子次数的数学期望是多少？

### 题解

期望dp，dp最重要的就是从一个已知的最优状态转化到另一个最优状态。

为什么期望要反着求呢，因为你并不知道$dp[0]$这个点的值，因为我们定义$dp[x]$为$x$点到$n$点的掷骰子数的数学期望。而$dp[n]$的数学期望我们是知道的，是0，因为已经在$n$点了。之后我们倒推前面点的数学期望，因为你骰子是6面，从一个点可以到后面的六个点并且是等概率的，所以

$dp[i] = \sum_{j=i+1}^{i+6}dp[j]/6+1$

而且如果是特殊的飞行点，那么他的数学期望直接就是他的到的点的数学期望。

+2：没有从n-1开始，居然sb到从n开始计算。

### AC代码

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
int
const
double
int
int
#ifdef
freopen("11.in"
#endif
while
rep(i,0
rep(i,0
int
nxt[x] = y;
}
per(i,0
if
dp[i] = dp[nxt[i]];
}else
double
rep(j,1
if
sum+=dp[i+j];
}
}
dp[i] = sum/6.0
}
}
printf
}
return
}
```

## B - Discovering Gold

## 题意

跟上面的差不多，就是求期望。

## 题解

跟上面基本相似。

### AC代码

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
int
double
int
#ifdef
freopen("2.in"
#endif
scanf
rep(test_case,1
scanf
rep(i,1
per(i,1
double
double
rep(j,i+1
if
}
dp[i] += sum/cnt;
}
printf
}

return
}
```

概率dp入门

https://www.cheasim.com/%E6%A6%82%E7%8E%87dp/2018/09/10/%E6%A6%82%E7%8E%87dp%E5%85%A5%E9%97%A8.html

作者
CheaSim

发布于
2018-09-10

更新于
2018-09-10

许可协议

#[acm](https://www.cheasim.com/tags/acm/)[概率dp](https://www.cheasim.com/tags/%E6%A6%82%E7%8E%87dp/)




