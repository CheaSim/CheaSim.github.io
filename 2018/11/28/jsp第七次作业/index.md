# jsp第七次作业

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/11/28/jsp%E7%AC%AC%E4%B8%83%E6%AC%A1%E4%BD%9C%E4%B8%9A/
发布日期：2018-11-28
更新日期：2018-11-28





# jsp大作业

作业要求

- mysql + CRUD

- 校验器

- Struts2+Hibernate 框架

- css美化

## 文件结构

![image-20181128192100403](https://www.cheasim.com/Users/cheasim/Library/Application Support/typora-user-images/image-20181128192100403.png)

## 运行截图

### 登陆界面

![image-20181128192157690](https://www.cheasim.com/Users/cheasim/Library/Application Support/typora-user-images/image-20181128192157690.png)

### 选择操作界面

![image-20181128192234733](https://www.cheasim.com/Users/cheasim/Library/Application Support/typora-user-images/image-20181128192234733.png)

### 增加和修改界面

使用了js语言，实现了一个form中有两个按钮，指向不同的action

![image-20181128192321558](https://www.cheasim.com/Users/cheasim/Library/Application Support/typora-user-images/image-20181128192321558.png)

### 校验器

应用对加入学生信息进行校验。

ID必须为0或者不为0开头的数字。

name和address不能为空。

![image-20181128192708351](https://www.cheasim.com/Users/cheasim/Library/Application Support/typora-user-images/image-20181128192708351.png)

### 成功添加后自动转到学生列表(改变也是一样)

![image-20181128192747889](https://www.cheasim.com/Users/cheasim/Library/Application Support/typora-user-images/image-20181128192747889.png)

### 查询和删除

因为用户可能不确定要删除哪一个，所以删除的旁边还有一个查询按钮。根据ID来进行查询。

![image-20181128192905933](https://www.cheasim.com/Users/cheasim/Library/Application Support/typora-user-images/image-20181128192905933.png)

![image-20181128192914679](https://www.cheasim.com/Users/cheasim/Library/Application Support/typora-user-images/image-20181128192914679.png)

## 代码

### 接口代码

![image-20181128193135141](https://www.cheasim.com/Users/cheasim/Library/Application Support/typora-user-images/image-20181128193135141.png)

```java
package

import

import

public
public
public
public
}
```

```java
package

import
import

public
void

List getAll
void
void
List queryStudent
}
```

```java
package

import

import

public

User queryUser
}

```

### 实现类代码

![image-20181128193145593](https://www.cheasim.com/Users/cheasim/Library/Application Support/typora-user-images/image-20181128193145593.png)

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
import

public
private
private
private
public
session = HibernateSessionFactory.getSession();
tx = session.beginTransaction();
}
@Override
public
init();
return
}
@Override
public
session.close();
}
@Override
public
Session session = null
session = getSession();
List alist = null
alist = session.createQuery(hql).list();
session.close();
return
}
}
```

```java
package

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
String sql = "insert into student (id,name,address) values('"
Integer.toString(student.getId()) +".'"
student.getName()+"','"
student.getAddress()+"')"
;
tx.commit();
session.close();
}

@Override
public
init();
List students = session.createQuery("from Student"

//List students  = (Student) session.createQuery("from Student ");
return
}
@Override
public
init();
Student student1 = (Student) session.get(Student.class, new
// hql 查询
//Student student2 = (Student) session.createQuery("from Student where id="+student.getId());
// sql 查询
//Query query = session.createSQLQuery("select * from student where id="+student.getId()).addEntity(Student.class);
//Student student3 = (Student) query.list();
student1.setName(student.getName());
student1.setAddress(student.getAddress());
session.update(student1);
tx.commit();
session.close();
}
@Override
public
init();
Student student1 = (Student) session.get(Student.class, student.getId());
// hql查询
//Student student2 = (Student) session.createQuery("from Student where id="+student.getId());
// sql 查询
//Query query = session.createSQLQuery("select * from student where id="+student.getId()).addEntity(Student.class);
//Student student3 = (Student) query.list();
if
session.delete(student1);
}
tx.commit();
session.close();
}
@Override
public
init();
Criteria criteria
= session.createCriteria(Student.class).add(Restrictions.like("id"
//hql 查询
Query query = session.createQuery("from Student where id="
// sql 查询
//Query query = session.createSQLQuery("select * from student where id="+student.getId()).addEntity(Student.class);
//List students2 = query.list();
List students = criteria.list();
//return students2;
return
}
}

```

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
Criteria criteria
= session.createCriteria(User.class).add(Restrictions.like("username"

User user = (User)criteria.uniqueResult();

return
}
}

```

### action类代码

![image-20181128193156432](https://www.cheasim.com/Users/cheasim/Library/Application Support/typora-user-images/image-20181128193156432.png)

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
students = dao.queryStudent(student);
return
}
public

dao.changeStudent(student);
return
}
public
dao.deleteStudent(student);
return
}
public
System.out.println("校验器!"
}
public
if
Integer ID = student.getId();
String IID = ID.toString();
if
this
}
if
this
}
if
this
}

}
super
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

