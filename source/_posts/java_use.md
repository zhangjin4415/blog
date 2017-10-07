title: JAVA学习篇
date: 2016-02-02 12:22:14
categories: "JAVA"
tags: "JAVA"
---
主要内容:JAVA语言学习教程
<!--more-->
第一章：介绍
======================
1.本教程介绍
---------------
本教程使用的是MyEclipse+JDK1.8。
学习java已经半年了，很多东西虽然熟悉，却是朦朦胧胧，没有一个系统的总结，这里主要做一个系统的总结。本教程志在通过自己的学习与仿真写一篇系统的java学习笔记，以便后面复习或者查询用，本教程主要参考明日科技的JAVA 编程宝典一书。

2.常用开发环境介绍
----------------------
下面文章来自：http://blog.csdn.net/futureinhands/article/details/1329148
1995年3月23日，San Jose Mercury News登出一篇题为“Why Sun thinks Hot Java will give you a lift”的文章，在那篇文章里预言Java技术将是下一个重大事件，这个预言现在看来并不仅仅是商家的宣传伎俩，虽然文章是当时Sun的公关经理 Lisa Poulson安排撰写的。从世人知道Java那一刻起到现在，算起来已经过去整整十年，回顾过去的十年值得总结的东西有许多，但在这里笔者只想就Java开发环境谈些个人的想法与朋友们交流一下。

　　现在的软件开发人员在整个软件的开发生命周期里，也许会根据需要使用各式各样的开发工具来完成相对复杂的开发任务，而在几十年以前，人们还只是使用文本编辑器、编译器和Debugger进行开发，对于这个阶段的开发环境人们称之为CLEs(Command Line Environments)。 而当人们发现如果将那些单独分开的开发工具集成起来就可以有效的提高开发效率时，IDEs(Integrated Development Environments)就出现了。Java的出现尽管只有十年，但其开发环境也大至经历了从CLEs到IDEs再到XDEs这三个阶段，现在即将进入CDEs阶段。在上述Java开发环境发展过程中，有许多值得我们大家关注的地方。

　　Java开发环境的历史回顾

　　纵观过去十年Java开发环境的发展，大致可以粗略的划分为如下几个阶段:

　　●  1995，命令行开发环境CLEs

　　●  1996-2000，集成开发环境IDEs 

　　●  2001-2004，扩展开发环境XDEs 

　　●  2005至今，协同开发环境CDEs 

　　1995年，不平凡的一年，这一年Java 获得了成功。可令人尴尬的是在1995年并没有一个令人满意的Java开发环境，开发人员在进行Java编程时，大多使用文本编辑器编辑源程序，然后再使用命令行的方式进行编译处理。那时的Java开发环境还处于CLEs时代，开发效率非常低，这预示着在Java开发工具上会有一番激烈的竞争。

　　有人称1996年为互联网年，有人却称之为Java年，还有人称之为Web开发年，但不论如何称呼1996年，它都反映了一个事实：Bill Joy将Java与互联网相结合的策略取得了成功。这一年的9月Sun推出了其Java开发环境-Java WorkShop，这是一款基于浏览器的Java开发工具，但由于当时 Java在许多方面还不成熟，所以实际上Java WorkShop并不成功，同年发布的Symantec Visual Cafe由于还是采用C/C++语言进行开发，所以性能与成熟度上就比WorkShop好得多。提到Visual Cafe就不能不提Eugene Wang，因为Eugene Wang常常是与计算机间谍这个词同时出现的人物，有人甚至讲当时Symantec的老板Gordon Eubanks与Eugene Wang签约时，也同时签下了监狱里的一个单元。Visual Cafe就是由Eugene Wang进行主要策划的，它是在同一年发布的Java开发环境中，唯一解决了与数据库连接问题的开发环境，带有一套可以与数据库相连接的组件，无需太多编程使用拖拽的方式就可完成大部分工作，这一优点使得Visual Cafe受到了Java开发人员的欢迎。这一年IBM收购了OTI公司，从而得到了Dave Thomas的弟子John Duimovich、Dave Thomson、Mike Wilson等一大批软件精英，这之中还包括“生活在技术刀锋上的开发者”Brian Barry。

　　1997年，由于微软垄断案，使得微软在Java开发环境上的努力受到了限制，Visual Cafe由于界面直观易用，可以很容易地连接各种数据源等功能再次受到开发人员的欢迎。这一年IBM发布VisualAge for Java。VisualAge for Java是面向代码库的开发环境，它提供代码库和项目管理以便于开发团队在 C/S环境下进行项目开发。但由于大多数Java开发人员比较熟悉面向文件的开发环境，还不太习惯面向代码库的开发，再加上VisalAge for Java对系统资源的要求比较高等因素，使得VisualAge for Java一开始未被Java开发人员所认可。

　　1998年至2000年比较成功的Java开发环境是JBuilder，这是由于Borland较好的把握住 J2SE、J2EE和J2ME发布后，Java技术升级的时机，全面支持Java1.1和Java1.2开发平台，它还提供了多种工具方便用户从旧的平台迁移到新的Java平台。JBuilder本身80%是基于JDK1.2进行开发的，它支持JavaBeans, Enterprise JavaBeans, JDBC等方面的应用开发，可以连接多种关系数据库。为支持分布式应用开发，JBuilder还集成了 VisiBroker ORB、JSP server、数据库和EJB AppServer，并提供Open Tools API便于第三方工具集成。上述种种的优点使得JBuilder一举超越Visual Cafe，成为当时最受欢迎的Java开发环境。在众多Java开发环境中，1999年IBM发布的VisualAge for Java Micro Edition是比较有特色的开发环境，它是由Erich Gamma和与Erich Gamma有“焦不离孟、孟不离焦”之称的John Wiegand共同进行设计的，采用了Java 扩展机制，并集成了JUnit测试框架，其当时所采用的架构深深地影响了后来Eclipse1.0所采用的架构。同时，通过VisualAge for Java Micro Edition的开发，那些来自“未来世界”(Smalltalk们总认为他们来自计算机的未来世界)的软件精英们，全面彻底地对Java技术进行了评估，得出了许多结论性的东西，这之中包括现在闹得沸沸扬扬的Swing和SWT对比。此外，Sun将其收购的NetBeans变成了开源的Java IDE也是一件不大不小的事情。

　　纵观1996年至2000年这五年时间里，随着Java及其相关开发应用的发展，Java开发环境也不断的完善，从CLEs进入到IDEs阶段。为了提高Java开发人员的开发效率，Java开发环境主要从两个方面进行改进与提高。一方面是提高集成在Java IDEs当中开发工具的性能和易用性，另一方面是将Java开发环境尽可能的覆盖到整个软件的开发生命周期。随着基于WEB，采用N-层结构的应用开发成为Java开发人员主要从事的开发任务，Java开发环境需要支持越来越多的技术，比如:XML、JSP、EJB和CORBA等，这就造成了Java IDEs的规模变得越来越大，许多Java开发环境都集成了数据库、JSP Server和AppServer，软件的研究人员将上述IDEs不断膨胀的现象称为“IDEs大爆炸”。

　　“IDEs大爆炸”现象发生以后，有关Java开发环境是走少而精的发展方向，还是走大而全的发展方向就成了广大Java开发人员关注的问题。2001年Java开发人员达到了200万，成为每个软件供应商都无法忽视的力量，这一年JetBrains推出了Java开发环境少而精的代表： IntelliJ IDEA。 IntelliJ IDEA明确的表示只做最好的Java代码编辑器，不做什么文件都可以编写的编辑器。它关注Java开发人员的工作实际并将这些工作进行了优化。由于减掉了一些可有可无的工具，所以价格上相对合理公道。当年IntelliJ IDEA击败JBuilder成为最受Java开发人员欢迎的Java开发环境，不过2002年随着JBuilder将大而全的功力再提升一步，将UML建模工具、JUnit测试框架以及Apache Struts等开发工具集成进来，大而全的发展方向又一次受到Java开发人员追捧。最全还是最好似乎使Java开发人员在选择Java开发环境时处于两难状况，但实际上当Eclipse 1.0发布时，这个问题已经得到了初步的解决，最好和最全是可以兼顾的。

　　Eclipse的出现不是从天上掉下来的，也不是某个天才拍脑袋想出来的，它是一群软件精英们集体智慧的结果。早在1998年IBM就打算开发新一代的工具平台以便将它现有的各种开发工具统一起来，并减少开发各种工具时重复的劳动，同时希望在新的平台上建立新的Java开发环境。经过一段时间的准备， IBM开始建立起一个开发团队，人员构成主要来自VisualAge for Java Micro Edition和VisualAge for Java两个项目的开发人员，选择的标准是过去10年至少开发过5到6个IDE。此外，IBM还联合了9家公司共同成立了一个开源组织Eclipse基金会，将Eclipse提供给开发人员使用，并在开源社区的帮助下进一步完善Eclipse本身。Eclipse在最初设计时，插件模型是静态的，不能实现插件的即插即用功能，即便是大受欢迎的Eclipse 2.1也还是静态的。所以到2004年发布Eclipse 3.0时，Eclipse进行了重大改进，采用OSGi的插件模型，初步实现了插件的即插即用功能，至此一个完美的、可扩展的开发环境展现在Java开发者面前，这时Java开发人员已经达到300万。

　　Java开发环境的现状

　　2004年Eclipse 3.0的发布极大刺激了Eclipse用户的增长，经过一年以后，Java开发人员现在使用Java开发环境的状况是如何的呢？看了下面的表格里的数据也许可以了解一个大致的状况。

　　首先需要指明的是上述的数据并不是当前Java用户使用Java开发环境的准确反映，但我们可以从中了解一个大致的状况。现在的Java环境可以分为三个集团，第一集团是Eclispe它大约占据1/3的份额，第二集团是 IntelliJ IDEA、NetBeans 和JBuilder占据另外1/3的份额，相互之间旗鼓相当，第三集团是以JDeveloper和WSAD为代表的十几种Java开发环境占据剩下的 1/3份额，但每种开发环境占总份额的比重不超过5%。我们考察Eclipse、intelliJ IDEA、NetBeans 和JBuilder这些主流开发环境，可以发觉它们有一个共同的特点那就是可扩展，尽管在实现手段上各有不同。这就是为什么称现在的Java开发环境为XDEs(eXtended Development Environments)的原因，IDEs已经死亡了4年，专业的开发人员需要了解这个事实，因为XDEs也快死了。

　　由于市场的压力，一个软件企业不仅要提高开发人员个体的工作效率，还要提高整个开发团队以及整个企业的开发效率，但在现有的Java开发环境XDEs下无法完全做到这些，所以新一代开发环境CDEs (Collaborative Development Environments)就产生。Grady Booch和Alan W. Brown的研究表明一个程序员一天工作时间的分配是这样的：分析占16%(从5%到40%不等)， 设计占14%(从1%到40%不等)，编程占16%(从0%到60%不等)，测试占10%，打电话占3%，阅读占7%(电子邮件，文档，月刊和杂志)，参加开发会议占10%，无关的会议占7% 。从这些数据可以发现，开发人员用于交流的时间约占工作时间的1/3，开发人员的相互交流非常重要。可是现有的主流Java开发环境一般仅将分析、设计、编程和测试等工具集成进来，却未包括用于交流的工具，这显然不合理。因此，所谓CDEs就是将用于人与人、人与团队以及团对于团队进行交流的工具集成进来的开发环境，比如，CDEs常具有发送电子邮件、进行及时通讯和屏幕分享等功能，通过实现无损耗过程的交流提高开发团队的开发效率。

　　现在已经商业化的CDEs是CodeBeamer Collaborative Development Platform和CodePro AnalytiX，上述两款软件都提供Eclipse的插件，可以与Eclipse集成在一起，使Eclipse升级成为一个CDEs。大家肯定知道Borland已经宣布开发基于Eclipse的新版JBuilder-“Peloton”，Peloton就是一个CDEs(Collaborative Development Environments)，当它明年上半年发布时，就意味着Java开发环境进入CDEs时代，现在Java开发环境还处于XDEs与CDEs交替的阶段。

　　Java开发环境的未来

　　在可以看得见的将来，Java的开发环境还会是以CDEs的形式存在。开源组织或开发工具供应商将会努力为软件的开发创建一个绝对光滑的平面 (Frictionless Surface)，实现无损耗的开发过程，以提高开发效率。为了实现无损耗的开发过程，Java的开发环境将会关注以下几个方面:

　　●  起步阶段方面 

　　●  协作开发方面 

　　●  维护开发团队有效沟通方面 

　　●  多个任务的时间协调方面 

　　●  相互协商方面 

　　●  资料有效性方面 

　　但这里必须承认未来Java开发环境是如何具体去实现无损耗的开发，还需要时间给与答案，因为现在所能采用的方法未必是最好的，比如，使用面向文件的 CVS进行协同开发就有需要改进的地方。

　　总结

　　罗里罗唆一大堆，归纳起来不过就是:一个目的、三种手段以及一条规律。

　　一个目的:十年Java开发环境的演变，其目的就是为了提高开发效率。

　　三种手段:

　　●  提高集成在Java开发环境中开发工具的性能和易用性 

　　●  将Java开发环境尽可能的覆盖到整个软件的开发生命周期 

　　●  集成人与人、人与团队以及团对于团队进行交流的工具 

　　一条规律:软件开发环境的发展过程是从CLEs到IDEs再到XDEs最后进入CDEs，这是由Grady Booch总结出来的，套在Java开发环境上也适用。 
3.java应用领域
----------------------
桌面应用系统开发
嵌入式系统开发
电子商务应用
企业级应用开发
交互式系统开发
多媒体系统开发
分布式系统开发
Web应用系统开发

4.基本知识构架
-----------------------
下图在网上看到的，具体地址遗忘：
![图片](img/javause/00.jpg)
                         
| NO |  类别	      |                                                                                                               |
| ---| -----------| --------------------------------------------------------------------------------------------------------------|
| 01 |	操作系统	  | Windows --> Linux                                                                                             |
| 02 |	中间件	  | Tomcat --> JBoss                                                                                              |
| 03 |	数据库	  | MySQL --> Oracle                                                                                              |
| 04 |	JAVA SE	  | 环境搭建 --> 基础程序 --> 面向对象 --> 应用开发 --> 高级应用 --> Java新特性 --> JDBC                                |
| 05 |	JAVA EE   | WEB	HTML --> JavaScript --> JSP --> JavaBean --> DAO --> Smartupload --> Servlet --> MVC                      |
| 06 |	开源框架   | Struts 1.x --> AJAX --> ECSide报表组件 --> Hibernate --> Spring --> Struts 2.0 --> AJAX框架（DWR、JSON、JQuery）  |
| 07 |	XML	  　  | 基础语法 --> 解析（DOM/SAX/JDOM）                                                                               |
| 08 |	分布式开发 |	RMI --> EJB 3.0 --> XFire --> Web Services                                                                    |
| 09 |	搜索引擎	  | Lucene、HTMLParser、Heritrix                                                                                    |
| 10 |	工作流	  | JBPM                                                                                                          |
| 11 |	开发工具	  | Eclipse、Jboss IDE                                                                                             |

具体可以参考如下：
http://blog.163.com/love_gzhj/blog/static/107086704201173135414127/?newFollowBlog



第二章：基本知识
======================
1.数据类型
---------------------
基本类型：
整数型：byte（1字节），short（2字节），int（4字节），long（8字节）
浮点型：float（4字节），double（8字节）
字符型：char-------------------------------------------
Unicode码：'a'=97，char强制转换为int就可以得到
布尔类型：boolean（true，false）

自动类型转换：低精度向高精度，整数型与浮点型
byte->short->int->long->float->double

强制数据类型转换：容易造成数据丢失。boolean不能与其他类型强制转换


2.运算符
---------------
赋值运算符：=
算术运算符：+,-,*,/,%
自增自减运算符：++，--      注意：a++;与++a;后者先加后运算，前者相反
比较运算符：>,<,==,>=,<=,!=
逻辑运算符:!,&&,&,||,|		注意：&&存在短路：前面有false不会计算后面，而&不存在短路，||与|区别一样
位运算符：按位运算符 ~,&,|,^(异或)；移位运算符：<<,>>,>>>(无符号右移位)
三元运算符：布尔表达式？表达式1：表达式2

3.常量变量，标识符关键字，注释
-----------------

4.流程控制语句
-----------------------
if...else
if...else if...else
switch(){case: break;default:break;}
for
while
do...while
注意：区别continue与break，使用标签与标志位
break退出整个循环，continue退出本次循环，进入下一次；
标签应用实例如下：
打印出来的是5*5乘法表
```
loop:
for(int i;i<=9;i++){
   for(int j=1;j<=i;j++){
		System.out.print(i+"*"+j+"="+i*j+"");
		if(j==5){
			break loop;
		}
	}
	System.out.println();
}
```
5.数组
---------------------
数组是相同类型的、用一个标识符封装到一起的对象序列或者基本类型数据序列，是效率最高的储存和随机访问对象引用序列的方式，他是一个简单的线性序列，所以访问速度快，缺点就是数组一旦创建大小就不可以改变。
可以是一维、二维、多维数组。

5.1 一维数组
声明
```
数组类型 数组名[]；
或者
数组类型[] 数组名；
```
分配空间
```
数组名字=new 数组类型[数组长度]；
```
初始化
```
int arr1[]=new int[]{1,2,3,4};//第一种
int arr2[]={1,2,3,4};//第二种
//第三种
int arr3[]=new int[4];\
arr3[0]=1;arr3[1]=2;arr3[2]=3;arr3[3]=4;
```
遍历
```
String day[]=new String[]{"星期一","星期二","星期三","星期四","星期五","星期六","星期七"};
for(int i=0;i<day.length;i++){
	System.out.println(day[i]);
}
```

5.2 二维数组
声明
```
数组类型 数组名[][];
或者
数组类型[][] 数组名;
```
分配空间
```
数组名字=new 数组类型[行][列]；
```
初始化
```
数据类型 变量名称[][]={
	{value1,value2...}
	{valu1,valu2,...}
}
或者
arr[i][j]=value;
```
遍历
```
String arr[][]={{"i","you"},{"he"},{"a","b","c"}};
for(int i=0;i<arr.length;i++){
	for(int j=0;j<arr[i].length;j++){
		System.out.print(arr[i][j]+" ");
		}
	System.out.println();
}
输出:
i you 
he 
a b c 
```

5.3 foreach遍历数组
```
for(元素变量:遍历对象){
	循环体
}
```
实例：
```
String arr[][]={{"i","you"},{"he"},{"a","b","c"}};
for(String[] is:arr){
	for(String is2:is){
		System.out.print(is2+" ");
	}
System.out.println();
}
输出:
i you 
he 
a b c
```

5.4 排序
冒泡排序：
```
public void mysort(){
		int arr[]={6,4,43,1,2,3,4,5};
		for(int i=0;i<arr.length;i++){
			for (int j = i+1; j < arr.length; j++) {
				if(arr[i]>arr[j]){//大的忘后面移动
					int c=arr[i];
					arr[i]=arr[j];
					arr[j]=c;
				}
			}
			System.out.print(arr[i]+" ");
		}
	}
输出结果：
1 2 3 4 4 5 6 43
```
直接用Arrays提供的sort方法：
```
int arr[]={6,4,43,1,2,3,4,5};
Arrays.sort(arr);
for (int i = 0; i < arr.length; i++) {
	System.out.print(arr[i]+" ");
}
输出结果：
1 2 3 4 4 5 6 43
```
Arrays提供的复制数组方法：
```
copyOf(arr,int newlength)//arr--要进行复制的数组，newlength-复制后的新数组长度 如果新数组长度大于arr数组，int用0填充，char用null填充
copyOfRange(arr,int formIndex,int toIndex)//arr-要进行复制的数组，formIndex-开始复制数组的索引位置，必须是0到数组长度之间，toIndex-复制范围的最后索引位置，可以大于arr长度，新数组包括索引为formIndex的位置，不包括索引为toIndex的位置
```

6.字符串
-------------
用java.lang包中的String类来创建字符串对象，String类有很多字符串处理方法

6.1 产生String对象
构造方法
```
String()   //构造的对象是一个空字符串（""）,与空值null是两个概念；用new String();
			//注意："a"+null+"b"结果为"anullb"

String(byte[] bytes)
		[   byte[] byteArr = new byte[]{65,66,67};
    		String str=new String(byteArr);
			System.out.print(str);
		]//输出：ABC

String(byte[] bytes,String charsetName)//指定charsetName编码格式和byte字节数组构造一个新的字符串

String(char[] value)//新字符串是字符数组中所有元素连接的结果
 
String(StringBuffer buffer)//StringBuffer(缓冲字符串)对象缓冲区中的所有内容

String(StringBuilder builder)//StringBuilder(字符串生成器)对象中的内容
```

6.2 字符串操作
获取长度：length（）
截取：substring(int beginIndex)//索引位置开始到字符串结尾
	 substring(int beginIndex,int endIndex)//索引开始位置到结束位置（不包括结束位置上的字符串）
分割：split(String sign)//根据sign(分割符进行分割)//也可以使用正则表达式
	 split(String sign,int limit)//根据分隔符进行分割，并限定拆分次数
如：
```
String str1="姓名：小明！年龄：20,性别：男";
String[] info=null;
info=str1.split("！|!|,");//中英文!或者,分   
for (int i = 0; i < info.length; i++) {
	System.out.println(info[i]);
}
输出：
姓名：小明
年龄：20
性别：男
```
去除前导空白和尾部空白：trim()
查找字符串：
indexOf(String str)//返回str在字符串中首次出现的位置，没有则返回-1
lastIndexOf(String str)//最后一次出现的位置
indexOf(int ch)//返回字符ch(如：105代表i 97代表a)在字符串中首次出现的位置，没有则返回-1
lastIndexOf(int ch)//最后一次出现的位置
indexOf(int ch,int startIndex)//指定搜索点，指定字符ch首次出现的位置
lastIndexOf(int ch,int startIndex)//指定搜索点，指定字符ch最后一次出现的位置
如：
```
String s="abcdefghijklmn";
int lastIndex=s.lastIndexOf(105,8);//i所在的位置为8，如果将8改为小于8的数之后返回-1
System.out.println("i所在的位置为"+lastIndex);
System.out.println(s.indexOf("i"));
```
判断是否相等：
==比较的是地址是否相同
equals（String）比较的是内容是否相同，区分大小写
equalsIgnoreCase（String）不区分大小写
toUpperCase()--转化为大写
toLowerCase()--转化为小写

6.3 可变字符串（StringBuffer类）
StringBuffer类创建的字符串可以进行增加、插入处理，可以转化为String对象
StringBuffer类的方法：
append()-----向字符串生成器中追加内容，此方法有多个重载形式的实现，可以接受任何类型数据
如：
```
StringBuffer bf=new StringBuffer("java");
bf.append("编程语言");
System.out.println(bf);//java编程语言
System.out.println(bf.toString());//java编程语言
```
delete(start,end)//从StringBuffer对象中移除指定字符串，start-起点位置 end-终点位置
如：
```
bf.delete(0, 4);
System.out.println(bf);//编程语言
```
insert(offset,arg)//向StringBuffer对象中指定位置插入指定内容，offset-开始位置，arg-插入内容（可以是任意内容）
如：
```
bf.insert(0,"java");
System.out.println(bf);//java编程语言
```
toString()---将StringBuffer类对象转化为String对象

6.4 字符串反转
```
private static String splitReverse(String text){//使用split方法
  String[] split= text.split("");//实现截取字符串
  String newstr="";
  int len=split.length;//数组长度length区别于字符串长度length()
  for (int i = len-1; i >= 0; i--) {
	newstr += split[i];
	}
	return newstr;
}


private static String chatAtReverse(String text){//使用chatAt方法
		String newstr = "";
		int len = text.length();
		for (int i = len-1; i >= 0; i--) {
			newstr += text.charAt(i);
		}
		return newstr;
	}
```

第三章 类（对象）、继承与多态、接口与抽象类
================
1.类与对象
------------
面向对象（OOP）：将数据和处理数据的方法紧密的结合一起，形成类，再将类实例化，就形成对象
在面向对象的世界，不再需要考虑数据结构和功能函数，只要关注对象就行
类是对某一事物的描述，是抽象的、概念的定义，对象是实际存在的该类事物的个体

通过创建类对象的方式来访问类的属性和行为

包：确保类名的唯一性
包定义：package 包名；
引入包名：import 包名；或者import 包名.类名；

静态方法与成员方法区别：
成员方法必须通过对象才能访问，而静态方法还可以直接通过类名调用

静态块：应用static关键字包围，不包含在任何方法中的静态代码块，当类被加载时，静态块就会被执行且只被执行一次
如：
```
public class Mytest {
	static{
		System.out.println("静态块被执行");
	}
	public static void main(String[] args) {
		new Mytest();
		new Mytest();
	}
}
上面不写new Mytest();或者写多个new Mytest();都只是执行一次
输出：静态块被执行
```

权限修饰符：
public--任意可访问
protected--只有本包内的该类的子类或者其他类可以访问
private--只能在本类中被使用，在子类中不可见，对其他包的类不可见

方法重载：一个类中，出现多个方法名相同，但是参数个数和参数类型不同的方法

构造方法：一定要与类名称相同，一定不含有返回值，定义中不可以用void标识，方法中不能用return语句

2.继承与多态
-----------
继承：子类需要拓展父类的功能，加强或者改进原本类所没有定义的属性及方法
多态：一个类有其他的表现形式，但是彼此间必须是继承关系

定义子类：
```
[修饰符] class 子类名 extends 父类名
```
//修饰符--指定类的访问权限，有public,abstract,final

继承原则：
（1）子类能够继承父类中被声明为public和protected的成员变量和成员方法，但不能继承被声明为private的成员变量和方法
（2）子类能够继承在同一个包的由默认修饰符修饰的成员变量和方法
（3）子类声明了一个与父类同名的成员变量或者方法，则子类不能继承父类的成员变量或者方法，此时称子类的成员变量隐藏了父类的成员变量或者方法
	
方法覆盖（方法重写）：被覆盖的方法必须与覆盖方法有相同的方法名称、参数以及返回值类型
方法覆盖限制：
（1）子类不能覆盖父类中声明为final或者static的方法
（2）子类必须覆盖父类声明为abstract的方法，或者子类也将该方法声明为abstract
（3）子类覆盖父类声明的同名方法时，子类中的方法声明必须与被覆盖方法的声明相同
 注意：子类不能使用比父类中被覆盖的方法更加严格的访问权限，子类的访问权限必须要比父类的大

super关键字：子类中访问被父类隐藏的成员变量或者方法，子类中使用父类的构造方法（子类并不继承父类的构造方法）
实例：
```
public class Animal {
	protected int x=1;
	public void s(){}
}

public class Bird extends Animal{
	public Bird(){
    super();//写在构造方法内正确，写在其他地方错误
	}
	int a=super.x;//父类中x为private则这里错误，可以是protected
	public void supers(){
	super.s();
	}

//	super.s();//放在外面错误
}
```
多态是指程序中的同一操作在不同环境中有不同的语义解释

方法重载：一个类中，出现多个相同名称的方法，但是参数类型和参数个数不同
注意：方法返回值类型不能作为区分方法重载的标志

上转型：子类可以强转为父类
实例：
```
public class Animal {
	public void move(){
		System.out.println("动物的爬行行为");
	}
}

public class Bird extends Animal{
	public void move(){
		System.out.println("鸟儿在天上飞");
	}
}

public class Zoo {
	public void free(Animal animal){//定义方式方法
		animal.move();
	}
	public static void main(String[] args) {
		Zoo zoo = new Zoo();
		Bird bird = new Bird();
		zoo.free(bird);//鸟儿在天上飞
	}
}
```
计算圆形和矩形面积：用方法重载就行，用不同的参数就行，圆形传入一个半径r，而矩形传入长宽

重写equals()方法：
两个对象是存放在不同内存空间的两个数据结构，“==”对比的是两个对象的地址，而不能对比内容
判断内容是否相等必须用equals()方法，这个方法在Object类中定义，它是所有类的父类，任何类都隐式地继承了该方法，只是没有具体的实现代码，一个完整的数据储存类都应该重写该方法，实现自己的相等性判断
实例：
```
public class Bird{
	private String name;
	private int id;
	public boolean equals(Object obj){
		if(this==obj)//当前对象
			return true;
		if(obj==null)
			return false;
		if(getClass() != obj.getClass())
			return false;
		Bird other = (Bird)obj;
		if(id != other.id)
			return false;
		if(null==name){
			if(null!=other.name)
				return false;
		}else if(!name.equals(other.name))//注意：字符串比较不能用==
			return false;
		return true;
	}
	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}
	public int getId() {
		return id;
	}
	public void setId(int id) {
		this.id = id;
	}
	
}

public class Zoo {
	public static void main(String[] args) {
		Bird a=new Bird();
		Bird b=new Bird();
		a.setName("a");
		a.setId(1);
		b.setName("b");
		b.setId(1);
		System.out.println(a.equals(b));//false
		b.setName("a");
		System.out.println(a.equals(b));//true
	}
}
```

