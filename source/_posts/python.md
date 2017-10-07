title: Python
date: 2016-06-15 20:36:00
categories: "Python"
tags: "Python"
---
主要内容：Python
<!--more-->

第一章 环境搭建
==============================
python有2.x和3.x之分，2.x运行速度较快，3.x功能更多，2.x开发程序更多，这里用2.x。
python以及开发工具PyCharm下载地址如下：
官网下载：https://www.python.org/downloads/ 注意：分64位和32位
官网下载：http://www.jetbrains.com/pycharm/download/#section=windows
具体安装步骤自己百度

第二章 基本知识
====================
1.变量
----------
python会自动识别变量类型，不用加变量类型
如：
```
a=1
b=2
c=a+b
print "c=",c
```
就可以得到c= 3

2.判断语句
```
#coding=utf-8  #程序中有中文时必须加#coding=utf-8 不然会提示错误

s=80
if s>=80: #注意要加冒号 :
    print("很好") #格式必须用tab键缩进
elif s>=60:
    print("及格")
else:
    print("很差")
```

3.循环
----------
输出0-9
```
for i in range(0,10):
    print ("out {0},{1}".format("hello",i)); #{0}{1}对应被"hello",i替换
```
输出结果：
out hello,0
out hello,1
out hello,2
out hello,3
out hello,4
out hello,5
out hello,6
out hello,7
out hello,8
out hello,9

4.定义函数
----------
```
#coding=utf-8

def sayHello():
    print("hello") #缩进部分都属于函数sayHello

sayHello() #函数调用 不能有缩进，否则认为属于上面函数的一部分

def max(a,b):
    if a>b:
        return a
    else:
        return b

print (max(1,2))
```
输出结果：
hello
2

5.类-面向对象
----------
```
#coding=utf-8

class Hello:
    def __init__(self):
        print
    def __init__(self,name):  #构造方法 注意init两边是两杠__
        self.name=name;

    def sayHello(self): #方法
        print ("Hello {0}".format(self.name))

class Hi(Hello): #继承自Hello
    def __init__(self,name):
        Hello.__init__(self,name)#继承后需要执行父类构造方法 不然会出错TypeError: __init__() takes exactly2 arguments(1 given)

    def sayHi(self):
        print ("Hi {0}".format(self.name))

h=Hello("liming") #定义类
h.sayHello() #调用方法

h1=Hi("xiaohua")
h1.sayHi()
```
输出结果:
Hello liming
Hi xiaohua

6.引入Python文件
---------------
pi.py
```
#coding=utf-8

class Hello:
    def sayHello(self):  # 方法
        print ("Hello")
```
my.py
```
#coding=utf-8
#方法一
import pi
h=pi.Hello()
h.sayHello()#输出Hello

#方法二
from pi import Hello
h=Hello()
h.sayHello()#输出Hello
```

第三章 Python语言Web开发框架web2py
==================
1.创建web2py项目
--------------
创建如下
![image](img/python/1.png)
没有选择local的话会下载文件
当然也可以在http://web2py.com/init/default/download选择source code下载之后，以后选择local
创建好如下：
![image](img/python/2.png)
可以直接点击运行如下：
![image](img/python/3.png)
端口用默认的8000，密码自己输入一个，这里输入123456，点击start server如下：
![image](img/python/4.png)

如果在创建的时候application name填写main则可以管理如下：
![image](img/python/5.png)
点击admin
![image](img/python/6.png)
密码和刚进入时设置的一样
登录后可以管理如下
![image](img/python/7.png)

2.处理静态文件
----------
可以直接输入static里面的地址访问内容，如下：
![image](img/python/8.png)

3.编写控制器
------------
在controllers（控制）目录下可以新建python文件
![image](img/python/9.png)
新建一个hello.py访问:直接新建文件写上代码就可以访问，不用自己重新部署，会自动实时部署
![image](img/python/10.png)
可以直接访问方法，不写方法默认访问index方法
![image](img/python/11.png)


第四章 Python 初识
================
1.python特点
--------------
大小写严格区分。简单、支持面向对象，开源、库丰富（如邮件标准库可以实现邮件功能）,跨平台使用，解释性语言（区别于C++等编译性语言 直接通过解释器执行），高级语言。

2.cmd下编写
----------
![image](img/python/12.png)
cmd下运行python文件
```
python xxx.py
```

3.Python 语法基础
---------------
(1)常量与变量
常量不可以更改
常量是指一旦初始化后就不能修改的固定值。c++中使用const保留字指定常量，而Python并没有定义常量的保留字。但是python是一门功能强大的语言，可以自己定义一个常量类来实现常量的功能。 
新建const.py放python安装目录下的Lib目录下
```
# -*- coding: UTF-8 -*- 
# Filename: const.py 
# 定义一个常量类实现常量的功能 
# 
# 该类定义了一个方法__setattr()__，和一个异常ConstError, ConstError类继承 
# 自类TypeError. 通过调用类自带的字典__dict__, 判断定义的常量是否包含在字典 
# 中。如果字典中包含此变量，将抛出异常，否则，给新创建的常量赋值。 
# 最后两行代码的作用是把const类注册到sys.modules这个全局字典中。 
class _const: 
    class ConstError(TypeError):pass 
    def __setattr__(self, name, value): 
        if self.__dict__.has_key(name): 
            raise self.ConstError, "Can't rebind const (%s)" %name 
        self.__dict__[name]=value 
import sys 
sys.modules[__name__] = _const() 
```
test.py引入const定义常量，重复赋值常量则会出错
![image](img/python/13.png)

变量可以更改 如：
```
i=1
i=2
```

(2)数与字符串
数类型:有符号型(int),长整型(long),浮点型(float),布尔型(bool),复数型(complex)。
![image](img/python/14.png)

字符串:用引号包含的字符
```
#coding=utf-8

a='hello'#单引号
print a
b='It is a "boy" '
print b
c="It's a gril"
print c
```
运行结果:
hello
It is a "boy"
It's a gril

##单引号和双引号可以交叉使用，但是单引号中不能使用单引号，双引号中不能使用双引号

三引号:三个单引号或者三个双引号
三引号中的字符串是可以换行的，但是单引号或者双引号中是不可以换行的
```
#coding=utf-8

#三引号 '''也可以用"""但是前后必须一致
a='''my
you
he
she
'''
print a
```
输出：
my
you
he
she

转义符 \
```
print 'It\'s a boy'
print "my\nyou"
```
输出:
It's a boy
my
you

自然字符串:如果一串字符串有转义符，也要按原样保留，可以用自然字符串，即在字符串前加上r
```
print 'It\'s a boy'
print r"my\nyou"
```
输出:
It's a boy
my\nyou

字符串的重复，可以使用重复字符串，如将hello重复5次
```
a="hello\n"*5
print a
```
输出:
hello
hello
hello
hello
hello

子字符串:如"HelloWorld"中"He","Hello","World"等都是"HelloWorld"的子字符串，可以进行子字符串运输找出一个字符串中子字符串。
方法一：索引运算符[]
方法二：切片运算符[:]
```
#coding=utf-8

a="HelloWorld"
#索引运算从0开始 返回下标对应的那个字符
a1=a[0]
print a1
#切片运算符[a:b]从第a下标开始到第b-1下标，第一个下标为0
a2=a[:2]
print a2
a3=a[2:]
print a3
a4=a[2:6]
print a4
```
输出:
H
He
lloWorld
lloW

