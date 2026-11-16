# [cf-767b]The Queue

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/11/17/cf-767b-the-queue/
发布日期：2018-11-17
更新日期：2018-11-17





# The Queue

## 题意

题意有点复杂，懒得写了。

## 题解

贪心。

注意的点就是，可以在还没有开始就进入队列进行排队，所以计算的时候虽然是一样的，但还是要注意一下。

特殊情况就是对于在ed以后的人来说，他们就不算了，不算人。

+1 p数组 忘记开long long了。

+1 如果加入时间超过进入时间了就不行了。

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
ll st,ed,t;
int
const
ll p[maxn];
int
#ifdef
freopen("4.in"
#endif
scanf
scanf
rep(i,0
ed -= st;
ll ans = 1e13
ll wait = 1e14
int
rep(i,0
if
cnt++;
if
ans = p[i]-1
cout
return
}else
ll temp = (ll)(i)*t - p[i];
if
wait = temp;
ans = p[i]-1l
}
}
}
ll temp = (ll)(cnt+1
printf

return
}
```

[cf-767b]The Queue

https://www.cheasim.com/acm/2018/11/17/cf-767b-The-Queue.html

作者
CheaSim

发布于
2018-11-17

更新于
2018-11-17

许可协议

#[贪心](https://www.cheasim.com/tags/%E8%B4%AA%E5%BF%83/)[范围](https://www.cheasim.com/tags/%E8%8C%83%E5%9B%B4/)




