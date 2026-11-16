# 单调队列学习笔记

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/08/28/%E5%8D%95%E8%B0%83%E9%98%9F%E5%88%97%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0/
发布日期：2018-08-28
更新日期：2018-08-28





# 单调队列

## 定义

单调队列，就是指队列中的元素是单调的。

$a_1,a_2,a_3,…,a_n$满足$a1\leq a_2\leq a_3…\leq a_n$的序列便是单调序列。

运用单调队列可以简化问题，由于队列是单调的，那么我们存取最大最小值的复杂度均是$O(1)$。而每一个元素入队一次，出队一次的复杂度也是$O(1)$。

而单调队列和数据结构deque结合较好，如果题目的数据量不是很大，没有卡std，就可以使用deque实现。

## 维护

以单调增序列为例子：

- 如果队列长度一定，先判断队首元素是否在规定范围内，如果超范围就弹出队首。

- 每次加入元素和队尾比较，如果当前元素小于队尾元素并且队列非空，就弹出队尾指针，直到满足单调性为止。

## 例题1 合并果子

(题目太老，只能换个改版的。代码有一定问题，细心的人能看下出来。)

### 题解

建两个单调队列，寻找两个最小值加入其中一个堆中，有点像haffman编码的方式。

```cpp
#include
using
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
int
int
#ifdef
freopen("111.in"
#endif
scanf
rep(i,0
scanf
}
deque
deque
sort(a,a+n);
rep(i,0
ans = 0
int
rep(i,0
if
x = dq1.front();
dq1.pop_front();
}else
x = dq2.front();
dq2.pop_front();
}else
if
x = dq1.front(),dq1.pop_front();
}else
x = dq2.front(),dq2.pop_front();
}
}
if
y = dq1.front();
dq1.pop_front();
}else
y = dq2.front();
dq2.pop_front();
}else
if
y = dq1.front(),dq1.pop_front();
}else
y = dq2.front(),dq2.pop_front();
}
}
ans += (x+y);
dq2.pb(x+y);
}
printf
return
}
```

## 例题2 Sliding Window

### 题解

单调队列+维护一下队头指针不能超过$k$的范围。

由于有最大值和最小值，维护两个单调队列。

需要注意一下的就是如果是手写双向队列的话，我一般是定义

```cpp
int
st = ed = 0
mmax[ed++] = a[0
//判定的时候需要判定ed-1才是指向队尾的值
while
```

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
const
int
int
int
int
int
#ifdef
freopen("12.in"
#endif
scanf
rep(i,0
int
st1 = st2 = ed2 = ed1 = 0
mmax[ed1++] = 0
rep(i,0
while
mmax[ed1++] = i;
while
mmin[ed2++] = i;
}
rep(i,k-1
while
while
mmin[ed2++] = i;
printf
}
rep(i,k-1
while
while
mmax[ed1++] = i;
printf
}
return
}
```

## 例题3 Max Sum of Max-K-sub-sequence

### 题意

给定一个序列，求不超过$k$长的最大连续子段和。

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
int
#ifdef
freopen("11.in"
#endif
scanf
while
scanf
rep(i,0
rep(i,1
deque
int
int
rep(i,1
while
while
dq.push_back(i-1
int
if
ans = temp;
l = dq.front()+1
if
}
}
printf
}
return
}
```

## 例题4 Subsequence

### 题意

给定一段序列，求最长的一段子序列，他的条件是

- 最大和最小值的差不超过$k$也不小于$m$。

### 题解

建立两个单调队列，维护$i$之前最大值的下标和$i$之前最小值的下标。

- 如果最大值最小值超过$k$就弹出下标较小的，并记录较小的位置。

答案是$i-pos$，如果之后的点满足条件了，那么说明$[pos+1,n]$是满足条件的，因为e.g.$a[min[st] 到min[st+1]]$中的元素都大于$a[min[st+1]]$，如果$a[min[st+1]]$满足那么，$a[min[st]+1]$肯定满足条件。

心路历程：我真是太弱了，这就是一道基础的单调队列题目，我想到用两个单调队列来维护，但是对于小于$k$和大于$m$这个条件，不知道怎么去掌控，妈蛋，其实可以靠单调队列的单调性来掌控他们之间的差距。因为一个是递增一个是递减，如果他们之间的差距过大，那么就可以pop掉队首元素，来减少他们的差距，那么大于$m$怎么维护呢？那就是特判他们之间差距是否大于$m$,大于的话就更新一下答案。对于每个$i$就是维护了他之前最大的值的下标和最小值的下标。

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
int
int
#ifdef
freopen("1.in"
#endif
while
rep(i,1
deque
deque
int
rep(i,1
while
dq1.push_back(i);
while
dq2.push_back(i);
while
if
pos = dq1.front(),dq1.pop_front();
else
pos = dq2.front(),dq2.pop_front();
}
if
ans = max(ans,i-pos);
}
printf
}
return
}

```

## 例题5 Trade

### 题意

股票交易

- $i$天你可以以$APi$价格买入股票，$BPi$价格卖出股票

- $i$天最多买$ASi$股，最多卖$BSi$股

- 最多拥有$MaxP$股股票

- 交易后有缓冲期$M$天

开始无限制的钱，问最多能赚多少钱？

### 题解

### AC代码

## 例题6 Cut the Sequence

## 例题7 瑰丽华尔兹

## 例题8 Sequence Partitioning

http://www.voidcn.com/article/p-bcrxdtjx-nd.html

单调队列学习笔记

https://www.cheasim.com/%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0/2018/08/28/%E5%8D%95%E8%B0%83%E9%98%9F%E5%88%97%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.html

作者
CheaSim

发布于
2018-08-28

更新于
2018-10-08

许可协议

#[acm](https://www.cheasim.com/tags/acm/)