(3).数据类型
python中没有数组，跟数组最接近的是列表和元组
列表：用来储存一连串元素的容器，用[]表示，元素内容可以修改
元组:元组用()表示，元素内容只能读取，不能修改
```
#coding=utf-8
#列表
stu=["张三","李四","王五"] #下标从0开始
print stu[2]
stu[2]="小明"
print stu[2]

stu1=("张三","李四","王五")
print stu1[2]
#stu1[2]="小明"  #TypeError: 'tuple' object does not support item assignment
```
输出：
王五
小明
王五

集合：格式set(元素) 功能：建立关系，消除重复元素
```
#coding=utf-8
#集合
a=set("abcdaaafg") #set(['a', 'c', 'b', 'd', 'g', 'f'])
b=set("cderr")
#交集
x=a&b #set(['c', 'd'])
#并集
y=a|b #set(['a', 'c', 'b', 'e', 'd', 'g', 'f', 'r'])
#差集
z=a-b #set(['a', 'b', 'g', 'f'])
#去除重复元素
new=set(a) #set(['a', 'c', 'b', 'd', 'g', 'f'])
print a,x,y,z,new
```
输出：
set(['a', 'c', 'b', 'd', 'g', 'f']) set(['c', 'd']) set(['a', 'c', 'b', 'e', 'd', 'g', 'f', 'r']) set(['a', 'b', 'g', 'f']) set(['a', 'c', 'b', 'd', 'g', 'f'])

字典:也叫关联数组，用{}括起来如a={'name':'小明','home':'北京','like':'音乐'}
每个元素分为两部分。冒号左边为项目名称，右边为其值
```
#coding=utf-8
#字典  ''也可以用""替换
a={'姓名':'小明','家乡':'北京','爱好':'音乐'}
print a['姓名']

#添加数据
a['QQ']="123456"
print a["QQ"]

#改数据
a['家乡']='重庆'
print a['家乡']

#a.clear()#删除 a中所有的条目
#del a#删除整个 dict2 字典
#a.pop('姓名')#删除并返回键为“name”的条目
#print a['姓名']  #KeyError: '\xe5\xa7\x93\xe5\x90\x8d'
```
输出:
小明
123456
重庆

(4).标识符
编程的时候起的名字统称为标识符
命名规则：
第一个字符必须只能是字母或者下划线，不能出现数字或者其他字符
标识符除第一个字符外，其他部分可以是字母、下划线、数字
对大小写敏感，name与Name不同

关键字：系统自带的具备特定含义的标识符，
常见有and,elif,global,or,else,pass,break,continue,import,class,return,for,while等

(5).对象
一切都是对象，如数字，字符串，元组等都是对象。
pickle(腌制):一些对象需要持久性储存，并且不丢失对象的类型与数据，我们则需要对其进行序列化，需要的时候再恢复数据，这种序列化的过程叫pickle.
序列化叫pickle腌制，恢复叫反pickle腌制
```
#coding=utf-8
#pickle腌制

import pickle

#dumps(object)将对象序列化
lista=["aaa","bbb"]
print lista               #['aaa', 'bbb']
listb=pickle.dumps(lista)
print listb               #(lp0 S'aaa' p1 aS'bbb' p2 a.

#loads(string)将对象原样恢复,并且对象类型也是恢复为原来的格式
listc=pickle.loads(listb)
print listc              #['aaa', 'bbb']

#dump(object,file)将对象储存到文件里面序列化
fa=("google","baidu")
f1=file('1.pkl','wb')
fa1=pickle.dump(fa,f1,True)
print fa1                      #None
f1.close()

#load(object,file)将dump()储存在文件里面的数据恢复
f2=file('1.pkl','rb')
fb=pickle.load(f2)
print fb                       #('google', 'baidu')
f2.close()
```

(6).行与缩进
逻辑行:一段代码在实际意义上的行数
物理行:实际看到的行数
```
#一个物理行，三个逻辑行
print "abc";print "def";print 123

#一个逻辑行，两个物理行
print '''hello
你好
'''
```
一个物理行包含多个逻辑行时需要用分号“;”隔开，最后一个可以省略

行连接
```
#行连接 \
print "我们都是\
好孩子"
```
输出:
我们都是好孩子

缩进:
python逻辑行行首的空白是有规定的，逻辑行行首的空白不对就会导致程序出错，这与其他语言不同
```
a="abc"
 print a #print前面多了一个空格 出错IndentationError: unexpected indent
```
一般情况逻辑行行首不会有空白，但是if,while需要缩进
```
#coding=utf-8

a=1
if a>0:
    print "a>0" #缩进一个tab字符或者任意个空格 否则错
# if a > 0:
# print "a>0"  #错误 IndentationError: expected an indented block
while a>0:
    print a
    a-=1
```
输出：
a>0
1

第五章 Python核心编程基础教程之Python运算符、运算符优先级、表达式简介
=======================
1.运算符
---------
常见运算符:+、-、*、/、**、<、>、!=、//、%、&、|、^、~、>>、<<、<=、>=、==、not、and、or。
```
#coding=utf-8
a=7+8 #15
b="Hello"+" World"#Hello+World
c = -(-8)#8
d="my"*3#mymymy
e=7/2#3
f=7.0/2#3.5
g=7/2.0#3.5
h=2**3#8
k=3<7#True
l=3<3#False

a=2!=3#True
b=2!=2#False
c=10//3 #返回商的整数部分
d=10%3#返回商的余数
e=10%1#0
f=7&18#按位与 2 7和18的2进制与为2
g=7|18#23 按位或
h=7^18#按位异或
i=~18#按位翻转 #x=-(x+1) ~18=-(18+1)=-19
j=18<<1#36   #左移n个单位相当于乘以2的n次幂
k=2<<1#4

a=18>>1  #9 向右移动n个单位相当于除以2的n次幂
b=3<=3 #True
c=12==13 #False
d="hello"=="hello"#True
e=not d #False #################  逻辑非 not
f=True and True #True #逻辑与 两个为真才为真 #逻辑与 and
g=True or False #True 逻辑或 两个为False才为False #逻辑或 or
```

2.python优先级
------------
选择优先级高的运算符先执行
```
#优先级排行榜
#1.函数调用，寻址，下标
#2.幂运算 **
a=2*3**2 #18
#3.翻转运算 ~
#4.正负号
b=4*-2 #-8
#5.乘除符号
#6.加减符号 + -
#7.向左移动向右移动 <<,>>
#8.按位&,^,|
#9.比较运算符
c=2*2+1<6 #True
#10.逻辑not,and,or
#11.lambda表达式

#优先级使用规律
#一般情况是左结合的
#出现赋值时候一般是右结合的
```

优先级记忆规律:
函数寻址下标一，幂运算小二小(*^__^*) 嘻嘻……；
全体单元第三位；单元运算符就是操作一个操作对象的运算符，如~，正负号
乘除求余四千里；
乘除完了五加减；
六娃玩耍左右移；
七是按位或跟与; 同时包括异或
八仙生气要比敌； 比较运算符
倒数第一逻辑或非与；
lambda表达式刚开始很少遇到，遇到时候将其放最低优先级；

不知道可以用()包含则先计算，优先级最高的是()里面的。

