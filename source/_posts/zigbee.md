title: ZigBee
date: 2016-07-13 13:28:00
categories: "ZigBee"
tags: ["ZigBee"]
---
主要内容： ZigBee
<!--more-->

第一章 环境搭建
===============
1.介绍
-------------
ZigBee技术是一种近距离、低复杂度、低功耗、低速率、低成本的双向无线通讯技术。
主要用于距离短、功耗低且传输速率不高的各种电子设备之间进行数据传输以及典型的有周期性数据、间歇性数据和低反应时间数据传输的应用。

2.开发环境
-------------------
zigbee需要的开发环境有硬件和软件
硬件：zigbee开发板
![image](img/zigbee/1.png)
软件：IAR for 8051
![image](img/zigbee/2.png)
工具包:zigbee 2007协议栈
![image](img/zigbee/3.png)
以上工具自己到网上购买或者下载

3.工程实例
---------------
点击project->create new project如下:
![image](img/zigbee/4.png)
之后输入项目名即可。
之后在点击File->save workspace
输入保存的文件名
![image](img/zigbee/5.png)
然后新建.c或者.h等源文件再将源文件添加到项目即可。
新建文件：file->new file命名为led.c
源文件添加到项目:proiect->add files选择刚刚新建的led.c添加即可。

第二章 入门-点对点通信
===============