注意：java C#使用单继承，而C++使用多继承

3.接口与抽象类
---------------
抽象方法：只定义方法名而没有定义方法体的方法
一个类中定义了抽象方法，则这个类一定是抽象类，但是抽象类不一定含有抽象方法
接口：接口中所有方法都是抽象的，是一个完全抽象的类，接口就是一种标准和规范，只定义了方法名而没有方法体，接口只定义了类应该做什么，而不关心如何去做。

接口定义：接口必须被定义为public,否则没有意义，接口文件的文件名必须与接口名相同
```
[修饰符] interface 接口名 [extends 父接口列表]{
	[public] [static] [final] 常量；
	[public] [abstract] 方法；
}
```

实现接口：
继承（extends）只能使用单继承，而一次可以实现多个接口（implements）,每个接口用“,”分隔
```
[修饰符] class <类名> [extends 父类名] [implements 接口列表]{}
修饰符--访问权限,可选参数：public,abstract,final; 
```
注意：实现接口时，方法名字、返回值类型、参数个数和类型必须与接口一样，必须实现接口中所有方法


抽象类（特殊类）：抽象类不能被实例化，即不能使用new关键字来创建对象
定义：
```
abstract class 类名{
	类体；
}
```
注意：abstract只能用在类和方法上，不能用在属性和一般变量上

抽象方法：
```
abstract <方法返回值类型> 方法名（参数列表）;
eg:public abstract void eat();
```

内部类（嵌套类）:在一个类的内部定义在另一个类，其使用范围只是这个类的内部
实例：
```
public class Outer {
	String outStr="外部变量";
	void outTest(){
		Inner inner=new Inner();
		inner.innerTest();//调用内部类方法
	}
	
	class Inner{//同一包中的其他类都不能访问
		void innerTest(){
			System.out.println("内部类调用外部变量:"+outStr);
		}
	}
	public static void main(String[] args) {
		Outer out = new Outer();
		out.outTest();//内部类调用外部变量:外部变量
	}
}
```

第四章 集合类（容器）
======================
数组长度固定，而集合长度固定
集合中储存的是对象，不是基本数据类型
集合类：用来存放java对象，常见的有List、Set、Map,其中List和Set实现了Collection接口
继承关系如下：
```
HashMap类，TreeMap类->Map接口->java.lang.Object
HashSet类，TreeSet类->Set接口->Collection接口->java.lang.Object
ArrayList类，LinkedList类->List接口->Collection接口->java.lang.Object 
```
1.Collection接口
------------
Collection接口常用方法：
```
add(Object)---将指定的对象添加到集合中
remove（Object）--将指定的对象移出集合
isEmpty()---返回boolean,用于判断当前集合是否为空
iterator()--返回在此Collection元素上进行迭代的迭代器，用于遍历集合中的对象
size（）--返回int型，获取该集合中元素的个数
clear（）--清空该集合
contains（Object obj）--集合中是否存在指定对象，存在返回true，否则false
sort()---排序 
```
实例：
```
public class Zoo {
	public static void main(String[] args) {
		String dog="dog";
		String cat="cat";
		String bird="bird";
		Collection<String> list=new ArrayList<String>();
		list.add(bird);//add方法
		list.add(cat);
		list.add(dog);
		Collection<String> list2=new ArrayList<String>();
		list2.addAll(list);//addAll方法
		Iterator<String> it=list2.iterator();//iterator() 
		//可以用isEmpty判断是否为空
		System.out.println("是否为空"+list2.isEmpty());//是否为空false
		while(it.hasNext()){//遍历输出
			System.out.println(it.next());//bird cat dog
		}
		list2.removeAll(list);
		System.out.println("是否为空"+list2.isEmpty());//是否为空true
	}
}
```
2.常见集合类
----------------
List、Set、Map区别：
List中对象可以重复，按照插入顺序排列
Set中对象没有顺序，对象不允许重复
Map按照Key-value形式储存

2.1 List集合
（1）list接口
列表类型，以线性方式储存，可以通过对象的索引操作对象
常用方法：
```
add(int index,Object obj)---向集合的索引位置添加对象，索引位置从0开始，其他对象索引位置后移
addAll(int index,Collection coll)--向集合中的索引位置添加指定集合中的所有对象
remove（int index）--清除集合中指定索引位置的对象
set（int index，Object obj）--将指定位置改为指定对象
get（int index）--获得指定位置的对象
indexOf(Object obj)--获取对象的第一个索引位置，不存在返回-1
lastIndexOf(Object obj)--获取对象的最后一个索引位置，不存在返回-1
```
（2）ArrayList类
ArrayList类实现的List集合采用数组结构保存对象，
数组结构优点：便于快速随机访问，如果经常需要根据索引位置访问对象，ArrayList类效率高
数组结构缺点：向指定索引位置插入、删除对象速度较慢，插入或者删除对象的索引位置越小效率越低，因为后面的对象要移动位置
eg：
```
public class Zoo {
	public static void main(String[] args) {
		String dog="dog";
		String cat="cat";
		String bird="bird";
		List<String> list=new ArrayList<String>();
		list.add(bird);//add方法
		list.add(cat);
		list.add(dog);
		List<String> list2=new ArrayList<String>();
		list2.addAll(list);//addAll方法
		Iterator<String> it=list2.iterator();//iterator() 
		//可以用isEmpty判断是否为空
		System.out.println("是否为空"+list2.isEmpty());//是否为空false
		while(it.hasNext()){//遍历输出
			System.out.println(it.next());//bird cat dog
		}
		list2.removeAll(list);
		System.out.println("是否为空"+list2.isEmpty());//是否为空true
	}
}
```

(3)LinkedList类
LinkedList类实现List接口使用链表结构保存对象
链表结构优点：便于向集合中插入删除对象
链表结构缺点：随机访问对象的数据较慢
常用方法
```
addFirst(E obj)--将指定对象插入列表的开头
addLast(E obj)--将指定对象插入列表的结尾
getFirst()--获得列表开头的对象
getLast()--获得列表结尾的对象
removeFirst()--移除列表开头对象
removeLast()--移除列表结尾对象
```
eg：
```
public class Zoo {
	public static void main(String[] args) {
		String dog="dog";
		String cat="cat";
		String bird="bird";
		LinkedList<String> list=new LinkedList<String>();
		list.add(bird);//add方法
		list.add(cat);
		list.addFirst(dog);
		Iterator<String> it=list.iterator();//iterator() 
		while(it.hasNext()){//遍历输出
			System.out.println(it.next());//dog bird cat
		}
	}
}
```

2.2 Set集合
Set集合为集类型，集是最简单的一种集合，集中的对象不按特定的方式排序，只是简单地把对象加入集合中，集中对象的访问操作是通过对象的引用进行的，故而在集中不能放重复对象
所以add()方法添加set对象存在对象时，不会进行操作
其实现类有HashSet和TreeSet类
（1）此类实现Set接口，由哈希表(实际上是一个HashMap实例)支持，它不保证Set的迭代顺序，此类允许用null元素
(2)TreeSet类不仅实现了Set接口，还实现了java.util.SortedSet接口，因此其在遍历集合时按照自然顺序递增排序，也可以是按照指定比较器递增排序
TreeSet类增加的方法:
```
first()--返回set中当前第一个（最低）元素
last()--返回set中当前最后一个（最高）元素
comparator()--对set中元素进行排序的比较器，如果set使用其元素的自然顺序，则返回null
headSet(Object obj)--返回一个新的Set集合，新的集合包含obj(不包含)之前的所有对象
subSet(Object form,Object to)---返回一个新的Set集合，新的集合包含from(包含)到to(不包含)之间的所有对象
tailSet（Object to）--返回一个新的Set集合，新的集合包含to(包含)之后的所有对象
```

2.3 Map集合
Map没有继承Collection接口，其提供的是key到value的映射，Map中不能包含相同的key值，每个key值只能映射一个value
(1)Map接口
Map接口包含集合常用的方法如clear()、isEmpty()与size()方法等还包含Map接口特有的方法.
常用方法：
```
put(key k,value v)--返回Object--向集合添加指定的key与value的映射关系
containskey(Object key)--返回boolean--包含指定键的映射则返回true
containsValue(Object value)--返回boolean--映射将一个或者多个键映射到指定值则返回true
get（Object key）--返回Object--返回指定键对象的值，无则返回null
keySet()--返回Set--返回集合中所有键对象形成的Set集合
values()--返回Collection--返回集合中所有值对象形成的Collection集合
```

（2）HashMap类
允许以null作为键对象，但是键对象不能重复，所以只能出现一次
HashMap类适合经常需要添加、删除和定位映射关系，不过在遍历集合时得到的映射关系是无序的
不能直接遍历Map集合，需要先获取集合中的Key集合与Value集合，再分别遍历Key集合与Value集合
实例：
```
public class Zoo {
	public static void main(String[] args) {
		String dog="dog";
		String cat="cat";
		String bird="bird";
		String pig="pig";
		HashMap<String,String> list=new HashMap<String,String>();
		list.put("1",bird);//add方法
		list.put("2",cat);
		list.put("3",dog);
		list.put("4", pig);
		
		Collection<String> keySet=list.keySet();
		Iterator<String> keyIt=keySet.iterator();//iterator() 	
		while(keyIt.hasNext()){//遍历输出
			System.out.print(keyIt.next()+" ");//3 2 1 4
		}
		
		Collection<String> valueSet=list.values();
		Iterator<String> valueIt=valueSet.iterator();//iterator() 	
		while(valueIt.hasNext()){//遍历输出
			System.out.print(valueIt.next()+" ");//dog cat bird pig 
		}
	}
```

(3)TreeMap类
TreeMap类不仅实现了Map接口，还实现了Map接口的子接口java.util.SortedMap
TreeMap类实现的集合不允许键对象为null，因为集合中的映射关系按照一定的顺序排序
需要进行有序的遍历输出建议用TreeMap类，否则建议用HashMap类
实例：
键升序排列
```
public class Zoo {
	public static void main(String[] args) {
		String dog="dog";
		String cat="cat";
		String bird="bird";
		String pig="pig";
		TreeMap<String,String> list=new TreeMap<String,String>();
		list.put("2",cat);
		list.put("1",bird);//add方法
		list.put("3",dog);
		list.put("4", pig);
		
		Collection<String> keySet=list.keySet();
		Iterator<String> keyIt=keySet.iterator();//iterator() 	
		while(keyIt.hasNext()){//遍历输出
			System.out.print(keyIt.next()+" ");//1 2 3 4  
		}
		
		Collection<String> valueSet=list.values();
		Iterator<String> valueIt=valueSet.iterator();//iterator() 	
		while(valueIt.hasNext()){//遍历输出
			System.out.print(valueIt.next()+" ");//bird cat dog pig 
		}
	}
```
2.4 例子
（1）简单电话本
```
public class Mytest{
	static Map map=new HashMap<String, String>();//此行放main中会出错
	
	public void addPerson(String name,String phone){
		map.put(name, phone);
	}
	public String findPhoneByName(String name){
		return (String) map.get(name);
	}
	public static void main(String[] args) {
		Mytest book=new Mytest();
		book.addPerson("liming", "111");
		book.addPerson("danling", "222");
		System.out.print("liming's phone is:"+book.findPhoneByName("liming"));//liming's phone is:111
	}
}
```

（2）去除List集合重复值
```
public class Zoo {
	public static void main(String[] args) {
		String dog="dog";
		String cat="cat";
		String bird="bird";
		List list=new ArrayList<String>();
		list.add(cat);
		list.add(bird);//add方法
		list.add(dog);
		list.add(dog);
		
		Iterator<String> it=list.iterator();
		while(it.hasNext()){//遍历输出
			System.out.print(it.next()+" ");//cat bird dog dog
		}
		//去除重复值---因为set不能重复
		Set set=new HashSet<String>();
		set.addAll(list);
		it=set.iterator();
		while(it.hasNext()){//遍历输出
			System.out.print(it.next()+" ");//bird cat dog 
		} 	
	}
}
```

第五章 IO流
=============
I/O处理技术可以将数据保存到文本文件、二进制文件等，以达到永久保存数据的要求
java以流的形式处理数据，流是一组有序的数组序列，程序从输入流读取数据，向输出流写入数据，每一个数据流都是一个对象，提供各种支持"读入"与"写出"操作的流类。
输入输出的数据流可以为文件、网络、压缩包、其他数据源
java的输入输出功能来自java.io包中的InputStream类、OutputStream类、Reader类、Writer类以及继承他们的各种子类
1.文件类
-----------
File类用于封装系统的文件和目录的相关信息
创建File对象
```
new File(String pathName);//pathName---包含文件名称的路径名eg:"D://1.txt"
或者
new File(String parent,String child);//patent-父路径（必须存在，否则IO异常），child-子路径eg：（"D://a","1.txt"）
或者
new File(File parent,String child);//patent-父抽象路径，child-子路径
```
File类常用方法：
```
String getName()--------------------获取文件名称
String getParent()------------------获取文件父路径字符串
String getPath()--------------------获取文件的相对路径字符串
String getAbsolutePath()------------获取文件的绝对路径字符串
boolean exists()--------------------判断文件或者文件夹是否存在
boolean isFile()--------------------判断是不是文件类型
boolean idDirectory()---------------判断是不是文件夹类型
boolean isAbsolute()----------------判断是不是绝对路径
boolean delete()--------------------删除文件或者文件夹，如果删除成功返回结果为true
boolean mkdir()---------------------创建文件夹，创建成功返回true
boolean mkdirs()--------------------创建路径中包含的所有父文件夹和子文件夹，如果所有父文件夹和子文件夹都成功创建返回true
boolean setReadOnly()---------------设置文件或者文件夹为只读属性
long length()-----------------------获取文件的长度
long lastModified()-----------------获取文件的最后修改日期
String[] list()---------------------获取文件夹中文件或者子文件夹的名称，并存放在字符串数组中
File[] listFiles()------------------获取文件夹中文件或者子文件夹的名称，并存放在File类型数组中
```
实例：
```
public class Mytest{
	public static void print(String str){//此处需要为static 不然main中不能直接调用
		System.out.println(str);
	}
	public static void main(String[] args) {
		String filePath="file/my.txt";
		File file=new File(filePath);//创建文件对象
		print(file.getName());//my.txt
		print(""+file.exists());//boolean类型需要+""转化字符串//false--------------因为没有创建
		print(file.getPath());//file\my.txt
		print(file.getAbsolutePath());//F:\Work\MyEclipse_Web\Test\file\my.txt
		print(file.canExecute()+"");//是不是可执行文件//false
		print(file.canRead()+"");//是不是可以读取//false
		print(file.canWrite()+"");//是否可写//false-----因为没有文件
		print(file.getParent());//file
		print(file.length()+"B");//0B
		print(new Date(file.lastModified())+"");//Thu Jan 01 08:00:00 CST 1970
		print(file.isFile()+"");//false
		print(file.isDirectory()+"");//false
	}
}
```
2.字节输入输出流
-------------
（1）字节输入流抽象类（不能new实例对象）InputStream
方法：
```
int available()----------------------------返回当前输入流数据读取方法可以读取的有效字节数量
Abstract int read()------------------------从当前数据流读取一个字节，已经达到结尾则返回-1
int read(byte[] bytes)---------------------从当前输入流读取一定的byte数据，并存放在数组中，返回读取byte数据的数量，达到结尾则返回-1
int read(byte[] bytes,int off,int len)-----从当前输入流读取一定的byte数据，并存放在数组中指定位置，返回读取byte数据的数量，达到结尾则返回-1
void reset()-------------------------------将当前输入流重新定位到最后一次调用mark()方法时的位置
void mark(int readlimit)-------------------在当前输入流中做标记位置，当调用reset方法时返回到该位置，从标记位置开始，到再读入readlimit个字符为止，这个标记都维持有效
boolean markSupported()-------------------测试当前输入流是否支持mark()和reset()方法，只要其中一个不支持则返回false
long skip(long n)--------------------------跳过和丢弃当前输入流的n个字节数据
void close()-------------------------------关闭当前输入流，并释放与之关联的系统资源
```
实例：用户输入什么，控制台就输出什么
```
public class Mytest{
	public static void main(String[] args) {
		InputStream in=System.in;
		byte[] info=new byte[1024];
		try {
			while(in.read(info) != -1){//循环读取用户输入信息
				String str=new String(info).trim();//根据输入信息创建字符串
				System.out.println(str);
			}
			in.close();//关闭数据流
		} catch (IOException e) {
			e.printStackTrace();
		}
	}
}
```
(2) 字节输出流抽象类OutputStream
方法：
```
void write(byte[] b)---------------------------将byte[]数组中的数据写入当前输出流
void write(byte[] b,int off,int len)-----------将byte[]数组下标off开始的len长度的数据写入当前输出流
Abstract void write(byte b)--------------------写入一个byte数据到当前输出流
void flush()-----------------------------------刷新当前输出流，并强制写入所有缓冲的字节数据
void close()-----------------------------------关闭输出流，释放资源
```
实例
```
public class Mytest{
	public static void main(String[] args) {
		OutputStream out=System.out;
		byte[] info="hello world".getBytes();
		try {
			out.write(info);//控制台输出：hello world
			out.close();
		} catch (IOException e) {
			e.printStackTrace();
		}
	}
}
```
(3)文件字节输入流FileInputStream
文件字节输入流可以从指定文件中读取字节数据，继承自InputStream类
创建FileInputStream实例：
```
new FileInputStream(File file);
或者
new FileInputStream(String filePath);
```
(4)文件字节输出流类FileOutputStream
数据通过文件字节输出流以字节为单位输出并保存到文件中
实例创建同FileInputStream
输入输出流应用程序：
```
public class Mytest{
	public static void main(String[] args) {
		File file=new File("1.txt");
		if(!file.exists()){//文件不存在情况
			try {
				file.createNewFile();//用File file=new File("file/1.txt");时出现找不到路径
				FileOutputStream out=new FileOutputStream(file);
				byte[] info="hello world".getBytes();
				out.write(info);//控制台输出：hello world
				out.close();
			} catch (IOException e) {
				e.printStackTrace();
			}
		}
		
		try {
			FileInputStream in = new FileInputStream(file);
			byte[] msg=new byte[1024];
			int len=in.read(msg);//读取文件信息存入msg
			System.out.print(new String(msg,0,len));//将文件信息输出  //hello world
			in.close();
		} catch (FileNotFoundException e) {
			e.printStackTrace();
		} catch (IOException e) {
			e.printStackTrace();
		}
	}
}
```
3.字符输入输出流
----------------
注意：
字节流以字节为单位传送数据，可以是任何类型的数据如：文本、音频、视频、图片等。
字符流以字符为单位传送数据，只能传送文本类型数据，优点：使用字符流读取中文不会乱码，而字节流不能保证
java中汉字两个字节，而字符类型数据也是两个字节，所以字符类型能够容纳汉字
(1)字符输入流抽象类Reader
方法:
```
boolean ready()-----------------------------判断数据流是否准备好
int read()----------------------------------读入一个字符，读到流结尾返回-1
int read(char[])----------------------------读取一些字符到char[]数组内，并返回所读入的字符数量，读到流结尾则返回-1
Abstract int read(char[] chars,int off,int len)-读取一些字符到char[]数组小标从off到off+len的位置，并返回读入字符的数量，达到结尾则返回-1
void reset()--------------------------------将当前输入流重新定位到最后一次调用mark()时的位置
void mark(int readLimit)--------------------在当前输入流中做标记位置，当调用reset方法时将返回该位置。从标记开始到再读入readLimit个字符为止，这个标记保持有效
boolean markSupported()---------------------测试当前输入流是否支持mark和reset方法，有一个不支持则返回false
long skip(long n)----------------------------跳过参数n指定的字符数量，并返回所跳过的字符数量
Abstract void close()-----------------------关闭流并释放资源
```
（2）字符输出流抽象类Writer
方法：
```
void write(char[] buf)---------------------------将字符数组中的数据写入当前输出流
Abstract void write(char[] b,int off,int len)----将字符数组下标off开始的len长度的数据写入当前输出流
void write(char c)-------------------------------向输出流写入一个字符数据
void write(String c)-----------------------------向输出流写入一个字符串数据
void write(String str,int off,int len)-----------向输出流写入一个字符串从off开始长度为len的数据
Abstract void flush()----------------------------刷新当前输出流，并强制写入所有缓冲的字节数据
Abstract void close()----------------------------关闭输出流，释放资源
```

（3）文件字符输入流FileReader
创建FileReader实例
```
new FileReader(File file)
或者
new FileReader(String filePath)
```
(4)文件字符输出流FileWriter
继承自Writer
数据通过文件字符输出流以字符为单位输出并保存到文件中
创建实例
```
new FileWriter(File file)
或者
new FileWriter(String filePath)
```

文件字符输入输出流实例：
```
public class Mytest{
	public static void main(String[] args) {
		File file=new File("1.txt");
			try {
				if(!file.exists()){//文件不存在情况
					file.createNewFile();//用File file=new File("file/1.txt");时出现找不到路径
					}
				FileWriter out=new FileWriter(file);
				String info="你好.......................";
				out.write(info);//控制台输出：
				out.close();
			} catch (IOException e) {
				e.printStackTrace();
		}
		
		try {
			FileReader in = new FileReader(file);
			char[] msg=new char[1024];
			int len;
			while((len=in.read(msg))!=-1){;//循环读取到文件末尾
			System.out.print(new String(msg,0,len));//将文件信息输出 
			}
			in.close();
		} catch (FileNotFoundException e) {
			e.printStackTrace();
		} catch (IOException e) {
			e.printStackTrace();
		}
	}
}
```

4.操作
----------
(1)复制文件夹
```
public class Mytest{
	public static void copy(File[] file1,File file2){
		if(!file2.exists())
			file2.mkdir();
		for(int i=0;i<file1.length;i++){
			if(file1[i].isFile()){
				try{
					FileInputStream in=new FileInputStream(file1[i]);
					FileOutputStream out=new FileOutputStream(new File(file2.getPath()+File.separator+file1[i].getName()));
					int count=in.available();
					byte[] data=new byte[count];
					if((in.read(data))!=-1)
						out.write(data);
					out.close();
					in.close();
				}catch(Exception e){
					e.printStackTrace();
				}
			}
			if(file1[i].isDirectory()){
				File des=new File(file2.getPath()+File.separator+file1[i].getName());
				des.mkdir();
				copy(file1[i].listFiles(),des);
			}
		}
	}
	public static void main(String[] args) {
		File sourFile=null,desFile=null;
		String sourFolder="mysrc";//被复制的文件夹
		String desFolder="copy";
		sourFile=new File(sourFolder);
		desFile=new File(desFolder);
		if(!sourFile.isDirectory()||!sourFile.exists()){//原文件夹不存在
			System.out.print("源文件夹不存在");
		}
		desFile.mkdir();
		copy(sourFile.listFiles(),desFile);
		System.out.print("文件夹复制成功");
	}
}
```
(2)分行向文件写入数据
```
public class Mytest{
	public static void main(String[] args) {
		String filePath="mysrc/1.txt";
		File file = new File(filePath);
		try{
			if(!file.exists()){
				file.createNewFile();
			}
			FileWriter fw=new FileWriter(file);//文件字符输出流
			BufferedWriter bw=new BufferedWriter(fw);//使用缓冲数据流封装输出流
			bw.write("hello".toCharArray());//写入数据到输出流
			bw.newLine();//写入换行符
			bw.write("你好啊");
			bw.flush();
		}catch(Exception e){
			e.printStackTrace();
		}
	}
}
```
注意：java中的输入输出流是针对内存而言的，将文件从磁盘写入内存就是输入，将内存内容写入磁盘就是输出


第六章 TCP与UDP协议
==========================
1.网络编程必需端口与套接字
---------------
网络实现服务器和客户端之间通信
服务器：提供信息的计算机或者程序
客户端：请求信息的计算机或者程序
客户端和服务器沟通除了用相同的协议外，还要指定一个专用开口------端口。

端口并非真实的物理存在，而是一个虚拟的连接装置，端口被规定为0-65535之间的整数
HTTP服务一般使用80端口，FTP服务使用21端口
```
客户机1 <-> 80端口 <-> HTTP服务器
客户机2 <-> 21端口 <->FTP服务器
```

套接字(Socket)：
用来接收或者传送分组的一个端点
```
客户端（应用程序） <-> Socket <-> Port ------------- Port <-> Socket <-> 服务器（应用程序）
```

2.TCP编程原理
-------------------
TCP（Transimission Control Protocol,传输控制协议）：一种以固接连线为基础的协议，提供两台计算机间可靠的数据传送。抵达数据顺序与传输顺序一样。
TCP负责数据或者文件的分组和重组，与IP协议一起称为TCP/IP协议，IP协议负责发送与接收数据包
TCP协议通信两个应用程序：服务器程序、客户机程序
服务器端与客户端交互如下：
(1)服务器程序创建一个ServerSocket(服务器套接字)，调用accept()方法等待客户端连接
(2)客户端程序创建一个Socket,请求与服务器建立连接
(3)服务器接收客户的连接请求，同时创建一个新的Socket与客户建立连接，服务器继续等待新的请求

TCP编程常用类
(1)InetAddress类
位于java.net包中，InetAddress类对象包含一个Internet主机地址的域名和IP地址
常用方法：
```
InetAddress getByName(String host)-------------------给定主机名确定IP地址
String getHostAddress()------------------------------返回IP地址字符串
String getHostName()---------------------------------获取此IP地址的主机名
Object get(int index)--------------------------------获取指定索引位置的对象
InetAddress getLocalHost()---------------------------返回本地主机的InetAddress对象
String toString()------------------------------------将IP地址转化为String
```
异常处理：UnknownHostException异常------指示主机IP无法确定而抛出的异常
实例：
```
public class Mytest{
	public static void main(String[] args) {
		InetAddress net;
		try{
			net=InetAddress.getLocalHost();//实例化对象
			System.out.println(net.getHostName());//主机名:DESKTOP-27618UQ
			System.out.println(net.getHostAddress());//IP:127.0.0.1
		}catch(UnknownHostException e){
			e.printStackTrace();
		}
	}
}
```

(2)服务器套接字(ServerSocket)
用来给服务器端创建套接字，功能：等待来自网络的"请求"，通过指定的端口来等待连接的套接字
服务器套接字一次可以与一个套接字连接，多台客户机同时请求时，服务器套接字会将连接的客户机存入队列，从中取出套接字连接，如果请求连接数大于最大容纳数（队列默认50），多出的请求将被拒绝。
常用构造方法：
```
ServerSocket(int port)----------------创建绑定到特定端口的服务器套接字
ServerSocket()------------------------创建非绑定服务器套接字
ServerSocket(int port,int backlog)----利用指定的最大列队长度创建指定的本地端口的服务器端套接字
```
常用方法：
```
Socket accept()------------------------等待客户机连接，连接上则创建一个套接字
boolean isBound()----------------------判断ServerSocket的绑定状态
InetAddress getInetAddress()-----------返回此服务器套接字的本地地址
boolean isClosed()---------------------返回服务器套接字的关闭状态
void close()---------------------------关闭服务器套接字
void bind(SocketAddress endpoint)------将ServerSocket绑定到特定地址（IP地址和端口号）
int getInetAddress()-------------------返回服务器套接字等待的端口号
```

(3)套接字Socket类
客户端创建Socket对象后会向指定的IP地址及端口尝试连接，服务器套接字会创建新的套接字与客户端套接字建立连接，连接成功则可以获取套接字的输入输出流，进行数据交换
Socket类常用构造方法
```
Socket(InetAddress address,int port)-------创建连接指定服务器的套接字
Socket(String host,int port)---------------创建连接指定服务器（主机和端口）的套接字
Socket()-----------------------------------创建未进行连接的套接字
```

常用方法：
```
InetAddress getInetAddress()--------------获取套接字连接的地址
int getPort()-----------------------------获取套接字连接的端口
InetAddress getLocalAddress()-------------获取套接字绑定的本地地址
int getLocalPort()------------------------获取套接字绑定的本地接口
void close()------------------------------关闭套接字连接
InputStream getInputStream()--------------获取套接字的输入流
OutputStream getOutputStream()------------获取套接字的输出流
```

(4)TCP程序编写
```
服务器:
public class Server {
	private static ServerSocket serverSocket;

	public static void main(String[] args) {
		try{
			serverSocket = new ServerSocket(1234);
			Socket cliSocket=serverSocket.accept();//客户端套接字--接收客户连接呼叫
			DataInputStream in=new DataInputStream(cliSocket.getInputStream());
			DataOutputStream out=new DataOutputStream(cliSocket.getOutputStream());
			String str=null;
			while(true){
				str=in.readUTF();//读取用户放入连接中的信息
				out.writeUTF(str);//信息写回去
				System.out.println("服务器收到数据："+str);
				Thread.sleep(1000);//线程休眠
			}
			
		}catch(Exception e){
			e.printStackTrace();
		}
	}

}

客户端：
public class Client {
	private static Socket clientScoket;

	public static void main(String[] args) {
		try{
		clientScoket = new Socket("127.0.0.1", 1234);
		DataInputStream in=new DataInputStream(clientScoket.getInputStream());
		DataOutputStream out=new DataOutputStream(clientScoket.getOutputStream());
		out.writeUTF("我是客户端");
		int i=0;
		String str;
		while(true){
			str=in.readUTF();
			out.writeUTF(i++ +"");
			System.out.println("客户端收到:"+str);
			Thread.sleep(1000);
		}
		
		}catch(Exception e){
			e.printStackTrace();
		}
	}

}

运行结果：
服务器收到数据：我是客户端
服务器收到数据：0
服务器收到数据：1
服务器收到数据：2
...

客户端收到:我是客户端
客户端收到:0
客户端收到:1
客户端收到:2
...

```