3.表达式
------------
值，变量，运算符共同组成的整体叫表达式。
如："ok",a="hello"
实例:
```
#coding=utf-8
4 #值表达式
"hello" #字符串表达式
25+7 #计算表达式
a=5 #赋值表达式
```

第六章 控制流
===============
1.控制流类型
---------
顺序结构，分支结构，循环结构

2.if，while,for
----------
if用法如下
```
#coding=utf-8
'''
if 条件:
    语句;
elif 条件:
    语句;
else:
    语句;
'''
a=78;
if a<60:
    print '不及格';
elif 60<=a<=80: #可以用a<=80
    print '良好';
else:
    print '优秀';
```

while语句用法
```
#coding=utf-8
'''
while 条件为真:
    循环执行语句;
else:  #else部分可以省略
    条件为假执行语句:
'''
a=False
while a:
    print "hello" #死循环 需要避免
else:
    print "你好"

#多层嵌套
b=1
while b<5:
    if b<3:
        print b;
    else:
        print "hello"
    b+=1;#不在else的缩进,属于while语句
else:
    print "b>=5"
#输出 1，2，hello，hello，b>=5
```

for语句用法
```
#coding=utf-8
'''
for 格式:
for i in 集合:
    执行语句;
else:
    执行语句：
'''
k=range(1,4);#[1, 2, 3]
for i in [1,3,45]:
    print i;#1,3,45
for j in range(1,4):
    print j;#1,2,3
for m in range(1,4,2):#2代表步长 ，每两个输出一个
    print m;#1,3
#嵌套分支结构
for n in range(1,5):
    if n%2==0:
        print ("{0}是偶数".format(n));
    else:
        print ("{0}是奇数".format(n));
#输出:1是奇数,2是偶数,3是奇数,4是偶数
```
break语句用法
```
#coding=utf-8
'''
break语句退出循环
'''
a=1;
while a:
    print a; #输出1，2  因为下面有a==3时退出循环
    a+=1;
    if a==3:
        break;
#输出结果:1,2

#双层嵌套循环
a=4;
while a<6: #4,5循环两次
    a+=1;
    for i in range(1,6):#输出1,2,3跳出当前循环，进入嵌套循环继续输出1,2,3
        print i;
        if i==3:
            break;
#运行结果:1,2,3,1,2,3

a=3;
while a<7:
    a+=1;
    for i in range(1,6):
        print ("{0}输出".format(i));
        if i==4:
            break;#跳出for
    if a==5:
        break;#跳出while
#运行结果:1输出,2输出,3输出,4输出,1输出,2输出,3输出,4输出
```
continue语句用法
```
#coding=utf-8
'''
continue语句结束本次循环，继续下一次循环
'''
for i in range(1,5):
    if i==3:
        continue;
    print i;
#输出结果：1，2，4
```

第七章 函数
==================
1.函数认识
--------------
函数(function)是用来封装特定功能的；分系统自带函数和用户自己定义的自定义函数。
```
#coding=utf-8
#系统自带的函数
#1,取字符串长度
a="hello"
print len(a) #5
#字符串切割
b=a.split("e") #['h', 'llo']
#自定义函数
def m():
    print "hello"
m(); #hello
```
函数定义格式：
```
def 函数名():
	函数内容;...
	函数内容;...
```

2.形参与实参
--------
形参一般发生在函数定义中，指参数的名称，而不代表参数的指；
实参一般在函数调用的时候出现，指的是具体的值；
```
#coding=utf-8
def fmax(a,b):  #a,b代表形参，只是一个名称而已
    if a>b:
        print a;
    else:
        print b;
fmax(1,3);  #1,3代表实参
```

3.参数的传递
---------
关键参数：一个函数出现多个参数的时候，我们可以通过参数的名字直接给我们的参数赋值，那么这些参数叫关键参数。
```
#coding=utf-8
#参数传递
#1.简单传递
def fmax(a,b):
    if a>b:
        print a;
    else:
        print b;
fmax(1,3);
#2.赋值传递
def fmax2(a,b=8):
    print a;print b;
fmax2(2);#输出2,8
fmax2(2,9);#输出2,9
#3.关键参数
def fmax3(a=1,b=2,c=3):
    print a;print b;print c;
fmax3(5); #a=5  输出5,2,3
fmax3(b=4,a=6); #按关键字传递 不会考虑参数位置 a=6,b=4,c=3 输出:6,4，3
fmax3(5,c=6,b=7); #5没有关键字，默认为第一个 有关键字的对应 输出:5,7,6
fmax3(b=5,c=6,a=4); #输出4,5,6
#注意参数不能冲突
#fmax3(b=2,c=1,5); #error!!!!!!!!!!
```

4.全局变量与局部变量
------------
作用域：一个变量在一定的范围内有效
```
def fa():
    i=8;
print i; #error!!!***** i的作用范围在函数内有效
print j; #error 因为先用后定义，定义后面才有效
j=9;
```
局部变量：在一定范围内起作用而非全局都起作用的变量；一个函数中变量没有进行全局变量声明时默认是局部变量。如上面的i.
全局变量:作用域为全局的变量，需要声明global.
```
#coding=utf-8
def fa():
    global i;
    i=8;
#print i; #global name 'i' is not defined--因为没有执行fa()等于还没有定义
i=9;
print i;  #9
fa();
print i;  #8
```

5.函数使用与返回值
------------
调用函数：在函数定义后直接输入函数名即可。
函数返回值：通过return实现，可以返回一个或者多个值
```
#coding=utf-8
def test():
    i=1;
    return i;
print test();   #输出： 1
def test2(i,j):
    k=i*j;
    return (i,j,k);
x=test2(2,3); #x默认为三个元素组成的元组
print x;   #输出： (2, 3, 6)
x,y,z=test2(3,4); #返回值赋给三个变量分别存储
print x;print y;print z;  #输出： 3,4,12
```

6.文档字符串
-------
函数太多太乱问题解决：
方法一：开发时为每一个函数写一个文档说明；
方法二：文档字符串-python特有，在每个函数开头加一行说明性文字，这行说明性文字叫文档字符串。
```
#coding=utf-8
#文档字符串 函数定义下面第一行开始 用三引号包含
#第一行概括函数功能
#第二行不写
#第三行以下为详细说明
#每行句末使用句号
#如果是英文每一行第一个字母必须大写，中文不用
#用法 函数名._doc_ 或者 help(函数名)
def d(i,j):
    '''
    这是一个乘法运算。

    函数传入两个数，返回相乘后的结果。
    '''
    k=i*j;
    return k;
print d.__doc__
#输出结果：
# 这是一个乘法运算。
#
# 函数传入两个数，返回相乘后的结果。

help(d)
#输出结果:
#Help on function d in module __main__:
#
#d(i, j)
#    这是一个乘法运算。
#
#    函数传入两个数，返回相乘后的结果。
```

第八章 模块
===========
1.认识模块
--------
函数是可以实现一项或者多项功能的一段程序，模块是函数功能的拓展，函数是一段程序，模块是一项程序块，函数和模块都是实现功能，但是模块比函数广，模块里面可以重用多个函数;
模块都是放在python安装目录下的Lib目录下的;
比如压缩模块zipfile.py实现了压缩解压一类功能;
使用模块时必须先导入，导入用import;
如math里面的pi=3.14159...
import math之后就可以使用math.pi得到pi的值。

