# [kuangbin带你飞7]线段树

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/09/06/kuangbin%E5%B8%A6%E4%BD%A0%E9%A3%9E7-%E7%BA%BF%E6%AE%B5%E6%A0%91/
发布日期：2018-09-06
更新日期：2018-09-06





# kuangbin带你飞7

## 前言

作为一名acm选手，不能连线段树都不会，练就完事了。而且我越发觉得在赛场上不能卡机，中档题才是区分牌子的题目。只有慢慢思索的题目才能真正地提高自己，立下一个flag，每十天完成一个kuangbin专题。现在时间9/6。必须在9/16完成这个线段树专题，就算是困死也得完成。

## 感想

- 左右区间还是注意一下，保不准出题人恶趣味。

- 初始化不能想当然$n$多大树多大，有可能他是一个范围，$n$只是代表着式子的个数罢了。

- 数组居然还是又一次忘记开4倍。

- lazy数组忘记初始化，或者lazy可以为0但是还是初始化为0了。

# A.敌兵布阵

## 题意

这如果我没有记错，应该是人生中第一个线段树题目，很是经典。单点修改，区间查询。

## 题解

线段树。

## AC代码

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
//head
const
int
int
void
sum[rt] = sum[rt

+5 $n$当坐范围

+3 误以为build函数能够初始化所有的点，但其实是要memset(vis,-1,sizeof(vis));

### AC代码

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
66
67
68
69
70
71
72
73
74
75
76
77
78
79
80
81
82
83
84
85
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
//head -------------------------
const
int
int
void
if
lazy[rt

acm还是靠智力和眼力啊，我想了半天都没想出来什么数学方法，原来只需要看出规律和找到最关键的突破点就ok了。

+1超时忘记开4倍数组了。。

+1 虚伪的看到了提醒要注意l,r的大小关系，妈的，这都卡，是不是人啊。

## AC代码

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
//head
const
int
ll sum[maxn>1
if
else
}
return
}
int
int
while
mid = l+r>>1
if
else
}
return
}
int
int
#ifdef
freopen("2.in"
#endif
while
stack
memset
memset
rep(i,1
while
char
if
int
st.push(x);
if
vis[x] = 1
add(x,-1
}else
int
if
else
}else
add(st.top(),1
vis[st.top()] = 0
st.pop();
}
}
}
return
}
```

# J.Assign the task

## 题意

dfs序+线段树模板题

## 题解

同上

+1 lazy数组没有初始化，没适应无build建树

## AC代码

```plain
#include
using namespace std;
#define rep(i,a,n) for(int i=(a);i=(a);i--)
#define fi first
#define se second
#define lson l,mid,rt pII;
typedef long long ll;
const int INF = 0x3f3f3f3f;
//head
const int maxn = 5e4+10;
int T,n,clk;
int on[maxn],in[maxn],ind[maxn],a[maxn G[maxn];
void init(){
clk = 0;
memset(on,0,sizeof(on));
memset(in,0,sizeof(in));
memset(ind,0,sizeof(ind));
memset(a,-1,sizeof(a));
memset(lazy,-1,sizeof(lazy));
rep(i,0,n+1) G[i].clear();
}
void dfs(int u,int fa){
for(auto v:G[u]){
if(v==fa) continue;
in[v] = ++clk;
dfs(v,u);
}
on[u] = clk;
}
void pushdown(int rt){
if(lazy[rt]!=-1){
lazy[rt>1;
if(L>1;
pushdown(rt);
if(p
- 将$[l,r]$区间的数字加上$val$.

- 将$[l,r]$区间的数字乘上$val$

- 将$[l,r]$区间的数字变成$val$

- 求区间$[l,r]$内所有数字$[1,2,3]$次方的和。

## 题解

线段树

对于线段树的懒惰标记和取模运算细节要求很高。

相信对于sum数组的转化大家都能够推得出来，但是关于pushdown的操作是另有玄机。

首先他的顺序很重要。得先将lazy[1]递推下去，也就是操作3把数字变成$val$，之后再进行乘法和加法的操作。对于乘法很重要的一点是你在lazy[2]标记递推的时候，其实你把子树中的加法也相当于乘了$val$，所以递推不仅要递推乘法标记，还要递推加法标记。

+3 更新Pushdown中你也要更新lazy数组的值

+1 更新的次序也有关系

+1初始化 有的要1.

+1 少写一个|1  rt[rt

+2 忘记掉可能初始不能放在A点，所以要加入一个全局变量flag，初始化maxl。

## AC代码

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
66
67
68
69
70
71
72
73
74
75
76
77
78
79
80
81
82
83
84
85
86
87
88
89
90
91
92
93
94
95
96
97
98
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
//head
int
const
int
void
sum[rt] = sum[rt
- 如果是女神来查询，那么空闲的时间也包括基友的时间

- 如果是基友来查询，那么只有空闲的时间可以选择

- 如果想要学习$[l,r]$，那么$[l,r]$之间的时间都会被清空。

## 题解

线段树的区间合并。

这里由于要维护两个线段树，所以用结构体来构造树，不过确实使用结构体封装之后复用性高了很多。

- 定义三个量$ll,rr,mm$分别表示从区间$[L,R]$最左边开始的最长长度和从区间最右边开始的最长长度和区间内横跨中点的最长长度。

- 定义$maxlen$来表示区间内最长的长度来剪枝。

这样就可以更新了。

一棵树代表屌丝+女神占有的，一棵树代表女神占有的。

查询分为三种方向

- 先查询左边开始的长度是否大于$val$，如果大于返回$L$，或者是递归左子树。

- 再查询中间的部分长度是否大于$val$，如果大于返回$mid-rr[lc]+1$就是中点减掉从左半部分右边的长度。

- 再查询递归右子树。

+1 区间合并中 更新父节点必须每个都更新，所以有时候你在return 之前也要更新一下。

## AC代码

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
//head ----------------------------------------
const
int
struct
int
int
int
void
lazy[rt] = -1
if
ll[rt] = rr[rt] = 0
mm[rt] = 1
return
}
int
build(lson); build(rson);
}
void
lazy[1
}
void
if
maxlen[rt] = ll[rt] = rr[rt] = mm[rt] = (lazy[rt]?(r-l+1
}else
int
ll[rt] = ll[lc];
if
mm[rt] = rr[lc] + ll[rc];
rr[rt] = rr[rc];
if
maxlen[rt] = max(maxlen[lc],max(maxlen[rc],mm[rt]));
}
}
void
if
int
lazy[lc] = lazy[rc] = lazy[rt];
lazy[rt] = -1
}
}
int
pushup(l,r,rt);
//cout Reference:https://www.cnblogs.com/DSChan/p/4861977.html

# N.picture

## 题意

求多个矩形周长的并

## 题解

扫描线+线段树

这道题目没有离散化$X$坐标就可以做。而且例子也只有一个。。

## ac代码

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
66
67
68
69
70
71
72
73
74
75
76
77
78
79
80
81
82
83
84
#include
#include
#include
using
#define
#define
#define
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
struct
int
int
node(){}
node(int
lx = _lx; rx = _rx; y = _y; f = _f;
}
bool
return
}
}L[maxn
[kuangbin带你飞7]线段树

https://www.cheasim.com/acm/2018/09/06/kuangbin%E5%B8%A6%E4%BD%A0%E9%A3%9E7-%E7%BA%BF%E6%AE%B5%E6%A0%91.html

作者
CheaSim

发布于
2018-09-06

更新于
2018-09-25

许可协议

#[线段树](https://www.cheasim.com/tags/%E7%BA%BF%E6%AE%B5%E6%A0%91/)




