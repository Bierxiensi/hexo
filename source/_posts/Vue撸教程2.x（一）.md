---
title: Vue撸教程2.x（一）
date: 2019-10-30 16:47:00
categories:
- [技术, review, Vue撸教程]
tags: [vue-cli, vue]
comments: true
photo: /img/vue/Vue撸教程2.x/Vue撸教程2.x（一）/1.jpg
index_img: /img/vue/Vue撸教程2.x/Vue撸教程2.x（一）/1.jpg
banner_img: /img/vue/Vue撸教程2.x/Vue撸教程2.x（一）/1.jpg
description: 学习反刍
author: zxy
avatar: /img/zxyaily/food.jpg
authorAbout: zxyaily
authordesc: i like ly
---
# 1、安装
## 1.1、兼容性与更新日志
兼容性这里涉及到ECMAScript发展历史等知识，javascript这块很大，对于前端也很重要，接下来应该单独跟进一个javascript系列博客
目前javascript这块的学习阶段还是集中在红宝书上，总之IE8以下的版本还是不支持的。vue的更新日志持续关注吧。

## 1.2、vue开发工具
一个是在html页面引入(制作原型或学习)
```
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
```
还一个就是vue-cli脚手架了 搭建过程有空还是写篇博客附上来
至于不同版本的vue就取决于构建环境和生产环境了

## 1.3、命令行工具（cli）
这是一个单独的小模块
配合之前的vue-cli脚手架博客理解

## 1.4、对不同构建版本的解释

### 1.4.1、术语
讲的比较清晰吧
>完整版：同时包含编译器和运行时的版本。
>编译器：用来将模板字符串编译成为 JavaScript 渲染函数的代码。
>运行时：用来创建 Vue 实例、渲染并处理虚拟 DOM 等的代码。基本上就是除去编译器的其它一切。

剩下的暂时没接触
### 1.4.2、运行时 + 编译器 vs. 只包含运行时
这个讲的也比较清晰 
当使用vue-loader或vueify的时候，*.vue文件内部的模板会在构建时预编译成JavaScript
这时候可以使用不包含编译器的vue版本即运行版本，应该是节省了服务器资源、提高了运行效率吧，毕竟不需判断执行编译模块了
webpack什么的具体配置也给了就不放了

例子也很清晰，看样子render函数就实现了挂载vue组件到DOM上的编译
<pre><code>
// 需要编译器
new Vue({
  template: '<div>{{ hi }}</div>'
})

// 不需要编译器
new Vue({
  render (h) {
    return h('div', this.hi)
  }
})
</code></pre>

### 1.4.3、开发环境 vs. 生产环境模式 、CSP 环境
需要研究一下 待续。。。
## 1.5、开发版本
同上
## 1.6、AMD模块加载器
同上
