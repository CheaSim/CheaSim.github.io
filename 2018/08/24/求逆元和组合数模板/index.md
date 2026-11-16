# 求逆元和组合数模板

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/08/24/%E6%B1%82%E9%80%86%E5%85%83%E5%92%8C%E7%BB%84%E5%90%88%E6%95%B0%E6%A8%A1%E6%9D%BF/
发布日期：2018-08-24
更新日期：2018-08-24

整理递推求逆元、阶乘与组合数的竞赛代码模板。




# 求逆元

## $O(n)$求逆元

```cpp
ll inv[maxn];
inv[1
rep(i,2
inv[i] = inv[mod%i] * (mod-mod/i) % mod;
```

## $O(n)$求阶乘

```cpp
ll f[maxn];
ll f[1
rep(i,2
f[i] = f[i-1
```

## 求$n\choose k$

```cpp
ll cur,p[maxn],q[maxn],inv[maxn];
ll C
return
}
ll c
if
if
return
}
void
p[0
for
inv[i] = (mod-mod/i)*inv[mod%i]%mod;
q[i] = q[i-1
p[i] = p[i-1
}
}
//在每次的时候就得cur初始化为1
```

## 求$A^k_n$

```cpp
int
return
}
```

求逆元和组合数模板

https://www.cheasim.com/acm%E6%A8%A1%E6%9D%BF/2018/08/24/%E6%B1%82%E9%80%86%E5%85%83%E5%92%8C%E7%BB%84%E5%90%88%E6%95%B0%E6%A8%A1%E6%9D%BF.html

作者
CheaSim

发布于
2018-08-24

更新于
2018-08-24

许可协议




