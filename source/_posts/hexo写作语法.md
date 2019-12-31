---
title: hexo写作语法
date: 2019-11-05 17:23:03
categories:
- [技术, study, hexo]
tags: [hexo写作语法]
photos: /img/hexo/1.jpg
comments: true
description: 学习反刍
author: zxy
avatar: /img/zxyaily/food.jpg
authorAbout: zxyaily
authordesc: i like ly
---
# 1、标题
- # 一级标题
`# 一级标题`
- ## 二级标题
`## 二级标题`
- ### 三级标题
`### 三级标题`
- #### 四级标题
`#### 四级标题`
- ##### 五级标题
`##### 五级标题`
- ###### 六级标题
`###### 六级标题`

注意#与标题间有空格

# 2、字体与文本
## 2.1、字体
- 1\. <font face="黑体">我是黑体字</font>
`<font face="黑体">我是黑体字</font>`

- 2\. <font face="微软雅黑">我是微软雅黑</font>
`<font face="微软雅黑">我是微软雅黑</font>`

- 3\. <font face="STCAIYUN">我是华文彩云</font>
`<font face="STCAIYUN">我是华文彩云</font>`

- 4\. <font color=red>我是红色</font>
`<font color=red>我是红色</font>`

- 5\. <font color=#008000>我是绿色</font>
`<font color=#008000>我是绿色</font>`

- 6\. <font color=Blue>我是蓝色</font>
`<font color=Blue>我是蓝色</font>`

- 7\. <font size=5>我是尺寸</font>
`<font size=5>我是尺寸</font>`

- 8\. <small>小型字体</small>
`<small>小型字体</small>`

- 9\. <font face="黑体" color=green size=5>我是黑体，绿色，尺寸为5</font>
`<font face="黑体" color=green size=5>我是黑体，绿色，尺寸为5</font>`

## 2.2、文本
- 1\. *强调文本* _强调文本_  
`*强调文本* _强调文本_`

- 2\. **加粗文本** __加粗文本__ 
`**加粗文本** __加粗文本__ ` 

- 3\. ==标记文本==  
`==标记文本==` 

- 4\. ~~删除文本~~  
`~~删除文本~~` 

- 5\. 引用文本
>H~2~O是液体。2^10^运算结果是1024。
`>H~2~O is是液体。2^10^运算结果是1024。`

6\. 引用嵌套列表
> - 这是引用里嵌套的一个列表
> - 还可以有子列表
     - 子列表需要从 - 之后延后四个空格开始

    > - 这是引用里嵌套的一个列表
    > - 还可以有子列表
        - 子列表需要从 - 之后延后四个空格开始

- 7\. 缩进换行
&ensp; 半角的空格
`&ensp; 半角的空格`
&emsp; 全角的空格
`&emsp; 全角的空格`

- 8\. 公式
$$\Gamma(z) = \int_0^\infty t^{z-1}e^{-t}dt\,.$$
$ 数学公式 $
`$$
 \Gamma(z) = \int_0^\infty t^{z-1}e^{-t}dt\,.
 $$
`

# 3、图标
- 1\. 照相机 <i class="fa fa-camera"></i> 
`<i class="fa fa-camera"></i>`

- 2\. 电池 <i class="fa fa-battery-4"></i> 
`<i class="fa fa-battery-4"></i>`

网址https://fontawesome.com/

# 4、列表
- 列表内容
+ 列表内容
* 列表内容

<pre><code>- 列表内容
+ 列表内容
* 列表内容
注意：- + * 跟内容之间都要有一个空格
</code></pre>


## 4.1、无序列表
- 1
- 2
- 3

<pre><code>- 1
- 2
- 3
注意：- 跟内容之间有一个空格
</code></pre>

## 4.2、有序列表
1. 列表一
2. 列表二
3. 列表三

<pre><code>1. 列表一
2. 列表二
3. 列表三
注意：. 跟内容之间有一个空格
</code></pre>
 
# 5、表格
- 1\. 形式一

| 资产 | 负债 | 股东权益 | 
| ----- | ------ | ------ |
| 在建工程 | 贷款 | 股本 |

<pre><code>| 资产 | 负债 | 股东权益 | 
| ----- | ------ | ------ |
| 在建工程 | 贷款 | 股本 |
</code></pre>

- 2\. 形式二
html语言

HTML table表格、Excel table表格、Markdown table表格在线转换工具 https://tableconvert.com/?output=html

# 6、代码
`代码内容`



# 7、标签插件
1\. 引用 Twitter
{% blockquote @DevDocs https://twitter.com/devdocs/status/356095192085962752 %}
NEW: DevDocs now comes with syntax highlighting. http://devdocs.io
{% endblockquote %}

2\. 引用 网易云
{% iframe //music.163.com/outchain/player?type=0&id=2025535275&auto=1&height=90 [width] [height] %}

3\. 引用 gist
{% gist 199bc1a29687f7ae6da0180836b5354b find %}
{% gist e95044ca4535fc4c268c41458bf4cc32 listen1_myplaylist_2782ed18-652e-be76-614c-af33c7deb4e8.md %}  

详情见hexo文档https://hexo.io/zh-cn/docs/tag-plugins
