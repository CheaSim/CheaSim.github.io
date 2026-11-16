# [hdoj1540]Tunnel Warfare

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/09/07/hdoj1540-tunnel-warfare/
发布日期：2018-09-07
更新日期：2018-09-07





# Tunnel Warfare

## 题意

在一条线上有二种操作

- 删掉一个点

- 恢复一个点

求某一个点和与之相连点的个数。

## 题解

线段树设左右标志或者是树状数组二分

HDOJ可以线段树+二分。

Cnm hdoj 多组数据不给提示

如果是树状数组500ms，线段树+二分1500ms。

POJ卡了线段树+二分。HDOJ没有写多组输入害得我WA成sb了。

垃圾HDOJ还造假数据，毁坏多个碉堡。也是服了。

## WA代码

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
sum[rt] = sum[rt>1
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
//cout>1
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

[hdoj1540]Tunnel Warfare

https://www.cheasim.com/acm/2018/09/07/hdoj1540-Tunnel-Warfare.html

作者
CheaSim

发布于
2018-09-07

更新于
2018-09-12

许可协议

#[线段树](https://www.cheasim.com/tags/%E7%BA%BF%E6%AE%B5%E6%A0%91/)