sys模块：在标准库中与系统功能有关的模块。
如下可以查看版本信息:
```
#coding=utf-8
import sys
print sys.version #python版本信息
print sys.executable #查看当前运行的程序的目录地址
print sys.getwindowsversion() #返回windows操作系统的版本信息
print sys.modules.keys() #查看已经导入模块的关键字
```

2.字节编译
----------
python需要到二进制才能执行，有两种执行方式：
(1)将模块里的内容编译成二进制语言，然后执行这些二进制语言；
(2)省略编译这一步，直接执行对应模块的二进制语言程序。
第二种方法比第一种快。
字节编译:把模块程序编译成二进制语言程序的过程；
.pyc文件:经过编译后的模块对应的二进制文件。

字节编译与编译区别:
python是解释型语言，而不是编译型语言，python中虽然出现了编译过程，但是python的编译过程是在python解释器中发生的；
编译型语言是指在软件中有一个独立的编译模块编译程序；
python中字节编译由解释器完成，所以python仍然是解释型语言。

两种.pyc文件产生的方式：
(1)在运行一个模块的时候，如果没有对应的.pyc文件则编译生成.pyc文件；有的话直接运行.pyc文件。
代码中如果没有对应.pyc文件，主要import 模块.py 就会自动编译生成.pyc文件。
(2)cmd下，进入对应模块目录；输入命令：
```
python -m compileall 模块.py
```
则会产生对应的.pyc文件。
.pyc最大作用就是加快模块的运行速度；.pyc文件可以作为反编译等高级功能。
利用二进制文件阅读器可以查看.pyc文件。
反编译就是把.pyc变成.py;比.py变成.pyc难。

3.from...import
----------
导入模块用import，没有导入模块的属性方法，可以用from...import导入属性方法。
```
import sys
sys.version #impot不能直接调用version方法
```
```
from sys import version
version
```
from ... import 只能导入模块的一个属性或者方法，而from ... import *可以导入模块的所有属性和方法。

4.__name__属性
----------
一个函数调用其他函数完成功能叫主函数，没有调用其他函数叫非主函数；一个模块被直接调用而没有被别人调用叫主模块，一个模块被别人调用叫非主模块。
将如下程序lname_.py放Lib目录下（模块目录）：
```
#coding=utf-8
#查看这个模块在不同场景下的__name__
print __name__

#查看__name__属性常用情况
if __name__=="__main__":
    print "It's main"
else:
    print "It's not main"
```
直接运行lname_.py则输出__main__，是主模块；
导入import lname_.py则它是非主模块。

注意：_ _name_ _前后都是两个下划线


5.自定义模块
--------
系统自带模块：python安装时自带模块；
自定义模块：用户自己定义的模块，只需要将自己编写的.py文件放在Lib目录下。
myadd.py如下：
```
def add(i,j):
    k=i+j
    return k
k=add(i,j)
print k
```
直接执行错误，因为k=add(i,j)中i,j没有确切的值；
如果在模块外面先定义i,j,再导入模块也会出错；
```
i=5;
j=6;
import myadd #出错 值还没有传递到模块的时候，模块就会错误
```
所以模块myadd.py应该先初始化一个i,j如下：
```
i=0;j=0;#也可以用 int i;int j;
def add(i,j):
    k=i+j
    return k
k=add(i,j)
print k
```
然后如下调用：
![image](img/python/15.png)
但是这里用test.py调用时输出永远为0
这里将myadd.py改为：
```
def add(i,j):
    k=i+j
    return k
```
test.py如下正确
```
from myadd import add
i=6;
j=5;
k=add(i,j);
print k;#运行结果:11
```

6.dir()函数
--------------
dir()函数：查看python模块的功能；
查看sys模块的功能
```
#coding=utf-8
import sys
print dir(sys)  #查看  输出：['__displayhook__', '__doc__',...]
print sys.__doc__; #使用功能 
```
dir()查看的仅仅是属性的列表，而不携带数据。
如：
```
#coding=utf-8
a=[]
b=['a','b']
c=()
print dir(a)  #['__add__', '__class__', '__contains__',...]
print dir(b) #输出同上一行
print dir(c) #输出元组的属性
```

第九章 数据结构
============
1.概述
-------
数据结构：将数据组织在一起的数据结构。
内置数据结构：系统定义的，如列表,元组，字典等；
拓展数据结构:需要用户定义的，如栈，队列等。
内置数据结构
```
#coding=utf-8
#列表 可以改变元素
["app","aqq","mmn"]
#元组 不可以改变元素
("app","aqq","mmn")
#字典 有名称(字典的键) 键后面跟着的是键对应的值
{"name":"liming","home":"beijin"}
```
数据结构是静态的，算法是动态的；数据结构是算法的基础，相同的数据结构运用不同的算法有不同的效率。

2.栈
------------
栈是一种数据结构；栈相当于一端开口一端封闭的容器，把数据移动到栈里面的过程叫进栈，也叫压栈或者入栈。数据只能从开口方进出。
栈是“先进后出，后进先出”。
```
#coding=utf-8
#栈的实现 栈就是在列表的基础上进行一定的改进
class Stack():#定义一个类
    #方法的第一个参数代表类本身
    def __init__(st,size): #定义初始化函数 st-栈的主体 size-栈的容量
        st.stack=[]; #把列表赋给栈
        st.size=size; #初始化容量
        st.top=-1; #第一个数据位置为0，所以没有数据时栈顶用-1

    def push(st,content):#入栈
        if st.Full():
            print "Stack is full"
        else:
            st.stack.append(content)
            st.top+=1;
    def out(st):#出栈
        if st.Empty():
            print "Stack is Empty"
        else:
            st.top-=1;
    def Full(st):#判断栈是否满
        if st.top==st.size:
            return True
        else:
            return False
    def Empty(st):#判断栈是否空
        if st.top==-1:
            return True;
        else:
            return False;

#调用
q=Stack(7);
print q.Empty();  #True
q.push("hello");
print q.Empty();  #False
q.out();
q.out();           #Stack is Empty
print q.Empty();  #True
```
上面的方法出栈时取不到值，如下是我改进后方法：
```
#coding=utf-8
class Stack():#定义一个类
    #方法的第一个参数代表类本身
    def __init__(st,size):
        st.stack=[]; #把列表赋给栈
        st.size=size; #初始化容量
        st.top=-1;
    def push(st,content):#入栈
        if st.Full():
            print "Stack is full"
        else:
            st.stack.append(content)
            st.top+=1;
    def pop(st):#出栈
        if st.Empty():
            print "Stack is Empty"
        else:
            st.top-=1;
            return st.stack.pop(st.top+1);#加上这行可以取得值
    def Full(st):#判断栈是否满
        if st.top==st.size:
            return True
        else:
            return False
    def Empty(st):#判断栈是否空
        if st.top==-1:
            return True;
        else:
            return False;

#调用
q=Stack(7);
print q.Empty();     #True
q.push("hello");
print q.Empty();     #False
print q.pop();       #hello 
print q.pop();       #Stack is Empty None
print q.Empty();     #True
```

