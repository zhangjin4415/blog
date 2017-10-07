title: Ardunio
date: 2016-07-06 16:28:00
categories: "Ardunio"
tags: ["Ardunio"]
---
主要内容： Ardunio
<!--more-->

第一章 Ardunio环境搭建
=================
1.Ardunio介绍
----------------
Ardunio是一块单板的微控制器和一整套的开发软件，它的硬件包含一个以AVR单片机为核心的开发板和其他各种I/O板；软件包含一个标准编程语言开发环境和在开发板上运行的烧录程序。Ardunio主要为业余爱好者设计，所以被设计成小型计算机形式。

2.环境搭建
------------
首先到淘宝上购买一块Ardunio（可以只要一块主板，需要其他拓展版的时候再购买），主板如下：
![image](img/arduino/1.png)
Ardunio IDE下载：网上比较多，可以到官网或者其他网站上下载一个免安装压缩包直接解压就可以用。
软件界面如下：
![image](img/arduino/2.png)
图中标志勾代表编译，标志左箭头代表烧录程序。烧录程序前先要保证工具->端口 选中其中的com端口号；
打开时默认只有setup()和loop()函数，setup()函数里面的内容只执行一次，loop()中的内容无限循环的执行。
在工具->串口监视器中可以查看串口输出。

第二章 简单Led功能
================
1.Led闪烁
-------------
电路连接：从ardunio的10引脚连接到Led的正极，
程序如下：
```
int led=10;
void setup() {
  pinMode(led,OUTPUT);//将IO口设置为输出模式
}

void loop() {
  digitalWrite(led,HIGH);//led引脚电平拉高
  delay(1000);
  digitalWrite(led,LOW);//led电平拉低
  delay(1000);
}
```

2.Led效果灯
--------------------
(1)Led跑马灯
实现led灯从左到右再从右到左循环；
```
byte ledPin[]={5,6,7,8,9,10};//也可以先声明大小byte ledPin[6]，再初始化 
int ledDelay(65);//int ledDelay=65;
int direction=1;
int currentLED=0;
unsigned long changeTime;
void setup() {
  for(int x=0;x<6;x++){
    pinMode(ledPin[x],OUTPUT);
  }
  changeTime=millis();//记录当前时间
}

void loop() {
  if((millis()-changeTime)>ledDelay){
    changeLED();
    changeTime=millis();
  }
}

void changeLED(){
  for(int x=0;x<6;x++){
    digitalWrite(ledPin[x],LOW);//关闭所有LED
  }
  digitalWrite(ledPin[currentLED],HIGH);
  currentLED+=direction;
  if(currentLED==5){direction=-1;}//达到最右边时开始向左走
  if(currentLED==0){direction=1;}//达到最左边时开始向右走
}
```

(2)控制跑马灯的速度
和上面的电路和程序基本一样，只需要在一个端口上连接一个电位计(如4.7K欧姆旋转电位计)，通过ledDelay=analogRead(potPin);//其中potPin为电位计的输入引脚，就可以读到一个0-1023之间的整数值，每个分度5V/1024=4.9mV.
代码和上面一样，只需要在loop()里面加上ledDelay=analogRead(potPin);即可通过电位计旋转控制跑马灯的跑动速度。

(3)通过PWM功能实现led的亮度变化
analogWrite(ledPin,ledVal); //ledPin是单片机的输出接口，ledVal是0到255之间的一个值，通过调节ledVal可以调节输出占空比，从而调节接口对于led的亮度。














