# [hdoj5521]Meeting

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/09/06/hdoj5521-meeting/
发布日期：2018-09-06
更新日期：2018-09-06





# Meeting

## 题意

将图分成$m$个块，每个块中的点到块中点的需要的时间为$E_i$。Bessie在点1，Elsie在点$n$，问他们在最短的时间走到可以到哪一个点会和。点可以在不同的块中。

## 题解

如果想要每个点都建边，无疑会爆空间。我们可以看出每个点都分配到几个块，而每个块又有几个点。那么我们可以将块看做点，连接着块中的点，这样每个块的边从$O(n^2)$变成了$O(n)$。

我tmWA了20发，就是因为以前都是将点做标记，但是这次是块也要做标记，不然每块会浪费很多时间。而且因为只要该点是最优的，那么该块也是最优的了(因为该点到该块的距离为0)。

## AC代码

```cpp
#include
#pragma
using
#define
#define
#define
#define
typedef
typedef
const
#define
const
ll val[maxn];
ll cnt1[maxn],cnt2[maxn];
inline
int
while
while
return
}
//head
int
ll ans[maxn];
int
struct
ll t;
int
node(){}
node(ll a,int
bool
return
}
};
void
cnt[rt] = 0
priority_queue
memset
int
memset
q.push(node(0
while
int
for
if
use[bk] = 1
for
if
cnt[v] = cnt[u] + val[bk];
q.push(node(cnt[v],v));
}
}
}
}
int
#ifdef
freopen("m.in"
#endif
scanf
rep(test_case,1
memset
memset
scanf
vector
vector
rep(i,1
rep(i,1
rep(i,1
val[i] = read(); int
rep(j,0
int
E[i].pb(x);B[x].pb(i);
}
}
bfs(1
ll mmin = 0xfffffff
rep(i,1
ans[i] = max(cnt1[i],cnt2[i]);
if
}
if
printf
else
printf
continue
}
int
ll res[maxn];
rep(i,1
if
res[cnt++] = i;
}
rep(i,0
printf
}
}
}
```

[hdoj5521]Meeting

https://www.cheasim.com/acm/2018/09/06/hdoj5521-Meeting.html

作者
CheaSim

发布于
2018-09-06

更新于
2018-09-06

许可协议

#[图论](https://www.cheasim.com/tags/%E5%9B%BE%E8%AE%BA/)




