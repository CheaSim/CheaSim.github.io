# [Codeforces Round #546 (Div. 2)题解]

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2019/03/18/codeforces-round-546-div-2-%E9%A2%98%E8%A7%A3/
发布日期：2019-03-18
更新日期：2019-03-18





# Codeforces Round #546 (Div. 2)

D题题目读错把爷给整自闭了，此篇题解除了D都只有代码了

## A. Nastya Is Reading a Book

### 做法

暴力

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

int
vector
int
#ifdef
freopen("1.in"
#endif
scanf
rep(i,0
int
ve.push_back(r);
}
int
int
printf

return
}
```

## B. Nastya Is Playing Computer Games

### 题解

找规律。 两个一组要六次。

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
int
#ifdef
freopen("2.in"
#endif
int
scanf
int
if
else
int
ans += mmin;
printf

return
}
```

## C. Nastya Is Transposing Matrices

### 题解

只有从左下到右上的有用。找规律。

我写得坐标变换有点绕。

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

int
const
int
int
#ifdef
freopen("3.in"
#endif
scanf
rep(i,0
rep(i,0
bool
n = max(n,m);
rep(i,0
map
rep(j,0
mmp[mx1[i-j][j]]++;
}
rep(j,0
mmp[mx2[i-j][j]]--;
if
}
if
if
}
rep(i,0
map
rep(j,0
mmp[mx1[n-j][i+j]]++;
}
rep(j,0
mmp[mx2[n-j][i+j]]--;
if
}
if
if
}

if
else
return
}
```

## D. Nastya Is Buying Lunch

### 题意

Nastya去排队，队伍中有这样一个规律。

- 已知有$m$对$(i,j)$，他们如果是相邻的话，并且$i$在$j$的前面，那么他们就可以调换位置。

问Nastya能够往前调换多少次位置，已知Nastya在最后一名。

### 题解

一开始我是看错题意，以为是可以隔空调换，直接想着用图论找一个环或者是找一个树来做。没有想到必须要相邻才能换，那么我们就可以这样想，我们的答案最多就只有$Nastya能够往前交换的人的数量$。之后我们尽可能的就是将不能交换的人往前面移动，能交换的人往后面移动。之后由于是一个一个相邻的同学移动，所以如果从前开始尽量往后移动的话，有可能会有的同学到达不到Nasyta的范围了。从后往前交换，那么我们就是将不可换的同学尽量地想前面推，之后如果前面的同学先交换到后面，那么对河Nasyta可以到达的来说，他也是一定能交换到Nasyta到达的点的。

举个栗子:

> 4 4
> 1 2 3 4
> 2 4
> 1 4
> 1 2
> 1 3

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

int
const
int
set
int
int
int
#ifdef
freopen("1.in"
#endif
scanf
rep(i,1
int
a[i] = x; idx[x] = i;
}
rep(i,0
int
st[x].insert(y);
if
}
per(i,1
if
int
while
swap(a[t],a[t+1
t++;
}
}
int
per(i,1
if
ans++;
}
printf
return
}
```

[Codeforces Round #546 (Div. 2)题解]

https://www.cheasim.com/cf/2019/03/18/Codeforces-Round-546-Div-2-%E9%A2%98%E8%A7%A3.html

作者
CheaSim

发布于
2019-03-18

更新于
2019-03-18

许可协议

#[贪心](https://www.cheasim.com/tags/%E8%B4%AA%E5%BF%83/)[cf](https://www.cheasim.com/tags/cf/)




