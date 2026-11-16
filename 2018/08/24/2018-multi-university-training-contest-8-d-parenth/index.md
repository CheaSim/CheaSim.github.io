# 2018 Multi-University Training Contest 8 D.Parenth

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/08/24/2018-multi-university-training-contest-8-d-parenth/
发布日期：2018-08-24
更新日期：2018-08-24





# 2018 Multi-University Training Contest 8 D.Parentheses Matrix

传送门

## 题目大意

一个由左括号和右括号组成的矩阵，定义矩阵的权值是矩阵中匹配的行数和列数的和。

## 题解

一道比较典型的构造题。

如果行数或者列数是奇数那么矩阵显然是奇数的行或列匹配不了。

> (())
> (())
> (())

当情况很多有两个变量的时候我们可以假设一个变量小于另一个变量，假设$h\leq m$。

构造过程还是题解比较清晰。

首先，第一行、最后一列中最多只有一个能够匹配，第一列、最后一行也只有一个能够匹配（考 虑右上角和左下角的括号选取方法），故答案不会超过 w+h−2。 当 h = 2 时，每一列可以构造一对匹配，这样答案已经到达上界。 当 h = 4 时，可以如下构造：

> ( ( ( ( ( (
> ) ) ) ) ) )
> ( ( ( ( ( (
> ) ) ) ) ) )

这样答案是 w+h−3。

若存在更优的答案，则必有一个边界能够匹配，不妨设是第一列。这样，就已 经有除第一行以外的两行（右括号开头的行）不匹配了，而第一行和最后一列中至少有一个不匹配， 因此最优解不会超过 w+h−3。

当 h≥6 时，可以如下构造：

> ( ( ( ( ( ( ( (
> ( ) ( ) ( ) ( )
> ( ( ) ( ) ( ) )
> ( ( ( ( ) ) ) )
> ( ( ) ( ) ( ) )
> ) ) ) ) ) ) ) )

答案是 w+h−4。同理可证明不存在更优的方法。

在实际操作的时候如果$h>m$可以将矩阵反转一下。就ok了。

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
char
int
#ifdef
freopen("d.in"
#endif
scanf
while
bool
scanf
if
rep(i,0
rep(j,0
g[i][j] = (j
2018 Multi-University Training Contest 8 D.Parenth

https://www.cheasim.com/acm/2018/08/24/2018-Multi-University-Training-Contest-8-D-Parenth.html

作者
CheaSim

发布于
2018-08-24

更新于
2018-08-24

许可协议

#[acm](https://www.cheasim.com/tags/acm/)




