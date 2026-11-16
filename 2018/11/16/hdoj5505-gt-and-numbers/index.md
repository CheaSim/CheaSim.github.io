# [hdoj5505]GT and numbers

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/11/16/hdoj5505-gt-and-numbers/
发布日期：2018-11-16
更新日期：2018-11-16





# GT and numbers

## 题意

题目意思比较绕，就是给定一个$N$和$M$问至少要多少次下列的操作可以使得$N$等于$M$。

- 将N乘上一个它的因子(注意$N$也会变)。

## 题解

由于我们要求$N$转化成$M$，那么其实就是他们的素因子变成相同。

$N = 2^{a_1} * 3^{a_2}5^{a_3}…$

$M = 2^{b_1}*3^{b_2}5^{b_3}…$

那么我们就可以看出 如果要让$a_1=b_1,a_2=b_2,a_3=b_3…$我们需要在他们差距最大的那个素因子中他们相差的倍数的。

$log_2(倍数)$

> tip 由于2e63 爆了long long 。所以要用unsigned long long。

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

int
bool
void

memset
isprime[1
for
{
if
for
{
isprime[i*prime[j]]=false
if
}
}
}
int
#ifdef
freopen("1.in"
#endif
int
getlist(4000000
while
scanf
ll ans = 0
bool
for
ll cnt1= 0
ll t = prime[i];
while
while
if
flag = true
break
}
if
ll temp = cnt2/cnt1;
if
ans = max(temp,ans);
}
if
if
puts
}else
if
puts
continue
}
ll temp = 1
int
while
printf
}
}
return
}
```

[hdoj5505]GT and numbers

https://www.cheasim.com/acm/2018/11/16/hdoj5505-GT-and-numbers.html

作者
CheaSim

发布于
2018-11-16

更新于
2018-11-16

许可协议

#[模拟](https://www.cheasim.com/tags/%E6%A8%A1%E6%8B%9F/)[数学](https://www.cheasim.com/tags/%E6%95%B0%E5%AD%A6/)