3.队列
----------
队列是一种拓展的数据结构；队列相当于两端都开通的队列，但是一端只能进行插入操作，叫做队尾；另外一端只能进行删除操作，叫做队首；
"对尾进，对首出"。
```
#coding=utf-8
#队列的实现
class Queue():
    def __init__(qu,size):
        qu.queue=[];
        qu.size=size;
        qu.head=-1;
        qu.tail=-1;
    def isEmpty(qu):
        if qu.head==qu.tail:
            return True;
        else:
            return False;
    def isFull(qu):
        if qu.tail-qu.head+1==qu.size:########
            return True;
        else:
            return False;
    def inQueue(qu,content):
        if qu.isFull():
            print "Queue is full"
        else:
            qu.queue.append(content);
            qu.tail+=1;
    def outQueue(qu):
        if qu.isEmpty():
            print "Queue is empty"
        else:
            qu.head+=1;
            return qu.queue.pop(qu.head-1);

#应用
q=Queue(6);
print q.isEmpty(); #True
q.inQueue("python");
print q.isEmpty(); #False
print q.outQueue(); #python
print q.isEmpty(); #True
```

第十章 基本的正则表达式
==================
1.pycharm运用
-------------
显示行号：file->setting->Editor->General->Appearance,选中 Show line nu8mbers.
调整字体:file->setting->Editor->General->Colors & Fonts->Font,选择主题(Scheme)如Default,点击Save As,弹出输入名字框随便输入名字（这里我用myFont）,之后发现在下面可以对字体进行改动。

pycharm调试：
在代码左边单击出现红色的断点，点击运行按钮右边的爬虫按钮进入调试。点击第一次发现i={int}0,a还没有执行。
![image](img/python/16.png)
点击如下按钮可以一步一步运行，如下，点击时a=0,i=0
![image](img/python/17.png)


2.正则表达式符号与方法
---------------
![image](img/python/18.png)
常用符号：
.：匹配任意字符，换行符\n除外；
*:匹配前一个字符0次或者无限次；
?:匹配前一个字符0次或者一次；
.*:贪心算法；
.*?:非贪心算法；
():括号内的数据作为结果返回；

常用方法：
findall:匹配所有符合规律的内容，返回包含结果的列表
Search:匹配并提取第一个符合规律的内容，返回一个正则表达式对象(object)
Sub:替换符合规律的内容，返回替换后的内容

实例：
```
#coding=utf-8
#导入re库文件
import re

# .的使用；"."就是一个占位符
a="xyz4321";
b=re.findall('x...',a);
print b;  #['xyz4']
b=re.findall('x..',a);
print b;  #['xyz']
a="aaxss"
b=re.findall('x.',a);
print b;  #['xs']
b=re.findall('x....',a);
print b;  #[]

# *的使用
#如下找不到x的位置为空
a='xaaxy123'
b=re.findall('x*',a);
print b; #['x', '', '', 'x', '', '', '', '', '']

# ？的使用
a='xaaxy123'
b=re.findall('x?',a);
print b; #['x', '', '', 'x', '', '', '', '', '']

# .*的使用
code='hadkfalifexxIxxfasdjifja134xxlovexx23345sdfxxyouxx8dfse';
b=re.findall('xx.*xx',code)
print b #['xxIxxfasdjifja134xxlovexx23345sdfxxyouxx']
c=re.findall('xx.*?xx',code)
print c #['xxIxx', 'xxlovexx', 'xxyouxx']

# 括号的使用 将需要的内容用()括起来
d=re.findall('xx(.*?)xx',code)
print d #['I', 'love', 'you']
for each in d:
    print each #I love you

s='''sdfxxhello
xxfsdfxxworldxxasdf'''
#一般匹配是不会包含换行符，所以如下得到
#的是['fsdf']，xxhello之后遇到换行符没有找到后面的xx，直接抛弃重新开始
e=re.findall('xx(.*?)xx',s)
print e #['fsdf']
#在后面加上re.S后可以包含换行符
f=re.findall('xx(.*?)xx',s,re.S)
print f #['hello\n', 'world']

#search与findall区别
s2='asdfxxIxx123xxlovexxdfd'
f1=re.search('xx(.*?)xx123xx(.*?)xx',s2);
print f1.group(1);#I 第一个括号里面的内容
print f1.group(2);#love 第二个括号里面的内容
f2=re.findall('xx(.*?)xx123xx(.*?)xx',s2);
print f2;#[('I', 'love')] 如果遇到匹配的第二个，将以元组的形式在列表中显示第二个
print f2[0]; #('I', 'love')
print f2[0][1]; #love

#sub：将符合条件的内容用后面的内容替换
s3='123assdfghh123'
f3=re.sub('123(.*?)123','123aaa123',s3);
print f3;#123aaa123
f4=re.sub('123(.*?)123','123%s123'%'aaa',s3);
print f4;#123aaa123
f5=re.sub('123(.*?)123','123%d123'%666,s3);
print f5;#123666123

#不要使用compile #因为多此一举--findall方法里面已经有这个
pat='xx(.*?)xx'
pat1=re.compile(pat,re.S)
out=re.findall(pat1,code)
print out #['I', 'love', 'you']

#匹配数字
ha='dsaakdsj676djsi1213rer'
hb=re.findall('(\d+)',ha)
print hb #['676', '1213']
```
相关技巧：
import re
from re import *
from re import findall,search,sub,S
不需要complie
使用\d+匹配纯数字

总结:
一个符号组合:(.*?)
三个方法：findall,search,sub

3.正则表达式实例
----------
写一个a.txt如下
```
<html>
   <head>
    <title>网络爬虫</title>
   </head>
   <body>
    <div class="div1"><a href="http://bestzhangjin.com">我的博客</a>
    <div class="list">
     <ul>
      <li><a href="http://bestzhangjin.com/1.html">第一条</a></li>
      <li><a href="http://bestzhangjin.com/2.html">第二条</a></li>
      <li><a href="http://bestzhangjin.com/3.html">第三条</a></li>
     </ul>
    </div>
   </div>
  </body>
</html>
```
可以从上面爬取内容
```
#coding=utf-8
#导入re库文件
import re

f=open('a.txt','r')
html=f.read()
f.close()

#爬取标题 #search只找第一个，节约时间
title=re.search('<title>(.*?)</title>',html,re.S).group(1)
print title #网络爬虫

#爬取链接
links=re.findall('href="(.*?)"',html,re.S)
for each in links:
    print each
#输出：
#http://bestzhangjin.com
#http://bestzhangjin.com/1.html
#http://bestzhangjin.com/2.html
#http://bestzhangjin.com/3.html

#抓取文字
#先爬大再爬小 可以限定范围
text=re.findall('<ul>(.*?)</ul>',html,re.S)[0]
text1=re.findall('">(.*?)</a>',text,re.S)
for each_text in text1:
    print each_text

#sub实现翻页
old_url='http://bestzhangjin.com/?pageNum=1'
#爬取网页
total_page=6 #总页数
for i in range(2,total_page+1):
    link=re.sub('pageNum=\d+','pageNum=%d'%i,old_url,re.S)
    print link
#输出:
# http://bestzhangjin.com/?pageNum=2
# http://bestzhangjin.com/?pageNum=3
# http://bestzhangjin.com/?pageNum=4
# http://bestzhangjin.com/?pageNum=5
# http://bestzhangjin.com/?pageNum=6
```

4.制作文本爬虫
------------
目标：
提取网站http://www.jikexueyuan.com/的课程图片
原理：
(1)保存网页源代码
(2)python读文件加载源代码
(3)正则表达式提取图片网址
(4)下载图片

