title: Struts 2框架详解
date: 2016-03-14 10:06:50
categories: "Struts 2"
tags: ["Struts 2","Web框架"]
---
主要内容：
<!--more-->
第一章 Struts2介绍
===================
著名的SSH三大框架分别为：表现层(Struts)、业务逻辑层(Spring),持久化层(Hibernate)。
Struts 2是Struts的下一代产品，是在 struts 1和WebWork的技术基础上进行了合并的全新的Struts 2框架。其全新的Struts 2的体系结构与Struts 1的体系结构差别巨大。Struts 2以WebWork为核心，采用拦截器的机制来处理用户的请求，这样的设计也使得业务逻辑控制器能够与ServletAPI完全脱离开，所以Struts 2可以理解为WebWork的更新产品。虽然从Struts 1到Struts 2有着太大的变化，但是相对于WebWork，Struts 2的变化很小。
MVC模型:
![img](img/structs2/1.png)

Struts2之MVC模型：
控制器：FilterDispatcher,是一个Sevelet过滤器，请求到来时经过FilterDispatcher过滤，FilterDispatcher决定该由哪个Action处理当前请求。
模型：Action,功能：调用业务逻辑处理请求，进行数据传递。Action处理完请求会返回一个逻辑视图。
视图:除jsp页面外，还可以是Velocity、FreeMarker、Tiles等多种视图资源。视图组件接收到Action返回的逻辑视图会寻找对应物理视图资源并返回给客户端。
Struts2前端控制器模式架构图：
![img](img/structs2/8.png)
1.JSP提交以".action"结尾的请求
2.FilterDispatcher接收请求并调用Action处理该请求
3.Action处理完毕返回一个逻辑视图
4.FilterDispatcher根据Action返回的逻辑视图创建物理视图
5.将物理视图返回给页面

Struts2页面控制器模式架构图：
![img](img/structs2/9.png)
1.JSP页面通过<s:action/>标签直接请求某个具体的Action
2.Action处理完毕返回一个逻辑视图
3.FilterDispatcher根据Action返回的逻辑视图创建物理视图
4.将物理视图放回给客户端


Struts2的工作原理:
![img](img/structs2/2.png)
一个请求在Struts2框架中的处理大概分为以下几个步骤 
1 客户端初始化一个指向Servlet容器（例如Tomcat）的请求 
2 这个请求经过一系列的过滤器（Filter）（这些过滤器中有一个叫做ActionContextCleanUp的可选过滤器，这个过滤器对于Struts2和其他框架的集成很有帮助，例如：SiteMesh Plugin）
3 接着FilterDispatcher被调用，FilterDispatcher询问ActionMapper来决定这个请是否需要调用某个Action 
4 如果ActionMapper决定需要调用某个Action，FilterDispatcher把请求的处理交给ActionProxy 
5 ActionProxy通过Configuration Manager询问框架的配置文件，找到需要调用的Action类 
6 ActionProxy创建一个ActionInvocation的实例。 
7 ActionInvocation实例使用命名模式来调用，在调用Action的过程前后，涉及到相关拦截器（Intercepter）的调用。 
8 一旦Action执行完毕，ActionInvocation负责根据struts.xml中的配置找到对应的返回结果。返回结果通常是（但不总是，也可 能是另外的一个Action链）一个需要被表示的JSP或者FreeMarker的模版。在表示的过程中可以使用Struts2 框架中继承的标签。在这个过程中需要涉及到ActionMapper


第二章 搭建Structs2应用
========================
1.准备工作
------------
所需环境:
JDK,Tomcat,Struts2
这里只介绍Struts2下载
官网下载：http://struts.apache.org/download
下载文件：struts-2.3.24.1-all.zip

程序开发流程：
(1)引入Struts2运行库
(2)配置Web.xml文件
(3)编写Action类
(4)配置struts.xml文件
(5)编写视图资源

2.图解流程
------------
Http请求流转流程：
![img](img/structs2/10.png)
配置文件连接点详述：
![img](img/structs2/11.png)

3.Struts2自带的项目
-------------------
(1) struts-2.3.24.1-all.zip解压目录分析
![img](img/structs2/3.png)
apps:示例应用
docs:帮助文档
lib:Struts2框架的核心类库及第三方插件类库
src:Struts2框架的全部源代码

(2)搭建步骤
A.引入Struts2工程需要的运行库文件
B.创建配置web.xml文件
C.创建一个Action类
D.创建配置struts.xml文件

找到apps下的struts2-blank.war文件发布到Tomcat上。
备注:war格式的文件，这个文件格式可能并不常见，这个通常是tomcat程序发布时候的自解压文件。这个文件可以用解压软件打开，也可以放到tomcat的发布目录，服务器启动是时候war文件会自动解压。
这里直接点击struts2-blank.war右键打开方式winrar，解压后目录：
![img](img/structs2/4.png)
![img](img/structs2/5.png)
![img](img/structs2/6.png)
![img](img/structs2/7.png)
jsp：放置工程中jsp文件
classes:放置所有编译后的文件及各个配置文件
lib:放置工程运行所需类库文件
src:放置java源码文件
lib中已经有需要的包，web.xml也有。
struts2-blank项目直接访问如下：
![img](img/structs2/12.png)


