# [cf545]A-D题解

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2019/03/09/cf545-a-d%E9%A2%98%E8%A7%A3/
发布日期：2019-03-09
更新日期：2019-03-09





# Codeforces Round #545 (Div. 2)

ps 小生不才，比赛时只做出3道。后面补了一道。

## Sushi for Two

### 题意

给定一个只含有1或者2的数组，让你找出一个子数组，子数组要求是$n个1 和 m个2$并要求$min(n,m)$最大。

### 题解

暴力模拟.

### ac代码

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
int
#ifdef
freopen("1.in"
#endif
vector
int
int
int
rep(i,0
int
while
cnt1= 0
cnt2 = 0
while
cnt++;
cnt1++;
}
ve.push_back(cnt1);
while
cnt++;
cnt2++;
}
ve.push_back(cnt2);
}
int
rep(i,0
ans = max(ans,2
}
printf
return
}
```

## Circus

### 题意

给定$n$个人，其中每个人可能会表演小丑也可能会表演杂技演员。要求把$n$个人分成两堆。要求

- 第一队只能表演小丑，第二队只能表演杂技演员

- 第一队中小丑的个数和第二队中杂技演员的个数相等

- 两队的人数相同。

### 题解

暴力枚举，因为人可以分为四类。所以我们可以枚举出其中两类的分配，之后通过条件舍掉一些答案，得到正确答案。

### ac代码

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
int
int
int
int
int
int
int
#ifdef
freopen("1.in"
#endif
scanf
rep(i,0
scanf
}
rep(i,0
vector
rep(j,0
sort(ve.begin(),ve.end());
rep(j,0
if
}
}
rep(j,0
vector
rep(i,0
sort(ve.begin(),ve.end());
rep(i,0
if
}
}
rep(i,0
vector
rep(j,0
sort(ve.begin(),ve.end());
auto
ve.erase(iter,ve.end());
rep(j,0
}
rep(j,0
vector
rep(i,0
sort(ve.begin(),ve.end());
auto
ve.erase(iter,ve.end());
rep(i,0
}
rep(i,0
int
int
int
if
temp = max(m - cnt_row[i], n + abs
}else
temp = max(n - cnt_col[j], m + abs
}
ans[i][j] = temp;
}
rep(i,0
printf
}

return
}
```

## C. Skyscrapers

### 题意

较为简单，自己看吧。

### 题解

离散化+一些技巧。

因为横竖上最大值会因为中间而改变，所以答案是在

$$max(n-cnt[i],m+abs(x-y)-cnt[j])$$

中产生的。其中$cnt[i]$表示行的重复个数，$cnt[j]$表示列的重复个数。$x,y$表示在行和列中的排名。

我做的有一点烦

### ac代码

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
int
int
int
int
int
int
int
#ifdef
freopen("1.in"
#endif
scanf
rep(i,0
scanf
}
rep(i,0
vector
rep(j,0
sort(ve.begin(),ve.end());
rep(j,0
if
}
}
rep(j,0
vector
rep(i,0
sort(ve.begin(),ve.end());
rep(i,0
if
}
}
rep(i,0
vector
rep(j,0
sort(ve.begin(),ve.end());
auto
ve.erase(iter,ve.end());
rep(j,0
}
rep(j,0
vector
rep(i,0
sort(ve.begin(),ve.end());
auto
ve.erase(iter,ve.end());
rep(i,0
}
rep(i,0
int
int
int
if
temp = max(m - cnt_row[i], n + abs
}else
temp = max(n - cnt_col[j], m + abs
}
ans[i][j] = temp;
}
rep(i,0
printf
}

return
}
```

## D. Camp Schedule

### 题意

给定两串字符串$s,t$。要求把$s$重新排列使得$s$中的子串里，$t$出现的次数尽可能多。

### 题解

kmp

我们可以想象一下，如果要$s$中要有尽量多的$t$，那么首先我们在$s$的最前面是一个$t$。之后我们需要加入后续的数字，使得尽可能多的像$t$。这和kmp的思想是很相似的。就是我们在最后一个字母失配之后，我们应该跳转到的那个字母开始，继续匹配就可以匹配成一个字符串了。

举个栗子吧。

> 111000
> 101

这个例子中，我们先在$s$的前面放一个$101$。

之后我们需要配一个字母，使得尽量减少失配的字符串的长度，所以我们加入$len[next]$，也就是$0$。之后我们加入$1$形成了$10101$这样就产生了两个$t$。之后我们模拟这样子的行为就可以了。

### ac代码

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
char
int
void
int
int
nxt[0
while
if
i++,j++;
nxt[i] = j;
}else
j = nxt[j];
}
}
}
int
#ifdef
freopen("1.in"
#endif
scanf
getnxt(t);
int
int
int
int
rep(i,0
if
else
}
int
bool
while
for
if
else
else
flag = false
}
}
i = nxt[len];
}
while
while
return
}
```

[cf545]A-D题解

https://www.cheasim.com/cf/2019/03/09/cf545-A-D%E9%A2%98%E8%A7%A3.html

作者
CheaSim

发布于
2019-03-09

更新于
2019-03-09

许可协议

#[cf](https://www.cheasim.com/tags/cf/)




