---
title: docker学习笔记(一)
date: 2019-10-30 09:27:58
tags: [docker]
categories:
- [技术, study, docker]
photos: /img/docker/docker学习随笔/docker学习笔记（一）/docker学习笔记（一）banner.jpg
comments: true
index_img: /img/docker/docker学习随笔/docker学习笔记（一）/docker学习笔记（一）banner.jpg
banner_img: /img/docker/docker学习随笔/docker学习笔记（一）/docker学习笔记（一）banner.jpg
description: docker个人学习随笔
author: zxy
avatar: /img/zxyaily/food.jpg
authorAbout: zxyaily
authordesc: i like ly
---

# 学习初衷
{% blockquote [by-PM] %}
我们需要的不是前端或者后端，而是能解决问题的人。
{% endblockquote %}
作为一个前端，或者说api调用者，对本地测试完merger代码后的过程一无所知实在是一件可笑的事情。

# 1、why pick docker？
项目驱动

# 2、what is docker？

## 2.1、官网上如是说
{% img [class names] /img/docker/docker学习随笔/docker学习笔记（一）/docker学习笔记（一）whatisdocker（1）.jpg [width] [height] "title text 'alt text'" %}
大概就是说，这是一个XXXX平台，允许你XXXX操作，使用了docker你可以XXXX，省时省力爽到起飞，就是一句话---好用。还说了什么呢？
{% img [class names] /img/docker/docker学习随笔/docker学习笔记（一）/docker学习笔记（一）whatisdocker（2）.jpg [width] [height] "title text 'alt text'" %}

