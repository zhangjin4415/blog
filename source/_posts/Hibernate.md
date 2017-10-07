title: Javaweb框架
date: 2016-04-01 14:15:00
categories: "Javaweb"
tags: ["Javaweb","框架"]
---
主要内容：
<!--more-->
第一章 持久层Hibernate
============================
本章介绍：本章讲解Hibernate基础，核心，与Mysql集合开发
1.Hibernate基础
-------------------------
1.1 介绍
Hibernate提供与数据库无关的API接口，可以让开发人员不关心数据库的差异，而是关心业务层的开发。Hibernate对JDBC进行了轻量级的封装。
Hibernate是一个JDO工具，通过文件把值对象和数据库表之间建立起映射关系。我们通过操作这些值对象和Hibernate提供的一些基本类就可以达到使用数据库目的。
操作数据库经历了三个阶段:操作JDBC,封装JDBC，ORM；这里只是介绍ORM。
ORM（Object Relational Mapping）对象关系映射是解决面向对象与关系数据库存在的不匹配的技术，ORM通过描述对象和数据库之间映射的元数据将java对象自动持久化到关系数据库。
数据实体3种表现形式：数据实体，数据表，映射对象。
部分流行ORM产品：Apache OJB,Hibernate,iBATIS,Cayenne等。
持久层框架方向：直接编写JDBC等SQL语句（eg:iBATIS）;O/R Mapping(eg:Hibernate)和JDO技术；EJB中实体Bean技术。

1.2 Hibernate配置与开发流程
(1)添加库包
下载MYSQL驱动mysql-connector-java-5.0.8-bin.jar
下载Hibernate安装包hibernate-3.0.zip
根目录下核心包:hibernate3.jar
lib目录下必需包：
cglib-2.1.jar、asm-attr.jar、asm.jar:CGLIB库，Hibernate用来实现PO字节码的动态生成；
dom4j-1.6.jar:dom4j类似于jdom,是一个XML API，用来读写XML文件；
commons-collections-2.1.1.jar:Apache Commons包中的一个，包含一些Apache开发的集合类，比java.util.*强大；
commons-logging-1.0.4.jar、log4j-1.2.9.jar:日志功能。
其他包非必需，这里不介绍，需要时查询资料。

项目下新建lib文件夹，将需要导入的库包复制到lib目录，选中包右键->Build Path->Add To Build Path添加库包

(2)Hibernate配置文件
配置文件包含一系列属性的配置，Hibernate根据这些属性来连接数据库。
配置有两种：properties与xml
properties与xml配置文件可以同时使用，当同时使用两种类型的配置文件时，在XML配置文件中的设置会覆盖properties配置文件的相同属性。

A.properties
hibernate.properties样例
```
hibernate.dialect=net.sf.Hibernate.dialect.MYSQLDialect //指定数据库使用SQL方言
hibernate.connection.driver_class=com.mysql.jdbc.Driver //指定驱动程序
hibernate.connection.url=jdbc:mysql://localhost:3306/test //指定数据库的URL
hibernate.connection.username=root //指定数据库的用户名
hibernate.connection.password=123456 //指定数据库密码
hibernate.show_sql=true //默认为false，为true时运行时控制台输出SQL语句
```
默认文件名hibernate.properties
样例位置：Hibernate软件包的etc目录
在项目中放置位置：必须在CLASSPATH指定位置中，如主程序执行位置或者WEB-INF/classes中
获取SessionFactory:
```
Configuration cfg=new Configuration().addClass(com.demo.hiberate.beans.User.class);//加载com/demo/hibernate.beans/User.hbm.xml
SessionFactory session=cfg.buildSessionFactory();
```

