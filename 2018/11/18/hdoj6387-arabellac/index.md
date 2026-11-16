# [hdoj6387]AraBellaC

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/11/18/hdoj6387-arabellac/
发布日期：2018-11-18
更新日期：2018-11-18





# AraBellaC

## 题意

一段序列中只有$A,B,C$三种字母，这段序列是一段周期序列，并且他的重复序列是这样子的。

- AAAABBBBCCCCC

他的重复序列由$a$个A,$b$个B,$c$个C组成，并且是有顺序的。

给定以下规则。

- 给你$m$个位置的值。

- 其余的位置

问你生成一个序列，使得$a,b,c$的字典序最小，如果没有输出$NO$

## 题解

二分。

枚举重复序列的长度，那么我们要检验的就是$a,b,c$满足不满足要求。下面就可以用二分来解决。

感觉复杂度有点高。。

我们分别用三个数组存放A,B,C的位置。那么在搜索每个区间内的最后面的一个A，B，C和最前面的一个A，B，C。

之后比较复杂的就是，将一些不对的答案剔除。

因为我们得到了每个字母第一次出现和最后一次出现的位置，我们就可以得到$a,b,c$并且把一些值给剔除。

定义$a_{max},a_{min},b_{max},b_{min},c_{max},c_{min}$分别为他们出现的位置。

- $a_{max}

$a=a_{max}-begin+1,b = b_{max}-a_{max}+1,c = len-a-b$

## ac代码

[hdoj6387]AraBellaC

https://www.cheasim.com/acm/2018/11/18/hdoj6387-AraBellaC.html

作者
CheaSim

发布于
2018-11-18

更新于
2018-11-18

许可协议

#[二分](https://www.cheasim.com/tags/%E4%BA%8C%E5%88%86/)




