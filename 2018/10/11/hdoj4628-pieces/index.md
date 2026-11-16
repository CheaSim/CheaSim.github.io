# [hdoj4628]Pieces

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/10/11/hdoj4628-pieces/
发布日期：2018-10-11
更新日期：2018-10-11





# HDU - 6071

## 题意

将一个字符串每次减少一个子回文串，例子avdffd可以减少dd，就是subsequence。问最少减少几个回文子串可以使得字符串消失。

## 题解

因为数据量只有16，所以是状压dp。

将每个字符串的位置状态压缩，之后再将回文子串先预处理出来，每次都判断一下是否可以减少回文子串，之后就是状压dp的基本操作了。

有一个检验是否可以减去的好方法

```cpp
if
dfs(S^x);
//表示了x是可以减掉的。
```

之后预处理的时候将状压的值进行check更加方便。

好久没做状压dp了，居然可以return dp[]这样做，惊奇！

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
char
int
int
bool
char
rep(i,0
if
str[cnt++] = s[i];
}
rep(i,0
if
}
return
}
int
int
int
if
rep(i,0
vis[S] = min(dfs(S^Set[i]),vis[S]);
}
return
}
int
#ifdef
freopen("1.in"
#endif
int
while
scanf
tot = 0
int
memset
vis[0
rep(i,1
if
}
printf
}

return
}
```

[hdoj4628]Pieces

https://www.cheasim.com/acm/2018/10/11/hdoj4628-Pieces.html

作者
CheaSim

发布于
2018-10-11

更新于
2018-10-11

许可协议

#[状压dp](https://www.cheasim.com/tags/%E7%8A%B6%E5%8E%8Bdp/)[预处理](https://www.cheasim.com/tags/%E9%A2%84%E5%A4%84%E7%90%86/)




