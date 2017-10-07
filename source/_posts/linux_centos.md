title: CentOS
date: 2016-11-17 18:59:00
categories: "Linux"
tags: "CentOS"
---
主要内容：
<!--more-->

第一章 安装与更新
==================
1.系统安装
--------------
详见
http://bestzhangjin.com/2016/04/27/centos_windows/

2.更新yum源
------------
```
cd /etc/yum.repos.d
mv CentOS-Base.repo CentOS-Base.repo.backup  //备份
wget http://mirrors.163.com/.help/CentOS6-Base-163.repo //源
mv CentOS6-Base-163.repo CentOS-Base.repo
yum clean all
yum makecache
yum -y update
```

第二章 软件安装
===============
1.ibus输入法
-------------
点击系统->首选项->输入法 点击使用IBus即可 ctrl+空格键可以切换输入法
没有IBus则参考安装:http://jingyan.baidu.com/article/c843ea0b94d61a77931e4a3b.html


第三章 常见问题
================
1.linux网络有线连接失败“设备未托管” 解决办法
-------------------
问题描述：
1).Linux 无线网络连接正常，有线网络无法连接
2).ifconfig 命令之后没有eth0 。
3).右上角网络连接处显示有线网络 设备未托管 
解决方法：
sudo /etc/NetworkManager/NetworkManager.conf
将managed=false改成true，重启一下就可以了。
