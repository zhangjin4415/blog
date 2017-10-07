title: hexo用法讲解
date: 2016-01-07 20:09:17
categories: "博客"
tags: "Hexo"
---
主要内容：新建页面，文章摘要，添加评论框，RSS订阅功能，站点地图sitemap插件
<!--more-->
一.新建页面
================
```
hexo new "新建页面的文件名"
```
二.文章摘要
==============

在需要显示摘要的地方添加如下代码即可：RSS订阅功能

```
以上是摘要...<!--more-->...以下是余下全文
```

三.添加评论框
==============
注册多说账号，得到对应域名

打开主题下的_config.yml加上
```
duoshuo_shortname: bestzhangjin
```
其中bestzhangjin是我在多说的二级域名

四.RSS订阅功能
===============
RSS插件安装：
```
npm install hexo-generator-feed
```
RSS功能开启：
博客根目录下的_config.yml：
```
plugins: hexo-generator-feed

# feed
feed:
  type: feed 
  path: atom.xml 
  limit: 20
```
重新布置到博客之后在博客上就可以看到RSS按钮，别人可以订阅你的博客了

下面在Chrome浏览器添加RSS Feed Reader，以便你可以订阅别人的博客
打开Chrome浏览器，点击设置，拓展程序，查找输入：RSS Feed Reader，找到后添加即可，然后再浏览器右上角可以看到一个对应的图标，点击图标可以添加

五.谷歌站点地图sitemap插件
======================
1.sitemap介绍
---------------
Sitemap 可方便网站管理员通知搜索引擎他们网站上有哪些可供抓取的网页。最简单的 Sitemap 形式，就是XML 文件，在其中列出网站中的网址以及关于每个网址的其他元数据（上次更新的时间、更改的频率以及相对于网站上其他网址的重要程度为何等），以便搜索引擎可以更加智能地抓取网站。
Google、雅虎、和微软都支持一个被称为xml网站地图（xml Sitemaps）的协议，而百度Sitemap是指百度支持的收录标准，在原有协议上做出了扩展。

2.sitemap安装
-----------------------------
Git bash下输入命令：
```
npm install hexo-generator-sitemap
```
也可以
```
npm install hexo-generator-sitemap --save
```

根目录下的_config.xml添加内容：
```
plugins: hexo-generator-sitemap

#sitemap
sitemap:
  path: sitemap.xml
```

输入如下命令：
```
hexo g
hexo d
```
在你的github上可以看到文件sitemap.xml

3.向google提交sitemap
-------------------------
google帐号登陆Webmaster Central:
英文入口：https://www.google.com/webmasters/verification/home?hl=en
中文入口：https://www.google.com/webmasters/verification/home?hl=zh
我用中文入口
点击添加属性，输入你的网址URL，点击继续
点击备用方法，选中HTML标记，将提供的如下代码(每个人的应该不一样)：
```
<meta name="google-site-..................." />
```
复制到blog\themes\hexo-theme-next\layout\_partials\head.swig中(有的是对应目录下的head.ejs)
利用hexo g,hexo d布置上去
点击Webmaster Central网页中的验证
验证成功显示：恭喜！http://www.bestzhangjin.com/ 现已通过验证！现在，您可以针对自己的资源使用 Search Console 等 Google 服务了。

在站点地图中添加你刚刚在生成的站点地图sitemap.xml，并点击提交
网址：https://www.google.com/webmasters/tools/home?hl=zh-CN
在添加资源框内输入自己网址：我的http://www.bestzhangjin.com
之后点击添加资源，再弹出的页面上点击添加站点地图，输入：sitemap.xml
点击提交sitemap
提醒：
如果站点地图提示错误http://yoursite.com/....的话，说明你的_config.xml中默认的http://yoursite.com还没有改成你自己的网址，改过来再重新生成添加即可


4.升级与卸载插件
------------------------
命令如下：
```
npm update
npm uninstall hexo-generator-sitemap
```


六.百度站点地图baidusitemap插件
=========================
1.安装
------------
国内用户需要安装插件 hexo-generator-baidu-sitemap, 是为百度量身打造的. 安装
```
npm install hexo-generator-baidu-sitemap --save
```
根目录下_config.yml
```
baidusitemap:
  path: baidusitemap.xml
```
利用hexo g,hexo d生成并上传，在你的github项目里面可以看到多了一个文件baidusitemap.xml
2.上传baidusitemap.xml
------------------
进入百度站长平台：http://zhanzhang.baidu.com/dashboard/index
点击添加站点，输入自己的网址，如我的：www.bestzhangjin.com
此处有三种方法，我选择的是HTML标签验证
将得到百度提供的如下的代码：
```
<meta name="baidu-site-verification" content="Si------" />
```
将代码复制到blog\themes\hexo-theme-next\layout\_partials\head.swig中(有的是对应目录下的head.ejs)
利用hexo g,hexo d布置上去
点击完成验证
验证号以后就可以在 链接提交->Sitemap 里面提交 Sitemap 了

