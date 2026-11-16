# codeforcesPoints

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/08/18/codeforcespoints/
发布日期：2018-08-18
更新日期：2018-08-18





# codeforcesPoints

#### 题意

给出几个点，让你求出在某个点的右边和上面最接近他的点是哪一个点。

#### 题解

线段树+set应用

对$x$进行离散化处理，对于每一个$x$进行建一个set，用线段树维护$x$之间的$y$的最大值。对于给出点的右上点，我们可以用二分来set搜索，还有在线段树中优先搜索左边靠近给出点的点。

这是我第一次看到离散化的线段树应用。哭泣

```cpp
#include
using
#define
#define
#define
#define
#define
#define
typedef
typedef
const
inline
//head
const
int
set
int
char
vector
void
if
maxy[rt] = -1
return
}else
int
build(lson);
build(rson);
}
}
void
maxy[rt] = Max(maxy[rt
codeforcesPoints

https://www.cheasim.com/cf1500/2018/08/18/codeforcesPoints.html

作者
CheaSim

发布于
2018-08-18

更新于
2018-08-18

许可协议




