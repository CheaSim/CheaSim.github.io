# [hdoj5559]Frog and String

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/11/21/hdoj5559-frog-and-string/
发布日期：2018-11-21
更新日期：2018-11-21





# Frog and String

## 题意

给定一个字符串的长度和他里面子回文串的个数。

- 子回文串是连续子串，并且相同的回文串不重复计数

- 字符串由前$K$个字符构成

## 题解

构造题嘛，最重要的就是规律啦。

对于构造题，我们就要一步一步来，把题目分段。

- 首先对于$K=1$来说，如果$n !=m$的话，无解。

- 对于$K=2$来说，这时候爆搜就起作用了，我怎么想也不肯能根据我那只有6长度的字符串想到会存在一个长度为8但是只有7个自回文串的字符串。他就是$AABABBAA$.估计只有搜才能发现这个玩意，之后就会发现只有两个字符，你也能构造一个长度很长，但只有很少的子回文串。$AABABB$这个玩意可以无限重复，但是只有$A,B,AA,BB,ABA,BAB,ABBA,BAAB$这四种玩意。

- 对于$K \ge 3$，最好想，就是$ABC$来重复计数，$m-3$个前导$A$

我真是蠢，真的，没有去用爆搜找一下答案，就凭自己的直觉在那里搞来搞去。

+1 $m=2$的时候少考虑了

+1 当$k>m$的时候

+1 单独测试用例 没有print case

+1 特判m==n没有加else if

+1 $k=2,n=m$的时候出现了错误。应该特判的。

## ac代码

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
const
int
char
int
#ifdef
freopen("1.in"
#endif
int
rep(test_case,1
scanf
bool
if
if
if
if
if
if
printf
puts
continue
}
}
printf
if
else
rep(i,0
puts
}else
int
rep(i,0
rep(i,0
puts
}else
vector
rep(i,0
rep(i,0
rep(i,0
printf
}
puts
}
}
return
}
```

[hdoj5559]Frog and String

https://www.cheasim.com/acm/2018/11/21/hdoj5559-Frog-and-String.html

作者
CheaSim

发布于
2018-11-21

更新于
2018-11-21

许可协议

#[构造](https://www.cheasim.com/tags/%E6%9E%84%E9%80%A0/)[爆搜](https://www.cheasim.com/tags/%E7%88%86%E6%90%9C/)




