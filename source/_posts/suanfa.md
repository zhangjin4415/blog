title: 数据结构与算法
date: 2016-10-07 21:45:02
categories: "数据结构与算法"
tags: ["算法","数据结构"]
---
主要内容：各种算法总结
<!--more-->

一.数据结构
=============
1.介绍
---------
数据之间三种基本数据结构：
线性结构：数据元素之间一对一关系；
树形结构：数据元素之间一对多关系；
网状结构：数据元素之间多对多关系。

2.线性表
-------
线性表分顺序表和链表；
顺序表存储位置是相邻连续的，可以随即访问的一种数据结构，一个顺序表在使用前必须指定起长度，一旦分配内存，则在使用中不可以动态的更改。他的优点是访问数据是比较方便，可以随即的访问表中的任何一个数据。
链表是通过指针来描述元素关系的一种数据结构，他可以是物理地址不连续的物理空间。不能随即访问链表元素，必须从表头开始，一步一步搜索元素。它的优点是：对于数组，可以动态的改变数据的长度，分配物理空间。
在使用中：如果一个数组在使用中，查询比较多，而插入，删除数据比较少，数组的长度不变时，选顺序表比较合理。如果插入，删除，长度不定的数组，可以选链表。

(1)顺序表
```
#include<stdio.h>
#define MAXSIZE 100 //顺序表最大长度

//定义数据类型 数据节点类型
typedef struct{
    char key[16];
    char name[16];
    int age;
} DATA;

//定义顺序表结构
typedef struct{
    DATA ListData[MAXSIZE+1];//保存顺序表的数组
    int ListLen;//已经存储的节点数量
}SeqList;

//初始化顺序表
void SeqListInit(SeqList *SL){
    SL->ListLen=0;//清空表
}

//长度查询
int SeqListLength(SeqList *SL){
    return SL->ListLen;
}

//添加节点
int SeqListADD(SeqList *SL,DATA data){
    if(SL->ListLen>=MAXSIZE){
        printf("表满，不可添加!");
        return 0;
    }
    SL->ListData[++SL->ListLen]=data;//在表后面添加数据同时len+1
    return 1;
}

//插入节点
int SeqListInsert(SeqList *SL,int n,DATA data){
    int i;
    if(SL->ListLen==MAXSIZE){
        printf("表满,不可插入节点!");
        return 0;
    }
    if(n<1||n>SL->ListLen-1){//插入序号不对
        printf("插入节点序号错误，不能插入!");
        return 0;
    }
    for(i=SL->ListLen;i>=n;i--){//数据后移
        SL->ListData[i+1]=SL->ListData[i];
    }
    SL->ListData[n]=data;
    SL->ListLen++;
    return 1;
}

//删除节点
int SeqListDelete(SeqList *SL,int n){
    int i;
    if(n<1||n>SL->ListLen+1){
        printf("输入节点序号错误，不能删除节点!");
        return 0;
    }
    for(i=n;i<SL->ListLen;i++)//数据表前移
        SL->ListData[i]=SL->ListData[i+1];
    SL->ListLen--;
    return 1;
}

//按序号查找节点
DATA *SeqListFindByNum(SeqList *SL,int n){
    if(n<1 || n>SL->ListLen+1){
        printf("节点序号错误，不能返回节点!");
        return NULL;
    }
    /*************/
    return &(SL->ListData[n]);//返回找到节点的指针
}

//按关键字（这里用key）查找节点
int SeqListFindByKey(SeqList *SL,char *key){
    int i;
    for(i=1;i<=SL->ListLen;i++){
        // /////////////////////
        if(strcmp(SL->ListData[i].key,key)==0)//查到节点
            return i;
    }
    return 0;
}

//遍历输出
int SeqListAll(SeqList *SL){
    int i;
    for(i=1;i<=SL->ListLen;i++){
        printf("(%s,%s,%d)\n",SL->ListData[i].key,SL->ListData[i].name,SL->ListData[i].age);
    }
}

int main(){
    int i;
    SeqList SL;
    DATA data,*data1;
    char key[16];

    SeqListInit(&SL);

    do{
        printf("输入添加的节点(学号 姓名 年龄)：");
        fflush(stdin);//清空输入缓冲区
        scanf("%s%s%d",&data.key,&data.name,&data.age);
        if(data.age){
            if(!SeqListADD(&SL,data))//添加节点失败
                break;
        }else{//年龄为0时退出死循环
            break;
        }
    }while(1);
    printf("\n顺序表中的数据为:\n");
    SeqListAll(&SL);

    fflush(stdin);
    printf("\n要取出节点的序号:");
    scanf("%d",&i);
    data1=SeqListFindByNum(&SL,i);
    if(data1)
        printf("第%d个节点为:(%s,%s,%d)\n",i,data1->key,data1->name,data1->age);
    fflush(stdin);
    printf("\n要查找节点的关键字:");
    scanf("%s",key);
    i=SeqListFindByKey(&SL,key);
    data1=SeqListFindByNum(&SL,i);
    if(data1)
        printf("第%d个节点为:(%s,%s,%d)\n",i,data1->key,data1->name,data1->age);
    return 1;
}

output:
输入添加的节点(学号 姓名 年龄)：1 liming 23
输入添加的节点(学号 姓名 年龄)：2 wanghua 21
输入添加的节点(学号 姓名 年龄)：3 nisan 14
输入添加的节点(学号 姓名 年龄)：0 0 0

顺序表中的数据为:
(1,liming,23)
(2,wanghua,21)
(3,nisan,14)

要取出节点的序号:1
第1个节点为:(1,liming,23)

要查找节点的关键字:2
第2个节点为:(2,wanghua,21)
```

(2)链表
链表有单向链表、双向链表、循环链表
A.单向链表
```
#include <stdio.h>

//数据类型
typedef struct {
    char key[16];
    char name[16];
    int age;
}DATA;

//链表
typedef struct Node{
    DATA data;
    struct Node *next;
}ChainList;


//添加节点到尾部
ChainList *ChainListAddEnd(ChainList *head,DATA data){
    ChainList *node,*h;
    if(!(node=(ChainList *)malloc(sizeof(ChainList)))){//为节点分配空间
        printf("为节点数据申请内存失败!\n");
        return NULL;
    }
    node->data=data;
    node->next=NULL;
    if(head==NULL){
        head=node;
        return head;
    }
    h=head;
    while(h->next!=NULL){
        h=h->next;//找到尾部
    }
    h->next=node;//尾部插入数据
    return head;
}

//添加节点到头部
ChainList *ChainListAddFirst(ChainList *head,DATA data){
    ChainList *node,*h;
    if(!(node=(ChainList *)malloc(sizeof(ChainList)))){//为节点分配空间
        printf("为节点数据申请内存失败!\n");
        return NULL;
    }
    node->data=data;
    node->next=head;
    head=node;
    return head;
}

//查找节点 按关键字key
ChainList *ChainListFind(ChainList *head,char *key){//注意：这里关键字key用指针 ---- 因为是数组
    ChainList *h;
    h=head;
    while(h){
        if(strcmp(h->data.key,key)==0)//节点关键字与传入关键字对比
            return h;
        h=h->next;
    }
    return NULL;
}

//插入节点
ChainList *ChainListInsert(ChainList *head,char *findkey,DATA data){
    ChainList *node ,*node1;
    if(!(node=(ChainList *)malloc(sizeof(ChainList)))){//为节点分配空间
        printf("为节点数据申请内存失败!\n");
        return NULL;
    }
    node->data=data;
    node1=ChainListFind(head,findkey);
    if(node1){//插入新节点
        node->next=node1->next;
        node1->next=node;
    }else{
        free(node);//  *******************malloc之后没有插入需要释放空间
        printf("没有找到插入口\n");
    }
    return head;
}

//删除节点
int ChainListDeleteByKey(ChainList *head,char *key){
    ChainList *node,*h;
    node=h=head;
    while(h){
        if(strcmp(h->data.key,key)==0){
            node->next=h->next;
            free(h);// ****************释放节点
            return 1;
        }else{
            node=h;// *****指向当前节点
            h=h->next;// 指向下一节点
        }
    }
    return 0;
}

//链表长度
int ChainListLength(ChainList *head){
    ChainList *h;
    int i=0;
    h=head;
    while(h){
        i++;
        h=h->next;
    }
    return i;
}

//遍历
void ChainListAll(ChainList *head){
    ChainList *h;
    DATA data;
    h=head;
    while(h){
        data=h->data;
        printf("(%s,%s,%d)\n",data.key,data.name,data.age);
        h=h->next;
    }
    return;
}


int main(void)
{
    ChainList *node,*head=NULL;
    DATA data;
    char key[16],findkey[16];
    printf("输入链表数据，关键字(为0时停止)、姓名、年龄:\n");
    do{
        fflush(stdin);
        scanf("%s",data.key);
        if(strcmp(data.key,"0")==0)break;
        scanf("%s%d",data.name,&data.age);// 数组本身就是地址 不用加&
        head=ChainListAddEnd(head,data);
    }while(1);
    printf("链表有 %d 个节点:\n",ChainListLength(head));
    ChainListAll(head);
    fflush(stdin);
    printf("\n插入节点，输入位置关键字key：");
    scanf("%s",&findkey);
    fflush(stdin);
    printf("输入插入数据: 关键字 姓名 年龄 :");
    scanf("%s%s%d",data.key,data.name,&data.age);
    head=ChainListInsert(head,findkey,data);
    ChainListAll(head);
}

output:
输入链表数据，关键字(为0时停止)、姓名、年龄:
1 xiaoming 32
2 lixiao 21
3 xuhan 13
0
链表有 3 个节点:
(1,xiaoming,32)
(2,lixiao,21)
(3,xuhan,13)

插入节点，输入位置关键字key：1
输入插入数据: 关键字 姓名 年龄 :4 shendu 80
(1,xiaoming,32)
(4,shendu,80)
(2,lixiao,21)
(3,xuhan,13)
```

