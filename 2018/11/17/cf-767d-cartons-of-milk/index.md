# [cf-767D]Cartons of milk

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/11/17/cf-767d-cartons-of-milk/
发布日期：2018-11-17
更新日期：2018-11-17





# Cartons of milk

## 题意

每天喝$k$瓶牛奶，每瓶牛奶都有$s$的保质日期，现在我有$n$瓶牛奶，去商场最多可以买多少瓶牛奶。

条件是每天都要喝$k$瓶牛奶，在最有情况下所有牛奶都不会过期。

## 题解

贪心，反正所有牛奶的贡献都是1，所以保质期越后面的越好。

计算能买多少瓶就是从第一天开始遍历，能买到就买对应的期限的牛奶。

+1： 中间一个变量爆了int

+1: 有两个变量$n,m$，sort的时候用了$n$，应该用$m$。

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
int
const
const
int
int
struct
int
int
bool
return
}
}a[maxn];
int
#ifdef
freopen("3.in"
#endif
scanf
bool
rep(i,0
int
vis[x]++;
}
rep(i,0
int
mx[x]++;
a[i].val = x; a[i].id = i+1
}
sort(a,a+m);
int
ll  now = k;
rep(i,0
if
flag = true
break
}else
int
int
ans += temp;
now += k-t;
}
}
if
else
printf
rep(i,0
printf
}
puts
}

return
}
```

[cf-767D]Cartons of milk

https://www.cheasim.com/acm/2018/11/17/cf-767D-Cartons-of-milk.html

作者
CheaSim

发布于
2018-11-17

更新于
2018-11-17

许可协议

#[贪心](https://www.cheasim.com/tags/%E8%B4%AA%E5%BF%83/)




