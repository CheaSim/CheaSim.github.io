# 第十届蓝桥杯题解

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2019/03/29/%E7%AC%AC%E5%8D%81%E5%B1%8A%E8%93%9D%E6%A1%A5%E6%9D%AF%E9%A2%98%E8%A7%A3/
发布日期：2019-03-29
更新日期：2019-03-29





# 第十届蓝桥杯题解(个人向)

## 第一题 平方和

算$1 ​$到$2019​$中含有$2,0,1,9​$的数的平方和。

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

bool
while
int
x /= 10
if
}
return
}
int
#ifdef
freopen("1.in"
#endif
ll ans = 0

rep(i,1
if
}
printf
return
}
```

## 第二题 数列求值

求类似斐波那契数列$f[i] = f[i-1] + f[i-2] + f[i-3]$ ，求$f[20190324]%10000$。

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
#ifdef
freopen("1.in"
#endif
a[0
a[1
a[2
rep(i,3
a[3
rep(j,0
}
printf
return
}
```

## 第三题 最大降雨量

答案34.贪心即可。注意中位数的中位数

## 第四题 迷宫

## 第九题 糖果

### 题意

有n袋糖，里面有m种糖，每袋糖有k个，问至少取几包才能攒够所有种类的糖。

$n \leq 100;m,k\leq 20​$

### 题解

状压dp。我场上直接上暴力了。但是场下经过队友提示，发现就是个简单的状压dp。

因为他的$m$低于20所以我们可以用二进制位来表示。总的复杂度$O(2^m *n)$

状态转移方程 $dp[S|i] = min(dp[S|i],dp[i]+1)$

### 可能ac的代码

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
int
#ifdef
freopen("1.in"
#endif
scanf
rep(i,0
rep(j,0
int
dp[i] |= (1
}
}
rep(i,0
dp[0
for
rep(j,0
dp[i|sta[j]] = min(dp[i]+1
}
}
printf
return
}
```

第十届蓝桥杯题解

https://www.cheasim.com/%E8%93%9D%E6%A1%A5%E6%9D%AF/2019/03/29/%E7%AC%AC%E5%8D%81%E5%B1%8A%E8%93%9D%E6%A1%A5%E6%9D%AF%E9%A2%98%E8%A7%A3.html

作者
CheaSim

发布于
2019-03-29

更新于
2019-03-29

许可协议

#[蓝桥杯](https://www.cheasim.com/tags/%E8%93%9D%E6%A1%A5%E6%9D%AF/)




