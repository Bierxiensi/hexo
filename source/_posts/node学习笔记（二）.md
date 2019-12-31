---
title: node学习笔记（二）
date: 2019-11-06 19:14:33
categories:
- [技术, study, node学习笔记]
tags: [node]
photos: /img/node/node学习笔记/node学习笔记（一）/cover.jpg
description: Node.js 模块
comments: true
author: zxy
avatar: /img/zxyaily/food.jpg
authorAbout: zxyaily
authordesc: ilikely
---
# 写在前面
#### 本篇对 Node.js 的包和模块的概念进行讲述。
#### 知识点
- Node.js 包
- Node.js 模块

#### 简介
- <font color=red>为了让Node.js的文件可以相互调用</font>，Node.js提供了一个简单的模块系统。模块是Node.js 应用程序的基本组成部分。
- 文件和模块是一一对应的。换言之，<font color=red>一个 Node.js 文u件就是一个模块</font>，这个文件可能是JavaScript 代码、JSON 或者编译过的C/C++ 扩展。
- 而<font color=red>包用于管理多个模块</font><font color=blue>（即Node.js文件）</font>及其依赖关系，可以对多个模块进行封装。

# Node.js 包
包的根目录必须包含 package.json 文件，package.json 文件是 CommonJS 规范用于描述包的文件，符合 CommonJS 规范的 package.json 文件一般包含以下字段：

1. name：包名。包名是唯一的，只能包含小写字母、数字和下划线。
2. version：包版本号。
3. description：包说明。
4. keywords：关键字数组，用于搜索。
5. homepage：项目主页。
6. bugs：提交 bug 的地址。
7. license：许可证。
8. maintainers：维护者数组。
9. contributors：贡献者数组。
10. repositories：项目仓库托管地址数组。
11. dependencies：包依赖。
一个 package.json 示例：
<pre><code>{
        "name": "zxyaily",
        "description": "zxyaily test package.",
        "version": "0.1.0",
        "keywords": [
           "zxyaily",
           "nodejs"
        ],
        "maintainers": [{
           "name": "test",
           "email": "test@zxyaily.top"
        }],
        "contributors": [{
           "name": "test",
           "web": "https://www.zxyaily.top/"
        }],
        "bugs": {
           "mail": "test@zxyaily.top",
           "web": "http://www.zxyaily.top/"
        },
        "licenses": [{
           "type": "Apache License v2",
           "url": "http://www.apache.org/licenses/apache2.html"
        }],
        "repositories": [{
           "type": "git",
           "url": "http://github.com/bierxiensi/github.io.git"
        }],
        "dependencies": { 
           "webkit": "1.2",
           "ssl": { 
               "gnutls": ["1.0", "2.0"],
               "openssl": "0.9.8"
           }
        }
}
</code></pre>

了解更多可以在[package.json](https://docs.npmjs.com/files/package.json)的介绍文档 查看。

## 包操作
- package.json 文件可以自己手动编辑，还可以通过 npm init 命令进行生成。
- 上传自己的项目在 github 上的时候，通常是不会把 node_modules 这个文件夹传上去的（太大了），只需要有 package.json 就能通过 npm install 命令安装所有依赖。
1. 安装包：
    npm install 包名
    
通过命令 npm install 模块名字就可以安装。 模块名字全球唯一。
2. 更新包：
    npm update 包名
3. 删除(卸载)包：
    npm uninstall 包名

更多 npm 的操作可以访问 [npm 中文文档](https://www.npmjs.cn/)。

# Node.js 模块
## 概述
在JavaScript中，我们通常把JavaScript代码分为几个js文件，然后在浏览器中将这些js文件合并运行，但是在 Node.js
中，是通过以模块为单位来划分所有功能的，每一个模块为一个js文件，每一个模块中定义的全局变量和函数的作用范
围也被限定在这个模块之内，只有使用exports对象才能传递到外部使用。Node.js官方提供了很多模块，这些模块分
别实现了一种功能，如操作文件及文件系统的模块fs，构建http服务的模块http，处理文件路径的模块path等，当然我
们也可以自己编写模块。

## 核心模块（服务端模块）
核心模块定义在 Node.js 源代码的 lib/ 目录下。require() 总是会优先加载核心模块。 例如，require('http') 始终返回内置的 HTTP 模块，即使有同名文件。

在代码中使用

    var http = require("http");
    ...
    http.createServer(...);
   
在代码中请求它并把返回值赋给一个本地变量。把本地变量变成了一个拥有所有http模块所提供的公共方法的对象。 
## 创建模块
创建 main.js 文件，代码如下:

    var hello = require('./hello');
    hello.world();

注意：require 加载模块，以'/' 为前缀的模块是文件的绝对路径。'./' 为前缀的模块是相对于调用 require() 的文件的，上面的例子中 index.js 和 myModule.js 是在同一个目录下（project 目录）。当没有以 '/'、'./' 或 '../' 开头来表示文件时，这个模块必须是一个核心模块或加载自 node_modules 目录。如果给定的路径不存在，则 require() 会抛出一个 code 属性为 'MODULE_NOT_FOUND' 的 Error。

创建 hello.js 文件，代码如下：

    exports.world = function() {
      console.log('Hello World');
    }

{% img [class names] /img/node/node学习笔记/node学习笔记（二）/1.jpg [width] [height] "title text 'alt text'" %}

## Node.js 的 require 方法中的文件查找策略
由于 Node.js 中存在 4 类模块（原生模块和3种文件模块），尽管 require 方法极其简单，但是内部的加载却是十分复杂的，其加载优先级也各自不同。如下图所示：