B.双向链表
双向链表对比单项链表多了一个指向前边的指针；
可以定义如下：
```
typedef struct Node{
	struct Node *before;
    DATA data;
    struct Node *after;
}ChainList;
```
原理与单向一样。

C.循环链表
循环链表就是单项链表的尾部又指向头部，形成一个循环。


3.队列
--------
先进先出。
只能前端删除，后端添加。插入端为队尾，删除端为队头。
分顺序队列和循环队列。
顺序队列：
```
#include <stdio.h>
#define QUEUEMAX 15

typedef struct{
    int key;
    char name[16];
}DATA;

typedef struct{
    DATA data[QUEUEMAX];//队列数组
    int head;//队头
    int tail;//队尾
}SeqQueue;

//初始化队列
SeqQueue *SeqQueueInit(){
    SeqQueue *q;
    if(q=(SeqQueue *)malloc(sizeof(SeqQueue))){//申请保存队列的内存
        q->head=0;//设置队头
        q->tail=0;//设置队尾
        return q;
    }else
        return NULL;
}

//释放队列
void SeqQueueFree(SeqQueue *q){
    if(q!=NULL)
        free(q);// 释放队列   malloc申请的内存都应该释放
}

//获取状态 空?满?长度?
int SeqQueueIsEmpty(SeqQueue *q){
    return (q->head==q->tail);
}
int SeqQueueIsFull(SeqQueue *q){
    return (q->tail==QUEUEMAX);
}
int SeqQueueLength(SeqQueue *q){
    return (q->tail-q->head);
}

//入队
int SeqQueueIn(SeqQueue *q,DATA data){
    if(q->tail==QUEUEMAX){
        printf("队列满\n");
        return 0;
    }else{
        q->data[q->tail++]=data;//加入队列 修改对尾序号
        return 1;
    }
}

//出队
DATA *SeqQueueOut(SeqQueue *q){
    if(q->head==q->tail){
        printf("\n队列空!\n");
        return NULL;
    }else{
        return &(q->data[q->head++]);//返回指向队列头的元素指针 修改队头序号
    }
}

//遍历
void SeqQueueAll(SeqQueue *q){
    if(SeqQueueIsEmpty(q)){
        printf("队列为空\n");
        return;
    }
    DATA data;
    SeqQueue *h=q;
    while(h->tail-h->head){
        data=h->data[h->head];
        printf("(%d,%s)\n",data.key,data.name);
        h->head++;
    }
}


int main(void)
{
    SeqQueue *head=SeqQueueInit();
    DATA data;
    while(1){
        printf("输入队列元素(key(int),name(char[16])),key=0时退出:");
        scanf("%d",&data.key);
        if(data.key==0)
            break;
        scanf("%s",data.name);
        SeqQueueIn(head,data);
    }
    SeqQueueAll(head);

}

output:
输入队列元素(key(int),name(char[16])),key=0时退出:1 limin
输入队列元素(key(int),name(char[16])),key=0时退出:2 wanghua
输入队列元素(key(int),name(char[16])),key=0时退出:3 xiaoming
输入队列元素(key(int),name(char[16])),key=0时退出:0
(1,limin)
(2,wanghua)
(3,xiaoming)
```

循环队列:
将队列的首尾相连构成一个环形区域，当第n个位置元素入队后，下一个地址就变为1，如此循环，称之为循环队列。
当tail=n+1时，tail=1;
head=tail则队列满。
```
#include <stdio.h>
#define QUEUEMAX 15

typedef struct{
    int num;//编号
    long time;//加入队列时间
}DATA;

typedef struct{
    DATA data[QUEUEMAX];
    int head;
    int tail;
}CycQueue;

//初始化
CycQueue *CycQueueInit(){
    CycQueue *q;
    if(q=(CycQueue *)malloc(sizeof(CycQueue))){//申请保存队列的内存
        q->head=0;
        q->tail=0;
        return q;
    }else
        return NULL;
}

//释放队列
void CycQueueFree(CycQueue *q){
    if(q!=NULL){
        free(q);
    }
}

int CycQueueIsEmpty(CycQueue *q){
    return (q->head==q->tail);
}

int CycQueueIsFull(CycQueue *q){
    return ((q->tail+1)%QUEUEMAX==q->head);
}

int CycQueueIn(CycQueue *q,DATA data){
    if((q->tail+1)%QUEUEMAX==q->head){
        printf("队列满!\n");
        return 0;
    }else{
        q->tail=(q->tail+1)%QUEUEMAX;
        q->data[q->tail]=data;
        return 1;
    }
}

DATA *CycQueueOut(CycQueue *q){//循环出队
    if(q->head==q->tail){
        printf("队列为空!\n");
        return NULL;
    }else {
        q->head=(q->head+1)%QUEUEMAX;
        return &(q->data[q->head]);
    }
}

int CycQueueLen(CycQueue *q){
    int n;
    n=q->tail-q->head;
    if(n<0){
        n=QUEUEMAX+n;//循环队列
    }
    return n;
}

DATA *CycQueuePeek(CycQueue *q){//获取队列中的第一个位置的数据
    if(q->head==q->tail){
        printf("队列为空!\n");
        return NULL;
    }else {
        return &(q->data[(q->head+1)%QUEUEMAX]);
    }
}

int num=0;//顾客序号
void add(CycQueue *q){
    DATA data;
    if(!CycQueueIsFull(q)){
        data.num=++num;
        data.time=time(NULL);//保存顾客排号时间
        CycQueueIn(q,data);
    }else{
        printf("\n排队的人太多，请稍后再排!\n");
    }
}

void next(CycQueue *q){
    DATA *data;
    if(!CycQueueIsEmpty(q)){
        data=CycQueueOut(q);//取队列头部数据
        printf("\n请编号为%d的顾客办理业务!\n",data->num);
    }
    if(!CycQueueIsEmpty(q)){
        data=CycQueuePeek(q);//取队列中指定位置的数据
        printf("请编号为%d的顾客准备，马上将为你办理业务!\n",data->num);
    }
}

int main(void)
{
    CycQueue *q;
    int i,n;
    char select;
    num=0;
    q=CycQueueInit();
    if(q==NULL){
        printf("创建队列时错误!\n");
        return 0;
    }
    do{
        printf("\n请输入:1.新到顾客 2.下一个顾客 0.退出");
        fflush(stdin);
        select=getch();
        switch (select) {
        case '1':
            add(q);
            printf("\n现在共有%d位顾客在等候!\n",CycQueueLen(q));
            break;
        case '2':
            next(q);
            printf("\n现在共有%d位顾客在等候!\n",CycQueueLen(q));
            break;
        default:
            break;
        }
    }while(select!='0');
    CycQueueFree(q);//释放队列
    return 0;
}

output:
请输入:1.新到顾客 2.下一个顾客 0.退出
现在共有1位顾客在等候!

请输入:1.新到顾客 2.下一个顾客 0.退出
现在共有2位顾客在等候!

请输入:1.新到顾客 2.下一个顾客 0.退出
请编号为1的顾客办理业务!
请编号为2的顾客准备，马上将为你办理业务!

现在共有1位顾客在等候!
```


