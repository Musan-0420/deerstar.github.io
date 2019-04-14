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

    ##### 思路：

    新建一个分支，将所有站点部署文件，放在分支上。在其它PC上写博客时，直接clone这个分支，并重新下载  hexo环境即可  
    还因为站点配置文件，配置deploy的分支是master，所以这样做的好处就是，静态博客文件默认放在master分支上。hexo的源文件（部署环境文件）可以都放在hexob分支上,两个分支互不干扰。

    ##### 步骤如下：  

    假设已经搭建好hexo博客，并部署过  
    执行以下步骤，若遇到报错，在文章末尾找对应原因
      1. 新建一个文件夹,命名hexob，将原站点目录下所有文件copy到这里。
      2. 初始化git工作空间，执行命令 `git init`  
      3. 新建本地分支命令 `git checkout -b hexob`
      4. 将根目录下所有文件提交`git add .`, `git commit -m 'ps'`, 再推送`git push origin hexob:hexob` ，通常多人协作时，需要pull三连 `git add && git commit && git pull`, 用于在本地处理冲突 
      5. 在GitHub上将hexob设为默认分支  
    执行完毕，可以在其他PC上使用了

    ##### 其他PC操作

    1. 克隆hexob分支到本地， 克隆分支命令 `git clone -b hexo https://github.com/deerstar/deerstar.github.io.git`  
    2. 在本地新拷贝的`deerstar.github.io`文件夹下通过Git bash依次执行下列指令：`npm install hexo、npm install、npm install hexo-deployer-git`（ps:不要hexo init）
    3. 在本地对博客进行修改（添加新博文、修改样式等等）后  
       1. 依次执行`git add . && git commit -m "..." && git push origin hexob`指令将改动推送到GitHub（此时当前分支应为hexob）
       2. 然后才执行`hexo clean && hexo g -d`发布网站到master分支上
       3. ps: 一般在source文件夹下，直接创建markdown来写

    ##### 报错记录

    - 报错`reinitialized existing git repository`  
         原因: theme目录和.deployer目录下已经有git文件，删除git文件，再执行`git init`即可  
    - 报错：`error:src refspec master does not match any`  
        原因：目录中没有文件，空目录是不能提交上去的  
        解决: 先创建一个readme，提交上去
        `touch README`  
        `git add README`  
        `git commit -m 'first commit'`  
        `git push origin hexob`  
    - 报错：git上传文件到仓库上提示：`origin does not to be a git repository`  
        解决：`git remote add origin https://github.com/deerstar/deerstar.github.io.git`，然后再推送
    - 删除远程分支命令`git push origin --delete hexo`
