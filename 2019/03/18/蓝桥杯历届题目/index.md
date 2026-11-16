# 蓝桥杯历届题目

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2019/03/18/%E8%93%9D%E6%A1%A5%E6%9D%AF%E5%8E%86%E5%B1%8A%E9%A2%98%E7%9B%AE/
发布日期：2019-03-18
更新日期：2019-03-18





# 还有6天蓝桥杯了

开始刷历届练习题了。

## 小计算器

### 题意

实现一个直接的计算器。没有四则运算规则优先级。并且能够有进制转换

### 题解

数字转换字符串的时候,$0$是关键点。

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
typedef
const
//head
int
const
const
char
int
char
void
memset
ull t = k;
int
if
while
if
ans[cnt++] = x%t+'0'
}else
ans[cnt++] = x%t+'A'
}
x/=t;
}
int
rep(i,0
}
char
ull real_num
int
ull t = 0
ull cnt = 1
per(i,0
if
t += cnt * (tt[i] - 'A'
}else
t += cnt * (tt[i] - '0'
}
cnt*= k;
}
return
}
int
#ifdef
freopen("1.in"
#endif
cin
ull now = 0
int
k = 10
bool
rep(i,0
cin
if
now = 0
init = true
}else
cin
ull temp = real_num();
if
now = temp;
init = false
continue
}
if
else
else
else
else
}else
sign = 1
}else
sign = 2
}else
sign = 3
}else
sign = 4
}else
sign = 5
}else
solve(now);
cout
}else
cin
}
}
return
}
```

## 合根植物

### 题意

并查集

数组开小了。

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
if
else
}
int
int
if
}
int
int
int
#ifdef
freopen("2.in"
#endif
scanf
rep(i,1
rep(i,0
int
Union(x,y);
}
int
rep(i,1
printf
return
}
```

蓝桥杯历届题目

https://www.cheasim.com/%E8%93%9D%E6%A1%A5%E6%9D%AF/2019/03/18/%E8%93%9D%E6%A1%A5%E6%9D%AF%E5%8E%86%E5%B1%8A%E9%A2%98%E7%9B%AE.html

作者
CheaSim

发布于
2019-03-18

更新于
2019-03-18

许可协议

#[蓝桥杯](https://www.cheasim.com/tags/%E8%93%9D%E6%A1%A5%E6%9D%AF/)