3.UDP编程原理
-----------------
UDP是一种无连接、不可靠的通信协议，信息传输速度比TCP快
UDP程序步骤：
发送数据包：
(1)使用DatagramSocket()构造方法创建一个数据包套接字
(2)使用DatagramPacket(byte[] buf,int offset,int length,InetAddress address,int port)创建要发送的数据包
(3)使用DatagramSocket类的send()方法发送数据包
接收数据包：
(1)使用DatagramSocket(int port)创建数据包套接字，绑定到指定的端口
(2)使用DatagramPacket(byte[] buf,int length)创建字节数组，来接收数据包
(3)使用DatagramPacket类的receive()方法接收UDP包

UDP编程常用类
(1)UDP程序套接字DatagramSocket类
构造方法：
```
DatagramSocket()------------------------------创建绑定到本地主机上的任何可用的端口
DatagramSocket(int port)----------------------创建绑定到本地主机上的指定端口的套接字
DatagramSocke(int port,InetAddress address)---创建数据报套接字，将其绑定到指定的本地地址
通过类的send()方法发送数据包，receive()方法接收数据包
```
(2)数据报包类DatagramPacket
构造方法：
```
DatagramPacket(byte[] buf,int length)------------------------------指定接收长度，创建DatagramPacket实例
DatagramPacket(byte[] buf,int length,InetAddress address,int port)--指定了数据包的内容空间和大小，同时指定了数据包的目标地址和端口
```

4.练习
---------------
(1)聊天室
```
//将连接套接字、删除套接字、通过套接字输出信息等操作封装在类 SocketManager中
public class SocketManager extends ArrayList {
	//synchronized -- Java语言的关键字，当它用来修饰一个方法或者一个代码块的时候，能够保证在同一时刻最多只有一个线程执行该段代码。
	synchronized void add(Socket socket) {
		super.add(socket);	
	}
	synchronized void delete(Socket socket){
		super.remove(socket);
	}
	synchronized void sendClientCount(){//输出当前聊天人数
		String info="当前聊天人数"+size();//ArrayList的方法
		System.out.println(info);
		writeAll(info);
	}
	
	synchronized void writeAll(String str){
		PrintWriter writer=null;//PrintWriter是一个非常实用的输出流。
		Socket socket;
		for (int i = 0; i < size(); i++) {
			socket = (Socket)get(i);
			try{
				writer=new PrintWriter(socket.getOutputStream(),true);
				if(writer!=null)
					writer.println(str);
			}catch(Exception e){
				e.printStackTrace();
			}
		}
	}
}


public class ServerProcess {
	private SocketManager socketMan=new SocketManager();
	void getServer(){//创建套接字方法
		try {
			ServerSocket serverSocket=new ServerSocket(1234);
			System.out.println("服务器套接字创建");
			while(true){
				Socket socket=serverSocket.accept();//等待连接
				new write_Thread(socket).start();
				socketMan.add(socket);
				socketMan.sendClientCount();
			}
		} catch (IOException e) {
			e.printStackTrace();
		}
	}
	
	class write_Thread extends Thread{
		Socket socket=null;
		private BufferedReader reader;
		private PrintWriter writer;
		public write_Thread(Socket socket){
			this.socket=socket;
		}
		@Override
		public void run() {
			try {
				reader =new BufferedReader(new InputStreamReader(socket.getInputStream()));
				writer =new PrintWriter(socket.getOutputStream(),true);
				String msg;
				while((msg=reader.readLine())!=null){
					System.out.println(msg);
					socketMan.writeAll(msg);
				}
			} catch (IOException e) {
				e.printStackTrace();
			}
		}
	}
	
	public static void main(String[] args) {
		ServerProcess server=new ServerProcess();
		server.getServer();
	}

}


public class Client extends JFrame implements Runnable {
	private JPanel jpanel = new JPanel();
	private JLabel nameLabel=new JLabel("姓名： ");
	private JTextField nameField=new JTextField();
	private JTextArea msgArea=new JTextArea();
	private JTextField sendFiled=new JTextField();
	private JScrollPane jScrollPane=new JScrollPane();
	private BufferedReader reader;
	private PrintWriter writer;
	private Socket socket;
	public Client(String title){
		super(title);
		this.setSize(360,340);
		this.add(jpanel);
		jpanel.setLayout(null);//窗体布局
		msgArea.setEditable(false);
		jpanel.add(nameLabel);
		nameLabel.setBounds(10,10,60,20);
		jpanel.add(nameField);
		nameField.setBounds(60,10,270,21);
		jpanel.add(sendFiled);
		sendFiled.setBounds(10,270,320,21);
		msgArea.setColumns(20);
		msgArea.setRows(5);
		jScrollPane.setViewportView(msgArea);
		jpanel.add(jScrollPane);
		jScrollPane.setBounds(10,40,320,220);
		sendFiled.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				writer.println(nameField.getText()+":"+sendFiled.getText());
				sendFiled.setText("");
			}
		});
	}
	public void run() {
		while(true){
			try{
				msgArea.append(reader.readLine()+"\n");//文本域中读取内容分行显示
			}catch(Exception e){
				e.printStackTrace();
			}
		}
	}
	void getSocket(){
		msgArea.append("尝试与服务器连接");
		try{
			socket=new Socket("127.0.0.1",1234);
			msgArea.append("聊天准备完毕");
			reader=new BufferedReader(new InputStreamReader(socket.getInputStream()));
			writer = new PrintWriter(socket.getOutputStream(),true);
			new Thread(this).start();
		}catch(Exception e){
			e.printStackTrace();
		}
	}

	public static void main(String[] args) {
		Client client=new Client("聊天室");
		client.setVisible(true);
		client.getSocket();
	}

}
```
运行结果：
服务器：
服务器套接字创建
当前聊天人数1
当前聊天人数2
zhang:你好
li:你好

客户端：
![图片](img/javause/12.png)
![图片](img/javause/13.png)

(2)广播数据报
一个UDP程序，实现主机不断地向客户端发送消息
```
public class Weather extends Thread {
	String weather="天气预报，明天降温";
	int port=1234;
	InetAddress iaddress=null;
	MulticastSocket socket=null;//创建多点广播套接字
	public Weather() {
		try {
			iaddress=InetAddress.getByName("127.0.0.1");//实例化InetAddress对象，指定地址
			socket=new MulticastSocket(port);//实例化多点广播套接字
			socket.setTimeToLive(1);//指定发送范围是本地网络
			socket.joinGroup(iaddress);//加入广播组
		} catch (Exception e) {
			e.printStackTrace();
		}
	}
	
	@Override
	public void run() {
		while(true){
			DatagramPacket packet=null;
			byte[] data=weather.getBytes();//声明字节数组
			packet=new DatagramPacket(data, data.length, iaddress, port);
			System.out.println(new String(data));
			try {
				socket.send(packet);
				sleep(3000);
			} catch (Exception e) {
				e.printStackTrace();
			}
		}
	}
	public static void main(String[] args) {
		Weather w=new Weather();
		w.start();
	}
}


public class Client extends JFrame implements Runnable, ActionListener {
	int port=1234;
	InetAddress group=null;
	MulticastSocket socket=null;
	JButton begain=new JButton("接收");
	JButton stop=new JButton("停止");
	JTextArea textArea=new JTextArea(10,10);//显示接收广播的文本域
	JTextArea textArea2=new JTextArea(10,10);
	Thread thread;
	boolean b=false;
	public Client() {
		super("广播数据报");
		thread=new Thread(this);
		begain.addActionListener(this);//绑定按钮的单击事件
		stop.addActionListener(this);//绑定按钮的单击事件
		textArea.setForeground(Color.blue);//指定文本域中文本的颜色
		JPanel north=new JPanel();//创建JPanel对象
		north.add(begain);
		north.add(stop);
		add(north,BorderLayout.NORTH);//将north放置在窗体的上面
		JPanel center=new JPanel();//创建面板对象center
		center.setLayout(new GridLayout(1,2));//设置面板布局
		center.add(textArea);//将文本域添加到面板上
		center.add(textArea2);//将文本域添加到面板上
		add(center,BorderLayout.CENTER);//设置面板布局
		validate();//刷新
		try {
			group=InetAddress.getByName("127.0.0.1");
			socket=new MulticastSocket(port);
			socket.joinGroup(group);//加入广播组
		} catch (Exception e) {
			e.printStackTrace();
		}
		setBounds(100,50,360,380);//设置布局
		setVisible(true);
	}
	
	public void actionPerformed(ActionEvent e) {
		if(e.getSource()==begain){//单击按钮begain触发事件
			begain.setBackground(Color.pink);//设置按钮颜色
			stop.setBackground(Color.gray);
			if(!(thread.isAlive())){//如果线程不处于新建状态
				thread=new Thread(this);//实例化Thread
			}
			thread.start();
			b=false;
		}
		if(e.getSource()==stop){
			begain.setBackground(Color.yellow);
			stop.setBackground(Color.red);
			b=true;
		}
	}

 	public void run() {
 		while(true){
 			byte[] data=new byte[1024];
 			DatagramPacket packet=new DatagramPacket(data, data.length, group, port);//待接收的数据包
 			try {
				socket.receive(packet);//接收数据包
				String msg=new String(data, 0, packet.getLength());//获取数据包中的内容
				textArea.setText("接收的内容： "+msg);//将接收的内容显示在文本域中
				textArea2.append(msg+"\n");//每条信息为一行
			} catch (IOException e) {
				e.printStackTrace();
			}
 			if(b==true){
 				break;
 			}
 			
 		}
	}

	public static void main(String[] args) {
		Client client=new Client();
		client.setSize(460, 200);
	}

}
```
运行结果：
![图片](img/javause/14.png)


第七章 窗口程序开发
===========================
Swing功能比AWT强大，Swing中除了保留AWT中的几个重要的重量级组件外，其他都是轻量级组件，使用java窗体开发很复杂。
java窗体开发包含窗体、面板、容器布局以及基本组件等
1.创建JFrame窗体
----------------
JFrame类：定义生成窗体的模板，实例化一个窗体类就生成一个窗体。创建窗体后，可以向窗体添加组件，同时为组件添加事件监听器，处理最大化、最小化、关闭、调整大小等窗体事件。
窗体是一个组件容器，所有组件都必须有窗体去承载。
构造方法：
```
public JFrame()//默认构造方法，创建一个初始不可见、没有标题的新窗体
或者
public JFrame(String title)//创建一个初始不可见、有标题的新窗体
注意：窗体创建是不可见的，需要使用setVisible(true)方法使窗体可见，自定义窗体继承自JFrame类
```
实例:
```
public class DemoFrame extends JFrame {
	public DemoFrame(){
		super();
		setTitle("JFrame窗体");//设置窗体标题
		setBounds(100,100,200,300);//设置窗口显示位置及窗体大小
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);//给予窗体关闭方式，EXIT_ON_CLOSE表示退出程序，并关闭窗体
		final JLabel label=new JLabel();//定义标签对象
		label.setText("我的自定义窗口");
		getContentPane().add(label,BorderLayout.CENTER);//向窗体添加组件，首先要在窗体中添加容器对象，在容器对象添加组件
	}
	public static void main(String[] args) {
		EventQueue.invokeLater(new Runnable() {
			public void run() {
				try{
					DemoFrame frame=new DemoFrame();
					frame.setVisible(true);
				}catch(Exception e){
					e.printStackTrace();
				}
			}
		});
	}

}
```
运行结果：
![自定义窗体图片](img/javause/1.png)

2.向窗体添加面板
----------------
面板也是一个Swing容器，可以容纳其他组件。
面板不能像窗口一样独立使用，必须添加到其他容器中才能发挥作用。
(1)JPanel面板
JPanel面板可以聚集一些组件进行布局，它继承自java.awt.Container类。
JPanel组件作为容器类，除可以添加组件，也可以设置布局管理器，将面板中组件布局
如:
```
public class JPanelTest extends JFrame {
	public JPanelTest(){
		Container c=getContentPane();
		c.setLayout(new GridLayout(2,2,2,2));//将容器设置为两行两列的网络布局
		//初始化面板，设置边界布局
		JPanel p1=new JPanel(new BorderLayout());
		JPanel p2=new JPanel(new BorderLayout());
		JPanel p3=new JPanel(new BorderLayout());
		JPanel p4=new JPanel(new BorderLayout());
		//在各面板中添加按钮
		p1.add(new JButton("按钮1"));
		p2.add(new JButton("按钮2"));
		p3.add(new JButton("按钮3"));
		p4.add(new JButton("按钮4"));
		//在容器中添加面板
		c.add(p1);
		c.add(p2);
		c.add(p3);
		c.add(p4);
		setVisible(true);
		setBounds(100,100,400,400);//设置窗体的显示位置与大小
		pack();
	}
	public static void main(String[] args) {
		new JPanelTest();
	}
}
```
运行结果:
![图片](img/javause/2.png)

(2)JScrollPane面板
JScrollPane面板是一种带滚动条的面板，可以较小的容器窗体显示一个较大部分的内容，但是常用于布置单个组件，不可以使用布局管理器。
如果要在JScrollPane面板上放置多个组件，需要将多个组件放置在JPanel面板上，然后将面板作为一个整体组件添加在JScrollPane组件上。
```
public class JScrollPaneDemo extends JFrame {
	public JScrollPaneDemo(){
		Container c=getContentPane();//创建容器
		JTextArea jta=new JTextArea(20, 50);//创建文本区域组件
		JScrollPane jspane=new JScrollPane(jta);
		c.add(jspane);//面板添加到容器中
		setTitle("有滚动条的文字编辑器");
		setSize(200, 200);//设置窗体大小
		setVisible(true);//可见
		setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
	}
	public static void main(String[] args) {
		new JScrollPaneDemo();
	}

}
```
运行结果:
![图片](img/javause/3.png)

(3)分割面板
分割面板不像JPanel与JScrollPane面板简单，需要设置分割面板水平分割还是垂直分割等
分割面板JSplitPane类常用构造方法:
```
JSplitPane()-----------------------------------------创建一个在水平方向进行分割、无连续布局且为组件使用两个按钮的分割面板
JSplitPane(int orient)-------------------------------创建一个水平方向分割且无连续布局的分割面板
JSplitPane(int orient,Component leftC,Component rigthC)-创建一个在指定方向进行分割、不连续重绘的指定组件的分割面板
```
常用方法：
```
getBottomComponent()-----------------------------返回分隔条下面或者右边的组件
getDividerSize()---------------------------------返回分隔条的大小
getLeftComponent()-------------------------------返回分隔条左边或者上面的组件
getRightComponent()------------------------------返回分隔条右边或者下面的组件
getTopComponent()--------------------------------返回分隔条上面或者左边的组件
remove(Component component)----------------------移除窗格中的子组件component
setBottomComponent(Component comp)---------------将组件设置到分隔条的下面或者右面
setLeftComponent(Component comp)-----------------将组件设置到分隔条的左边或者上面
setRightComponent(Component comp)----------------将组件设置到分隔条的右边或者下面
setTopComponent(Component comp)------------------将组件设置到分隔条的上面或者左边
setDividerLocation(int location)-----------------设置分隔条位置
setDividerSize(int newSize)----------------------设置分隔条大小
setOneTouchExpandable(boolean newValue)----------属性为true时，可以使分隔条上提供一个UI小部件来快速展开/折叠分隔条
setOrientation(int orient)-----------------------设置分隔方向，JSplitPane.HORIZONTAL_SPLIT-------------------------水平方向上对分割面板进行分割，JSplitPane.VERTICAL_SPLIT-------------------------垂直方向上对分割面板进行分割
```
实例：
```
public class SplitPaneFrame extends JFrame {
	public SplitPaneFrame(){
		setTitle("使用分割面板");
		setBounds(100,100,200,200);
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		//创建在水平方向分割的分割面板
		final JSplitPane hSplitPane=new JSplitPane();
		JButton labelLeft=new JButton("左边");//创建标签
		//创建一个在垂直方向进行分割的分割面板
		final JSplitPane vSplitPane=new JSplitPane(JSplitPane.VERTICAL_SPLIT);
		JLabel labelTop=new JLabel("上面");//创建标签
		JLabel labelBottom=new JLabel("下面");
		vSplitPane.setBottomComponent(labelBottom);
		vSplitPane.setTopComponent(labelTop);
		vSplitPane.setDividerLocation(40);//设置垂直分割分隔条距离上边为40像素
		hSplitPane.setLeftComponent(labelLeft);//水平分割面板左边放置标签
		hSplitPane.setRightComponent(vSplitPane);//水平分割面板右边放置垂直分割面板
		hSplitPane.setDividerLocation(40);//水平分隔条距离左边为40像素
		hSplitPane.setOneTouchExpandable(true);//设置水平分割面板分隔条显示UI小部件
		getContentPane().add(hSplitPane);//把水平分割面板添加到窗体上
	}
	public static void main(String[] args) {
		SplitPaneFrame splitPaneFrame=new SplitPaneFrame();
		splitPaneFrame.setVisible(true);
	}

}

```
运行结果:
![图片](img/javause/4.png)

(4)选项卡面板
JTabbedPane对象
选项卡面板可以在窗体中放置多个标签页，每个标签页相当于与选项卡大小相同的容器，每个标签页可以放置一个或者多个组件，使每个标签页实现不同页面的效果。
构造方法：
```
JTabbedPane()-------------------------------创建一个上面显示标签，布局方式为自动换行的空选项卡
JTabbedPane(int tabPlace)-------------------创建一个在指定位置显示标签，布局方式为自动换行的空选项卡
JTabbedPane(int tabPlace,int tabLayout)-----创建一个在指定位置显示标签和具有指定布局策略的空选项卡
```
JTabbedPane类常用字段:
```
JTabbedPane.TOP-----------------------------选项卡的上边位置显示标签
JTabbedPane.BOTTOM--------------------------选项卡的下边位置显示标签
JTabbedPane.LEFT----------------------------选项卡的左边位置显示标签
JTabbedPane.RIGHT---------------------------选项卡的右边位置显示标签
JTabbedPane.WRAP_TAB_LAYOUT-----------------当选项卡的一行或一列不能显示所有标签时，标签会自动换行或者换列
JTabbedPane.SCROLL_TAB_LAYOUT---------------当选项卡的一行或一列标签显示不全时，标签行或列会出现UI调节组件
```
选项卡面板常用方法：
```
addTab(String title,Component component)-------------------------添加一个标题为title且没有图标的选项卡
addTab(String title,Icon icon,Component component)-------------------------添加一个标题为title,图标为icon的选项卡
addTab(String title,Icon icon,Component component，String tip)-------------------------添加一个标题为title,图标为icon，工具提示文本为tip的选项卡
getSelectedComponent()-------------------------------------------返回选项卡面板当前选择的选项卡
getSelectedIndex()-----------------------------------------------返回当前选择的选项卡的索引
getTabComponentAt(int index)-------------------------------------返回索引值为index位置上的选项卡
getTabCount()----------------------------------------------------返回选项卡面板的选项卡数
getTitleAt(int index)--------------------------------------------返回索引值为index位置的选项卡标题
getToolTipTextAt(int index)--------------------------------------返回索引值为index位置的选项卡工具的提示文本
insertTab(String title,Icon icon,Component component,String tip,int index)--在索引值为index位置插入一个标题为title，图标为icon,工具提示文本为tip的选项卡
setIconAt(int index,Icon icon)-----------------------------------将索引值为index的位置的图标设置为icon
setSelectedComponent(Component e)--------------------------------设置此选项卡面板的已选组件
setSelectedIndex(int index)--------------------------------------设置索引值为index位置处的选项卡为当前选项卡
setTitleAt(int index,String title)-------------------------------将索引值为index位置的选项卡标题设置为true
setToolTipTextAt(int index,String toolTipText)-------------------将索引值为index位置的工具提示文本设置为toolTipText
```
实例:-------------------------------------------------------图片怎么弄???????????????????????
```
public class JTabblePaneText extends JFrame {
	public JTabblePaneText(){
		super();
		setTitle("创建选项卡面板");
		setBounds(100,100,200,200);
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		//创建一个在上面显示标签，布局方式为自动换行的空选项卡
		final JTabbedPane tabbedPane=new JTabbedPane();
		final JButton button=new JButton("按钮");//创建按钮组件
		URL url1=JTabblePaneText.class.getResource("1.ico");//获取图片所在的URL，本类路径下包含一个1.gif的图片文件，路径不正确会抛出异常
		Icon icon1=new ImageIcon(url1);//实例化Icon对象
		tabbedPane.addTab("选项卡1", icon1, button, "这里使用了按钮");//添加组件是按钮，提示文本：这里使用了按钮
		final JCheckBox checkBox=new JCheckBox("复选框");//创建复选框组件
		tabbedPane.addTab("选项卡2", null, checkBox, null);//第二个选项卡，放置复选框组件，无标题图标和工具栏提示文本
		URL url2=JTabblePaneText.class.getResource("2.ico");
		Icon icon2=new ImageIcon(url2);
		tabbedPane.setIconAt(1, icon2);//第二个选项卡添加标签图标
		JTextArea textArea = new JTextArea("文本区域");//创建文本域组件
		URL url3=JTabblePaneText.class.getResource("3.ico");
		Icon icon3=new ImageIcon(url3);
		tabbedPane.addTab("选项卡3", icon3, textArea, null);//第三个选项卡，放置文本域组件，选项卡无标签图片和工具提示文本
		tabbedPane.setToolTipTextAt(2, "这里使用文本域");//为第3个选项卡添加工具提示文本
		final JRadioButton radioButton=new JRadioButton("单选按钮");//创建单选按钮组件
		URL url4=JTabblePaneText.class.getResource("4.ico");
		Icon icon4=new ImageIcon(url4);
		tabbedPane.addTab("选项卡4", icon4, radioButton, null);
		getContentPane().add(tabbedPane, BorderLayout.CENTER);//选项卡放到窗体上
	}
	public static void main(String[] args) {
		JTabblePaneText tabblePaneFrame=new JTabblePaneText();
		tabblePaneFrame.setVisible(true);
	}

}
```

3.布局
-------------
java开发应用程序必须用布局管理器管理每个容器中的组件布局，因为不同的平台显示组件的策略和样式不一样，无法确定不同平台的组件大小和样式
(1)绝对布局
使用绝对布局的窗体，需要牺牲跨平台的性能，采用绝对布局在不同的平台上可能出现组件重叠现象。
绝对布局步骤：
A.使用Container.setLayout(null)方式取消布局管理器
B.使用Component.setBounds()方法来设置每个组件的大小与位置
实例：绝对布局创建登录窗体
```
public class EntryFrame extends JFrame {
	public EntryFrame(){
		super();
		getContentPane().setLayout(null);//窗体设置为绝对布局
		setBounds(100,100,320,180);//窗体显示位置和大小
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		final JPanel panel=new JPanel();//定义面板组件
		panel.setLayout(null);//面板布局方式
		panel.setBounds(0,0,316,150);//面板位置和大小
		getContentPane().add(panel);//窗体中添加面板
		
		final JLabel name =new JLabel();//标签
		name.setFont(new Font("微软雅黑", Font.PLAIN,12));//设置标签显示字体样式
		name.setText("用户名：");//设置标签显示内容
		name.setBounds(62,27,52,26);
		panel.add(name);
		JTextField nameTextField=new JTextField();//文本控件框
		nameTextField.setBounds(120,30,129,22);
		panel.add(nameTextField);
		
		final JLabel passWd =new JLabel();//标签
		passWd.setFont(new Font("微软雅黑", Font.PLAIN,12));//设置标签显示字体样式
		passWd.setText("密码：");//设置标签显示内容
		passWd.setBounds(65,55,44,18);
		panel.add(passWd);
		JTextField passWdTextField=new JTextField();//文本控件框
		passWdTextField.setBounds(120,58,129,22);
		panel.add(passWdTextField);
		
		final JButton entry=new JButton();
		entry.setText("登录");
		entry.setBounds(84,104,64,28);
		panel.add(entry);
		final JButton cancel=new JButton();
		cancel.setText("取消");
		cancel.setBounds(170,104,64,28);
		panel.add(cancel);
		
	}
	public static void main(String[] args) {
		EventQueue.invokeLater(new Runnable() {
			public void run() {
				try{
					EntryFrame frame=new EntryFrame();
					frame.setVisible(true);
				}catch(Exception e){
					e.printStackTrace();
				}
			}
		});
	}

}
```
运行结果:
![图片](img/javause/6.png)

(2)边界布局
BorderLayout类
该布局管理器将组件布局在东南西北中五个区域，每个区域放置一个组件，也可以是指定区域中放置包含其他组件的容器。
构造方法：
```
BorderLayout()--------------------------创建默认的边界布局管理器，在各个区域的水平垂直方向没有设置组件间距
BorderLayout(h,v)-----------------------根据接收的两个参数设置管理器水平和垂直方向的间距
```
定位常量:
```
BorderLayout.NORTH-----------------------在容器中添加组件时组件位于顶部
BorderLayout.SOUTH-----------------------在容器中添加组件时组件位于底部
BorderLayout.EAST------------------------在容器中添加组件时组件位于右部
BorderLayout.WEST------------------------在容器中添加组件时组件位于左 部
BorderLayout.CENTER----------------------在容器中添加组件时组件置于中间开始填充，直到与其他组件边界连接
```
实例：
```
public class BorderFrame extends JFrame {
	public BorderFrame(){
		setTitle("边界布局管理器");
		setBounds(100,100,300,200);
		JButton northButton=new JButton("北");
		JButton southButton=new JButton("南");
		JButton westButton=new JButton("西");
		JButton eastButton=new JButton("东");
		JButton centerButton=new JButton("中");
		Container panel=getContentPane();//获取窗体容器
		panel.setLayout(new BorderLayout());//容器使用边界布局管理器
		panel.add(northButton,BorderLayout.NORTH);//将按钮添加到指定位置
		panel.add(southButton,BorderLayout.SOUTH);//将按钮添加到指定位置
		panel.add(westButton,BorderLayout.WEST);//将按钮添加到指定位置
		panel.add(eastButton,BorderLayout.EAST);//将按钮添加到指定位置
		panel.add(centerButton,BorderLayout.CENTER);//将按钮添加到指定位置
		setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
	}
	public static void main(String[] args) {
		BorderFrame frame=new BorderFrame();
		frame.setVisible(true);
	}
}
```
运行效果：
![图片](img/javause/7.png)

(3)网格布局
GridLayout类
网格布局：容器被分成大小相等的矩形，每个矩形区域可以放置一个组件
构造方法:
```
GridLayout()-----------------------------------------------创建默认网格布局，组件排列在一行或者一列中
GridLayout(int rows,int cols)------------------------------指定行数、列数网格布局，所有组件分配相同大小空间
GridLayout(int rows,int cols,int hgap,int vgap)------------指定行数、列数、组件间距网格布局，所有组件分配相同大小空间
```
常用方法:
```
setColumns(int cols)---------------------------------------设置布局管理器列数
setRows(int rows)------------------------------------------设置布局管理器行数
setHgap(int hgap)------------------------------------------设置布局管理器组件水平距离
setVgap(int vgap)------------------------------------------设置布局管理器组件垂直距离
```
实例
```
public class GridLayoutFrame extends JFrame {
	public GridLayoutFrame(){
		setTitle("网格布局");
		setBounds(100,100,300,200);
		JButton[] button=new JButton[9];//定义按钮数组
		Container panel=getContentPane();//定义容器
		panel.setLayout(new GridLayout(3,3));
		for (int i = 0; i < button.length; i++) {
			button[i]=new JButton("按钮"+(i+1));//不能用++i---否则死循环
			panel.add(button[i]);
		}
		setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
	}
	public static void main(String[] args) {
		GridLayoutFrame frame=new GridLayoutFrame();
		frame.setVisible(true);
	}

}
```
运行结果：
![图片](img/javause/8.png)

