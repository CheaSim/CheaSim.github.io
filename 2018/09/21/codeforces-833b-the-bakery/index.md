# Codeforces 833B - The Bakery

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/09/21/codeforces-833b-the-bakery/
发布日期：2018-09-21
更新日期：2018-09-21





# Codeforces 833B - The Bakery

## 题意

将一段数字分成最多50个区间，每个区间的价值是区间内不同数字的个数，问怎么样分区间使得价值总和最大。

## 题解

$dp$加线段树。

$dp[i][j]$表示第$j$个坐标分成$i$块最大的价值。

转移方程

- $dp[i][j] = max(dp[i][j],dp[i-1][x] + restofx)$，其中$x$是从1到$j$。

因为每次要获得剩下的x中数字不同的个数，暴力的做法是$O(n^2*k)$，

## ac代码

Codeforces 833B - The Bakery

https://www.cheasim.com/%E7%BA%BF%E6%AE%B5%E6%A0%91/2018/09/21/Codeforces-833B-The-Bakery.html

作者
CheaSim

发布于
2018-09-21

更新于
2018-09-21

许可协议

#[acm](https://www.cheasim.com/tags/acm/)[线段树](https://www.cheasim.com/tags/%E7%BA%BF%E6%AE%B5%E6%A0%91/)[dp](https://www.cheasim.com/tags/dp/)