4.栈
--------
后进先出；
顺序栈：使用一连续内存地址保存栈中数据；
链式栈：使用链表形式保存栈中各元素的值。
```
#include <stdio.h>
#define SIZE 16

typedef struct{
    char name[15];
    int age;
}DATA;

typedef struct stack{
    DATA data[SIZE+1];//数据元素
    int top;
}SeqStack;

//初始化栈
SeqStack *SeqStackInit(){
    SeqStack *p;
    if(p=(SeqStack *)malloc(sizeof(SeqStack))){
        p->top=0;
        return p;
    }
    return NULL;
}

//释放内存
void SeqStackFree(SeqStack *s){
    if(s){
        free(s);
    }
}

//是否为空
int SeqStackIsEmpty(SeqStack *s){
    return (s->top==0);
}

//清空栈
void SeqStackClear(SeqStack *s){
    s->top=0;
}

//判断栈是否满
int SeqStackIsFull(SeqStack *s){
    return (s->top==SIZE);
}

//入栈
int SeqStackPush(SeqStack *s,DATA data){
    if((s->top+1)>SIZE){
        printf("栈溢出!\n");
        return 0;
    }
    s->data[++s->top]=data;
    return 1;
}

//出栈
DATA SeqStackPop(SeqStack *s){
    if(s->top==0){
        printf("栈为空");
        exit(0);
    }
    return (s->data[s->top--]);
}

//获取栈顶元素
DATA SeqStackPeek(SeqStack *s){
    if(s->top==0){
        printf("栈为空!");
        exit(0);
    }
    return (s->data[s->top]);
}


int main(void)
{
    SeqStack *stack;
    DATA data,data1;
    stack=SeqStackInit();
    while(1){
        printf("1.入栈 2.出栈 3.退出:");
        int i;
        scanf("%d",&i);
        switch (i) {
        case 1:
            printf("输入姓名 年龄入栈:");
            scanf("%s%d",data.name,&data.age);
            if(data.name=="0"||data.age==0)
                break;
            SeqStackPush(stack,data);
            break;
        case 2:
            data1=SeqStackPop(stack);
            printf("出栈数据是(%s,%d)\n",data1.name,data1.age);
            break;
        case 3:
            SeqStackFree(stack);
            exit(1);
            break;
        default:
            break;
        }

    }
}

output:
1.入栈 2.出栈 3.退出:1
输入姓名 年龄入栈:小明 23
1.入栈 2.出栈 3.退出:1
输入姓名 年龄入栈:李华 21
1.入栈 2.出栈 3.退出:2
出栈数据是(李华,21)
1.入栈 2.出栈 3.退出:3
```
  
5.树
------
树是n个节点的集合，集合中有一个称为根的特殊节点，根节点下分布着一些互不相交的集合，每一个集合又是一个树，这些树称为根节点的子树。
空集合也是树，称为空树，空树中没有节点；
单个节点是一棵树，树根就是节点本身；
有多个节点时，每个节点都可以看做根节点(整个树或者某个树的根节点)；
在一棵树中，有且仅有根节点没有前驱，其余每个节点有且只有一个前驱，每个节点有任意多个后继（连接当前节点的接着的后面节点）；
节点的度：一个节点的子树（下面的后继）的数量称为该节点的度；
树的度：一棵树的度是指该树中节点的最大度数；
叶节点：树中度为0的节点；
分支节点：树中度不为0的节点；
根节点为第一层，后面依次第二层、第三层、...
树的深度:一棵树的最大层数；
有序树：树中节点的子树（兄弟节点）是按一定的次序从左到右安排的，称为有序树；否则称为无序树。
森林：m(m>=0)棵互不相交的树的集合。

二叉树：
任意树可以方便地转化为对应的二叉树，二叉树对许多算法应用简单。
二叉树任意节点最多只能有两个子节点，如果只有一个子节点，可以是左子树，也可以是右子树；
空树或者单个节点也是二叉树。

二叉树与树区别：
树中节点最大度数没有限制，而二叉树节点最大度数为2；
树的节点无左右之分，而二叉树的节点有左右之分。

满二叉树：除了最下面一层叶节点，每层的节点都有两个子节点；
完全二叉树：除了最后一层外，其他各层节点数都达到最大个数，最后一层从左到右叶节点连续存在，只缺右边若干个节点。
满二叉树一定是完全二叉树，完全二叉树不一定是满二叉树。
 
二叉树性质:
(1) 第i层节点的总数最多为2^(i-1)个；
(2) 深度为k的二叉树最多有2^k-1个；最少有k个节点；
(3) 叶节点数n余度为2的节点总数m,有n=m+1;
(4) 有n个节点的完全二叉树的深度k=[log2n]+1;([log2n]---以2为底n的对数再取整)
(5) 有n个节点的完全二叉树各节点如果顺序存储，对任意节点i有：
   如果i!=1,则其父节点的编号为i/2;
   如果2*i<=n,则其左子树根节点的编号为2*i,若2*i>n,则无左子树；
   如果2*i+1<=n，则其右子树根节点编号为2*i+1;若2*i+1>n,则无右子树；

二叉树按存储结构分为顺序存储与链式存储结构
顺序存储结构：
```
typedef DATA SeqBinTree[MAXSIZE];
SeqBinTree SBT;//定义保存二叉树数组的变量
```
对一个完全二叉树，用顺序结构，各节点之间有对应关系，对于节点i,其父节点为i/2(若商不整数，则进行取整)，而其左子节点的编号为2*i,右子节点的编号为2*i+1。
对于不是完全二叉树的的树转化为完全二叉树，将缺少的节点虚设为无数据的节点（这里以"#"表示），如图：
![image](img/suanfa/2.jpg)
之后每个节点的序号与数组有了对应关系

| 1| 2| 3| 4| 5| 6| 7| 8| 9| 10| 11| 12| 13| 14| 15|
| -| -| -| -| -| -| -| -| -| -| -| -| -| -| -|
| A| B| C| #| D| #| E| #| #| F| #| #| #| G| H|

保存A~H共7个节点共占用15个节点的存储空间，空间造成了浪费。
顺序存储浪费空间，所以常用链式存储。

链式存储结构
二叉链表结构：一个节点由节点元素和两个分别指向左、右子树的指针组成的节点结构；
三叉链表结构：在二叉链表结构基础上增加父节点的指针。
二叉链式结构
—————————————————————
| LSon | Data | RSon |
—————————————————————
```
typedef struct ChainTree{
	DATA data;
	struct ChainTree *left;
	struct ChainTree *right;
}ChainTreeType;
ChainTreeType *root=NULL;//定义二叉树根节点指针
```

三叉链式结构
```
typedef struct ChainTree{
	DATA data;
	struct ChainTree *left;
	struct ChainTree *right;
	struct ChainTree *parent;//父节点指针
}ChainTreeType;
ChainTreeType *root=NULL;//定义二叉树根节点指针
```
——————————————————————————————
| LSon | Data | RSon | Parent |
——————————————————————————————

