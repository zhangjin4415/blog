title: MySql
date: 2016-01-27 18:00:00
categories: "MySql"
tags: ["数据库","MySql"]
---
主要内容：安装与配置MYSQL
<!--more-->
第一章 安装与配置MYSQL
=====================
MYSQL是一个开源的关系型数据库管理系统，分社区版和企业版。
下载地址：http://dev.mysql.com/downloads/mysql/
我选择Windows (x86, 64-bit), ZIP Archive下载----自己根据自己电脑版本下载
1.配置
---------------
将下载文件解压到你的目录，配置环境变量：path：E:\mysql-5.7.10-winx64\bin
每个人根据自己的解压目录而定
配置完环境变量之后先别忙着启动mysql，我们还需要修改一下配置文件
E:\mysql-5.7.10-winx64\my-default.ini
在其中修改或添加配置：
basedir=E:\mysql-5.7.10-winx64（mysql所在目录）
datadir=E:\mysql-5.7.10-winx64\data （mysql所在目录\data）

2.安装服务
-----------------------
以管理员身份运行cmd（一定要用管理员身份运行，不然权限不够），
备注：管理员身份运行cmd
方法一：C:\Windows\System32目录下的cmd.exe右键管理员运行
方法二：点击左下角的“开始菜单”图标按钮，弹出的菜单列表中的“搜索程序和文件”框里输入cmd，输入后不要回车哦,然后在上面显示的列表中找到cmd字样的程序，紧接着在那个程序上单击鼠标右键并在弹出的菜单中选择“以管理员身份运行”，win10在Cortana中搜索。

