# 计算几何模板

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/09/05/%E8%AE%A1%E7%AE%97%E5%87%A0%E4%BD%95%E6%A8%A1%E6%9D%BF/
发布日期：2018-09-05
更新日期：2018-09-05

计算几何题目 Distance to work 的简短记录与参考代码模板。




## J .Distance to work

### 题意

懒得看了

### 题解

计算几何。

扒一扒dls的板子

```cpp
typedef
const

inline

inline

struct
db x, y;
P() {}
P(db _x, db _y) : x(_x), y(_y) {}
P operator
P operator
P operator
P operator

bool
int
if
return
}

bool
return
}

db dot
db det

db distTo
db alpha
void
void
db abs
db abs2
P rot90
P unit
int
P rot
};

struct
P ps[2
L() {}
L(P p1,P p2) { ps[0
P& operator
P dir
bool
L push
const
P delta = (ps[1
return
}
};
```

```cpp
#define
#define

bool
db a1 = cross(q1, q2, p1), a2 = -cross(q1, q2, p2);
return
}

P isLL
db a1 = cross(q1, q2, p1), a2 = -cross(q1, q2, p2);
return
}

P isLL

bool
if
return
}

bool
return
crossOp(p1,p2,q1) * crossOp(p1,p2,q2)  0
}
return
}

vector
int
sort(ps.begin(), ps.end());
vector
for
while
for
while
qs.resize(k - 1
return
}

vector
//caution: need to unique the Ps first
int
sort(ps.begin(), ps.end());
vector
for
while
for
while
qs.resize(k - 1
return
}

db convexDiameter
int
int
int
db ret = ps[i].distTo(ps[j]);
do
if
(++j)%=n;
else
(++i)%=n;
ret = max(ret,ps[i].distTo(ps[j]));
}while
return
}

vector
vector
int
rep(i,0
P p1 = ps[i], p2 = ps[(i+1
int
if
if
}
return
}

//min_dist
```

```cpp
db min_dist
if
db ret = 1e100
rep(i,l,r) rep(j,l,i) ret = min(ret,ps[i].distTo(ps[j]));
return
}
int
db ret = min(min_dist(ps,l,m),min_dist(ps,m,r));
vector
sort(qs.begin(), qs.end(),[](P a,P b) -> bool
rep(i,1
ret = min(ret,qs[i].distTo(qs[j]));
return
}

int
db d = o1.distTo(o2);
if
if
if
if
return
}

vector
db x = (p1-o).dot(p2-p1), y = (p2-p1).abs2(), d = x * x - y * ((p1-o).abs2() - r*r);
if
d = max(d,0.0
return
}

vector
db d = o1.distTo(o2);
if
if
d = min(d, r1 + r2);
db y = (r1 * r1 + d * d - r2 * r2) / (2
P dr = (o2 - o1).unit();
P q1 = o1 + dr * y, q2 = dr.rot90() * x;
return
}

vector
db x = (p - o).abs2(), d = x - r * r;
if
P q1 = o + (p - o) * (r * r / x);
P q2 = (p - o).rot90() * (r * sqrt
return
}

vector
vector
if
P dr = (o2 - o1).unit().rot90() * r1;
ret.pb(L(o1 + dr, o2 + dr)), ret.pb(L(o1 - dr, o2 - dr));
} else
P p = (o2 * r1 - o1 * r2) / (r1 - r2);
vector
rep(i,0
}
return
}

vector
vector
P p = (o1 * r2 + o2 * r1) / (r1 + r2);
vector
rep(i,0
return
}

db areaCT
vector
if
bool
if
if
sign((p1-is[0
return
else
}
if
if
return
}

bool

bool

bool
if
return
} else
return
}
}

bool
if
return
} else
return
}
}

bool
return
}

vector
sort(l.begin(), l.end());
deque
for
if
while
while
q.push_back(l[i]);
}
while
while
vector
for
return
}

P inCenter
double
return
}

P circumCenter
P bb = b - a, cc = c - a;
double
return
}

P othroCenter
P ba = b - a, ca = c - a, bc = b - c;
double
A = ca.x * ba.y - ba.x * ca.y,
x0 = (Y + ca.x * ba.y * b.x - ba.x * ca.y * c.x) / A,
y0 = -ba.x * (x0 - c.x) / ba.y + ca.y;
return
}
```

### AC代码（别人家的模板。）

```cpp
#include
using
#define
const
const
const
const
// Compares a double to zero
int
if
if
return
else
return
}
// square of a double
inline
return
}
/*
15 * Point
16 * Point() - Empty constructor
17 * Point(double _x,double _y) - constructor
18 * input() - double input
19 * output() - %.2f output
20 * operator == - compares x and y
21 * operator 作者
CheaSim

发布于
2018-09-05

更新于
2018-09-05

许可协议

#[计算几何](https://www.cheasim.com/tags/%E8%AE%A1%E7%AE%97%E5%87%A0%E4%BD%95/)




