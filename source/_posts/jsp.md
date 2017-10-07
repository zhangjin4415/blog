title: JSP网站开发
date: 2016-03-12 18:53:03
categories: "网站开发"
tags: ["JSP","网站开发"]
---
主要内容：环境搭建，网页布局，JDBC，Servlet
<!--more-->

第一章 环境搭建
============
1.JDK
-----------
JDK(Java Development Kit) 是 Java 语言的软件开发工具包(SDK)。
J2SE：(Java SE/SE)，标准版，是我们通常用的一个版本;
J2EE:(Java EE/EE)，企业版，使用这种JDK开发J2EE应用程序;
J2ME:(Java ME/ME)，主要用于移动设备、嵌入式设备上的java应用程序。
JDK用于编译Java程序，JRE用于运行Java程序。

官网下载：http://www.oracle.com/technetwork/java/javaee/downloads/index.html
安装会连续安装jdk和jre，安装好后配置环境变量：
JAVA_HOME： jdk的安装目录(如E:\Java\jdk)
Path： %JAVA_HOME%\bin;%JAVA_HOME%\jre\bin;（注意原Path末尾有没有;号，没有则先输入）
CLASSPATH： .;%JAVA_HOME%\lib;%JAVA_HOME%\lib\tools.jar（注意最前面有一点）

配置完后cmd下输入java和javac命令没有提示找不到命令则安装配置成功！


2.Myeclipse
------------
在eclipse 基础上加上自己的插件开发而成的功能强大的企业级集成开发环境，主要用于Java、Java EE以及移动应用的开发。
官网下载： http://www.myeclipsecn.com/

安装过程自己网上查，特别多！


3.Tomcat
-------------
Tomcat 服务器是一个免费的开放源代码的Web 应用服务器，属于轻量级应用服务器，在中小型系统和并发访问用户不是很多的场合下被普遍使用，是开发和调试JSP 程序的首选。Tomcat和IIS等Web服务器一样，具有处理HTML页面的功能，另外它还是一个Servlet和JSP容器，独立的Servlet容器是Tomcat的默认模式。不过，Tomcat处理静态HTML的能力不如Apache服务器。常用服务器还有Nginx等。
官网下载： https://tomcat.apache.org/

安装前首先需要配置好java的环境。与一般软件安装无异，直接安装就可以。
安装好打开tomcat安装目录的bin 文件夹，找到里面的执行文件，运行，然后在浏览器上输入本地地址：http：//localhost:8080  或者  http：//127.0.0.1:8080 看到tomcat默认界面则安装成功！


4.Mysql
-------------
本节详见本博客的mysql篇，有详细介绍！


5.小结
----------
本章环境搭建好了就可以进行开发了，Mysql中注意界面化软件连接时尽量用127.0.0.1而不是localhost.有时候用localhost不识别！


第二章 网页布局与修饰-HTML+CSS+JavaScript
=============
本章不讲，详见本博客的Html+css+javascript网页布局篇！


第三章 JDBC
=============
1.介绍与流程
--------
本章不懂的参考对应博客文章mysql
JDBC（Java DataBase Connectivity）是Sun公司开发的针对数据库应用程序的API(应用程序编程接口)，其由Java编写跨平台！
流程：
(1)加载JDBC驱动（首先要导入驱动包）
```
Class.forName("com.mysql.jdbc.Driver");
```
(2)创建连接
```
String url="jdbc:mysql://localhost:3306/test";  //3306--端口 test:数据库名
String username="root";//数据库用户名
String password="";//数据库的密码
Connection conn=DriverManeger.getConnection(url,username,password);
```
(3)获得java.sql.Statement实例
```
Statement s=conn.createStatement();
PreaparedStatement p=conn.prepareStatement(sql);
CallableStatement c=conn.prepareCall("{CALL demoSp(?,?)}");
```
************
执行静态SQL语句：Statement
执行动态SQL语句：PreparedStatement
执行数据库储存过程：CallableStatement
(4)执行SQL语句
```
ResultSet rs=s.executeQuery(String sql);//查询并返回一个ResultSet对象
int rows=s.executeUpdate(String sql);//执行INSERT、UPDATE、DELETE、SQL DDL(数据定义)语句，返回影响行数
boolean flag=s.execute(String sql);//用于执行返回多个结果集、多个更新计数或二者组合的语句
```
(5)处理结果
ResultSet方法：