操作二叉树：
```
#include <stdio.h>
#define QUEUE_MAXSIZE 50
typedef char DATA;//元素类型
typedef struct ChainTree{//二叉树节点类型
    DATA data;
    struct ChainTree *left;
    struct ChainTree *right;
}ChainBinTree;

//初始化二叉树
ChainBinTree *BinTreeInit(ChainBinTree *node){
    if(node!=NULL)
        return node;
    else
        return NULL;
}

//添加节点
//bt--父节点 node--子节点 n=1添加左子树 n=2添加右子树
int BinTreeAddNode(ChainBinTree *bt,ChainBinTree *node,int n){
    if(bt==NULL){
        printf("父节点不存在,请先设置父节点！\n");
        return 0;
    }
    switch(n){
    case 1:
        if(bt->left){
            printf("左子树节点不为空!\n");
            return 0;
        }else
            bt->left=node;
        break;
    case 2:
        if(bt->right){
            printf("右树节点不为空!\n");
            return 0;
        }else
            bt->right=node;
        break;
    default:
        printf("参数错误!\n");
        return 0;
    }
    return 1;
}

//返回二叉树的左右子树节点
ChainBinTree *BinTreeLeft(ChainBinTree *bt){
    if(bt)
        return bt->left;
    else
        return NULL;
}
ChainBinTree *BinTreeRight(ChainBinTree *bt){
    if(bt)
        return bt->right;
    else
        return NULL;
}

//获取二叉树状态
int BinTreeIsEmpty(ChainBinTree *bt){
    if(bt)
        return 0;
    else {
        return 1;
    }
}

int BinTreeDepth(ChainBinTree *bt){
    int dep1,dep2;
    if(bt==NULL){
        return 0;
    }else{
        dep1=BinTreeDepth(bt->left);
        dep2=BinTreeDepth(bt->right);
        if(dep1>dep2)
            return dep1+1;
        else {
            return dep2+1;
        }
    }
}

//查找
ChainBinTree *BinTreeFind(ChainBinTree *bt,DATA data){
    ChainBinTree *p;
    if(bt==NULL)
        return NULL;
    else {
        if(bt->data==data)
            return bt;
        else{
            if(p=BinTreeFind(bt->left,data))
                return p;
            else if(p=BinTreeFind(bt->right,data))
                return p;
            else {
                return NULL;
            }
        }
    }
}

//清空二叉树
void BinTreeClear(ChainBinTree *bt){
    if(bt){
        BinTreeClear(bt->left);
        BinTreeClear(bt->right);
        free(bt);
        bt=NULL;
    }
    return;
}

//***********************遍历************
//先序遍历   oper--函数指针
void BinTree_BLR(ChainBinTree *bt,void (*oper)(ChainBinTree *p)){
    if(bt){
        oper(bt);
        BinTree_BLR(bt->left,oper);
        BinTree_BLR(bt->right,oper);
    }
    return;
}
//中序遍历
void BinTree_LDR(ChainBinTree *bt,void(*oper)(ChainBinTree *p)){
    if(bt){
        BinTree_LDR(bt->left,oper);
        oper(bt);
        BinTree_LDR(bt->right,oper);
    }
    return;
}
//后序遍历
void BinTree_LRD(ChainBinTree *bt,void(*oper)(ChainBinTree *p)){
    if(bt){
        BinTree_LRD(bt->left,oper);
        BinTree_LRD(bt->right,oper);
        oper(bt);
    }
    return;
}
//按层遍历
void Bintree_level(ChainBinTree *bt,void(*oper)(ChainBinTree *p)){
    ChainBinTree *p;
    ChainBinTree *q[QUEUE_MAXSIZE];
    int head=0,tail=0;
    if(bt){
        tail=(tail+1)%QUEUE_MAXSIZE;//计算循环队列的队尾序号
        q[tail]=bt;
    }
    while(head!=tail){
        head=(head+1)%QUEUE_MAXSIZE;//计算循环队列队首序号
        p=q[head];
        oper(p);
        if(p->left!=NULL){//节点为左子树，则左子树指针进队
            tail=(tail+1)%QUEUE_MAXSIZE;
            q[tail]=p->left;
        }
        if(p->right!=NULL){
            tail=(tail+1)%QUEUE_MAXSIZE;
            q[tail]=p->right;
        }
    }
    return;
}

void oper(ChainBinTree *p){
    printf("%c ",p->data);
    return;
}

//创建二叉树根节点
ChainBinTree *InitRoot(){
    ChainBinTree *node;
    if(node=(ChainBinTree *)malloc(sizeof(ChainBinTree))){
        printf("\n输入根节点数据：");
        scanf("%s",&node->data);
        node->left=NULL;
        node->right=NULL;
        return node;
    }
    return NULL;
}
//向二叉树添加子节点
void ADDNode(ChainBinTree *bt){
    ChainBinTree *node,*parent;
    DATA data;
    char select;
    if(node=(ChainBinTree *)malloc(sizeof(ChainBinTree))){
        printf("\n输入二叉树节点数据:");
        fflush(stdin);
        scanf("%s",&node->data);
        node->left=NULL;
        node->right=NULL;
        printf("输入父节点数据：");
        fflush(stdin);
        scanf("%s",&data);
        parent=BinTreeFind(bt,data);
        if(!parent){
            printf("没有找到父节点!\n");
            free(node);
            return;
        }
        printf("1.添加到左子树\n2.添加到右子树\n");
        do{
            select=getch();
            select-='0';
            if(select==1||select==2)
                BinTreeAddNode(parent,node,select);
        }while(select!=1&&select!=2);
    }
    return;
}


int main(void)
{
    ChainBinTree *root=NULL;
    char select;
    void (*oper1)();//指向函数的指针
    oper1=oper;
    do{
        printf("\n1.设置二叉树根元素 2.添加二叉树节点 3.先序遍历 4.中序遍历 5.后序遍历 6.按层遍历 7.二叉树深度 0.退出\n");
        select=getch();
        switch (select) {
        case '1':
            root=InitRoot();
            break;
        case '2':
            ADDNode(root);
            break;
        case '3':
            printf("先序遍历结果:\n");
            BinTree_BLR(root,oper1);
            printf("\n");
            break;
        case '4':
            printf("中序遍历结果：\n");
            BinTree_LDR(root,oper1);
            printf("\n");
            break;
        case '5':
            printf("后序遍历结果:\n");
            BinTree_LRD(root,oper1);
            printf("\n");
            break;
        case '6':
            printf("按层遍历结果：\n");
            Bintree_level(root,oper1);
            printf("\n");
            break;
        case '7':
            printf("二叉树深度:%d\n",BinTreeDepth(root));
            break;
        case '0':
            break;
        default:
            break;
        }
    }while(select!=0);
    BinTreeClear(root);
    root=NULL;
    return 0;
}

output:
1.设置二叉树根元素 2.添加二叉树节点 3.先序遍历 4.中序遍历 5.后序遍历 6.按层遍历 7.二叉树深度 0.退出
先序遍历结果:
A B D E C F G

1.设置二叉树根元素 2.添加二叉树节点 3.先序遍历 4.中序遍历 5.后序遍历 6.按层遍历 7.二叉树深度 0.退出
中序遍历结果：
D B E A F C G

1.设置二叉树根元素 2.添加二叉树节点 3.先序遍历 4.中序遍历 5.后序遍历 6.按层遍历 7.二叉树深度 0.退出
后序遍历结果:
D E B F G C A

1.设置二叉树根元素 2.添加二叉树节点 3.先序遍历 4.中序遍历 5.后序遍历 6.按层遍历 7.二叉树深度 0.退出
按层遍历结果：
A B C D E F G

1.设置二叉树根元素 2.添加二叉树节点 3.先序遍历 4.中序遍历 5.后序遍历 6.按层遍历 7.二叉树深度 0.退出
二叉树深度:3
```

