---
title: Vue撸教程2.x（四）
date: 2019-11-05 16:38:35
categories:
- [技术, review, Vue撸教程]
tags: [vue-cli, vue]
photos: /img/vue/Vue撸教程2.x/Vue撸教程2.x（四）/1.jpg
comments: true
description: 学习反刍
author: zxy
avatar: /img/zxyaily/food.jpg
authorAbout: zxyaily
authordesc: i like ly
---
# 1、模板语法
## 1.1、插值

###文本
1. 使用“Mustache”语法 (双大括号) 
2. v-once 指令，能执行一次性地插值，当数据改变时，插值处的内容不会更新
```html
<code><span v-once>这个将不会改变:{{msg}}</span></code>
```
