title: 软件工程师常见问题汇总
date: 2016-03-15 21:23:59
categories: "常见问题"
tags: ["软件工程师","常见问题"]
---
好记性不如烂笔头，本文收集了我在学习过程中遇到的常见问题
<!--more-->
1.端口冲突问题
================
win+R打开运行，然后输入cmd即可。
在dos命令中输入以下命令查询正在被使用的端口号(第二列)以及使用它的程序。
命令：netstat -ano
看到后面一列是有一个PID，然后把占用端口的PID号记下来。
打开任务管理器，选择服务，找到对应PID进程结束进程即可。

2.ubuntu中文乱码-没有中文库
=============
安装中文语言包：
apt-get install language-pack-zh-hans
不行的话先更新下源:apt-get update

用vim配置语言环境变量：
vim /etc/environment 
在下面添加如下两行
LANG=”zh_CN.UTF-8″ 
LANGUAGE=”zh_CN:zh:en_US:en” 
如果你想用英文环境了，改成这两行就OK
LANG=”en_US.UTF-8″ 
LANGUAGE=”en_US:en” 

重启Ubuntu Server：
reboot 

可以用locale查看一下环境变量：
locale





****************************
更新中............
