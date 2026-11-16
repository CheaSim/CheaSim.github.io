# [hdoj6438]Buy and Resell

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/08/27/hdoj6438-buy-and-resell/
发布日期：2018-08-27
更新日期：2018-08-27





# [hdoj6438]Buy and Resell

## 题意

给定$n$个城市和无限制的初始金钱你可以在每个城市里

- 以$a_i$的价格买个商品

- 以$a_i$的价格卖出商品

- 啥都不做

问最多能赚多少钱？

## 题解

贪心 + 数据结构

假设每个城市都卖出商品。那么之前买入的最便宜的商品来卖。对于买卖次数就将假设买入的商品记录为两种

- $1$表示他是之前买入并且在这次卖出

- $2$表示他是没有买卖，直接抵消了。

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
int
ll ans = 0
int
#ifdef
freopen("3.in"
#endif
scanf
while
priority_queue
scanf
rep(i,0
int
pq.push(make_pair
pq.push(make_pair
ll temp = x + pq.top().fi;
if
ans += temp;
pq.pop();
}
printf
}
return
}

```

[hdoj6438]Buy and Resell

https://www.cheasim.com/acm/2018/08/27/hdoj6438-Buy-and-Resell.html

作者
CheaSim

发布于
2018-08-27

更新于
2018-08-27

许可协议

#[贪心](https://www.cheasim.com/tags/%E8%B4%AA%E5%BF%83/)