4.手动搭建Struts2程序
-----------------------
编写Action类：
(1)要包含与请求参数对应的属性以及setter、getter方法
(2)Action类增加一个execute方法，Struts2框架默认会执行，该方法不做业务逻辑处理，而是调用其他业务逻辑来完成这部分工作。
(3)Action类返回一个标准的字符串，该字符串是一个逻辑视图名，该视图名对应实际的物理视图。
编写如下:
```
public class UserAction{
	private String username;
	private String password;
	
	public String getPassword(){
		return password;
	}
	
	public void setPassword(String password){
		this.password=password;
	}
	
	public String getUsername(){
		return username;
	}
	
	public void setUsername(String username){
		this.username=username;
	}
	
	public String execute() {
		if(username.equals("zhang")&&password.equals("123456")){
			return "success";
		}else{
			return "error";
		}
	}
}
```
编译成UserAction.class放在WEB-INF/classes下。

配置WEB-INF/struts.xml
```
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE struts PUBLIC
	"-//Apache Software Foundation//DTD Struts Configuration 2.3//EN"
	"http://struts.apache.org/dtds/struts-2.3.dtd">

<struts>
    <package name="default" namespace="/" extends="struts-default">
        <action name="login" class="com.zhang.UserAction">
                <result name="success">/jsp/success.jsp</result>
                <result name="error">/jsp/error.jsp</result>
        </action>
    </package>
</struts>
```
程序发布运行时会自动在WEB-INF/classes下找到加载structs.xml
<action... >标签中两个属性name和class,name:用户URL请求的action名，
如用户请求如果为：http://localhost:8080/login.action则name为login，class表示请求实现的类。
<result...>标签定义逻辑视图与物理视图之间的映射，Action返回"success"则success.jsp处理；返回error则error.jsp处理。

编写视图资源:
登录页面
index.jsp
```
<%@ page language="java" import="java.util.*" pageEncoding="utf-8"%>
<%
String path = request.getContextPath();
String basePath = request.getScheme()+"://"+request.getServerName()+":"+request.getServerPort()+path+"/";
%>

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html>
  <head>
  </head>
  
  <body>
    <form action="<%=path %>/new/login.action" method="post">
    	用户名：<input type="text" name="username"><br>
    	密码：<input type="text" name="password"><br>
    	<input type="submit" value="提交">
    </form>
  </body>
</html>
```
success.jsp
```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html>
  <head>
  </head>
  
  <body>
   	登陆成功！
  </body>
</html>
```

fail.jsp
```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html>
  <head>
  </head>
  
  <body>
    登录失败！
  </body>
</html>
```



3.使用Myeclipse开发Structs2程序
-------------------
(1)新建Web工程
File->"new"->"Project"->"Web Project"或者
File->"new"->"Project"->"MyEcipse"->"java Enterprise Projects"->"Web Project"

(2)加载struts2类库文件
项目名右键->MyEclipse->Project Facets[Capabilities]->Install Apache struts(2.x) Facet  选择版本finish即可。

(3)项目直接运行
第二步会自动加载库和生成对应文件
项目结构图如下：
![img](img/structs2/13.png)
直接布到tomcat下如下：
![img](img/structs2/14.png)

(4)修改成登录项目
项目结构图如下：
![img](img/structs2/15.png)

对应文件信息：
web.xml
```
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://java.sun.com/xml/ns/javaee" xsi:schemaLocation="http://java.sun.com/xml/ns/javaee http://java.sun.com/xml/ns/javaee/web-app_3_0.xsd" version="3.0">
  <display-name>MyWeb</display-name>
  <filter>
    <filter-name>struts2</filter-name>
    <filter-class>org.apache.struts2.dispatcher.ng.filter.StrutsPrepareAndExecuteFilter</filter-class>
  </filter>
  <filter-mapping>
    <filter-name>struts2</filter-name>
    <url-pattern>/*</url-pattern>
  </filter-mapping>
</web-app>
```
struts.xml
```
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE struts PUBLIC "-//Apache Software Foundation//DTD Struts Configuration 2.1//EN" "http://struts.apache.org/dtds/struts-2.1.dtd">
<struts>
	<package name="default" extends="struts-default">
		<action name="login" class="com.zhang.struts2.User">
		<result name="success">success.jsp</result>
		<result name="fail">fail.jsp</result>
		</action>
	</package>
</struts>
```
User.java
```
package com.zhang.struts2;

import com.opensymphony.xwork2.ActionSupport;

public class User extends ActionSupport {
	 private String name;
	 private String password;
	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}
	public String getPassword() {
		return password;
	}
	public void setPassword(String password) {
		this.password = password;
	}
	 @Override
	public String execute() throws Exception {
		if(name.equals("zhang")&&"123456".equals(password)){
			return "success";
		}
		return "fail";
	}	
}
```
index.jsp
```
<%@ page language="java" import="java.util.*" pageEncoding="utf-8"%>
<%@ taglib prefix="s" uri="/struts-tags" %>
<%
String path = request.getContextPath();
String basePath = request.getScheme()+"://"+request.getServerName()+":"+request.getServerPort()+path+"/";
%>

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html>
  <head>
    <base href="<%=basePath%>"> 
    <title>登录页面</title>
  </head>
  
  <body>
    <s:form action="login">
    <s:textfield name="name" label="用户名"></s:textfield>
    <s:textfield name="password" label="密码"></s:textfield>
    <s:submit value="确定"></s:submit>
    </s:form>
  </body>
</html>
```
success.jsp
```
<%@ page language="java" import="java.util.*" pageEncoding="utf-8"%>
<%@ taglib prefix="s" uri="/struts-tags" %>
<%
String path = request.getContextPath();
String basePath = request.getScheme()+"://"+request.getServerName()+":"+request.getServerPort()+path+"/";
%>

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html>
  <head>
    <base href="<%=basePath%>">
    <title>登录成功</title>
  </head>
  
  <body>
    <p>登录成功!欢迎您:<s:property value="name"/></p>
  </body>
</html>
```
fail.jsp
```
<%@ page language="java" import="java.util.*" pageEncoding="utf-8"%>
<%
String path = request.getContextPath();
String basePath = request.getScheme()+"://"+request.getServerName()+":"+request.getServerPort()+path+"/";
%>

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html>
  <head>
    <base href="<%=basePath%>">
    <title>失败页面</title>
  </head>
  
  <body>
    <p>登录失败!</p>
  </body>
</html>
```

