# ACM-ICPC 2018 徐州赛区网络预赛

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/09/10/acm-icpc-2018-%E5%BE%90%E5%B7%9E%E8%B5%9B%E5%8C%BA%E7%BD%91%E7%BB%9C%E9%A2%84%E8%B5%9B/
发布日期：2018-09-10
更新日期：2018-09-10





# ACM-ICPC 2018 徐州赛区网络预赛

## A. Hard to prepare

### 题意

$n$个人围成环，每个人可以选择$[0,2^k-1]$中的一个数字，要求相邻两人不能同或为0。

### 题解

递归。

可以YY出，第一个人有$2^k$种选择，之后第2到第$n-1$个人有$2^k-1$种选择，最后一个人可能可以选$2^k-2$，也可能可以选$2^k-1$。这取决于倒数第二个人是否跟第一个人选一样的。这时候我们就可以加上如果第一个人和倒数第二个人选择相同，并且，最后一个人多选了那$2^k-1-(2^k-2)$种，那么他们三个点变成一个点来选择了。

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
int
const
ll pow3
ll ans = 1
while
if
a = a*a%mod;
b>>=1
}
return
}
ll k2,kk2,kk1;
ll solve
if
if
if
ll res = (k2*kk2%mod)*pow3(kk1,n-2
res = (res+solve(n-2
return
}
int
#ifdef
freopen("4.in"
#endif
int
while
scanf
k2 = pow3(2
kk1 = (k2-1
kk2 = (k2-2
printf
}

return
}
```

## B.BE,GE or NE

### 题意

两个人玩游戏，给出$[0,3]$个选项和一个$m$初始值，两个人依次选择，有以下三种选择

- 选择将值$+a$

- 选择将值$-b$

- 选择将值倒过来 $m=-m$

两个人一个想将值变大，一个想让值变小，两个人都知晓所有情况和选项，在最优情况下，问谁赢。

### 题解

博弈论dp+记忆化搜索

因为数据量很小，范围也在200之间，所以记忆化状态回复的很多。

$dp[pos][val]$表示在pos位置数值是val,之后dp代表的是最优可以赢还是输还是平，分别用2,1,0代表。

之后对于边界值要处理一下。数组存不了负值，我们统一加100处理。

妈的。我看到这个以为是纯博弈论直接人傻了。之后想着能不能记忆化搜索，但是看到$n=1000$还以为他喵的会爆，但是这道题的情况限制在范围$-100到100$，所以情况很少。所以可以直接记忆化，不过对于答案的选择和状态转移我可能还是不会太轻松地做出来，带int的dfs我还是不怎么熟悉，这按道理应该是算是博弈论dp了。从最优状态转移到最优状态。

### AC代码

```cpp
#include
using
#define
#define
#define
#define
#define
#define
#define
#define
typedef
typedef
typedef
const
ll powmod
ll gcd
// head
int
const
int
int
// op
int
if
if
return
}else
return
}else
return
}
}
if
if
int
int
int
if
if
if
return
}else
int
int
int
if
if
if
return
}
}
int
#ifdef
freopen("b.in"
#endif
rep(i,0
scanf
l += 100
rep(i,0
scanf
}
int
if
else
else
return
}

```

ACM-ICPC 2018 徐州赛区网络预赛

https://www.cheasim.com/acm/2018/09/10/ACM-ICPC-2018-%E5%BE%90%E5%B7%9E%E8%B5%9B%E5%8C%BA%E7%BD%91%E7%BB%9C%E9%A2%84%E8%B5%9B.html

作者
CheaSim

发布于
2018-09-10

更新于
2018-09-12

许可协议

#[网络赛](https://www.cheasim.com/tags/%E7%BD%91%E7%BB%9C%E8%B5%9B/)[acm](https://www.cheasim.com/tags/acm/)




