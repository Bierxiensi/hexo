---
title: node学习笔记（四）
date: 2019-11-12 15:29:22
categories:
- [技术, study, node学习笔记]
tags: [node]
photos: /img/node/node学习笔记/node学习笔记（一）/cover.jpg
description: Node.js 函数
comments: true
author: zxy
avatar: /img/zxyaily/food.jpg
authorAbout: zxyaily
authordesc: ilikely
---
# 写在前面 
#### Node.js 的事件、监听器的整个生命周期这两个角度，对 Node.js 进一步讲解。
#### 知识点
- 事件概述
- EventEmitter
- 监听器相关操作
- error事件

## 事件

### EventEmitter
所有能触发事件的对象都是 EventEmitter 类的实例。这些对象有一个 eventEmitter.on() 函数，用于将一个或多个函数绑定到命名事件上。当 EventEmitter 对象触发一个事件时，所有绑定在该事件上的函数都会被同步地调用。

#### 添加监听器
1. emitter.on(eventName, listener)
使用 emitter.on(eventName, listener) 方法为指定事件注册一个监听器。添加 listener 函数到名为 eventName 的事件的监听器数组的末尾。 不会检查 listener 是否已被添加。 多次调用并传入相同的 eventName 与 listener 会导致 listener 会被添加多次。
emitter.addListener(eventName, listener) 是 emitter.on(eventName, listener) 的别名。
2. 参数说明：
  - eventName：事件名称，string 类型。
  - listener：回调函数。
3. 例子：
<pre><code>// 引入 events 模块
var events = require('events');
// 创建 server 对象
var emitter = new events.EventEmitter();
// 为 connection 事件注册一个监听器
emitter.on('connection', function(){
    console.log('已连接');
})
// 箭头函数，有兴趣的可以自行了解一下
emitter.prependListener('connection',() =>console.log('zxyaily'))
// 一秒后调用监听器
setTimeout(function() {
   emitter.emit('connection');
}, 1000);</code></pre>

#### 调用监听器
1. emitter.emit(eventName[, ...args]) 
使用 emitter.emit(eventName[, ...args]) 按照监听器注册的顺序，同步地调用每个注册到名为 eventName 的事件的监听器，并传入提供的参数。如果事件有注册监听返回 true，否则返回 false。
2. 参数说明：
    - eventName ：事件名称
    - args：传递的参数，多个，类型为任意。
3. 例子：
<pre><code>// 引入 events 模块
var events = require('events');
// 创建 emitter 对象
var emitter = new events.EventEmitter();
//定义一个回调函数
var callback1 =  function(arg1,arg2,arg3) {
console.log('callback1',arg1,arg2,arg3);
};
var callback2 = function(arg4, arg5, arg6) {
console.log('callback2',arg4, arg5, arg6);
};
//为 connection 事件注册监听器
emitter.on('connection',callback1);
emitter.on('connection',callback2);
//调用监听器
emitter.emit('connection','zxy','ai','ly');</code></pre>
执行结果
<pre><code>callback1 zxy ai ly
callback2 zxy ai ly</code></pre>
同名事件可以重复触发

#### 只执行一次的监听器
1. eventEmitter.on(eventName, listener)
当使用 eventEmitter.on(eventName, listener) 注册监听器时，监听器会在每次触发命名事件时被调用。
<pre><code>// 引入 events 模块
var events = require('events');
// 创建 emitter 对象
var emitter = new events.EventEmitter();
//为 connection 事件注册一个监听器
var n = 0;
emitter.on('connection', function() {
   ++n;
 console.log('调用第'+ n + '次');
});
//调用监听器
emitter.emit('connection');
emitter.emit('connection');
emitter.emit('connection');
emitter.emit('connection');</code></pre>

emitter.prependOnceListener() 方法可用于将事件监听器添加到监听器数组的开头。用法与我们前面所学的 emitter.prependListener() 方法一致，区别在于这个方法注册的监听器最多只能调用一次。

#### 移除监听器
emitter.removeListener(eventName, listener)


1048542019004471