网页http://www.jikexueyuan.com/如下，有较多图片
热门推荐，最新课程等等下面都有图片
![image](img/python/19.png)
鉴于还有一些知识没学，这里将http://www.jikexueyuan.com/页面的部分需要的代码复制到source.txt
输入网址view-source:http://www.jikexueyuan.com/可以得到对应网页的源码
我这里将源码全部复制粘贴到source.txt中
这里requests的安装详见附录
test.py如下：
```
#coding=utf-8
#导入re库文件
import re
import requests #这里用来保存图片

f=open('source.txt','r')
html=f.read()
f.close()

#匹配图片网址
url=re.findall('img src="(.*?)" class="lessonimg"',html,re.S) #查找条件
i=0
for each in url:
    print 'loding: '+each
    pic=requests.get(each)
    fp=open('pic\\'+str(i)+'.jpg','wb')
    fp.write(pic.content)
    fp.close()
    i+=1
```
运行后结果如下：
![image](img/python/20.png)

第十一章 单线程爬虫
=====================
1.Requests介绍
--------
Requests：HTTP for Humans
完美替代python的urllib2模块

2.第一个网页爬虫
-----------
使用Requests获取网页源代码，利用正则表达式获取自己想要的内容。
直接获取源代码或者修改http头获取源代码。
三行获取源代码：
```
#coding=utf-8
#导入re库文件
import requests
#爬取python百度贴吧的源代码
html=requests.get('http://tieba.baidu.com/f?ie=utf-8&kw=python')
print html.text
```
运行如下：
![image](img/python/22.png)
但不是这三行能够获得所有网页的源代码；
因为一个网站会对访问它的程序进行检查，防止网络爬虫，所以需要伪装。伪装相当于让网站以为你是浏览器请求而非爬虫。
网页User-Agent获取方法：
打开要爬取的网页，右键选择审查元素->Network->Network下面左边随便选择找到右边对应的User-Agent。
![image](img/python/23.png)
如下则可伪装爬取网页源码：
```
#coding=utf-8
#导入re库文件
import requests
#爬取如下网站的源代码
#html=requests.get('http://jp.tingroom.com/yuedu/yd300p/')
header={'User-Agent':'Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/38.0.2125.122 Safari/537.36 SE 2.X MetaSr 1.0'}
html=requests.get('http://jp.tingroom.com/yuedu/yd300p/',headers=header)
html.encoding='utf-8'
print html.text
```
内容提取：使用正则表达式获得我们想要的内容
```
#coding=utf-8
#导入re库文件
import requests
import re
#爬取如下网站的源代码
#html=requests.get('http://jp.tingroom.com/yuedu/yd300p/')
header={'User-Agent':'Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/38.0.2125.122 Safari/537.36 SE 2.X MetaSr 1.0'}
html=requests.get('http://jp.tingroom.com/yuedu/yd300p/',headers=header)
html.encoding='utf-8'
title=re.findall('color:#666666;">(.*?)</span>',html.text,re.S)
for each in title:
    print each
#输出
#第二章 昔々、といってもせいぜい二十年ぐらい前のことなのだ...
#挪威的森林（中日对照） 内容简介： 汉堡机场一曲忧郁的《挪...
#藤野先生名文选读中日文对照 東京も格別のことはなかつた。上..
#...
```

3.向网页提交数据
----------
Get与Post介绍；分析目标网站；Requests的表单提交
Get是从服务器上获取数据，Post是向服务器传送数据；
Get通过构造url中的参数来实现功能，Post将数据放在header提交数据。
向网页提交数据-Requests表单提交：
核心方法：requests.post;
核心步骤:构造表单-提交表单-获取返回信息

有些网页如下：
![image](img/python/24.png)
点击show more显示更多，但是网页地址不会变。因为其使用了异步加载的技巧。
异步加载：先把网页的一些基本框架加载起来，然后剩下的信息需要哪里就加载哪里，可以大大提高网页的加载效率；
好比吃饭时做好一个菜上一个而非所有菜都好啦才上。
正是由于异步加载原因，我们利用原方法只能加载最开始显示的而不能加载点击show more显示的内容。
解决方法如下：
网页右键点击审查元素->network发现是空的，但是点击SHOW MORE之后如下：
![image](img/python/25.png)
点击出现的信息(图中左下角)如下：
![image](img/python/26.png)
说明采用了post向上一行的url地址提交了数据。继续往下有：
![image](img/python/27.png)
可以看到page:2 再点击show more有page:3 以此类推。
如下代码只能显示初始加载的源码：
```
#coding=utf-8
import requests
url='https://www.crowdfunder.com/browse/deals'
html=requests.get(url).text
print html
```
而如下改进后代码则可以根据'page':'1'#这里1可以换2,3,4...得到show more后的源代码。
```
#coding=utf-8
import requests
import re
url='https://www.crowdfunder.com/browse/deals&template=false'
data={
    'entities_only':'true',#这里true是字符串不是布尔值
    'page':'1' #这里1可以改为2,3,...
}

html_post=requests.get(url,data=data)
title=re.findall('"card-title">(.*?)</div>',html_post.text,re.S)
for each in title:
    print each
```
上面代码：'page':'1' #这里1可以改为2,3,...
可以通过改变page后面的值为几得到第几次show more显示内容的源代码

4.极客学院课程爬虫
-----------
目标网站：http://www.jikexueyuan.com/course/
目标内容：获取前10页的课程名称，课程介绍，课程时间，课程等级，学习人数
知识点：Requests获取网页，re.sub换页，正则表达式匹配内容

