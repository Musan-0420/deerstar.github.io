---
title: hexo博客搭建流程
date: 2019-04-14 16:51:06
tags: hexo博客搭建
categories: 一些教程  
toc: true
---

> [hexo 官方使用文档](https://hexo.io/zh-cn/docs/)  
[next官方使用文档](http://theme-next.iissnan.com/getting-started.html)

1. #### 搭建环境

   1. ##### 安装git

   2. ##### 安装node.js

        以上两个都是exe安装

   3. ##### 安装hexo

       1. CMD命令 ``npm install -g hexo-cli``
       2. hexo 是node.js 的一个框架，npm是软件包管理系统

1. #### 搭建博客

   1. 新建文件夹，如：blog，该文件夹目录下即为站点根目录，所有文件都会在该文件夹下生成
   2. 在根目录下，打开cmd命令行  
    `hexo init`  //初始化博客  
    `npm install` // 安装补充文件  
    `hexo g`     //生产静态文件  
    `hexo s`     //启动服务器
   3. 博客雏形搭建完成
   4. 安装git部署插件
    `npm install hexo-deployer-git --save`
   5. 修改配置文件_config.yml，将网址`url: http://yoursite.com`修改`https:xxx.github.io`, xxx为你GitHub用户名
   6. 修改配置后，进行生成及部署  
    `hexo clean`  //清除缓存文件 (db.json) 和已生成的静态文件 (public)  
    `hexo g`  // 生成静态文件  
    `hexo d`  // 部署，两个命令可以合并为 `hexo g -d` 或 `hexo -g d`  
    或 `hexo clean && hexo g -d`  
    ps: 如果报错`TypeError: source.replace is not a function`, 就是语法错误  

1. #### 配置博客

   1. ##### 配置主题

      1. 下载next 主题到站点目录下  
        `git clone https://github.com/iissnan/hexo-theme-next themes/next`
      1. 修改站点配置文件  
        当克隆/下载完成后，打开站点配置文件，找到theme字段，并将其值更改为next`theme: next`  
      1. 主题设定  
        Scheme 的切换通过更改 主题配置文件，搜索 scheme 关键字。 你会看到有三行 scheme 的配置，将你需用启用的 scheme 前面注释 # 去除即可。  

        修改配置后，`hexo s -debug` 查看博客主题是否更改了  

        > yaml语法比较严格，修改配置文件后，一定要检查冒号后面的空格，否则会报错

1. #### 至此一个博客基本功能配置完成，博客优化见下篇文章

1. #### 绑定自定义域名

    1. 在阿里云购买一个域名，填写实名认证等等。然后解析域名
    2. 然后在github.io仓库的Settings的GitHub Pages项直接设置Custom domain为自己购买的域名,点击`save`, github会自动添加CNAME文件  

2. #### 问题记录

    Q：每次配置 custom domain 之后，再次 hexo deploy 之后，custom domain 会被重置失效  
    A: 解决方案:  
    在 hexo 生成的博客的 source 目录下新建一个 CNAME 文件，然后在这个文件中填入你的域名，这样就不会每次发布之后，gitpage 里的 custom domain 都被重置掉啦