# [hdoj4614]Vases and Flowers

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/09/07/hdoj4614-vases-and-flowers/
发布日期：2018-09-07
更新日期：2018-09-07





# Vases and Flowers

## 题意

Alice去一排$n$的花盆中种花，有两种操作

- 从$a$开始种花，如果该花盆有花就跳到下一个花盆。直到没有花种或者到了$n$盆

- $[a,b]$区间的所有花都扔掉。

询问

- 1操作中开始种花的盆和停止种花的盆

- 2操作中丢掉的花

## 题解

线段树，$sum$表示花的个数，用$lazy$来懒惰标记。

妈的，我线段树还是不够熟悉，居然使用了$update(p,n,1)$这样子的形式，以为每个区间的$rt$都是随机的，其实线段树的区间都是固定的，你只能通过$lson,rson$来寻找每一个区间，不能自己xjb改区间。

寻找p开始位置的时候，需要思考一下。image一下中点和左端与p的关系就好了。

## AC代码

```cpp
#include
using
#define
#define
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
bool
int
void
sum[rt] = sum[rt
[hdoj4614]Vases and Flowers

https://www.cheasim.com/%E7%BA%BF%E6%AE%B5%E6%A0%91/2018/09/07/hdoj4614-Vases-and-Flowers.html

作者
CheaSim

发布于
2018-09-07

更新于
2018-09-07

许可协议

#[线段树](https://www.cheasim.com/tags/%E7%BA%BF%E6%AE%B5%E6%A0%91/)