线索二叉树：
二叉树遍历结果可以看成一个线性表（节点序列），除了第1个节点外，每个节点有且仅有一个前驱，除最后一个节点，每个节点有且仅有一个后继。
二叉树链表保存二叉树只能找到节点的左右子树，不能直接得到节点的前驱和后继（只有遍历才行）
为了将二叉树在遍历过程中的前驱后继谢谢保存起来，将每个节点为空的左右指针分别用于指向节点的前驱和后继得到线索二叉树
左线索：左指针域中存放的指向前驱节点的指针
右线索：右这边域中存放的指向后继节点的指针
按遍历顺序不同保存的线索二叉树分先序，中序，后序。
![image](img/suanfa/3.jpg)
上图中序遍历为BFDACGEH
为了区别每个节点左右指针域存放的是子树的指针还是线索，必须在节点结构中添加两个标志域：一个左线索域lflag另外一个右线索域rflag,这个标志为1则表示指针域为线索，否则为子树指针。
![image](img/suanfa/4.jpg)
操作线索二叉树
```
#include <stdio.h>
#include <stdlib.h>
#define QUEUE_MAXSIZE 50
typedef char DATA;       //定义元素类型
typedef enum
{
    SubTree,
    Thread
}NodeFlag;  //枚举值SubTree(子树)和Thread(线索)分别为0，1
typedef struct ThreadTree  //定义线索二叉树结点类型
{
    DATA data;	//元素数据
    NodeFlag lflag; //左标志
    NodeFlag rflag; //右标志
    struct ThreadTree *left;	//左子树结点指针
    struct ThreadTree *right;	//右子树结点指针
}ThreadBinTree;

ThreadBinTree *Previous=NULL;     //前驱结点指针

ThreadBinTree *BinTreeInit(ThreadBinTree *node) //初始化二叉树根结点
{
     if(node!=NULL) //若二叉树根结点不为空
         return node;
     else
         return NULL;
}
int BinTreeAddNode(ThreadBinTree *bt,ThreadBinTree *node,int n) //添加数据到二叉树
//bt为父结点，node为子结点,n=1表示添加左子树，n=2表示添加右子树
{
    if(bt==NULL)
    {
        printf("父结点不存在，请先设置父结点!\n");
        return 0;
    }
    switch(n)
    {
        case 1: //添加到左结点
            if(bt->left) //左子树不为空
            {
                printf("左子树结点不为空!\n");
                return 0;
            }else
                bt->left=node;
            break;
        case 2://添加到右结点
            if( bt->right) //右子树不为空
            {
                printf("右子树结点不为空!\n");
                return 0;
            }else
                bt->right=node;
            break;
        default:
            printf("参数错误!\n");
            return 0;
    }
    return 1;
}
ThreadBinTree *BinTreeLeft(ThreadBinTree *bt) //返回左子结点
{
    if(bt)
        return bt->left;
    else
        return NULL;
}
ThreadBinTree *BinTreeRight(ThreadBinTree *bt) //返回右子结点
{
    if(bt)
        return bt->right;
    else
        return NULL;
}
int BinTreeIsEmpty(ThreadBinTree *bt) //检查二叉树是否为空，为空则返回1,否则返回0
{
    if(bt)
        return 0;
    else
        return 1;
}
int BinTreeDepth(ThreadBinTree *bt) //求二叉树深度
{
    int dep1,dep2;
    if(bt==NULL)
        return 0; //对于空树，深度为0
    else
    {
        dep1 = BinTreeDepth(bt->left); //左子树深度 (递归调用)
        dep2 = BinTreeDepth(bt->right); //右子树深度 (递归调用)
        if(dep1>dep2)
           return dep1 + 1;
        else
            return dep2 + 1;
    }
}
ThreadBinTree *BinTreeFind(ThreadBinTree *bt,DATA data) //在二叉树中查找值为data的结点
{
    ThreadBinTree *p;
    if(bt==NULL)
        return NULL;
    else
    {
        if(bt->data==data)
            return bt;
        else{ // 分别向左右子树递归查找
            if(p=BinTreeFind(bt->left,data))
                return p;
            else if(p=BinTreeFind(bt->right, data))
                return p;
            else
                return NULL;
        }
    }
}
void BinTreeClear(ThreadBinTree *bt) // 清空二叉树，使之变为一棵空树
{
     if(bt)
     {
         BinTreeClear(bt->left); //清空左子树
         BinTreeClear(bt->right);//清空右子树
         free(bt);//释放当前结点所占内存
         bt=NULL;
     }
     return;
}
void BinTree_DLR(ThreadBinTree *bt,void (*oper)(ThreadBinTree *p))  //先序遍历
{
     if(bt)//树不为空，则执行如下操作
     {
         oper(bt); //处理结点的数据
         BinTree_DLR(bt->left,oper);
         BinTree_DLR(bt->right,oper);
     }
     return;
}
void BinTree_LDR(ThreadBinTree *bt,void(*oper)(ThreadBinTree *p))  //中序遍历
{
     if(bt)//树不为空，则执行如下操作
     {
         BinTree_LDR(bt->left,oper); //中序遍历左子树
         oper(bt);//处理结点数据
         BinTree_LDR(bt->right,oper); //中序遍历右子树/
     }
     return;
}
void BinTree_LRD(ThreadBinTree *bt,void (*oper)(ThreadBinTree *p)) //后序遍历
{
     if(bt)
     {
         BinTree_LRD(bt->left,oper); //后序遍历左子树
         BinTree_LRD(bt->right,oper); //后序遍历右子树/
         oper(bt); //处理结点数据
     }
     return;
}
void BinTree_Level(ThreadBinTree *bt,void (*oper)(ThreadBinTree *p)) //按层遍历
{
     ThreadBinTree *p;
     ThreadBinTree *q[QUEUE_MAXSIZE]; //定义一个顺序栈
     int head=0,tail=0;//队首、队尾序号
     if(bt)//若队首指针不为空
     {
         tail=(tail+1)%QUEUE_MAXSIZE;//计算循环队列队尾序号
         q[tail] = bt;//将二叉树根指针进队
     }
     while(head!=tail) //队列不为空，进行循环
     {
         head=(head+1)%QUEUE_MAXSIZE; //计算循环队列的队首序号
         p=q[head]; //获取队首元素
         oper(p);//处理队首元素
         if(p->left!=NULL) //若结点存在左子树，则左子树指针进队
         {
             tail=(tail+1)%QUEUE_MAXSIZE;//计算循环队列的队尾序号
             q[tail]=p->left;//将左子树指针进队
         }

         if(p->right!=NULL)//若结点存在右孩子，则右孩子结点指针进队
         {
             tail=(tail+1)%QUEUE_MAXSIZE;//计算循环队列的队尾序号
             q[tail]=p->right;//将右子树指针进队
         }
     }
     return;
}
void BinTreeThreading_LDR(ThreadBinTree *bt)     //二叉树按中序线索化
{
    if(bt) //结点非空时，当前访问结点
    {
        BinTreeThreading_LDR(bt->left); //递归调用，将左子树线索化
        bt->lflag=(bt->left)?SubTree:Thread; //设置左指针域的标志
        bt->rflag=(bt->right)?SubTree:Thread;//设置右指针域的标志
        if(Previous) //若当前结点的前驱Previous存在
        {
            if(Previous->rflag==Thread) //若当前结点的前驱右标志为线索
                Previous->right=bt;//设Previous的右线索指向后继
            if(bt->lflag==Thread) //若当前结点的左标志为线索
                bt->left=Previous;//设当前结点的左线索指向中序前驱
        }
        Previous=bt;//让Previous保存刚访问的结点
        BinTreeThreading_LDR(bt->right);//递归调用，将右子树线索化
    }
}
ThreadBinTree *BinTreeNext_LDR(ThreadBinTree *bt) //求指定结点的后继
{
    ThreadBinTree *nextnode;
    if(!bt) return NULL; //若当前结点为空，则返回空
    if(bt->rflag==Thread) //若当前结点的右子树为空
        return bt->right; //返回右线索所指的中序后继
    else{
        nextnode=bt->right; //从当前结点的右子树开始查找
        while(nextnode->lflag==SubTree) //循环处理所有左子树不为空的结点
            nextnode=nextnode->left;
        return nextnode; //返回左下方的结点
    }
}
ThreadBinTree *BinTreePrevious_LDR(ThreadBinTree *bt) //求指定结点的前驱
{
    ThreadBinTree *prenode;
    if(!bt) return NULL; //若当前结点为空，则返回空
    if(bt->lflag==Thread) //若当前结点的左子树为空
        return bt->left; //返回左线索所指的中序后继
    else{
        prenode=bt->left; //从当前结点的左子树开始查找
        while(prenode->rflag==SubTree) //循环处理所有右子树不为空的结点
            prenode=prenode->right;//书中错误为 prenode=prenode->left;
        return prenode; //返回右下方的结点
    }
}

void ThreadBinTree_LDR(ThreadBinTree *bt,void (*oper)(ThreadBinTree *p)) //遍历中序线索二叉树
{
    if(bt) //二叉树不为空
    {
        while(bt->lflag==SubTree)//有左子树
            bt=bt->left; //从根往下找最左下结点，即中序序列的开始结点
        do{
           oper(bt); //处理结点
           bt=BinTreeNext_LDR(bt);//找中序后继结点
        }while(bt);
    }
}

void oper(ThreadBinTree *p) //操作二叉树结点数据
{
     printf("%c ",p->data); //输出数据
     return;
}
ThreadBinTree *InitRoot()  //初始化二叉树的根
{
    ThreadBinTree *node;
    if(node=(ThreadBinTree *)malloc(sizeof(ThreadBinTree))) //分配内存
    {
        printf("\n输入根结点数据:");
        scanf("%s",&node->data);
        node->left=NULL;
        node->right=NULL;
        return BinTreeInit(node);
    }
    return NULL;
}
void AddNode(ThreadBinTree *bt)
{
     ThreadBinTree *node,*parent;
     DATA data;
     char select;
    if(node=(ThreadBinTree *)malloc(sizeof(ThreadBinTree))) //分配内存
    {
        printf("\n输入二叉树结点数据:");
        fflush(stdin);//清空输入缓冲区
        scanf("%s",&node->data);
        node->left=NULL; //设置左右子树为空
        node->right=NULL;


        printf("输入父结点数据:");
        fflush(stdin);//清空输入缓冲区
        scanf("%s",&data);
        parent=BinTreeFind(bt,data);//查找指定数据的结点
        if(!parent)//若未找到指定数据的结点
        {
            printf("未找到父结点!\n");
            free(node); //释放创建的结点内存
            return;
         }
         printf("1.添加到左子树\n2.添加到右子树\n");
         do{
            select=getch();
            select-='0';
            if(select==1 || select==2)
                BinTreeAddNode(parent,node,select); //添加结点到二叉树
         }while(select!=1 && select!=2);
    }
    return ;
}
int main()
{
    ThreadBinTree *root=NULL; //root为指向二叉树根结点的指针
    char select;
    void (*oper1)(); //指向函数的指针
    oper1=oper; //指向具体操作的函数
    do{
        printf("\n1.设置二叉树根元素    2.添加二叉树结点\n");
        printf("3.生成中序线索二叉树  4.遍历线索二叉树\n");
        printf("0.退出\n");
        select=getch();
        switch(select){
        case '1': //设置根元素
             root=InitRoot();
             break;
        case '2': //添加结点
             AddNode(root);
             break;
        case '3'://生成中序线索二叉树
             BinTreeThreading_LDR(root);
             printf("\n生成中序线索二叉树完毕！\n");
             break;
        case '4'://遍历中序线索二叉树
             printf("\n中序线索二叉树遍历的结果：");
             ThreadBinTree_LDR(root,oper1);
             printf("\n");
             break;
        case '0':
             break;
        }
    }while(select!='0');
    BinTreeClear(root);//清空二叉树
    root=NULL;
    getch();
    return 0;
}

output:
1.设置二叉树根元素    2.添加二叉树结点
3.生成中序线索二叉树  4.遍历线索二叉树
0.退出

输入根结点数据:A

1.设置二叉树根元素    2.添加二叉树结点
3.生成中序线索二叉树  4.遍历线索二叉树
0.退出

输入二叉树结点数据:B
输入父结点数据:A
1.添加到左子树
2.添加到右子树

1.设置二叉树根元素    2.添加二叉树结点
3.生成中序线索二叉树  4.遍历线索二叉树
0.退出

输入二叉树结点数据:C
输入父结点数据:B
1.添加到左子树
2.添加到右子树

1.设置二叉树根元素    2.添加二叉树结点
3.生成中序线索二叉树  4.遍历线索二叉树
0.退出

生成中序线索二叉树完毕！

1.设置二叉树根元素    2.添加二叉树结点
3.生成中序线索二叉树  4.遍历线索二叉树
0.退出

中序线索二叉树遍历的结果：B C A
```

