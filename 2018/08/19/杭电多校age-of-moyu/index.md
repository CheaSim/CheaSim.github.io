# 杭电多校Age_of_Moyu

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/08/19/%E6%9D%AD%E7%94%B5%E5%A4%9A%E6%A0%A1age-of-moyu/
发布日期：2018-08-19
更新日期：2018-08-19





# Age of Moyu

#### 题解

标程的set+bfs貌似有漏洞。

```cpp
5
1
2
3
4
1
1
```

这个数据就可以hack掉了。

所以我果断copy了dls队伍的代码。(用边做)

```cpp
#include
#include
#include
#include
#include
#include
using
inline

return
}
inline

char
while
ch = inputchar();
ret = ch - '0'
ch = inputchar();
while
{
ret = ret * 10
ch = inputchar();
}
}
const
int
class
{
public
int
}e[MAXM * 2
int
int
deque
void

int
//    scanf("%d%d%d", &u, &v, &c);
inputnum(u);
inputnum(v);
inputnum(c);
e[++en].to = v;
e[en].c = c;
e[en].next = head[u];
head[u] = en;
e[++en].to = u;
e[en].c = c;
e[en].next = head[v];
head[v] = en;
}
bool

if
return
memset
en = 1
for
insert();
memset
for
dis[i / 2
while
{
int
q.pop_front();
for
if
{
if
dis[i / 2
}
else
{
if
dis[i / 2
}
for
if
{
if
dis[i / 2
}
else
{
if
dis[i / 2
}
}
int
for
if
ans = dis[i / 2
if
ans = -1
printf
return
}
int

#ifdef
freopen("a.in"
#endif
while
return
}
```

时间卡的非常紧。优化了很多终于2.4s过了。

$$O(n^2)$$

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
void
char
for
for
}
const
int
int
struct
int
}G[maxn
杭电多校Age_of_Moyu

https://www.cheasim.com/acm/2018/08/19/%E6%9D%AD%E7%94%B5%E5%A4%9A%E6%A0%A1Age-of-Moyu.html

作者
CheaSim

发布于
2018-08-19

更新于
2018-08-19

许可协议

#[hdoj](https://www.cheasim.com/tags/hdoj/)




