---
title: 如何制作blog
date: 2018-07-27 10:37:55
tags: hexo
categories: JS
---

> 这是一篇关于如何用 github page 和 hexo 搭建博客的文章，因为技术太菜我打了一天才搭好，哭唧唧~(；д；) 今天就写出来告诉大家怎么搭建吧~ 

<!-- more -->

1. 首先你要有个 github 账号，没有账号就去注册一个，不知道怎么注册的话去百度或者 google 一下。
2. 然后你要新建一个仓库~ 仓库名称需要遵循一个规则，格式必须是：yourusername.github.io
3. 准备 hexo 环境：
    * 安装 node 环境(这一个步骤自己上网找怎么安装哈~ヾ(◍°∇°◍)ﾉﾞ)
    * 安装 Hexo 
    ```
        sudo npm install -g hexo-cl
    ```
    * 检查是否安装 
    ```
        hexo version
    ```
    * 手动创建一个放置 blog 的文件夹，创建完成后初始化 blog 目录
    ```
        hexo init <yourFloder>
    ```
    * hexo 的一些常用命令
    ```
        hexo new "postName" #新建文章
        hexo new page "pageName" #新建页面
        hexo generate #生成静态页面至public目录
        hexo server #开启预览访问端口（默认端口4000，'ctrl + c'关闭server）
        hexo deploy #将.deploy目录部署到GitHub
        hexo help #查看帮助
    ```
4. 配置你的 hexo
   在创建完成之后，你会在对应的文件夹里面看到一个文件名为"_config.yml"的文件，在里面可以修改你的配置。
   这边有一个对该文件的说明[ hexo 配置](https://hexo.io/zh-cn/docs/configuration.html)，参照文档进行修改~
5. 关联 hexo 与 github
   * 安装扩展
    ```
    npm install hexo-deployer-git --save
    ```
    * 修改"_config.yml"文件，配置如下：
    ```
    deploy:
        type: git
        repo: 刚刚步骤 '2' 中你创建的 github 地址
        branch: master
    ```
    * 执行下列代码之后你写的博客内容就会上传至 github 了
    ```
    hexo clean 
    hexo generate
    hexo deploy
    ```

