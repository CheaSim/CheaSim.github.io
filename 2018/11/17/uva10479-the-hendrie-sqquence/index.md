# [uva10479]The Hendrie Sqquence

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/11/17/uva10479-the-hendrie-sqquence/
发布日期：2018-11-17
更新日期：2018-11-17





# The Hendrie Sequence

## 题意

给定一段序列的生成方式，问第$n$个元素是多少。  $0
- $H(1) = 0$

- $H(n) = H(n-1)$中的每个元素$a_i$，那么每个元素就生成一个小子序列$0,0,0,0,0,a_i+1$其中$0$的个数是$a_i$。

- 除了第一个元素之外的所有元素都要进行这种变化

举个例子,

$H(1) = 0$

$H(2) =0,1$     //$0$变成了$0,1$

$H(4) = 0,1,0,2$   //$0$ 变成了$0,1$， $1$变成了$0,2$

$H(8) = 0,1,0,2,1,0,0,3$   //$0$ 变成了$0,1$， $1$变成了$0,2$ ,$2$变成了$0,0,3$

## 题解

找规律，我们可以发现每次都变化之后序列的长度都翻了一倍。所以我们单独把他增长的序列拿出来看。可以用心去发现这样一个规律。

- 定义增长的序列为$b_i$

- $b_i$是由$1$个$b_{i-1}$，$2$个$b_{i-2}$，$3$个$b_{i-3}$，$4$个$b_{i-4}$…$i$个$b_{0}$ ,再加上一个单独的数字$i$。以此类推出来的。

那么我们就可以从第$n$个元素表示在它属于的那次增长中，它排第几个递归到最初的那几个元素中去，要判断一下范围。

由于题目中的数据比较极限，所以能用unsigned long long 还是用unsigned long long 吧。

如果用unsigned long long。一般数据量输入很小 可以用cin很靠谱。但是要把endl换成’\n’还有输入

```cpp
std
cin
```

或者判断他是$2$的几次幂的时候可以这样子判断最高位的$1$在哪里。

```cpp
ll n; int
ll temp = n;
while
dep--;
```

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
ll n;
ll lie[10
ll solve
if
return
}
ll st = 0
rep(i,2
ll temp = pow
if
if
st += temp*(ll)(i-1
}
return
}
int
#ifdef
freopen("4.in"
#endif
std
cin
while
int
n--;
ll tn = n;
while
temp
[uva10479]The Hendrie Sqquence

https://www.cheasim.com/acm/2018/11/17/uva10479-The-Hendrie-Sqquence.html

作者
CheaSim

发布于
2018-11-17

更新于
2018-11-17

许可协议

#[递归](https://www.cheasim.com/tags/%E9%80%92%E5%BD%92/)[规律](https://www.cheasim.com/tags/%E8%A7%84%E5%BE%8B/)