（4）流式布局
FlowLayout类
像流一样按指定方向排放控件，直到占据一行的所有空间（根据窗体大小而定），再向下移动到下一行。
构造方法:
```
FlowLayout()-----------------------------------------居中对齐，默认的水平和垂直间距是5个单位
FlowLayout(int align)--------------------------------创建具有指定对齐方式的FlowLayout对象
FlowLayout(int align,int hgap,int vgap)--------------创建指定对齐方式及指定的水平垂直间隔
```
对齐方式（align）:
```
FlowLayout.LEFT---------------单行中左对齐
FlowLayout.CENTER-------------单行中中对齐
FlowLayout.RIGHT--------------单行中右对齐
```
实例：
```
public class FlowLayoutFrame extends JFrame {
	public FlowLayoutFrame(){
		setTitle("流式布局管理器");
		Container c=getContentPane();
		c.setLayout(new FlowLayout(FlowLayout.CENTER,10,10));//窗体使用流式布局，控件居中
		for (int i = 0; i < 10; i++) {
			c.add(new JButton("按钮"+i));
		}
		setSize(300,200);//设置窗体大小
		setVisible(true);
		setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
	}
	public static void main(String[] args) {
		new FlowLayoutFrame();
	}

}
```
运行结果：调整窗体大小会得到不同排列结果------根据窗口大小一行一行排完
![图片](img/javause/9.png)

4.基本控件
---------------
组件是绘制软件界面的基本元素，是软件和用户之间的交流要素。
(1)标签JLabel
标签用于显示文本或者提示信息，支持文本字符串和图标。
构造方法：
```
JLabel()-----------------------------------------------创建一个既无文本内容又无图像内容的标签
JLabel(String text)------------------------------------创建一个具有文本内容的标签
JLabel(String text,int horizontalAlignment)------------创建一个具有文本内容并且指定水平显示位置的标签
JLabel(Icon icon)--------------------------------------创建一个具有图像内容的标签
JLabel(Icon icon,int horizontalAlignment)--------------创建一个具有图像内容并且指定水平显示位置的标签
JLabel(String text,Icon icon,int horizontalAlignment)--创建一个既有文本内容又有图像内容并且指定水平显示位置的标签
```
常用方法：
```
setText(String text)-----------------------------------设置显示的文本
setIcon(Icon icon)-------------------------------------设置显示的图像
setHorizontalAlignment(int alignment)------------------设置标签内容在水平方向的对齐方式
setHorizontalTextPosition(int textPosition)------------设置文本相对于图像在水平方向的位置
setVerticalAlignment(int alignment)--------------------设置标签内容在垂直方向的对齐方式
setVerticalTextPosition(int textPosition)--------------设置文本相对于图像在垂直方向的位置
setIconTextGap(int iconTextGap)------------------------设置文本与图像之间的距离，单位像素，默认为4
setEnabled(boolean enabled)----------------------------设置标签是否可用
setDisabledIcon(Icon disabledIcon)---------------------设置当标签不考用时显示的图像
```

(2)普通按钮JButton
构造方法：
```
JButton(String text)-----------------------------创建一个带有文本标识的按钮
JButton(Icon icon)-------------------------------创建一个带有图像标识的按钮
JButton(String text，Icon icon)------------------创建一个带有文本和图像标识的按钮
```
常用方法:
```
isDefaultButton()--------------------------------查看按钮是否为所在顶层容器组件的默认按钮，是则true
removeNotify()-----------------------------------如果按钮为所在顶层容器组件的默认按钮，则将顶层容器组件的默认按钮设置为null
setEnabled(boolean b)----------------------------设置按钮是否可用，默认可用，设置false不可用
setIcon(Icon defaultIcon)------------------------设置按钮的默认图像
setRolloverIcon(Icon rolloverIcon)---------------设置当光标移动到按钮上时显示的图像
setPressedIcon(Icon pressedIcon)-----------------设置当按钮被按下时显示的图像
setDisabledIcon(Icon disabledIcon)---------------设置当按钮不可用时显示的图像
addActionListener(ActionListener l)--------------为按钮添加一个ActionListener监听器，捕获按钮的ActionEvent事件
addChangeListener(ChangeListener l)--------------为按钮添加一个ChangeListener监听器，捕获按钮的ChangeEvent事件
```

(3)单选按钮JRadioButton
JRadioButton类可以单独使用，也可以与ButtonGroup类联合使用组成一个单选按钮组（只能选择其中一个）
ButtonGroup常用方法:
```
add(AbstractButton b)--------------------------------------添加按钮到按钮组中
remove(AbstractButton b)-----------------------------------从按钮组中移除按钮
getButtonCount()-------------------------------------------返回按钮组中包含按钮的个数，返回int型
getElements()----------------------------------------------返回一个Enumeration类型的对象，通过该对象可以遍历按钮组中包含的所有按钮对象
```
JRadioButton构造方法:
```
JRadioButton()------------------------------------------创建一个默认的单选按钮，在默认情况下没有指定文本和图像，而且没有被选中
JRadioButton(String text)-------------------------------创建一个指定文本的单选按钮
JRadioButton(String text,boolean selected)--------------创建一个指定文本和选择状态的单选按钮
```
注意:在联合使用JRadioButton和ButtonGroup时，并不能将包含JRadioButton对象的Button对象添加到相应的容器组中，只能逐个添加JRadioButton对象到相应的容器控件中
实例:
```
public class JRadioButtonFrame extends JFrame {
	public JRadioButtonFrame(){
		super();
		setTitle("单选按钮");
		ButtonGroup group=new ButtonGroup();
		getContentPane().setLayout(new FlowLayout(FlowLayout.CENTER));
		setBounds(100,100,230,90);
		setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
		final JRadioButton radioButton1=new JRadioButton();
		group.add(radioButton1);
		radioButton1.setText("运动");
		getContentPane().add(radioButton1);
		final JRadioButton radioButton2=new JRadioButton("读书",true);
		group.add(radioButton2);
		getContentPane().add(radioButton2);
//		final JRadioButton radioButton3=new JRadioButton("音乐",true);//设置成这样不取作用，还是只有按钮2被选中
		final JRadioButton radioButton3=new JRadioButton("音乐");
		group.add(radioButton3);
		getContentPane().add(radioButton3);
		setVisible(true);
	}
	public static void main(String[] args) {
		new JRadioButtonFrame();
	}

}

```
运行结果:
![图片](img/javause/10.png)

(4)复选框JCheckBox
复选框控件可以同时选择多个选项
构造方法：
```
JCheckBox()--------------------------------------------创建一个默认的复选框，在默认情况下既未指定文本又未指定图像，并且未被选择
JCheckBox(String text)---------------------------------创建一个指定文本的复选框
JCheckBox(String text,boolean selected)----------------创建一个指定文本和选择状态的复选框
```
实例：
```
public class CheckBoxFrame extends JFrame {
	public CheckBoxFrame(){
		super();
		getContentPane().setLayout(null);
		setBounds(100,100,300,100);
		setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
		JCheckBox cb1=new JCheckBox();
		cb1.setBounds(10,34,64,26);
		cb1.setText("运动");
		getContentPane().add(cb1);
		JCheckBox cb2=new JCheckBox();
		cb2.setBounds(110,34,64,26);
		cb2.setText("读书");
		getContentPane().add(cb2);
		JCheckBox cb3=new JCheckBox();
		cb3.setBounds(210,34,64,26);
		cb3.setText("音乐");
		getContentPane().add(cb3);
		final JLabel label=new JLabel();
		label.setText("你的爱好是:");
		label.setBounds(10,10,91,18);
		getContentPane().add(label);
		setVisible(true);
	}
	public static void main(String[] args) {
		new CheckBoxFrame();
	}
}
```
![图片](img/javause/11.png)

（5）文本
文本控件包含单行文本框控件JTextFiled、密码控件JPasswordField、文本域控件JTextArea
单行文本框控件JTextFiled类构造方法：
```
JTextFiled()---------------------------------------创建一个默认的文本框
JTextFiled(String text)----------------------------创建一个指定初始化文本信息的文本框
JTextFiled(int columns)----------------------------创建一个指定列数的文本框
JTextFiled(String text,int columns)----------------创建一个指定初始化文本信息又指定列数的文本框
```
密码控件JPasswordField构造方法：
```
JPasswordField()-----------------------------------创建一个默认的密码框
JPasswordField(String text)------------------------创建一个指定初始化文本信息的密码框
JPasswordField(int columns)------------------------创建一个指定列数的密码框
JPasswordField(String text,int columns)------------创建一个指定初始化文本信息和指定列数的密码框

方法：
setEchoChar(char a)--------------------------------改变密码框中的显示字符
```

文本域控件JTextArea构造方法：
```
JTextArea()---------------------------------------创建一个默认的文本域
JTextArea(String text)----------------------------创建一个包含指定内容的文本域
JTextArea(int rows,int columns)-------------------创建一个指定行数和列数的文本域
JTextArea(String text,int rows,int columns)-------创建一个包含指定内容又指定行数和列数的文本域
```
实例：
```
public class FieldDemo extends JFrame {
	private JTextArea textArea;
	public static void main(String[] args) {
		FieldDemo frame=new FieldDemo();
		frame.setVisible(true);
	}
	public FieldDemo() {
		super();
		getContentPane().setLayout(null);
		setBounds(100, 100, 378, 311);
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		final JScrollPane scrollPane=new JScrollPane();//滚动面板
		scrollPane.setBounds(0,0,370,277);
		getContentPane().add(scrollPane);//将滚动面板添加到窗体中
		textArea=new JTextArea();//创建文本域控件
		scrollPane.setViewportView(textArea);//将文本域添加到控制面板
		String aline;
		try {
			BufferedReader br=new BufferedReader(new FileReader("src/com/zhang/test/FieldDemo.java"));
			while((aline=br.readLine())!=null){
				textArea.append(aline+"\n");
			}
			br.close(); 
		} catch (Exception e) {
			e.printStackTrace();
		}
	}
}
```

![图片](img/javause/15.png)


(6)列表控件
列表框包括列表框Jlist和下拉列表框JComboBox。
Jlist类构造方法：
```
Jlist()------------------------------------------创建一个不包含任何选项的列表框
Jlist(Object[] listData)-------------------------创建一个包含选项的列表框，选项为指定数组的所有元素
JList(Vector<?> listData)------------------------创建一个包含选项的选择框，选项为指定数组的所有元素
```
实例：
```
public class JListDemo extends JFrame {
	private JList list;
	public JListDemo() {
		super();
		getContentPane().setLayout(null);
		setBounds(100, 100, 266, 182);
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		final JPanel panel=new JPanel();
		panel.setLayout(null);
		panel.setBounds(0, 0, 262, 151);
		getContentPane().add(panel);
		final JLabel label=new JLabel();//定义标签
		label.setText("爱好");
		label.setBounds(44, 30, 39, 18);
		panel.add(label);
		final JScrollPane scrollPane=new JScrollPane();//滚动面板
		scrollPane.setBounds(92, 28, 100, 105);
		panel.add(scrollPane);
		String[] like={"看电影","跑步","听音乐","读书","打游戏","健身","聊天"};
		list=new JList(like);//将数组添加到组件中
		scrollPane.setViewportView(list);//将列表添加到滚动面板
	}
	public static void main(String[] args) {
		JListDemo frame=new JListDemo();
		frame.setVisible(true);
	}
}
```
![图片](img/javause/16.png)


JComboBox类构造方法:
```
JComboBox()--------------------------------------创建一个不包含任何选项的选择框
JComboBox(Object[] items)------------------------创建一个包含选项的选择框，选择为指定数组中的所有元素
JComboBox(Vector<?> items)-----------------------创建一个包含选项的选择框，选项为指定向量中的所有元素
JComboBox(ComboBoxModel aModel)------------------创建一个JComboBox，列表项目取自指定的ComboBoxModel
```
实例：
```
public class JComboBoxDemo extends JFrame {
	private JComboBox list;
	public JComboBoxDemo() {
		super();
		getContentPane().setLayout(null);
		setBounds(100, 100, 266, 240);
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		final JPanel panel=new JPanel();
		panel.setLayout(null);
		panel.setBounds(0, 0, 262, 151);
		getContentPane().add(panel);
		final JLabel label=new JLabel();//定义标签
		label.setText("爱好");
		label.setBounds(44, 30, 39, 18);
		panel.add(label);
		final JScrollPane scrollPane=new JScrollPane();//滚动面板
		scrollPane.setBounds(92, 28, 100, 30);
		panel.add(scrollPane);
		String[] like={"看电影","跑步","听音乐","读书","打游戏","健身","聊天"};
		list=new JComboBox(like);//将数组添加到组件中
		scrollPane.setViewportView(list);//将列表添加到滚动面板
	}
	public static void main(String[] args) {
		JComboBoxDemo frame=new JComboBoxDemo();
		frame.setVisible(true);
	}
}
```
![图片](img/javause/17.png)

5.练习
-----------------
(1)制作不规则按钮
不规则按钮可以使按钮只显示图片，需要用到JButton类方法setContentAreaFilled(Boolean bool)使按钮取消填充区域和setBorder(Border border)取消组件的边框。
```
setContentAreaFilled(Boolean bool)---------bool为ture表示填充内容区域，false取消填充区域
setBorder(Border border)-------------------border表示为此组件呈现的边框，为null时取消组件的边框
```
实例：
```
class ComBoBoxDemo extends JFrame {
	private JComboBox comboBox;
	public ComBoBoxDemo(){
		super();
		getContentPane().setLayout(null);//设置容器
		setBounds(100,100,182,144);
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		final JPanel panel=new JPanel();
		panel.setLayout(null);
		panel.setBounds(0,0,176,164);
		getContentPane().add(panel);
		URL url=getClass().getResource("1.png");//1.png与类ComBoBoxDemo放一起
		ImageIcon icon=new ImageIcon(url);//根据图片地址定义ImageIcon对象
		final JButton button=new JButton();
		button.setIcon(icon);//设置按钮显示图片
		button.setBounds(61, 10, 46, 46);
		button.setContentAreaFilled(false);//设置按钮没有填充效果
		button.setBorder(null);//设置按钮不显示边框
		panel.add(button);
		final JLabel msg=new JLabel();
		msg.setText("定义不规则按钮");
		msg.setBounds(37, 77, 91, 18);
		panel.add(msg);
	}
	public static void main(String[] args) {
		ComBoBoxDemo frame=new ComBoBoxDemo();
		frame.setVisible(true);
	}
}
```
![图片](img/javause/18.png)

(2)设置关于信息窗体
```
public class Demo extends JFrame{
	public Demo(){
		super();
		getContentPane().setLayout(null);
		setTitle("设置信息窗体");
		setBounds(100, 100, 346, 178);
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		final JPanel panel=new JPanel();
		panel.setLayout(null);//设置面板布局null
		panel.setBounds(0, 0, 338, 144);
		getContentPane().add(panel);
		final JLabel label=new JLabel();//标签控件
		label.setFont(new Font("华文楷体", Font.PLAIN, 42));
		label.setText("MR");
		label.setBounds(26, 41, 65, 59);
		panel.add(label);
		final JLabel label2=new JLabel();
		label2.setText("企业进销系统");
		label2.setBounds(10, 106, 98, 18);
		panel.add(label2);
		final JLabel name=new JLabel();
		name.setText("科技企业系统");
		name.setBounds(140, 21, 156, 18);
		panel.add(name);
		final JLabel number=new JLabel();
		number.setText("版本1.1");
		number.setBounds(140, 47, 135, 18);
		label.add(number);
		final JLabel flat=new JLabel();
		flat.setText("适用于任何平台");
		flat.setBounds(140, 71, 135, 18);
		panel.add(flat);
		final JLabel copyright=new JLabel();
		copyright.setText("版权所有:");
		copyright.setBounds(140, 106, 66, 18);
		panel.add(copyright);
		final JLabel company=new JLabel();
		company.setText("科技有限公司");
		company.setBounds(209, 106, 119, 18);
		panel.add(company);
	}
	
	public static void main(String[] args) {
		Demo demo=new Demo();
		demo.setVisible(true);
	}

}
```
![图片](img/javause/19.png)




第八章 多线程技术
======================
1.多线程介绍
---------------
程序启动就自动产生一个线程，主函数在这个线程上运行，当不在有多的线程产生，程序就是单线程，否则多线程
程序：计算机指令集合，以文件形式储存在磁盘上
进程：一个运行的程序，每个进程都有其独立的内存空间和系统资源
线程：进程内部的任务，线程是进程的实体一个进程可以拥有多个线程

线程生命周期：创建，可执行，非可执行，消亡
实例化一个线程并执行start()后线程进入“可执行”状态，同一时间只有一个线程在执行。
启用start()方法后，进入可执行状态，执行用户覆盖的run（）方法，但并不是一直执行到run（）结束，只是加入应用程序执行安排的队列中，可能正在等待取得CPU时间
当线程离开可执行状态下的队列时，线程进入非可执行状态，可以使用Thread类的wait()和sleep()方法进入非可执行状态
run()方法执行完毕后，线程自动消亡

2.实现多线程
---------------
创建线程(必须实现Runnable接口)的两种方法：继承Thread类(已经实现Runnable接口)和实现Runnable接口
(1)继承Thread类
语法：
```
//创建
public class 类名 extends Thread{
	public void run(){
		执行代码;
	}
}

//启动线程
public void start()
```
实例:
```
public class ThreadDemo extends Thread {
	private String name="name";
	public ThreadDemo(String name){
		this.name=name;
	}
	public void run() {
		while(true){
			System.out.println(name+"");
			try{
				Thread.sleep((int)Math.random()*1000);
			}catch(Exception e){
				e.printStackTrace();
			}
		}
	}
	public static void main(String[] args) {
		Thread a1=new ThreadDemo("线程1");
		Thread a2=new ThreadDemo("\t线程2");
		a1.start();
		a2.start();
	}
}
```
运行效果:
```
...
线程1
	线程2
线程1
	线程2
线程1
	线程2
线程1
线程1
	线程2
...
```
(2)实现Runnable接口
如果继承Thread类,会导致无法继承其他类------因为单继承
使用Runnable接口可以实现继承其他类的同时创建线程
语法:
```
public class Simple implements Runnable{
	Simple simple=new Simple();//实例化Simple对象
	Thread thread=new Thread(simple);//实例化Thread对象
	thread.start();//启动线程
}
```
实例程序：实现标签的大小变化
```
public class SimpleThread extends JFrame implements Runnable {
	JLabel jlabel=new JLabel();
	public SimpleThread(){
		super();
		getContentPane().setLayout(null);//窗体布局
		setBounds(100,100,700,700);
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);//窗口关闭状态
		URL url=getClass().getResource("2.jpeg");
		ImageIcon icon=new ImageIcon(url);
		Thread thread=new Thread(this);
		thread.start();
//		jlabel=new JLabel(); //不能放这里，要放外面 否则不是一个label
		jlabel.setBounds(40,10,640,640);
		jlabel.setIcon(icon);
		getContentPane().add(jlabel);
	}
	public void run() {
		while(true){
			for (int i = 10; i <= 640; i++) {
				jlabel.setBounds(40,10,i,i);
				try{
					Thread.sleep(50);
				}catch(Exception e){
					e.printStackTrace();
				}
				if(100==i){
					for (int j = 640; j >= 0; j--) {
						jlabel.setBounds(40,10,j,j);
						try{
							Thread.sleep(50);
						}catch(Exception e){
							e.printStackTrace();
						}
					}
				}
			}
		}
	}

	public static void main(String[] args) {
		SimpleThread frame=new SimpleThread();
		frame.setVisible(true);
	}
}
```
运行结果:
图片由小变大到一定程度再全屏由大变小
![图片](img/javause/20.png)


3.线程控制
-----------------------
(1)启动
调用start()方法启动线程run()方法不同于一般调用方法，调用一般方法必须等一般方法执行完毕才能返回，而start()方法启动run()方法后就返回继续调用start()方法后面的语句，此时可能run()方法还在执行，从而形成多线程
(2)休眠
线程的休眠是指线程的暂停，通过调用sleep()可以实现，休眠单位为毫秒
(3)停止
JDK1.1开始就取消了stop()方法，因为stop()方法会造成系统进入不安全状态，提倡在run()方法中使用布尔型标记控制循环停止。
eg:
```
public class 类名 implements Runnable{
	private continue isContinue=false;
	public void run(){
		while(true){
			if(!isContinue)
				break;
		}
	}
}
```
(4)优先级
每个线程都有优先级，优先级高的线程比优先级低的线程获得更多的执行时间
优先级范围1~10，默认为5
使用Thread类中的setPriority()方法设定优先级，但是必须1~10，否则异常
优先级高的线程会提前执行，执行完毕才会轮到优先级低的线程，优先级相同的的线程常用轮流执行方式
例：
本领运行出来应该是线程1先运行完再线程2-------------------但是我运行出来是随机的
```
public class Priority extends Thread {
		public void run() {
			for (int i = 1; i <=5 ; i++) {
				System.out.println(getName()+":"+i);
			}
		}
	public static void main(String[] args) {
		Priority p1=new Priority();
		Priority p2=new Priority();
		p1.setName("线程1");
		p2.setName("线程2");
		p1.setPriority(MAX_PRIORITY);//最高优先级10
		p2.setPriority(MIN_PRIORITY);//最低优先级1
		p1.start();
		p2.start();
	}
}
```

4.练习
-------
(1)会游泳的鱼
```
public class FishFrame extends JFrame implements Runnable {
	JPanel panel=new JPanel();//JPanel面板
	JLabel label=new JLabel();
	public FishFrame(){
		super();
		getContentPane().setLayout(null);//设置窗体绝对布局
		setBounds(100, 100, 345, 193);
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		panel.setLayout(null);
		panel.setBounds(0, 0, 337, 159);
		getContentPane().add(panel);
		URL url=getClass().getResource("fish.jpg");
		ImageIcon imageIcon=new ImageIcon(url);
		label.setIcon(imageIcon);//设置标签显示图片
//		label.setBounds(271,47,80,42);
		label.setBounds(0,0,80,42);
		panel.add(label);
		Thread thread=new Thread(this);//创建线程
		thread.start();
	}
	public void run() {
		while(true){
			int lx=label.getX()+1;//提供标签控件坐标地址
			if(label.getX()<271){
				label.setLocation(lx, label.getY());//设置标签显示位置
			}else{//如果小雨游到窗体边缘
				label.setBounds(0, 0, 80, 42);//重新定义标签位置
			}
			try {
				Thread.sleep(30);
			} catch (InterruptedException e) {
				e.printStackTrace();
			}
		}
	}

	public static void main(String[] args) {
		FishFrame fishFrame=new FishFrame();
		fishFrame.setVisible(true);
	}

}

```
小鱼从左到右移动，到最右边再重新到左边开始
![图片](img/javause/21.png)


(2)控件的曲线运动
```
public class CircleSport extends JFrame implements Runnable {
	private int angle;//起始角度
	private int moveAngle;//每次移动的角度
	private int len;//圆周半径
	private int cx,cy;//圆周中心坐标
	private JLabel label;
	public CircleSport() {
		super();
		getContentPane().setBackground(Color.WHITE);//白色背景
		getContentPane().setLayout(null);
		setBounds(100, 100, 500, 400);
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		cx=200;
		cy=146;
		ImageIcon icon=new ImageIcon(getClass().getResource("bee.jpg"));
		label=new JLabel(icon);
		label.setBounds(200, 146, icon.getIconWidth(), icon.getIconHeight());//设置标签组件位置和大小
		getContentPane().add(label);
		angle=90;//起始角度
		moveAngle=1;//初始化移动角度
		len=120;//初始化圆周半径
	}
	public void run() {
		int x,y;//下一个移动目标
		while(true){
			//计算下一个坐标
			x=(int) (len*Math.sin(Math.toRadians(angle)));
			y=(int) (len*Math.cos(Math.toRadians(angle)));
			label.setLocation(cx-x, cy+y);//设置标签坐标
			angle=angle+moveAngle;
			try {
				Thread.sleep(10);
			} catch (InterruptedException e) {
				e.printStackTrace();
			}
		}
	}

	public static void main(String[] args) {
		CircleSport frame=new CircleSport();
		frame.setVisible(true);
		new Thread(frame).start();//启动
	}
}
```
小蜜蜂转圈运动
![图片](img/javause/22.png)




第九章 JDBC技术
====================
数据库系统由数据库、数据库管理系统(DBMS)、应用系统、数据库管理员构成
JDBC技术是连接数据库与应用程序的纽带，可以实现向数据库插入、修改、查询、删除操作。
数据库分为层次型、网状型、面向对象型、关系型。
JDBC依赖于关系模型，JDBC不能直接访问数据库，必须依赖于数据库厂商提供的JDBC驱动程序，JDBC完成三步工作:
(1)与数据库建立连接
(2)向数据库发送SQL语句
(3)处理从数据库返回的结果

1.JBDC不可缺少的接口与类
-----------------------
位于包java.sql中
(1)管理数据库驱动类DriverManager
DriverManager类管理JDBC驱动程序的基本服务，作用于用户和驱动程序之间，负责跟踪可用的驱动程序，并在数据库和驱动程序之间建立连接。
DriverManager类常用方法:
```
getConnection(String url,String user,String passWd)-------指定三个入口参数，依次为连接数据库的URL、用户名、密码，来获取与数据库的连接
setLoginTimeout()-----------------------------------------获取驱动程序试图登录到某一数据库可以等待的最长时间(秒)
println(String message)-----------------------------------将一条消息打印到当前JDBC日志流中
```

(2)数据库连接接口Connection
Connection接口代表与特定数据库的连接，在连接的上下文中可以执行SQL语句并返回结果，可以通过getMetaData()方法获得由数据库提供的相关信息。Connection实例就像在应用程序与数据库之间开通的一条渠道。
常用方法：
```
createStatement()--------------------------------------创建并返回一个Statement实例，通常在执行无参SQL语句时创建该实例
prepareStatement()-------------------------------------创建并返回一个PrepareStatement实例，通常在执行包含参数的Sql语句时创建该实例，并对SQL语句进行了预编译处理
prepareCall()------------------------------------------创建并返回一个CallableStatement实例，通常在调用数据库储存过程时创建该实例
setAutoCommit()----------------------------------------设置当前Connection实例的自动提交模式。默认为true，即自动将更改同步到数据库中，如果设为false,需要通过执行commit()或rollback()方法手动将更改同步到数据库中
getAutoCommit()----------------------------------------查看当前Connection实例是否处于自动提交模式，如果是返回true，否则返回false
setSavepoint()-----------------------------------------在当前事物中创建并返回一个Savepoint实例，前提条件是当前的Connection实例不能处于自动提交模式，否则将抛出异常
releaseSavepoint()-------------------------------------从当前事物中移除指定的Savepoint实例
setReadOnly()------------------------------------------设置当前Connection实例的读取模式，默认为非只读模式，不能在事物当中执行该操作，否则将抛出异常，true-只读，false-关闭只读。
isReadOnly()-------------------------------------------查看当前Connection实例是否为只读模式
isClosed()---------------------------------------------查看当前Connection实例是否被关闭
commit()-----------------------------------------------将从上一次提交或者回滚以来进行的所有更改同步到数据库，并释放Connection实例当前拥有的所有数据库锁定
rollback()---------------------------------------------取消当前事物中的所有更改，并释放当前Connection实例拥有的所有数据库锁定，只能在非自动提交模式下使用
close()-----------------------------------------------立即释放Connection实例占用的数据库和JDBC资源，关闭数据库连接
```
(3)发送SQL语句接口Statement
Statement接口用来执行静态的SQL语句，并返回执行结果。 
对于insert、update、delete语句调用executeUpdate(String sql)方法
select语句调用executeQuery(String sql)方法，并返回一个永远不能为null的ResultSet实例
Statement常用方法:
```
executeQuery(String sql)------------------------执行指定的静态SELECT语句，并返回一个永远不能为null的ResultSet实例
executeUpdate(String sql)-----------------------执行指定的静态INSERT、UPDATE、DELETE语句，并返回一个int型数值，为同步更新记录的条数
clearBatch()------------------------------------清除位于Batch中的所有SQL语句，如果驱动程序不支持批量处理则抛出异常
addBatch(String sql)----------------------------将指定的sql命令添加到Batch中，String型入口参数通常为静态的INSERT或者UPDATE语句，驱动程序不支持批量处理则抛出异常
executeBatch()----------------------------------执行Batch中的所有SQL语句，全部执行成功则返回更新计数组成的数组，数组元素的排序与SQL语句的添加顺序对应，数组元素情况：大于等于0的数->SQL语句执行成功返回更新计数，-2->执行成功但未得到受影响的行数，-3->SQL语句执行失败
close()-----------------------------------------立即释放Statement实例占用的数据库和JDBC资源
```
(4)可执行动态SQL的接口PreparedStatement
PreparedStatement接口继承并拓展了Statement接口，用来执行动态的SQL语句(包含参数的SQL语句)，可以使用Connection类的preparedStatement()方法来获取PreparedStatement实例。
常用方法:
```
executeQuery(String sql)------------------------执行指定的静态SELECT语句，并返回一个永远不能为null的ResultSet实例
executeUpdate(String sql)-----------------------执行指定的静态INSERT、UPDATE、DELETE语句，并返回一个int型数值，为同步更新记录的条数
setInt(int i,int x)-----------------------------为参数设置int型值，对应参数SQL类型为INTEGER
setLong(int i,long x)---------------------------为参数设置long型值，对应参数SQL类型为BIGINT
setFloat(int i,float x)-------------------------为参数设置float型值，对应参数SQL类型为FLOAT
setDouble(int i,double x)-----------------------为参数设置double型值，对应参数SQL类型为DOUBLE
setString(int i,String x)-----------------------为参数设置String型值，对应参数SQL类型为VARCHAR或LONGVARCHAR
setBoolean(int i,boolean x)---------------------为参数设置boolean型值，对应参数SQL类型为BIT
setDate(int i, Date x)--------------------------为参数设置java.aql.Date型值，对应参数SQL类型为BATE
setObject(int i,Object x)-----------------------用来设置各种类型的参数，JDBC规范定义了从Object类型到SQL类型的标准映射关系，向数据库发送时将被转换为对应的SQL类型
setNull(int i,int sqlType)----------------------将指定参数设置为SQL中的NULL，该方法的第二个入口参数用来设置参数的SQL类型,并且必须设置，具体值从java.sql.Types类中定义的静态常量中选择
clearParameters()-------------------------------清除当前所有参数的值
```
(5)查询结果集接口ResultSet
ResultSet接口类似于一张数据表，用来暂时存放从数据库查询操作所获得的结果集。
常用方法:
```
getInt()-------------------------------以int形式获取此ResultSet对象的当前行中的指定列值，列值为null则返回0
getFloat()-----------------------------以float形式获取此ResultSet对象的当前行中的指定列值，列值为null则返回0
getDate()------------------------------以Date形式获取此ResultSet对象的当前行中的指定列值，列值为null则返回0
getBoolean()---------------------------以boolean形式获取此ResultSet对象的当前行中的指定列值，列值为null则返回0
getString()----------------------------以String形式获取ResultSet对象的当前行的指定列值，列值为NULL则返回null
getObject()----------------------------以Object形式获取此ResultSet对象的当前行中的指定列值，列值为null则返回null
first()--------------------------------将指针移到当前记录的第一行
last()---------------------------------将指针移到当前记录的最后一行
next()---------------------------------将指针向下移一行
beforeFirst()--------------------------将指针移动到集合的开头(第一行位置)
afterLast()----------------------------将指针移动到集合的尾部(最后一行位置)
absolute(int index)--------------------将指针移动到ResultSet给定编号的行
isFrist()------------------------------判断指针是否位于ResultSet集合的第一行
isLast()-------------------------------判断指针是否位于ResultSet集合的最后一行
updateInt()----------------------------用int值更新指定列
updateFloat()--------------------------用float值更新指定列
updateLong()---------------------------用long值更新指定列
updateString()-------------------------用String值更新指定列
updateObject()-------------------------用Object值更新指定列
updateNull()---------------------------将指定的列值修改为NULL
```