运行效果:
![img](img/structs2/16.png)
输入zhang 123456时登录成功，其他登录失败！



第三章 Struts2核心基础
=====================
1.Struts2模型
--------------------
(1)抽象模型
![img](img/structs2/17.png)
Struts2执行流程:
A.Struts2收集到HTTP请求，交由FilterDispatcher处理
B.FilterDispatcher对请求解析得到Action名称，从struts.xml配置文件中获得该Action配置信息并调用该Action
C.系统获得Action配置信息后，会记录该Action所配置的拦截信息，并在此Action执行的前后调用这些拦截器
D.当Action执行结束后会返回一个结果类型，由此结果类型映射到视图界面，整个流程执行完毕。

(2)拦截器
![img](img/structs2/18.png)


2.Action应用详解
-----------------
(1)类的使用
通常Action都会继承ActionSupport，因为ActionSupport帮助我们实现了一部分常用功能，简化代码，提高效率。
ActionSupport实现的接口：
Action:提供SUCCESS,ERROR,NONE,INPUT,LOGIN这5个常量作为返回结果并提供了execute()方法
Validateable:提供了validate()方法用于校验表单数据
ValidationAware:定义了一些方法用来对Action执行过程中的信息进行处理，方法如下：

|  方法                                | 描述                                                        |
| -------------------------------------| -----------------------------------------------------------|
| void addActionError(String anErrorMessage)| 增加一个Action级别的错误信息到对应Action |
| void addActionMessage(String aMessage)| 增加一个Action级别的信息到该Action|
| void addFieldError(String fieldName,String errorMessage)| 增加一个错误信息到指定字段|
| Collection getActionErrors()| 获得Action中用于装载Action级别错误信息字符串的集合|
| Collection getActionMessages()| 获得Action中用于装载Action级别信息字符串的集合|
| Map getFieldErrors()| 获取与本Action相关联的指定字段错误信息|
| boolean hasActionErrors()| 检查是否存在Action级别的错误信息|
| boolean hasActionMessages()| 检查是否存在Action级别的信息|
| boolean hasErrors()| 检查是否存在Action级别的信息或者字段错误信息|
| boolean hasFieldErrors()| 检查是否存在与本Action相关联的特定字段错误信息|
| void setActionErrors(Collection errorMessages)| 设置用于封装Action级别错误信息字符串的集合|
| void setActionMessages(Collection messages)| 设置装载Action级别信息字符串的集合|
| void setFiledErrors(Map errorMap)| 设置字段错误信息映射|

LocalProvider:Struts2中当前用户语言、地区信息被封装在java.util.Locale类中，通过com.opensymphony.xwork.LocaleProvider接口中的getLocale方法来获取Local中的语言/地区信息。
TextProvider:提供了一系列getText()方法获取对应的国际化信息资源，在Struts2中国际化资源都是以key=value表示，方法通过key找到符合的value


(2)Action传值方式
A.字段驱动
```
public class User(){
	private String name;
	private String password;
	public void setName(String name){
		this.name=name;
	}
...
}
```
如上定义两个字段name和password,这这个字段分别和登录表单的用户名密码表单域对应，登录页面提交的表单数据被映射到对应的Action字段，由此Action得到传入数据。

B.模型驱动
User.java
```
public class User{
	 private String name;
	 private String password;
	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}
	public String getPassword() {
		return password;
	}
	public void setPassword(String password) {
		this.password = password;
	}	
}
```
UserAction.java
```
public class UserAction extends ActionSupport {
	private User user;
	 public User getUser() {
		return user;
	}
	public void setUser(User user) {
		this.user = user;
	}
	@Override
	public String execute() throws Exception {
		if(user.getName().equals("zhang")&&"123456".equals(user.getPassword())){
			return "success";
		}
		return "fail";
	}
}
```
struts.xml
```
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE struts PUBLIC "-//Apache Software Foundation//DTD Struts Configuration 2.1//EN" "http://struts.apache.org/dtds/struts-2.1.dtd">
<struts>
	<package name="default" extends="struts-default">
		<action name="login" class="com.zhang.struts2.UserAction">
		<result name="success">success.jsp</result>
		<result name="fail">fail.jsp</result>
		</action>
	</package>
</struts>    
```
index.jsp
```
<%@ page language="java" import="java.util.*" pageEncoding="utf-8"%>
<%@ taglib prefix="s" uri="/struts-tags" %>
<%
String path = request.getContextPath();
String basePath = request.getScheme()+"://"+request.getServerName()+":"+request.getServerPort()+path+"/";
%>

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html>
  <head>
    <base href="<%=basePath%>"> 
    <title>登录页面</title>
  </head>
  
  <body>
    <s:form action="login">
    <s:textfield name="user.name" label="用户名"></s:textfield>
    <s:textfield name="user.password" label="密码"></s:textfield>
    <s:submit value="确定"></s:submit>
    </s:form>
  </body>
</html>
```
success.jsp
```
<%@ page language="java" import="java.util.*" pageEncoding="utf-8"%>
<%@ taglib prefix="s" uri="/struts-tags" %>
<%
String path = request.getContextPath();
String basePath = request.getScheme()+"://"+request.getServerName()+":"+request.getServerPort()+path+"/";
%>

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html>
  <head>
    <base href="<%=basePath%>">
    <title>登录成功</title>
  </head>
  
  <body>
    <p>登录成功!欢迎您:<s:property value="user.name"/></p>
  </body>
</html>
```
模型驱动传值JSP页面取值时必须"模型对象名.属性名"

