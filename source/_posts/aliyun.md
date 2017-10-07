title: 阿里云ECS（linux）搭建web环境
date: 2016-03-04 09:15:00
categories: "阿里云服务器"
tags: ["阿里云","服务器"]
---
主要内容：阿里云ECS（linux）搭建web环境
<!--more-->

1.阿里云ECS介绍
=================
阿里云，阿里巴巴集团旗下云计算品牌，全球卓越的云计算技术和服务提供商。创立于2009年，在杭州、北京、硅谷等地设有研发中心和运营机构。
云服务器ECS：一种简单高效，处理能力可弹性伸缩的计算服务。助您快速构建更稳定、安全的应用。提升运维效率，降低IT成本，使您更专注于核心业务创新。


2.连接服务器、向服务器上传文件
=================
(1)连接到服务器
连接到服务器的SSH工具有很多，这里介绍SSH Secure Shell Client和putty两种软件的用法.选择自己喜欢的一种就可以（本文选择SSH Secure Shell Client）
A.SSH Secure Shell Client
下载安装.SSH Secure Shell Client
打开界面点击profiles->add profiles输入你要远程的机器的名字（随便输入即可）
之后点击profiles->你要远程的主机名：
![image](img/aliyun/3.png)
在HostName里输入Linux主机地址
UserName输入账号（一般root）
Port输入端口(一般22)
点击connection之后输入服务器主机密码即可连接成功

传送文件:
点击如下图标new file transfer window:
![image](img/aliyun/4.png)
![image](img/aliyun/5.png)
从左侧本地文件目录拖放文件到右侧窗口则完成文件上传


B.putty
下载软件putty,打开后只是填写你的服务器ip地址(图中00000000位置)：
![putty](img/aliyun/1.png)
点击打开，输入服务器的用户名密码就连接成功:
![putty](img/aliyun/2.png)


(2)更新source-list到最新的源信息：
```
apt-get update
```


3.Web环境搭建
=================
3.1 Web环境介绍
---------------
本文采用JSP技术创建的网页需要jdk（java）环境，服务器采用tomcat.

3.2 jdk安装
---------------
(1)JDK版本介绍
Java SE Development Kit 8u74：jdk java开发环境 jdk自带了前边的jre
Java SE Development Kit 8u74 Demos and Samples：是jre，是java运行环境
eclipse也是属于java程序 只要有了java运行环境以后就能运行的 但是没有jdk的话不能编译java程序 还是个摆设.
本文采用后者，因为服务器上运行即可，不需要编译环境.
官网下载：http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html
选择Java SE Development Kit 8u74的Linux x64版:jdk-8u74-linux-x64.tar.gz下载

(2)安装
解压：
```
tar -xvzf jdk-8u74-linux-x64.gz
```
jdk所在位置:/home/java/jdk1.8.0_74
配置环境变量:
vi ~/.bashrc在后面添加如下代码：
```
export JAVA_HOME=/home/java/jdk1.8.0_74
export JAVA_BIN=$JAVA_HOME/bin
export JAVA_LIB=$JAVA_HOME/lib
export CLASSPATH=.:$JAVA_LIB/tools.jar:$JAVA_LIB/dt.jar
export PATH=$JAVA_BIN:$PATH
```

我们在进行编辑完成之后，可以使用source命令来生效。
```
source ~/.bashrc
```
之后输入java -version弹出java版本安装成功


3.3 tomcat安装
----------------
(1)下载
官网下载：http://tomcat.apache.org/download-80.cgi
本文下载的是apache-tomcat-8.0.32.tar.gz
tomcat需要java环境，所以先安装了jdk

(2)安装
解压：
```
tar -xvzf apache-tomcat-8.0.32.tar.gz
```
解压得到文件夹:apache-tomcat-8.0.32
当解压成功以后，我们直接进入到tomcat bin目录中。
输入 ./startup.sh启动Tomcat，假如显示Tomcat started，则表明启动成功。
tomcat默认是8080端口。
所以浏览器上输入地址：http://你的服务器地址:8080/就可以访问到默认的tomcat主页面了

(3)更改tomcat的8080端口为80端口
找到tomcat的安装目录下的conf下的server.xml将8080改为80
找到如下一段：
```
<!-- A "Connector" represents an endpoint by which requests are received  
         and responses are returned. Documentation at :  
         Java HTTP Connector: /docs/config/http.html (blocking & non-blocking)  
         Java AJP  Connector: /docs/config/ajp.html  
         APR (HTTP/AJP) Connector: /docs/apr.html  
         Define a non-SSL HTTP/1.1 Connector on port 8080  
    -->
<Connectorport="8080"protocol="HTTP/1.1"
connectionTimeout="20000"
redirectPort="8443"URIEncoding="UTF-8"/>
```

把那上面port="8080"里面的8080改成80就可以了.保存后，记的重启下tomcat，这样就可以了。
现在直接http://你的服务器ip地址/就可以访问了


4.服务器ip与域名绑定
=====================
我在阿里云处买的万维网域名。设置比较简单。
登录阿里云，点击域名->解析->设置网站解析->输入ip地址提交即可。
然后输入你的域名就可以访问服务器。

5.上传网站
============
将编写好的网站传入服务器上的tomcat对应目录下就可以实现访问。