---
title: Vue-Cli
date: 2019-11-06 11:14:24
categories:
- [技术, study, vue]
tags: [vue, vue-cli]
photos: /img/vue/Vue-Cli/1.jpg
description:  Vue-Cli创建Vue项目
comments: true
author: zxy
avatar: /img/zxyaily/food.jpg
authorAbout: zxyaily
authordesc: i like ly
---
# 1、Vue CLI 简介
Vue CLI 是一个基于 Vue.js 进行快速开发的标准工具，可以通过 @vue/cli 搭建交互式的项目脚手架，目前 @vue/cli 已经升级到 3.x 版本。 Vue CLI 分为独立的几个部分，我们需要对其进行一定的了解：
CLI：即 @vue/cli，它是一个需要全局安装的 npm 包，向我们提供了 vue 命令，我们可以通过使用它来满足我们快速创建 Vue 项目的需求。

CLI 服务：即 @vue/cli-service ，它是一个开发环境依赖，是一个局部安装在 @vue/cli 创建的项目中的 npm 包。它安装了一个名为 vue-cli-service 的命令，我们可以在创建项目后的 packsge.json 文件中找到对应的 script 命令。通过 npm 调用这些 script 命令可以达到配置服务器或打包的目的。

CLI 插件：它的作用是向我们创建的项目中提供可选功能的 npm 包，可以更好的帮助我们完成对项目的管理。同样，我们可以在 package.json 文件当中找到对应的 dependencies，这里标注了我们所安装的功能插件的信息。

熟练掌握 Vue CLI 的使用，可以帮助我们更轻松的完成 Vue 项目的创建和管理。

# 2、 Vue CLI 创建项目
>Node 版本要求
 Vue CLI 需要 Node.js 8.9 或更高版本 (推荐 8.11.0+)。

## 2、1 安装 Vue CLI
使用 @vue/cli 3.x 版本进行创建项目，需要先对 @vue/cli 进行安装，在命令行中输入如下命令：

    npm install -g @vue/cli
    # OR
    yarn global add @vue/cli

## 2.2 安装中
我用的是实验楼的虚拟环境，飞速安装中
{% img [class names] /img/vue/Vue-Cli/11.jpg [width] [height] "title text 'alt text'" %}
{% img [class names] /img/vue/Vue-Cli/12.jpg [width] [height] "title text 'alt text'" %}

## 2.3 安装结束，检查版本状况
可以看到安装完成了，这样就完成了 @vue/cli 的全局安装。可以用这个命令来检查其版本是否正确：
    
    vue --version

{% img [class names] /img/vue/Vue-Cli/13.jpg [width] [height] "title text 'alt text'" %}
安装没有问题

# 3、使用 @vue/cli 搭建 Vue 项目
vue create：运行以下命令即可创建一个新的项目，本次项目名为：zxyaily
{% img [class names] /img/vue/Vue-Cli/14.jpg [width] [height] "title text 'alt text'" %}
  
## 3.1、项目文件结构
{% img [class names] /img/vue/Vue-Cli/15.jpg [width] [height] "title text 'alt text'" %}

{% img [class names] /img/vue/Vue-Cli/16.jpg [width] [height] "title text 'alt text'" %}

- node_modules 这个目录是存放我们项目开发依赖的一些模块。这里面有很多很多内容，但我们不需要去了解他，只需要知道用途就好。
- public 这个目录提供的是一个应急手段。存放在这个文件夹中的静态资源不会经过 webpack，我们如果需要使用里面的静态资源就需要使用绝对路径来对其进行引用。
- src 这个目录是我们的源码所在。我们会在这里面存放我们几乎所有的代码文件，也是我们需要着重介绍的。
- static 这个目录是资源目录。里面包含我们的样式文件、字体文件、图片文件等等各种静态资源（但在本项目中并未使用，我们使用的是 src 目录下的 assets）。
- .xxxx 文件 这些文件是一些配置文件，包括语法配置，git 配置，还有我们引入的一些插件配置等。这些文件我们都不需要去了解，只需要知道他们是配置文件即可。
- package.json 这个文件是项目配置文件，我们在前面就用到过，前面所引入的插件的配置信息都在里面，还有一些与项目有关的配置也在其中。
- README.md 这个文件是项目的说明文档，使用 markdown 格式进行编写。
- src 目录是我们整个 Vue 项目中最为重要的一个目录文件，其中包含了我们大部分的代码：
    - api 这个目录是用于新建接口模块并使用 axios 实例。
    - assets 这个目录便是模块资源目录，与 static 不同的是，他会被 webpack 所处理，而 static 文件则是直接使用即可。
    - components 这个目录是模块组件目录，里面存放着我们所创建的各个组件，在本次项目中将这些组件分为两组：common 公共组件和 page 页面组件。
    - router 这个目录是路由配置目录，里面存放着我们去中心化之后的路由配置文件。
    - untils 这个目录是用于存放项目公用的 js 文件。
    - App.vue 这个文件是主应用程序组件，也是我们项目的根组件，所有组件都需要挂载到这个根组件上面。
    - main.js 这个文件是项目的核心入口文件，我们之前安装的插件也是在这个文件当中去进行引入和挂载，在这里面引入的插件我们就可以直接在整个项目中进行使用。

官方文档https://cli.vuejs.org/zh/
