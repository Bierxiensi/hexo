---
title: Vue撸教程2.x（二）
date: 2019-10-31 13:54:18
categories:
- [技术, review, Vue撸教程]
tags: [vue-cli, vue]
photos: /img/vue/Vue撸教程2.x/Vue撸教程2.x（二）/1.jpg
comments: true
description: 学习反刍
author: zxy
avatar: /img/zxyaily/food.jpg
authorAbout: zxyaily
authordesc: i like ly
---
接着昨天的写 现在到了介绍部分
# 1、介绍
## 1.1、Vue.js 是什么
文档上这么说
>Vue (读音 /vjuː/，类似于 view) 是一套用于构建用户界面的渐进式框架。
>与其它大型框架不同的是，Vue 被设计为可以自底向上逐层应用。

关于渐进式框架，文档上对比的react  目前还都不是很了解
## 1.2、起步
官方要求HTML、CSS和JavaScript的中级知识 
脚手架em，反正，script标签引进来得会

## 1.3、声明式渲染
文档这么说
>Vue.js 的核心是一个允许采用简洁的模板语法来声明式地将数据渲染进DOM的系统

也就是数据的双向绑定，所见即所得吧
插值表达式形式
{% img [class names] /img/vue/Vue撸教程2.x/Vue撸教程2.x（二）/2.jpg [width] [height] "title text 'alt text'" %}

除了文本插值，我们还可以用v-bind绑定
{% img [class names] /img/vue/Vue撸教程2.x/Vue撸教程2.x（二）/3.jpg [width] [height] "title text 'alt text'" %}

## 1.4、条件与循环
条件v-if 循环v-for
使用v-for的时候可能会出现一些问题 比如:key问题

待补充

## 1.5、处理用户输入
这里就到了交互部分，对用户操作进行监听v-on，没有触碰DOM，
所有的DOM操作都由Vue来处理，编写的代码只需要关注逻辑层面即可

v-model指令，一般绑定表单输入

## 1.6、组件化应用构建
按照dom树理解吧

## 1.7、与自定义元素的关系
待续
