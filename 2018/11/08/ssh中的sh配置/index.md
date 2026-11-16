# SSH中的SH配置

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/11/08/ssh%E4%B8%AD%E7%9A%84sh%E9%85%8D%E7%BD%AE/
发布日期：2018-11-08
更新日期：2018-11-08





# IDEA+Hibernate+Struts2

笔者能力有限，只能用老版Hibernate和老版Struts2.

我们在IDEA中选择Struts2中的2.3版本我是直接下了jar包加入进去的，还有自动下载Hibernate3.6中的。之后进行配置。

之后再加入connector我用的是Mysql5.7版本所以用了对应的connector。

之后选择左下角的persistence，右键下面的一个文件之后generate Mapping。

之后选择链接服务器 记得?useSSL=false。之后配置一下hibernate.cfg.xml中的文件,其中username和password和前面四个是自己设置的。

还要选择mapping的class和resource

```xml

update -->
之后把jstl中的jar包加入到tomcat文件夹中。这样就不用每次配置了。

之后在preference中搜索dtds

```cpp
1
http://java.sun.com/jsp/jstl/core
```

url填写这个 之后再搜索你下载好的jstl中的c.tld文件 慢慢找就在里面

下载链接

http://archive.apache.org/dist/jakarta/taglibs/standard/binaries/

```java
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35
36
37
38
39
40
41
42
43
44
45
46
47
48
49
50
51
52
53
54
55
56
57
58
59
60
package

import
import
@Entity
@Table(name="student")
public
@Id
@GeneratedValue
private
@Column(name="name")
private
@Column(name="address")
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
StudentEntity that = (StudentEntity) o;
return
Objects.equals(name, that.name) &&
Objects.equals(address, that.address);
}

@Override
public
return
}
}

```

```java
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35
36
37
38
39
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
@SessionTarget
Session session;
@TransactionTarget
Transaction transaction;
@SuppressWarnings("unchecked")
public

List students = new
try
{
students = session.createQuery("from student"
for
Object[] o = (Object[])iter.next();
System.out.println(o[0
}
}
catch
{
e.printStackTrace();
}
return
}
public

session.save(student);
}
}
```

```java
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35
36
37
38
39
40
package

import
import
import
import
import

public
implements
Student student  = new
List students = new
StudentDAO dao = new
@Override
public
return
}
public

dao.addStudent(student);
return
}
public

students = dao.getStudents();
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

12345678910111213141516171819202122                                                listStudents                                        index.jsp

```java
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35
36
37
38
39
40
41
42
43
44
45
46
47
48
49
50
51
52
53
54
55
56
57
58
59
60
61
62
63
64
65
66
67
68
69
70
71
72

import
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
@Before
public
sessionFactory = new
configure("hibernate.cfg.xml"
buildSessionFactory();
session = sessionFactory.openSession();
tx = session.beginTransaction();
}
//增加
@Test
public
Student ue = new
ue.setName("Anny"
ue.setId(123321
ue.setAddress("wodediercichangshi"
session.save(ue);
tx.commit();
}
//修改
@Test
public
Student user = (Student) session.get(Student.class, new
user.setName("Penny"
session.update(user);
tx.commit();
session.close();
}
//查找
@Test
public
Student user = (Student) session.get(Student.class, new
tx.commit();
session.close();
System.out.println("ID号："
"；密码："
}
//删除
@Test
public
Student user = (Student) session.get(Student.class, new
if
session.delete(user);
}
tx.commit();
session.close();
}

@Test
public
List students = session.createSQLQuery("select *from student"
for
Object[] o = (Object[])iter.next();
System.out.println(o[0
}
}
}
```

SSH中的SH配置

https://www.cheasim.com/%E6%90%AC%E7%A0%96/2018/11/08/SSH%E4%B8%AD%E7%9A%84SH%E9%85%8D%E7%BD%AE.html

作者
CheaSim

发布于
2018-11-08

更新于
2018-11-08

许可协议

#[配置](https://www.cheasim.com/tags/%E9%85%8D%E7%BD%AE/)