2.数据库操作
---------------
2.1 执行步骤
加载数据库驱动，创建数据库连接，执行SQL语句，获取查询结果集，关闭连接
(1)加载数据库驱动
数据库驱动程序只需在第一次访问数据库时加载一次，然后每次访问数据库时创建一个Connection实例来获取数据库连接，之后向数据库SQL语句来操作数据，最后完成数据库操作释放连接。
语法：
```
Class.forName(String driverManager)//加载成功则将驱动类注册给DriverManager,加载失败抛出ClassNotFoundException异常
eg:加载SQL Server2000数据库驱动jtds
try{
	Class.forName("net.sourceforge.jtds.jdbc.Driver");
	}catch(ClassNotFoundException e){
		e.printStackTrace();
	}
```
备注：通常将负责加载驱动的代码放static中--------------避免重复加载驱动程序

(2)创建数据库连接
数据库管理类DriverManager负责建立与管理数据库连接，通过DriverManager类的静态方法getConnection(String url,String user,String passwd)可以建立数据库连接
语法:
```
Connection conn=DriverManager.getConnection(String url,String user,String passwd)
url：指定连接数据库的url,user:用户，passwd:密码
```

注意事项：
a.java应用程序连接数据库需要保证数据库是启动的，即：net start mysql
b.不同数据库url,驱动程序不一样，需要加载。mysql如下：
```
Class.forName("com.mysql.jdbc.Driver");//加载驱动程序
String url="jdbc:mysql://127.0.0.1:3306/test";
```
c.驱动程序加载方法：java项目下新建一个文件lib,将驱动包mysql-connector-java-5.0.8.jar放到lib目录下，点击包右键->Build Path->Add to Build Path
实例：
```
public class GetConn {
	Connection conn=null;
	static{
		try{
			Class.forName("com.mysql.jdbc.Driver");//加载驱动程序
			System.out.println("数据库驱动加载成功");
		}catch(ClassNotFoundException e){
			e.printStackTrace();
		}
	}
	public Connection getConn(){
		String url="jdbc:mysql://127.0.0.1:3306/test";//3306：端口号 test：数据库名称
		String userName="root";
		String passwd="";
		try{
			conn=DriverManager.getConnection(url,userName,passwd);
			if(conn != null){
				System.out.println("数据库连接成功!");
			}
		}catch(SQLException e){
			e.printStackTrace();
		}
		return conn;
	}
	
	public static void main(String[] args) {
			GetConn getConn=new GetConn();
			Connection conn=getConn.getConn();
	}

}
运行结果：
数据库驱动加载成功
数据库连接成功!
```

(3)执行SQL语句
由Connection接口的createStatement()方法获取Statement对象
```
Statement statement=con.createStatement();
```
Statement接口只能执行静态SQL语句，要执行SQL动态语句需要使用PreparedStatement实例。
插入、删除、修改可以通过Statement接口的executeUpdate()方法，查询数据可以通过Statement接口的executeQuery()方法。

(4)获取查询结果集
通过Statement接口的executeUpdate()方法实现插入、删除、修改返回int数据（影响数据库记录的条数），查询数据Statement接口的executeQuery()方法返回的是ResultSet型的结果集，其中不仅包括所有满足查询条件的记录，还包含相应数据表的相关信息如每一列的名称、类型和列的数量等。
如：从tb表中查询所有数据记录，并通过ResultSet实例的getXXX()方法通过指定列的序列号或者名称获取数据。
```
ResultSet res=statement.executeQuery("select * from tb");//从tb表中查询所有数据记录
//通过ResultSet实例的getXXX()方法通过指定列的序列号或者名称获取数据
while(res.next()){
	int id=res.getInt(1);//获取第一列数据
	String name=res.getString("name");//获取名称为name的列的数据
	String salary=res.getString(3);//获取第三列数据
}
```
数据表如下：
id   name     salary
1    liming   3000
2    wangmei  4000

(5)关闭连接
建立Connection、Statement、ResultSet实例时，占用一定的数据库和JDBC资源，每次访问结束访问数据库后应该销毁这些实例释放资源，建议如下顺序：
```
resultSet.close();
statement.close();
connection.close();
```
注：通过DriverManager类的getconnection()方法得到的Connection实例在close()时会同时关闭Statement实例和ResultSet实例。但是通常情况常用数据库连接池，调用Connection实例在close()时Connection实例可能并没有被释放，而是被放到了连接池中，又被其他连接调用，这种情况下不手动关闭Statement实例和ResultSet实例将导致他们越来越多，影响计算机和数据库速度甚至导致软件或者系统瘫痪。

2.2 数据库的增删改查
(1)添加数据
SQL的insert语法：
```
INSERT INTO 表名[(字段名1，字段名2...)] VALUES(属性值1，属性值2...)
如：
insert into tb values(1,'liming','3000');
```
通过Statement接口的executeUpdate()执行插入操作
实例：
```
public static void main(String[] args) {
		GetConn getConn=new GetConn();
		Connection conn=getConn.getConn();
		String createtb="CREATE TABLE IF NOT EXISTS tb(id SMALLINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,name VARCHAR(20) NOT NULL,salary VARCHAR(20) NOT NULL)";//建立tb表  id,name,salary
		String insert1="INSERT tb(name,salary) VALUES('wangmei','4000')";//插入数据---运行一次插入一次
		try {
			Statement statement=conn.createStatement();
			statement.executeUpdate(createtb);
			statement.executeUpdate(insert1);
		} catch (SQLException e) {
			e.printStackTrace();
		}
}
```
(2)删除数据
delete语法：
```
DELETE FROM 数据表名 where 条件表达式
eg:delete from td where id = 1;
实例：
String sql="delete from tb where id = 1";
statement.executeUpdate(sql);
```
注意：如果delete没有通过where语句指定删除记录的添加，则会删除数据表中的全部记录
delete删除全部记录但保留表，"DROP TABLE"删除整张表

(3)修改数据
update语法：
```
UPDATE 数据表名 SET 字段名 = 新的字段值 WHERE 条件表达式
eg:update tb set name='zhanghua' where id=2;
实例：
String sql="update tb set name='zhanghua' where id=2";
statement.executeUpdate(sql);
```

(4)查询数据
select语法：
```
SELECT 所选字段列表 FROM 数据表名 WHERE 条件表达式 GROUP BY 字段名 HAVING 条件表达式 (指定分组的条件) ORDER BY 字段名[ASC|DESC]
eg:select name,salary from tb where id=2 order by salary;
```
A.顺序查询
顺序查询指应用select语句将数据表中满足条件的记录检索下来
实例：
```
String sql="select * from tb where id != 1";
ResultSet rest=statement.executeQuery(sql);
while(rest.next()){
	int id=rest.getInt(1);
	String name=rest.getString("name");
	String salary=rest.getString(3);
}
```

B.模糊查询
SQL通过LINK操作符进行模糊查询，可以使用"%"字符来代替0个或者多个字符，使用下划线"_"来代替一个字符。
实例：
```
select * from tb where name like 'li%';
eg:
String sql="select * from tb where name like 'li%'";
ResultSet rest=statement.executeQuery(sql);
while(rest.next){
	int id=rest.getInt(1);
	String name=rest.getString("name");
	String salary=rest.getString(3);
}
```
增删改查实例：
```
public class GetConn {
	Connection conn=null;
	static{
		try{
			Class.forName("com.mysql.jdbc.Driver");//加载驱动程序
			System.out.println("数据库驱动加载成功");
		}catch(ClassNotFoundException e){
			e.printStackTrace();
		}
	}
	public Connection getConn(){
		String url="jdbc:mysql://127.0.0.1:3306/test";//3306：端口号 test：数据库名称
		String userName="root";
		String passwd="";
		try{
			conn=DriverManager.getConnection(url,userName,passwd);
			if(conn != null){
				System.out.println("数据库连接成功!");
			}
		}catch(SQLException e){
			e.printStackTrace();
		}
		return conn;
	}
	
	public static void main(String[] args) {
			GetConn getConn=new GetConn();
			Connection conn=getConn.getConn();
			String createtb="CREATE TABLE IF NOT EXISTS tb(id SMALLINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,name VARCHAR(20) NOT NULL,salary VARCHAR(20) NOT NULL)";//建立tb表  id,name,salary
			String insert1="INSERT tb(name,salary) VALUES('wangmei','4000')";//插入数据---运行一次插入一次
			String delete1="delete from tb where id = 1";
			String update1="update tb set name='zhanghua' where id=2";
			String find1="select * from tb where id != 1";
			try {
				Statement statement=conn.createStatement();
				statement.executeUpdate(createtb);
				statement.executeUpdate(insert1);//增
				statement.executeUpdate(delete1);//删
				statement.executeUpdate(update1);//该
				ResultSet rest=statement.executeQuery(find1);
				while(rest.next()){
					int id=rest.getInt(1);
					String name=rest.getString("name");
					String salary=rest.getString(3);
					System.out.println("id="+id+" "+"name="+name+" "+"salary="+salary);
				}
			} catch (SQLException e) {
				e.printStackTrace();
			}
	}

}
输出结果：
id=2 name=zhanghua salary=3000
id=3 name=wangmei salary=4000
id=4 name=wangmei salary=4000
```
执行前：

|  id  |  name | salary |
| -----| ------| -------|
| 1    |liming | 3000   |
| 2    |liming | 3000   |
| 3    |wangmei| 4000   |

执行后：

|  id  |  name  | salary |
| -----| -------| -------|
| 2    |zhanghua| 3000   |
| 3    |wangmei | 4000   |
| 4    |wangmei | 4000   |


3.使用预处理语句
---------------
如果用户名和密码查询信息，name为"'apple' or 'a'='a'"，passwd为"'12' or 1=1"则SQL语句为
```
String sql="select * from tb where name='apple' or 'a'='a' and passwd='12' or 1=1";
```
上面语句虽然正确，可以访问数据库，但是不能保证数据的安全性，可以使用预处理解决这个问题。
预处理语句的第二个优点是可以提高数据查询速度。因为向数据库发送sql语句需要数据库中的sql解释器把sql语句生成底层的内部命令，然后再执行完成相关操作，不断向提交sql语句会增加数据库解释器的负担，影响执行速度，而预处理语句是对SQL语句编译预处理生成底层数据库命令，封装在PreparedStatement对象中，通过调用该对象的方法执行底层数据库命令，这样应用程序针对连接的数据库将SQL语句解释为数据库底层内部命令，然后让数据执行这个命令，减轻数据库负担，提高访问数据库的速度。
对SQL语句预处理时，可以使用通配符"?"来代替任何的字段值。eg:
```
String sql="select * from tb where id=?";
```
执行预处理语句前，必须调用相应的方法来设置通配符所代表的值如：
```
PreparedStatement pstatement=connection.preparedStatement(sql);
pstatement.setInt(1,1);
```
设置完通配符值后调用PreparedStatement实例的executeQuery()方法执行预处理语句

实例：通过预处理方法实现添加信息
```
public class GetConn {
	Connection conn=null;
	static{
		try{
			Class.forName("com.mysql.jdbc.Driver");//加载驱动程序
			System.out.println("数据库驱动加载成功");
		}catch(ClassNotFoundException e){
			e.printStackTrace();
		}
	}
	public Connection getConn(){
		String url="jdbc:mysql://127.0.0.1:3306/test";//3306：端口号 test：数据库名称
		String userName="root";
		String passwd="";
		try{
			conn=DriverManager.getConnection(url,userName,passwd);
			if(conn != null){
				System.out.println("数据库连接成功!");
			}
		}catch(SQLException e){
			e.printStackTrace();
		}
		return conn;
	}
	
	public static void main(String[] args) {
			GetConn getConn=new GetConn();
			Connection conn=getConn.getConn();
			String sql="insert into tb values(?,?,?)";	
			String find1="select * from tb";
			try {
				PreparedStatement preparedStatement=conn.prepareStatement(sql);//获取PreparedStatement实例
				preparedStatement.setInt(1, 1);//第1个值id设置1
				preparedStatement.setString(2, "lihua");//第2个值名字设置lihua
				preparedStatement.setString(3, "5000");//第3个值工资设置为5000
				preparedStatement.executeUpdate();
			
				Statement statement=conn.createStatement();
				ResultSet rest=statement.executeQuery(find1);
				while(rest.next()){
					int id=rest.getInt(1);
					String name=rest.getString("name");
					String salary=rest.getString(3);
					System.out.println("id="+id+" "+"name="+name+" "+"salary="+salary);
				}
			} catch (SQLException e) {
				e.printStackTrace();
			}
	}

}
```
运行结果：
数据库驱动加载成功
数据库连接成功!
id=1 name=lihua salary=5000
id=2 name=zhanghua salary=3000
id=3 name=wangmei salary=4000
id=4 name=wangmei salary=4000
添加前：

|  id  |  name  | salary |
| -----| -------| -------|
| 2    |zhanghua| 3000   |
| 3    |wangmei | 4000   |
| 4    |wangmei | 4000   |

添加后:

|  id  |  name  | salary |
| -----| -------| -------|
| 1    |lihua   | 5000   |
| 2    |zhanghua| 3000   |
| 3    |wangmei | 4000   |
| 4    |wangmei | 4000   |



4.练习
--------------
(1)将查询结果显示在窗体中
在原tb数据库下，查询id=2的用户显示在窗体中
```
public class User {
	private int id;
	private String name;
	private String salary;
	public int getId() {
		return id;
	}
	public void setId(int id) {
		this.id = id;
	}
	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}
	public String getSalary() {
		return salary;
	}
	public void setSalary(String salary) {
		this.salary = salary;
	}
}


public class JdbcUser {
	Connection conn=null;
	static{
		try{
			Class.forName("com.mysql.jdbc.Driver");//加载驱动程序
			System.out.println("数据库驱动加载成功");
		}catch(ClassNotFoundException e){
			e.printStackTrace();
		}
	}
	
	public Connection getConn(){
		String url="jdbc:mysql://127.0.0.1:3306/test";//3306：端口号 test：数据库名称
		String userName="root";
		String passwd="";
		try{
			conn=DriverManager.getConnection(url,userName,passwd);
			if(conn != null){
				System.out.println("数据库连接成功!");
			}
		}catch(SQLException e){
			e.printStackTrace();
		}
		return conn;
	}
	
	public User selectUser(int id){
			User user=null;
			JdbcUser jdbcUser=new JdbcUser();
			Connection conn=jdbcUser.getConn();
			String sql="select * from tb where id="+id;
			try {
				Statement statement=conn.createStatement();
				ResultSet rest=statement.executeQuery(sql);
				while(rest.next()){
					user=new User();
					user.setId(rest.getInt(1));
					user.setName(rest.getString("name"));
					user.setSalary(rest.getString(3));
					}
				}catch (SQLException e) {
				e.printStackTrace();
				}
			return user;
			}
}



public class ViewMessage extends JFrame {
	public ViewMessage(){
		super();
		getContentPane().setLayout(null);//设置容器显示绝对布局
		setBounds(100, 100, 309, 219);
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		JdbcUser jdbcUser=new JdbcUser();
		User user=jdbcUser.selectUser(2);//查询id=2的user
		
		final JPanel panel=new JPanel();
		panel.setLayout(null);
		panel.setBounds(0, 0, 301, 185);
		getContentPane().add(panel);//将面板添加到窗体中
		final JLabel namelabel=new JLabel();
		namelabel.setText("姓名");
		namelabel.setBounds(59, 37, 39, 24);
		panel.add(namelabel);//标签添加到面板
		JTextField nametextTield=new JTextField();//姓名设置为文本框显示内容
		nametextTield.setText(user.getName());
		nametextTield.setBounds(104, 38, 132, 22);
		panel.add(nametextTield);
		final JLabel salarylabel=new JLabel();
		salarylabel.setText("姓名");
		salarylabel.setBounds(59, 67, 39, 24);
		panel.add(salarylabel);//标签添加到面板
		JTextField salarytextTield=new JTextField();//姓名设置为文本框显示内容
		salarytextTield.setText(user.getSalary());
		salarytextTield.setBounds(104, 68, 132, 22);
		panel.add(salarytextTield);
	}
	public static void main(String[] args) {
		ViewMessage viewMessage=new ViewMessage();
		viewMessage.setVisible(true);
	}

}
```
效果如下：
![图片](img/javause/23.png)

(2)修改员工工资信息
将zhanghua的工资增加3000元
```
public class GetConn {
	Connection conn=null;
	static{
		try{
			Class.forName("com.mysql.jdbc.Driver");//加载驱动程序
			System.out.println("数据库驱动加载成功");
		}catch(ClassNotFoundException e){
			e.printStackTrace();
		}
	}
	public Connection getConn(){
		String url="jdbc:mysql://127.0.0.1:3306/test";//3306：端口号 test：数据库名称
		String userName="root";
		String passwd="";
		try{
			conn=DriverManager.getConnection(url,userName,passwd);
			if(conn != null){
				System.out.println("数据库连接成功!");
			}
		}catch(SQLException e){
			e.printStackTrace();
		}
		return conn;
	}
	
	public static void main(String[] args) {
			GetConn getConn=new GetConn();
			Connection conn=getConn.getConn();
			String sql="update tb set salary=salary+3000 where name='zhanghua'";	///////////
			try {
				Statement statement=conn.createStatement();
				statement.executeUpdate(sql);
				} catch (SQLException e) {
				e.printStackTrace();
			}
	}
}
```
执行前:

|  id  |  name  | salary |
| -----| -------| -------|
| 1    |lihua   | 5000   |
| 2    |zhanghua| 3000   |
| 3    |wangmei | 4000   |
| 4    |wangmei | 4000   |

执行后:

|  id  |  name  | salary |
| -----| -------| -------|
| 1    |lihua   | 5000   |
| 2    |zhanghua| 6000   |
| 3    |wangmei | 4000   |
| 4    |wangmei | 4000   |



第十章 GUI事件处理机制
=======================
GUI控件与用户交互需要为控件添加事件，如：移动鼠标、键盘按键、单击按钮等。

1.GUI事件
------------
事件:用户对控件的一个操作，如单击按钮、关闭窗体等
事件源：发生事件的控件
事件处理器：负责处理事件的方法
AWT事件类：
```
ActionEvent------------------------动作事件，用户单击按钮、选择菜单、列表等操作时产生该事件
AdjustmentEvent--------------------调整事件，在滚动条变化时产生该事件
ComponentEvent---------------------控件事件，在控件隐藏、显示、移动等操作中产生
ContainerEvent---------------------容器事件，在容器发生变化时产生该事件，如向容器添加移除事件
FocusEvent-------------------------焦点事件，当控件获得焦点与失去焦点时，触发该事件
HierarchyEvent---------------------层次事件，当控件级别改变时触发事件
InputMethodEvent-------------------输入法事件，输入法改变时触发事件
ItemEvent--------------------------选项事件，复选框、列表、下拉选择框等控件的数据改变时触发事件
KeyEvent---------------------------按键事件，按下键盘按钮或者释放键盘按钮时触发的事件
MouseEvent-------------------------鼠标事件，当改变鼠标状态时触发的事件，例如单击鼠标按键、鼠标按键的按下与抬起状态、鼠标进入离开控件等
MouseWheelEvent--------------------鼠标滚轮事件，当滚动鼠标滚轮时触发事件
PaintEvent-------------------------绘图事件，发生绘图事件时触发该事件
TextEvent--------------------------文本事件，当文本框和文本域控件的内容发生改变时触发事件
WindowEvent------------------------窗口事件，当窗体被打开、关闭、最大化、最小化、还原和激活时触发事件
```

事件监听器：
用于监听指定的事件类型，如ActionListener(单击事件ActionEvent的监听接口)、KeyListener(键盘监听器接口),必须实现该接口编写自己的监听器实现类来处理事件，监听器类收到事件后，将委托指定的方法来执行事件处理。
事件监听器接口会定义很多方法实现接口时需要实现。如键盘监听器KeyListener代码如下：
```
import java.util.EventListener;
public interface KeyListener extends EventListener{
	public void keyTyped(KeyEvent e);//键入某键时调用此方法
	public void keyPressed(KeyEvent e);//按下某键时执行方法
	public void keyReleased(KeyEvent e);//释放某键时调用方法
}
```

实现事件监听器如下：
```
public class KeyListener implements java.awt.event.KeyListener{
	public void keyTyped(KeyEvent e){}//键入某键时调用此方法
	public void keyPressed(KeyEvent e){}//按下某键时执行方法
	public void keyReleased(KeyEvent e){}//释放某键时调用方法
}
```

2.动作事件
------------
动作事件包括单击按钮、选择菜单项目等，Java中动作事件由ActionEvent类表示，与动作事件相对应的事件处理器接口为ActionLisenter接口，该接口只有一个方法actionPerformed()。
为按钮添加动作事件要如下两步：
(1)定义实现事件监听器的类
```
public class ActionDemo implements ActionLisenter{
	public void actionPerformed(ActionEvent e){
		//添加处理事件代码
	}
}
```
(2)向事件源注册监听者对象
```
button.addActionListener(ad);//ad为动作事件监听器接口对象，动作事件注册给按钮点击按钮就会出现相应的动作
```

实例：点击按钮实现窗体关闭
```
public class ActionEventDemo extends JFrame {
	public ActionEventDemo() {
		super();
		getContentPane().setLayout(null);
		setBounds(100, 100, 238, 124);
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		final JPanel panel=new JPanel();//面板
		panel.setLayout(null);
		panel.setBounds(0, 0, 232, 90);
		getContentPane().add(panel);//面板添加到窗体
		final JButton button=new JButton();
		button.addActionListener(new ActionListener() {//绑定按钮单击事件
			public void actionPerformed(ActionEvent e) {
				System.exit(0);////////关闭窗体
			}
		});
		button.setText("关闭按钮");
		button.setBounds(73, 27, 86, 28);
		panel.add(button);
	}
	public static void main(String[] args) {
		ActionEventDemo actionEventDemo=new ActionEventDemo();
		actionEventDemo.setVisible(true);
	}
}
```
运行结果：点击按钮“关闭”窗体关闭
![图片](img/javause/24.png)


3.窗体控制
---------------
窗体控制指发生窗口定义的WindowEvent窗口事件，窗口事件由WindowListener对象负责监听，可以使用addWindowListener()方法为窗口注册WindowListener对象，注册之后才可以接收窗口事件，当窗口状态(如最大化、最小化、图标化)改变时，由控件(比如窗体)生成此窗口事件，并由WindowListener对象进行处理。
WindowListener对象7个方法：

| 方法                                            | 描述                                                  |
| ------------------------------------------------| -----------------------------------------------------|
| void windowActivated(WindowEvent e)             | 当窗口由非活动窗口变为活动窗口时调用此方法                |
| void windowClosed(WindowEvent e)                | 当窗口的默认关闭模式设置为JFrame.DISPOSE_ON_CLOSE时调用  |                                  
| void windowClosing(WindowEvent e)               | 当窗口即将关闭（点击窗体关闭按钮时）时调用                |
| void windowDeactivated(WindowEvent e)           | 当窗口由活动状态变非活动状态时调用                       |
| void windowDeiconified(WindowEvent e)           | 当窗口从图标化状态变为正常状态时调用                     |
| void windowIconified(WindowEvent e)             | 当窗口从正常状态变为图标化状态时调用                     |
| void windowOpened(WindowEvent e)                | 当窗口打开时调用                                      |  

窗体事件执行过程：
(1)创建WindowListener对象
(2)调用addWindowListener()方法为窗口注册WindowListener对象作为监听器
(3)由外部操作触发，使窗口状态改变
(4)窗口状态改变后生成窗口事件
(5)执行WindowListener对象的方法完成窗口事件的处理

备注：WindowAdapter类实现了WindowListener接口，可以使用根据需要的方法使用该类方法

实例：窗口打开关闭时在控制台输出信息
```
public class UseWindowEventFrame extends JFrame {
	public UseWindowEventFrame() {
		super();
		addWindowListener(new WindowAdapter() {//为窗体添加窗口监听器，这里使用的匿名内部类实现窗口适配器创建
			public void windowOpened(WindowEvent e) {
				System.out.println("打开类窗体");
			}
			
			public void windowClosing(WindowEvent e) {
				System.out.println("窗体即将关闭");
			}
		});
		setTitle("窗口事件");
		setBounds(100, 100, 298, 190);
		setDefaultCloseOperation(JFrame.DISPOSE_ON_CLOSE);
	}
	public static void main(String[] args) {
		UseWindowEventFrame frame=new UseWindowEventFrame();
		frame.setVisible(true);
	}
}
```
运行控制台输出：
打开窗体时：
打开类窗体

关闭窗体时：
窗体即将关闭

![图片](img/javause/25.png)

4.鼠标控制
--------------
鼠标的移动、单击、拖动等操作可以实现交互效果如拖动窗体、单击按钮、选择文本框等。
鼠标事件由MouseListener对象监听，使用addMouseListener()方法为控件注册MouseListener对象之后才可以接收鼠标事件。
MouseListener接口提供了5个方法：

| 方法                          | 说明                           |
| ------------------------------| ------------------------------|
| mouseClicked(MouseEvent e)    | 处理鼠标单击事件的方法           |
| mouseEntered(MouseEvent e)    | 鼠标进入控件区域时执行的方法      |
| mouseExited(MouseEvent e)     | 鼠标离开控件区域时执行的方法      |
| mousePressed(MouseEvent e)    | 按下鼠标按键时执行的方法          |
| mouseReleased(MouseEvent e)   | 释放鼠标按键时执行的方法          |

MouseMotionListener接口的两个方法:

| 方法                          | 说明                           |
| ------------------------------| ------------------------------|
| mouseMoved(MouseEvent e)      | 处理鼠标移动事件的方法           |
| mouseDragged(MouseEvent e)    | 处理鼠标拖动事件的方法           |

以上两个鼠标监听器的方法都定义了MouseEvent类型的形参，MouseEvent类是鼠标事件类，可以通过此类的下面方法获取相应属性:

| 方法                          | 说明                                                            |
| ------------------------------| ---------------------------------------------------------------|
| getButton()                   | 返回更改了状态的鼠标按键(如果有)                                   |
| getClickCount()               | 返回与此事件关联的鼠标单击参数                                     |
| getLocationOnScreen()         | 返回鼠标相对于屏幕的绝对x,y坐标                                    |
| getPoint()                    | 返回事件相对于源控件的x,y坐标                                      |
| translatePoint(int x,int y)   | 通过将事件坐标加上指定的x(水平)和y(垂直)偏移量，将事件的坐标平移到新位置|