B.XML
XML格式配置文件除了基本的Hibernate配置信息，还可以指定具体的持久化类映射文件，避免将持久化类配置文件编码在程序中。
hibernate.cfg.xml样例
```
<?xml version='1.0' encoding='UTF-8'?>
<!DOCTYPE hibernate-configuration PUBLIC
	"-//Hibernate/Hibernate Configuration DTD 3.0//EN"
	"http://hibernate.sourceforge.net/hibernate-configuration-3.0.dtd">

<hibernate-configuration>
	<session-factory>
		<property name="myeclipse.connection.profile">JDBC for MySQL</property>
		<!-- 显示执行的sql语句 -->
		<property name="show_sql">true</property>
		<!-- 连接字符串 -->
		<property name="connection.url">jdbc:mysql://localhost:3306/test</property>
		<!-- 数据库用户名 -->
		<property name="connection.username">root</property>
		<!-- 数据库密码 -->
		<property name="connection.password">123456</property>
		<!-- 数据库驱动 -->
		<property name="connection.driver_class">com.mysql.jdbc.Driver</property>
		<!-- 使用的方言 -->
		<property name="dialect">org.hibernate.dialect.MySQLDialect</property>
		<!-- 映射文件 -->
		<mapping resource="com/demo/hibernate/beans/User.hbm.xml"/>
	</session-factory>
</hibernate-configuration>
```
默认文件名hibernate.cfg.xml
样例位置：Hibernate软件包的etc目录
在项目中放置位置：必须在CLASSPATH指定位置中，如主程序执行位置或者WEB-INF/classes中
获取SessionFactory:
```
SessionFactory session=new Configuration().configure().buildSessionFactory();
//默认XML文件名称是hibernate.cfg.xml，也可以指定文件的名称如下
SessionFactory session=new Configuration().configure("dbt.cfg.xml").buildSessionFactory();
```

(3)开发流程
包含三步：创建Hibernate配置/映射文件/持久化类/辅助类、编写DAO层、编写Service层。



1.3 实例
通过用户名密码实现用户验证。
编写流程:创建数据库；添加配置文件hibernate.cfg.xml;编写映射文件User.hbm.xml;编写持久化类User.java;编写辅助类HibernateSessionFactory.java;编写DAO类UserDAO.java;编写Service类UserService.java。

(1)添加驱动和库包

(2)创建数据库hibernate，数据表user

| 名称 | 类型   | 空  | 默认值   |
| ----| -------| ----| --------|
| id| int| no| <auto_increment>|
| username| varchar(48)| yes| null|
| password| varchar(48)| yes| null|
| email| varchar(48)| yes| null|

添加一组数据1,admin,admin,12345@qq.com

(3)添加配置文件hibernate.cfg.xml
在项目的src目录下添加hibernate.cfg.xml
```
<!DOCTYPE hibernate-configuration PUBLIC
	"-//Hibernate/Hibernate Configuration DTD 3.0//EN"
	"http://hibernate.sourceforge.net/hibernate-configuration-3.0.dtd">

<hibernate-configuration>
	<session-factory>
		<property name="myeclipse.connection.profile">JDBC for MySQL</property>
		<property name="connection.url">jdbc:mysql://127.0.0.1:3306/test</property>
		<property name="connection.username">root</property>
		<property name="connection.password"></property>
		<property name="connection.driver_class">com.mysql.jdbc.Driver</property>
		<property name="dialect">org.hibernate.dialect.MySQLDialect</property>
		<property name="show_sql">true</property>
		<mapping resource="com/hibernate/beans/User.hbm.xml"/>
	</session-factory>
</hibernate-configuration>
```

(4)编写映射文件User.hbm.xml
hibernate映射文件包含了对象/关系映射(O/R Mapping)所需的元数据，元数据包含持久化类声明和属性到数据库的映射;
映射文件负责持久化类与数据库表之间的映射，根元素是hibernate-mapping,并通过package指定类所在的包；
每一个表使用一个class定义，name属性表示类的名称，table表示关联的表名，通过property子元素来映射类的变量名与数据库表字段名之间的映射关系。
User.hbm.xml
```
<!DOCTYPE hibernate-mapping PUBLIC
	"-//Hibernate/Hibernate Mapping DTD 3.0//EN"
	"http://hibernate.sourceforge.net/hibernate-mapping-3.0.dtd">

<hibernate-mapping package="com.hibernate.beans">
	<class name="User" table="user">
		<id name="id" column="id" type="integer">
			<generator class="native"/>
		</id>
		<property name="username" column="username" type="string"></property>
		<property name="password" column="password" type="string"></property>
		<property name="email" column="email" type="string"></property>
	</class>
</hibernate-mapping>
```

