title: Ubuntu学习
date: 2016-02-26 12:55:12
categories: "Ubuntu"
tags: "Ubuntu"
---
主要内容:
<!--more-->
第一章 终端
================
1.打开终端命令快捷键
----------------------

```
ctrl+alt+f1		//打开字符模式终端
ctrl+alt+T		//打开图像模式终端
ctrl+alt+f7		//退出终端回到桌面
```

第二章 vim安装与配置
===============
1.vim介绍
-------------
vim是从VI发展而来的一个文本编辑器，功能更强大
在命令行敲入“vi”后按"tab"键，可以看到目前系统中只安装了vi和vim.tiny，vim.tiny是vim的精简版

2.vim安装
--------------------
终端输入:
sudo apt-get update
sudo apt-get install vim
安装完成之后，在命令行敲入vi，按“tab”键。

可以看到，已经有vim命令的存在。

安装成功。现在vim可以用了，但是不太方便，为了更人性化，我们对他进行配置


3.vim配置
-------------
现在按照我们的需求去修改它
在命令行下，输入命令：sudo vim /etc/vim/vimrc

必须加上sudo，否则你是没有权限编辑vimrc的

请在您的VIM的最后一行，输入他们，可以让您的VIM变得更漂亮、舒服。

set nu                           " 在左侧行号
set ai!                          "设置自动缩进
set incsearch                "设置单词匹配
set tabstop=4                "tab 长度设置为 4
set shiftwidth=4             "设置当行之间交错时使用4空格
set nobackup                 "覆盖文件时不备份
set ruler                        "在右下角显示光标位置的状态行
set showmatch                "设置匹配模式
set cindent                  "cindent是针对C语言语法自动缩进
set mouse=a                  "设置鼠标点击时有反应            
保存之后，配置完毕。

上面的配置，其实是非常简单的，比如一些配色方案等，并没有写入，如果您还有其他需求的话，建议百度。

保存后退出，现在界面已经变得友好了


第三章 软件安装篇
=================




****************************
更新中............

