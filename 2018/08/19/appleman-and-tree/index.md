# Appleman_and_Tree

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/08/19/appleman-and-tree/
发布日期：2018-08-19
更新日期：2018-08-19





# Appleman and Tree

链接

如果觉得我的题解看不懂可以去看 大佬的题解

### 题目大意

将一颗树节点染成白色或者黑色，减去几条变使得每个联通分支都有一个黑色节点，问有多少种减边方案。

### 题解

树状dp+dfs

下次看到两种状态加点的。dp应该想到用2维。

- 定义$dp[i][j]$表示点$i$在以点$i$为根的子树去掉点$i$所在的联通快有黑点$1$和无黑点$0$的方案数

- 假设点$u$，首先如果$u$是黑色，那么$$dp[i][1]=1$$，否则$dp[i][0]=1$。
点$u$加入一个子树$v$。假设原来$u$没有黑点。
如果加入的$v$是有黑点的，有两种选择，切断边$u$还是没有黑点，方案数$dp[u][0]=dp[u][0]*dp[v][1]$，不切断边$u$就产生了黑点$dp[u][1]=dp[u][0]*dp[v][1]$

- 如果加入的$v$是无黑点的，只能选择不切断。方案数$dp[u][0]=dp[u][0]*dp[v][0]$

- 点$$u$$加入一个子树$v$。假设原来$u$有黑点。
如果加入的$v$是有黑点的，只能选择切断，方案数$dp[u][1]=dp[u][1]*dp[v][1]$

- 如果加入的点$v$是无黑点的，只能选择切断，因为不能产生无黑点的联通分支，方案数$dp[u][1]=dp[u][1]*dp[v][0]$

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
}G[maxn
Appleman_and_Tree

https://www.cheasim.com/acm/2018/08/19/Appleman-and-Tree.html

作者
CheaSim

发布于
2018-08-19

更新于
2018-08-19

许可协议

#[dptree](https://www.cheasim.com/tags/dptree/)