(3)访问Servlet API
Struts2的Action不依赖于任何Servelet API,好处是可以脱离Web容器测试Action。
但是我们要用到request对象或者session对象时则需要Servelet API。
Struts2提供了两种方式访问Servelet API：ActionContext和*Aware接口
A.ActionContext
ActionContext类常用方法与功能

| 方法                         | 功能                                                  |
| -----------------------------| -----------------------------------------------------|
| ActionContext getContext()   | 获取系统的ActionContext实例                            |
| Map getSession() | 返回一个Map对象，该对象存入HttpSession实例 |
| void setSession(Map session)| 直接传入一个Map实例，将实例中的key、value对应转换成session的属性名和属性值| 
| Map getApplication()| 返回一个Map对象，该对象存入ServletContext实例|
| void setApplication(Map application)| 直接传入一个Map实例，将实例中的key、value对应转换成application的属性名与属性值|
| Map getParameters()| 获得所有的请求参数，类似于调用HttpSeveletRequest对象的getParameterMap方法|

ServletActionContext常用方法与功能
| 方法                         | 功能                                                  |
| -----------------------------| -----------------------------------------------------|
| HttpServletRequest getRequest()| 获得Web应用的HttpServletRequest对象|
| HttpServletResponse getResponse()| 获得Web应用的HttpServletResponse对象|
| ServletContext getServletContext()| 获得Web应用的ServletContext对象|

B.*Aware接口

| 实现接口名称| 获得Servlet对象的方法|
| ----------| --------------------|
| ApplicationWare| void setApplication(Map application)|
| CookiesAware | void setCookiesMap(Map cookies)|
| RequestAware| void setRequest(Map request)|
| ServletRequestAware| void setServletRequest(HttpServletRequest request)|
| ServletResponseAware| void setServletResponse(HttpServletResponse response)|
| SessionAware| void setSession(Map session)|
 
(4)Action返回字符串结果原则:
A.返回结必须是字符串类型
B.除非返回结果对应相同的物理视图资源，否则返回结果不可使用同一字符串
C.对于继承了ActionSupport类的Action来说，可以用其中的5个常量代替字符串:SUCCESS,ERROR,NONE,INPUT,LOGIN

(5)Action中定义多个方法
自定义方法实现功能时，可以随意命名，但是必须返回类型为String
eg:
```
public String login() {
	if(user.getName().equals("zhang")&&"123456".equals(user.getPassword())){
		return "loginSuccess";
	}
	return "loginFail";
}
public String regist(){
	if(user.getName().equals("")&&"".equals(user.getPassword())){
		return "registError";
	}
	return "registSuccess";
}
```

3.结果类型与视图
----------------
Struts2框架通过Action返回字符串在struts.xml中将逻辑视图与物理视图建立一个映射关系。
(1)result
Struts.xml
```
<action name="Action名称" class"Action类路径" method="方法名">//这里的方法名为自己在Action中定义的，不写的话默认执行execute方法
	<result name="逻辑视图名称" type="结果类型">//逻辑视图名称--Action返回的字符串 name不写时默认success,type默认dispatcher
		<param name="参数名称">参数值</param>
	</result>
</action>
```
struts-default.xml(struts_core_...包下)部分代码
```
!-- 结果类型的种类-->      
<result-types>      
<result-type name="chain" class="com.opensymphony.xwork2.ActionChainResult"/>      
<result-type name="dispatcher" class="org.apache.struts2.dispatcher.ServletDispatcherResult" default="true"/>      
<result-type name="freemarker" class="org.apache.struts2.views.freemarker.FreemarkerResult"/>      
<result-type name="httpheader" class="org.apache.struts2.dispatcher.HttpHeaderResult"/>      
<result-type name="redirect" class="org.apache.struts2.dispatcher.ServletRedirectResult"/>      
<result-type name="redirectAction" class="org.apache.struts2.dispatcher.ServletActionRedirectResult"/>      
<result-type name="stream" class="org.apache.struts2.dispatcher.StreamResult"/>      
<result-type name="velocity" class="org.apache.struts2.dispatcher.VelocityResult"/>      
<result-type name="xslt" class="org.apache.struts2.views.xslt.XSLTResult"/>      
<result-type name="plainText" class="org.apache.struts2.dispatcher.PlainTextResult" />      
<result-type name="redirect-action" class="org.apache.struts2.dispatcher.ServletActionRedirectResult"/>      
<result-type name="plaintext" class="org.apache.struts2.dispatcher.PlainTextResult" />      
</result-types>
```
返回类型功能：

