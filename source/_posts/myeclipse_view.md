title: Myeclipse应用技巧
date: 2016-03-15 21:00:51
categories: "Myeclipse"
tags: ["Myeclipse","应用技巧"]
---
主要内容：
<!--more-->
1.Myeclipse搭建安卓环境
==========================
工具：Myeclipse,ADT,SDK
1.安装Myeclipse
2.ADT解压，将解压目录下的features与plugins文件夹放到Myeclipse安装目录的dropins目录下面
3.复制SDK，制定Myeclipse对应到这个SDK
  windows->perference->android->SDK目录

2.myeclipse导入项目
==========================
File->Import->General->Existing Projects into Workpace
点击next，选择"Browse...",浏览工程所在目录，找到工程所在文件夹，确定。
此时projects里面会出现工程所在目录对应所有的工程，选择你需要的工程，选择”Finish"，即可！

3.javabean之自动生成set、get方法
============================
java文件工作区右键->source->generate getting and setting...

4.myeclipse导入架包
=====================
将架包复制到项目的lib目录下，选中架包右键->Build Path->Add To Build Path



****************************
更新中............