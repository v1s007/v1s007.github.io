---
layout:     post
title:      Github+Jekyll搭建个人博客（最新版）
subtitle:   手把手教你建个人站点
date:       2018-07-30
author:     LZP[原创]
header-img: img/bg-it6.jpg
catalog: true
tags:
    - Blog
    - Github
    - Jekyll
---

# Github+Jekyll搭建个人博客（最新版）

------

**写在前面的话：**

> 搭建博客，最简单的方式，就是到各种博客网站上，注册一个账号，一切就OK了！
> 但如果想自己控制一切，随意的式样，随意添加功能，就是本文所讲：自己搭建！ 

------

## 博客的搭建教程

* 入门
	* [需要什么环境？](#需要什么环境？)
	* [开始搭建环境](#开始搭建环境)
	* [撰写博文](#撰写博文)
* 进阶
	* [挑选模板](#挑选模板)
	* [迷你关于我](#mini-about-me)
	* [推荐标签](#featured-tags)
	* [好友链接](#friends)
	* [HTML5 演示文档布局](#keynote-layout)
	* [评论](#comment)
	* [网站分析](#analytics) 
* 高级部分
	* [自定义](#customization)
	* [标题底图](#header-image)
	* [搜索展示标题-头文件](#seo-title)

****

### 需要什么环境？

- 1.一个互联网上的主机/虚拟主机
- 2.一个本地写好的Web网站（本质就是写好的一堆html文件的组合，最简单的方式，就是一个html文件，命名为index.html，在地址栏里不写文件名时， 
    默认就是这个文件），Web网站放到主机/虚拟主机上的时候，会有一个IP地址，或者是二级域名。
- 3.一个自己的域名，这个需要先在域名注册网站上查找，找自己喜欢，并且别人没有注册的，然后自己花钱注册一个。
    然后把这个域名指向前面那个IP地址，或者二级域名。
- 4.可以通过自己的域名访问了！http://你的域名 （上面的第三步也可以省略，就可以通过http://IP地址，或者http://二级域名访问。）

****

### 开始搭建环境

#### 一：一个互联网上的主机/虚拟主机

 - 要想在互联网上发布信息，让其他人能够浏览这些信息，需要一个连在互联网上的主机/虚拟主机：......
 - Github就是我们选择的连在互联网上的主机/虚拟主机，Github是互联网上的一个版本控制平台，也是一个开发者社区，Github提供了Github Pages服务，这是一个静态Web服务器，意味着你不能在服务器上执行你写的任何程序。但可以把静态Web页面放在上面，供其他人浏览。
 - Github的公共开源项目是免费的，所以，无需交纳任何费用，就可以拥有自己的虚拟主机：[**Github Pages**](http://github.com)，方法如下：
	- 第一步：在http://github.com上注册账号（准备好电子邮箱，需要验证电子邮箱）
	- 第二步：在Start a Project(开始一个工程)，工程名字随便取，  如果取“你的账号名.github.io”作为工程名字，以后可以直接通过https://你的账号名.github.io访问，如果取其它名字，通过htttps://你的账号名.github.io/工程名来访问。**号外！号外！这一步，可以先不做，因为后面有捷径**

**现在，我们在互联网上的主机就找好了，那就是Github Pages，它提供给你的二级域名就是 https://你的账号.github.io ，或者 htttps://你的账号名.github.io/工程名**

----

#### 二：写好自己的静态网站
 - 第一：各种常见的网站都不用写（开发），都有现成的工具，可以直接生成！只需要准备好自己想发布的图片和文字（文章）就可以了。
 - 第二：这样的工具有jekyll（Github Pages默认支持的）、Hugo、Hexo、Sphinx、......
 - 我们要下载一个上面的工具，然后开始写自己的网站吗？NO！NO！NO！
 - 世界很简单，因为有复制！我们选择直接复制一个，前面说过，github是一个开源的开发者社区，这里面，各种各样的网站都有，并且都是开放源码的，不只是源码，你可以看到全部：代码、图片、数据，随你修改。
 - 我列出几个还不错的，你随便复制：
	- https://github.com/longzeping/longzeping.github.io.git
		- 上面是源码地址，先看网站中不中意：https://longzeping.github.io
	- https://github.com/huxpro/huxpro.github.io.git
		- 上面是源码地址，先看网站中不中意：https://huxpro.github.io
	- https://github.com/gaohaoyang/gaohaoyang.github.io.git
  		- 上面是源码地址，先看网站中不中意：https://gaohaoyang.github.io
	- https://github.com/qiubaiying/qiubaiying.github.io.git
  		- 上面是源码地址，先看网站中不中意：https://qiubaiying.github.io
	- 