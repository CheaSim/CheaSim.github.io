# 2018 ICPC南京赛区网络赛

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/09/03/2018-icpc%E5%8D%97%E4%BA%AC%E8%B5%9B%E5%8C%BA%E7%BD%91%E7%BB%9C%E8%B5%9B/
发布日期：2018-09-03
更新日期：2018-09-03





# ACM-ICPC 2018 南京赛区网络预赛

## A. An Olympian Math Problem

### 题意

$S=1×1!+2×2!+⋯+(n - 1) \times (n-1)!(n−1)×(n−1)!$问$Smodn$是多少。

### 题解

思维题，打表题？答案就是$n-1$证明如下。

看到$n-1$很不爽，那就加一个$(n-1)!$就凑好了。

$S+1!+2!+…+(n-1)!=2!+3!+…+n!$

之后再减掉。

$S=n!-1!$那么对$n$取余$S modn=-1modn=n-1$搞定。

### AC代码

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
ll n;
int
#ifdef
freopen("1.in"
#endif
scanf
while
scanf
printf
}
return
}
```

## B. The writing on the wall

## E. AC Challenge

### 题意

做题目，要按照一定顺序做题目，每个题目有两个值$a,b$，表示做了题目后增加$t*a+b$。

### 题解

状态压缩+剪枝+拓扑排序。

因为$n$的数据量小于$20$所以可以使用状态压缩。

$S$表示已经做的题目。

$vs$数组存储已知做题的最大值。如果做同样的题值比较小就减掉。

### AC代码

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
}G[maxn*maxn*3
int
ll a[maxn],b[maxn];
int
void
G[cnt].to = v;
G[cnt].next = head[u];
head[u] = cnt++;
}
int
ll ans = 0
ll vis[maxn];
ll vs[1
void
ans = max(ans,temp);
if
vs[S] = temp;
for
int
ind[v]--;
}
rep(i,1
if
vis[i] = 1
dfs(i,t+1
vis[i] = 0
}
}
for
int
ind[v]++;
}
}
int
#ifdef
freopen("e.in"
#endif
memset
scanf
rep(i,1
int
rep(j,0
int
add(u,i);ind[i]++;
}
}
rep(i,1
if
ind[i]++;
add(0
}
}
ans = 0
dfs(0
printf
return
}
```

## G. Lpl and Energy-saving Lamps

### 题意

一个人去给所有房间换灯泡，每个月都会获得$m$个灯泡，每个房间有$a_i$个灯泡，之后以能换就换的态度每个月从第一个房间开始换，没有能换的房间就停止，把灯泡留到下一个月。换过灯泡就不用再换了。问给定月份中已经换好的房间数和当月剩下的灯泡数。

### 题解

线段树维护一个区间最小值。

由于线段树遍历是从前往后的，就不用担心顺序问题。

### AC代码

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
int
void
Min[rt] = min(Min[rt
- 马拉车+hash

- 回文树+dfs

### AC代码1

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
#include
#include
#include
#include
#include
#include
#include
using
#define
#define
const
const
ULL P = 1313131
ULL sqr[maxn/2
ll ha[maxn/2
int

const

bool
{
int
for
if
}
Next[++cnt]=Laxt[u];
Laxt[u]=cnt;
V[cnt]=Now;
return
}
ll ans=0
void
ULL Now=has[y]-has[x-1
if
{
ans+=((ha[y]-ha[x-1
ans%=mod;
}
}
int
char
void
{
int

scanf
Len=strlen
sqr[0
has[0
for
sqr[i]=sqr[i-1
has[i]=has[i-1
tmp[i]=tmp[i-1
ha[i]=(ha[i-1
}

for
_hash(i,i);
if
while
_hash(i-r[i]-1
r[i]++;
}
if
R=i+r[i];
Mid=i;
}
}

cnt=0
memset
memset
for
if
while
_hash(i-r[i]-1
++r[i];
}
if
R=i+r[i]-1
Mid=i;
}
}
printf
}
int

_malacher();
return
}
```

### AC代码2

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
99
100
101
102
103
104
105
106
107
108
109
110
111
112
113
114
#include
#include
using
typedef
const
const

ll pow
ll t,y;
t=1
while
if
y=y*y%MOD; b=b>>1
}
return
}

int
int
int
int
int
int
int
int
int

int
cnt[tot]=0
num[tot]=0
len[tot]=l;
return
}

void
tot=0
new_node(0
new_node(-1
last=0
N=0
S[N]=-1
fail[0
}

int
while
x=fail[x];
return
}

void
c-='0'
S[++N]=c;
int
if
int
fail[now]=nxt[get_fail(fail[cur])][c];
nxt[cur][c]=now;
num[now]=num[fail[now]]+1
}
last=nxt[cur][c];
cnt[last]++;
}

ll jans=0
ll oans=0

void
for
if
ll cur;
if
jans+=i;
cur=i;
jans%=MOD;
}
else
cur=i*pow
jans=(jans+cur%MOD)%MOD;
jans%=MOD;
}
dfs1(nxt[x][i],cur%MOD);
}
}
}

void

for
if
ll cur;
cur=i*pow
oans=(oans+cur%MOD)%MOD;
dfs2(nxt[x][i],cur%MOD);
}
}
}

char

int
scanf
int
init_tree();
for
add_char(str[i]);
dfs1(1
dfs2(0
printf
return
}

```

## L. Magical Girl Haze

### 题意

给定一个图，问从$1$走到$n$如果可以选择$k$条路为$0$，那么最短的路径是多少。

### 题解

分层图最短路+堆优化dijistra

每使用一次道路为0，就进入$step+1$的路径比较。比较好的dp思维。对于pair使用了一个小trick，负值就可以不用手写greater和重载小于了。但是现场赛应该还是手写node算了。

dp转移两种状态.

- $dp[v][step+1] = min(dp[v][step+1],dp[u][step])$

- $dp[v][step] = min(dp[v][step],dp[u][step]+val(u,v))$

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
#include
using
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
struct
int
}G[maxn
2018 ICPC南京赛区网络赛

https://www.cheasim.com/acm/2018/09/03/2018-ICPC%E5%8D%97%E4%BA%AC%E8%B5%9B%E5%8C%BA%E7%BD%91%E7%BB%9C%E8%B5%9B.html

作者
CheaSim

发布于
2018-09-03

更新于
2018-09-04

许可协议

#[网络赛](https://www.cheasim.com/tags/%E7%BD%91%E7%BB%9C%E8%B5%9B/)




