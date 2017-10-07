title: Android studio应用技巧
date: 2016-01-16 09:29:12
categories: "Android studio"
tags: ["Android studio","应用技巧"]
---
主要内容：Android studio应用技巧
<!--more-->
1.项目路径修改
=====================
查看当前项目的路径：navigate->File path
注意：Android Studio的project相当于eclipse的workspace，Android Studio的module相当于eclipse的project，android Stduio，把一个项目比喻成一个工程的一个个模块，外部的依赖也是一个个模块，这样一个项目的结构就很清晰明了。当然也有一个缺点，就是一个窗口只能打开一个project,不能像eclipse那样一次一个窗口打开多个项目。

2.SDK/JDK路径修改
=======================
查看和修改：Fiew->project strcture或者View->open module settings->SDK Location
打开会发现SDK/JDK路径设置

3.工程名(apk名称)修改
========================
项目右键->refactor->rename

4.导入架包
=================
项目下默认有libs文件夹，将架包拷贝到libs目录下。
但是还未导入，所以看不到jar中包含的内容。而已导入的jar，则可以看到jar中内容。
右键点击新黏贴的jar，在弹出菜单中点击Add As Library.

5.Android studio导入项目
===============
Android Studio默认使用 Gradle 构建项目， Eclipse 默认使用Ant构建项目。建议Android Studio导入项目时，使用 Gradle 构建项目。
(1)导入android studio项目
--------------------------
File->new->import project


(2)使用Gradle构建导入Eclipse项目
-----------------------------



(3)使用Ant构建构建导入Eclipse项目
-----------------------------



****************************
更新中............