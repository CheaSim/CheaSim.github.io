# ST表学习笔记

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/08/19/st%E8%A1%A8%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0/
发布日期：2018-08-19
更新日期：2018-08-19





# ST表学习笔记

## 功能

ST表示用来求解给定区间RMQ的最值问题。

预处理复杂度:$O(nlongn)$，查询复杂度$O(1)$。

## 详解

### 原理

将原数组分成以2幂次的区间块，用$mn[i][j]$表示从$j$到$j-2^i-1$的最小值，最小值显然等于$$min(前半段最小值,后半段中最小值)$$从而得到递推式子

$$min[i][j]=min(mn[i-1][j],mn[i-1][j+2^{i-1}])$$

### 预处理代码

```cpp
p[0
rep(i,1
Log[0
rep(i,1
rep(i,1
rep(i,1
rep(j,1
if
mn[i][j] = min(mn[i-1
```

### 查询

定理1:$$2^{log(a)}>a/2$$

查询$x$到$y$的最小值可以假设$len=y-x+1,t=log(len)$，根据定理1，$2^t>len/2$，那么位置过了一半之后最小值的可能就落在了$x$后面的$2^t$和$y$前面的$2^t$。式子为$$mmin = min(mn[t][x],mn[t][y-2^t+1])$$

### 实现

```cpp
int
int
```

Reference:https://blog.csdn.net/hanks_o/article/details/77547380

ST表学习笔记

https://www.cheasim.com/%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0/2018/08/19/ST%E8%A1%A8%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.html

作者
CheaSim

发布于
2018-08-19

更新于
2018-08-19

许可协议

#[acm](https://www.cheasim.com/tags/acm/)