进入mysql的bin文件夹，输入mysqld -install(如果不用管理员身份运行，将会因为权限不够而出现错误：Install/Remove of the Service Denied）
安装成功后就要启动服务了，继续在cmd中输入:net start mysql（如图）,服务启动成功！

可能错误分析：
（1）.MySQL 服务正在启动 ..MySQL 服务无法启动。
解决：切换到目录E:\mysql-5.7.10-winx64>
执行bin\mysqld --defaults-file=my-default.ini --initialize-insecure
之后再执行net start mysql服务器启动
备注：如果目录没有data文件夹，不用自己创建，主要my-default.ini配置好了后会自己创建的

（2）net start mysql 发生系统错误 5。  拒绝访问。
解决：权限不够，切换到管理员模式就可以启动了。在开始菜单的搜索框张收入cmd，然后右键单击，并选择以管理员身份运行！

3.进入MYSQL
-----------------
dos下：
```
mysql -u root -p
```
Enter password那里，初始密码为空，直接回车就行,显示
mysql>
如此则进入了MYSQL


centos7下安装mysql
===================
sudo wget http://dev.mysql.com/get/mysql-community-release-el7-5.noarch.rpm
如果出现错误 -bash: wget: 未找到命令 则 yum -y install wget
sudo rpm -ivh mysql-community-release-el7-5.noarch.rpm
sudo yum install mysql-community-server
成功安装之后重启mysql服务
service mysqld restart
初次安装mysql是root账户是没有密码的
设置密码的方法	
mysql -uroot
mysql> set password for ‘root’@‘localhost’ = password('mypasswd');
mysql> exit
搞定！


第二章 DOS下简单操作数据库MYSQL
======================
1.服务的启动与停止及版本信息
--------------------
启动
```
net start mysql
```
停止
```
net stop mysql
```
卸载 
```
sc delete mysql
```
备注：所有的windows服务都可以通过net start/stop启动停止

版本信息
```
mysql -V
```

2.登录与退出
------------------
登录：
```
mysql -u root -p
MYSQL提示符：\D--完整的日期  \d--当前数据库 \h--服务器名称 \u--当前用户
```
退出：
```
exit
quit
\q
```

3.常用命令
----------------------------
```
SELECT VERSION();-----------显示当前服务器版本
SELECT NOW();---------------显示当前日期时间
SELECT USER();--------------显示当前用户
shell>mysql -uroot -proot --prompt------修改MySQL提示符：连接客户端时通过参数指定
mysql>prompt 提示符----------修改MySQL提示符：连接客户端后通过prompt修改
eg：prompt \u@\h \d>
```
备注：规范用大写--------虽然小写也可以运行
MYSQL语句的规范：
关键字和函数名称全部大写，数据库名称、表名称、字段名称全部小写，SQL语句必须以分号结尾

4.数据库操作命令
-------------------
创建数据库：
```
CREATE {DATABASE|SCHEMA} [IF NOT EXISTS] db_name [DEFAULT] CHARAACTER SET [=] charset_name
如：
CREATE DATABASE test;
```
查看当前服务器下的数据表列表：
```
SHOW {DATABASES|SCHEMAS} [LINK 'pattern' | WHERE expr]
如：
SHOW DATABASES;
```

5.从文本文件执行SQL语句
--------------
这里在D盘下建一个文件my.txt:
```
CREATE DATABASE mma;
SHOW DATABASES;
```
打开cmd运行结果如下：
```
E:\mysql-5.7.10-winx64\bin>mysql < D:\my.txt -u root -p
Enter password:
Database
information_schema
mma
mysql
performance_schema
sys
test
```
如果正在运行mysql，则如下：
source D:\my.txt也可以用\. D:\my.txt
```
mysql> source D:\my.txt
Query OK, 1 row affected (0.00 sec)

+--------------------+
| Database           |
+--------------------+
| information_schema |
| mma                |
| mysql              |
| performance_schema |
| sys                |
| test               |
+--------------------+
6 rows in set (0.00 sec)
```




第三章 数据库基本操作
===============
1.创建数据库
---------------
```
CREATE DATABASE [IF NOT EXISTS] tb_name; 
CREATE DATABASE tb_name CHARACTER SET big5 COLLATE big5_chinese_ci;//创建并指定字符集为big5,校对规则为big5_chinese_ci
```

2.查看数据库
-------------
```
SHOW DATABASE;
SHOW CREATE DATABASE tb_name;//查看某一数据库详细信息
SHOW CREATE DATABASE tb_name \G;// \G使显示的信息更加直观
```

3.修改数据库
----------------
注意:储存引擎为MyISAM可以修改数据库名称，但是储存引擎为InnoDB无法修改，可以修改字符集和校对规则：
```
ALTER ADTABASE tb_name CHARACTER SET gb2312;//将数据库字符集设置为gb2312
```

4.删除数据库
-----------
```
DROP DATABASE [IF EXISTS] tb_name;
```

5.当前数据库选择
------------
```
SELECT DATABASE();//显示当前数据库
USE tb_name;//运行mysql时选择指定数据库
shell> mysql -u root -p tb_name;//打开时指定
```
备注：修改显示格式
```
mysql> prompt \u@\h \d>
PROMPT set to '\u@\h \d>'
root@localhost mma>
```


第四章 数据表操作
===============
1.数据表类型
------------
只有BDB属于事务安全型，其他属于非事务安全型。
(1)ISAM
现在已经被MyISAM取代
(2)MyISAM
mysql5.4以前使用
(3)Merge
一种把相同结构的MyISAM数据表组织为一个逻辑单元的方法
(4)HEAP
使用内存的数据表，检索速度快，作为一种临时数据表，在指定情况下特别有用
(5)BDB
支持事务处理机制，具有良好的并发性能。
(6)InnoDB
新加入mysql的数据表类型，支持事务处理机制，崩溃后能够立即恢复，具有并发功能，支持外键功能，包括级联删除

2.字段数据类型
-------------
范围自己按位数推： 如TINYINT 1B 8位 有符号时(-2^7~2^7-1) 无符号(UNSIGNED)时(0~2^8-1)
(1)整数型

| 类型             | 大小 | 用途    |
| -----------------| ----| --------|
| TINYINT          | 1B  | 小整数   |
| SMALLINT         | 2B  | 大整数   |
| MEDIUMINT        | 3B  | 大整数   |
| INT或者INTEGER   | 4B  | 大整数   |
| BIGINT           | 8B  | 极大整数 |

(2)浮点型

| 类型         | 大小     | 用途    |
| ------------| ---------| --------|
| FLOAT       | 4B       | 单精度  |
| DOUBLE      | 8B       | 双精度  |
| DECIMAL     |          | 小数    |

备注：FLOAT(7,3)----显示值不超过7位，小数点后面有三位小数


(3)字符型

| 类型         | 大小           | 用途                       |
| ------------| ---------------| ---------------------------|
| CHAR        | 0~255B         | 定长字符串                  |
| VARCHAR     | 0~255B         | 变长字符串                  |
| TINYBLOB    | 0~255B         | 不超过255个字符二进制字符串   |
| TINYTEXT    | 0~255B         | 短文本字符串                |
| BLOB        | 0~65535B       | 二进制长文本数据             |
| TEXT        | 0~65535B       | 长文本数据                  |
| MEDIUMBLOB  | 0~16777215B    | 二进制中等长文本数据         |
| MEDIUMTEXT  | 0~16777215B    | 中等长文本数据              |
| LONGBLOB    | 0~4294967295B  | 二进制极大文本数据           |
| LONGTEXT    | 0~4294967295B  | 极大文本数据                |

备注：
CHAR(长度) 而 VARCHAR根据实际内容长度动态改变储存长度，节约磁盘空间和提高储存效率
TEXT和BLOB用于储存文本块或者图像声音等二进制文件，TEXT不区分大小写，BLOB区分大小写

(4)时间日期

| 类型         | 大小 | 范围                                     | 格式                  | 用途           |
| ------------| -----| -----------------------------------------| ---------------------| ---------------|
| DATE        | 3    | 1000-01-01/9999-12-31                    | YYYY-MM-DD           | 日期值          |
| TIME        | 3    | '-838:59:59'/'838:59:59'                 | HH:MM:SS             | 时间值或持续时间 |
| YEAR        | 1    | 1901/2155                                | YYYY                 | 年份值          |
| DATETIME    | 8    | 1000-01-01 00:00:00/9999-12-31 23:59:59  | YYYY-MM-DD HH:MM:SS  | 混合日期和时间值 |
| TIMESTAMP   | 8    | 1970-01-01 00:00:00/2037年某时            | YYYYMMDD HHMMSS      | 混合日期和时间值,时间戳 |


(5)复合类型
mysql支持的复合类型为ENUM和SET
ENUM只允许在集合中取得一个值，作用类似于单选项，用于处理相互排斥的数据。大小写不匹配时会自动转化为一致的，一个ENUM类型最多包括65536个元素，从1开始索引，其中一个元素被mysql保留，用来储存错误信息，这个错误用索引0或者一个空字符表示。
SET从预定义中取任意多个值，类似复选框，与ENUM相同，插入非预定义值会插入一个空字符，一个SET最多可以包含64项元素。


3.表的操作
---------------
(1)创建
```
USE 数据库名称;CREATE TABLE 表的名称(字段1的名称 字段1的类型 字段1的约束,字段2...);
或者
CREATE TABLE 数据库名称.表的名称(字段1的名称 字段1的类型 字段1的约束,字段2...);
eg:
CREATE TABLE student(sid INT UNSIGNED NOT NULL,name VARCHAR(20) NOT NULL,sex VARCHAR(4) NULL);
```
(2)查看表结构
Field：字段名称
Type：字段类型
Null：是否可以为null
Key：是否编制索引
Default：是否默认值，是多少
Extra：附加信息如AUTO_INCREMENT
```
DESCRIBE 表名;
或者
DESC 表名;
eg:
root@localhost test>DESC student;
+-------+----------------------+------+-----+---------+----------------+
| Field | Type                 | Null | Key | Default | Extra          |
+-------+----------------------+------+-----+---------+----------------+
| id    | smallint(5) unsigned | NO   | PRI | NULL    | auto_increment |
| stuid | varchar(20)          | NO   |     | NULL    |                |
| name  | varchar(20)          | NO   |     | NULL    |                |
+-------+----------------------+------+-----+---------+----------------+
3 rows in set (0.39 sec)
```
查看表的详细结构：
```
root@localhost test>SHOW CREATE TABLE student \G
*************************** 1. row ***************************
       Table: student
Create Table: CREATE TABLE `student` (
  `id` smallint(5) unsigned NOT NULL AUTO_INCREMENT,
  `stuid` varchar(20) NOT NULL,
  `name` varchar(20) NOT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=latin1
1 row in set (0.00 sec)
```

(3)添加与查看数据
```
root@localhost test>INSERT INTO student(stuid,name) VALUES("001","xiangming");
Query OK, 1 row affected (0.16 sec)

root@localhost test>SELECT * FROM student;
+----+-------+-----------+
| id | stuid | name      |
+----+-------+-----------+
|  1 | 001   | xiangming |
+----+-------+-----------+
1 row in set (0.03 sec)
```

(4)删除表
```
DELETE FROM tablename;//删除表中数据
DROP TABLE tablename;//删除整个表
```

(5)修改表名
```
ALTER TABLE 旧表名 RENAME [TO] 新表名;
```


4.字段操作
------------
(1)字段类型修改
```
ALTER TABLE 表名 MODIFY 字段名 数据类型;
```

(2)添加字段
```
ALTER TABLE 表名 ADD 新字段名 数据类型 [约束条件] [FIRST | AFTER 已存在的字段名];//FIRST将字段设置为第一个字段，将字段AFTER添加到已存在的字段名后面
```

(3)删除字段
```
ALTER TABLE 表名 DROP 字段名；
```

(4)字段位置修改
```
ALTER TABLE 表名 MODIFY 字段1 数据类型 FIRST|AFTER 字段2；//将字段1改到第一或者字段2的后面
```


第五章 字段约束
==============
(1)主键约束
----------------
关系库依赖主键，主键用途:唯一地标识一行记录,作为一个可以被外键引用的有效对象。
一般设计表的时候，需要额外添加一个字段id，用来作为主键的标识列，同时添加自增约束，确保唯一性
单字段主键在字段数据类型后面添加PRIMARY KEY即可
```
CREATE TABLE user(
id INT PRIMARY KEY,
name VARCHAR(20)
);
```
复合主键在字段创建后，添加PRIMARY KEY(字段列表用,隔开)
```
CREATE TABLE user(
id INT,
stuid INT,
name VARCHAR(20),
PRIMARY KEY(id,stuid)
);
```

删除全部主键
```
LTER TABLE 表名 DROP PRIMARY KEY;
```

删除添加指定主键
```
ALTER TABLE 表名 DROP/ADD PRIMARY KEY(字段名)；
```

修改字段类型并设为主键
```
ALTER TABLE 表名 MODIFY 字段名 字段类型 PRIMARY KEY;
```

(2)外键约束
-------------------
主键用于标识表中数据，而外键用于表与表之间字段的联系。
外键作用:数据库通过外键保证数据的完整性和一致性，增加数据库表之间的可读性
注意:所有表必须是InnoDB表，不能是临时表,对应非InnoDB表，FOREIGN KEY子句会被忽略。建立外键的字段必须建立约束。

拥有外键的表是子表。主键被其它表引用的表是父表
tablename:子表 tbl_name：父表
添加外键:
```
ALTER TABLE tablename
ADD [CONSTRAINT 外键名] FOREIGN KEY [id] (index_col_name,...)
REFERENCES tbl_name (index_col_name,...)
[ON DELETE {CASCADE | SET NULL | NO ACTION | RESTRICT}]
[ON UPDATE {CASCADE | SET NULL | NO ACTION | RESTRICT}]
```
CASCADE:外键表中外键字段值会跟随父表被更新，或者所在的列会被删除
SET NULL：在父表外键关联字段被修改和删除时，外键表的外键列被设置null
NO ACTION：不进行任何关联操作
RESTRICT：相当于NO ACTION，拒绝父表修改外键关联列，删除记录

实例：课程表course中任课教师字段ctid对应教师信息表teachers的tid字段
```
ALTER TABLE course
ADD CONSTRAINT ctid FOREIGN KEY(ctid)
REFERENCES teachers(tid)
ON DELETE RESTRICT
ON UPDATE CASCADE;
```
创建外键注意：
外键使用建议用ON DELETE RESTRICT ON UPDATE CASCADE;
创建外键时，定义的外键名不能加引号；
字段名与对应数据表名不能错误；
字段类型必须对应，如上面的ctid和tid类型一致;
字段的约束除了主键和外键的约束外其他必须一致;
字符集尽量使用utf-8。

查看外键:通过查看创建表代码查看
```
SHOW CREATE TABLE 表名;
```
删除外键:
```
ALTER TABLE 表名 DROP FOREIGN KEY 外键名;//只是删除了外键约束，没有删除字段本身
```
若系统报错，那出错信息将显示FOREIGN KEY的系统外键名，使用该外键名来删除指定外键。


(3)非空约束
------------------
在字段后面加上NOT NULL即可
如：
```
id INT NOT NULL
```
修改为非空或者空约束:
```
ALTER TABLE 表名 MODIFY 字段名 字段类型 NOT NULL;
ALTER TABLE 表名 MODIFY 字段名 字段类型 NULL;
```
通过查看表结构查看非空字段:
```
DESC 表名;
```

(4)默认值约束
-----------------
被设置默认值的字段最好不为null
默认值修改需要删除再添加
添加默认值
```
ALTER TABLE 表名 ALTER 列名 SET DEFAULT 默认值数据;
```
创建时也可以指定默认值
```
CREATE TABLE user(id INT NULL,year INT NOT NULL DEFAULT 2016)；
```
删除默认值
```
ALTER TABLE 表名 ALTER 字段名 DROP DEFAULT;
```
************************************
设置默认值为当前时间：
数据类型设置成TIMESTAMP,默认值设置为CURRENT_TIMESTAMP即可。格式xxxx-xx-xx xx:xx:xx

(5)唯一性约束
-----------------
注意：定义为唯一性约束的列，没有定义非空约束时，最好不要填入空值，两个空值将导致列的数据违背唯一性。
创建时添加唯一性约束(UNIQUE)：
```
CREATE TABLE user(
id INT NOT NULL UNIQUE,//方法1
name VARCHAR(20) NOT NULL,
sex VACHER(20),
UNIQUE(name)//方法2
);
```

查看用SHOW CREATE TABLE 表名;

添加唯一性约束:
```
ALTER TABLE 表名 ADD UNIQUE(字段列表);//字段列表中字段间用,隔开
```
删除唯一性约束：
```
ALTER TABLE 表名 DROP INDEX 列名;
```

(6)自增约束
-------------------
使用AUTO_INCREMENT实现
注意：
AUTO_INCREMENT是数据列的一种属性，只是适用于整数型数据列；
设置AUTO_INCREMENT属性的数据列应该是一个正数序列，应该声明为UNSIGNED；
AUTO_INCREMENT数据列必须唯一约束，以避免序号重复；
MySql表中只能有一个AUTO_INCREMENT字段；
自增字段必须定义为键如主键或者外键；
AUTO_INCREMENT数据列必须有NOT NULL属性；
AUTO_INCREMENT序号最大值受该列数据类型限制，TINYINT最大为127，加上UNSIGNED为255，达到上限AUTO_INCREMENT会失效；
全表数据删除时（删除所有数据，保留表结构），AUTO_INCREMENT会从1重新开始编号；
要重新排列现有的序列编号，最简单的方法是先删除该列，再创建该列，mysql会重新生成连续的编号序列；
自增每次只能加1。
每种数据表机制不一样，这里用的是InnDB表

创建自增约束：
```
CREATE TABLE worker(
id INT PRIMARY KEY AUTO_INCREMENT
);
```
添加自增约束:
```
ALTER TABLE worker MODIFY COLUMN id INT NOT NULL AUTO_INCREMENT;
```
删除自增约束：
```
ALTER TABLE worker MODIFY COLUMN id INT NOT NULL;
```

(7)删除指定名称的约束
--------------------
```
ALTER TABLE 表名 DROP INDEX 约束名；
```
如：
```
root@localhost test>SHOW CREATE TABLE worker;
+-------------------+
| Table  | Create Table                                                                                                                                                                                                    |
+-------------------+
| worker | CREATE TABLE `worker` (
  `id` int(11) NOT NULL,
  `name` varchar(20) NOT NULL,
  `sex` varchar(20) DEFAULT NULL,
  UNIQUE KEY `id` (`id`),
  UNIQUE KEY `name` (`name`)
) ENGINE=InnoDB DEFAULT CHARSET=latin1 |
+-------------------+
1 row in set (0.00 sec)

//如上，name 字段上有UNIQUE KEY约束，名称为name
删除后：
root@localhost test>ALTER TABLE worker DROP INDEX name;////////
Query OK, 0 rows affected (0.15 sec)
Records: 0  Duplicates: 0  Warnings: 0

root@localhost test>show create table worker;
+------+
| Table  | Create Table                                                                                                                                                                      |
+------+
| worker | CREATE TABLE `worker` (
  `id` int(11) NOT NULL,
  `name` varchar(20) NOT NULL,
  `sex` varchar(20) DEFAULT NULL,
  UNIQUE KEY `id` (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=latin1 |
+------+
1 row in set (0.00 sec)
```

第六章 数据记录基本操作
====================
1.SELECT基本语法
------------
使用顺序必须如下：
```
SELECT [STRAIGHT_JOIN] [SQL_SMALL_RESULT] [SQL_BIG_RESULT]
[HIGH_PRIORITY]
	[DISTINCT | DISTINCTROW | ALL]
 select_expression,...
 [INTO {OUTFILE | DUMPFILE} 'file_name' export_options]
 [FROM table_references 
	[WHERE where_definition]
	[GROUP BY col_name,...]
	[HAVING where_definition]
	[ORDER BY {unsigned_integer | col_name | formula} [ASC | DESC] ,...]
	[LIMIT [offset,] rows]
	[PROCEDURE procedure_name]]
```
select_expression:需要查询的字段名；
table_references:从此处指定的表或者视图中查询数据；
WHERE where_definition:指定查询的条件；
col_name:按照指定的字段进行分组；
HAVING where_definition:满足这个条件的表达式才能输出；
ORDER BY：按照指定的字段进行排序，ASC-升序 DESC-降序；
PROCDURE procedure_name:指定的储存过程名称。

2.单表查询
-----------




十一、数据库界面化
=========================
上面安装的mysql没有界面，可以在dos下操作，如果你想要界面化的话可以自己找相关界面化软件，这里用Navicat for MySQL！
自己安装好软件Navicat for MySQL！
打开软件，点击连接，随便输入一个连接名，密码这里不用输入（因为初始数据库没有密码，如果你的MYSQL数据库加了密码的话输入即可）
点击确定即可看见数据库了，里面有MYSQL自带的数据表

十二、Mysql问题
=================
1.ERROR 1215 (HY000): Cannot add foreign key constraint
--------------------------------------
```
root@localhost test>ALTER TABLE stu ADD FOREIGN KEY(stuid) REFERENCES stuinfo(stu_id);
ERROR 1215 (HY000): Cannot add foreign key constraint
root@localhost test>show create table stu;
+-------------------------+
| Table | Create Table                                                                                                                                                                                         |
+-------------------------+
| stu   | CREATE TABLE `stu` (
  `id` smallint(5) unsigned NOT NULL AUTO_INCREMENT,
  `stuid` varchar(20) NOT NULL,
  `name` varchar(20) NOT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=latin1 |
+-------------------------+
1 row in set (0.05 sec)

root@localhost test>show create table stuinfo;
+-------------------------+
| Table   | Create Table                                                                                                                   |
+-------------------------+
| stuinfo | CREATE TABLE `stuinfo` (
  `stu_id` varchar(20) NOT NULL,
  `city` varchar(20) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=latin1 |
+--------------------------+
1 row in set (0.00 sec)

root@localhost test>ALTER TABLE stu ADD PRIMARY KEY(stuid);
ERROR 1068 (42000): Multiple primary key defined
root@localhost test>ALTER TABLE stuinfo ADD PRIMARY KEY(stu_id);
Query OK, 0 rows affected (0.53 sec)
Records: 0  Duplicates: 0  Warnings: 0

root@localhost test>ALTER TABLE stu ADD FOREIGN KEY(stuid) REFERENCES stuinfo(stu_id);
Query OK, 0 rows affected (0.77 sec)
Records: 0  Duplicates: 0  Warnings: 0
```

2.Duplicate entry '005' for key 'PRIMARY'
---------------------------------------
数据库中主键不能添加重复值.


目录：MYSQL相关查询
====================
1.参数
-------------


2.数据类型
-------------




****************************
更新中............