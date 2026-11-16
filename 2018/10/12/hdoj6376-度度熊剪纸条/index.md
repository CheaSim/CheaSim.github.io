# [hdoj6376]度度熊剪纸条

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/10/12/hdoj6376-%E5%BA%A6%E5%BA%A6%E7%86%8A%E5%89%AA%E7%BA%B8%E6%9D%A1/
发布日期：2018-10-12
更新日期：2018-10-12





## 度度熊剪纸条

### 题意

将一段01的序列分成$k$段，将他们重新拼接，问拼接成的纸条中前导0最多有多少个。

- 拼接不可以改变方向。

### 题解

我模拟下来就是我们可以将这段序列分成三部分，

比如

> 11111/0/111/0/1111/0/11111

最前方的1部分和最后方的1部分和中间的1部分。

如果想将中间的1放在前面就必须剪两次，前方和后方的只需要1次。

模拟的话。

- 我们首先如果第一段不剪，那么就是从后面的中间1和后方1选择，中间1需要剪两次，后方1只要剪一次。

- 如果第一段剪掉，那么就是选择最大的，在他前面切一刀，把它当做最后的处理，其余的是前面的和后面的剪一刀和中间的剪两刀。

如果$k==0$特殊处理一下。

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
char
int
int
bool
int
int
int
int
int
while
l = st;
while
r = n-ed-1
rep(i,st,ed+1
if
if
ve[++j] = cnt;
cnt = 0
}
}
if
sort(ve+1
while
ans += ve[j--];
k-=2
}
if
ans += max(l+r,ve[j]);
}else
ans += max(l+r,max(l+ve[j],r+ve[j]));
}
return
}
char
int
#ifdef
freopen("1.in"
#endif
while
scanf
rep(i,0
printf
}

return
}
```

[hdoj6376]度度熊剪纸条

https://www.cheasim.com/acm/2018/10/12/hdoj6376-%E5%BA%A6%E5%BA%A6%E7%86%8A%E5%89%AA%E7%BA%B8%E6%9D%A1.html

作者
CheaSim

发布于
2018-10-12

更新于
2018-10-12

许可协议

#[贪心](https://www.cheasim.com/tags/%E8%B4%AA%E5%BF%83/)