为控件添加鼠标事件步骤:
(1)创建MouseListenser对象
(2)调用addMouseListener()方法为控件注册MouseListenser对象作为监听器
(3)在控件上操作鼠标生成的鼠标事件
(4)执行MouseListenser对象的方法完成鼠标事件的处理

实例:添加鼠标事件跟踪鼠标的变化
```
public class UseMouseEventFrame extends JFrame {
	public UseMouseEventFrame() {
		super();
		setTitle("鼠标事件");
		getContentPane().setLayout(null);
		setBounds(100, 100, 325, 204);
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		final JLabel label=new JLabel();
		label.addMouseListener(new MouseAdapter() {//MouseAdapter()
			public void mouseClicked(MouseEvent e) {
				label.setText("在标签上单击鼠标");
			}
			public void mouseEntered(MouseEvent e) {
				label.setText("鼠标进入标签");
			}
			public void mouseExited(MouseEvent e) {
				label.setText("鼠标移出标签");
			}
			public void mousePressed(MouseEvent e) {
				label.setText("在标签上按下鼠标按键");
			}
			public void mouseReleased(MouseEvent e) {
				label.setText("在标签上释放鼠标按键");
			}
		});
		label.setOpaque(true);//将标签设置为不透明
		label.setBackground(Color.PINK);
		label.setText("显示鼠标事件的标签");//设置标签上的显示文本
		label.setBounds(70, 38, 171, 83);
		getContentPane().add(label);//标签加入窗体
	}
	public static void main(String[] args) {
		UseMouseEventFrame frame=new UseMouseEventFrame();
		frame.setVisible(true);
	}
}
```
部分效果如下:
![图片](img/javause/26.png)
![图片](img/javause/27.png)


5.键盘控制
-------------
键盘事件监听器由KeyListener接口定义，3个方法:

| 方法                          | 说明                           |
| ------------------------------| ------------------------------|
| keyPressed(KeyEvent e)        | 按下某个按键时调用              |
| keyReleased(KeyEvent e)       | 释放某个按键时调用              |
| keyTyped(KeyEvent e)          | 键入某个按键时调用              |

KeyEvent类中的方法：

| 方法                                       | 说明                                           |
| -------------------------------------------| ----------------------------------------------|
| char getKeyChar()                          | 返回与此事件中的键关联的字符                      |
| int getKeyCode()                           | 返回与此事件中的键关联的整数keyCode               |
| String getKeyModifiersText(int modifiers)  | 返回描述修改键的String,如"Shift"或者"Ctrl+Shift" |
| String getKeyText(int keyCode)             | 返回描述KeyCode的String,如"HOME"、"F1"或者"A"     |
| boolean isActionKey()                      | 返回此事件中的键是否为"动作"键                     |
| setKeyChar(char keyChar)                   | 设置keyCode值。以表示某个逻辑字符                  |
| setKeyCode(int keyCode)                    | 设置keyCode值。以表示某个物理键                    |

KeyEvent类对应按键常量(这里是部分，其他参考JDK文档):

| 按键                        | 说明                                       |
| ----------------------------| ------------------------------------------|
| VK_A到VK_Z                  | 对应键盘的"A"到"Z"按键                      |
| VK_0到VK_9                  | 对应键盘的"0"到"9"按键                      |
| VK_F1到VK_F24               | 对应键盘的"F1"到"F24"按键,普通键盘支持到F12   |
| VK_NUMPAD0到VK_NUMPAD9      | 对应小键盘的"0"到"9"按键                    |  
| VK_ALT                      | 对应键盘的"Alt"按键                         |
| VK_BACK_SLASH               | 对应键盘的"\"按键                           |
| VK_CONTROL                  | 对应键盘的"Ctrl"按键                        |
| VK_DELETE                   | 对应键盘的"Delete"按键                      |
| VK_END                      | 对应键盘的"End"按键                         |
| VK_ENTER                    | 对应键盘的"Enter"按键                       |
| VK_EQUALS                   | 对应键盘的"="按键                           |
| VK_ESCAPE                   | 对应键盘的"Esc"按键                         |
| VK_INSERT                   | 对应键盘的"Insert"按键                      |
| VK_LEFT                     | 对应键盘的左方向按键                         |
| VK_PERIOD                   | 对应键盘的"."按键                           |
| VK_RIGTH                    | 对应键盘的右方向按键                         |
| VK_SHIFT                    | 对应键盘的"Shift"按键                       |
| VK_SLASH                    | 对应键盘的"/"按键                           |


为控件添加键盘事件步骤:
(1)创建KeyListener对象
(2)调用addKeyLisenter()方法为控件注册KeyListener对象作为监听器
(3)操作键盘生成键盘事件
(4)执行KeyListener对象的方法，完成键盘事件的处理

实例:按下上下左右键时，不规则按钮位置随着变化
```
public class KeyDemo extends JFrame {
	public KeyDemo() {
		super();
		getContentPane().setLayout(null);
		setBounds(100,100,500,500);
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		final JPanel panel=new JPanel();//创建面板
		panel.setLayout(null);
		panel.setBounds(0, 0, 490, 490);
		getContentPane().add(panel);//面板添加到窗体
		final JButton button=new JButton();
		button.addKeyListener(new KeyAdapter() {
			public void keyPressed(KeyEvent e) {
				int key=e.getKeyCode();//获取用户的按键信息
				int x=button.getX();
				int y=button.getY();
				if(key==39){//用户按下右键情况
					x+=2;
				}
				if(key==37){//左
					x-=2;
				}
				if(key==38){//上
					y-=2;
				}
				if(key==40){//下
					y+=2;
				}
				button.setLocation(x, y);//重新定义按钮位置
			}
		});
		button.setContentAreaFilled(false);//不填充按钮区域
		button.setBorder(null);//不显示按钮边框
		URL url=getClass().getResource("bee.jpg");
		ImageIcon icon=new ImageIcon(url);//根据URL创建图片对象
		button.setIcon(icon);//设置按钮显示图片
		button.setBounds(45, 48, 80, 80);
		panel.add(button);//按钮添加到面板
	}
	public static void main(String[] args) {
		KeyDemo demo=new KeyDemo();
		demo.setVisible(true);
	}
}
```
按上下左右键图片对应移动
![图片](img/javause/28.png)


6.练习
-------
(1)登录窗体
```
public class SelectUser {
	Connection conn=null;
	static{
		try{
			Class.forName("com.mysql.jdbc.Driver");//加载驱动程序
			System.out.println("数据库驱动加载成功");
		}catch(ClassNotFoundException e){
			e.printStackTrace();
		}
	}
	
	public Connection getConn(){
		String url="jdbc:mysql://127.0.0.1:3306/test";//3306：端口号 test：数据库名称
		String userName="root";
		String passwd="";
		try{
			conn=DriverManager.getConnection(url,userName,passwd);
			if(conn != null){
				System.out.println("数据库连接成功!");
			}
		}catch(SQLException e){
			e.printStackTrace();
		}
		return conn;
	}
	
	//查询用户密码，有则返回true,没有则返回false
	public boolean selectUser(String user,String passwd){
		SelectUser selectUser=new SelectUser();
		Connection connection=selectUser.getConn();//获取数据库连接
		String sql="select * from user where name=? and passwd=?";//查询的sql语句
		//使用预处理语句进行查询
		try {
			PreparedStatement pStatement=connection.prepareStatement(sql);
			pStatement.setString(1, user);
			pStatement.setString(2, passwd);
			ResultSet rest=pStatement.executeQuery();//查询结果
			if(rest.next()){
				return true;
			}
		} catch (SQLException e) {
			e.printStackTrace();
		}
		return false;
	}
}


public class EntryFrame extends JFrame {
	public EntryFrame(){
		super();
		getContentPane().setLayout(null);//窗体设置为绝对布局
		setBounds(100,100,320,180);//窗体显示位置和大小
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		final JPanel panel=new JPanel();//定义面板组件
		panel.setLayout(null);//面板布局方式
		panel.setBounds(0,0,316,150);//面板位置和大小
		getContentPane().add(panel);//窗体中添加面板
		
		final JLabel name =new JLabel();//标签
		name.setFont(new Font("微软雅黑", Font.PLAIN,12));//设置标签显示字体样式
		name.setText("用户名：");//设置标签显示内容
		name.setBounds(62,27,52,26);
		panel.add(name);
		final JTextField nameTextField=new JTextField();//文本控件框
		nameTextField.setBounds(120,30,129,22);
		panel.add(nameTextField);
		
		final JLabel passWd =new JLabel();//标签
		passWd.setFont(new Font("微软雅黑", Font.PLAIN,12));//设置标签显示字体样式
		passWd.setText("密码：");//设置标签显示内容
		passWd.setBounds(65,55,44,18);
		panel.add(passWd);
		final JTextField passWdTextField=new JTextField();//文本控件框
		passWdTextField.setBounds(120,58,129,22);
		panel.add(passWdTextField);
		
		final JButton entry=new JButton();
		entry.setText("登录");
		entry.setBounds(84,104,64,28);
		panel.add(entry);
		final JButton cancel=new JButton();
		cancel.setText("关闭");
		cancel.setBounds(170,104,64,28);
		panel.add(cancel);	
		
		//登录按钮单击事件
		entry.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				String name=nameTextField.getText();//获取用户输入名字
				String passwd=passWdTextField.getText();//获取用户输入密码
				if(!name.equals("")&&!passwd.equals("")){//输入 不为空时
					SelectUser selectUser=new SelectUser();
					boolean bool=selectUser.selectUser(name, passwd);
					if(true==bool){
						JOptionPane.showConfirmDialog(null, "用户名密码正确","信息提示框",JOptionPane.WARNING_MESSAGE);
					}else{
						JOptionPane.showConfirmDialog(null, "用户名密码不正确","信息提示框",JOptionPane.WARNING_MESSAGE);
					}
				}else{
					JOptionPane.showConfirmDialog(null, "请输入用户名密码","信息提示框",JOptionPane.WARNING_MESSAGE);
				}
			}
		});
		
		cancel.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				System.exit(0);//关闭窗体
			}
		});
	}
	public static void main(String[] args) {
		EntryFrame frame=new EntryFrame();
		frame.setVisible(true);
	}

}
```
运行结果：
user数据表:

| name | passwd |
| -----| -------|
| zhang| 1      |
| li   | 1      |


![图片](img/javause/29.png)
![图片](img/javause/30.png)


(2)匹配游戏
通过图片的拖拽应用鼠标事件实现匹配
用1个面板放窗体底部，上面加3个JLabel标签代表图片匹配的位置，再创建1个面板上面加3个JLabel标签用于显示3个图片
实现了MouseListener和MouseMotionListener接口
```
public class Matching extends JFrame implements MouseListener,
		MouseMotionListener {
	private JLabel img[]=new JLabel[3];
	private JLabel targets[]=new JLabel[3];
	private Point pressPoint;//按住鼠标时的坐标
	public Matching() {
		getContentPane().setLayout(null);
		setBounds(100, 100, 364, 312);
		setTitle("匹配游戏");
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		final JPanel imagePanel=new JPanel();
		imagePanel.setLayout(null);
		imagePanel.setOpaque(false);//设置控件透明
		setGlassPane(imagePanel);//public Component getGlassPane()设置 glassPane 属性  GlassPane是透明的，用来捕获鼠标事件
		getGlassPane().setVisible(true);///////
		ImageIcon[] icon=new ImageIcon[3];
		icon[0]=new ImageIcon(getClass().getResource("bee.jpg"));
		icon[1]=new ImageIcon(getClass().getResource("fish.jpg"));
		icon[2]=new ImageIcon(getClass().getResource("dog.jpg"));
		final JPanel bottomPanel=new JPanel();
		bottomPanel.setLayout(new FlowLayout(FlowLayout.CENTER,20,3));//距离上面为3，左右间距20
		bottomPanel.setBounds(20, 180, 300, 80);//没有这行则不显示出目标面板
		
		for (int i = 0; i < 3; i++) {
			img[i]=new JLabel(icon[i]);
			img[i].setSize(50, 50);
			img[i].setBorder(new LineBorder(Color.GRAY));//设置线性边框
			int x=(int) (Math.random()*(getWidth()-50));
			int y=(int) (Math.random()*(getHeight()-150));
			img[i].setLocation(x, y);
			img[i].addMouseListener(this);//鼠标监听器
			img[i].addMouseMotionListener(this);
			imagePanel.add(img[i]);
			targets[i]=new JLabel();
			targets[i].setOpaque(true);//标签不透明，显示背景颜色
			targets[i].setBackground(Color.ORANGE);
			targets[i].setHorizontalTextPosition(SwingConstants.CENTER);//设置文本域图像水平居中
			targets[i].setVerticalTextPosition(SwingConstants.BOTTOM);//设置文本显示在图像下方
			targets[i].setPreferredSize(new Dimension(80,80));//设置标签首选大小
			targets[i].setHorizontalAlignment(SwingConstants.CENTER);//文字居中对齐
			bottomPanel.add(targets[i]);
		}
		targets[0].setText("蜜蜂");
		targets[1].setText("小鱼");
		targets[2].setText("小狗");
		getContentPane().add(bottomPanel,BorderLayout.SOUTH);
	}
	
	
	private boolean check(){
		boolean result=true;
		for (int i = 0; i < 3; i++) {
			Point location=img[i].getLocationOnScreen();//获取每个图像标签的位置
			Point seat=targets[i].getLocationOnScreen();//获取每个对应位置的坐标
			targets[i].setBackground(Color.GREEN);//设置匹配后的颜色
			if(location.x<seat.x||location.y<seat.y||location.x>seat.x+80||location.y>seat.y+80){//匹配失败情况
				targets[i].setBackground(Color.ORANGE);//恢复原来的颜色
				result=false;
			}
		}
		return result;
	}
	
	public void mousePressed(MouseEvent e) {
		pressPoint=e.getPoint();//保存拖放图片标签时的起始坐标
	}
	
	public void mouseDragged(MouseEvent e) {
		JLabel sourse=(JLabel) e.getSource();//获取事件源控件
		Point imgPoint=sourse.getLocation();//获取控件坐标
		Point point=e.getPoint();//获取鼠标坐标
		sourse.setLocation(imgPoint.x+point.x-pressPoint.x, imgPoint.y+point.y-pressPoint.y);
	}
	
	public void mouseReleased(MouseEvent e) {
		if(check()){//如果配对成功
			getGlassPane().setVisible(false);
			for(int i=0;i<3;i++){//遍历所有匹配位置的标签
				targets[i].setText("匹配成功");
				targets[i].setIcon(img[i].getIcon());//设置匹配的图标
			}
		}
	}
	
	public void mouseMoved(MouseEvent e) {}
	public void mouseClicked(MouseEvent e) {}	
	public void mouseEntered(MouseEvent e) {}
	public void mouseExited(MouseEvent e) {}
	
	public static void main(String[] args) {
		Matching matching=new Matching();
		matching.setVisible(true);
	}
}
```
运行效果:

![图片](img/javause/31.png)
![图片](img/javause/32.png)
![图片](img/javause/33.png)

补充:
都实现对事件监听的适配器与事件监听接口区别:
监听器有些方法用不到，用接口必须重写方法，适配器是对监听器的一个简化，适配器是抽象类，但类中方法并不是抽象的，可以对需要的方法重写，从而简化代码。


第十一章 Swing的高级控件
====================
Swing提供了一些高级控件如文本编辑器、工具栏、菜单、系统托盘等。

1.菜单
---------------
向框架中添加菜单需要3个类:菜单栏类(JMenuBar)、菜单类(JMenu)、菜单项类(JMenuItem)

(1)添加菜单步骤
创建菜单栏->创建菜单->创建菜单项

A.创建菜单栏
使用JMenuBar创建菜单栏，使用JFrame类的setJMenuBar()方法将菜单栏添加到窗体。
具体如下：
```
JMenuBar mb=new JMenuBar();
setJMenuBar(mb);//易错-------------------------------区别于其add()方法
备注:JMenuBar实例的add()方法实现在菜单栏中添加菜单对象
```

B.创建菜单
使用JMenu创建菜单，使用JMenuBar类的add()方法将菜单添加到菜单栏中。
JMenu构造方法：
```
JMenu()           //创建没有文本的新菜单
JMenu(String s)   //创建一个初始文本为指定字符串的新菜单
```
JMenu类常用方法：

| 方法                                | 说明                         |
| ------------------------------------| ----------------------------|
| add(JMenuItem menuItem)             | 将某个菜单项追加到此菜单的末尾  |
| insert(JMenuItem menuItem,int pos)  | 在给定位置插入指定的菜单项     |
| addSeparator()                      | 将新分隔符追加到菜单的末尾     |
| insertSeparator(int pos)            | 在指定的位置插入分隔符         |

C.创建菜单项
菜单项用于执行某个特定的命令，完成特定的操作(打开窗口，退出程序等)，可以从相应的菜单中选择菜单项。
使用JMenuItem创建菜单项，使用JMenu的add()方法添加到菜单上.
通过JMenuItem类可以创建普通的文字菜单项，也可以创建带有图片的菜单项。
JMenuItem类常见构造方法:
```
JMenuItem()			                   //创建不带有文本或者图标的菜单项
JMenuItem(String text)                 //创建带有指定文本的菜单项
JMenuItem(Icon icon)                   //创建带有指定图标的菜单项
JMenuItem(String text,Icon icon)       //创建带有文本或者图标的菜单项
```
菜单项的添加动作事件可以使用addActionListener(ActionListener actionListener)实现。

实例:创建菜单"文件"，在其中添加菜单项"打开"和"退出",在"打开"项添加图片文件，退出项添加单击事件
```
public class MenuDemo extends JFrame {
	public MenuDemo() {
		setTitle("创建菜单");
		setBounds(100, 100, 240, 160);
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		JMenuBar menuBar=new JMenuBar();//创建菜单栏
		JMenu menu_file=new JMenu("文件");//创建菜单“文件”
		URL url=getClass().getResource("file.png");
		ImageIcon icon=new ImageIcon(url);//图片实例
		JMenuItem menuItem_open=new JMenuItem("打开", icon);//菜单项"打开"
		JMenuItem menuItem_exit=new JMenuItem("退出");
		menuItem_exit.addActionListener(new ActionListener() {//菜单项"退出"监听事件
			public void actionPerformed(ActionEvent e) {
				System.exit(0);
			}
		});
		menu_file.add(menuItem_open);//添加菜单项
		menu_file.addSeparator();//打开和退出之间添加分隔符
		menu_file.add(menuItem_exit);
		menuBar.add(menu_file);
		setJMenuBar(menuBar);//菜单栏添加到窗体
		
	//二级菜单如下
		JMenu menu_new=new JMenu("新建");//创建菜单“新建”
		menu_file.add(menu_new);//将菜单"新建"添加到菜单"文件"
		JMenuItem menuItem_txt=new JMenuItem("文本");
		menu_new.add(menuItem_txt);
	}
	public static void main(String[] args) {
		MenuDemo frame=new MenuDemo();
		frame.setVisible(true);
	}
}
```
![图片](img/javause/34.png)
![图片](img/javause/35.png)

(2)创建弹出式菜单
弹出式菜单就是单击鼠标右键时弹出的菜单，弹出式菜单由鼠标位置决定弹出菜单位置。
使用JPopupMenu类表示弹出式菜单。
JPopupMenu类构造方法:
```
JPopupMenu()             //构造一个新的弹出式菜单
JPopupMenu(String label) //构造一个有标题的弹出式菜单
```
可以通过add()方法向JPopupMenu类中添加JMenuItem对象

JPopupMenu类常用方法:

| 方法                                | 说明                                                      |
| ------------------------------------| ---------------------------------------------------------|
| add(JMenuItem menuItem)             | 将指定菜单项添加到此弹出菜单的末尾                            |
| addSeparator()                      | 将新分隔符添加到菜单的末尾                                   |
| isPopupTrigger(MouseEvevt e)        | 如果弹出菜单的当前组件将鼠标事件视为弹出菜单的触发器，则返回true |
| show(Component parent,int x,int y)  | 在组件调用者的坐标空间中的位置(x,y)处显示弹出菜单              |

实例如下:
```
public class JPopupMenuDemo extends JFrame {
	public JPopupMenuDemo() {
		setBounds(100, 100, 250, 203);
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		getContentPane().setLayout(null);
		final JPopupMenu menu=new JPopupMenu("编辑");
		JMenuItem copy=new JMenuItem("编辑");
		JMenuItem stick=new JMenuItem("粘贴");
		JMenuItem cut=new JMenuItem("剪切");
		menu.add(copy);
		menu.add(stick);
		menu.add(cut);
		this.addMouseListener(new MouseAdapter() {//为标签添加鼠标监听器
			public void mouseReleased(MouseEvent e) {
				if(e.isPopupTrigger()){//如果弹出菜单的当前组件将鼠标事件视为弹出菜单的触发器
					menu.show(e.getComponent(), e.getX(), e.getY());//鼠标右键单击处显示
				}
			}
		});
	}
	public static void main(String[] args) {
		JPopupMenuDemo demo=new JPopupMenuDemo();
		demo.setVisible(true);
	}
}
```
鼠标右键:
![图片](img/javause/36.png)


2.工具栏
----------------
javax.swing.JToolBar类创建工具栏，而对话框包括信息对话框、文件对话框等。
(1)创建工具栏并添加工具按钮
与菜单相比，工具栏更适合使用图像来表示命令，窗体中工具栏紧挨着菜单栏。工具栏与菜单栏一样是控件容器，可以添加菜单、组合框等。
JToolBar类常用构造方法:
```
JToolBar()                   //构造一个默认位置为水平方向的工具栏
JToolBar(String name)        //构造一个默认位置为水平方向，当工具栏成为浮动状态时具有指定的图标
```

JToolBar类常用方法:

| 方法                                | 说明                                         |
| ------------------------------------| --------------------------------------------|
| Component add(Component c)          | 在工具栏末尾添加指定组件如按钮、复选框、单选按钮等 |
| void addSeparator()                 | 将默认大小的分隔符添加到工具栏末尾              |
| void addSeparator(Dimension size)   | 将指定大小的分隔符添加到工具栏末尾              |
| void setFloatable(boolean b)        | 设置工具栏是否可以移动，可以移动设置为true      |

备注:如果希望工具栏可以随意移动，窗体一定要采用默认的边界布局方式，并且不能在边界布局的四周添加任何控件。

实例：在窗体中添加可移动的工具栏对象，并在工具栏中添加"新建"、"保存"、"退出"按钮。
```

```
![图片](img/javause/37.png)
![图片](img/javause/38.png)
![图片](img/javause/39.png)


(2)文件对话框
实际应用中经常需要选择文件，如读取文件或者选择指定类型文件等。通过javax.swing.JFileChooser类实现。
JFileChooser类常用构造方法:
```
JFileChooser()                //构造一个指定默认目录的文件选择对话框
JFileChooser(File f)          //使用给定的File作为路径来构造一个文件选择对话框
JFileChooser(String dif)      //构造一个使用给定路径的选择对话框

重要字段:
APPROVE_OPTION-------------单击了打开按钮，用户选择了文件，可以对文件进行操作
CANCEL_OPTION--------------单击了取消按钮，用户没有选择文件

方法:
int showOPenDialog()---------显示对话框
```

实例:文件菜单中添加打开项，弹出打开文件对话框
```
public class FileChooseDemo extends JFrame {
	public FileChooseDemo() {
		setBounds(100, 100, 294, 167);
		setTitle("文件选择对话框");
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		JMenuBar menuBar=new JMenuBar();//菜单栏
		setJMenuBar(menuBar);//添加到窗体
		JMenu menu=new JMenu("文件");//菜单
		menuBar.add(menu);//添加菜单
		JMenuItem open=new JMenuItem("打开");//菜单项
		menu.add(open);
		open.addActionListener(new ActionListener() {//添加单击事件
			public void actionPerformed(ActionEvent e) {/////////////////////////////////////
				JFileChooser fileChooser=new JFileChooser();//文件选择对话框
				fileChooser.showOpenDialog(getContentPane());//显示对话框
				//public int showOpenDialog(Component parent)-------parent - 该对话框的父组件，可以为 null
			}
		});
	}
	public static void main(String[] args) {
		FileChooseDemo demo=new FileChooseDemo();
		demo.setVisible(true);
	}
}
```
![图片](img/javause/40.png)


文件过滤器:
JFileChooser类的方法setFileFilter(FileFilter filter)对文件选择框实现过滤，只显示指定类型文件。
该方法的参数类型javax.swing.filechooser.FileFilter为一个抽象类，实现该类可以对文件进行过滤。
FileFilter类方法：

| 方法                                       | 说明                                         |
| -------------------------------------------| --------------------------------------------|
| public abstract boolean accept(File file)  | 过滤文件                                     |
| public abstract String getDescription()    | 返回选择对话框中文件类型的描述信息              |

javax.swing.filechooser.FileNameExtensionFilter实现了FileFilter类。
FileNameExtensionFilter只有一个构造方法：
```
FileNameExtensionFilter(String description,String...extensions) //description文件选择对话框中文件类型的描述信息，extensions文件对话框中允许显示的文件类型，多个文件类型用逗号分隔。
```
实例：
```
public class FileChooseDemo extends JFrame {
	public FileChooseDemo() {
		setBounds(100, 100, 294, 167);
		setTitle("文件选择对话框");
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		JMenuBar menuBar=new JMenuBar();//菜单栏
		setJMenuBar(menuBar);//添加到窗体
		JMenu menu=new JMenu("文件");//菜单
		menuBar.add(menu);//添加菜单
		JMenuItem open=new JMenuItem("打开");//菜单项
		menu.add(open);
		open.addActionListener(new ActionListener() {//添加单击事件
			public void actionPerformed(ActionEvent e) {/////////////////////////////////////
				JFileChooser fileChooser=new JFileChooser();//文件选择对话框
				FileFilter filter=new FileNameExtensionFilter("图像文件(*。bmp,*.gif,*.jpg,*.ipeg,*.png)","bmp","gif","jpg","jpeg","png");
				fileChooser.setFileFilter(filter);//设置文件过滤器
				fileChooser.showOpenDialog(getContentPane());//显示对话框
				//public int showOpenDialog(Component parent)-------parent - 该对话框的父组件，可以为 null			
			}
		});
	}
	public static void main(String[] args) {
		FileChooseDemo demo=new FileChooseDemo();
		demo.setVisible(true);
	}
}
```
![图片](img/javause/41.png)


(3)信息对话框
进行一个重要的操作动作时，可以使用信息对话框给用户提供一些重要信息。
javax.swing.JOptionPane类提供信息对话框功能，showMessageDialog()方法创建一个信息对话框。
```
public static void showMessageDialog(Component parentComponent,Object message,String title,int messageType)
parentComponent//信息对话框所依赖的控件，信息对话框会在该控件正前方显示，如JFrame窗体等
message//指定对话框上显示的文字信息
title//对话框的标题字符串
messageType//要显示的信息类型，包括ERROR_MESSAGE,INFORMATION_MESSAGE,WARNING_MESSAGE,QUESTION_MESSAGE,PLAIN_MESSAGE。当为WARNING_MESSAGE时对话框会有"!"
```
实例:根据长和宽计算面积，输入非法数据时给出提示信息
```
public class Square extends JFrame {
	public Square() {
		getContentPane().setLayout(null);
		setTitle("计算面积");
		setBounds(100, 100, 300, 200);
		JPanel panel=new JPanel();
		panel.setBounds(0, 0, 280, 180);
		panel.setLayout(null);
		getContentPane().add(panel);
		JLabel wLabel=new JLabel();
		wLabel.setText("长");
		wLabel.setBounds(40, 20, 20, 18);
		panel.add(wLabel);
		JLabel hLabel=new JLabel();
		hLabel.setText("宽");
		hLabel.setBounds(40, 60, 20, 18);
		panel.add(hLabel);
		
		final JTextField wTextField=new JTextField();
		wTextField.setBounds(70, 20, 100, 20);
		panel.add(wTextField);
		final JTextField hTextField=new JTextField();
		hTextField.setBounds(70, 60, 100, 20);
		panel.add(hTextField);
		
		JButton button=new JButton();
		button.setText("确定");
		button.setBounds(80, 100, 60, 40);
		panel.add(button);
		button.addActionListener(new ActionListener() {
			
			public void actionPerformed(ActionEvent e) {
				String w=wTextField.getText();
				String h=hTextField.getText();
				boolean bool=true;
				char[] length=w.toCharArray();//获取字符串的字符数组
				char[] hight=h.toCharArray();
				for(int i=0;i<length.length;i++){//判断是否有非数字字符
					if(!(Character.isDigit(length[i]))){
						bool=false;
					}
				}
				for(int i=0;i<hight.length;i++){//判断是否有非数字字符
					if(!(Character.isDigit(hight[i]))){
						bool=false;
					}
				}
				if(false==bool){
					JOptionPane.showMessageDialog(getContentPane(), "输入了非法字符", "警告提示框", JOptionPane.WARNING_MESSAGE);
				}else{
					int leng=Integer.parseInt(w);//字符串转换为整数
					int widt=Integer.parseInt(h);
					JOptionPane.showMessageDialog(getContentPane(), "面积:"+leng*widt, "面积计算结果", JOptionPane.INFORMATION_MESSAGE);
				}
			}
		});
	}
	public static void main(String[] args) {
		Square square=new Square();
		square.setVisible(true);
	}
}
```
![图片](img/javause/42.png)
![图片](img/javause/43.png)