目标网页如下：
![image](img/python/28.png)
第一页的网址和http://www.jikexueyuan.com/course/内容一样，第二页网址为http://www.jikexueyuan.com/course/?pageNum=2，以此类推。
点击开发者工具或者右键审查元素，如下再点击放大镜图标，之后点击网页上内容会跳到对应内容的代码，方便查看。
![image](img/python/29.png)
当然，点击代码也可以找到相应的页面内容。
分析代码以及与原网页对应课程对比如下：
![image](img/python/30.png)
![image](img/python/31.png)
for循环一一爬取可能会报错（如遇到没有课程说明的情况），这时候考虑先爬大再爬小的方法。
课程列表如下，可以从抓大着手：
![image](img/python/32.png)
可以通过输出获取的源代码利用相应的正则表达式技巧获得需要的内容
程序如下：
```
#coding=utf-8
import requests
import re
import sys
#这里的import语句其实并不是sys的第一次导入语句，也就是说这里其实可能是第二、三次进行sys模块的import，这里只是一个对sys的引用，只能reload才能进行重新加载。
reload(sys)
sys.setdefaultencoding("utf-8");#修改编码方式和网页一样，不然中文乱码

class spider(object):
    def __init__(self):
        print u'开始爬取内容...'
    def getsource(self,url):
        html=requests.get(url)
        return html.text
    def changepage(self,url,total_page):
        now_page=int(re.search('pageNum=(\d+)',url,re.S).group(1))
        page_group=[]
        for i in range(now_page,total_page+1):#因为range包含下边不包含上边的 所以用total_page+1
            link=re.sub('pageNum=\d+','pageNum=%s'%i,url,re.S)
            page_group.append(link)
        return page_group
    def geteveryclass(self,source):#获取每一门课程
        text = re.findall('<ul class="cf" style="display: block;">(.*?)</ul>',source, re.S)[0]
        print text
#  **************# 注意: 这里 .*? 不可以用 （.*?） 具体原因现在还没弄明白
        everyclass=re.findall('(<li.*?</li>)',text,re.S)
        print everyclass
        return everyclass
    def getinfo(self,eachclass):
        info={} #定义字典
        txt=re.search('<h2 class="lesson-info-h2">(.*?)</h2>',eachclass,re.S).group(1)
        print txt
        info['title']=re.search('">(.*?)</a>',txt,re.S).group(1)
        print info['title']
        info['content']=re.search('<p style="height: 0px; opacity: 0; display: none;">\n\t\t\t(.*?)\n\t\t</p>',eachclass,re.S).group(1)
        print info['content']
        timeandlevel=re.findall('<em>(.*?)</em>',eachclass,re.S)
        info['classtime']=timeandlevel[0]
        info['classlevel']=timeandlevel[1]
        info['learnnum']=re.search('"learn-number">(.*?)</em>',eachclass,re.S).group(1)
        return info
    def saveinfo(self,classinfo):
        #f=open('info.txt','a') #'a'追加内容
        f=open('info.txt', 'w')  # 'w'写，没有时创建，有时清空内容再写入  'r'读
        for each in classinfo:
            f.writelines('title:'+each['title']+'\n')
            f.writelines('content:'+each['content']+'\n')
            f.writelines('classtime:'+each['classtime']+'\n')
            f.writelines('classlevel:'+each['classlevel']+'\n')
            f.writelines('learnnum:'+each['learnnum']+'\n\n')
        f.close()

if __name__ =='__main__':#如果本程序自己运行
    classinfo=[] #创建一个列表用来存放课程信息
    url='http://www.jikexueyuan.com/course/?pageNum=1'
    jikespider=spider()
    all_links=jikespider.changepage(url,10)
    for link in all_links:
        print u'正在处理页面：'+link
        html=jikespider.getsource(link)
        everyclass=jikespider.geteveryclass(html)
        for each in everyclass:
            info=jikespider.getinfo(each)
            classinfo.append(info)
        jikespider.saveinfo(classinfo)
```
运行结果如下：
![image](img/python/33.png)




第十二章 XPath与多线程爬虫
==================================
1.XPath介绍与配置
-----------
XPath是一门语言，可以在XML文档中查找信息
XPath支持HTML，XPath通过元素和属性进行导航
XPath可以用来提取信息，比正则表达式更加厉害，简单

安装lxml库：直接cmd下用pip install lxml即可
用法：
```
from lxml import etree
Selector=etree.HTML(网页源代码)
Selector.xpath(一段神奇的符号)
```

2.XPath的使用
------------
正则表达式与XPath的比喻：
正则表达式：极客大楼的左边是三角形大楼，右边是正方形大楼，全世界去找
XPath：极客大楼在北京xx路xx号

XPath与HTML结构：
树状结构；逐层展开；逐层定位；寻找独立节点。

网页实例(index.html):
```
<!DOCTYPE html>
<html>
<head lang="en">
	<meta charset="utf-8" />
    <title>XPath用法</title>
</head>

<body>
<div id="content">
	<ul id="useful">
    	<li>第一条信息</li>
        <li>第二条信息</li>
        <li>第三条信息</li>
    </ul>
    <ul id="useless">
    	<li>不需要信息1</li>
        <li>不需要信息2</li>
        <li>不需要信息3</li>
    </ul>
    
    <div id="url">
    	<a href="http://bestzhangjin.com">我的博客</a>
        <a href="http://jikexueyuan.com" title="极客学院课程库">极客学院</a>
    </div>
</div>
</body>
</html>
```

获取网页的XPath方法：手动分析法；Chrome生成法
手动分析法：html->body->div->ul[@useful]->li
Chrome生成法://*[@id="useful"]/li

Chrome生成法获取技巧：
![image](img/python/34.png)
在浏览器中打开index.html选择审查元素；选中需要的元素如图中li的第一条信息右键copy xpath即可得到//*[@id="useful"]/li[1]
//*[@id="useful"]/li则可以得到id="useful"元素的所有li中内容。

//:定位根节点
/:往下层寻找
提取文本内容:/text()
提取属性内容:/@xxxx

提取一般内容程序：
```
#coding=utf-8
from lxml import etree
html='''
<!DOCTYPE html>
<html>
<head lang="en">
	<meta charset="utf-8" />
    <title>XPath用法</title>
</head>

<body>
<div id="content">
	<ul id="useful">
    	<li>第一条信息</li>
        <li>第二条信息</li>
        <li>第三条信息</li>
    </ul>
    <ul id="useless">
    	<li>不需要信息1</li>
        <li>不需要信息2</li>
        <li>不需要信息3</li>
    </ul>

    <div id="url">
    	<a href="http://bestzhangjin.com">我的博客</a>
        <a href="http://jikexueyuan.com" title="极客学院课程库">极客学院</a>
    </div>
</div>
</body>
</html>
'''
selector=etree.HTML(html)
#提取文本
content=selector.xpath('//ul[@id="useful"]/li/text()')
for each in content:
    print each
#输出结果：
#第一条信息
#第二条信息
#第三条信息

#提取属性
link=selector.xpath('//a/@href')#从a标签开始寻找其下面的href属性
for each in link:
    print each
#输出结果:
#http://bestzhangjin.com
#http://jikexueyuan.com

#提取a标签里面的title
title=selector.xpath('//a/@title')
#返回结果title是一个列表
print title  ##[u'\u6781\u5ba2\u5b66\u9662\u8bfe\u7a0b\u5e93']
for each in title:
    print each  #极客学院课程库
print title[0]  #极客学院课程库
```

3.xpath特殊使用
---------------
情况：(1)以相同字符开头；(2)标签套标签。
(1)以相同字符开头
方法：starts-with(@属性名称，属性字符相同部分)
eg：
```
<div id="test-1">内容1</div>
<div id="test-2">内容2</div>
<div id="test-3">内容3</div>
```

(2)标签套标签
方法:string(.)
eg：
```
<div id="class">你好，
	<font color=red>你的电话是多少啊?</font>
</div>
```

应用实例:
```
#coding=utf-8
from lxml import etree
html='''
<!DOCTYPE html>
<html>
<head lang="en">
	<meta charset="utf-8" />
    <title>XPath用法</title>
</head>

<body>
    <div id="test1">内容1</div>
    <div id="test2">内容2</div>
    <div id="test3">内容3</div>

    <div id="long">
        我左青龙
        <span id="tiger">
            右白虎
            <ul>上朱雀,
                <li>下玄武。</li>
            </ul>
            老牛在当中,
        </span>
        龙头在胸口。
    </div>
</body>
</html>
'''
selector=etree.HTML(html)
#以相同字符开头 提取文本
content=selector.xpath('//div[starts-with(@id,"test")]/text()')
for each in content:
    print each
#  输出：
# 内容1
# 内容2
# 内容3

#标签套标签 提取其中的所有文字
#如下方法只能提取div中内容，div中标签中内容不可提取
content1=selector.xpath('//div[@id="long"]/text()')
for each in content1:
    print each
#输出:
#我左青龙

#龙头在胸口。
# **************应该用如下方法
data=selector.xpath('//div[@id="long"]')[0] #列表只有一个元素 故用[0]
print data #输出: <Element div at 0x2955bc8>
info=data.xpath('string(.)')
print info
# 输出:
#我左青龙
#
#右白虎
#上朱雀,
#下玄武。
#
#老牛在当中,
#
#龙头在胸口。
content2=info.replace('\n','').replace(' ','')#\n和' '用''替代
print content2
#输出:
#我左青龙右白虎上朱雀,下玄武。老牛在当中,龙头在胸口。
```

