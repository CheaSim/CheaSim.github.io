# Codeforces Round #499 (Div. 2)

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/09/02/codeforces-round-499-div-2/
发布日期：2018-09-02
更新日期：2018-09-02





# Codeforces Round #499 (Div. 2)](http://codeforces.com/contest/1011)

## A. Stages

### 题意

给定一段序列，每个字母代表这一个权值，比如$a$代表$1$。之后问从中挑选出一个序列，要求$a[i]$和$a[i+1]$之间相隔一个字母，问从任意顺序选择$k$个字母，最少可以有多少权值。

### 题解

贪心，其实如果取最大值的话， 我就有点不会了。但是取最小值可以贪心的对所有位置都取能取的最小值。

### AC代码

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
char
int
int
#ifdef
freopen("1.in"
#endif
scanf
scanf
int
rep(i,0
sort(a,a+len);
int
rep(i,0
if
ans +=a[i];
t++;
si = a[i];
}
}
if
printf
}else
puts
}
return
}
```

## B. Planning The Expedition

### 题意

每个人每天都要吃一个特定种类(由你分配)的食物，你现在有$k$种食物，每个食物都有对应的数量，问怎么分配可以在当前食物下过存活尽量多的天数。

### 题解

二分枚举答案(坑爹cf，$m>1
int
if
if
else
else
cout
return
}
cnt = (cnt+1
}
return
}
```

Codeforces Round #499 (Div. 2)

https://www.cheasim.com/cf1500/2018/09/02/Codeforces-Round-499-Div-2.html

作者
CheaSim

发布于
2018-09-02

更新于
2018-09-02

许可协议

#[cf](https://www.cheasim.com/tags/cf/)




