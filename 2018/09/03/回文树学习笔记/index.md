# 回文树学习笔记

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/09/03/%E5%9B%9E%E6%96%87%E6%A0%91%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0/
发布日期：2018-09-03
更新日期：2018-09-03





# 回文树学习笔记

## 神奇的数据结构 Palindromic Tree 回文树

### 功能简介

- 求一个串$S$中$[0,i]$中本质不同回文串的个数

- 求串$S$中每一个本质不同回文串出现的次数

- 求指定下标$i$结尾的回文串的个数

### 变量简介

- $len[i]$表示编号为$i$节点所表示的回文串的$len$。

- $next[i][c]$表示编号为$i$的节点表示的回文串在两边添加字符$c$之后会变成的回文串的编号。

- $fail[i]$表示节点$i$失配以后跳转后不等于自己的节点$i$所表示的回稳产的最长长度。

- $cnt[i]$表示节点$i$表示的本质不同的串的个数。

- $num[i]$表示以节点$i$表示的最长回文串的最右端点为回文串结尾的回文串个数。

- $last$指向新添加一个字母后所形成的最长回文串表示的节点。

- $S[i]$表示第$i$次添加的字符(初始化S[0]=不存在的字符)。

- $p$表示添加的节点个数。

- $n$表示添加的字符个数。

### 模板(抄的)

```cpp
const
const

struct
int
int
int
int
int
int
int
int
rep(i,0
cnt[p] = 0
return
}
void
p = 0
newNode(0
last = 0
}
int
while
return
}
void
c -= 'a'
S[++n] = c;
int
if
int
fail[now] = next[get_fail(fail[cur])][c];
next[cur][c] = now;
num[now] = num[fail[now]] + 1
}
last = next[cur][c];
cnt[last]++;
}
void
per(i,0
}
}
```

> https://blog.csdn.net/u013368721/article/details/42100363

回文树学习笔记

https://www.cheasim.com/%E6%A8%A1%E6%9D%BF/2018/09/03/%E5%9B%9E%E6%96%87%E6%A0%91%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.html

作者
CheaSim

发布于
2018-09-03

更新于
2018-09-03

许可协议

#[字符串](https://www.cheasim.com/tags/%E5%AD%97%E7%AC%A6%E4%B8%B2/)