通俗的说
{% blockquote @alwaysVe https://segmentfault.com/a/1190000019487122 %}
Docker 可理解为跑在宿主机上的非常精简、小巧、高度浓缩的虚拟机。 它可以将容器里的进程安稳的在宿主机上运行。
Docker重要的三个概念必须要知道：
Image: 镜像
Container: 容器
Repository： 镜像仓库
为了好理解 我们从 Docker 的 Logo 入手
图片是一条鲸鱼游在海里 身上载着N个集装箱，下面是Docker字样。OK 图片描述完毕
图片给出的信息：
-海：宿主机
-集装箱：Docker容器
-鲸鱼+集装箱：Docker技术
也就是说：Docker容器（集装箱）里可以存放着我们写的代码，然后 Docker 载着代码在大海（宿主机）里运行
之所以用鲸鱼，可能是它在海里没什么天敌 体型又巨大而且游泳速度很快，毕竟Docker使用GO语言写的呢。
{% endblockquote %}

## 2.2、Docker重要的三个概念必须要知道：
Image: 镜像
Container: 容器
Repository： 镜像仓库

## 2.3、keys：
{% blockquote @alwaysVe https://segmentfault.com/a/1190000019487122 %}
 1：属于 Linux 容器的一种封装，提供简单易用的容器使用接口。
 2：将应用程序与该程序的依赖，打包在一个文件里面。运行这个文件，就会生成一个虚拟容器。
 程序在这个虚拟容器里运行，就好像在真实的物理机上运行一样.
{% endblockquote %}
 
{% blockquote @weixin_33895657 https://blog.csdn.net/weixin_33895657/article/details/93167085 %}
上文中只说了Container，而Image与Container的关系 就像类与实例的关系:
var p1 = new Person();
即：p1是容器、Person是镜像。
{% endblockquote %}

# 3、docker安装
## step1 进入官网 get docker
{% img [class names] /img/docker/docker学习随笔/docker学习笔记（一）/docker学习笔记（一）install1.jpg [width] [height] "title text 'alt text'" %}
## step2 get docker engine 我的操作系统是windows10 选择windows engine
{% img [class names] /img/docker/docker学习随笔/docker学习笔记（一）/docker学习笔记（一）install2.jpg [width] [height] "title text 'alt text'" %}
## step3 环境需求 可以看到docker for win支持win10 需要Hyper-V虚拟机
{% img [class names] /img/docker/docker学习随笔/docker学习笔记（一）/docker学习笔记（一）install3.jpg [width] [height] "title text 'alt text'" %}
## 看来安装教程不怎么友好
{% img [class names] /img/docker/docker学习随笔/docker学习笔记（一）/docker学习笔记（一）install4.jpg [width] [height] "title text 'alt text'" %}
## step4 我的环境 windows10家庭版
{% img [class names] /img/docker/docker学习随笔/docker学习笔记（一）/docker学习笔记（一）install5.jpg [width] [height] "title text 'alt text'" %}
## step5 docker对windows不同版本的支持
{% img [class names] /img/docker/docker学习随笔/docker学习笔记（一）/docker学习笔记（一）install6.jpg [width] [height] "title text 'alt text'" %}
{% img [class names] /img/docker/docker学习随笔/docker学习笔记（一）/docker学习笔记（一）install7.jpg [width] [height] "title text 'alt text'" %}

{% blockquote @zhuiyisinian https://blog.csdn.net/zhuiyisinian/article/details/88700889 %}
最早的docker只能运行在linux上，所以以前如果想在win上使用docker只能通过虚拟机的方式。不过，近两年微软和docker达成了合作关系，也开发出了基于windows的docker引擎。
如果去网上查资料的话，大部分都比较老旧，会让你下载安装docker toolbox，但它总体来说不如docker for windows方便，所以此处不考虑toolbox的安装。（PS：toolbox和docker for windows不能很好的共存，同时安装会出现错误。而且即使安装过toolbox后再卸载之后安装docker for win也会出现一些错误，我下面会提到一些）
另外，很重要的一点，docker for win目前只支持win10，其他版本的win系统目前只能使用toolbox.
{% endblockquote %}

## step6 
{% img [class names] /img/docker/docker学习随笔/docker学习笔记（一）/docker学习笔记（一）install8.jpg [width] [height] "title text 'alt text'" %}
可以看到 windows10家庭版是没有Hyper-V虚拟机的  现在就有两个选择了
方案一：通过docker toolbox来安装
方案二：hyper时win10自带一个虚拟机，安装Hyper-V虚拟机
我选择方案一安装Hyper-V虚拟机，注意查看处理器是否支持虚拟化技术，不支持的话，就别费劲找回Hyper-V功能了

## step7 systeminfo 查看处理器是否支持虚拟化技术 重点信息的最后，4个要求全都是“是”，确定电脑支持虚拟化技术。
{% img [class names] /img/docker/docker学习随笔/docker学习笔记（一）/docker学习笔记（一）install9.jpg [width] [height] "title text 'alt text'" %}

## step8 将如下代码添加到记事本中，并另存为Hyper-V.cmd文件，之后以管理员身份打开这个文件，重启完成就能使用功能完整的Hyper-V了。（注意添加功能需要联网哦）
```$xslt
pushd "%~dp0"
dir /b %SystemRoot%\servicing\Packages\*Hyper-V*.mum >hyper-v.txt
for /f %%i in ('findstr /i . hyper-v.txt 2^>nul') do dism /online /norestart /add-package:"%SystemRoot%\servicing\Packages\%%i"
del hyper-v.txt
Dism /online /enable-feature /featurename:Microsoft-Hyper-V-All /LimitAccess /ALL
``` 
## step9 安装完成 重启电脑 查看程序信息 可以看到已经安装完成
PS:安装了Hyper-v之后，virtualbox和vmware之类的虚拟机就无法使用，具体解决方法自行百度
{% img [class names] /img/docker/docker学习随笔/docker学习笔记（一）/docker学习笔记（一）install10.jpg [width] [height] "title text 'alt text'" %}
{% img [class names] /img/docker/docker学习随笔/docker学习笔记（一）/docker学习笔记（一）install11.jpg [width] [height] "title text 'alt text'" %}

## 然而看到这位仁兄的操作后还是放弃家庭版安装了 改完注册表后还是绕不开家庭版检查 没办法 不想重新装系统 只能选择方案一
{% blockquote @颹蕭蕭 https://blog.csdn.net/itnerd/article/details/88920230 %}
{% endblockquote %}

##待续


