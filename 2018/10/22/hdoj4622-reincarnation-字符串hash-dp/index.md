# [hdoj4622]Reincarnation 字符串hash+dp

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/10/22/hdoj4622-reincarnation-%E5%AD%97%E7%AC%A6%E4%B8%B2hash-dp/
发布日期：2018-10-22
更新日期：2018-10-22





## Reincarnation

### 题意

区间查询不同字符串的数量。

### 题解

字符串hash+dp思想

我们从$1-len$枚举子串的长度，如果该区间内子串就加1。由于可能会有重复所以记录长度为$x$的子串最后一次出现的$L$。如果子串出现过那么$dp[L][R]-1$。

定义$dp[l][r]$为在$[l,r]$区间内不同子串的数量那么可以得到递推公式

- $dp[i][j]=dp[i+1][j]+dp[i][j-1]-dp[i+1][j-1]$

相当于把一个区间拆成三部分，$[l+1][r],[l][r-1],[l+1][r-1]$，这三个区间合并就是前两个集合个数相加之后减掉这两个集合并的部分元素的个数。

妙啊！

之后在预处理枚举出每一种长度的子串，从1循环到Len，如果发生重复那么可以将之前出现的+1操作的$L$到现在操作的$R$减少一个，那么这个区间的不同子串的个数就减少了一个。而且由于是递推的所以所有$[1,2,3,4,5]-L,R$都会减少1.

由于$n\leq 2000$所以可以使用$O(n^2)$的做法。

主要是dp要想明白，如果一旦确定了递推情况，就不用管细枝末节的东西了，直接在区间上减少就可以了，使得每次dp都是正确的。

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
typedef
int
char
ull base[maxn],has[maxn],pos[maxn];
ull bas = 131
const
struct
int
ull edgenum[maxn];
int
void
num = 0
memset
}
int
int
for
if
int
return
}
}
edgenum[num] = val;
close[num] = id;
next[num] = head[u];
head[u] = num++;
return
}
}H;
int
int
#ifdef
freopen("3.in"
#endif
int
base[0
rep(i,1
while
scanf
memset
rep(i,1
for
H.init();
for
int
dp[i][x+i-1
if
}
}
per(i,1
dp[i][j] += dp[i+1
int
while
int
printf
}
}

return
}
```

[hdoj4622]Reincarnation 字符串hash+dp

https://www.cheasim.com/acm/2018/10/22/hdoj4622-Reincarnation-%E5%AD%97%E7%AC%A6%E4%B8%B2hash-dp.html

作者
CheaSim

发布于
2018-10-22

更新于
2018-10-22

许可协议

#[字符串hash](https://www.cheasim.com/tags/%E5%AD%97%E7%AC%A6%E4%B8%B2hash/)