哈夫曼树(最优二叉树)基本概念：
节点的权：根据各节点数据的重要性赋予节点的数；
路径：树中从一个节点到另外一个节点的分支，称为这两个节点之间的路径；
路径长度：一个路径上分支数量；
树的路径长度：从树的根节点到每个节点的路径长度之和，节点数目相同的二叉树，完全二叉树路径最短；
节点的带权路径长度：若节点是带权的，从节点到根节点的路径长度与该节点的权的乘积；
树的带权路径长度：树中所有节点的带权路径长度之和(WPL)
![image](img/suanfa/5.jpg)
上图中带权路径长度分别为节点A B C D的带权路径长度之和：
(a)WPL=5x2+7x2+2x2+13x2=54;
(b)WPL=5x1+7x2+2x3+13x3=64;
(c)WPL=1x13+2x7+3x2+5x3=48;
图c最小，为一棵哈夫曼树。
哈夫曼树创建过程：
(1)首先根据n个有权值的节点构建n棵二叉树，每个节点为一棵二叉树，其权值保存在根节点中，其左右子树均为空；
(2)在这n棵二叉树中找到两棵权值最小的树，用这两棵树作为左右子树构建一棵新的二叉树，将左右子树根节点的权值相加，作为新二叉树根节点的权值；
(3)将上面找到的两棵权值最小二叉树排除在下次寻找范围之外，将新创建的二叉树添加到查找范围之内；
(4)重复2,3直到只剩下一棵树，即为哈夫曼树。
![image](img/suanfa/6.jpg)
![image](img/suanfa/7.png)
用途：
假设A B C D四个出现次数分别5 7 2 13
原始（等长编码）:A-00 B-01 C-10 D-11 编码总长度：5x2+7x2+2x2+13x2=54
不等长码：A-01 B-1 C-10 D-0 则0101编码字符串出现歧义
所以采用哈夫曼编码：A-110 B-10 C-111 D-0
![image](img/suanfa/8.jpg)
实现代码：
```
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
typedef struct
{
    int weight; //权值
    int parent; //父结点序号
    int left; //左子树序号
    int right; //右子树序号
}HuffmanTree;
typedef char *HuffmanCode;  //Huffman编码
void SelectNode(HuffmanTree *ht,int n,int *bt1,int *bt2)
//从1~x个结点选择parent结点为0,权重最小的两个结点
{
     int i;
     HuffmanTree *ht1,*ht2,*t;
     ht1=ht2=NULL; //初始化两个结点为空
     for(i=1;i<=n;++i) //循环处理1~n个结点（包括叶结点和非叶结点）
     {
         if(!ht[i].parent) //父结点为空(结点的parent=0)
         {
             if(ht1==NULL) //结点指针1为空
             {
                 ht1=ht+i; //指向第i个结点
                 continue; //继续循环
             }
             if(ht2==NULL) //结点指针2为空
             {
                 ht2=ht+i; //指向第i个结点
                 if(ht1->weight>ht2->weight) //比较两个结点的权重，使ht1指向的结点权重小
                 {
                     t=ht2;
                     ht2=ht1;
                     ht1=t;
                 }
                 continue; //继续循环
             }
             if(ht1 && ht2) //若ht1、ht2两个指针都有效
             {
                 if(ht[i].weight<=ht1->weight) //第i个结点权重小于ht1指向的结点
                 {
                     ht2=ht1; //ht2保存ht1，因为这时ht1指向的结点成为第2小的
                     ht1=ht+i; //ht1指向第i个结点
                 }else if(ht[i].weight<ht2->weight){ //若第i个结点权重小于ht2指向的结点
                     ht2=ht+i; //ht2指向第i个结点
                 }
             }
         }
     }
     if(ht1>ht2){ //增加比较，使二叉树左侧为叶结点
         *bt2=ht1-ht;
         *bt1=ht2-ht;
     }else{
         *bt1=ht1-ht;
         *bt2=ht2-ht;
     }
}

void CreateTree(HuffmanTree *ht,int n,int *w)
{
    int i,m=2*n-1;//总的节点数
    int bt1,bt2; //二叉树结点序与
    if(n<=1) return ; //只有一个结点，无法创建
    for(i=1;i<=n;++i) //初始化叶结点
    {
        ht[i].weight=w[i-1];
        ht[i].parent=0;
        ht[i].left=0;
        ht[i].right=0;
    }
    for(;i<=m;++i)//初始化后续结点
    {
        ht[i].weight=0;
        ht[i].parent=0;
        ht[i].left=0;
        ht[i].right=0;
    }
    for(i=n+1;i<=m;++i) //逐个计算非叶结点，创建Huffman树
    {
        SelectNode(ht,i-1,&bt1,&bt2); //从1~i-1个结点选择parent结点为0,权重最小的两个结点
        ht[bt1].parent=i;
        ht[bt2].parent=i;
        ht[i].left=bt1;
        ht[i].right=bt2;
        ht[i].weight=ht[bt1].weight+ht[bt2].weight;
    }
}
void HuffmanCoding(HuffmanTree *ht,int n,HuffmanCode *hc)//,char *letters)
{
     char *cd;
     int start,i;
     int current,parent;
     cd=(char*)malloc(sizeof(char)*n);//用来临时存放一个字符的编码结果
     cd[n-1]='\0'; //设置字符串结束标志
     for(i=1;i<=n;i++)
     {
         start=n-1;
         current=i;
         parent=ht[current].parent;//获取当前结点的父结点
         while(parent) //父结点不为空
         {
             if(current==ht[parent].left)//若该结点是父结点的左子树
               cd[--start]='0'; //编码为0
             else //若结点是父结点的右子树
               cd[--start]='1'; //编码为1
             current=parent; //设置当前结点指向父结点
             parent=ht[parent].parent; //获取当前结点的父结点序号
         }
         hc[i-1]=(char*)malloc(sizeof(char)*(n-start));//分配保存编码的内存
         strcpy(hc[i-1],&cd[start]); //复制生成的编码
     }
     free(cd); //释放编码占用的内存
}

void Encode(HuffmanCode *hc,char *alphabet,char *str,char *code)
//将一个字符串转换为Huffman编码
//hc为Huffman编码表 ,alphabet为对应的字母表,str为需要转换的字符串,code返回转换的结果
{

     int len=0,i=0,j;
     code[0]='\0';
     while(str[i])
     {
         j=0;
         while(alphabet[j]!=str[i])
             j++;
         strcpy(code+len,hc[j]); //将对应字母的Huffman编码复制到code指定位置
         len=len+strlen(hc[j]); //累加字符串长度
         i++;
     }
     code[len]='\0';
}

void Decode(HuffmanTree *ht,int m,char *code,char *alphabet,char *decode)
//将一个Huffman编码组成的字符串转换为明文字符串
//ht为Huffman二叉树,m为字符数量,alphabet为对应的字母表,str为需要转换的字符串,decode返回转换的结果
{
     int position=0,i,j=0;
     m=2*m-1;
     while(code[position]) //字符串未结束
     {
          for(i=m;ht[i].left && ht[i].right; position++) //在Huffman树中查找左右子树为空 ，以构造一个Huffman编码
          {
              if(code[position]=='0') //编码位为0
                  i=ht[i].left; //处理左子树
              else //编译位为 1
                  i=ht[i].right; //处理右子树
          }
          decode[j]=alphabet[i-1]; //得到一个字母
          j++;//处理下一字符
     }
     decode[j]='\0'; //字符串结尾
}
int main()
{
    int i,n=4,m;
    char test[]="DBDBDABDCDADBDADBDADACDBDBD";
    char code[100],code1[100];
    char alphabet[]={'A','B','C','D'}; //4个字符
    int w[]={5,7,2,13} ;//4个字符的权重
    HuffmanTree *ht;
    HuffmanCode *hc;
    m=2*n-1;
    ht=(HuffmanTree *)malloc((m+1)*sizeof(HuffmanTree)); //申请内存，保存赫夫曼树
    if(!ht)
    {
        printf("内存分配失败！\n");
        exit(0);
    }
    hc=(HuffmanCode *)malloc(n*sizeof(char*));
    if(!hc)
    {
        printf("内存分配失败！\n");
        exit(0);
    }

    CreateTree(ht,n,w); //创建赫夫曼树
    HuffmanCoding(ht,n,hc); //根据赫夫曼树生成赫夫曼编码
    for(i=1;i<=n;i++) //循环输出赫夫曼编码
        printf("字母:%c,权重:%d,编码为 %s\n",alphabet[i-1],ht[i].weight,hc[i-1]);

    Encode(hc,alphabet,test,code); //根据赫夫曼编码生成编码字符串
    printf("\n字符串:\n%s\n转换后为:\n%s\n",test,code);

    Decode(ht,n,code,alphabet,code1); //根据编码字符串生成解码后的字符串
    printf("\n编码:\n%s\n转换后为:\n%s\n",code,code1);
    getch();
    return 0;
}

output：
字母:A,权重:5,编码为 110
字母:B,权重:7,编码为 10
字母:C,权重:2,编码为 111
字母:D,权重:13,编码为 0

字符串:
DBDBDABDCDADBDADBDADACDBDBD
转换后为:
010010011010011101100100110010011001101110100100

编码:
010010011010011101100100110010011001101110100100
转换后为:
DBDBDABDCDADBDADBDADACDBDBD

```


