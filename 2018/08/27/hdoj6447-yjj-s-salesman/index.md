# [hdoj6447] YJJ's Salesman

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/08/27/hdoj6447-yjj-s-salesman/
发布日期：2018-08-27
更新日期：2018-08-27





# [hdoj6447] YJJ’s Salesman

## 题意

给定一个地图，只能向右或者向上走，地图上有很多点，有以下条件

- 每个点有钱$val$

- 你只能从该点的左下方进入点才可以拿钱。

问最多能获得多少钱。

## 题解

dp + 树状数组优化

单dp就是$O(n^2)$的复杂度。但是题目数据范围$1e5$所以不行。只有树状数组优化了。

树状数组处理的是$dp[i]$代表着以$i$点为重点的权值。

并且由于$x,y$范围是$1e9$所以必须离散化。

有一步我看了好久代码才看懂。在dp方程转移的时候，先对于$x$进行排列，之后在之后更大的$x$再更新之后的dp数组，保证每一次update的dp数组都是最优的。

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
struct
int
bool
return
}
}a[maxn];
int
int
int
return
}
void
for
}
int
int
for
s = max(s,bit[i]);
}
return
}
int
#ifdef
freopen("2.in"
#endif
scanf
while
vector
memset
scanf
rep(i,0
int
a[i].x = x;a[i].y = y;a[i].val = v;
}
rep(i,0
sort(v.begin(),v.end());
sort(a,a+n);
v.erase(unique(v.begin(),v.end()),v.end());
tot = v.size();
rep(i,0
rep(i,0
int
rep(i,0
while
update(a[pos].y,dp[pos]);
pos ++;
}
dp[i] = query(a[i].y-1
ans = max(ans,dp[i]);
}
printf
}
return
}
```

[hdoj6447] YJJ's Salesman

https://www.cheasim.com/acm/2018/08/27/hdoj6447-YJJ-s-Salesman.html

作者
CheaSim

发布于
2018-08-27

更新于
2018-08-27

许可协议

#[dp](https://www.cheasim.com/tags/dp/)




