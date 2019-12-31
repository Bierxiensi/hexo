---
title: node学习笔记（一）
date: 2019-10-31 22:01:58
categories:
- [技术, study, node学习笔记]
tags: [node, mysql]
photos: /img/node/node学习笔记/node学习笔记（一）/cover.jpg
description: Node.js 简介及简单使用
comments: true
author: zxy
avatar: /img/zxyaily/food.jpg
authorAbout: zxyaily
authordesc: ilikely
---
# 写在前面
早就听说node.js强大，虽然一直在用node的npm工具，但无奈一直没有写脚本
今天有时间看一看，哇，这个node脚本 它又短又强悍，哦呦，不对哦，这和python脚本差不多嘛
{% img [class names] /img/node/node学习笔记/node学习笔记（一）/1.jpg [width] [height] "title text 'alt text'" %}
{% img [class names] /img/node/node学习笔记/node学习笔记（一）/4.jpg [width] [height] "title text 'alt text'" %}

这段python脚本用的pymysql(另SQLAlchemy的语法看起来类似javaJpa吧)，过程上类似，建立查询，执行sql语句
{% img [class names] /img/node/node学习笔记/node学习笔记（一）/2.jpg [width] [height] "title text 'alt text'" %}

好了，接下来进入正题
# 1、Node.js 概述
{% blockquote 维基百科 https://wikipedia.tw.wjbk.site/wiki/Node.js %}
- Node.js 是一个能够在服务器端运行 JavaScript 的开放源代码、跨平台 JavaScript 运行环境。
- Node.js 由 Node.js 基金会持有和维护，并与 Linux 基金会有合作关系。
- Node.js 采用 Google 开发的 V8 运行代码，使用事件驱动、非阻塞和异步输入输出模型等技术来提高性能，可优化应用程序的传输量和规模。这些技术通常用于数据密集的即时应用程序。
- Node.js 大部分基本模块都用 JavaScript 语言编写。<font color=red>
- 在 Node.js 出现之前，JavaScript 通常作为客户端程序设计语言使用，以JavaScript 写出的程序常在用户的浏览器上运行。Node.js 的出现使 JavaScript 也能用于服务端编程。
</font>
- Node.js 含有一系列内置模块，使得程序可以脱离 Apache HTTP Server 或 IIS，作为独立服务器运行。
{% endblockquote %}

# 2、Node.js 特点
- 它是一个 JavaScript 运行环境。
- 依赖于 Chrome V8 引擎进行代码解释。
- 事件驱动：在 Node 中，客户端请求建立连接，提交数据等行为，会触发相应的事件。在 Node 中，在一个时刻，只能执行一个事件回调函数，但是在执行一个事件回调函数的中途，可以转而处理其他事件，然后返回继续执行原事件的回调函数。
- 非阻塞 I/O：Node.js 中采用了非阻塞型 I/O 机制，在执行了访问数据库的代码之后，将立即转而执行其后面的代码，把数据库返回结果的处理代码放在回调函数中，从而提高了程序的执行效率。
- 轻量可伸缩，适用于实时数据交互应用。
- 单线程：好处是减少内存开销，不用像多线程编程那样处处在意状态同步的问题。缺点是错误会引起整个应用退出。

# 3、Node.js 适用场景
我们从 Node.js 的特点中可以知道 Node.js 擅长处理 I/O，不善于计算（单线程的缺点），因此 Node.js 适用于：
- 当应用程序需要处理大量并发的 I/O，而在向客户端发出响应之前，应用程序内部并不需要进行非常复杂的处理的时候，
- Node.js 也非常适合与 web socket 配合，开发长连接的实时交互应用程序。比如：聊天室，博客系统，考试系统等。

## 3.1、cmd查看系统中 Node.js 版本:

    node -v
## 3.2、node安装:
https://nodejs.org/en/

# 4、NPM 介绍
NPM 是随同 Node.js 一起安装的包管理工具。因此当我们安装好 Node.js 的时候，也安装好了 NPM。
NPM 是一个命令行工具，用于从 NPM Registry 中下载、安装 Node.js 程序，同时解决依赖问题。

cmd查看系统中 NPM 版本：

    npm -v

# 5、Node.js REPL(交互式解释器)
{% blockquote 菜鸟教程 https://www.runoob.com/nodejs/nodejs-repl.html %}
Node.js REPL(Read Eval Print Loop:交互式解释器) 表示一个电脑的环境，类似 Window 系统的终端或 Unix/Linux shell，我们可以在终端中输入命令，并接收系统的响应。
Node 自带了交互式解释器，可以执行以下任务：
- 读取 - 读取用户输入，解析输入了Javascript 数据结构并存储在内存中。
- 执行 - 执行输入的数据结构
- 打印 - 输出结果
- 循环 - 循环操作以上步骤直到用户两次按下 ctrl-c 按钮退出。
Node 的交互式解释器可以很好的调试 Javascript 代码。
{% endblockquote %}

## 5.1、REPL 常用命令
- Ctrl + C - 退出当前终端
- Ctrl + C - 连续按两次退出 Node REPL
- Ctrl + D - 退出 Node REPL
- 向上/向下 键 - 查看输入的历史命令
- tab 键 - 列出当前命令
- help - 列出使用命令
- break - 退出多行表达式
- clear - 退出多行表达式
- save filename - 保存当前的 Node REPL 会话到指定文件
- load filename - 载入当前 Node REPL 会话的文件内容。

## 5.2、启动 Node 终端
输入以下命令来启动 Node 终端：

    node

## 5.3、简单的表达式运算
<pre><code>$ node
> 1 +4
5
> 5 / 2
2.5
> 3 * 6
18
> 4 - 1
3
> 1 + ( 2 * 3 ) - 4
3
></code></pre>

## 5.4、使用变量
可以将数据存储在变量中，并在需要的时候使用它。
变量声明需要使用 var 关键字，如果没有使用 var 关键字变量会直接打印出来。
使用 var 关键字的变量可以使用 console.log() 来输出变量。
<pre><code>$ node
> x = 10
10
> var y = 10
undefined
> x + y
20
> console.log("Hello zxyaily")
Hello zxyaily
undefined
> console.log("www.zxyaily.top")
www.zxyaily.top
undefined</code></pre>

## 5.5、多行表达式
<pre><code>> for(var i=0;i<10;i++){
... console.log("mrZ ❤ missL");
... }
mrZ ❤ missL
mrZ ❤ missL
mrZ ❤ missL
mrZ ❤ missL
mrZ ❤ missL
mrZ ❤ missL
mrZ ❤ missL
mrZ ❤ missL
mrZ ❤ missL
mrZ ❤ missL
undefined
> </code></pre>

## 5.6、下划线变量
可以使用下划线(_)获取上一个表达式的运算结果：
<pre><code>$ node
> var x = 10
undefined
> var y = 20
undefined
> x + y
30
> var sum = _
undefined
> console.log(sum)
30
undefined
></code></pre>

# 6、Node.js 全局对象
在 JavaScript 中全局对象通常是 window，而在 Node.js 中全局对象是 globa，
所有全局变量（除了 global 本身以外）都是 global 对象的属性，我们可以直接访问到 global 的属性。

## 6.1、全局变量
global 最根本的作用是作为全局变量的宿主。按照 ECMAScript 的定义，满足以下条 件的变量是全局变量：
- 在最外层定义的变量；
- 全局对象的属性；
- 隐式定义的变量（未定义直接赋值的变量）。

定义一个全局变量的时候，这个变量同时也会成为全局对象的属性，反之亦然。在 Node.js 中不可能在最外层定义变量，因为所有用户代码都是属于当前模块的，而模块本身不是最外层上下文。<font color=red>定义变量一定要使用 var 关键字，因为全局变量会污染命名空间。</font>
详情见此例 https://wikipedia.tw.wjbk.site/wiki/Node.js

## 6.2、常用的全局变量和全局函数
### __filename 
表示当前正在执行的脚本的文件名。它将输出文件所在位置的绝对路径，且和命令行参数所指定的文件名不一定相同。
如果在模块中，返回的值是模块文件的路径。比如创建一个叫 hello.js 的文件，输入以下代码：

    console.log(__filename);
运行效果
    
    /home/project/hello.js

### __dirname 
表示当前执行脚本所在的目录。比如创建一个 hello.js 的文件，输入以下代码：

    console.log(__filename);
运行效果
    
    /home/project
    
### setTimeout(cb, ms) 
全局函数在指定的毫秒(ms)数后执行指定函数(cb),只执行一次函数。比如创建一个 hello.js 的文件，输入以下代码：
<pre><code>function hello(){
  console.log( "Hello, syl!");
}
// 三秒后执行以上函数
setTimeout(hello, 3000);</code></pre>

### clearTimeout(t) 
用于停止一个之前通过 setTimeout() 创建的定时器。 参数 t 是通过 setTimeout() 函数创建的定时器。比如清除上面案例的定时器：
<pre><code>function hello(){
  console.log( "Hello, syl!");
}
// 三秒后执行以上函数
var t = setTimeout(hello, 3000);
// 清除定时器
clearTimeout(t);</code></pre>

### setInterval(cb, ms) 
与 setTimeout(cb, ms) 类似，不同的是这个方法会不停的执行函数。直到 clearInterval() 被调用或窗口被关闭，也可以按 Ctrl+C 停止。比如创建一个 hello.js 的文件，输入以下代码：
<pre><code>function hello(){
  console.log( "Hello, syl!");
}
// 三秒后执行以上函数
var t = setInterval(hello, 3000);</code></pre>

### console.log() 
全局函数用于进行标准输出流的输出，即在控制台中显示一行字符串，和 JavaScript 中的使用一样。

<font color=red>console 用于提供控制台标准输出，它是由 Internet Explorer 的 JScript 引擎提供的调试工具，后来逐渐成为浏览器的实施标准。Node.js 沿用了这个标准，提供与习惯行为一致的 console 对象，用于向标准输出流（stdout）或标准错误流（stderr）输出字符。</font>
详情见console.log篇
