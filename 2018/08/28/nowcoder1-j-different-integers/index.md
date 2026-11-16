# [nowcoder1] J.Different Integers

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/08/28/nowcoder1-j-different-integers/
发布日期：2018-08-28
更新日期：2018-08-28





# [nowcoder1]J. Different Integers

## 题意

给出一段序列$a_1,a_2,…,a_n$，和$l,r$，求区间$[1,l],[r,n]$中不同数字的个数。

## 题解

树状数组+倍增序列

将查询的$l,r$转化为查询序列$[r,l+n]$中不同中数字的个数。

使用$pre[]$数组维护一个前缀不同种类数字的个数。针对查询就是$pre[r]-pre[l-1]$再加上同时出现在$[1,l-1]$和$[l,r]$上的元素，因为在计算$pre[r]$的时候对于和$[1,l-1]$序列中相同的元素是剔除的，但是减掉之后是需要再加上去的。

对于查询$a[l,…,r]$和$a[1,…,l-1]$内同时出现数字的种类，可以使用树状数组来进行维护。$bit[i]$表示$a[i]$已经在$1,…,l$出现过了。

先对区间查询进行离线排序操作，对于左端每次右移把对应的数的下一个位置加入到树状数组中即可。(嘤嘤嘤？)

tips:处理每个位置数字下一次出现位置的方式很巧妙哦！

```cpp
//last 记录上一个出现该数字的位置
//nxt 记录下一个出现该数字的位置
rep(i,1
if
vis[a[i]] = 1
pre[i] = pre[i-1
}else
pre[i] = pre[i-1
}
if
last[a[i]] = i;
}
```

## AC代码

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
int
struct
int
bool
return
}
}ask[maxn];
int
void
for
bit[i] += val;
}
}
int
int
for
s += bit[i];
}
return
}
int
return
}
void
memset
memset
memset
memset
}
int
#ifdef
freopen("j.in"
#endif
while
init();
rep(i,1
rep(i,1
if
pre[i] = pre[i-1
vis[a[i]] = 1
}else
pre[i] = pre[i-1
}
if
last[a[i]] = i;
}
rep(i,0
int
int
ask[i].l = l;ask[i].r = r;ask[i].id = i;
}
sort(ask,ask+q);
int
int
rep(i,0
while
if
nowl++;
}
ans[ask[i].id] = pre[ask[i].r] - pre[ask[i].l-1
}
rep(i,0
}
return
}
```

Reference:https://www.nowcoder.com/discuss/87249?type=101&order=0&pos=12&page=1

[nowcoder1] J.Different Integers

https://www.cheasim.com/acm/2018/08/28/nowcoder1-J-Different-Integers.html

作者
CheaSim

发布于
2018-08-28

更新于
2018-08-28

许可协议

#[树状数组](https://www.cheasim.com/tags/%E6%A0%91%E7%8A%B6%E6%95%B0%E7%BB%84/)




