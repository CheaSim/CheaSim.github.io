# [dp+graph] CodeForces - 721C

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2019/05/04/dp-graph-codeforces-721c/
发布日期：2019-05-04
更新日期：2019-05-04





# [dp+graph] CodeForces - 721C

## 题意

给定一个有向无环图DAG，之后问从点$1$走到点$n$中，在一定的费用要求下，最多能经过多少个点。并给出经过的点。

## 题解

$n \leq 5000$

我们可以考虑一下二维dp，定义一个dp数组

- $dp[i][j]$代表着在$i$这个点到终点，经过$j$个点所需要花费的最少时间。

之后利用dfs进行更新。因为是深度优先，所以经过的点不用在遍历一遍。

对于记录经过的点，可以用一个二维数组代表，第$j$个点的时候下一个点是什么。

### 错误的思想。 WA14

定义两个数组，一个记录已知这个点到达$n$最少耗-费的时间，一个记录已知这个点到达$n$最多的点数。之后利用这两个数组进行剪枝，但是已知wa14的点，我也不知道为什么。可能是dfs的顺序有关。

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
const
int
int
struct
int
ll val;
}G[maxn];
void
memset
cnt = 1
}
void
G[cnt].to = v;
G[cnt].val = val;
G[cnt].next = head[u];
head[u] = cnt++;
}
int
void
vis[u] = 1
if
for
int
if
rep(j,1
if
dp[u][j+1
bef[u][j+1
}
}
}
}
int
#ifdef
freopen("1.in"
#endif
scanf
init();
memset
rep(i,1
int
addedge(u,v,val);
}
dp[n][1
dfs(1
int
per(i,1
if
printf
idx = i;
break
}
}
printf
int
while
printf
cnt = bef[cnt][idx--];
}
return
}
```

[dp+graph] CodeForces - 721C

https://www.cheasim.com/cf/2019/05/04/dp-graph-CodeForces-721C.html

作者
CheaSim

发布于
2019-05-04

更新于
2019-05-04

许可协议

#[dp](https://www.cheasim.com/tags/dp/)[cf](https://www.cheasim.com/tags/cf/)[graph](https://www.cheasim.com/tags/graph/)




