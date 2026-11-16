# codeforces 1600-2200 题目刷

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2019/04/10/codeforces-1600-2200-%E9%A2%98%E7%9B%AE%E5%88%B7/
发布日期：2019-04-10
更新日期：2019-04-10





### F. Graph Without Long Directed Paths

#### 题意

给定一个无向图，里面没有重边也没有circle也就是自反。问把这个无向图变成有向图，怎么变才能使得图中的路径没有超过2的，就是可以穿过两条边的路径。

输出是 每条边是正向还是反向。

#### 题解

一开始想着只能有树的格式，但是其实是找一个偶数环。如果有奇数环就一定无法实现路径小于2，偶数环都可以实现。之后将每个点指定为1或者0。之后如果1到0就把边置为1，0到1就把边置为0。详情请看代码。

#### ac代码

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
struct
int
}G[maxn
codeforces 1600-2200 题目刷

https://www.cheasim.com/1600/2019/04/10/codeforces-1600-2200-%E9%A2%98%E7%9B%AE%E5%88%B7.html

作者
CheaSim

发布于
2019-04-10

更新于
2019-04-10

许可协议

#[cf](https://www.cheasim.com/tags/cf/)