```java
package

import
import
import
import

public

private
private

public
User tempuser = dao.queryUser(user.getUsername());
if
return
}else
return
}
}
public
return
}

public
this
}

}

```

### Hibernate配置文件

#### cfg.xml

```xml

123456789101112131415

### model类 Student User

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

public
private
private
public
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
User user = (User) o;
return
Objects.equals(password, user.password);
}

@Override
public
return
}
}

```

### Struts2配置文件

12345678910111213141516171819202122232425262728293031323334353637383940414243444546                                        listStudents.action                        add.jsp                                            listStudents.action                                                        index.jsp                                                        queryStudent.jsp                                                        success.jsp                                         index.jsp            login.jsp

## 前端代码

### css

```css
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
73
74
75
76
77
78
79
80
81
82
83
84
85
86
87
88
89
90
91
92
body
{
background
background-size
background-attachment
}
form
display
margin-top
}
h1
{
color
text-align
}
p
{
font-family
font-size
}
table
{
border-collapse
}
table
{
border
border-bottom-color
}
form
{
background
border
font-family
font-size
border-radius
}
.input_control
width
margin
}
.error_message
color
font-size
}
input
box-sizing
text-align
font-size
height
border-radius
border
color
-web-kit-appearance
-moz-appearance
display
outline
padding
text-decoration
width
}
input
box-sizing
text-align
font-size
height
border-radius
border
color
-web-kit-appearance
-moz-appearance
display
outline
padding
text-decoration
width
}
input
border
}
.button
background-color
border
color
padding
text-align
text-decoration
display
font-size
border-radius
}

```

### JSP

第一个页面

```jsp
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

登陆界面

# 管理员登陆界面

```

选择页面

123456789101112131415161718192021222324252627282930313233343536373839404142434445464748495051525354555657585960616263  学生登录系统              .button{            background-color: #af8c99; /* Green */            border: none;            color: white;            padding: 15px 30px;            text-align: center;            text-decoration: none;            display: inline-block;            font-size: 24px;            border-radius:13px;        }                function goAdd(){            document.myform.action='add.jsp';            document.myform.submit();        }        function goDelete(){            document.myform.action='queryStudent.jsp';            document.myform.submit();        }    学生系统学生一览                                                                                                         0">            Student Id      Name      Address

增加和修改

```jsp
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

增加学生

```

查询和删除

```jsp
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

查询结果

# 学生查询结果

Student Id
Name
Address

```

jsp第七次作业

https://www.cheasim.com/uncategorized/2018/11/28/jsp%E7%AC%AC%E4%B8%83%E6%AC%A1%E4%BD%9C%E4%B8%9A.html

作者
CheaSim

发布于
2018-11-28

更新于
2018-11-28

许可协议




