title: Hadoop
date: 2016-11-09 21:10:12
categories: "大数据"
tags: "Hadoop"
---
主要内容：Hadoop大数据分布式处理实践
<!--more-->

第一章 Hadoop集群搭建
================
1.环境准备
---------------
准备4台电脑，安装上centos系统,准备一台路由器，将4台电脑连上此路由器，即4台电脑在同一个局域网。

(1)设置静态IP
设置4台电脑的静态IP地址：
192.168.1.100
192.168.1.101
192.168.1.102
192.168.1.103

备注：192.168.1.100作为namenode  192.168.1.101-103作为datanode
说明：静态IP设置：
进入目录:
```
cd /etc/sysconfig/network-scripts/
```
查看是否有ifcfg-eth0文件
没有则复制ifcfg-lo:
```
cp ifcfg-lo ifcfg-eth0
```
然后对ifcfg-eth0进行修改(root模式下)：
```
vi ifcfg-eth0
```
修改如下：
```
DEVICE=eth0
IPADDR=192.168.1.100
NETMASK=255.255.255.0
NETWORK=192.168.1.0
# If you're having problems with gated making 127.0.0.0/8 a martian,
# you can change this to something else (255.255.255.255, for example)
BROADCAST=127.255.255.255
ONBOOT=yes
BOOTPROTO="static"
GATEWAY=192.168.1.1
NM_CONTROLLED="no"
```
NM_CONTROLLED="no" 可以使得重启电脑后ip不变
静态IP设置后通过命令service network start生效
设置好静态IP后ping一下，保证四台电脑之间相互能够连通

如果电脑太多，不方便一个一个改的话可以用scp复制(scp用于不同电脑/系统的文件/文件夹(-r)复制)
如下命令可以将本机的ifcfg-eth0文件复制到192.168.1.101电脑下的tmp目录下
用这个要先安装有SSH（看下面(2)）
```
scp ifcfg-eth0 zhang@192.168.1.101：/tmp/
```
如果提示Pemission denied（证明没有权限） 只需要将其复制到有权限的目录然后再用ssh进入对方电脑进行cp就可以；也可以通过修改对方文件夹权限实现。

(2)ssh配置与防火墙设置
安装SSH
```
yum install openssh-server
```
开启SSH服务
```
service sshd start
```
之后可以连接和退出其他电脑:
```
ssh 192.168.1.101 //连接ip为192.168.1.101的电脑
logout            //退出连接的电脑
```

重点：
以上设置后重启电脑(reboot)后又需要重新弄，所以必须改成永久性的
```
chkconfig sshd on //ssh开机即启动
chkconfig iptables off //防火墙永久关闭
```

但是上面的连接需要输入对方的密码才能访问，下面搭建免密码SSH
配置SSH免密码访问
运行ssh-keygen -t rsa 这里遇到输入时直接回车
```
[root@localhost zhang]# ssh-keygen -t rsa
Generating public/private rsa key pair.
Enter file in which to save the key (/root/.ssh/id_rsa): 
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /root/.ssh/id_rsa.
Your public key has been saved in /root/.ssh/id_rsa.pub.
The key fingerprint is:
63:fc:01:3e:8d:21:cf:5f:ce:c3:49:c5:e0:1d:84:6f root@localhost.localdomain
The key's randomart image is:
+--[ RSA 2048]----+
|            .oo  |
|           ..+ . |
|      . o   ..+  |
|       * =   .E  |
|        S o o.   |
|       . = B .   |
|          o *    |
|             .   |
|                 |
+-----------------+
```
之后进入目录/root/.ssh 通过ls -a可以看到.ssh文件夹目录
```
[root@localhost .ssh]# ls -a
.  ..  id_rsa  id_rsa.pub  known_hosts
```
其他三台电脑同理，运行如上。




(3)常见错误分析：
SSH登陆错误 WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!
```
Connection to 192.168.10.20 closed.
[root@localhost ~]# ssh 192.168.10.88
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
b6:0c:41:43:60:79:eb:05:9e:c9:72:1d:a0:41:9a:50.
Please contact your system administrator.
Add correct host key in /root/.ssh/known_hosts to get rid of this message.
Offending key in /root/.ssh/known_hosts:5
RSA host key for 192.168.10.88 has changed and you have requested strict checking.
Host key verification failed.
```
方法1.在客户端执行下述指令即可 #mv /root/.ssh/known_hosts /tmp
方法2.当然也可以直接编辑known_hosts文件,把里面与所要连接IP(192.168.10.20)相关的内容删掉即可.

(4)参考文献：
http://www.cnblogs.com/ylh1223/archive/2012/05/31/2528517.html
http://jingyan.baidu.com/article/3ea51489f9efbf52e61bba05.html
http://www.jb51.net/LINUXjishu/70474.html








