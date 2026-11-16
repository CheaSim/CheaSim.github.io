# [UVA11174] Stand in a line

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/08/30/uva11174-stand-in-a-line/
发布日期：2018-08-30
更新日期：2018-08-30





# Stand in a line

## 题意

给定$n-1​$组关系，节点$a​$不能站在节点$b​$的前面，使得$n​$站成一行，问有多少种站法。

## 题解

树形dp + 组合数学

- 先建树，把没有父亲的节点都并入$0$节点，这样我们就有一颗完整的树了。

- 寻找规律，假设$f[i]$为以$i$为根节点的方案数，那么当每增加一颗子树的时候，他的组合是相当于有一个有拓扑排序方案和另外一个拓扑排序方案相组合。

> 我们可以这样想像，假设拓扑排序是不存在的，这些点的排序忽略，那么点可以看做是同样颜色的点，那么$x_1,x_2$个数的点排列的排列数为$(x_1+x_2)! /(x_1! * x_2!)$。而这些点其实是不一样的，他们有自身的拓扑排序顺序，于是答案就是$f(x_1)  f(x_2)  (x_1+x_2)!/(x1! * x_2!)$。

- 于是乎，我们先处理好每个节点的子节点(包含他自身)，可以用拓扑排序直接做，不用递归，当然也可以递归，于是就是相当于从子树开始处理，把所有子树的节点数的阶乘除掉就可以了。

简单写一下从递推到通向。$c_i$表示是$root$的子节点，$s(i)$表示$i$节点的子节点数。

$f(root) = f(c1)f(c2)…f(c_k)*((s(root)-1)!/s(c_1)!/s(c_2)!/…/s(c_k)!)$

$f(c_1)=f(x_1)f(x_2)…f(x_z)*((s(c_1)-1)!/s(x_1)!/s(x_2)!/…/s(x_z)!)$

$s(c_1)和s(c_1-1)$可以约掉。而且到叶子节点$f(x_1)$都变成$1$了$s(x_1)$也变成了0.

$f(root)=(s(root)-1)!/s(1)/s(2)/…/s(n)$

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
int
struct
int
}G[maxn>=1
}
return
}
int
#ifdef
freopen("2.in"
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
add(u,v);vis[v] = 1
}
rep(i,1
memset
vis[0
int
while
int
for
int
if
pre[v] = u;
vis[u] = 1
q[++r] = v;
}
}
per(i,1
sz[q[i]]++;
sz[pre[q[i]]] += sz[q[i]];
}
sz[0
ll res = 0
ll cnt = fac[n];
rep(i,1
printf
}
return
}
```

Reference:https://blog.csdn.net/xiao_k666/article/details/78609562

[UVA11174] Stand in a line

https://www.cheasim.com/acm/2018/08/30/UVA11174-Stand-in-a-line.html

作者
CheaSim

发布于
2018-08-30

更新于
2018-08-30

许可协议

#[树形dp](https://www.cheasim.com/tags/%E6%A0%91%E5%BD%A2dp/)




