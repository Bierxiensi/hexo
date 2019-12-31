---
title: JavaScriptWebApI
date: 2019-11-18 12:16:38
categories:
- [技术, study, JavaScriptWebApI]
tags: [JavaScript]
photos:
description:
comments: true
---
# 写在前面
#### 浏览器是一个封装的较为完善的软件，它给我们提供了操作浏览器功能和页面元素的接口
#### 知识点
- API 概念
- BOM 简介
- BOM 的顶级对象window
- DOM 简介
- DOM HTML
- DOM CSS
- DOM 节点
- DOM 事件

>API（Application Programming Interface,应用程序编程接口）: " 计算机操作系统 "
>（Operating system）或 " 程序库 " 提供给应用程序调用使用的代码。其主要目的是让应用程序
>开发人员得以调用一组例程功能，而无须考虑其底层的源代码为何、或理解其内部工作机制的细节。
>API本身是抽象的，它仅定义了一个接口，而不涉及应用程序在实际实现过程中的具体操作。
>Web API 是浏览器提供的一套操作浏览器功能和页面元素的 API(BOM 和 DOM)。

## BOM
浏览器对象模型(BOM)指的是由 Web 浏览器暴露的所有对象组成的表示模型。<font color=red>BOM 与 DOM 不同，其既没有标准的
实现，也没有严格的定义</font>, 所以浏览器厂商可以自由地实现 BOM。作为显示文档的窗口, 浏览器程序将其视为对象的分
层集合。当浏览器分析文档时, 它将创建一个对象的集合, 以定义文档, 并详细说明它应如何显示。浏览器创建的对象称
为文档对象。它是浏览器使用的更大的对象集合的一部分。此浏览器对象集合统称为浏览器对象模型或 BOM。BOM 
层次结构的顶层是窗口对象, 它包含有关显示文档的窗口的信息。某些窗口对象本身就是描述文档和相关信息的对象。

### BOM 的顶级对象 window 以及常用操作方法
window 是浏览器的顶级对象，当调用 window 下的属性和方法时，可以省略 window。
#### 对话框
- alert()：显示带有一段消息和一个确认按钮的警告框。
- prompt():显示可提示用户输入的对话框。
- confirm():显示带有一段消息以及确认按钮和取消按钮的对话框。

#### 页面加载事件
1. onload
<pre><code>window.onload = function () {
 // 当页面加载完成执行
 // 当页面完全加载所有内容（包括图像、脚本文件、CSS 文件等）执行
}
</code></pre>
2. onunload
<pre><code>window.onunload = function () {
 // 当用户退出页面时执行
}</code></pre>

#### 浏览器尺寸
<pre><code>var width = window.innerWidth
|| document.documentElement.clientWidth
|| document.body.clientWidth;

var height = window.innerHeight
|| document.documentElement.clientHeight
|| document.body.clientHeight;</code></pre>
上述代码可以获取所有浏览器的宽高(（不包括工具栏/滚动条）)。

#### 定时器
1. setTimeout() 方法在指定的毫秒数到达之后执行指定的函数，<font color=red>只执行一次</font>。clearTimeout() 方法取消由 setTimeout() 方法设置的 timeout。
<pre><code>// 创建一个定时器，2000毫秒后执行，返回定时器的标示
var timerId = setTimeout(function () {
 console.log('Hello shiyanlou');
}, 2000);
// 取消定时器的执行
clearTimeout(timerId);</code></pre>

2. setInterval() 方法设置定时调用的函数也就是可以按照给定的时间(单位毫秒)<font color=red>周期调用</font>函数，clearInterval() 方法取消由setInterval() 方法设置的 timeout。
<pre><code>// 创建一个定时器，每隔2秒调用一次
var timerId = setInterval(function () {
 var date = new Date();
 console.log(date.toLocaleTimeString());
}, 2000);
// 取消定时器的执行
clearInterval(timerId);</code></pre>
