---
title: JavaScript语法
date: 2019-11-15 13:07:20
categories:
- [技术, study, JavaScript学习笔记]
tags: [JavaScript]
photos:
description:
comments:
---
####

## 语句
- 执行单位为行（line）。
- 一般情况下，每一行就是一个语句。
- 语句以分号结尾，一个分号就表示一个语句结束
- 分号前面可以没有任何内容，JavaScript 引擎将其视为空语句。

## 变量
- 变量名区分大小写，A和a是两个不同的变量。

### 变量提升
JavaScript 引擎的工作方式是，先解析代码，获取所有被声明的变量，然后再一行一行地运行。这造成的结果，就是所有的变量的声明语句，都会被提升到代码的头部，这就叫做变量提升（hoisting）

    console.log(a);
    var a = 1;

上面代码首先使用console.log方法，在控制台（console）显示变量a的值。这时变量a还没有声明和赋值，所以这是一种错误的做法，但是实际上不会报错。因为存在变量提升，真正运行的是下面的代码。

    var a;
    console.log(a);
    a = 1;

标识符命名规则如下。

    第一个字符，可以是任意 Unicode 字母（包括英文字母和其他语言的字母），以及美元符号（$）和下划线（_）。
    第二个字符及后面的字符，除了 Unicode 字母、美元符号和下划线，还可以用数字0-9。
    中文是合法的标识符，可以用作变量名。
   
## 标识符 
保留字，不能用作标识符：
    
    arguments、break、case、catch、class、const、continue、debugger、default、delete、do、else、enum、eval、export、extends、false、finally、for、function、if、implements、import、in、instanceof、interface、let、new、null、package、private、protected、public、return、static、super、switch、this、throw、true、try、typeof、var、void、while、with、yield。

## 注释

    // 这是单行注释

    /*
     这是
     多行
     注释
    */
此外，由于历史上 JavaScript 可以兼容 HTML 代码的注释，所以<!--和-->也被视为合法的单行注释。

    x = 1; <!-- x = 2;
    --> x = 3;

上面代码中，只有x = 1会执行，其他的部分都被注释掉了。需要注意的是，-->只有在行首，才会被当成单行注释，否则会当作正常的运算。

## 区块 
JavaScript 使用大括号，将多个相关的语句组合在一起，称为"区块"（block）。对于var命令来说，JavaScript 的区块不构成单独的作用域（scope）。
 
    {
      var a = 1;
    } 
    a // 1
上面代码在区块内部，使用var命令声明并赋值了变量a，然后在区块外部，变量a依然有效，区块对于var命令不构成单独的作用域，与不使用区块的情况没有任何区别。

## 条件语句

### if结构

### if...else

### switch

### ?:(三目运算符)

## 循环语句

### while循环

### for循环

### do...while循环

### break语句和continue语句

### 标签