(5)编写持久化类User.java
Hibernate使用简单的java对象(Plain Old/Ordinary Java Objects就是POJOs)编程模型持久化；POJO类似javabean,通过getter、sertter方法访问属性。
POJO规则：
a.为属性值声明set/get方法；
b.实现一个默认的无参构造方法;
c.提供一个标识属性；
d.使用非final类。
User.java
```
package com.hibernate.beans;

public class User {
	private Integer id;
	private String username;
	private String password;
	private String email;
	
	public User() {
	}

	public Integer getId() {
		return id;
	}

	public void setId(Integer id) {
		this.id = id;
	}

	public String getUsername() {
		return username;
	}

	public void setUsername(String username) {
		this.username = username;
	}

	public String getPassword() {
		return password;
	}

	public void setPassword(String password) {
		this.password = password;
	}

	public String getEmail() {
		return email;
	}

	public void setEmail(String email) {
		this.email = email;
	}
}
```
备注:getXXX()、setXXX方法必须如getUsername形式，getUSERNAME、getusername等运行会提示异常

(6)编写辅助类HibernateSessionFactory.java
Hibernate的Session是一个持久化管理器，通过它可以从数据库中存取User。
```
SessionFactory sessionFactory = new Configuration().configure().buildSessionFactory();
```
对configure()调用装载hibernate.cfg.xml配置文件并初始化为一个Configuration实例；SessionFactory通常只是初始化一次。
```
package com.hibernate.util;

import org.hibernate.HibernateException;
import org.hibernate.Session;
import org.hibernate.SessionFactory;
import org.hibernate.cfg.Configuration;

public class HibernateSessionFactory {
	private static String CONFIG_FILE_LOCATION="/hibernate.cfg.xml";
	private static final ThreadLocal THREAD_LOCAL=new ThreadLocal();
	private static Configuration cfg=new Configuration();
	private static SessionFactory sessionFactory;
	//获取Session
	public static Session currentSession() throws HibernateException{
		Session session= (Session) THREAD_LOCAL.get();
		if(session==null){
			cfg.configure(CONFIG_FILE_LOCATION);
			sessionFactory=cfg.buildSessionFactory();
			session=sessionFactory.openSession();
			THREAD_LOCAL.set(session);
		}
		return session;
	}
	//关闭Session
	public static void closeSession() throws HibernateException{
		Session session=(Session) THREAD_LOCAL.get();
		THREAD_LOCAL.set(null);
		if(session!=null){
			session.close();
		}
	}
}
```

(7)编写DAO类UserDAO.java
DAO(Data Access Object)层，就是数据访问接口，为基于Hibernate开发，通常将业务层与数据层分开；DAO层只是负责调用Hibernate API实现CRUD操作，Service层面向用户负责调用DAO层代码；使得数据层不用关心业务功能，更好实现移植。
这里编写一个DAO类UserDAO.java实现根据用户名查询用户对象；使用HibernateSession获得Session对象，然后通过Session执行事务，创建查询对象，返回查询的用户对象。
```
package com.hibernate.dao;

import org.hibernate.HibernateException;
import org.hibernate.Query;
import org.hibernate.Session;
import org.hibernate.Transaction;

import com.hibernate.beans.User;
import com.hibernate.util.HibernateSessionFactory;

public class UserDAO {
	public User getUser(String username) throws HibernateException{
		Session session=null;
		Transaction tx=null;
		User user=null;
		
		try{
			session=HibernateSessionFactory.currentSession();
			tx=session.beginTransaction();
			Query query=session.createQuery("from  User where username=?");///////////////
			query.setString(0, username.trim());
			user=(User) query.uniqueResult();
			query=null;
			tx.commit();
		}catch(HibernateException e){
			throw e;
		}finally{
			if(tx!=null){
				tx.rollback();
			}
			HibernateSessionFactory.closeSession();
		}
		return user;
	}
}
```