| 方法       | 描述                         |
| -----------| ----------------------------|
| next()     | 移动到ResultSet下一行        |
| first()    | 移动到ResultSet第一行        |
| last()     | 移动到ResultSet最后一行      |
| previous() | 移动到ResultSet上一行        |

```
String name=rs.getString("name");//根据字段名获取
String passwd=rs.getString(3);//根据列数获取 ------ 此方法更加高效
int id=rs.getInt(1);
```
(6)关闭JDBC对象
关闭顺序是声明顺序的反序
(1)关闭记录集
(2)关闭声明
(3)关闭连接对象
```
rs.close();
s.close();
conn.close();
```


2.JDBC数据类型
--------------
本节参考 http://www.yiibai.com/jdbc/jdbc_data_types.html


3.JDBC事务处理
------------
(1)JDBC事务处理-原子操作
一般应用是多表联系操作，如银行取款。
事务，是指一组原子操作(一组SQL语句执行)的工作单元，要么全部执行，要么全部失败。
JDBC事务步骤：
A.设置事务提交方式为非自动提交
B.将需要添加的代码放try-catch块内
C.try块内添加提交操作，提交事务
D.catch块内添加回滚事务，表示操作出现异常，撤销事务
E.设置事务提交方式为自动提交
实例：
操作前信息表
stu

| id| stuid| name|
| --| -----| ----|
| 1 | 001  | zhang|

stuinfo

| sti_id| city|
| ------| ----|
| 001   | beijin|
| 002   | shanghai|

```
public class JdbcTransation {
	public static void main(String[] args) {
		java.sql.Connection conn=null;
		PreparedStatement pStatement=null;
		try {
			Class.forName("com.mysql.jdbc.Driver");
			conn=DriverManager.getConnection("jdbc:mysql://localhost:3306/test","root","");
			String sql="INSERT INTO stuinfo(stu_id,city) VALUES(?,?)";
			String sql2="DELETE FROM stu WHERE id=1";
			
			conn.setAutoCommit(false);
			pStatement=conn.prepareStatement(sql);
			pStatement.setString(1,"003");//设置学号001
			pStatement.setString(2,"shenzhen");//家庭地址：北京
			System.out.println("第一条语句执行...");
			pStatement.executeUpdate();
			
			pStatement=conn.prepareStatement(sql2);
			System.out.println("第二条语句执行...");
			pStatement.executeUpdate();
			//pStatement.executeQuery();
			conn.commit();	//提交事务
			System.out.println("提交事务...");
		} catch (Exception e) {
			try {
				conn.rollback();//出现异常则回滚事务
				System.out.println("回退事务...");
			} catch (Exception e1) {
				e1.printStackTrace();
			}
			e.printStackTrace();
		}finally{
			try {
				conn.setAutoCommit(true);//设置自动提交
				pStatement.close();
				conn.close();
			} catch (SQLException e) {
				e.printStackTrace();
			}
		}
	}
}
```
操作后信息表
stu

| id| stuid| name|
| --| -----| ----|
| null| null| null|

stuinfo

| sti_id| city|
| ------| ----|
| 001   | beijin|
| 002   | shanghai|
| 003   | shenzhen|

运行正确时:
第一条语句执行...
第二条语句执行...
提交事务...

遇到错误时:
第一条语句执行...
第二条语句执行...
回退事务...

