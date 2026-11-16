# [pat1139]First Contact 前导零

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2019/08/28/pat1139-first-contact-%E5%89%8D%E5%AF%BC%E9%9B%B6/
发布日期：2019-08-28
更新日期：2019-08-28





# First Contact

## 题意

给定一个图，图中的点只有男的点或者女的点。给定两个不同的点AB，问他们第一个点通过两个不同的点找到第二个点，并且A找到的点和A同性，B连接的点跟B同性，这样的点对有多少对。

## 题解

暴力枚举即可，找到所有相邻的同性点，之后同性点之间有连接就是一对点对。

- wa点 前导零输出，-0000输入

- 中间的点不能是两边的点，必须是不同的四个点

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
map
const
int
int
int
void
char
ch[0
ch[1
ch[2
ch[3
ch[4
int
while
ch[cnt--] = (x%10
x /= 10
}
printf
}
int
int
int
if
rep(i,1
a += pow
}
sign = 1
}else
rep(i,0
a += pow
}
}
return
}
int
#ifdef
freopen("1.in"
#endif
int
scanf
int
rep(i,0
string
int
int
x = trans(a,sign1) ; y = trans(b,sign2);
if
mx[x] = cnt++;
if
idx[mx[x]] = x;
}
if
mx[y] = cnt++;
if
idx[mx[y]] = y;
}
int
int
vis[id1][id2] = vis[id2][id1] = 1
}
int
rep(i,0
int
x = max(-1
y = max(-1
int
vector
if
puts
continue
}
rep(j,1
if
xx.push_back(j);
rep(j,1
if
yy.push_back(j);
vector
for
for
if
ans.push_back(make_pair
}
}
}
sort(ans.begin(),ans.end());
printf
for
output(x.fi); printf
puts
//printf("%d %d\n",x.fi,x.se);
}
}
return
}
```

[pat1139]First Contact 前导零

https://www.cheasim.com/pat/2019/08/28/pat1139-First-Contact-%E5%89%8D%E5%AF%BC%E9%9B%B6.html

作者
CheaSim

发布于
2019-08-28

更新于
2019-08-28

许可协议

#[pat](https://www.cheasim.com/tags/pat/)




