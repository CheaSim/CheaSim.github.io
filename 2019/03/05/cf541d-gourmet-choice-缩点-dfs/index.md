# [cf541D]Gourmet choice (缩点+dfs)

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2019/03/05/cf541d-gourmet-choice-%E7%BC%A9%E7%82%B9-dfs/
发布日期：2019-03-05
更新日期：2019-03-05





# Gourmet choice

## 题意

给定$n$个蛋糕和$m$个蛋糕，和他们之间的大小关系。问给所有的蛋糕一个可能最小的值，使得关系成立。

## 题解

首先由于有$=$的存在，有一些蛋糕的值是要一样的。所以我们需要把题目中的相等的点给缩到一起。

之后用dfs把值给确定下来。

其中缩点用到的技巧很厉害。

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
vector
// m is behind of the n
int
int
return
}
void
int
int
if
}
int
char
int
// flag means the 矛盾
bool
int
void
if
dp[x] = max(dp[x],dep);
for
if
flag = true
return
}
if
vis[to] = 1
dfs(to,dep+1
vis[to] = 0
}
}
}
int
#ifdef
freopen("1.in"
#endif
scanf
rep(i,0
scanf
}
rep(i,0
rep(i,0
rep(j,0
if
Union(i,n+j);
rep(i,0
int
if
e[x].push_back(y);
ind[y] ++;
use[x] = 1
}else
e[y].push_back(x);
ind[x] ++;
use[y] = 1
}else
use[x] = 1
}
}
bool
rep(i,0
if
fflag = true
vis[i] = 1
dfs(i,1
vis[i] = 0
}
}
if
puts
}else
puts
rep(i,0
puts
rep(i,n,m+n) printf
}
return
}
```

[cf541D]Gourmet choice (缩点+dfs)

https://www.cheasim.com/cf/2019/03/05/cf541D-Gourmet-choice-%E7%BC%A9%E7%82%B9-dfs.html

作者
CheaSim

发布于
2019-03-05

更新于
2019-03-05

许可协议

#[缩点](https://www.cheasim.com/tags/%E7%BC%A9%E7%82%B9/)[dfs](https://www.cheasim.com/tags/dfs/)




