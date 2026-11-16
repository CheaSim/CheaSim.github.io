# [nowcoder3]补题向

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/09/05/nowcoder3-%E8%A1%A5%E9%A2%98%E5%90%91/
发布日期：2018-09-05
更新日期：2018-09-05





## J.Coloring Tree

### 题意

给一棵树，每个节点从$[1,k]$选择一种颜色染。定义树的颜色值为两个相同颜色节点之间的最小值。问如果一棵树的颜色值为$D$，那么它有多少种染色方式。

### 题解

> Reference:https://www.nowcoder.com/discuss/88556?type=101&order=0&pos=1&page=1

### 本地能过就是能过

谁能知道我为啥超时10%有重赏

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
const
struct
int
}G[maxn>=1
}
return
}
ll bfs
queue
ll ans = 0
q.push(make_pair
while
int
if
cnt[u]--;
for
int
if
vis[v] = rt;
q.push(make_pair
}
}
return
}
inline

int
char
bool
while
while
return
}
int
#ifdef
freopen("j.in"
#endif
memset
scanf
rep(i,0
int
add(u,v); add(v,u);
}
ll ans1 = 1
rep(i,1
queue
memset
q.push(1
while
int
ans1 = ans1*bfs(u,D)%mod;
for
int
if
sign[v] = 1
q.push(v);
}
}
rep(i,1
memset
q.push(1
while
int
ans2 = ans2*bfs(u,D+1
for
int
if
sign[v] = 1
q.push(v);
}
}
printf
return
}
```

### 真丶AC代码

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
const
struct
int
}G[maxn
[nowcoder3]补题向

https://www.cheasim.com/acm/2018/09/05/nowcoder3-%E8%A1%A5%E9%A2%98%E5%90%91.html

作者
CheaSim

发布于
2018-09-05

更新于
2018-09-05

许可协议

#[牛客网](https://www.cheasim.com/tags/%E7%89%9B%E5%AE%A2%E7%BD%91/)




