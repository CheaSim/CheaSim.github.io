# [acm]hash学习笔记

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2019/03/09/acm-hash%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0/
发布日期：2019-03-09
更新日期：2019-03-09





# hash学习

hash是一种比较常见的处理字符串的手法。在acm题目中，经常使用hash来处理字符串。比如判断一个子串在一个字符串中出现过几次。就可以使用hash来处理。

hash主要的方法就是把不同的字符串对应到不同的数字，之后通过数组来确定字符串是否出现过，从而减少检索字符串的时间。

常见的hash方法

```cpp
typedef
ull base[maxn],has[maxn];
void
base[0
rep(i,1
scanf
int
has[len] = 0
per(i,0
}
ull get_hash
return
}
```

## 练习

### hdoj4821 String

题目大意就是求$S$子串中，

- 长为$M*L$

- 其中每一段连续的$L$长度的子串都各不相同。

就是使用hash来做。但是我TLE了。因为暴力了每一段的hash值。

其实由于如果$S$的长度很长的话。其中很多段子段的hash值是被反复求的。所以我们在求完一段$M$个的字符串之后，就可以按照这个把第一段去除。之后选择后一段。这样重复下去。

Wa1:等于号想清楚了在判定。

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
typedef
const
ull xp[maxn],Hash[maxn];
void
xp[0
rep(i,1
}
ull get_Hash
return
}
int
char
int
#ifdef
freopen("1.in"
#endif
init();
// m = length of L
while
scanf
int
Hash[len] = 0
per(i,0
Hash[i] = Hash[i+1
}
int
for
map
for
ull temp = get_Hash(j,m);
mx[temp] ++;
}
if
for
ull temp = get_Hash(j-n*m,m);
mx[temp]--;
if
temp = get_Hash(j,m);
mx[temp]++;
if
}
}
printf
}
return
}
```

### hdoj4080 Stammering Aliens

题目大意是找到字符串$S$中，出现次数大于$m$次并且最长的字符串。

我是用hash做的，不过时间是4800ms，差点超时。用别人后缀数组＋二分，200ms可以过。。

就酱吧。

```cpp
#include
using
#define
#define
#define
#define
typedef
typedef
typedef
const
//head

const
ull base[maxn],has[maxn];
void
base[0
rep(i,1
}
ull get_hash
return
}

int
char
int
map
int
rep(i,0
ull temp = get_hash(i,len);
mx[temp] ++;
if
ans = i;
}
}
return
}
int
int
void
int
while
mid = l+r>>1
int
if
l = mid + 1
res = mid;
right_most = temp;
}else
r = mid - 1
}
}
}
int
#ifdef
freopen("2.in"
#endif
init();
while
scanf
n = strlen
has[n] = 0
per(i,0
right_most = 0
solve(1
if
puts
}else
printf
}
}

return
}
```

reference:

> https://blog.csdn.net/u012965373/article/details/38929637
> https://blog.csdn.net/ck_boss/article/details/47066727

[acm]hash学习笔记

https://www.cheasim.com/%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0/2019/03/09/acm-hash%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.html

作者
CheaSim

发布于
2019-03-09

更新于
2019-03-11

许可协议

#[acm](https://www.cheasim.com/tags/acm/)[hash](https://www.cheasim.com/tags/hash/)