4.Python 并行化介绍与演示
------------------
并行化(多线程)和Map的使用。
Python由于历史原因，多线程不是真正的多线程，但仍然可以提高爬虫的效率，下面进入主题。
多个线程同时处理：高效快速
Map函数包办了序列操作，参数传递和结果保存等一系列操作。
应用:
```
from multiprocessing.dummy import Pool
pool=Pool(4) #这里4代表电脑4核的 8核电脑可以换成8速度更快
results=pool.map(爬取函数,网址列表)
```
实例：
```
#coding=utf-8
from multiprocessing.dummy import Pool as ThreadPool
import requests
import time

def getsource(url):
    html=requests.get(url)

urls=[]

for i in range(1,21):
    newpage='http://tieba.baidu.com/p/3522395718?pn=' + str(i)
    urls.append(newpage)

time1=time.time()
for i in urls:
    #print i
    getsource(i)
time2=time.time()
print u'单线程耗时:'+str(time2-time1)

pool=ThreadPool(4)
time3=time.time()
#使用map函数连接函数和列表
results=pool.map(getsource,urls)
pool.close()
pool.join()
time4=time.time()
print u'多线程耗时:'+str(time4-time3)

#************输出
#单线程耗时:12.7400000095
#多线程耗时:4.02600002289
```

5.百度贴吧爬虫
-------------
目标网站:http://tieba.baidu.com/p/3522395718
目标内容:跟帖用户名,跟帖内容，跟帖时间
知识点：
Requests获取网页
XPath提取内容
map实现多线程爬虫

(1)打开网页发现网站第i页就是http://tieba.baidu.com/p/3522395718?pn=i
(2)源码分析
![image](img/python/35.png)
![image](img/python/36.png)
(3)程序
```
#coding=utf-8
from multiprocessing.dummy import Pool as ThreadPool
import requests
import json#因为源码中有json格式 当然也可以用正则表达式解析
from lxml import etree
import sys
reload(sys)

sys.setdefaultencoding('utf-8')

def towrite(contentdict):
    f.writelines(u'回帖时间:'+str(contentdict['topic_reply_time'])+'\n')
    f.writelines(u'回帖内容:'+unicode(contentdict['topic_reply_content'])+'\n')
    f.writelines(u'回帖人:'+contentdict['user_name']+'\n\n')

def spider(url):
    html=requests.get(url)
    selector=etree.HTML(html.text)
    content_filed=selector.xpath('//div[@class="l_post j_l_post l_post_bright  "]')
    item={}
    for each in content_filed:
        reply_info=json.loads(each.xpath('@data-field')[0].replace('&quot',''))
        print reply_info
        author=reply_info['author']['user_name']
        print author
        content=each.xpath('div[@class="d_post_content_main"]/div/cc/div[@class="d_post_content j_d_post_content  clearfix"]/text()')[0]
        print content
        reply_time=reply_info['content']['date']
        print reply_time
        item['user_name']=author
        item['topic_reply_content']=content
        item['topic_reply_time']=reply_time
        towrite(item)

if __name__=='__main__':
    pool=ThreadPool(4)
    f=open('content.txt','w')
    page=[]
    for i in range(1,21):
        newpage='http://tieba.baidu.com/p/3522395718?pn='+str(i)
        page.append(newpage)
       # spider(newpage)
        print newpage
    print page
    results=pool.map(spider,page)
    pool.close()
    pool.join()
    f.close()
```
运行结果:
![image](img/python/37.png)


第十三章 Python操作数据库——MySQL篇
=========================
1.数据库种类概述
--------------
数据库分类：
(1)SQL:结构化查询语言和NoSQL:泛指非关系型数据库
(2)单机(数据库运行在一台机器上)和分布式(数据库运行在服务器集群上)
(3)文件型(数据放硬盘)和内存型(数据放内存里)
(4)批处理(将SQL分成MR任务)和分布式(分级查询之后汇总)
![image](img/python/38.png)
![image](img/python/39.png)
![image](img/python/40.png)
mysql也可以搭分布式，只是用的少
![image](img/python/41.png)
![image](img/python/42.png)
云平台AWS（亚马逊）：
![image](img/python/43.png)

2.MySQL 概述及基本使用
----------------
可以用AWS(亚马逊)中启动MYSQL，免费用一年，但是注册需要信息较多，这里直接用自己电脑上的mysql讲解，mysql部分见博客的mysql.
mysql安装见博客mysql部分；mysql驱动安装见附录。
这里










附录：工具包安装
=================
1.easy_install
------------
easy_install是一个python的扩展包，主要是用来简化python安装第三方安装包，在安装了easy_install之后，安装python第三方安装包就只需要在命令行中输入：easy_install packagename，然后程序会自动搜索相应版本的安装包并配置各种文件，免去了手工下载安装的复杂度。
搜索easy_install	下载文件ez_setup.py
cmd下python ez_setup.py就可以安装成功
然后就会在python的安装目录中生成scripts目录，其中有easy_install.exe
将scripts目录配置环境变量到path就可以用啦
备注：少使用easy_install，因为easy_install只能安装不能卸载
一般安装用pip.

2.pip
------------
pip install packagename可以安装工具包
cmd下easy_inatall pip安装好pip就可以直接用

3.requests
-----------
requests是python的一个HTTP客户端库。
win系统，下载了安装包（网页中download the zipball处链接），然后$ python setup.py install就装好了。
当然，有easy_install或pip的朋友可以直接使用：easy_install requests或者pip install requests来安装。
在IDLE中输入import requests，如果没提示错误，那说明已经安装成功了！

4.mysql驱动
----------------
网站http://www.lfd.uci.edu/~gohlke/pythonlibs/#mysql-python
下载MySQL_python-1.2.5-cp27-none-win_amd64.whl
在下载目录下运行pip install MySQL_python-1.2.5-cp27-none-win_amd64.whl


附录：常见问题解决
=====================
1.撞墙解决方法
-----------
撞墙用如下网站：这里有基本上的python第三方库
http://www.lfd.uci.edu/~gohlke/pythonlibs/
进入网页使用Ctrl+f可以进行搜索下载：
![image](img/python/21.png)
可以下载得到一个后缀名为.whl的文件
下载完后将后缀名.whl改为.zip然后解压将解压的文件夹放到python安装目录的Lib目录下即可。

2.easy_install 或者pip 安装时出现unable to find vcvarsall.bat
--------------------------------
很多python 库实际上使用c或者c++写的，所以安装编译时会需要用到msvc的东西；如果你的机器里没有装VS或者注册表设置不太对的话，就会报错。
微软出了一个msi包来解决这个问题： 
Microsoft Visual C++ Compiler for Python 2.7
下载地址：
http://www.microsoft.com/en-us/download/details.aspx?id=44266 