(4)颜色对话框
用户可以通过颜色对话框选择自己喜欢的颜色，来改变字体颜色.
javax.swing.JColorChooser类的静态方法可以创建一个颜色对话框。
```
showDialog(Component component,String title,Color initialColor)
component            //指定对话框所依赖的控件，如窗体等
title                //指定对话框的标题
initialColor         //指定颜色对话框中选择颜色返回一个颜色对象
```
实例：单击按钮选择窗体背景颜色
```
public class ColorChooseDemo extends JFrame {
	public ColorChooseDemo() {
		getContentPane().setLayout(null);
		setBounds(100, 100, 251, 182);
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		final JPanel panel=new JPanel();
		panel.setLayout(null);
		panel.setBounds(0, 0, 243, 148);
		getContentPane().add(panel);
		final JButton button=new JButton("选择颜色");
		button.setBounds(65, 43, 86, 28);
		panel.add(button);
		button.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				Color color=JColorChooser.showDialog(getContentPane(), "调色板", panel.getBackground());//显示颜色对话框
				panel.setBackground(color);
			}
		});
	}
	public static void main(String[] args) {
		ColorChooseDemo demo=new ColorChooseDemo();
		demo.setVisible(true);
	}
}
```
![图片](img/javause/44.png)
![图片](img/javause/45.png)
![图片](img/javause/46.png)


(5)确认对话框
确认对话框一般会出现在用户要删除数据、修改数据时，用于保护系统的安全。
通过javax.swing.JOptionPane类静态方法showConfirmDialog()可以创建一个确认对话框。
```
showConfirmDialog(Component parentComponent,Object message,String title,int optionType)
parentComponent  //指定确认对话框所依赖的控件，确认对话框会在该控件的正前方显示
message          //对话框中显示的信息
title            //指定对话框的标题
optionType       //确认对话框的外观，可选值为YES_NO_OPTION,YES_NO_CANCEL_OPTION,OK_CANCEL_OPTION，如值为YES_NO_OPTION时只有yes、no两个按钮。
```

实例：用户输入姓名后单击回车弹出“确认”对话框，确定时将用户姓名显示在文本域中。
```
public class JOptionPaneDemo extends JFrame {
	public JOptionPaneDemo() {
		getContentPane().setLayout(null);
		setBounds(100,100, 300, 200);
		JPanel panel=new JPanel();
		getContentPane().add(panel);
		panel.setLayout(null);
		panel.setBounds(0, 0, 300, 200);
		JLabel label=new JLabel("请输入姓名:");
		panel.add(label);
		label.setBounds(40, 40, 70, 20);
		final JTextField field=new JTextField();//需要final后面才能调用----文本框-----输入信息
		field.setBounds(140, 40, 120, 20);
		panel.add(field);
		final JTextArea field2=new JTextArea();//文本域------显示信息----------区别于文本框
		field2.setBounds(40, 80, 180, 60);
		panel.add(field2);
		field.addActionListener(new ActionListener() {//输入框添加监听事件，输入完毕回车时执行
			public void actionPerformed(ActionEvent e) {
				String name=field.getText();
				if(name.equals("")){//没有输入就回车情况
					JOptionPane.showConfirmDialog(getContentPane(), "没有输入姓名", "信息提示框", JOptionPane.CANCEL_OPTION);
				}else{//输入姓名后弹出确认框
					int n=JOptionPane.showConfirmDialog(getContentPane(), "确认正确吗?", "确认对话框", JOptionPane.YES_NO_CANCEL_OPTION);
					if(JOptionPane.YES_OPTION==n){//如果用户确认信息 //选择NO时返回NO_OPTION
						field2.append(name+"\n");
						field.setText("");
					}
				}
			}
		});
	}
	public static void main(String[] args) {
		JOptionPaneDemo demo=new JOptionPaneDemo();
		demo.setVisible(true);
	}
}
```
![图片](img/javause/47.png)



3.表格
--------------
表格是由多行多列组成的二维表形式，由Swing中的JTable类实现。
表格通常需要显示在滚动面板上，否则面板不会显示列标题。
(1)表格创建及其常用方法
构造方法：
```
JTable()                                      //创建一个没有初始数据的表格
JTable(Object[][] rowData,Object[] columnName)//以二维数组rowData中的元素值作为单元格中显示的数据，以一维数组columnName中的元素值作为列名创建一个表格
JTable(TableModel model)                      //使用表格模型model创建一个表格
JTable(Vector dataVector,Vector columnVector) //以向量dataVector中的元素值作为单元格中显示的数据，以向量columnVector中的元素值作为列名创建一个表格
```
后三个构造方法详情见下：
```
String[] columnNames={"学号","姓名","分数"};
String[][] rowData={{"1","zhang","80"},{"2","li","79"}};
JTable table=new JTable(rowData,columnNames);
JScrollpane pane=new JScrollpane();//创建滚动窗格
pane.setViewportView(table);//添加表格到窗格
getContentPane().add(pane);


DefaultTableModel model=new DefaultTableModel(rowData,columnNames);
JTable table=new JTable(model);
JScrollpane pane=new JScrollpane();//创建滚动窗格
pane.setViewportView(table);//添加表格到窗格
getContentPane().add(pane);


Vector columnVector=new Vector();
columnVector.add("学号");//添加列名
columnVector.add("姓名");
columnVector.add("分数");
Vector dataVector=new Vector();//定义表格数据向量
Vector rowVector=new Vector();//定义行向量
rowVector.add("1");
rowVector.add("zhang");
rowVector.add("80");
dataVector.add(rowVector);
JTable table=new JTable(dataVector,columnVctor);
JScrollpane pane=new JScrollpane();//创建滚动窗格
pane.setViewportView(table);//添加表格到窗格
getContentPane().add(pane);
```

表格常见方法:

| 方法                     | 说明                                                 |
| ------------------------| -----------------------------------------------------|
| getModel()              | 获取表格所显示数据的表格模型                             |
| getRowCount()           | 获取表格中所显示数据的行数                               |
| getSelectedColumn()     | 获取表格中第一个选择列的索引，如果没有被选择的列，返回-1    |
| getSelectedRow()        | 获取表格中第一个选择行的索引，如果没有被选择的行，返回-1    |
| getValueAt()            | 获取由指定行索引row和列索引column指定单元格的值           |
| setAutoResizeMode()     | 设置表格的自动调整模式                                  |
| setSelectionMode()      | 设置表格的选择模式                                      |

实例：窗体中添加表格控件，实现向表格中添加数据行、修改数据库以及删除数据行。
```
public class EditTableModelFrame extends JFrame {
	DefaultTableModel tableModel;
	JTable table;
	JTextField aTextField,bTextField;
	
	public EditTableModelFrame() {
		setTitle("维护表格模型");
		setBounds(100, 100, 400, 200);
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		final JScrollPane scrollPane=new JScrollPane();//滚动面板
		getContentPane().add(scrollPane,BorderLayout.CENTER);
		String[] columnNames={"学号","姓名"};//定义表格列名数组
		String[][] tableValue={{"1","zhang"},{"2","li"}};//定义表格数据数组
		tableModel=new DefaultTableModel(tableValue, columnNames);
		table=new JTable(tableModel);//创建指定表格模型的表格
		table.setRowSorter(new TableRowSorter(tableModel));//设置表格的排序器
		table.setSelectionMode(ListSelectionModel.SINGLE_SELECTION);//设置表格的选择模式单选
		table.addMouseListener(new MouseAdapter() {//为表格添加鼠标事件监听器
			public void mouseClicked(MouseEvent e) {
				int selectedRow=table.getSelectedRow();//获取被选中的行的索引
				Object oa=tableModel.getValueAt(selectedRow, 0);//从表格模型中获得指定值---学号
				Object ob=tableModel.getValueAt(selectedRow, 1);  //姓名
				aTextField.setText(oa.toString());//将获得的值赋值给文本框
				bTextField.setText(ob.toString());
			}
		});
		scrollPane.setViewportView(table);//把表格放到滚动面板的视图中
		final JPanel panel=new JPanel();
		getContentPane().add(panel,BorderLayout.SOUTH);//面板添加到窗体下面
		panel.add(new JLabel("A: "));
		aTextField=new JTextField("A3", 4);//创建文本框
		panel.add(aTextField);
		panel.add(new JLabel("B: "));
		bTextField=new JTextField("B3", 4);
		panel.add(bTextField);
		
		final JButton addButton=new JButton("添加");
		addButton.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				String[] rowValues={aTextField.getText(),bTextField.getText()};//创建表格行数组
				tableModel.addRow(rowValues);//向表格模型中添加一行
				int rowCount=table.getRowCount()+1;//表格行总数加1
				aTextField.setText("A"+rowCount);//文本框设置值为A连接总行数加1的值
				bTextField.setText("B"+rowCount);
			}
		});
		panel.add(addButton);
		
		final JButton updButton=new JButton("修改");
		updButton.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				int selectedRow=table.getSelectedRow();
				if(selectedRow!=-1){//判断 是否存在被选中行
					tableModel.setValueAt(aTextField.getText(), selectedRow, 0);
					tableModel.setValueAt(bTextField.getText(), selectedRow, 1);
				}
			}
		});
		panel.add(updButton);
		
		final JButton delButton=new JButton("删除");
		delButton.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				int selectedRow=table.getSelectedRow();
				if(selectedRow!=-1){//是否存在选中行
					tableModel.removeRow(selectedRow);
				}
			}
		});
		panel.add(delButton);
	}
	public static void main(String[] args) {
		EditTableModelFrame frame=new EditTableModelFrame();
		frame.setVisible(true);
	}
}
```
如下可以实现增加、修改、删除
![图片](img/javause/48.png)


(2)对模型事件的监听和处理
TableModelListener接口可监听模型事件，实现该接口，可监控表格的变化，该接口中只有一个方法tableChanged(),当模型产生表格事件时被调用。
tableChanged()方法只有一个入口参数为TableModelEvent,该类通过的方法可以对表格模型事件进行处理。
TableModelEvent类方法如下：

| 方法             | 说明                                                 |
| -----------------| ----------------------------------------------------|
| getColumn()      | 返回表格模型中事件的列                                 |
| getFirstRow()    | 返回表格模型中第一个被更改的行                          |
| getLastRow()     | 返回表格模型中最后一个被更改的行                        |
| getType()        | 返回事件类型，该类型为INSERT、UPDATE、DELETE之一         |

TableModelEvent类的 getType()方法可以判断事件的类型，通过TableModelEvent类的字段可以实现对事件类型的判断。
TableModelEvent类常用字段：

| 字段                    | 说明                                   |
| ------------------------| --------------------------------------|
| TableModelEvent.DELETE  | 表示对表格模型中的行或者列进行了删除操作   |
| TableModelEvent.INSERT  | 表示在表格模型中添加了新的行或者列        |
| TableModelEvent.UPDATE  | 表示对表格模型中的现有数据进行了修改操作   |

除了数据模型发生变化会触发表格模型监听事件外，还可以通过AbstractTableModel类提供的方法来触发表格模型事件监听器对事件进行处理。
AbstractTableModel常用方法：

| 字段                                               | 说明                                             |
| ---------------------------------------------------| ------------------------------------------------|
| firstTablecellUpdated(int row,int column)          | 通知所有监听器，已更新[row,column]处的单元格值       |
| firstTableRowsDeleted(int firstRow,int lastRow)    | 通知所有监听器，已删除范围在[firstRow,lastRow]的行   |
| firstTableRowsInserted(int firstRow,int lastRow)   | 通知所有监听器，已插入范围在[firstRow,lastRow]的行   |
| firstTableRowsUpdated(int firstRow,int lastRow)    | 通知所有监听器，已更新范围在[firstRow,lastRow]的行   |

备注：AbstractTableModel类方法触发事件监听器时，并不是真正的对表格进行了添加删除等操作，只是通过这些方法通知表格的所有监听器，并对事件进行响应处理。事件响应代码可以对事件类型分类，不同事件分别实现不同功能。

实例：实现表格数据的修改删除，更改后提示
```
public class TableModelEventFrame extends JFrame {
	private DefaultTableModel tableModel;//表格模型
	private JTable table;//表格
	public TableModelEventFrame() {
		setTitle("表格模型事件");
		setBounds(100, 100, 300, 160);
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		final JScrollPane scrollPane=new JScrollPane();//滚动面板
		getContentPane().add(scrollPane,BorderLayout.CENTER);//添加在中间
		String[] columnNames={"学号","姓名"};//表格列名数组
		String[][] tableValues={{"1","zhang"},{"2","cheng"}};//表格数据数组
		tableModel=new DefaultTableModel(tableValues,columnNames);
		tableModel.addTableModelListener(new TableModelListener() {//为表格添加事件监听器
			public void tableChanged(TableModelEvent e) {
				if(e.getType()==TableModelEvent.UPDATE){//是否修改
					JOptionPane.showConfirmDialog(getContentPane(), "单击修改按钮", "信息对话框", JOptionPane.CANCEL_OPTION);
				}
				if(e.getType()==TableModelEvent.DELETE){//是否修改
					JOptionPane.showConfirmDialog(getContentPane(), "单击删除按钮", "信息对话框", JOptionPane.CANCEL_OPTION);
				}
			}
		});
		table=new JTable(tableModel);//创建表格
		table.setRowSorter(new TableRowSorter(tableModel));//表格排序器
		table.setSelectionMode(ListSelectionModel.SINGLE_SELECTION);//表格选择模式单选
		scrollPane.setViewportView(table);//表格添加到面板视图
		final JPanel panel=new JPanel();
		getContentPane().add(panel,BorderLayout.SOUTH);
		final JButton updButton=new JButton("修改");
		updButton.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				int selectedRow=table.getSelectedRow();
				if(selectedRow!=-1){
					tableModel.fireTableRowsUpdated(selectedRow, selectedRow);//通知所有监听器修改了索引位置的数据行
				}
			}
		});
		panel.add(updButton);
		final JButton delButton=new JButton("删除");
		delButton.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				int selectedRow=table.getSelectedRow();				
				if(selectedRow!=-1){
					tableModel.fireTableRowsDeleted(selectedRow, selectedRow);//通知所有监听器修改了索引位置的数据行
				}				
			}
		});
		panel.add(delButton);
	}
	public static void main(String[] args) {
		TableModelEventFrame frame=new TableModelEventFrame();
		frame.setVisible(true);
	}
}
```
单击按钮或者直接在表格中改变数据后回车弹出窗口
![图片](img/javause/49.png)
![图片](img/javause/50.png)


4.系统托盘
--------------
系统托盘
系统托盘是一个特殊区域，可以驻留程序，被运行在桌面的所有程序共享，系统托盘显示在桌面底部。
(1)获取系统托盘
java.awt.SystemTray类表示桌面的系统托盘，每个java应用程序在运行时都会分配一个该类实例。
SystemTray类常用方法:

| 方法                               | 说明                                      |
| -----------------------------------| -----------------------------------------|
| void add(TrayIcon trayIcon)        | 将托盘图标添加到系统托盘                    |
| static SystemTray getSystemTray()  | 获取表示桌面托盘区的系统托盘实例             |
| TrayIcon[] getTrayIcons()          | 返回由此应用程序添加到托盘中的所有图标的数组   |
| Dimension getTrayIconSize()        | 返回托盘图标在系统托盘中占用的空间大小（像素） |
| static boolean isSupported()       | 返回当前平台是否支持系统托盘                 |
| void remove(TrayIcon trayIcon)     | 从系统托盘中移除指定的托盘图标               |

备注:有些平台不支持系统托盘，因此在使用时可以先使用isSupported()判断一下。可以再获取系统托盘getSystemTray()

(2)为系统托盘添加图标
系统托盘可以包含一个或者多个托盘图标，需要时add(TrayIcon trayIcon)添加，不需要时remove(TrayIcon trayIcon)移除。
托盘图标由TrayIcon类表示，其构造方法：
```
TrayIcon(Image image)                                 //创建带有指定图像的托盘图标
TrayIcon(Image image,String tooltip)                  //创建带有指定图像和工具提示文本的托盘图标
TrayIcon(Image image,String tooltip,PopupMenu popup)  //创建带有指定图像、工具提示文本和弹出菜单的托盘图标
```
指定图像：托盘显示的图像
工具提示文本：鼠标放置在系统托盘中出现的文字
弹出菜单：鼠标右键弹出菜单

(3)添加弹出菜单
在托盘中单击鼠标右键时会显示菜单。
TrayIcon类的setPopupMenu(PopupMenu popupMenu)方法实现为系统托盘设置弹出式菜单


实例:
```
public class SystemTrayFrame extends JFrame {
	public SystemTrayFrame() {
		setTitle("使用系统托盘");
		setBounds(100, 100, 260, 180);
		setDefaultCloseOperation(JFrame.DISPOSE_ON_CLOSE);
		if(SystemTray.isSupported()){//是否支持系统托盘
			URL url=getClass().getResource("system.png");
			ImageIcon icon=new ImageIcon(url);
			Image image=icon.getImage();//获取Image对象
			TrayIcon trayIcon=new TrayIcon(image);
			trayIcon.setToolTip("系统托盘");//添加工具提示文本
			PopupMenu popupMenu=new PopupMenu();//弹出式菜单
			MenuItem exit=new MenuItem("退出");//菜单项
			MenuItem show=new MenuItem("显示主窗体");
			//添加事件监听器
			exit.addActionListener(new ActionListener() {
				public void actionPerformed(ActionEvent e) {
					System.exit(0);//退出系统
				}
			});
			show.addActionListener(new ActionListener() {
				public void actionPerformed(ActionEvent e) {
//					getContentPane().setVisible(true);//显示窗体  这条语句和下面一条一样的效果
					showFrame();
				}
			});
			popupMenu.add(show);//为弹出菜单添加菜单项
			popupMenu.add(exit);
			trayIcon.setPopupMenu(popupMenu);//为托盘图标添加弹出菜单
			SystemTray systemTray=SystemTray.getSystemTray();
			try {
				systemTray.add(trayIcon);//为系统添加托盘图标
			} catch (AWTException e1) {
				e1.printStackTrace();
			}
		}
	}
	
	public void showFrame(){
		this.setVisible(true);
	}
	
	public static void main(String[] args) {
		SystemTrayFrame frame=new SystemTrayFrame();
		frame.setVisible(true);
	}
}
```
![图片](img/javause/51.png)
![图片](img/javause/52.png)



5.练习
--------------
(1)随意获取文件属性
打开文件选择对话框选择任意文件将用户选择文件的属性显示在窗体中。
```
public class OpenTextFileFrame extends JFrame {
	JTextArea ta_showProperty = new JTextArea();//文本域
	JTextArea ta_showText =new JTextArea();
	public OpenTextFileFrame() {
		//getContentPane().setLayout(null); //取消这行才能显示---不然只有窗体
		setBounds(100, 100, 260, 200);
		setTitle("打开文件");
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		
		final JToolBar toolBar=new JToolBar();//工具栏
		getContentPane().add(toolBar,BorderLayout.NORTH);
		JButton open_Button=new JButton("打开");
		open_Button.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				openTextFile();//调用方法操作文件
			}
		});
		toolBar.add(open_Button);
		
		JButton exit_Button=new JButton("退出");
		exit_Button.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				int n=JOptionPane.showConfirmDialog(getContentPane(), "确认退出吗","确认对话框",JOptionPane.YES_NO_OPTION);
				if(JOptionPane.YES_OPTION==n){
					System.exit(0);//退出系统
				}
			}
		});
		toolBar.add(exit_Button);
		final JTabbedPane tabbedPane=new JTabbedPane();//选项卡面板
		getContentPane().add(tabbedPane,BorderLayout.CENTER);
		final JScrollPane scrollPane=new JScrollPane();
		tabbedPane.addTab("文件的属性",null,scrollPane,null);//滚动面板放到选项卡的第一个选项页
		scrollPane.setViewportView(ta_showProperty);//文本域添加到滚动面板视图-----------------注意：不能用add
		final JScrollPane scrollPane2=new JScrollPane();
		tabbedPane.addTab("文件内容",null,scrollPane2,null);//第二个选项卡
		scrollPane2.setViewportView(ta_showText);
	}
	
	public void openTextFile(){
		JFileChooser fileChooser=new JFileChooser();//文件选择对话框
		int returnValue=fileChooser.showOpenDialog(getContentPane());//打开文件选择对话框
		if(returnValue==JFileChooser.APPROVE_OPTION){//是否选择了文件
			File file=fileChooser.getSelectedFile();//获取文件对象
			ta_showProperty.append("文件路径："+file.getAbsolutePath()+"\n");
			ta_showProperty.append("隐藏文件:"+file.isHidden()+"\n");
			FileReader reader;//字符流
			BufferedReader in;//字符缓冲流
			try {
				reader=new FileReader(file);//字符流
				in=new BufferedReader(reader);//字符缓冲流
				String info=in.readLine();//从文件中读取一行信息
				while(info!=null){
					ta_showText.append(info+"\n");
					info=in.readLine();//继续读下一行
				}
				in.close();
				reader.close();
			} catch (Exception e) {
				e.printStackTrace();
			}
		}
	}
	
	public static void main(String[] args) {
		OpenTextFileFrame frame=new OpenTextFileFrame();
		frame.setVisible(true);
	}
}
```
打开txt文件如下:
![图片](img/javause/53.png)
![图片](img/javause/54.png)

打开图片文件如下:
![图片](img/javause/55.png)
![图片](img/javause/56.png)



(2)实现浏览图片
创建窗体，在窗体上添加"上一张"与"下一张"按钮，实现浏览指定文件夹下的图片。
```
public class BrowsePictureFrame extends JFrame {
	public BrowsePictureFrame() {
		setTitle("浏览图片");
		setBounds(100, 100, 300, 180);
		setDefaultCloseOperation(JFrame.DISPOSE_ON_CLOSE);
		final JSplitPane splitPane=new JSplitPane();//分割面板
		getContentPane().add(splitPane,BorderLayout.CENTER);
		final JPanel buttonPanel=new JPanel();
		splitPane.setLeftComponent(buttonPanel);//放按钮的面板放到分割面板左边
		splitPane.setDividerLocation(90);//设置分割线的位置
		final JPanel showpictureJPanel=new JPanel();
		final CardLayout cardLayout=new CardLayout();//创建卡片式布局
		showpictureJPanel.setLayout(cardLayout);//把显示图片的面板设置为卡片式布局
		splitPane.setRightComponent(showpictureJPanel);
		for(int i=1;i<=5;i++){
			String pictureIndex=String.valueOf(i);//把图片的索引值转换为字符串
			String pictureName=String.valueOf(pictureIndex)+".jpg";
			URL url=getClass().getResource(pictureName);
			ImageIcon icon=new ImageIcon(url);
			showpictureJPanel.add(new JLabel(icon),pictureIndex);
		}
		final JButton previousButton=new JButton();
		previousButton.setText("上一张");
		previousButton.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				cardLayout.previous(showpictureJPanel);//显示上一张图片
			}
		});
		buttonPanel.add(previousButton);//按钮添加到左侧面板
		final JButton nextButton=new JButton();//创建显示下一张图片的按钮
		nextButton.setText("下一张");
		nextButton.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				cardLayout.next(showpictureJPanel);//显示下一张图片
			}
		});
		buttonPanel.add(nextButton);
	}
	public static void main(String[] args) {
		BrowsePictureFrame frame=new BrowsePictureFrame();
		frame.setVisible(true);
	}
}
```
按上一张下一张可以实现图片1，2，3，4，5循环.
![图片](img/javause/57.png)
![图片](img/javause/58.png)


备注：菜单的启动和禁用可以通过JMenuItem类的setEnabled()方法，参数设置false菜单禁用，true菜单启用。



第十二章 绘图与打印技术
======================
前面的内容无法在程序界面显示背景图片、无法处理图片、无法实现打印功能等。为了美化java应用程序的界面，可以通过java提供的绘图技术实现。PrintJob可以获得打印对象再调用相应的方法打印。

1.java绘图
-----------------------------
Java使用Graphics类和Graphics2D类(继承自Graphics 推荐使用，Graphics类的实例可以进行强转)绘制图形。
Graphics类常用方法:

| 方法                                                                             | 说明        |
| ---------------------------------------------------------------------------------| -----------|
| drawArc(int x,int y,int width,int height,int startAngle,int arcAngle)            | 弧形       |
| drawLine(int x1,int y1,int x2,int y2)                                            | 直线       |
| drawOval(int x,int y,int width,int height)                                       | 椭圆       |
| drawPolygon(int[] xPoints,int[] yPoints,int n) //(xn,yn)坐标全部依次连成n点,首尾闭合| 多边形      |
| drawPolyline(int[] xPoints,int[] yPoints,int n) //(xn,yn)坐标全部依次连成 首尾不闭合| 多边线      |
| drawRect(int x,int y,int width,int height)                                       | 矩形       |
| drawRoundRect(int x,int y,int width,int height,int arcWidth,int arcHeight)       | 圆角矩形   |
| fillArc(int x,int y,int width,int height,int startAngle,int arcAngle)            | 实心弧形    |
| fillOval(int x,int y,int width,int height)                                       | 实心椭圆    |
| fillPolygon(int[] xPoints,int[] yPoints,int n) //(xn,yn)坐标全部依次连成n点,首尾闭合| 实心多边形   |
| fillRect(int x,int y,int width,int height)                                       |实心矩形     |
| fillRoundRect(int x,int y,int width,int height,int arcWidth,int arcHeight)       |实心圆角矩形  |  

Graphics2D类是继承Graphics的，Graphics2D类可以分别使用不同的类来表示不同的形状，如Line2D,Recttangle2D等。
绘制指定图形需要先创建并初始化该图形类的对象，这些图形必须是Shape接口的实现类，然后使用Graphics2D类的draw()方法绘制或者使用fill()方法填充。
java.awt.geom包提供如下常用的图形类，这些图形类都实现了Shape接口。
Arc2D、CubicCurve2D、Ellipse2D、Line2D、Point2D、QuadCurve2D、Rectangle2D、RoundRectangle2D
在不同的图形类中有Double和Float两个实现类,以不同的精度构建图形对象，图形太多时建议使用Float类实例绘制，节省空间


实例:绘图
```
public class DrawGraphics extends JFrame{
	public DrawGraphics() {
		super();
		this.setSize(400, 400);//设置窗体大小
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		setContentPane(new DrawPanel());/////////设置窗体面板为绘图面板对象
		this.setTitle("绘制图像");
	}
	
	class DrawPanel extends JPanel{//创建用于绘图的内部面板类
		public void paint(Graphics g) {
			super.paint(g);
			g.drawOval(10, 20, 80, 80);
			g.drawRect(100, 20, 80, 80);
			g.drawLine(10, 120, 380, 120);
			
			Graphics2D g2=(Graphics2D) g;
//			g2.drawRoundRect(190, 20, 80, 60, 20, 10);
			Rectangle2D rect1=new Rectangle2D.Double(190, 20, 80, 60);//创建矩形对象
			g2.draw(rect1);//绘制无填充的矩形对象
			Rectangle2D rect2=new Rectangle2D.Double(280, 20, 80, 60);//创建矩形对象
			g2.fill(rect2);//绘制填充的矩形对象	
			
//java.awt.Shape接口提供了表示一些几何形状对象的定义，其主要实现类有Ellipse2D.Double（椭圆）、Line2D.Double（直线）、Rectangle2D.Double（矩形）、
//			RoundRectangle2D.Double（带圆角的矩形）和Arc2D.Double（孤形）等。
			Shape[] shapes=new Shape[4];//声明图形数组
			shapes[0]=new Rectangle2D.Double(25,165,70,70);//矩形
			shapes[1]=new Rectangle2D.Double(130,150,100,100);
			shapes[2]=new Ellipse2D.Double(130,150,100,100);
			shapes[3]=new Ellipse2D.Double(10,150,100,100);
			for (int i = 0; i < shapes.length; i++) {
				if(i%2==0)
					g2.fill(shapes[i]);
				else
					g2.draw(shapes[i]);
			}
		}
	}
	public static void main(String[] args) {
			new DrawGraphics().setVisible(true);
	}
}
```
![图片](img/javause/59.png)


2.绘图颜色与笔画属性
-----------------------
Color类对颜色属性进行管理,java2D的Graphics2D类的setStroke()方法可以指定笔画属性(线的粗细、虚实、线段端点的形状、风格等)
Color对象构造方法:
```
Color(int r,int g,int b)       //使用RGB值创建颜色对象的构造方法
Color(int rgb)                 //使用RGB 3原色的总和创建颜色对象
用法:
Graphics2D g2=(Graphics2D)g;
g2.setColor(Color.BLUE);
```
常用Color常量:

