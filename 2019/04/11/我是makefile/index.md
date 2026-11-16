# 我是Makefile

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2019/04/11/%E6%88%91%E6%98%AFmakefile/
发布日期：2019-04-11
更新日期：2019-04-11





# 我是Makefile

我是makefile而不是makelove。最近学校开了Linux这门课，于是我就开始自学Linux了，看的是《Linux就是这个范儿》。实名制推荐，语言又风趣又实在。

## 什么是Makefile

作为一名程序员，我们第一个程序大概率是通过vs或者是vc6.0来写的。这些都是IDE集成开发环境，他们帮我们做了很多事情，很多底层的事情。其中比较重要的就是编译这个命令了。如果像我参加acm的，会知道如果经常只是写一个单cpp文件的话，我们只需要使用GCC中的g++命令就可以完成将cpp文件编译成可执行文件，但是如果我们是写一个项目呢？如果我们的项目中有好几个头文件，好几个cpp文件呢？这时候makefile就出现了。

Makefile的作用就是自动化编译，一旦我们写好了makefile文件，只需要一个make命令，整个工程就能自动编译。Makefile定义了一系列的规则，来指定哪些文件需要先编译，哪些文件需要后编译，就像一个shell脚本一样。

> IDE是高手的挡泥板，却是新手的遮阳伞。

我在南大的编译原理课件中就看到，他们项目的要求也是要用Makefile来完整的做一个项目的。南大还是南大啊。

## Makefile的基本概念

### 目标、条件和命令

对于Makefile来说，最最重要的就是目标、条件和命令这三大要素。

- 目标是make要产生的东西或者是要做的事情

- 条件是用于产生目标所需要的文件

- 命令是有条件转化为目标的方法

举个例子

```makefile
main.o:main.c line.h buffer.h tedef.h
cc -c -o main.o main.c
```

main.o就是目标，main.c line.h buffer.h tedef.h就是条件，最下面那句”cc -c -o main.o main.c”就是命令。

all命令就是Makefile的默认目标。

### 基本语法

Makefile是看成是一种解释型语言，一般解释型语言都是采用“自顶向下”的解释逻辑。

tip:所有命令都是需要以\tab开头的，规定如此

### 变量

作为一种类似语言的东西，那么变量肯定是少不了啊。Makefile中的变量类似于宏替代，采用的语法。

```makefile
CC := gcc -g
```

这就定义了一个变量，变量的名称是CC，变量的值是”gcc -g”，我们可以用”$()或者${}”来替代。

### 自动变量

Makefile中有特殊变量，他们可以自动取用一条规则中目标和条件中的元素，这样就可以节省输入文件名和条件文件名的力气。ps:确实在vim一键编译中我也看到了类似的东西。

并且自动变量不需要加$().

我是Makefile

https://www.cheasim.com/%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0/2019/04/11/%E6%88%91%E6%98%AFMakefile.html

作者
CheaSim

发布于
2019-04-11

更新于
2019-04-11

许可协议

#[学习笔记](https://www.cheasim.com/tags/%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0/)




