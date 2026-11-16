# JavaBean和Hibernate

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/11/11/javabean%E5%92%8Chibernate/
发布日期：2018-11-11
更新日期：2018-11-11





# javabean学习笔记

参考https://www.cnblogs.com/Qian123/p/5277425.html

## JavaBean简介

javabeans就是符合某种特定规范的Java类，功能区分很明确，并且有如下设计原则

> 公有类，无参的共有构造方法，属性私有，有getter和setter。

## Jsp联动

JavaBean和JSP有关的动作标签有

123

## 如何使用

### 普通的使用

可以当做一个普通的java类在jsp中插入java代码来使用。

具体分析就是：

1、创建一个web project项目。2、在src文件下，创建一个包，在包中创建一个类，满足设计原则即可3、在index.jsp页面中通过import导入之前创建的类（import=”包名.类名”）4、通过使用new创建Javabean实例(创建对象)5、使用set方法赋值6、使用get方法取值

### 使用jsp动作标签

#### useBean

123

其中java类名是java类的全名要有package

#### setProperty

# Hibernate

## ORM

对象关系映射

当我们工作在一个面向对象的系统中时，存在一个对象模型和关系数据库不匹配的时候，在java中他有一个对象关联图。

hibernate将java类映射到数据表中，

## Session

Session用于获取与数据库的物理连接，由于Session对象是轻量级的，并且每次与数据库进行交互都要实例化，持久太对象被保存，并通过Session对象检索找回。

因为Session对象不是线程安全的，应该根据需求被创建或者销毁。他的主要功能是映射实体类的实例提供创建，读取和删除操作。

典型的事务语法。

```java
Session session = factory.openSession();
Transaction tx = null
try
tx = session.beginTransaction();
// do some work
...
tx.commit();
}
catch
if
e.printStackTrace();
}finally
session.close();
}
```

个人认为比较重要的方法

```java
Transaction beginTransaction
//开始工作单位，并返回关联事务对象。

Connection close
//通过释放和清理 JDBC 连接以结束该会话。

Query createQuery
//为给定的 HQL 查询字符创建查询的新实例。

SessionFactory getSessionFactory
//获取创建该会话的 session 工厂。
```

## 持久化类

在 Hibernate 中，其对象或实例将会被存储在数据库表单中的 Java 类被称为持久化类。若该类遵循一些简单的规则或者被大家所熟知的 Plain Old Java Object (POJO) 编程模型，Hibernate 将会处于其最佳运行状态。以下所列就是持久化类的主要规则，然而，在这些规则中，没有一条是硬性要求。

- 所有将被持久化的 Java 类都需要一个默认的构造函数。

- 为了使对象能够在 Hibernate 和数据库中容易识别，所有类都需要包含一个 ID。此属性映射到数据库表的主键列。

- 所有将被持久化的属性都应该声明为 private，并具有由 JavaBean 风格定义的 getXXX 和 setXXX 方法。

- Hibernate 的一个重要特征为代理，它取决于该持久化类是处于非 final 的，还是处于一个所有方法都声明为 public 的接口。

- 所有的类是不可扩展或按 EJB 要求实现的一些特殊的类和接口。

POJO 的名称用于强调一个给定的对象是普通的 Java 对象，而不是特殊的对象，尤其不是一个 Enterprise JavaBean。

他并不是一个javabean

```java
public
private
private
private
private

public
public
this
this
this
}
public
return
}
public
this
}
public
return
}
public
this
}
public
return
}
public
this
}
public
return
}
public
this
}
}
```

关键点 对于s: jstl标签中 查询不能用createSQLquery得用createquery 获得的查询才是正确的查询。属于可以直接放到上面去的。

个人理解

hibernate把数据读入 之后将数据传输给javabean，之后依靠javabean将数据显示在jsp页面上，

## 上课笔记

Hibernate就是实现ORM的一个框架

```xml

- 如果对象是和数据库一直是一样的，那就是持久态。Persistent

- 如果对象是还没有提交到数据库中，就是临时态，Transient

- 如果是对象不和数据库一致 就是游离态 Detached

- 把对象删除了 Removed

可以使用save()函数将Transient状态转化为Persistent

当session.close()以后你再设置对象的状态就是Detached状态了。

### 通过Criteria查询 QBC Query By Criteria

```java
1
2
3
Criteria criteria =
session.createCriteria(Student.class).add(Restrictions.like("id"

```

新建一个约束(查询条件) id=1

(Student.class)强制类型转换 把他变成了Student。

### HQL Hibernate Query Language

可以通过HQL来查询。

HQL使用了类来查询

```java
1
String hql = "from Student"
```

因为Hibernate框架的支持所以只需发要这样写就可以直接查询了。

## 字段操作

基于Hibernate的操作有几种操作

- Session

- HQL

- Criteria

- SQL

解释函数的意义。

```java
1
2
Query query = session.createQuery(hql);

```

query 是流数据，是二进制数据，所以要强制类型转化。

带参数的HQL语句

```java
1
2
3
4
5
6
String hql = "select * from Employee emp where emp.id=:id and emp.name=:name"
Query query = session.createQuery(hql).addEntity(Employee.class);
query.setParameter("id"
query.setParameter("name"
this

```

JavaBean和Hibernate

https://www.cheasim.com/uncategorized/2018/11/11/JavaBean%E5%92%8CHibernate.html

作者
CheaSim

发布于
2018-11-11

更新于
2018-11-19

许可协议