(8) 编写UserService.java
Service层为服务层，面向用户服务，其定义的方法与实际的业务相关，它有一个函数valid(),根据用户和密码来判断用户是否存在，该函数调用DAO层的UserDAO类来获取一个用户对象，并比较该对象的密码与输入密码是否相等，相等则返回true,否则返回false.可以用一个main函数进行测试。
```
package com.hibernate.service;

import com.hibernate.beans.User;
import com.hibernate.dao.UserDAO;

public class UserService {
	public boolean valid(String username,String password){
		UserDAO test=new UserDAO();
		User user=test.getUser("admin");
		if(user.getPassword().equals(password)){
			return true;
		}else{
			return false;
		}
	}
	public static void main(String[] args) {
		UserService service=new UserService();
		boolean login=service.valid("admin", "admin");
		System.out.println("验证结果:"+login);
	}
}
```
运行查看结果：
选中UserService.java右键run as->java Application即可。
如有异常请看错误总结。
```
Hibernate: select user0_.id as id, user0_.username as username0_, user0_.password as password0_, user0_.email as email0_ from user user0_ where user0_.username=?
验证结果:true
```

1.4 自动生成工具MiddleGen
可以选择手写XML映射文件，也可以使用一些工具来生成映射文件。如：XDoclet,MiddleGen,AndroMDA.
有一些工具可以实现数据库SQL、Hibernate映射文件、Hibernate持久化类之间的相互转化。
![image](img/hibernate/1.png)
MiddleGen应用流程：
(1)安装Ant
MiddleGen依赖于Ant运行，可以在http://ant.apache.org下载Ant版本apache-ant-1.9.7.bin.zip.
Ant是免安装的，解压到安装目录后配置环境变量即可。
```
ANT_HOME:D:\SSH2\apache-ant-1.9.7
path添加:%ANT_HOME%\bin
```
添加后输入ant命令有反应就说明安装成功，具体如下：
```
C:\Users\zhang>ant
Buildfile: build.xml does not exist!
Build failed
```

(2)安装MiddleGen
下载MiddleGen包，这里下载middlegen-2.1.zip解压
安装后使用，鉴于时间问题，这里不在详解，详见《java高手真经-Java web核心框架篇》84页s


2.Hibernate核心
----------------------
2.1 Hibernate映射文件hbm.xml
hbm.xml反映持久化类与关系数据库之间的映射关系。

&lt;hibernate-mapping&gt;
根元素----每个hbm.xml文件只有唯一一个。
属性列表：

| 属性名称  | 描述 | 可选值 | 默认值  | 是否必选  |
| ---------| -----| ------| -------| ----------|
| package| 指定包名，映射文档没有指定全限定的类名时用其作为包名|  |  | 否|
| schema| 数据库schma的名称| | | 否|
| catalog| 数据库catalog的名称| | | 否|
| default-cascade| 默认的级联风格| | none | 否|
| default-access| Hibernate用来访问属性的策略，可以通过实现PropertyAccessor接口自定义| field,property,className| property| 否|
| default-lazy| 指定了未明确标注lazy属性的java属性和集合类，Hibernate会采用什么样的默认加载风格| true,false| true| 否|
| auto-import| 指定我们是否可以在查询语言中使用非全限定的类名| true,false| true| 否|

指定了schema和catalog属性则表名会加上所指定的schema和catalog的名字扩展为全限定名，如果没有指定，则表名不会使用全限定名。
auto-import属性默认让我们在查询语言中可以使用非全限定名的类名，如果两个非全限定名是一样的（两个类名字一样，包不一样），那么应该设置auto-import="false",否则会出现异常。

备注：&lt;hibernate-mapping&gt;元素允许嵌套多个&lt;class&gt;映射，但建议一个持久化类一个映射文件，并以持久化类名命名。


&lt;class&gt;
&lt;hibernate-mapping&gt;的子元素，用以定义一个持久化类与数据表的映射关系。
属性列表：
![image](img/hibernate/2.png)
![image](img/hibernate/3.png)
class也可以是一个接口，之后用<subclass>来指定该接口的实际实现类。也可以持久化任何static内部类。