6.图
--------
图是多对多关系，每一个数据元素都可以与其他任意元素相关；
图由数据元素和连接数据元素的线构成；
数据元素称为顶点，线称为边。
一个图由顶点集合与边集合组成，如下：
G=(V,E)或者G=(V(G),E(G))
V(G)表示顶点的非空集合（至少一个顶点），每个顶点可以用不同的字母或者数字表示；
E(G)是图里面所有边的集合，可以为空，图的每一条边由连接的两个顶点表示。
边没有方向的为无向图，有方向的为有向图。
![image](img/suanfa/9.jpg)
无向图：V(G)={V1，V2，V3，V4，V5} E(G)={(V1,V2),(V1,V3),(V1,V5),(V2,V4),(V3,V5),(V4,V5)}
有向图：V(G)={V1，V2，V3，V4，V5，V6} E(G)=&lt;V1,V2&gt;,&lt;V2,V1&gt;,&lt;V2,V3&gt;,&lt;V3,V4&gt;,&lt;V4,V5&gt;,&lt;V5,V6&gt;,&lt;V6,V4&gt;,&lt;V6,V2&gt;}

常用概念：
邻接点：一条边的两个顶点互称邻接点；有向图中有起点和终点之分，<V1,V2>中，V1是V2的入边邻接点，V2是V1的出边邻接点。
顶点的度D(V)：在图中连接某顶点的边的数量。对于有向图有入度ID(V)和出度OD(V)之分,D(V)=ID(V)+OD(V).
完全图：图中每两个顶点之间都存在一条边。
![image](img/suanfa/10.jpg)
n个顶点的无向完全图总边数为 n(n-1)/2,有向完全图总边数为 n(n-1).
子图：一个图的所有顶点和边都是另外一个图的子集，则称这个图是另外一个图的子图。必须顶点和边都是子集。
路径：从顶点Vm到Vn之间存在的一个顶点序列Vm、V1 ... Vi、Vn,有(Vm,V1)、(V1,V2)...（Vi,Vn）,则表示Vm到Vn的一条路径；
路径长度：路径上边的数量
回路：第一个顶点与最后一个顶点相同的路径如(V2,V1),(V1,V3),(V3,V4),(V4,V1)
无向图中任意两个顶点可以连通称为连通图，否则为非连通图，有些分连通图可以分为多个连通分量；
有向图中任意两个顶点连通(Vi到Vj连通，反之不一定)称为强连通图；
带权值的图为带权图或者网：
![image](img/suanfa/11.jpg)

图的存储有邻接矩阵和邻接表两种。
邻接矩阵：
![image](img/suanfa/12.jpg)
Aij为1表示(Vi,Vj)或者<Vi,Vj>构成一条边，为0表示不构成一条边；
无向图邻接矩阵左下角和右上角对称，有向图则不一定。
带权图只要把1改为权值，将0改为最大MAX(大于所有边的权值之和)即可。
邻接矩阵：
```
#define VERTEX_MAX 26   //图的最大顶点数
#define MAXVALUE 32767 //最大值(可设为一个最大整数)
typedef struct
{
    char Vertex[VERTEX_MAX]; //保存顶点信息(序号或字母)
    int Edges[VERTEX_MAX][VERTEX_MAX]; //保存边的权
    int isTrav[VERTEX_MAX]; //遍历标志
    int VertexNum; //顶点数量
    int EdgeNum;//边数量
    int GraphType; //图的类型(0:无向图，1:有向图)
}MatrixGraph; //定义邻接矩阵图结构

void CreateMatrixGraph(MatrixGraph *G);//创建邻接矩阵图
void OutMatrix(MatrixGraph *G); //输出邻接矩阵

void CreateMatrixGraph(MatrixGraph *G)//创建邻接矩阵图
{
    int i,j,k,weight;
    char start,end; //边的起始顶点
    printf("输入各顶点信息\n");
    for(i=0;i<G->VertexNum;i++) //输入顶点
    {
        getchar();
        printf("第%d个顶点:",i+1);
        scanf("%c",&(G->Vertex[i])); //保存到各顶点数组元素中
    }
    printf("输入构成各边的两个顶点及权值(用逗号分隔):\n");
    for(k=0;k<G->EdgeNum;k++)  //输入边的信息
    {
        getchar(); //暂停输入
        printf("第%d条边：",k+1);
        scanf("%c,%c,%d",&start,&end,&weight);
        for(i=0;start!=G->Vertex[i];i++); //在已有顶点中查找始点
        for(j=0;end!=G->Vertex[j];j++); //在已有顶点中查找结终点
        G->Edges[i][j]=weight; //对应位置保存权值，表示有一条边
        if(G->GraphType==0)  //若是无向图
            G->Edges[j][i]=weight;//在对角位置保存权值
    }
}

void OutMatrix(MatrixGraph *G)//输出邻接矩阵
{
    int i,j;
    for(j=0;j<G->VertexNum;j++)
        printf("\t%c",G->Vertex[j]);          //在第1行输出顶点信息
    printf("\n");
    for(i=0;i<G->VertexNum;i++)
    {
        printf("%c",G->Vertex[i]);
        for(j=0;j<G->VertexNum;j++)
        {
            if(G->Edges[i][j]==MAXVALUE) //若权值为最大值
                printf("\t∞");          //输出无穷大符号
            else
                printf("\t%d",G->Edges[i][j]); //输出边的权值
        }
        printf("\n");
    }
}

int main()
{
    MatrixGraph G; //定义保存邻接矩阵结构的图
    int i,j;
    printf("输入生成图的类型(0:无向图,1:有向图):");
    scanf("%d",&G.GraphType); //图的种类
    printf("输入图的顶点数量和边数量:");
    scanf("%d,%d",&G.VertexNum,&G.EdgeNum); //输入图顶点数和边数
    for(i=0;i<G.VertexNum;i++)  //清空矩阵
        for(j=0;j<G.VertexNum;j++)
            G.Edges[i][j]=MAXVALUE; //设置矩阵中各元素的值为最大值
    CreateMatrixGraph(&G); //创建用邻接表保存的图
    printf("邻接矩阵数据如下:\n");
    OutMatrix(&G);
    getch();
    return 0;
}

输入生成图的类型(0:无向图,1:有向图):0
输入图的顶点数量和边数量:5,6
输入各顶点信息
第1个顶点:1
第2个顶点:2
第3个顶点:3
第4个顶点:4
第5个顶点:5
输入构成各边的两个顶点及权值(用逗号分隔):
第1条边：1,2,2
第2条边：1,3,5
第3条边：1,5,3
第4条边：2,4,4
第5条边：3,5,5
第6条边：4,5,2
邻接矩阵数据如下:
        1       2       3       4       5
1       ∞      2       5       ∞      3
2       2       ∞      ∞      4       ∞
3       5       ∞      ∞      ∞      5
4       ∞      4       ∞      ∞      2
5       3       ∞      5       2       ∞
```

