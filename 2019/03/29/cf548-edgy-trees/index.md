# [cf548]Edgy Trees

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2019/03/29/cf548-edgy-trees/
发布日期：2019-03-29
更新日期：2019-03-29





# Codeforces Round #548 (Div. 2)

## C.Edgy Trees

### 题意

给一个树，树上的边分为黑色或者红色，现在我们定义一个序列[𝑎1,𝑎2,…,𝑎𝑘]

- 我们按照次序经过序列中的每一个点(最短路径)

- 如果进过至少一条黑边，那这个序列就是好的。

### 题解

至少一条的反义词就是一条都没有，这道题就是找没有黑边的子树。之后答案就是每个子树中的个数的$k$次方。

想着树形dp做，想了很久都没有写出来。

### ac代码

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
int
struct
int
}G[maxn>= 1
x = x*x%mod;
}
return
}
int
#ifdef
freopen("3.in"
#endif
init();
scanf
rep(i,0
int
addedge(u,v,val); addedge(v,u,val);
}
ll ans = pow3(n,k);
ll last = 0
rep(i,1
if
ll temp = t - last;
last = t;
ans = (ans + mod - pow3(temp,k)) % mod;
}
printf
return
}
```

[cf548]Edgy Trees

https://www.cheasim.com/cf/2019/03/29/cf548-Edgy-Trees.html

作者
CheaSim

发布于
2019-03-29

更新于
2019-03-29

许可协议

#[cf](https://www.cheasim.com/tags/cf/)[dfs](https://www.cheasim.com/tags/dfs/)[math](https://www.cheasim.com/tags/math/)




