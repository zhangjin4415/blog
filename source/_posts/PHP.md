title: PHP
date: 2016-07-19 17:25:00
categories: "PHP"
tags: "PHP"
---
主要内容：PHP
<!--more-->

第一章 环境搭建
=============
下载软件:
xampp-win32-5.6.21-0-VC11-installer.exe
PhpStorm-2016.2.exe
XAMPP(Apache+MySQL+PHP+PERL)是一个功能强大的建 XAMPP 软件站集成软件包；
PhpStorm是JetBrains公司开发的一款商业的PHP集成开发工具。
先安装XAMPP，完成如下:
![image](img/php/1.png)
再安装PhpStorm，之后指定php目录为XAMPP安装目录下的php文件夹就可以用啦，编写完代码后在鼠标移到右上角有显示浏览器，直接点击一个已经安装的浏览器就可以在页面看到效果。
指定php目录:file->setting->languages->php
![image](img/php/2.png)

第二章 语法
============
1.标记符
--------
php文件开头<?php 结尾为?> 只有php代码时可以不要结尾；
与html混编时要结尾.
如下是html中嵌入php代码
```
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <title>PHP</title>
</head>
<body>
HTML!<br>
<?php
echo 'PHP';
?>
</body>
</html>
```
输出:
HTML!
PHP

2.常量与变量
----------
变量声明以$符号开头,常量用const.
```
<?php
$a=1;
$a=120;
echo $a;//变量值可以改变
const b=21;
echo b;//常量值不可以改变
define('VALUE',289);//常量的另外一种定义方法
echo VALUE;
?>
```

3.函数
-----------
```
<?php
function echoHello(){
    echo 'hello<br>';
    echo 'php';
}
echoHello();
////输出:
//hello
//php

//函数可以通过变量执行，如下
$func='echoHello';
$func();
//输出效果与:echoHello();相同

//传参
function sayHello($name){
    echo 'Hello ',$name;
}
sayHello('zhangsan');//Hello zhangsan
function echoNUM($a,$b){
    echo 'a='.$a.',b='.$b.'<br>';
    //也可以如下写
    //echo "a=$a,b=$b"; //a=1,b=2 //这里双引号不能换为单引号
    //echo 'a=$a,b=$b';//a=$a,b=$b
}
echoNUM(1,2);//a=1,b=2

//返回值
function add($a,$b){
    return $a+$b;
}
echo add(3,4) //7
?>
```

4.流程控制
---------
选中代码Ctrl+/可以注释
```
<!DOCTYPE html><!-- 这里用html目的是用charset='utf-8'防止乱码 -->
<html>
<head>
    <meta charset="utf-8">
    <title>PHP</title>
</head>
<body>
<?php
function getLevel($score){
    //if语句
//    if($score>90){
//        return '优秀';
//    }elseif ($score>60){
//        return '及格';
//    }else{
//        return '差';
//    }
    //swith语句
    $result='';
    switch (intval($score/10)){//要强转为整数 否则都是default
        case 10:
        case 9:
            $result='优秀';
            break;
        case 8:
        case 7:
        case 6:
            $result='及格';
            break;
        default:
            $result='差';
            break;
    }
    return $result;
}
echo getLevel(72);//及格
?>
</body>
</html>
```

5.循环
---------
```
<?php
//以下三个都输出:hello 0, hello 1, hello 2, hello 3, hello 4,
for($i=0;$i<9;$i++){
    echo 'hello '.$i.', ';
    if($i==4){
        break;//注意break与continue的区别
    }
}
$i=0;
while ($i<5){
    echo 'hello '.$i.', ';
    $i++;
}
$i=0;
do{
    echo 'hello '.$i.', ';
    $i++;
}while($i<5)
?>
```

6.逻辑运算
----------
```
<?php
for($i=0;$i<30;$i++){
    //与 &&
    if($i%2==0 && $i%3==0) {
        echo $i;
        //或 ||
        //非 !
    }
}
?>
```

第三章 部署 PHP 代码
==============
在服务器上安装lampp







附录：
============
1.ubuntu上部署php项目
------------
安装php
安装tomcat
使用quercus支持
去官网上下载一个http://quercus.caucho.com/，是war格式的，放到tomcat的webapps目录下，运行tomcat，会在当前目录下生成一个名字一样的项目，把php文件放进去就可以了，和管理普通jsp项目一样，简单方便！
