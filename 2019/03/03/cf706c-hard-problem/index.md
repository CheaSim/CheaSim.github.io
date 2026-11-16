# [cf706C]Hard Problem

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2019/03/03/cf706c-hard-problem/
发布日期：2019-03-03
更新日期：2019-03-03





# 706C - Hard problem

## 题意

题意很简单，就是给定$n$串字符串，对每一串字符串只有一种操作，翻转。之后每翻转一个字符串需要消耗$c_i$的能量，问至少需要多少能量是的，这$n$个字符串是以字典序排列的。

ps:相等也算按字典序

## 题解

dp，定义一个二维数组$dp[i][j]$。其中$i$表示第$i$个字符串中选择$j$产生字典序的最少能量消耗。$j$只有1和0，表示翻转或者不翻转，之后就是四种情况下去。具体可以看代码.

## ac代码

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

ll n,m,q;
ll d;
const
ll num[maxn];
ll dp[maxn][12
ll a[maxn];
ll MOD
ll tx = x % mod;
if
return
}
int
#ifdef
freopen("1.in"
#endif
int
rep(test_case,1
scanf
rep(i,1
printf
while
scanf
rep(i,1
memset
rep(i,0
rep(i,1
rep(j,1
rep(k,0
rep(k,0
dp[i][j][(k+a[i])%d] += dp[i-1
}
}
}
printf
}
}
return
}
```

[cf706C]Hard Problem

https://www.cheasim.com/dp/2019/03/03/cf706C-Hard-Problem.html

作者
CheaSim

发布于
2019-03-03

更新于
2019-03-06

许可协议

#[dp](https://www.cheasim.com/tags/dp/)[cf](https://www.cheasim.com/tags/cf/)




