# [hdoj1556]Color the ball

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/08/30/hdoj1556-color-the-ball/
发布日期：2018-08-30
更新日期：2018-08-30





# Color the ball

## 题意

给定$n$次操作，吧$l,r$区间内+1，最后问每个点是多少。

## 题解

树状数组骚操作。

既然我单点更新只能更新一个点，那么我就更新$l$点加上1，之后$r+1$的点减1，那么我对于在区间中的点，求得就是他之前$l$出现的次数。

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
void
for
bit[i] += val;
}
}
int
int
for
res += bit[i];
}
return
}
int
#ifdef
freopen("3.in"
#endif
while
memset
rep(i,0
int
update(a,1
}
rep(i,1
printf
}
}
return
}
```

[hdoj1556]Color the ball

https://www.cheasim.com/acm/2018/08/30/hdoj1556-Color-the-ball.html

作者
CheaSim

发布于
2018-08-30

更新于
2018-08-30

许可协议

#[树状数组](https://www.cheasim.com/tags/%E6%A0%91%E7%8A%B6%E6%95%B0%E7%BB%84/)




