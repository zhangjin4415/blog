title: U盘装Windows10/CentOS双系统
date: 2016-04-27 16:31:00
categories: "CentOS"
tags: "CentOS"
---
本文以原电脑没有系统和数据操作，有系统或者数据的可以部分采纳！
<!--more-->

1.磁盘分区
=================
将磁盘分为一个主分区+2个逻辑分区+一个空闲盘，主分区用来装windows系统,空闲盘用来装centos系统。我的分区如下：
![image](img/centos_windows/1.png)

2.windows系统安装
================
windows系统安装较为简单，网上教程也多，这里不再详述！安装到主分区即可！

3.centos安装
=====================
制作centos系统U盘，U盘启动，
选择Install or upgrade an existing system
选择语言(chinese(simplified))
选择键盘格式(us)
选择installation method:Hard drive
选择Select Partition:/dev/sda4  (选择sda项--就是有系统盘U盘项)备注：每个电脑不一样，有些是sdb,一般选择与其余不一样的就行。
之后如下：
![image](img/centos_windows/2.png)
点击下一步
选择基本储存设备，点击下一步
设置主机名，点击下一步
选择时钟（默认上海即可），下一步
设置密码，下一步
下面的设置较为关键！
选择哪种类型的安装，不能使用所有空间，否则电脑所有东西全部清空，选择自定义布局 如下：
![image](img/centos_windows/3.png)
点击下一步，弹出窗口如下：
![image](img/centos_windows/4.png)
谨记我们建立分区要点在那个空闲上面，进行创建，否则其他盘数据将丢失！
下面进行分区，我具体操作如下三步：
（1）/boot(启动分区)
选中空闲盘，点击右下角的创建按钮，选择标准分区，点击创建
![image](img/centos_windows/5.png)
之后选择如下（sda项不选，这里分区大小依每个人自己而定，盘小也可以只分100-200M）：
![image](img/centos_windows/6.png)
点击确定。

(2)Swap(交换空间)
通常设置为1-2G，一般内存小于2G时，设置为内存的2倍;内存大于或等于2G时，设置为2G!
选中空闲，点击创建，选择标准分区，点击创建，设置如下：
![image](img/centos_windows/7.png)

(3)/(根分区)
选中空闲盘，点击右下角的创建按钮，选择标准分区，点击创建,剩余空闲空间大小全部设置为其大小。如下：
![image](img/centos_windows/8.png)

设置完毕后如下：
![image](img/centos_windows/9.png)
点击下一步。点击将修改写入磁盘。
之后弹出的界面需要仔细设置，点击更换设备，主引导记录选择MBR项，BIOS驱动器顺序选择第一项为电脑硬盘(sdb),第二才是U盘(sda).引导装载程序操作系统列表的Other代表的是windows系统，为了更加直观，建议将其编辑为windows或者windows10.设置完后如下：
![image](img/centos_windows/10.png)
之后点击下一步
下面一般默认选择即可，以后自定义和现在自定义建议选择现在自定义可以安装过程中更新自己选中的程序或者服务。
之后下一步就开始安装啦！
安装完毕显示恭喜你，已经成功安装，点击重新引导重新启动。
重启后会进入设置界面，这里比较简单，就是设置用户名密码什么的，设置完后就进入系统啦。如此系统安装完成。

4.启动设置
==============
在centos系统下，修改文件/etc/grub.conf，打开文件如下：
![image](img/centos_windows/11.png)
改动后如下：
![image](img/centos_windows/12.png)
之后保存重启系统。
![image](img/centos_windows/13.png)
如上显示window10将在10s后启动，此时不点击任何键将启动windows10，点击回车可以显示如下：
![image](img/centos_windows/14.png)
选择自己要进入的系统即可！















