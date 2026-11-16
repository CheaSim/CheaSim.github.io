# DNA Sequence

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2019/05/04/dna-sequence/
发布日期：2019-05-04
更新日期：2019-05-04





## DNA Sequence

### 题意

给定$m$个指定串，寻找长度为$n$的不含指定串的字符串。

### 题解

AC自动机+dp+矩阵快速幂。

如果要不含病毒串，那么我们相当于在每个状态中不能指向那个病毒终点串。对于每个状态来说，可以选择的就是4个字母去掉下一个状态是病毒的字母。

$dp[i] += dp[j] (j是非病毒终点)$

初始化$dp[i]$为可以选择的字母。相当于$i$状态加上状态$j$乘上字母数。可以构造一个矩阵mx。$mx[i][j]$表示$i$到$j$的字母数，矩阵的$n$次方之后就是经过$n$个状态转化后的值。

举个例子，比如我们是AC,AT,AG,AA这四个病毒串，那么root = 0,A是1,C=2,T=3,A=4。有五个状态。

当我们状态为0的时候，有两种选择。我们到状态0的选择字母可以选3个’C’’T’’G’。到状态1可以选1个’A’。之后到状态1没有选择了，因为全是病毒串。所以我们的矩阵是

3 1

0 0

之后矩阵乘就完事了。

我感觉讲得有点不清楚。。。

+2 TLE因为矩阵的大小是有build的trie树决定的，所以越小越好用ac.tot来表示矩阵的大小，也就是状态的大小。

+10 矩阵的大小其实是状态的大小，状态的大小是 输入的病毒串长度*病毒串的次数。最大tot为这么大。

+1 因为转移的状态只有四种，所以maxson为4就好了，大了的话创造矩阵的时候会出现问题。

###ac代码

```cpp
#include
#include
#include
#include
#include
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
const
int
struct
ll mx[MAX][MAX];
int
Matrix(){memset
Matrix operator
Matrix res;
rep(i,0
res.mx[i][j] = (mx[i][j]+b.mx[i][j])%mod;
return
}
Matrix operator
Matrix res;
rep(i,0
rep(k,0
res.mx[i][j] += mx[i][k]*b.mx[k][j];
}
res.mx[i][j] %= mod;
}
return
}
void
rep(i,0
rep(j,0
cout
}
cout
}
}
}U,V;
Matrix pow3
Matrix res;
rep(i,0
while
if
n>>=1
f = f*f;
}
return
}
struct
int
int
int
int
rep(i,0
flag[tot++] = 0
return
}
void
tot = 0
root = newnode();
encode['A'
encode['T'
encode['C'
encode['G'
memset
}
void
int
int
rep(i,0
int
if
next[now][k] = newnode();
now = next[now][k];
}
flag[now] = id;
}
void
queue
fail[root] = root;
rep(i,0
if
next[root][i] = root;
}else
fail[next[root][i]] = root;
q.push(next[root][i]);
}
}
while
int
if
rep(i,0
if
next[now][i] = next[fail[now]][i];
}else
fail[next[now][i]] = next[fail[now]][i];
q.push(next[now][i]);
}
}
}
}
Matrix build_mx
Matrix res;
rep(i,0
if
res.mx[i][next[i][j]] ++;
}
}
return
}
void
for
printf
for
printf
}
}
}ac;
char
int
#ifdef
freopen("3.in"
#endif
scanf
ac.init();
rep(i,0
scanf
ac.insert(s,1
}
ac.build();
tot = ac.tot;
Matrix res1 = ac.build_mx();
Matrix res = pow3(res1,m);
ll ans = 0
res1.debug();
rep(i,0
ans += res.mx[0
}
ans = ans % mod;
printf

return
}

```

DNA Sequence

https://www.cheasim.com/ac%E8%87%AA%E5%8A%A8%E6%9C%BA/2019/05/04/DNA-Sequence.html

作者
CheaSim

发布于
2019-05-04

更新于
2019-07-11

许可协议

#[dp](https://www.cheasim.com/tags/dp/)[ac自动机](https://www.cheasim.com/tags/ac%E8%87%AA%E5%8A%A8%E6%9C%BA/)[matrix](https://www.cheasim.com/tags/matrix/)




