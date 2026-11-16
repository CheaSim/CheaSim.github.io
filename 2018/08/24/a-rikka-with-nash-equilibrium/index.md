# A. Rikka with Nash Equilibrium

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/08/24/a-rikka-with-nash-equilibrium/
发布日期：2018-08-24
更新日期：2018-08-24





# A. Rikka with Nash Equilibrium

## 题解：

神仙dp题

将数字从大到小一次排列，从大往小取.

- 构造一个三维$dp[now][j][k]​$,表示放入$now​$数字的时候有$i​$行和$j​$列有数字下的情况。为了防止数字成为平衡位置，每次放置的位置都要放置在之前放置元素所在的列或者行上，如果不这么放置的话，他就会成为剩下当前行和当前列最大的(就没能有比他大的数字了)。

- 初始化，因为第一个数字可以任意存放所以$dp[0][1][1]=m*n$。

- 转移方程:

该点放置位置上行和列都有元素，那就是有$i$列和$j$行可以存放。剩下的位置是$j*k-i+1$
，$dp[next][j][k]+=dp[now][j][k]*(jk-i+1)$

- 该点放置位置上列已经有元素了，但是行上没有元素，从位置的行数减一转移加了一行$dp[next][j][k]+=dp[now][j-1][k]*j(n-i+1)$

- 同理如果行有元素的话。$dp[next][j][k]+=dp[now][j][k-1]*i(m-j+1)$

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
ll mod;
ll dp[2
inline
return
}
inline
return
}
int
#ifdef
freopen("a.in"
#endif
scanf
while
scanf
memset
dp[0
int
rep(i,2
int
memset
rep(j,0
rep(k,0
if
ll tot = j*k - i + 1
dp[nxt][j][k] = add(dp[nxt][j][k],dp[now][j][k]*tot);
dp[nxt][j+1
dp[nxt][j][k+1
//cout
A. Rikka with Nash Equilibrium

https://www.cheasim.com/acm/2018/08/24/A-Rikka-with-Nash-Equilibrium.html

作者
CheaSim

发布于
2018-08-24

更新于
2018-08-30

许可协议

#[acm](https://www.cheasim.com/tags/acm/)




