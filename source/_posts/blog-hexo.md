title: Github和Hexo搭建属于自己的博客
date: 2016-01-03 10:19:50
categories: "博客"
tags: ["Hexo","Github"]
---
主要内容：hexo环境搭建，相关软件安装，Github配置，域名绑定
<!--more-->
一.简介
==============
前几天利用Github和Hexo搭建了一个属于自己的博客，为了方便更多的人学习！将具体流程写下来！主要分4步：软件安装，Github配置，Hexo配置，域名绑定。

二.软件安装
===================
1.安装node.js
------------------------------
百度一下nodejs官网，找到DOWNLOADS点击，找到符合自己电脑系统的版本。点击下载，安装！

2.安装Git
-------------------------------
下载安装Git，用法：在Windows下，打开Git Bash，其他系统下面则打开终端（Terminal）。

三.Github配置
=========================
1.注册Github帐号
-----------------------------------------
已经有Github帐号跳过此步，首先进入Github进行注册，用户名、邮箱和密码之后都需要用到，自己记好。

2.创建repository
--------------------------------------------
在自己的Github下创建repository
![blog-hexo1](img/blog-hexo/1.png)
命名方式：你的Github账号.github.io

3.配置 SSH keys
--------------------------------------------
下面内容参考：[http://cnfeat.com/blog/2014/05/10/how-to-build-a-blog/](http://cnfeat.com/blog/2014/05/10/how-to-build-a-blog/)

我们如何让本地git项目与远程的github建立联系呢？用SSH keys。
打开git bash
首先我们检查你电脑上现有的ssh key：
```Bash
$ cd ~/.ssh
```
如果提示：No such file or directory 说明你是第一次使用git.
生成新的SSH Key:
```Bash
$ ssh-keygen -t rsa -C "邮件地址@youremail.com"
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/your_user_directory/.ssh/id_rsa):<回车就好>
```
然后系统会要你输入密码：
```Bash
Enter passphrase (empty for no passphrase):<输入加密串>
Enter same passphrase again:<再次输入加密串>
```
在回车中会提示你输入一个密码，这个密码会在你提交项目时使用，如果为空的话提交项目时则不用输入。这个设置是防止别人往你的项目里提交内容。
注意：输入密码的时候没有字样的，你直接输入就可以了。
最后看到这样的界面，就成功设置ssh key了：
![blog-hexo](img/blog-hexo/2.png)

添加 SSH Key 到 GitHub
在本机设置SSH Key之后，需要添加到GitHub上，以完成SSH链接的设置。
(1)、打开本地C:\Users\主机名\.ssh\id_rsa.pub文件。此文件里面内容为刚才生成人密钥。如果看不到这个文件，你需要设置显示隐藏文件。准确的复制这个文件的内容，才能保证设置的成功。
(2)、登陆github系统。点击右上角的 Account Settings—>SSH Public keys —> add another public keys
(3)、把你本地生成的密钥复制到里面（key文本框中）， 点击 add key 就ok了

测试:
可以输入下面的命令，看看设置是否成功:
```Bash
$ ssh -T git@github.com
```
如果是下面的反馈：
```Bash
The authenticity of host 'github.com (207.97.227.239)' can't be established.
RSA key fingerprint is 16:27:ac:a5:76:28:2d:36:63:1b:56:4d:eb:df:a6:48.
Are you sure you want to continue connecting (yes/no)?
```
不要紧张，输入yes就好，然后会看到：
```Bash
Hi 某某某! You've successfully authenticated, but GitHub does not provide shell access.
```
现在你已经可以通过 SSH 链接到 GitHub 了，还有一些个人信息需要完善的。

设置用户信息:
Git 会根据用户的名字和邮箱来记录提交。GitHub 也是用这些信息来做权限的处理，输入下面的代码进行个人信息的设置，把名称和邮箱替换成你自己的，名字必须是你的真名，而不是GitHub的昵称。
```Bash
$ git config --global user.name "yourname"//用户名
$ git config --global user.email  "yourmail@mail.com"//填写自己的邮箱
```
SSH Key 配置成功
本机已成功连接到 github。

四.Hexo配置
==================
1.hexo常用命令介绍
--------------------------------------
hexo常用的命令,#后面为注释:
```Bash
$ hexo g #完整命令为hexo generate,用于生成静态文件
$ hexo s #完整命令为hexo server,用于启动服务器，主要用来本地预览
$ hexo d #完整命令为hexo deploy,用于将本地文件发布到github上
$ hexo n #完整命令为hexo new,用于新建一篇文章
$ hexo s#完整命令为hexo server启动本地服务，进行文章预览调试
```
2.安装hexo
------------------------------
打开Git Bash,输入下面命令：
```Bash
$ npm install -g hexo-cli
```
我用的windows10,64位,没有配置环境变量就可以用,其他系统不可以的话自己配置环境变量Path(hexo的安装路径下的lib),一般在C:\Users\Administrator\AppData\Roaming\npm\node_modules\hexo\lib。
接下来创建放置博客文件的文件夹：hexo文件夹。在自己想要的位置创建文件夹，如我hexo文件夹的位置为E:\hexo，名字和地方可以自由选择，当然最好不要放在中文路径下。之后进入文件夹，即E:\hexo内，点击鼠标右键，选择Git Bash，执行以下命令，Hexo会自动在该文件夹下下载搭建网站所需的所有文件。
```Bash
$ hexo init
```
安装依赖包
```Bash
$ npm install
```
在E:\hexo内执行以下命令：
```Bash
$ hexo g
$ hexo s
```
然后用浏览器访问http://localhost:4000/，
此时，你应该看到了一个漂亮的博客了，当然这个博客只是在本地的，别人是看不到的，hexo3.0使用的默认主题是landscape。

3.配置Hexo
------------------------------------------------
进入hexo文件夹，找到__config.yml在最后加代码如下
```Bash
deploy:      
type: git   #最新版3.X把这个github缩写成git了     
repository: https://github.com/你的github账号/你的github账号.github.io.git      
branch: master
```
执行下面命令：
```Bash
hexo g 
hexo d
```
如果上面的hexo d命令没有反应，ERROR Deployer not found: git解决
```
npm install hexo-deployer-git --save
```
之后就可以执行hexo d了。
中间会提示输入账号，密码
如此完成！
在浏览器上输入：你的githun账号.github.io就可以访问你的博客了
但是如果你有自己的域名并且要绑定的话，请看第五步

五.域名绑定
=========================
1.购买域名
---------------------------------------
购买域名比较简单，此处不再介绍，我的是万维的：www.bestzhangjin.com
2.将独立域名与 GitHub Pages 的空间绑定
-----------------------------------
DNS 设置:
注册DNSpod，添加域名，如下图设置。
![blog-hexo](img/blog-hexo/3.png)
其中A的两条记录指向的ip地址是github Pages的提供的ip
192.30.252.153
192.30.252.154
如博客不能登录，有可能是 github 更改了空间服务的 ip 地址，记得及时到在GitHub Pages查看最新的ip即可
www 指定的记录是你在 github 注册的仓库

去阿里云（因为阿里云、万维合作--我在阿里云买的域名）修改 DNS 地址
进入阿里云找到域名修改DNS 地址
![blog-hexo](img/blog-hexo/4.png)

CNAME文件上传
在hexo文件的source目录下创建一个名字为CNAME的文件
文件内容：
http://beastzhangjin.com
每个人的不一样---------为自己的域名
然后执行仿照第三步hexo配置，输入hexo g hexo d上传即可
浏览器上输入你的域名就可以访问你的博客了！




