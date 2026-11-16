# 最大子段和学习笔记

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/08/27/%E6%9C%80%E5%A4%A7%E5%AD%90%E6%AE%B5%E5%92%8C%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0/
发布日期：2018-08-27
更新日期：2018-08-27





# 最大子段和学习笔记

## 什么是最大子段和？

给定$n$个整数(可以为负数)组成的序列$a_1,a_2,…,a_n$，求该序列连续的字段和最大值。显然如果都是负数最大值可以为0。

## 解决方案1

暴力枚举开始位置$i$和终止位置$j$，对每一种可能性计算和。

复杂度$O(n^3)$

## 解决方案2

使用前缀和优化，保存$\sum_{i=1}^{j-1}a[i]$的结果。

复杂度$O(n^2)$

## 解决方案3

采用分治策略优化复杂度。

将给定序列$a$分成长度两段子序列$a[1,n/2],a[n/2+1,n]$，分别求出这两段的最大子段和，而总序列的最大子段和有三种情况

- 和前半段相同

- 和后半段相同

- 由前半段的部分和后半段的部分组成的序列相同

```cpp
int
int
if
int
int
int
int
for
lefts += ve[i];
ls = max(ls,lefts)  //遍历更新最大值
}
int
for
rights += ve[i];
rs = max(rs,rights);
}
sum = ls + rs;
sum = max(sum,max(lm,rm));
return
}
```

复杂度$O(nlogn)$

## 解决方案4

动态规划。

- 设置$dp[i] = max(dp[i-1]+a[i],a[i])$，$dp[i]$表示以$i$为结尾的最长子串的和。

- 对于每一个$a[i]$如果之前的最大子串小于$0$了，那么就要重新以他为开头建立一个子串。

```cpp
int
int
int
for
if
sum = ve[i];
L = R = i;
}else
sum += ve[i];
R ++;
}
if
mmax = sum;
l = L;r = R;
}
}
return
}
```

复杂度$O(n)$

## 解决方案5

最大子段的左右两个数字必定为正数，最左边数字

reference:https://blog.csdn.net/zhong36060123/article/details/4381391

最大子段和学习笔记

https://www.cheasim.com/%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0/2018/08/27/%E6%9C%80%E5%A4%A7%E5%AD%90%E6%AE%B5%E5%92%8C%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.html

作者
CheaSim

发布于
2018-08-27

更新于
2019-04-28

许可协议

#[最大子段和](https://www.cheasim.com/tags/%E6%9C%80%E5%A4%A7%E5%AD%90%E6%AE%B5%E5%92%8C/)




