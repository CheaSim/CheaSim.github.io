# 逆元模板

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/08/19/%E9%80%86%E5%85%83%E6%A8%A1%E6%9D%BF/
发布日期：2018-08-19
更新日期：2018-08-19

收录递推、费马小定理及扩展欧几里得相关的逆元代码模板。




# 求逆元模板

### 递推求逆元

```cpp
int
int
rep(i,2
inv[i] = inv[mod%i]*(mod-mod/i)%mod;
}
```

### 费马小定理求逆元

```cpp
ll extend_gcd
if
if
x = 1
return
}
ll d = extend_gcd(b,a%b,y,x);
y -= a/b*x;
return
}
ll mod_reverse
ll x,y;
ll d = extend_gcd(a,n,x,y);
if
else
}
```

逆元模板

https://www.cheasim.com/acm%E6%A8%A1%E6%9D%BF/2018/08/19/%E9%80%86%E5%85%83%E6%A8%A1%E6%9D%BF.html

作者
CheaSim

发布于
2018-08-19

更新于
2018-08-19

许可协议




