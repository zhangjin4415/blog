title: CentOS与大数据处理
date: 2016-04-25 09:57:00
categories: ["CentOS","大数据"]
tags: ["CentOS","linux","大数据"]
---
主要内容：
<!--more-->

第一章 centos常见问题
====================
1.更新
---------
```
# yum check-update
# yum update -y
```
2.网页视频播放问题
---------------
将下载的flash安装包.tar.gz解压到/home/用户名/.mozilla/plugins下即可
```
tar zxvf .tar.gz文件 -C 解压到的目录
```


第二章 hadoop安装前期知识
=================
1.通过主机名代替ip访问主机
-----------
主机名修改：
su下命令:
```
vi /etc/sysconfig/network
```
修改里面的HOSTNAME就可以，之后重启机器或者命令sudo hostname 你的新主机名，即可生效！需要exit后重新登录一下发现改变。
可以通过配置实现主机名与ip一一对应。需要在su下操作。
```
vi /etc/hosts
```
备注：windows在C:\Windows\System32\drivers\etc\hosts中可以改。
在文件后面加上需要的ip与对应主机名即可：
```
ip地址 主机名
```
集群搭建需要全部都配置这个文件！
然后
```
ping 主机名
```
可以连通。

2.查看hodoop版本64位还是32位
--------------------
解压后进入$hadoop_home/lib/native,使用file命令。
```
file libhadoop.so.1.0.0
```

第三章 centos搭建hadoop环境
============================
1.jdk安装
-----------
下载jdk压缩包解压到目录/home/用户名/software/java/下，然后配置环境变量，vi ~/.bashrc在后面添加如下代码：
```
export JAVA_HOME=/home/用户名/software/java/jdk1.8.0_74
export JAVA_BIN=$JAVA_HOME/bin
export JAVA_LIB=$JAVA_HOME/lib
export CLASSPATH=.:$JAVA_LIB/tools.jar:$JAVA_LIB/dt.jar
export PATH=$JAVA_BIN:$PATH
```
输入生效命令
```
source ~/.bashrc
```
有人说上面针对当前用户有效，针对所有用户有效需要在/etc/profile下配置，然后再source /etc/profile生效。
现在在任意目录下运行java,javac有反应，不会提示命令不存在，说明jdk安装成功！

2.hadoop配置
--------------
下载hadoop并解压到目录hadoop下，进入其etc目录改配置。
备注：cmd文档代表在windows下的，而sh文档代表在linux下的。
(1) hadoop-env.sh
env==environment环境变量，修改内容：JAVA_HOME。
输入命令：
```
vi hadoop-env.sh
```
打开文档找到
```
#The java implementation to use.
export JAVA_HOME=${JAVA_HOME}
```
将其改为绝对路径，因为不改的话经常找不到java目录。修改后如下：
```
# The java implementation to use.
export JAVA_HOME=/home/zhang/software/java/jdk1.8.0_74
```

(2) core-site.xml
找到
```
<configuration>
</configuration>
```
添加如下：
```
<configuration>
<property>
<name>fs.defaultFS</name>
<value>hdfs://zhang:9000/</value>
</property>

<property>
<name>hadoop.tmp.dir</name>
<value>/home/zhang/software/hadoop/data/</value>
</property>
</configuration>
```

fs.defaultFS 默认文件系统
<value>hdfs://zhang:9000/</value> 采用uri格式，hdfs-协议为hdfs,zhang-主节点地址为zhang(因为前面已经配置主机地址与主机名对应)，9000-默认端口号。
hadoop.tmp.dir 共同工作目录

(3) hdfs-site.xml
配置运行的细节
```
<configuration>
<property>
<name>dfs.replication</name> 
<value>2</value>
</property> 
</configuration>
```
其中dfs.replication-配置副本数量， 3个为最佳，会放在不同的主机上，放在同一主机没有任何意义，会报错，这里我用两个data节点（data主机），存2个副本。
切块大小也可用在这里配置，默认128M。
上面配置好后hdfs可以运行啦，但是yarn不能运行，还需要配置.

(4) mapred-site.xml
mv mapred-site.xml.template mapred-site.xml
对于.xml才能找到执行，所以需要改后缀名。
配置如下
```
<configuration>
<property>
<name>mapreduce.framework.name</name>
<value>yarn</value>
</property>
</configuration>
```
map-reduce应该放到哪个资源调度集群上跑，指定用yarn这个集群跑，hdfs与yarn都是集群，其在物理主机上没有分开，但是是不同的。

(5) yarn-site.xml 
配置yarn中的老大以及node节点采用mapreduce_shuffle机制（map产生的中间结果传递给reduce采用哪种机制）。
配置如下：
```
<configuration>
<!-- Site specific YARN configuration properties -->
<property>
<name>yarn.resourcemanager.hostname</name>
<value>zhang</value>
</property>

<property>
<name>yarn.nodemanager.aux-services</name>
<value>mapreduce_shuffle</value>
</property>
</configuration>
```

3.启动前准备工作
---------------
(1) 防火墙设置
hadoop都是一些网络服务，伪分布式情况端口号被防火墙屏蔽，需要打开端口号或者关闭防火墙。
hodoop一般就是公司内部一个网络，不会与外界联系，所有可以使用关闭防火墙情况更加简单。
root用户下命令如下：
```
service iptables stop   //关闭防火墙
service iptables status //查看状态
```
下次打开又会开启，因为这是一个自启动服务，可以使用下面命令让其不自启动
```
sudo chkconfig iptables off //如果是on则打开
sudo chkconfig iptables --list//查看状态 此时所有级别全部off
```

(2) 格式化
未来方面起见，首先将hadoop命令添加环境变量，以便在任何地方可以调用hadoop命令.
root权限下
```
vi /etc/profile
```
添加如下代码：
```
export HADOOP_HOME=/home/zhang/software/hadoop/hadoop-2.6.4
export HADOOP_BIN=$HADOOP_HOME/bin
export PATH=$HADOOP_BIN:$PATH
```
利用source /etc/profile 生效,我重启才生效！

格式化命令：
```
hadoop namenode -format
```
看到如下语句说明格式化成功：
```
16/04/26 11:53:24 INFO common.Storage: Storage directory /home/zhang/software/hadoop/data/dfs/name has been successfully formatted.
```
格式化时在data目录下新建目录/dfs/name 里面初始化一些文件.
查看目录：
```
[zhang@zhang hadoop-2.6.4]$ cd /home/zhang/software/hadoop/data/dfs/name
[zhang@zhang name]$ ls
current
[zhang@zhang name]$ cd current
[zhang@zhang current]$ ls
fsimage_0000000000000000000  fsimage_0000000000000000000.md5  seen_txid  VERSION
```
因为namenode指定的是这台机器192.168.0.107,所以文件会建到这个主机上。
fsimage储存原数据(管理datanode节点的数据)。
现在可以进行启动！

(3) datanode节点与sbin环境变量
启动命令在hadoop安装目录下的sbin目录下。一般不用start-all，用start-dfs,start-yarn更能够理解操作。
用时首先将sbin加入环境变量。

/etc/hadoop下有slaves文件，可以配置datanode主机.
```
vi /etc/hadoop/slaves
```
内容如下(3台datanode主机)：
```
zhang
mem1
mem2
```

4 启动
-------------



















备注：
==============
1.为保证内存充分利用，尽量采用64位系统。