| 返回类型名称| 功能描述|
| ----------| --------|
| chain | 将两个连续执行的Action串联，通过前一个Action的getXXX()方法与后一个Action的setXXX()方法完成Action值的传递|
| dispatcher | 返回结果对应视图为JSP,没有配置返回结果时此类型被使用|
| freemarker | 返回结果对应视图为Freemarker视图模板|
| httpheader | 返回HTTP头信息，控制特殊HTTP行为|
| redirect | 重定向到另一个JSP页面|
| redirectAction | 重定向到另一个Action|
| stream | 向浏览器返回一个数据流，一般用于文件下载|
| velocity | 返回结果对应视图Velocity视图模板|
| xslt | Action执行完毕属性信息进行交换 |
| plainText| 显示某个页面的原始代码的结果类型|
| redirect-action| 作用同redirectAction|
 
(2)dispatcher(请求转发)
dispatcher返回类型可以设置两个参数：
location:指定具体物理视图信息(具体的JSP页面)
parse(默认true):对结果配置信息中的OGNL表达式运算替换原来OGNL表达式，这样可以在配置结果时使用动态页面和动态URL，如:my.jsp?name=${name}实际替换为my.jsp?name=zhang.没有特殊需要必须将自动解析OGNL表达式功能关闭，因为Struts2的<s:property>标签获得参数时候也会利用OGNL获得对应参数。
结果类型dispatcher时注意：
请求转发只能将请求转发到同一个Web应用；
利用请求转发浏览器地址栏不会变化；
利用请求转发调用者与被调用者之间共享相同的request和response对象，属于同一个访问请求和响应。

(3)redirect(重定向)
重定向不仅可以指定到一个Web应用，还能够指定到任何JSP资源；
重定向访问结束时地址栏发生变化；
重定向的调用者和被调用者使用各自的request和response对象，属于两个独立的访问请求和响应过程。

重定向与请求转发区别：
重定向需要两次请求完成的工作请求转发一次请求就可以完成，如此请求转发不会造成数据丢失而重定向会失去第一次请求中的数据。

(4)chain(Action链)
Action链是通过chain拦截器实现的，用一个在Action执行完毕返回结果直接跳转到另一个Action的时候，其可以实现两个Action的数据共享。
Action链中Action可以共享数据是因为处于Action链中的所有Action都共享一个值栈(临时储存中间数据)，当Action1执行时会将自身的信息压人值栈，当Action2执行时也会，Action2执行过程中需要Action1的信息则会到值栈获取。
Action链必须为第二个Action及后面的所有Action都配置chain拦截器才能正常工作。
Action链原理图:
![img](img/structs2/19.png)

(5)视图简介
Struts2支持视图多种多样，除JSP页面外还有Velocity和Freemarker模板视图、XSLT转换、JsperReport等。
实例：
```
<action name="test" class="com.zhang.Test">
	<result type="freemarker">test.ftl</result>
</action>
```

4.struts.properties
----------------------
struts.properties定义了Struts2程序运行所必须的常量信息，能够修改Struts2框架的一些默认行为方式，该文件包含一系列key-value键值对，每个key就是一个Struts2属性名，key对应value就是一个struts2属性值，如果一个key对应多个属性值时需要用英文逗号分开。
所有在struts.xml文件中通过<constant></constant>标签进行配置,也可以在web.xml文件中通过<init-param></init-param>标签进行配置。
由于Struts2已经为我们提供了默认配置文件default.properties,可以不需要struts.properties.
需要修改默认信息时可以在工程的WEB-INF/classes文件夹下建立一个struts.properties文件，将修改信息配置到文件中，新配置信息会覆盖系统默认配置信息。
几个常用常量配置信息如下:

| 配置信息内容     | 默认值   |  功能描述                 |
| ---------------| ---------| -------------------------|
| struts.il8n.encoding| UTF-8| 指定默认编码集，对于请求参数带有中文情况，可以设置GBK或者GB2312|
| struts.il8n.reload | false | 是否每次HTTP请求到达时，都重新加载国际化资源文件|
| struts.configuration.xml.reload| false| 当struts.xml改动后是否重新加载该文件|
| struts.devMode| false| 指定是否使用Struts2框架作为开发模式，开发模式下会在运行错误时得到更多的错误信息|
| Struts.serve.static.browserCache| true| 设置浏览器是否缓存静态页面|
| struts.action.extension| action| 指定后缀为.action形式的请求可以被Struts2处理，可以配置多个请求配置如.do、.struts2等，配置时多个后缀名需要用逗号隔开|
| struts.url.http.port| 8080| 配置服务器运行时的端口号|

5.struts.xml
---------------
(1)构成元素
Struts2框架根据struts.xml文件配置信息知道要处理哪些程序，struts.xml配置元素功能如下:

| 配置元素 | 功能描述 |
| --------| --------|
| include | 引入其他xml配置文件|
| constant| 配置常量信息|
| bean| 由容器创建并注入的组件|
| package| 包含一系列Action及拦截器配置信息，并对其进行统一管理|
| default-action-ref| 配置默认Action|
| default-class-ref| 配置默认class|
| default-interceptor-ref| 配置默认拦截器，对包范围内所有Action有效|
| global-results| 配置全局结果集，对包范围内所有Action有效|
| global-exception-mappings| 配置全局异常映射，对包范围内所有Action有效|
| result-types| 配置自定义返回结果类型|
| interceptors| 包含一系列拦截器配置信息|
| action| 包含与Action操作相关的一系列配置信息|
| exeception-mapping| 配置异常映射，Action范围内有效|
| interceptor-ref| 配置Action应用的拦截器|
| result| 配置Action的结果映射|

