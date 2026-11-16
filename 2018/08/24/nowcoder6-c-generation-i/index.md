# nowcoder6 C.Generation I

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/08/24/nowcoder6-c-generation-i/
发布日期：2018-08-24
更新日期：2018-08-24





# Generation I

## 题解

首先放$k$种数字的情况，有$A_n^k$中可能。

由于操作后，前面的球就无法放置,就可以第一个放置该数字的点来确定该结果的区别。相当于将$k$种放在$n$个格子里面。使用隔板法$n\choose k$。

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
const
ll cur,p[maxn],q[maxn],inv[maxn];
ll n,m;
ll C
return
}
ll c
if
if
return
}
void
p[0
for
inv[i] = (mod-mod/i)*inv[mod%i]%mod;
q[i] = q[i-1
p[i] = p[i-1
}
}
int
#ifdef
freopen("j.in"
#endif
init();
scanf
rep(test_case,1
scanf
ll len = min(n,m);
ll ans = 0
cur = 1
for
ans = (ans + (c(m,i)*p[i]%mod)*c(n-1
}
printf
}
return
}
```

nowcoder6 C.Generation I

https://www.cheasim.com/acm/2018/08/24/nowcoder6-C-Generation-I.html

作者
CheaSim

发布于
2018-08-24

更新于
2018-08-24

许可协议

#[组合数学](https://www.cheasim.com/tags/%E7%BB%84%E5%90%88%E6%95%B0%E5%AD%A6/)




