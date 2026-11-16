# web应用开发笔记

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/09/03/web%E5%BA%94%E7%94%A8%E5%BC%80%E5%8F%91%E7%AC%94%E8%AE%B0/
发布日期：2018-09-03
更新日期：2018-09-03





# web应用开发

现代人的生活方式

- 移动端,mobile

- 浏览器,browser

10年前还是以客户端,client软件形式。

## 两个主流技术

- .Net

- J2ee

.Net过气了，用J2ee

### J2ee的三个方面

- M 模型:负责数据方面的事情，数据分为两个方面，store存储，access访问。依靠模型完成这个功能。
承载数据。

- 把数据中的信息进行表达convey，存储信息和加工信息。

- 不只是一个dbms。

- V 视图:将信息呈现出来，view显示。
把数据呈现给用户。

- 承载用户修改功能，使用户能够修改信息。

- C 控制:把用户的信息进行处理(按照一定的算法和一定的逻辑)，之后再保存在M端。

summary：M存储信息，V交互，C逻辑控制（算法）。

梅宏，杨芙青，吕健——网构建

### 开发V端

V html,jsp,css,jQuery

自学html。 在w3c学

jQuery,是js的一个库。

extjs 扩展版js 丰富了UI设计功能

### 开发M端

MySql，Oracle，SQL server,DB2,Access

框架Hibernate统一了不同的dbms的操作。

缺点：是将数据和公共模型进行映射，一旦确定就不好改变，开发的时候麻烦。

iBatis 容易改进的框架

MyBatis

### 开发C端

struts 框架，把数据进行逻辑处理之后保存到M端。

jQuery js spring 开发代码是Java。framework

## 开发模式

Html + css + mySQL 几种在view端和modle端

jsp + css + mySQL

jQuery+css+mySQL

PHP + css + mySQL

这些都是小型网站。 乐色

我们的模式

JSP+Struts+mySQL  plus + spring + ssh

Real 项目： JSP + SSH + CSS + MYSQL

### SSH Spring Struts Hibernate

## JSP详解

## element 语素

```jsp

```

### 有三类语句

- 表达式

- 小脚本

- 声明

### 声明

table称为一个标签，tag。标签有很多属性

## 看看JSP和mySQL

NaviCat可视化操作MySQL

1433 SQLServer

3306 mySQL 端口

各种端口号是必记。

### Myecl

集成了子IDE,所以比较方便。

### JAR包

是将java代码和文档集成在一个包中。

5.1.35java connect是可以用的

jdbc driver

URL，第一节是JDBC协议，第二节是MySQL表示数据库名称，第三节是代表这MySQL服务器的名字，localhost 127.0.0.1,第四节是端口号。后面都删掉。后面是连着的库。

driver name 随便取。

Schema 是 database的超集。 datebase是table的超集。

### 数据库

```jsp
StringTypeConversion //把子段转化成串
```

connection transantion statement resultset

先建立连接，使用JSP连接MySQL

getConnection函数是静态类型，可以通过类名直接调用函数。

语句分为两方面

- 静态的，

- 动态的，是由运行时候确定的查询和修改语句

获得了resultset之后因为其中有很多条记录，所以必须要用循环。resultset自带了迭代器，iterator。一行一行，一个记录一个记录访问。

```jsp
//把当前指针指向的record赋予re,之后指针往下走。
while
TypeConversion(rs,Type.VARCHAR,1
//and so on 把结果串加入过来。

}
```

```jsp
rs.close();
stmt.close();
conn.close();
// 记得关闭连接 一级一级一级往回退
```

### 交互界面(登陆界面)

早年窗口还叫Window，现在流行叫frame。

- 使用html的指令去做

- 使用JSTL做窗口，使用扩展模板库

```html

- web.xml

- 配置struts.xml文件

- 建立Action类文件

- 建立Action执行后转向的jsp文件。

## 例子

${message} 直接将message类中的信息直接输出出来。

他把control端的数据在页面里输出出来。

那么如何把view端的数据在control中获得呢？

### 实现原理

- 数据共享 data sharing

- 配置文件 configuration

struts2提供在一个类中，具有一定特征的函数就可以映射成actions。

### result

dispatcher分发包裹的方式，之前建立的页面缺省的是dispatcher。

web应用开发笔记

https://www.cheasim.com/%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0/2018/09/03/web%E5%BA%94%E7%94%A8%E5%BC%80%E5%8F%91%E7%AC%94%E8%AE%B0.html

作者
CheaSim

发布于
2018-09-03

更新于
2018-12-08

许可协议

#[web](https://www.cheasim.com/tags/web/)