(2)<include>
工程浩大时需要将一个struts.xml按照一定的规则划分为多个配置文件，再由<include>标签引入其他配置文件
eg:
struts.xml
```
...
<struts>
<include file="goods.xml">//商品
<include file="users.xml">//用户
<include file="order.xml">//订单
</struts>
...
```
users.xml
```
<struts>
	<package name="zhang" extends="struts-default">
	<action name="login" class="com.zhang.struts2.User">
		<result>...
	</action>
	</package>
</struts>
```

(3)<constant>
由于需要修改的常量信息不多，所以比起在struts.properties或者web.xml中配置更推荐在struts.xml中配置
eg:
```
<struts>
<!-- 设置编码格式 -->
<constant name="struts.il8n.encoding" value="GB2312"/>
</struts>
```

(4)<package>
为了增加系统可维护性，包提供了将多个action组织为一个模块的方式，Struts2框架通过package来管理action、result、interceptor、interceptor-stack等配置信息，一个package可以拓展另外一个package。属性如下:

| 属性 | 是否必须 | 描述 |
| ----| --------| -----|
| name| 是| 包名，作为其他包引用本包的标记,包名必须唯一,一个struts.xml不能出现两个同名的包|
| extends| 否| 设置本包继承其他包，继承父包后会包含父包的所有配置如action、result等，父包必须在子包前定义，struts-default.xml包配置了Struts2的所有内置结果类型、内置拦截器等信息，所以经常继承之后就不用声明直接使用那些内置信息了|
| namespace| 否| 设置包的命名空间，实际是在包基础上对Action的进一步划分，可以解决Action重名问题(不同命名空间可以使用相同Action名)|
| abstract| 否| 设置为抽象包,包被设置为抽象包时不能包含Action配置信息，可以被其他包继承|

namespace补充:
****************************如下有待补充
使用命名空间URL将改变
运行如下正确:
```
struts.xml:
<struts>
	<package name="mySpace" namespace="/" extends="struts-default">
		<action name="login" class="com.zhang.struts2.UserAction" method="login">
		<result name="success">success.jsp</result>
		<result name="fail">fail.jsp</result>
		</action>
	</package>
</struts>  

index.jsp:
  <body>
    <s:form action="login" method="post">
    <s:textfield name="user.name" label="用户名"></s:textfield>
    <s:textfield name="user.password" label="密码"></s:textfield>
    <s:submit value="确定"></s:submit>
    </s:form>
  </body>  
或者
   <s:form action="login" namespace="/" method="post">
或者
	<s:form action="login" namespace="/space" method="post">
或者
   <s:form action="login!login" namespace="/space" method="post"> //login!login---Action名称！方法名称
```
运行如下错误:
```
struts.xml:
<struts>
	<package name="mySpace" namespace="/space" extends="struts-default">
		<action name="login" class="com.zhang.struts2.UserAction" method="login">
		<result name="success">success.jsp</result>
		<result name="fail">fail.jsp</result>
		</action>
	</package>
</struts>    

index.jsp:
<body>
    <s:form action="login" namespace="/space" method="post">
    <s:textfield name="user.name" label="用户名"></s:textfield>
    <s:textfield name="user.password" label="密码"></s:textfield>
    <s:submit value="确定"></s:submit>
    </s:form>
  </body>
```

(5)<action>与<result>
<action>标签

| 属性名 | 是否必须 | 功能描述 |
| ------| --------| --------|
| name | 是 | 请求的Action名称|
| class| 否 | Action处理类对应的具体路径|
| method| 否| 指定Action中的方法名,没有设置是会默认调用execute方法|
| converter| 否| 指定Action使用的类型转换器|

<result>标签

| 属性名 | 是否必须 | 功能描述 |
| ------| --------| --------|
| name | 否| 对应Action返回逻辑视图的名称，默认为success|
| type | 否| 返回结果类型，默认为dispatcher|

通配符使用：
原始代码如下:
```
<struts>
	<package name="mySpace" namespace="/" extends="struts-default">
		<action name="login" class="com.zhang.struts2.UserAction" method="login">
		<result name="st1">st1.jsp</result>
		<result name="st2">st2.jsp</result>
		<result name="st3">st3.jsp</result>
		...
		</action>
	</package>
</struts>    
```
大量的result语句，使用通配符如下：
```
Test.java
public class Test extends ActionSupport{
	public String st1(){
			return st1;	
		}
	public String st2(){
			return st2;	
		}
	public String st3(){
			return st3;	
		}
}

struts.xml
<struts>
	<package name="mySpace" namespace="/" extends="struts-default">
		<action name="st*" class="com.zhang.struts2.Test" method="st{1}">
		<!--  动态获取返回结果，其中"{1}"取得的是"*"的内容 -->
		<result name="st{1}">st{1}.jsp</result>
		</action>
	</package>
</struts>    
```
缺陷:Action请求名称为"st*"则方法名称和逻辑视图名称必须以st开头!
每个人就根据需要选择是否使用!

(6)<exception-mapping>与<global-exception-mappings>
用来配置发生异常时对应的视图信息！一个是Action范围内的，一个是包范围内的。
属性:

| 属性名称| 是否必须 | 功能描述|
| -------| --------| -------|
| name| 否| 用来标识该异常配置信息|
| result| 是| 指定发生异常时显示的视图信息|
| exception| 是| 指定异常类型|

