---
title: hexo博客优化
date: 2019-04-14 16:51:06
tags: hexo博客搭建
categories: 一些教程  
toc: true
---

1. #### 侧边栏显示分类及标签

    添加下面代码到 sidebar.swig 文件中适当的位置即可，标签同理，使用 list_tags 函数即可  
    见 Hexo API：https://hexo.io/zh-cn/docs/helpers.html#list-categories  

    ```
    <div class="category-all-page">
        <div class="category-all">
            {{ list_categories({depth: 1}) }}
        </div>
    </div>
    ```

1. #### 添加fork me on github

    在 http://tholman.com/github-corners/ 或者 https://github.com/blog/273-github-ribbons 选择合适的样式复制代码到`themes/next/layout/_layout.swig文件，<div class="headband"></div>`下面  
    位置样式须改为这个:`img style="position:absolute; top:0; right:0; border:0;"`，否则会显示在中间  
    将GitHub网址替换为你自己的即可  

1. #### 添加文章目录

    - 配置  
    在博客主题目录下的 _config.yml 中如下配置：  

        ```
        toc:
        maxDepth: 3
        ```

        > maxDepth 表示目录深度为3，即最多生成三级目录  

    - 标记  
    在Markdown的front matter中添加`toc: true`  

1. #### 在多台电脑上提交和更新博客  

    - 对master克隆一个分支出来(命名hexo)，将hexo分支设为默认分支
    - 克隆hexo到本地，
    克隆分支命令 `git clone -b hexo https://github.com/deerstar/deerstar.github.io.git`  
    - 在分支目录下，执行git branch 命令查看当前所在分支，应为新建的分支hexo
    - 将本地博客的部署文件拷贝进 deerstar.github.io文件目录
