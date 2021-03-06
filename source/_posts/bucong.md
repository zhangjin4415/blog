title: 孤陋寡闻
date: 2016-10-20 10:40:20
categories: "知识补充"
tags: "孤陋寡闻"
---
千里之行始于足下，千里之堤溃于蚁穴
<!--more-->

位域
----------
引用自：http://bbs.csdn.net/topics/330120699
有些信息在存储时，并不需要占用一个完整的字节， 而只需占几个或一个二进制位。例如在存放一个开关量时，只有0和1 两种状态， 用一位二进位即可。为了节省存储空间，并使处理简便，Ｃ语言又提供了一种数据结构，称为“位域”或“位段”。所谓“位域”是把一个字节中的二进位划分为几个不同的区域， 并说明每个区域的位数。每个域有一个域名，允许在程序中按域名进行操作。 这样就可以把几个不同的对象用一个字节的二进制位域来表示。一、位域的定义和位域变量的说明位域定义与结构定义相仿，其形式为： 
struct 位域结构名 
{ 位域列表 };
其中位域列表的形式为： 类型说明符 位域名：位域长度 
例如： 
struct bs
{
int a:8;
int b:2;
int c:6;
};
位域变量的说明与结构变量说明的方式相同。 可采用先定义后说明，同时定义说明或者直接说明这三种方式。例如： 
struct bs
{
int a:8;
int b:2;
int c:6;
}data;
说明data为bs变量，共占两个字节。其中位域a占8位，位域b占2位，位域c占6位。对于位域的定义尚有以下几点说明：

1. 一个位域必须存储在同一个字节中，不能跨两个字节。如一个字节所剩空间不够存放另一位域时，应从下一单元起存放该位域。也可以有意使某位域从下一单元开始。例如： 
struct bs
{
unsigned a:4
unsigned :0 /*空域*/
unsigned b:4 /*从下一单元开始存放*/
unsigned c:4
}
在这个位域定义中，a占第一字节的4位，后4位填0表示不使用，b从第二字节开始，占用4位，c占用4位。

2. 由于位域不允许跨两个字节，因此位域的长度不能大于一个字节的长度，也就是说不能超过8位二进位。

3. 位域可以无位域名，这时它只用来作填充或调整位置。无名的位域是不能使用的。例如： 
struct k
{
int a:1
int :2 /*该2位不能使用*/
int b:3
int c:2
};
从以上分析可以看出，位域在本质上就是一种结构类型， 不过其成员是按二进位分配的。

二、位域的使用位域的使用和结构成员的使用相同，其一般形式为： 位域变量名·位域名 位域允许用各种格式输出。
main(){
struct bs
{
unsigned a:1;
unsigned b:3;
unsigned c:4;
} bit,*pbit;
bit.a=1;
bit.b=7;
bit.c=15;
printf("%d,%d,%d\n",bit.a,bit.b,bit.c);
pbit=&bit;
pbit->a=0;
pbit->b&=3;
pbit->c|=1;
printf("%d,%d,%d\n",pbit->a,pbit->b,pbit->c);
} 
上例程序中定义了位域结构bs，三个位域为a,b,c。说明了bs类型的变量bit和指向bs类型的指针变量pbit。这表示位域也是可以使用指针的。
程序的9、10、11三行分别给三个位域赋值。( 应注意赋值不能超过该位域的允许范围)程序第12行以整型量格式输出三个域的内容。第13行把位域变量bit的地址送给指针变量pbit。第14行用指针方式给位域a重新赋值，赋为0。第15行使用了复合的位运算符"&="， 该行相当于： pbit->b=pbit->b&3位域b中原有值为7，与3作按位与运算的结果为3(111&011=011,十进制值为3)。同样，程序第16行中使用了复合位运算"|="， 相当于： pbit->c=pbit->c|1其结果为15。程序第17行用指针方式输出了这三个域的值。

链表回路问题
-------------------
来自：http://www.cnblogs.com/kqingchao/archive/2011/07/06/whether_there_is_a_loop_in_link.html
如果你曾经想过要参加面试，像我一样，你一定看过这个问题：如何判断链表中存在环路。（我不太清楚这个问题的应用在哪里，烦请各位读者能够提示一下。）

先简单说一下我之前看到的方法。

方法一：蛮力法。

方法二：在链表中增加一个域visited，初始化都为0，从链表的头部开始走，每走过一个链表就标记visited为1，如果要访问的下一个节点的visited域为1，那么证明链表中有环。

方法三：如果不能增加域，可以设置一个数组，将已经访问的链表节点依次放入到数组中，在访问下一个节点时，如果这个节点的地址已经在数组中，那么也能证明链表中有环。

进入正题之前，先简单说一下今天的面试。今天下午我参加面试的时候也被问到了这个问题，面试官是个南开的MM。似乎她也意识到诸如此类的问题已经在网上司空见惯，所以就试探性的问我是不是之前已经在网上看到了方法。我很老实，回答：嗯。我俩相视而笑。

然后，她又问我一个问题：如何找到一个链表的中间元素？我想了想，灵光一闪，说：设置两个指针p和q，p一次走一下，q一次走两下，这样当q走到链表的尾部的时候，p应该正好走到链表的中间（我当时很佩服我自己。。。）。那个MM笑了一下，表示赞同，接下来随口的一句话把我带入了漩涡：嗯，刚才那个判断链表是否有环的问题也可以用这个方法。顿时，我脸上呈现出迷茫的表情，好奇心驱使着我问道：真的？MM一看我竟然不知道这个方法，说：哦，原来你不知道啊！正好，你想想用你刚才说的方法解决一下链表有环的问题。同志们，好奇心害死猫啊！

然后我就囧了，折腾了半天，画了个链表，在上面试着画了一下，发现如果链表有环，有可能q会追上p，相当与长跑中的套圈。但是，有一个问题：p是不是一定会和q重合？

这个问题看起来有些复杂，我们现在来抽象一下，这个问题不是很难。

假设此时p点刚刚进入到链表中的环中，q在环中的某一个位置，如图所示。
![image](img/bucong/1.png)
设t时间后，p和q在环中的某一点相遇，初始时p和q相隔k个节点（0<=k<=n-1，其中n为环中的节点数；图中p和q相隔3个节点，而不是2个：因为假如q不动，p需要经过3步移动才可以和q重合），那么可得：

t(mod n) = k + 2t(mod n)

那么，对任意的正整数m，使得：t + mn  = k + 2t

那么显然此时 t = mn-k，m>=1。

靠！原来这么简单。。。