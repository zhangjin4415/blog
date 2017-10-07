title: Myeclipse常见问题与解决方法
date: 2016-01-15 13:51:52
categories: "Myeclipse"
tags: ["Myeclipse","常见问题"]
---
主要内容：Myeclipse错误及解决方法
<!--more-->
第一章 搭建安卓环境错误
==========================
1.Error when loading the SDK:\android-wear\armeabi-v7a\devices.xml发现以元素'd:skin'开头的无效内容，\android-wear\x86\devices.xml发现以元素'd:skin'开头的无效内容
--------------------------------------------------------

解决：
方法1： 在SDK Manager里删除Android-wear相关的image 
方法2： 进入sdk目录下，把..\android-sdk\system-images\android-22\android-wear\armeabi-v7a\devices.xml
和..\android-sdk\system-images\android-22\android-wear\x86\devices.xml文件删除，
再把sdk里面..\android-sdk\tools\lib\下的devices.xml拷贝到上述两个文件夹里，重启eclipse即可

2.'Open Project' has encountered a problem,The project description file(.project) for 'APP' is missing
-----------------------------------------
解决：
可能一：这种情况往往是工程文件夹中的.project文件丢失了，所以从别的工程复制过来，就可以用啦。
方法二：项目路径改变了，删除项目（不勾选删除文件）后，再重新导入

3.MyEclipse中导入项目出现Select at least one project 
----------------------------------------------------
解决：在导入工程的时候出现的，这是因为有同名的工程的，
进入windows->show view->project explorer 这里找出来删掉再导入工程即可。

第二章 服务器tomcat不能启动
===============================
1.Publishing to Tomcat Server at localhost Could not publish
--------------------------------
我出现这个错误是因为Myeclipse的工作目录下项目被我直接删除而Myeclipse不知道。
解决：删除工作目录workpace下的.metadata文件夹，重新启动Myecllipse，Myecllipse将生成新的.metadata文件夹，启动tomcat发现问题解决！


第三章 Struts2方面问题
=================================
1.HTTP Status 500 - The Struts dispatcher cannot be found. This is usually caused by using Struts tags
--------------------------
（1）JSP页面中没有加入类似下面内容： <%@ taglib prefix="s" uri="/struts-tags"%> 
（2）拦截器不是/* <filter-mapping> <filter-name>struts2</filter-name> <url-pattern>/*</url-pattern> </filter-mapping>

2.struts.xml提示The content of element type "package" must match "(result-types ,interceptors ,default-interceptor-ref ,default-action-ref ,default-class-ref ,global-results ,global-exception-mappings ,action*)"
----------------------------
这个错误的意思是，package里元素必须按照一定的顺序排列。这个顺序
就是
result-types
interceptors
default-interceptor-ref
default-action-ref
default-class-ref
global-results
global-exception-mappings
action*(就是所有的action放到最后)





****************************
更新中............