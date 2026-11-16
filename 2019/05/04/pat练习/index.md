# PAT练习

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2019/05/04/pat%E7%BB%83%E4%B9%A0/
发布日期：2019-05-04
更新日期：2019-05-04





# PAT练习

为了拿PAT的50元代金券，刷一刷牛客网上的PAT真题。

点我连接

## Rational Sum

### 题意

求一百个分数的和。

### 题解

大整数秒了。

其实我想用python，现在acm区域赛都让用python了

### ac代码

##Read Number in Chinese

### 题意

给定一个数字，用中文拼音输出他。

### 题解

模拟。

- 如果是负数，输出”Fu”

- 每四位分隔一下，都是一样的。

-

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
char
string
ll n;
int
#ifdef
freopen("1.in"
#endif
scanf
int
int

if
per(i,t,sz) s[i+10
rep(i,t,10
vector
if
bool
int
rep(i,1
idx = i;
break
}
rep(i,1
if
ans.push_back(chinese[s[1
ans.push_back("Yi"
}
if
ans.push_back(chinese[s[2
ans.push_back("Qian"
}else
if
}
if
flag = true
ans.push_back(chinese[s[3
ans.push_back("Bai"
}else
if
}
if
flag = true
ans.push_back(chinese[s[4
ans.push_back("Shi"
}else
if
}
if
ans.push_back(chinese[s[5
}else
if

// gewei
flag = true

if
ans.push_back(chinese[s[6
ans.push_back("Qian"
}else
if
}
if
ans.push_back(chinese[s[7
ans.push_back("Bai"
}else
if
}
if
ans.push_back(chinese[s[8
ans.push_back("Shi"
}else
if
}
if
if
bool
rep(i,0
if
continue
}
if
else
cout
if
else
}
return
}
```

## List Grades (25)

### 题意

给定最多100个人，给他们排序，输出指定成绩区间内的人名和ID。

### 题解

模拟，sort

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
struct
string
string
int
bool
return
}
node(){}
node(string
name = a;
id = b;
grade = g;
}
};
int
#ifdef
freopen("1.in"
#endif
vector
int
rep(i,0
string
cin
ve.push_back(node(a,b,g));
}
sort(ve.begin(),ve.end());
int
scanf
bool
rep(i,0
int
while
while
cout
cnt++;
}
if

return
}
```

## Tree Traversals Again (25)

### 题意

用栈表示一个树的先根遍历，求这颗二叉树的后跟遍历。

### 题解

dfs模拟一下即可。

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

char
struct
int
node *left = NULL
};
void
if
root->left = new
root->left->id = n;
}else
root->right = new
root->right->id = n;
}
}
void
int
// left
if
cin
addnode(u,n,1
dfs(u->left);
}
scanf
if
cin
addnode(u,n,0
dfs(u->right);
}else
return
}
}
void
if
post_order(rt->left);
}
if
post_order(rt->right);
}
printf
}
int
#ifdef
freopen("1.in"
#endif
node * root = new
int
scanf
root->id = n;
dfs(root);
post_order(root);
return
}
```

PAT练习

https://www.cheasim.com/pat/2019/05/04/PAT%E7%BB%83%E4%B9%A0.html

作者
CheaSim

发布于
2019-05-04

更新于
2019-05-05

许可协议

#[pat](https://www.cheasim.com/tags/pat/)




