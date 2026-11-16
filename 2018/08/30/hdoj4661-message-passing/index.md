# [hdoj4661] Message Passing

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/08/30/hdoj4661-message-passing/
发布日期：2018-08-30
更新日期：2018-08-30





# HDOJ 4661: Message Passing

## 题意

每个人拥有一个信息，也可以传给另外一个人他拥有的所有信息。现在给定一个联络树，问至少多少次传递可以让所有人拥有所有信息。

## 题解

可以看出至少要$(n-1)*2$次传递，因为每个人都至少传出一次，传入一次。而怎么可以最少传递呢？我们可以假设根为中心，先将所有信息传递给他，之后再从他传递回来。这里有一点很巧妙，传入和传出的可能种类是一样的，所以我们只需要计算一次传入，平方后便是该点为中心的方案数。

因为子节点必须先传给父节点信息以免漏传，所以传入的方案数是满足一种拓扑排序的。那么可以看我之前的一篇博客，计算拓扑排序对一个点进行计算的。

那么怎么从已知的父节点的$f(root)$传递到子节点$f(v)$呢？

$s(i)$表示以$i$为根节点的子节点数目。

我们假设子节点$s(v)=q$，那么如果子节点变成根节点后，子节点的$s(v)=n$，而原来的父节点$f(u)$变成了$n-q$个子节点数目了。于是通过公式

$f(root)=(f(root)-1)!/s(1)/s(2)/…/s(n)$

我们可以推导出$f(v) = f(u) * s(q)/s(n-q)$

搞定!

## AC代码

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
const
struct
int
}G[maxn>=1
}
return
}
int
#ifdef
freopen("1.in"
#endif
scanf
fac[0
rep(i,1
fac[i] = fac[i-1
}
while
scanf
init();
rep(i,0
int
add(u,v);add(v,u);
}
int
while
int
for
int
if
pre[v] = u;
vis[v] = 1
q[++r] = v;
}
}
per(i,1
sz[q[i]] ++;
sz[pre[q[i]]] += sz[q[i]];
}
sz[1
ll cnt = fac[n];
rep(i,1
ll ans = 0
ans = cnt*cnt %mod;f[1
rep(i,1
ll cur = f[pre[q[i]]];
cur = cur*sz[q[i]] %mod;
cur = cur*pow3(n-sz[q[i]],mod-2
f[q[i]] = cur;
ans = (ans + cur*cur%mod) % mod;
}
printf
}
return
}
```

[hdoj4661] Message Passing

https://www.cheasim.com/acm/2018/08/30/hdoj4661-Message-Passing.html

作者
CheaSim

发布于
2018-08-30

更新于
2018-08-30

许可协议

#[树形dp](https://www.cheasim.com/tags/%E6%A0%91%E5%BD%A2dp/)




