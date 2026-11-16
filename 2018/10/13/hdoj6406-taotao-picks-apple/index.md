# [hdoj6406]Taotao Picks Apple

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/10/13/hdoj6406-taotao-picks-apple/
发布日期：2018-10-13
更新日期：2018-10-13





## Taotao Picks Apples

### 题意

一段序列，从中挑选的子序列是这样规定的

> 能取就取，而且取得数字一定要比上一次取得数字要大。

已知一段序列，问如果改变序列中的一个数字，那么取得数字的个数是多少。

### 题解

每次查询将数组分为两部分$[1,p-1],[p+1,n]$，前半部分的最长长度就是可以通过预处理得到。很容易想到先处理出从头到$i$的最大长度$dl[i]$。然后针对后半段，我们要得到的是置换的$q$，然后大于他的第一个数字到末尾的最大长度。

有一个细节就是，如果置换的数字小于前面最大的数字，那么就是从前面最大的数字到$[p+1,n]$中间大于这个数字的第一个数字开始。

如果置换的数字大于前面最大的数字，那么答案就是$dl([1,p-1])+1+dr([p+1,n])$这个意思。

寻找第一个比该数字大的最前数字用的是线段树。

+1 判断最大值的时候直接用mmax判断，应该用a[x]判断

+1 得到dr数组的时候范围搞错了，应该是[i,n]的范围内比a[i]大的第一个数字。

### ac代码

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
struct
int
void
int
id[rt] = a[x]>a[y]?x:y;
mmax[rt] = max(mmax[rt
[hdoj6406]Taotao Picks Apple

https://www.cheasim.com/acm/2018/10/13/hdoj6406-Taotao-Picks-Apple.html

作者
CheaSim

发布于
2018-10-13

更新于
2018-10-13

许可协议

#[线段树](https://www.cheasim.com/tags/%E7%BA%BF%E6%AE%B5%E6%A0%91/)[数据结构](https://www.cheasim.com/tags/%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84/)




