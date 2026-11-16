# [hdoj2260]Difficulty control(dfs)

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2019/03/06/hdoj2260-difficulty-control-dfs/
发布日期：2019-03-06
更新日期：2019-03-06





# Difficulty Control

## 题意

中文题目不说了。

## 题解

dfs+剪枝

- 剩下的加不到最优值剪掉

- 已经加过了最优值剪掉

我在大二的时候TLE了20次的题目终于在队友的指导之下完成了。

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

ll n,m;
const
ll num[maxn];
vector
ll ans = INT_MAX;
int
int
void
if
ans = abs
memcpy
}
ll tt = 0
if
rep(i,x,n) tt += num[ve[i]];
if
if
return
}
temp[ve[x]] = 1
dfs(x+1
temp[ve[x]] = 0
dfs(x+1
}
int
#ifdef
freopen("1.in"
#endif
while
ve.clear();
memset
memset
rep(i,0
ll x; char
ve.push_back(ch-'A'
num[ch-'A'
}
sort(ve.begin(),ve.end());
ans = INT_MAX;
dfs(0
vector
rep(i,0
int
printf
rep(i,0
printf
}
}
return
}
```

[hdoj2260]Difficulty control(dfs)

https://www.cheasim.com/dfs/2019/03/06/hdoj2260-Difficulty-control-dfs.html

作者
CheaSim

发布于
2019-03-06

更新于
2019-03-06

许可协议

#[dfs](https://www.cheasim.com/tags/dfs/)