| 常量名          | 颜色值  | 使用方法           |
| ---------------| --------| ------------------|
| BLACK          | 黑色    | Color.BLAC        |
| WHITE          | 白色    | Color.WHITE       |
| GRAY           | 灰色    | Color.GRAY        |
| GREEN          | 绿色    | Color.GREEN       |
| LIGHT_GRAY     | 浅灰色  | Color.LIGHT_GRAY  |
| CYAN           | 青色    | Color.CYAN        |
| MAGENTA        | 洋红色  | Color.MAGENTA     |
| ORANGE         | 橘黄色  | Color.ORANGE      |
| BLUE           | 蓝色    | Color.BLUE        |
| PINK           | 粉红色  | Color.PINK        |
| DARK_GRAY      | 深灰色  | Color.DARK_GRAY   |
| RED            | 红色    | Color.RED         |
| YELLOW         | 黄色    | Color.YELLOW      |


Graphics绘图默认使用笔画属性为粗细为1个像素的正方形，Graphics2D可调用setStroke(Stroke stroke)方法设置笔画属性。
java.awt.BasicStroke类实现了Stroke接口，其构造方法如下：
```
BasicStroke()
BasicStroke(float width,int cap)
BasicStroke(float width,int cap,int join)
BasicStroke(float width,int cap,int join,float miterlimit)
BasicStroke(float width,int cap,int join,float miterlimit,float[] dash,float dash_phase)
```

参数说明:

| 参数          | 说明                                                             |
| -------------| -----------------------------------------------------------------|
| width        | 笔画宽度，此宽度必须大于或者等于0.0f(0.0f时将设置为当前设备默认宽度)    |
| cap          | 线端点的装饰  可选值:CAP_BUIT,CAP_ROUND,CAP_SQUARE                 |
| join         | 应用在路径线段交汇处的装饰  可选值:JOIN_BEVEL,JOIN_MITER,JOIN_ROUND  |
| miterlimit   | 斜接处的剪切限制，该参数必须大于等于1.0f                             |
| dash         | 表示虚线模式的数组                                                 |
| dash_phase   | 开始虚线模式的偏移量                                               |


3.绘制文本
-----------------
Graphics2D类的drawString()在图像上绘制文本内容。
```
drawString(String str,int x,int y)    //str:绘制的文本字符串，x:水平起始位置  y：垂直起始位置
drawString(String str,float x,float y)
```
java.awt.Font类封装了字体名称、字号、样式等属性，构造方法如下:
```
Font( String name,int style,int size)//name:字体名称  style:字体样式（PLAIN-普通 BOLD-粗体 ITALIC-斜体） size:字体大小
用法:
setFont(Font font)
```
实例:
```
public class DrawString extends JFrame {
	public DrawString() {
		this.setSize(260,180);
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		add(new CanvasPanel());
		this.setTitle("绘制文本信息");
	}
	
	class CanvasPanel extends Canvas{//继承Canvas类成为画布类
		public void paint(Graphics g) {
			super.paint(g);
			Graphics2D g2=(Graphics2D) g;
			g2.setColor(Color.BLUE);
			Font font=new Font("宋体", Font.BOLD, 24);
			g2.setFont(font);
			g2.drawString("静夜思", 80, 40);
			font=new Font("宋体",Font.BOLD|Font.ITALIC,18);
			g2.setFont(font);
			g2.drawString("李白", 130, 70);
			font=new Font("宋体", Font.PLAIN, 14);
			g2.setFont(font);
			g2.drawString("床前明月光，", 40, 100);
			g2.drawString("疑是地上霜。", 120, 100);
			g2.drawString("举头望明月，", 40, 120);
			g2.drawString("低头思故乡。", 120, 120);
		}
	}
	
	
	public static void main(String[] args) {
		DrawString frame=new DrawString();
		frame.setVisible(true);
	}
}
```
![图片](img/javause/60.png)


4.绘制图像
-------------
(1)绘制图像
绘图类不仅可以绘制图形和文本，还可以使用Graphics2D类的drawImage()方法将图片资源绘制到绘图上下文中，而且可以实现图片的缩放、翻转、倾斜、旋转等效果。
```
drawImage(Image img,int x,int y,ImageObserver observer)//在x,y指定位置上将图像对象img指定的图片绘制到上下文 observer：要通知的图像观察者
```

实例：
```
public class DrawImageFrame extends JFrame {
	private Image img=null;
	private JPanel panel=null;
	private Canvas canvas=null;//画布
	public DrawImageFrame() {
		URL imgurl=getClass().getResource("/img/img.jpg");//图片放src下的img文件夹中
		img=Toolkit.getDefaultToolkit().getImage(imgurl);//获取图片资源
		canvas=new CanvasPanel();
		setBounds(200, 160,460, 300);
		setContentPane(getContPanel());
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		setTitle("绘制图片");
	}
	
	private JPanel getContPanel(){
		if(panel==null){
			panel=new JPanel();
			panel.setLayout(new BorderLayout());
			panel.add(canvas,BorderLayout.CENTER);
			panel.repaint();/////////////////////////重绘component的方法  component中己有的图形发生变化后不会立刻显示，须使用repaint方法。
		}
		return panel;
	}
	
	class CanvasPanel extends Canvas{
		public void paint(Graphics g) {
			super.paint(g);
			g.drawImage(img, 0, 0, this);
		}
	}
	public static void main(String[] args) {
		new DrawImageFrame().setVisible(true);
	}
}
```
![图片](img/javause/61.png)

(2)翻转特效
翻转使用Graphics2D类的另一个drawImage()方法
采用源矩形到目标矩形坐标的映射实现翻转
```
drawImage(Image img,int dx1,int dy1,int dx2,int dy2,int sx1,int sy1,int sx2,int sy2,ImageObserver observer)

dx1,dy1,dx2,dy2分别为目标矩形的第1,2个x,y位置；sx1,sy1,sx2,sy2分别为源矩形矩形的第1,2个x,y位置
```
实例:
```
public class DrawImageFrame extends JFrame {
	private int dx1,dy1,dx2,dy2;//目标矩形位置
	private int sx1,sy1,sx2,sy2;//源矩形位置
	private JPanel jPanel1=null;
	private JPanel jPanel2=null;
	private JButton button1=null;
	private JButton button2=null;
	private Image img=null;
	private MyCanvas canvasPanel=new MyCanvas();
	
	public DrawImageFrame() {
		dx2=sx2=650;
		dy2=sy2=650;
		URL imgURL=getClass().getResource("/img/img.jpg");
		img=Toolkit.getDefaultToolkit().getImage(imgURL);
		setBounds(100, 100, 700, 700);
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		setTitle("图片翻转");
		
		if(button1==null){//水平按钮
			button1=new JButton();
			button1.setText("水平翻转");
			button1.addActionListener(new ActionListener() {
				public void actionPerformed(ActionEvent e) {
					sx1=Math.abs(sx1-650);//水平翻转==水平方向坐标减去初始大小
					sx2=Math.abs(sx1-650);
					canvasPanel.repaint();///////////////
				}
			});
		}
		if(button2==null){//垂直按钮
			button2=new JButton();
			button2.setText("垂直翻转");
			button2.addActionListener(new ActionListener() {
				public void actionPerformed(ActionEvent e) {
					sy1=Math.abs(sy1-650);//垂直翻转==垂直方向坐标减去初始大小
					sy2=Math.abs(sy1-650);
					canvasPanel.repaint();///////////////
				}
			});
		}
		if(jPanel2==null){//按钮控制面板
			GridBagConstraints gridBagConstraints=new GridBagConstraints();
			gridBagConstraints.gridx=1;
			gridBagConstraints.gridy=0;
			jPanel2=new JPanel();
			jPanel2.setLayout(new GridBagLayout());
			jPanel2.add(button1,new GridBagConstraints());
			jPanel2.add(button2,gridBagConstraints);
		}
		
		if(jPanel1==null){//内容面板
			jPanel1=new JPanel();
			jPanel1.setLayout(new BorderLayout());
			jPanel1.add(jPanel2,BorderLayout.SOUTH);
			jPanel1.add(canvasPanel,BorderLayout.CENTER);
		}
		setContentPane(jPanel1);
	}
	
	class MyCanvas extends JPanel{
		public void paint(Graphics g) {
			super.paint(g);
			g.drawImage(img, dx1, dy1, dx2, dy2, sx1, sy1, sx2, sy2, this);//绘制图片
		}
	}
	
	public static void main(String[] args) {
		new DrawImageFrame().setVisible(true);
	}
}
```
原图:
![图片](img/javause/62.png)
水平翻转:
![图片](img/javause/63.png)
垂直翻转:
![图片](img/javause/64.png)


(3)放大缩小
Graphics2D的drawImage()方法如下:
```
drawImage(Image img,int x,int y,int width,int height,ImageObserver observer)//显示在x,y位置，并指定宽高
```
实例:
```
public class ImageScaleFrame extends JFrame {
	private Image img=null;
	private JPanel contentJPanel=new JPanel();
	private JSlider jSlider=new JSlider();//滑块
	private int imgWidth,imgHeight;
	private Canvas canvas=new MyCanvas();//画板
	
	public ImageScaleFrame() {
		setBounds(100, 100, 800, 600);
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		setTitle("放大缩小图片");
		URL imgUrl=getClass().getResource("/img/img2.jpg");
		img=Toolkit.getDefaultToolkit().getImage(imgUrl);//获得图片资源
		setContentPane(contentJPanel);//设置面板内容
		
		contentJPanel.setLayout(new BorderLayout());
		contentJPanel.add(jSlider, BorderLayout.SOUTH);
		contentJPanel.add(canvas, BorderLayout.CENTER);
		
		jSlider.setMaximum(1000);
		jSlider.setValue(100);
		jSlider.setMinimum(1);
		jSlider.addChangeListener(new ChangeListener() {
			public void stateChanged(ChangeEvent e) {
				canvas.repaint();//改变后重新画
			}
		});
	}
	
	class MyCanvas extends Canvas{
		public void paint(Graphics g) {
			super.paint(g);
			int newW=0,newH=0;
			imgWidth=img.getWidth(this);
			imgHeight=img.getHeight(this);
			float value=jSlider.getValue();//滑块组件的取值
			newW=(int) (imgWidth*value/100);//图片缩放后大小
			newH=(int) (imgHeight*value/100);
			g.drawImage(img, 0, 0, newW, newH, this);
		}
	}
	
	public static void main(String[] args) {
		new ImageScaleFrame().setVisible(true);
	}
}
```
![图片](img/javause/65.png)
![图片](img/javause/66.png)


(4)倾斜
Graphics2D提供的shear()方法绘制图像的倾斜特效。
```
shear(double shx,double shy)  //shx、shy分别为水平垂直方向倾斜量
```

将放大缩小实例部分代码修改如下:
```
Graphics2D g2=(Graphics2D) g;
g2.shear(0.5, 0);/////////////////////倾斜
g2.drawImage(img, 0, 0, newW, newH, this);
```
![图片](img/javause/67.png)


(5)旋转
Graphics2D类的rotate(double rotate)方法指定图像旋转的弧度进行旋转。
将放大缩小实例部分代码修改如下:
```
Graphics2D g2=(Graphics2D) g;
g2.rotate(Math.toRadians(10));//图片旋转10度         Math.toRadians将角度转化为弧度
g2.drawImage(img, 0, 0, newW, newH, this);
g2.rotate(Math.toRadians(10));//图片旋转10度
g2.drawImage(img, 0, 0, newW, newH, this);
g2.rotate(Math.toRadians(10));//图片旋转10度
g2.drawImage(img, 0, 0, newW, newH, this);
```
![图片](img/javause/68.png)


5.打印
-------------------
(1)打印控制类
PrinterJob类是进行打印控制的主要类。PrinterJob类使用单例模式，用getPrinterJob获得唯一实例，之后再次调用该方法将直接返回该对象的引用。
获取PrinterJob对象:
```
PrinterJob job=PrinterJob.getPrinterJob();
```
设置打印页面:
```
job.setPrinterable(Printerable painter)//painter:接口Printerable实现类的实例对象
```
设置获取打印任务名称:
```
job.setJobName(String jobName)
String printName=job.getJobName()
```
获取打印状态：
用户可以控制取消下一次打印作业
```
boolean cancel=job.isCancelled()  //打印被取消时返回true,否则返回false
```

(2)打印对话框
用户可以使用打印对话框对打印任务进行设置，如打印纸张的大小、是否彩色、打印方向、打印份数等。
PrinterJob类的printDialog()方法将打开"打印"对话框。
```
boolean ok=job.printDialog()        //用户点击打印框"确定"返回true,单击取消返回"false"
```

(3)打印页面
打印页面是打印任务要执行打印的内容如文本、图片、网页和图形等。
打印需要实现java.awt.print.Printable接口。该接口有一个方法如下：
```
print(Graphics graphics,PageFormat pageFormat,int pageInddex)     //返回值可选：PAGE_EXISTS:页面可以打印  NO_SUCH_PAGE:页面不能打印
graphics:绘制打印页面的图形上下文
pageFormat:绘制打印页面的格式属性，如方向大小等
pageInddex:当前打印页的索引
```
可打印区域：纸张除被打印机夹住区域剩余的部分
打印设置对话框可以设置打印区域大小，可以使用pageFormat参数设置打印区域的宽度、高度、打印区域的起始位置坐标。
PageFormat类常用方法:

| 方法                     | 说明                                       |
| -------------------------| ------------------------------------------|
| getWidth()               | 获取打印页面的宽度                          |
| getHeight()              | 获取打印页面的高度                          |
| getImageableWidth()      | 获取可打印区域的宽度                        |
| getImageableHeight()     | 获取可打印区域的高度                        |
| getImageableX()          | 获取可打印区域左上方起始坐标x轴的位置         |
| getImageableY()          | 获取可打印区域左上方起始坐标x轴的位置         |

实例：打印《静夜思》
```
public class PrintDemo extends JFrame {
	public static void main(String[] args) {
		PrinterJob job=PrinterJob.getPrinterJob();//获取打印对象
		if(!job.printDialog())//打开打印对话框
			return;
		job.setPrintable(new Printable() {
			public int print(Graphics graphics, PageFormat pageFormat, int pageIndex)
					throws PrinterException {
				if(pageIndex>0)//////////////////当前打印页索引大于0时不能打印
					return Printable.NO_SUCH_PAGE;
				int x=(int) pageFormat.getImageableX();
				int y=(int) pageFormat.getImageableY();
				Graphics2D  g2=(Graphics2D) graphics;
				g2.setColor(Color.BLUE);
				Font font=new Font("宋体", Font.BOLD, 24);
				g2.setFont(font);
				g2.drawString("静夜思", 80, 40);
				font=new Font("宋体",Font.BOLD|Font.ITALIC,18);
				g2.setFont(font);
				g2.drawString("李白", 130, 70);
				font=new Font("宋体", Font.PLAIN, 14);
				g2.setFont(font);
				g2.drawString("床前明月光，", 40, 100);
				g2.drawString("疑是地上霜。", 120, 100);
				g2.drawString("举头望明月，", 40, 120);
				g2.drawString("低头思故乡。", 120, 120);
				return Printable.PAGE_EXISTS;
			}
		});
		job.setJobName("打印唐诗");
		try {
			job.print();////////////////////打印
		} catch (PrinterException e) {
			e.printStackTrace();
		}
	}
}
```
运行效果:
![图片](img/javause/69.png)
打印效果:
![图片](img/javause/70.png)

6.练习
--------
(1)简单画图程序
```
//画布类
public class DrawPictureCanvas extends Canvas{
	private Image image=null;
	public DrawPictureCanvas() {
		super();
	}
	public void setImage(Image image) {
		this.image = image;
	}
	public void paint(Graphics g) {
		g.drawImage(image, 0, 0, null);
	}
	public void update(Graphics g) {
		paint(g);
	}
}


public class DrawPictureFrame extends JFrame {
	BufferedImage image=new BufferedImage(570, 390, BufferedImage.TYPE_INT_BGR);//创建图像对象
	Graphics gs=image.getGraphics();//获得图像的上下文对象
	Graphics2D g=(Graphics2D) gs;
	DrawPictureCanvas canvas=new DrawPictureCanvas();//创建画布
	Color foreColor=Color.BLUE;//定义前颜色
	Color backgroundColor=Color.WHITE;//定义背景颜色
	boolean rubber=false;//橡皮擦标识变量
	int x=-1,y=-1;//上一次鼠标绘制点的横纵坐标
	
	public DrawPictureFrame() {
		setBounds(100, 100, 570, 390);
		g.setColor(backgroundColor);//用背景颜色设置绘图上下文对象的颜色
		g.fillRect(0, 0, 570, 390);//用背景颜色填充整个画布
		g.setColor(foreColor);//用前景颜色设置绘图上下文对象的颜色
		canvas.setImage(image);
		canvas.setBounds(20, 20, 550, 370);
		getContentPane().add(canvas);//添加画布到窗体
		
//		工具栏
		JToolBar toolBar=new JToolBar();
		toolBar.setFloatable(true);//可以移动
		getContentPane().add(toolBar,BorderLayout.NORTH);//添加到窗体
		JButton line0_Button=new JButton("细线");
		toolBar.add(line0_Button);
		JButton line1_Button=new JButton("粗线");
		toolBar.add(line1_Button);
		JButton line2_Button=new JButton("较粗");
		toolBar.add(line2_Button);
		JButton background_Button=new JButton("背景颜色");
		toolBar.add(background_Button);
		JButton fore_Button=new JButton("前景颜色");
		toolBar.add(fore_Button);
		JButton clear_Button=new JButton("清除");
		toolBar.add(clear_Button);
		final JButton rubber_Button=new JButton("橡皮");
		toolBar.add(rubber_Button);
		JButton exit_Button=new JButton("退出");
		toolBar.add(exit_Button);
		
//为画布添加鼠标拖动事件,在画布上画画
		canvas.addMouseListener(new MouseAdapter() {
			public void mouseReleased(MouseEvent e) {//鼠标释放事件		
				x=-1;//上一次鼠标绘制点的横坐标
				y=-1;
			}
		});
		canvas.addMouseMotionListener(new MouseMotionListener() {
			public void mouseMoved(MouseEvent e) {//设置鼠标形状
				if(rubber){
					setCursor(Cursor.getPredefinedCursor(Cursor.HAND_CURSOR));
				}else{
					setCursor(Cursor.getPredefinedCursor(Cursor.CROSSHAIR_CURSOR));
				}
			}
			public void mouseDragged(MouseEvent e) {
				if(rubber){
					if(x>0&&y>0){
						g.setColor(backgroundColor);//背景色绘制内容----擦除
						g.fillRect(x, y, 10, 10);//擦除鼠标经过的位置
//						g.fillRect(e.getX(), e.getY(), 10, 10);//擦除鼠标经过的位置
					}
					x=e.getX();
					y=e.getY();
				}else{
					if(x>0&&y>0){
						g.drawLine(x, y, e.getX(), e.getY());
					}
					x=e.getX();//上一次鼠标绘制点的横坐标
					y=e.getY();//上一次鼠标绘制点的纵坐标
				}
				canvas.repaint();
			}
		});
		
//	为工具栏添加事件
		line0_Button.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				BasicStroke bs=new BasicStroke(1, BasicStroke.CAP_BUTT,BasicStroke.JOIN_MITER);
				g.setStroke(bs);
			}
		});
		line1_Button.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				BasicStroke bs=new BasicStroke(2, BasicStroke.CAP_BUTT,BasicStroke.JOIN_MITER);
				g.setStroke(bs);
			}
		});
		line2_Button.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				BasicStroke bs=new BasicStroke(4, BasicStroke.CAP_BUTT,BasicStroke.JOIN_MITER);
				g.setStroke(bs);
			}
		});
		background_Button.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				Color bgColor=JColorChooser.showDialog(null, "选择颜色对话框",Color.CYAN);
				if(bgColor!=null){
					backgroundColor=bgColor;
				}
				g.setColor(backgroundColor);
				g.fillRect(0, 0, 570, 390);
				g.setColor(foreColor);
				canvas.repaint();
			}
		});
		fore_Button.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				Color fColor=JColorChooser.showDialog(null, "选择颜色对话框",Color.CYAN);
				if(fColor!=null){
					foreColor=fColor;
				}
				g.setColor(foreColor);
			}
		});
		clear_Button.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				g.setColor(backgroundColor);
				g.fillRect(0, 0, 570, 390);
				g.setColor(foreColor);
				canvas.repaint();
			}
		});
		rubber_Button.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				if(rubber_Button.getText().equals("橡皮")){
					rubber=true;
					rubber_Button.setText("画图");
				}else{
					rubber=false;
					rubber_Button.setText("橡皮");
				}
			}
		});
		exit_Button.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				System.exit(0);
			}
		});
	}
	
	public static void main(String[] args) {
		DrawPictureFrame frame=new DrawPictureFrame();
		frame.setVisible(true);
	}
}
```
![图片](img/javause/71.png)


(2)打印预览
java.swing没有提供打印预览，打印预览可以使用户在打印前查看要打印的内容和样式。
在组件的paint()方法中调用Printable接口的print()方法就可以实现打印预览。
```
public class PrintPanel extends JPanel implements Printable {
	private JButton printButton;
	private JButton previewButton;
	private JPanel controlJPanel;
	private Image img;
	private Dimension size;
	private PrinterJob job;
	private JFrame previewDialog;
	private PageFormat pf;
	private static URL imgUrl=null;
	
	public PrintPanel() {
		setLayout(new BorderLayout());
		setBackground(Color.WHITE);
		add(getControlPanel(),BorderLayout.SOUTH);
		pf=new PageFormat();
		pf.setOrientation(PageFormat.LANDSCAPE);
		job=PrinterJob.getPrinterJob();
		previewDialog=new JFrame("显示预览效果");
		previewDialog.setSize(800, 600);
	}
	
	private void drawPage(Graphics2D g2){
		g2.drawImage(img, 0, 0, this);
	}
	
	protected JButton getPreviewButton(){
		if(previewButton==null){
			previewButton=new JButton();
			previewButton.addActionListener(new ActionListener() {
				public void actionPerformed(ActionEvent e) {
					pf=job.pageDialog(pf);
					MyCanvas canvas=new MyCanvas(pf, img);
					JScrollPane spanel=new JScrollPane(canvas);
					previewDialog.getContentPane().setLayout(new BorderLayout());
					previewDialog.getContentPane().add(spanel);
					previewDialog.setVisible(true);
					canvas.repaint();
				}
			});
			previewButton.setText("打印预览");
		}
		return previewButton;
	}
	
	protected JButton getPrintButton(){
		if(printButton==null){
			printButton=new JButton();
			printButton.addActionListener(new ActionListener() {
				public void actionPerformed(ActionEvent e) {
					job.setPrintable(PrintPanel.this);
					job.setJobName("打印图形");
					try {
						job.print();
					} catch (PrinterException e1) {
						e1.printStackTrace();
					}
				}
			});
			printButton.setText("打印");
		}
		return printButton;
	}
	
	protected JPanel getControlPanel(){
		if(controlJPanel==null){
			controlJPanel=new JPanel();
			controlJPanel.setBorder(new LineBorder(Color.BLUE, 1, false));
			final FlowLayout flowLayout=new FlowLayout();
			flowLayout.setHgap(20);
			controlJPanel.setLayout(flowLayout);
			controlJPanel.add(getPreviewButton());
			controlJPanel.add(getPrintButton());
		}
		return controlJPanel;
	}
	
	@Override
	protected void paintComponent(Graphics g) {
		super.paintComponent(g);
		if(size==null){
			size=getSize();
			img=Toolkit.getDefaultToolkit().getImage(imgUrl);
		}
		Graphics2D g2=(Graphics2D) g;
		drawPage(g2);
	}
	
	public int print(Graphics graphics, PageFormat pageFormat, int pageIndex)
			throws PrinterException {
		if(pageIndex>0)
			return Printable.NO_SUCH_PAGE;
		int x=(int) pageFormat.getImageableX();
		int y=(int) pageFormat.getImageableY();
		Graphics2D g2=(Graphics2D) graphics;
		g2.translate(x, y);
		drawPage(g2);
		return Printable.PAGE_EXISTS;
	}

	public static void main(String[] args) {
		JFrame frame=new JFrame("打印预览");
		frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		frame.setSize(600, 480);
		imgUrl=PrintPanel.class.getResource("/img/img2.jpg");
		PrintPanel canvas=new PrintPanel();
		frame.add(canvas);
		frame.setVisible(true);
	}
}
```
![图片](img/javause/72.png)
![图片](img/javause/73.png)
![图片](img/javause/74.png)


附录：JAVA查询
=======================
1.运算符优先级
--------------------
由高到低如下：
括号：（）
正负号：+，-
一元运算符：++，--，！
乘除：*，/,%
加减:+,-
移位运算：<<,>>,>>>
比较大小:<,>,<=,>=
比较是否相等:==,!=
按位与：&
按位异或：^
按位或：|
逻辑与:&&
逻辑或：||
三元运算符：？：
赋值运算符：=

2.java关键字
----------------
int,public,this,finally,boolean,abstract,continue,float,long,short,throw,throws,return,break,
for,static,new,interface,if,goto,default,byte,do,case,strictfp,package,super,void,try,switch,
else,catch,implements,private,final,class,extends,volatile,while,synchronized,instanceof,char,
protected,import,transient,double

3.键盘keycode列表
--------------------
![图片](img/javause/keycode.jpg)

4.异常处理
---------
异常产生后不做处理程序将会结束，使用try-catch方法或者将异常向上抛出由方法的调用者来处理，进行异常处理后异常语句后面的代码继续执行
原则：
（1）当前方法声明中使用try-catch语句捕获异常
（2）一个方法被覆盖时，覆盖他的方法必须抛出相同的异常或者异常的子类
（3）如果父类抛出多个异常，那么覆盖方法必须抛出那些异常的一个子集，不能抛出新异常
try-catch方法：
```
try{
//程序代码块
}catch(Exceptiontype1 e){
//Exceptiontype1异常处理
}catch(Exceptiontype2 e){
//Exceptiontype2异常处理
}
...
finally{
//程序块，永远会执行
}
```

throws关键字抛出异常:
throws关键字通常应用在声明方法时，用来指定方法可能抛出的异常，多个异常可以用","分隔
使用throws关键字将异常抛给上级调用者后，如果不想处理，可以继续向上抛出，但是最终一定要有处理该异常的语句
eg:
```
//异常处理加不加运行时都不会报错，当出现异常时抛出异常
public class Mytest{
	static int pop(int num1,int num2) throws ArithmeticException{
		return num1/num2;
	}
	public static void main(String[] args) {
		try{
			int result=pop(1,0);
			System.out.print(result);
		}catch(ArithmeticException e){
			//e.printStackTrace();
			System.out.println("除数不能为0!");//除数不能为0!
		}
	}
}
```

自定义异常：
（1）创建自定义异常类，必须继承自Exception类
（2）在方法中通过throw(区别于throws)关键字抛出异常对象
（3）当前抛出异常的方法中处理可以使用try-catch语句捕获并处理，否则在方法声明处通过throws关键字指明要抛出给方法调用者的异常，继续进行下一步操作
（4）在出现异常方法的调用者中捕获并处理异常
实例:
```
public class MyException extends Exception {
	String msg;
	public MyException(String errorMsg){
		msg=errorMsg;
	}
	public String getMessage(){//覆盖getMessage()方法
		return msg;
	}
}


public class Mytest{
	static int pop(int num1,int num2) throws MyException{
		if(num2<0){
			throw new MyException("除数不能<0");
		}
		return num1/num2;
	}
	public static void main(String[] args) {
		try{
			int result=pop(1,-1);
			System.out.print(result);
		}catch(MyException e){
			System.out.println(e.getMessage());//////输出异常信息
		}catch(ArithmeticException e){
			//e.printStackTrace();
			System.out.println("除数不能为0!");//除数不能为0!
		}catch(Exception e){
			System.out.println("发生了其他异常");
		}
	}
}
```


常见异常列表：
```
ClassCastException----------------------------类型转换异常类
ClassNotFoundException------------------------未找到相应类异常
ArithmeticException---------------------------算术异常类
ArrayIndexOutOfBoundsException----------------数组下标越界异常类
ArrayStoreException---------------------------数组中包含不兼容的值异常类
SQLException----------------------------------操作数据库异常类
NullPointerException-------------------------空指针异常类
NoSuchFiledException--------------------------字节未找到异常类
NoSuchMethodException-------------------------方法未找到异常类
NumberFormatException-------------------------字符串转换为数字异常类
NegativeArraySizeException--------------------数组元素个数为负数异常
StringIndexOutOfBoundsException---------------字符串索引超出范围异常
IOException-----------------------------------输入输出异常
IllegalAccessException------------------------不允许访问某类异常
InstantiationException------------------------使用newInstance方法创建一个类的实例，而指定类无法被实例化时抛出异常
EOFException----------------------------------文件结束异常
FileNotFoundException-------------------------文件未找到异常
```