(7)<default-class-ref>
配置时没有为某个Action指定class时，系统将自动引用<default-class-ref>标签指定的类
```
<struts>
	<package name="mySpace" namespace="/" extends="struts-default">
		<!-- 指定默认class为Hello -->
		<default-class-ref class="com.zhang.struts2.Hello">
		<action name="st1">
			<result>index.jsp</result>
		</action>
		<action name="st2">
			<result>index.jsp</result>
		</action>
	</package>
</struts>    
```
st1和st2都没有指定class信息，当浏览器输入http://localhost:8080/MyWeb/st1.action与http://localhost:8080/MyWeb/st2.action执行结果相同。
如上手动指定类是必须包含execute方法，指定后默认的将被覆盖。

(8)<default-action-ref>
为了避免不理想的404页面出现，可以使用<default-action-ref>标签指定一个默认的Action处理。
eg:
```
<struts>
	<package name="mySpace" namespace="/" extends="struts-default">
	<default-action-ref name="actionError">
		<action name="actionError">
			<result>actionError.jsp</result>
		</action>
	</package>
</struts>    
```
如此可以用actionError.jsp

(9)<default-interceptor-ref>
用来设置整个包范围内全部Action所要应用的默认拦截器信息

(10)<interceptors>
向Struts2框架中注册拦截器或者拦截器栈，多用于自定义拦截器或者拦截器的注册。
```
<interceptors>
<interceptor name="拦截器名" class="拦截器类"/>
	<interceptor-stack name "拦截器栈名">
		<interceptor-ref name="拦截器名"/>
	</interceptor-stack>
</interceptors>
```

(11)<interceptor-ref>
对其所在的Action添加拦截器功能，为某个Action单独添加拦截器后<default-interceptor-ref>拦截器对这个Action不在起作用。

(12)<global-results>
设置包范围内的全局结果集。多个Action返回相同的逻辑视图情况下可以通过<global-results>标签统一配置这些逻辑视图所对应物理视图。
eg:
如下Test1和Test2返回为“test”都调到index.jsp
```
<struts>
	<package name="mySpace" namespace="/" extends="struts-default">
		<global-results>
			<result name="test">/index.jsp</result>
		</global-results>

		<action name="test1" class="com.zhang.struts2.Test1">
		</action>

		<action name="test2" class="com.zhang.struts2.Test2">
		</action>
	</package>
</struts> 
```
注意:如果test1的Action添加了<result name="test">/test.jsp</result>则跳转test.jsp

6.web.xml
----------------
web.xml是Web应用的核心配置文件，用于配置Servelet、过滤器Filter、监听器Listenter及Welcome-File等，任何Web框架想要与Web集合就必须依靠web.xml进行设置，核心过滤器FilterDispatcher是Struts2框架的基础，充当中央控制器作用，ActionContextCleanUp过滤器是Struts2的一个常用辅助类，主要用于清理当前线程的ActionContext和Dispatcher防止内存泄漏。web.xml通常只需要配置这两个过滤器就行。
```
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://java.sun.com/xml/ns/javaee" xsi:schemaLocation="http://java.sun.com/xml/ns/javaee http://java.sun.com/xml/ns/javaee/web-app_3_0.xsd" version="3.0">
  <display-name>MyWeb</display-name>
  <!-- 
  <filter>
    <filter-name>struts2</filter-name>
    <filter-class>org.apache.struts2.dispatcher.ng.filter.StrutsPrepareAndExecuteFilter</filter-class>
  </filter>
  <filter-mapping>
    <filter-name>struts2</filter-name>
    <url-pattern>/*</url-pattern>
  </filter-mapping>
    -->
    <!--  配置Struts2的ActionContextCleanUp过滤器 -->
    <filter>
    	<filter-name>struts2-cleanup</filter-name>
 		<filter-class>org.apache.struts2.dispatcher.ActionContextCleanUp</filter-class>
    </filter>
    <filter-mapping>
    	<filter-name>struts2-cleanup</filter-name>
    	<url-pattern>/*</url-pattern>
    </filter-mapping>
        <!--  配置Struts2的核心过滤器FilterDispatcher -->
    <filter>
    	<filter-name>struts2</filter-name>
 		<filter-class>org.apache.struts2.dispatcher.FilterDispatcher</filter-class>
    </filter>
    <filter-mapping>
    	<filter-name>struts2</filter-name>
    	<url-pattern>/*</url-pattern>
    </filter-mapping>
</web-app>
```
备注:
FilterDispatcher是struts2.0.x到2.1.2版本的核心过滤器!  StrutsPrepareAndExecuteFilter是自2.1.3开始就替代了FilterDispatcher的! 
如果我们自己定义过滤器的话, 是要放在strtus2的过滤器之前的, 如果放在struts2过滤器之后,你自己的过滤器对action的过滤作用就废了,不会有效!除非你是访问jsp/html!  那我现在有需求, 我必须使用Action的环境,而又想在执行action之前拿filter做一些事, 用FilterDispatcher是做不到的! 那么StrutsPrepareAndExecuteFilter可以把他拆分成StrutsPrepareFilter和StrutsExecuteFilter,可以在这两个过滤器之间加上我们自己的过滤器! 

7.值栈
----------------
Struts2的值栈是一个存放对象的堆栈，对象以map的形式储存在这个堆栈中，并且该堆栈中的对象属性的数值可以通过表达式语言获得。
值栈储存内容都是对象，储存对象包括临时对象、模型对象、Action对象、命名对象。
临时对象:在程序执行过程中由容器自动创建并储存到值栈中，应用结束时该对象被清空
模型对象:仅在Action使用模型驱动方式传值的时候，当Action被请求时，modeldriven拦截器会自动从Action中获得模型对象，并将对象放在值栈对应的Action对象上，JSP页面可以到值栈找到模型对象获得数值
Action对象：每个Action请求到来时，容器都会先创建一个此Action对象并存入值栈，该对象携带所有与Action执行过程有关的信息
命名对象:主要包括Servlet作用范围内相关的对象信息，比如request、session、application等
遍历顺序从栈顶开始依次是临时对象、模型对象、Action对象、命名对象。模型对象放Action对象前面因为请求需要模型携带数据时可以先找set()方法，没有则查找模型对象对应的Action对象。