使用&lt;id&gt;定义主键
主键用来识别记录，并保证每条记录的唯一性。
对象标识符OID是关系数据库中主键在java对象模型中的等价物：
```
Transaction tx=session.beginTransaction();
//加载OID为1的User对象，从数据库中查找ID为1的记录，然后创建相应的User实例
User user1=(User)session.load(User.class,new Long(1));
User user1=(User)session.load(User.class,new Long(1));
User user1=(User)session.load(User.class,new Long(3));
System.out.println(user1==user2);//true
System.out.println(user1==user3);//false
```
&lt;id&gt;属性列表：

| 属性名称| 描述| 可选值| 默认值| 是否必选|
| --------| ---| -----| -----| -------|
| name| 标识属性的名字|  | | 否|
| type| 标识Hibernate类型的名字| | 属性名| 否|
| column| 主键字段名字| | | 否|
| unsaved-value| 用来标志该实例是刚刚创造的，未保存；可以把这种实例和以前在Session中装载过但是没有再次持久化的实例区分开| null,any,none,undefined,id_value| | 否|
| access| Hibernate用来访问属性的策略| field,property,ClassName| property| 否|

如果name不存在，则会认为这个类没有标识属性，如果类的标识属性不是正常的java默认值(null或者0)，那么应该指定正确的unsaved-value默认值。
如果表使用联合主键，那么可以映射类的多个属性作为标识符属性。&lt;composite-id&gt;元素接受&lt;key-property&gt;属性映射和&lt;key-many-to-one&gt;属性映射作为子元素。
```
<composite-id>
	<key-property name="username"/>
	<key-property name="password"/>
</composite-id>
```
此时持久化类必须重载equals()和hashCode()方法，来实现组合的标识符的相等判断，实现Serialzable接口也是必须的。

&lt;generator&gt;设置主键生成方式
&lt;generator&gt;指定主键的生成器，通过一个class属性指定生成器对应的类。该类必须实现org.hibernate.IdentifierGeneator接口。如果需要传递参数，需要通过&lt;param&gt;子元素指定；
```
<id name="id" column="ID" type="long">
	<generator class="hilo">
		<param name=""table">uid_table</param>
		<param name="column">next_hi_value_column</param>
	</generator>
</id>
```
Hibernate内置生成器:
assigned算法：generator没有指定时的默认生成器；主键由外部程序负责生成，无须Hibernate参与,需要应用程序在执行save()之前为对象分配一个标识符。






3.Hibernate——mysql开发
-----------------






错误总结
================
1.hibernate，自己写的xxx.hbm.xml文件 出现错误：Attribute "column" must be declared for element type"property"
----------------------------------------
因为复制了hibernate.cfg.xml的头部文件
<?xmlversion='1.0' encoding='UTF-8'?>
<!DOCTYPE hibernate-configuration PUBLIC
         "-//Hibernate/Hibernate Configuration DTD 3.0//EN"
         "http://hibernate.sourceforge.net/hibernate-configuration-3.0.dtd">

改为mapping的头文件就行了
<?xmlversion="1.0" encoding="UTF-8"?>
<!DOCTYPEhibernate-mapping PUBLIC
         "-//Hibernate/Hibernate Mapping DTD 3.0//EN"
         "http://hibernate.sourceforge.net/hibernate-mapping-3.0.dtd">

2.org.hibernate.PropertyNotFoundException:Could not find a setter for property username in class com.zhang.hibernate.User
-----------------------------------
编写持久化类User.java时getXXX()、setXXX方法必须如getUsername形式，getUSERNAME、getusername等运行会提示异常

3. 缺包异常
------------------
3.1 hibernate Exception in thread "main" java.lang.NoClassDefFoundError: net/sf/ehcache/CacheException
缺少ehcache.jar(高速缓存，提高存取速度)包

3.2 Exception in thread "main" java.lang.NoClassDefFoundError: antlr/ANTLRException
缺少antlr.jar包

4.log4j:WARN ...
-----------------------
出现没有定义log4j的警告信息，这是因为添加了log4j.jar包但是没有配置，只需要到hibernate包下面将log4j.properties文件复制到项目的根目录即可。

