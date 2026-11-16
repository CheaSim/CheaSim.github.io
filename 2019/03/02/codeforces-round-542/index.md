# Codeforces Round #542

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2019/03/02/codeforces-round-542/
发布日期：2019-03-02
更新日期：2019-03-02





# Codeforces Round #542

## A. Be Positive

### 题意

给定一个数组$a_1,a_2,…,a_n$，让你到一个数字，是的数组内的所有数字处以这个数字之后，数组内大于0的数字超过$\cfrac{n}{2}$的上界。

### 题解

由于没有要求整除，所以直接看负数多还是正数多，哪个超过上届，就用$-1或者1$

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
int
const
int
int
#ifdef
freopen("1.in"
#endif
scanf
int
rep(i,0
scanf
if
if
}
int
if
if
if
printf
return
}
```

## B. Two Cakes

### 题意

两个人要买$n$层蛋糕，他们必须从$1$开始买到$n$，之后给定$2n$个蛋糕店，他们从$1$这个点出发，之后去买蛋糕。其中一旦一个人从一家蛋糕店买了蛋糕，那么另外一个人就不能在那家蛋糕店买蛋糕。问两个人花费的最少步数是多少？

### 题解

由于每一步只有两种可能，一个人去$x+1$中的一家蛋糕店，另外一个人去另一家。每一步的选择都只有两种，且无后效性。所以我们用贪心来解决。每一步的时候都选择花费步数最少的选择。

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
struct
int
bool
return
}
}a[maxn
- 桥的花费是欧几里得距离的平方

- 只能建造一座桥

- 可能不需要建造桥

### 题解

由于只建造一座桥，所以我们可以枚举起始点的陆地和终点的陆地，之后挑选出最近的点。

由于数据小，随便做。

### ac代码

```cpp
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35
36
37
38
39
40
41
42
43
44
45
46
47
48
49
50
51
52
53
54
55
56
57
58
59
60
61
62
63
64
65
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
int
int
const
int
char
vector
vector
void
vis[x][y] = 1
queue
q.push(make_pair
while
int
q.pop();
if
else
rep(i,0
int
int
if
if
if
vis[xxx][yyy] = 1
q.push(make_pair
}
}
}
int
#ifdef
freopen("3.in"
#endif
scanf
scanf
stx--;sty--;edx--;edy--;
rep(i,0
scanf
}
int
bfs(stx,sty,1
bfs(edx,edy,0
int
int
rep(i,0
rep(j,0
int
int
int
int
ans = min(ans,(x1-x2)*(x1-x2) + (y1-y2)*(y1-y2));
}
}
printf
return
}
```

## D2. Toy Train

### 题意

Alice开火车，他火车的轨道是确定的，之后火车开的方向也是确定的，火车的轨迹是一个圈，轨迹上有很多站点，每个站点上有糖果。

- 火车在站点上只可以拿起一个糖果

- 火车在站点上可以放下无限个糖果

目标是将所有站点上的糖果放到指定的站点所花费的时间最小。

### 题解

由于每一个站点都是独立的。你只需要管他是怎么拿起来的。所以每一个站点如果有$x$个糖果，那么从他开始至少要$x-1$圈加上一个最短的距离。所以我们可以枚举每一个站点所需要的最远距离。

假设从$i$起始点到$j$站点。那么我们开始的距离是$dis(i,j)=(j-i+n)\mod n$。

之后我们需要$x-1$圈。$(x-1)\times n$

之后我们需要从那个点到最近的放置点.$dis(j,z) = (z-j+n)\mod n$

之后两层循环即可。

### ac代码

```cpp
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35
36
37
38
39
40
41
42
43
44
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
const
int
vector
int
int
#ifdef
freopen("4.in"
#endif
scanf
rep(i,0
int
candys[x-1
}
int
rep(i,0
mmax = max(mmax,(int
}
// ans
rep(i,0
int
rep(j,0
if
int
int
for
tx = min(tx,(x-j+n)%n);
}
ans = max(ans, ((int
}
printf
}
return
}
```

Codeforces Round #542

https://www.cheasim.com/cf/2019/03/02/Codeforces-Round-542.html

作者
CheaSim

发布于
2019-03-02

更新于
2019-03-02

许可协议

#[cf](https://www.cheasim.com/tags/cf/)[greedy](https://www.cheasim.com/tags/greedy/)