8.OGNL
--------------
OGNL(Object-Graph Navigation Language)图对象导航语言，是表达式语言的一种，我们是通过OGNL来访问值栈中信息的。
(1)对list、map操作
| list/map | java访问方式     | OGNL访问方式 |
| ---------| ----------------| ------------|
| 创建list | List list=new ArrayList();list.add("a");list.add("b");list.add(c);| {"a","b","c"}|
| 访问list | list.get(i);list.size();list.isEmpty();| list[i];list.size;list.isEmpty;|
| 创建map  | Map map=new HashMap();map.put("one","name");map.put("two","passwd");map.put("three","age");| #{"one":"name","passwd";"three":"age"} |
| 访问map  | map.get("one");map.size();map.isEmpty();| map['one'];map.size;map.isEmpty;|
     
导航图深度:
![img](img/structs2/20.png)
A,B,C对象对应导航图深度值分别0,1,2;
获得A,B,C对象的name属性分别为[0].name;[1].name;[2].name;


第四章 拦截器
===================
1.拦截器
------------
(1)介绍
拦截器是动态拦截Action调用的对象，Struts2配置应用拦截器只需要在struts.xml中添加或者删除拦截器配置信息即可。
struts2内置（struts-default.xml）拦截器:

| 拦截器       | 功能                                   |
| ------------| ---------------------------------------|
| alias | 对不同请求中的相同参数进行命名转换|
| autowiring| 框架自动寻找相应的Bean并完成设置工作|
| chain| 构建Action链，当使用<result type="chain">进行配置时，当前Action可以使用前一个已经执行结束的Action的属性，实现Action链数据传递|
| checkbox| 否则检查checkbox表单控件是否被选中，未被选中时，提交一个默认值(通常false)|
| cookie| 把带有特定名/值映射关系的cookie注射到Action中|
| conversionError| 处理类型转换时的错误信息，把ActionContext中的错误信息转换为相应的Action字段的错误信息并保存,需要时可以通过视图显示相关错误信息|
| createSession| 自动创建一个HttpSession对象，有些拦截器必须要有HttpSession对象才能工作(eg:TokenInterceptor)|
| debugging| 负责调试，当页面中使用<S:debug>标签时，可以获得值栈、上下文等信息|
| execAndWait| 在后台执行Action,并将等待画面传送给用户|
| exception| 提供处理异常功能，将异常映射为结果|
| fileUpload| 负责文件上传|
| i18n| 把指定Locale信息放入Session|
| logger| 输出Action名称|
| store| 储存或者访问实现ValidationAware接口的Action类出现的消息，错误，字段错误等|
| model-driven| 某个Action实现了ModelDriven接口时，把getModel()方法的结果放入值栈中|
| scoped-model-driven| 某个Action实现了ScopedModelDriven接口,拦截器获得指定的模型，通过setModel()方法将其传送到Action|
| params| 解析HTTP请求参数将其传送给Action,设置成Action对应的属性值|
| prepare| 处理Action执行之前所要执行的操作，Action需要实现Preparable接口，在Action执行之前调用prepare()方法|
| scope| 将一些公有参数信息储存到Session作用域或者Application作用域，当Action需要时，拦截器检查并从Session或者Application中将其取出|
| servletConfig| 提供对HttpServletRequest和HttpServletResponse的访问机制|
| staticParams| 把定义在xml中的<action>标签下<param>标签中的参数传入Action|
| roles| 检查用户是否具有JAAS授权，只有授权用户才可以调用相应的Action|
| timer| 输出Action的执行时间|
| token| 检查传入到Action中的Token信息，防止重复提交|
| tokenSession| 功能和TokenInterceptor相似,只不过将无效的Token信息存放在Session中|
| validation| 执行定义在xxAction-validation.xml中的校验器，完成数据校验|
| workflow| 调用Action的validate方法进行校验，校验失败返回input视图|
| N/A| 从参数列表删除不必要的参数|
| profiling| 通过参数激活profile|

(2)部署拦截器
```
<interceptors>
	<interceptor name="拦截器名" class="拦截器类">
		<param name="参数名">参数值</param>
	</interceptor>
	<interceptor name="拦截器名" class="拦截器类">
		<param name="参数名">参数值</param>
	</interceptor>
...
</interceptors>
```

(3)添加拦截器
```
<action name="Action名" class="Action类">
	<interceptor-ref name="拦截器名">
		<param name="参数名">参数值</param>
	</interceptor-ref>
	<interceptor-ref name="拦截器名">
		<param name="参数名">参数值</param>
	</interceptor-ref>
...
</action>
```

(4)实例
```

```


 

2.拦截器栈
-------------

3.应用
------------










附录：
============
1.配置dtd的本地url校验
--------------------
一般struts.xml中有"http://struts.apache.org/dtds/struts-2.1.dtd"需要联网才能提示，可以添加本地，方法如下：
将struts2-core-2.1.8解压到E盘，在myeclipse中->windows->preferences->搜索框输入xml->XML Catalog  ->User Specified Entries里面自己配置个dtd的本地url校验，这样就不用去联网校验了




****************************
更新中............