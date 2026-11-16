# [HDOJ5592] ZYB's Premutation

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/09/18/hdoj5592-zyb-s-premutation/
发布日期：2018-09-18
更新日期：2018-09-18





# [HDOJ5592] ZYB’s Premutation

## 题意

ZYB有一个序列所有的逆序数前缀和，$a_1,a_2,a_3,…,a_n$，他们各个都表示从1到$i$的逆序数的前缀和。

## 题解

树状数组+二分

首先我们可以倒着看，对于最后一个数字，他的逆序数减前面的逆序数就代表着前面大于他的个数。所以我们就可以把问题转化为，已知数字$a_i$在前$i$个中的位置，求$a_i是多少。

我们可以用树状数组来维护，$sum(i)$表示到$i$代表着$i$是第几个数字，每当一个数字用过之后，他后面的数字都要-1，因为他们的排序相当于减少了一个，第四个数字变成第三个数字。

+n 没有想到这个序列是单调的，所以可以二分。居然想的是怎么让整个数组往前挪。

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
const
int
int
int
return
}
int
for
bit[i] += val;
}
}
int
int
for
s += bit[i];
}
return
}
int
int
while
int
int
if
r = mid-1
ans = mid;
}else
l = mid+1
}
}
return
}
int
#ifdef
freopen("2.in"
#endif
scanf
while
scanf
memset
memset
rep(i,1
rep(i,1
rep(i,1
per(i,1
int
ans[i] = solve(1
add(ans[i],-1
}
rep(i,1
printf
}
}
return
}
```

[HDOJ5592] ZYB's Premutation

https://www.cheasim.com/acm/2018/09/18/HDOJ5592-ZYB-s-Premutation.html

作者
CheaSim

发布于
2018-09-18

更新于
2018-09-18

许可协议

#[树状数组，hdoj](https://www.cheasim.com/tags/%E6%A0%91%E7%8A%B6%E6%95%B0%E7%BB%84%EF%BC%8Chdoj/)




