---
title: Vue撸教程2.x（三）
date: 2019-11-04 15:39:52
categories:
- [技术, review, Vue撸教程]
tags: [vue-cli, vue]
photos: /img/vue/Vue撸教程2.x/Vue撸教程2.x（三）/1.jpg
comments: true
description: 学习反刍
author: zxy
avatar: /img/zxyaily/food.jpg
authorAbout: zxyaily
authordesc: i like ly
---
# 1、Vue实例
## 1.1、创建一个 Vue 实例
每个Vue应用都是通过用Vue函数创建一个新的Vue实例开始的，即
<pre>
<code>
var vm = new Vue({
  // 选项
})
</code>
</pre>
其中vm即为vue的实例，除了el这样根实例特有的选项外，其余组件均可被复用

## 1.2、数据与方法
Vue 实例被创建时，将 data 对象中的所有的属性加入到 Vue 的响应式系统中，
属性的值发生改变时，视图将会产生“响应”，即匹配更新为新的值。
这就是数据的双向绑定
<pre>
<code>
// 数据对象
var data = { a: 1 }

// 该对象被加入到一个 Vue 实例中
var vm = new Vue({
  data: data
})

// 获得这个实例上的属性
// 返回源数据中对应的字段
vm.a == data.a // => true
</code>
</pre>
>data 中的属性才是响应式的

使用 Object.freeze()，这会阻止修改现有的属性
<pre>
<code>
var obj = {
  foo: 'bar'
}

Object.freeze(obj)

new Vue({
  el: '#app',
  data: obj
})
</code>
</pre>
实例属性与方法，它们都有前缀 $，以便与自定义的属性区分
<pre>
<code>
var data = { a: 1 }
var vm = new Vue({
  el: '#example',
  data: data
})

vm.$data === data // => true
vm.$el === document.getElementById('example') // => true

// $watch 是一个实例方法
vm.$watch('a', function (newValue, oldValue) {
  // 这个回调将在 `vm.a` 改变后调用
})
</code>
</pre>

## 1.3、实例生命周期钩子
这个贯穿整个vue始终

## 1.4、生命周期图示
{% img [class names] /img/vue/Vue撸教程2.x/Vue撸教程2.x（三）/lifecycle.png [width] [height] "title text 'alt text'" %}