邻接表：
从邻接矩阵表示图可以看出很多元素值为0，造成存储空间浪费。
![image](img/suanfa/13.jpg)
邻接表对每个顶点建立一个邻接关系的单链表，如图中V1连接三个顶点次序是任意的，只要是邻接点就行。 
邻接表保存图：
```
#include <stdio.h>
#define VERTEX_MAX 20   //图的最大顶点数
typedef struct edgeNode
{
    int Vertex; //顶点信息(序号或字母)
    int weight; //权值
    struct edgeNode *next; //指向下一个顶点指针 (当前顶点和指向的下一顶点构成一条边)
}EdgeNode; //邻接表边结构

typedef struct
{
    EdgeNode* AdjList[VERTEX_MAX]; //指向每个顶点的指针
    int VextexNum,EdgeNum; //图的顶点的数量和边的数量
    int GraphType; //图的类型(0:无向图，1:有向图)
}ListGraph;  //图的结构

void CreateGraph(ListGraph *G); //生成图的邻接表
void OutList(ListGraph *G); //输出邻接表

void CreateGraph(ListGraph *G)  //构造邻接表结构图
{
    int i,weight;
    int start,end;
    EdgeNode *s;
    for(i=1;i<=G->VextexNum;i++)//将图中各顶点指针清空
        G->AdjList[i]= NULL;
    for(i=1;i<=G->EdgeNum;i++) //输入各边的两个顶点
    {
        getchar();
        printf("第%d条边:",i);
        scanf("%d,%d,%d",&start,&end,&weight); //输入边的起点和终点
        s=(EdgeNode *)malloc(sizeof(EdgeNode)); //申请保存一个顶点的内存
        s->next=G->AdjList[start]; //插入到邻接表中
        s->Vertex=end; //保存终点编号
        s->weight=weight; //保存权值
        G->AdjList[start]=s; //邻接表对应顶点指向该点
        if(G->GraphType==0) //若是无向图，再插入到终点的边链中
        {
            s=(EdgeNode *)malloc(sizeof(EdgeNode)); //申请保存一个顶点的内存
            s->next=G->AdjList[end];
            s->Vertex=start;
            s->weight=weight;
            G->AdjList[end]=s;
        }
    }
}
void OutList(ListGraph *G)
{
    int i;
    EdgeNode *s;
    for(i=1;i<=G->VextexNum;i++)
    {
        printf("顶点%d",i);
        s=G->AdjList[i];
        while(s)
        {
            printf("->%d(%d)",s->Vertex,s->weight);
            s=s->next;
        }
        printf("\n");
    }
}

int main()
{
    ListGraph G; //定义保存邻接表结构的图
    printf("输入生成图的类型(0:无向图,1:有向图):");
    scanf("%d",&G.GraphType); //图的种类
    printf("输入图的顶点数量和边数量:");
    scanf("%d,%d",&G.VextexNum,&G.EdgeNum); //输入图顶点数和边数
    printf("输入构成各边的两个顶点及权值(用逗号分隔):\n");
    CreateGraph(&G); //生成邻接表结构的图
    printf("输出图的邻接表:\n");
    OutList(&G);
    getch();
    return 0;
}

output:
输入生成图的类型(0:无向图,1:有向图):1
输入图的顶点数量和边数量:5,6
输入构成各边的两个顶点及权值(用逗号分隔):
第1条边:1,2,2
第2条边:1,3,5
第3条边:1,5,3
第4条边:2,4,4
第5条边:3,5,5
第6条边:4,5,2
输出图的邻接表:
顶点1->5(3)->3(5)->2(2)
顶点2->4(4)
顶点3->5(5)
顶点4->5(2)
顶点5

```


 











二.算法
==========




三.常用程序
===========
1 进制转化
----------
```
#include <stdio.h>
#include <string.h>
/** **********进制转换
 *输入10进制数和需要转换的进制
 *输出对应进制数
 */


void convto(char *s,int n,int b){
    char bit[]={"0123456789ABCDEF"};
    int len;
    if(n==0){
        strcpy(s,"");
        return;
    }
    convto(s,n/b,b);
    len=strlen(s);
    s[len]=bit[n%b];
    s[len+1]='\0';
}

int main(void)
{
    char s[80];
    int base,old;
    printf("输入十进制数:");
    scanf("%d",&old);
    printf("输入转换的进制:");
    scanf("%d",&base);
    convto(s,old,base);
    printf("%s\n",s);
    //char i=getch(); //从控制台读取一个字符，但不显示在屏幕上 会等待你按下任意键，再继续执行下面的语句
    //printf("%c\n",i);
    return 0;
}
```


四.题库
=============
1.试探法生成彩票组合
-----------------
描述：通过每一注彩票的位数和组成彩票的数字输出彩票号码。不可重复。
如:位数3 数字4
则组合：
4 3 2
4 3 1
4 2 1
3 2 1

程序如下：
```
#include <stdio.h>
#define MAXN 3
#define NUM 4

int num[NUM];
int lottery[MAXN];
void combine(int n,int m){
    int i,j;
    for(i=n;i>=m;i--){
        lottery[m-1]=num[i-1];//保存一位数字
        if(m>1)
            combine(i-1,m-1);
        else{
            for(j=MAXN-1;j>=0;j--)
                printf("%3d",lottery[j]);
            printf("\n");
        }
    }
}


int main(void)
{
    int i,j;
    for(i=0;i<NUM;i++)
        num[i]=i+1;
    for(j=0;j<MAXN;j++)
        lottery[j]=0;
    combine(NUM,MAXN);
    return 0;
}

output：
  4  3  2
  4  3  1
  4  2  1
  3  2  1
```

2.汉诺塔问题
-----------
汉诺塔问题是使用递归解决问题的经典范例。
汉诺（Hanoi）塔问题：古代有一个梵塔，塔内有三个座A、B、C，A座上有64个盘子，盘子大小不等，大的在下，小的在上。有一个和尚想把这64个盘子从A座移到C座，但每次只能允许移动一个盘子，并且在移动过程中，3个座上的盘子始终保持大盘在下，小盘在上。在移动过程中可以利用B座，要求打印移动的步骤。如果只有一个盘子，则不需要利用B座，直接将盘子从A移动到C。
分析：
(1)如果只有一个圆盘，则把该圆盘从A棒移动到C棒，完成任务；
(2)如果圆盘数量n>1,移动过程分三步：
第一步：将A棒的n-1个圆盘移动到B棒上，
第二步：将A棒的1个盘移动到C棒上，
第三步：将B棒的n-1个圆盘移动到C棒上。
```
#include<stdio.h>

int count=0;
int main()
{
  void hanio(int n,char one ,char two,char three);
  int m;
  printf("输入盘子的数量");
  scanf("%d",&m);
  printf("移动个%d盘子步骤\n",m);
  hanio(m,'A','B','C');
  printf("总共移动了%d次",count);
  return 0;
}

void hanio(int n,char one,char two,char three)
{
  void move(char x,char y);
  if(1==n) move(one,three);
  else{
        hanio(n-1,one ,three,two);
        move(one,three);
        hanio(n-1,two,one,three);
    }
}

void move(char x,char y)
{
    printf("%c--->%c\n",x,y);
    count++;
}

output:
输入盘子的数量3
移动个3盘子步骤
A--->C
A--->B
C--->B
A--->C
B--->A
B--->C
A--->C
总共移动了7次
```

3.算术表达式求值
---------------
输入表达式，输出计算值,这里只有数字和加减乘除小括号。
如:
输入:(1+1)*2=
输出:4
分析如下:
![image](img/suanfa/1.png)
运算符优先级：

| O1\O2| +、-| *、/ | （| ）|
| ---| ---| ---| ---| ---|
| +、-| 1| -1| -1| 1|
| *、/| 1| 1| -1| 1|
| （ | -1| -1| -1| 0|
| ） | 1 | 1| | 1|


程序：
```

```