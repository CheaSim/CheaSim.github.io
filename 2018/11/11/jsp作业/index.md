# jsp作业

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/11/11/jsp%E4%BD%9C%E4%B8%9A/
发布日期：2018-11-11
更新日期：2018-11-11





# jsp第五次上机

## 题目1

实现Hibernate的增加数据功能

## 题目2

实现Hibernate的查找数据功能

## 项目构成

DAO是项目的功能接口类，DAOImpl是DAO功能接口的实现类。AddStudent是主要的Action类，有两个方法，一个是增加学生数据一个是显示学生数据。Student和hbm由IDE自动根据数据库生成。

## java类函数代码

#### 接口类

```java
package
import
import

public
public
public
}
```

#### 实现类

```java
package

import
import
import
import
import
import

import
import

public
SessionFactory sessionFactory = null
Session session = null
Transaction tx = null
public
public
sessionFactory = new
configure("hibernate.cfg.xml"
buildSessionFactory();
session = sessionFactory.openSession();
tx = session.beginTransaction();
}
@Override
public
init();
session.save(student);
tx.commit();
}

@Override
public
init();
List students = session.createQuery("from Student"
return
}
}
```

#### Action类

```java
package

import
import
import
import
import
import
import

public
private
private
private
public
return
}
public

dao.saveStudent(student);
return
}
public

students = dao.getAll();
return
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

#### model类

```java
package

import
import
public
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

@Override
public
if
if
Student that = (Student) o;
return
Objects.equals(name, that.name) &&
Objects.equals(address, that.address);
}

@Override
public
return
}
}

```

#### 对应的数据库mapping

```xml

 students = students = session.createQuery("from Student"
for
Object[] o = (Object[])iter.next();
System.out.println(o[0
}
}
}
```

#### 显示页面

写了两种显示方式

1234567891011121314151617181920212223242526272829303132333435363738394041424344454647  Hello World                        ID      Name      Address                                                   0">            Student Id      Name      Address

## 运行界面

输入信息之后submit加载到数据库中，并显示数据库中所有数据。

jsp作业

https://www.cheasim.com/uncategorized/2018/11/11/jsp%E4%BD%9C%E4%B8%9A.html

作者
CheaSim

发布于
2018-11-11

更新于
2018-11-11

许可协议