(2)JDBC批量处理
Statement的execute()等方法一次只能一条sql语句，同时执行多条可以用addBatch()方法将要执行的语句加入，然后执行executeBatch()方法，为保证这一批语句全部失败或者全部成功，应该放之于事务中执行。
注意：批处理中执行语句只能是更新语句(insert,delete,update),否则异常。
实例:
采用PreparedStatement方法
```
public class JdbcTransation {
	public static void main(String[] args) {
		java.sql.Connection conn=null;
		PreparedStatement pStatement=null;
		try {
			Class.forName("com.mysql.jdbc.Driver");
			conn=DriverManager.getConnection("jdbc:mysql://localhost:3306/test","root","");
			String sql="INSERT INTO stuinfo(stu_id,city) VALUES(?,?)";
			
			conn.setAutoCommit(false);
			pStatement=conn.prepareStatement(sql);
			pStatement.setString(1,"004");//设置学号001
			pStatement.setString(2,"tianjin");//家庭地址：北京
			pStatement.addBatch();
			pStatement.setString(1, "005");
			pStatement.setString(2, "chongqin");
			pStatement.addBatch();
			pStatement.executeBatch();
			
			conn.commit();	//提交事务
			System.out.println("提交事务...");
		} catch (Exception e) {
			try {
				conn.rollback();//出现异常则回滚事务
				System.out.println("回退事务...");
			} catch (Exception e1) {
				e1.printStackTrace();
			}
			e.printStackTrace();
		}finally{
			try {
				conn.setAutoCommit(true);//设置自动提交
				pStatement.close();
				conn.close();
			} catch (SQLException e) {
				e.printStackTrace();
			}
		}
	}
}
```
采用Statement方法
```
public class JdbcTransation {
	public static void main(String[] args) {
		java.sql.Connection conn=null;	
		Statement statement =null;
		try {
			Class.forName("com.mysql.jdbc.Driver");
			conn=DriverManager.getConnection("jdbc:mysql://localhost:3306/test","root","");
			statement=conn.createStatement();
			
			conn.setAutoCommit(false);
			statement .addBatch("INSERT INTO stuinfo(stu_id,city) VALUES('006','wuhan')");
			statement.addBatch("INSERT INTO stuinfo(stu_id,city) VALUES('007','changsha')");
			statement.executeBatch();
			
			statement.executeBatch();
			conn.commit();	//提交事务
			System.out.println("提交事务...");
		} catch (Exception e) {
			try {
				conn.rollback();//出现异常则回滚事务
				System.out.println("回退事务...");
			} catch (Exception e1) {
				e1.printStackTrace();
			}
			e.printStackTrace();
		}finally{
			try {
				conn.setAutoCommit(true);//设置自动提交
				statement.close();
				conn.close();
			} catch (SQLException e) {
				e.printStackTrace();
			}
		}
	}
}
```

4.应用案例
--------------
(1)信息管理
A.创建商品表
```
root@localhost test>CREATE TABLE goods(
    -> id INT UNSIGNED NOT NULL AUTO_INCREMENT,
    -> name VARCHAR(20),
    -> price INT,
    -> PRIMARY KEY (id));
Query OK, 0 rows affected (0.33 sec)

root@localhost test>DESC goods;
+-------+------------------+------+-----+---------+----------------+
| Field | Type             | Null | Key | Default | Extra          |
+-------+------------------+------+-----+---------+----------------+
| id    | int(10) unsigned | NO   | PRI | NULL    | auto_increment |
| name  | varchar(20)      | YES  |     | NULL    |                |
| price | int(11)          | YES  |     | NULL    |                |
+-------+------------------+------+-----+---------+----------------+
3 rows in set (0.02 sec)
```
B.创建类添加商品并查询
```
public class JdbcTransation {
	static java.sql.Connection conn=null;	
	static PreparedStatement pStatement=null;
	public void conn(){
		try {
		Class.forName("com.mysql.jdbc.Driver");
		conn=DriverManager.getConnection("jdbc:mysql://localhost:3306/test","root","");
				}catch(Exception e){
			e.printStackTrace();
		}
	}
	
	public void close(){
		try {
			pStatement.close();
			conn.close();
		} catch (SQLException e) {
			e.printStackTrace();
		}
	}
	
	public void insert(String name,int price){ 
		String sql="INSERT INTO goods(name,price) VALUES (?,?)";
			try {
				pStatement=(PreparedStatement) conn.prepareStatement(sql);
				pStatement.setString(1, name);
				pStatement.setInt(2, price);
				pStatement.executeUpdate();//返回1添加成功
			} catch (SQLException e) {
				e.printStackTrace();
			}
		}
	
	public void findall(){
		try {
			ResultSet resultSet=pStatement.executeQuery("SELECT name,price FROM goods");
			while(resultSet.next()){
				String name=resultSet.getString("name");
				int price=resultSet.getInt("price");
				System.out.println(name+":"+price);
			}
		} catch (SQLException e) {
			e.printStackTrace();
		}
	}
	
	public static void main(String[] args) {
		JdbcTransation goods=new JdbcTransation();
		goods.conn();
		goods.insert("book1",100);
		goods.insert("book2",80);
		goods.findall();
		goods.close();
	}
}
```
输出结果:
book1:100
book2:80

(2)JDBC操作数据库工具类封装
整个流程放一起代码重复，利用率低，把相同代码抽取出来封装成一个类。
A.封装Connection对象
B.封装关闭JDBC资源类
C.封装执行数据库操作类



5.小结
------------





第四章 Servlet
=============



****************************
更新中............