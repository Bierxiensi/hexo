---
title: node学习笔记（三）
date: 2019-11-12 12:38:49
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
#### 本篇对 Node.js 函数的概念进行讲述。
#### 知识点
- Node.js 中的函数
- 匿名函数
- Node.js 异步编程

#### 简介
Node.js 大部分模块都由 js 编写，所以函数的语法与 js 基本相同

## Node.js中的函数
在JavaScript中，一个函数可以作为另一个函数的参数。我们可以先定义一个函数，然后传递，也可以在传递参数的地方直接定义函数。
Node.js中函数的使用与Javascript类似，代码如下：

    function zxyaily(value){
        console.log(value)
    }
    function execute(Func,value){
        Func(value)
    }
    execute(zxyaily,'zxy❥(^_-)ly')
    
或者

    function execute(Func,value){
        Func(value)
    }
    execute(function(value){
        console.log(value)
    },'zxy❥(^_-)ly')

用这种方式，我们甚至不用给这个函数起名字，这也是为什么它被叫做匿名函数。
## 匿名函数
匿名函数就是没有命名的函数。语法为：
    
    function(){
    
    }

### 箭头函数
ES6 标准新增了一种新的函数，箭头函数表达式的语法比函数表达式更短，并且没有自己的 this，arguments，super 或 new.target。这些函数表达式更适用于那些本来需要匿名函数的地方，并且它们不能用作构造函数。
语法为:

    (参数1, 参数2, …, 参数N) => { 函数声明 }
    
    //相当于：(参数1, 参数2, …, 参数N) =>{ return 表达式; }
    (参数1, 参数2, …, 参数N) => 表达式（单一）
    
    // 当只有一个参数时，圆括号是可选的
    (单一参数) => {函数声明}
    单一参数 => {函数声明}
    
    // 没有参数的函数应该写成一对圆括号。
    () => {函数声明}

如

    function(){
        console.log('hello syl');
    }
    //上面的匿名函数可以用箭头函数改写为下面的
    () => console.log('hello syl');


## Node.js 异步编程
Node.js异步编程的直接体现就是回调。回调函数在完成任务后就会被调用，Node.js使用了大量的回调函数，Node.js所有API都支持回调函数。回调函数一般作为函数的最后一个参数出现。

### Node.js 回调函数
Node.js 异步编程的直接体现就是回调。异步编程依托于回调来实现，但不能说使用了回调后程序就异步化了。回调函数在完成任务后就会被调用，Node 使用了大量的回调函数，Node 所有 API 都支持回调函数。例如，我们可以一边读取文件，一边执行其他命令，在文件读取完成后，我们将文件内容作为回调函数的参数返回。这样在执行代码时就没有阻塞或等待文件 I/O 操作。这就大大提高了 Node.js 的性能，可以处理大量的并发请求。回调函数一般作为函数的最后一个参数出现：

    function foo1(name, age, callback) { }
    function foo2(value, callback1, callback2) { }

先创建一个 hello.txt 的文件，里面随便输入一段文本内容，比如：zxyaily。
#### 阻塞代码实例

    var fs = require("fs");
    var data = fs.readFileSync('hello.txt');
    console.log(data.toString());
    console.log("程序执行完毕!");
    
执行结果

    zxyaily
    程序执行完毕！

#### 非阻塞代码

    var fs = require("fs");
    fs.readFile('hello.txt', function (err, data) {
        if (err) return console.error(err);
        console.log(data.toString());
    }); 
    console.log("程序执行完毕!");

执行结果

    程序执行完毕！
    zxyaily
