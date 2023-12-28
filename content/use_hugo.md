+++
title = 'Use_hugo'
date = 2023-12-28T10:04:28+08:00
draft = false

+++



1. 什么是Hugo？

   1. 由Go语言实现的静态网站生成器。简单、易用、高效、易扩展、快速部署

2. 为什么会使用Hugo？

   1. 在使用csdn以及其他博客网站时萌生了自己建立一个简易博客，通过[手把手教你从零开始免费的搭建个人博客，20 分钟上手](https://www.youtube.com/watch?v=dbtMf3kXUfw)的学习,成功搭建了一个简易版的博客，现在记录和分享成功经验

3. 使用Hugo以及github pages搭建博客（Mac）

   1. 安装homebrew、git、Node.js

      1. 安装homebrew

         ```shell
         /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
         ```

      2. 安装git
   
         ```shell
         brew install git
         ```
   
      3. [Node.js下载链接](https://nodejs.org/en/download/)
   
   2. 安装Hugo
   
      1. ```shell
         brew install hugo
         ```
   
   3. 使用Hugo搭建博客
   
      1. 在当前目录创建一个博客文件夹
   
         1. ```shell
            hugo new site your_filename
            ```
   
      2. 进入博客文件夹，并更换皮肤
   
         1. ```shell
            cd your_filename
            git init # 初始化git
            git submodule add https://github.com/lxndrblz/anatole.git themes/anatole # 将anatole仓库作为themes/anatole的字模块添加到当前的git仓库 
            echo theme = "anatole" >> config.toml # 主题改为anatole主题
            ```
   
      3. 创建第一个博客
   
         1. ```shell
            hugo new name.md # 一定要加.md,创建后会放在content目录
            vim content/name.md # 使用vim或其他md编辑工具编写你的第一个博客，并将draft = true 修改为 draft = false
            hugo server # 启动hugo server，并访问生成的一个url，即可看到你的博客
            
            ```
   
         2. 
   
      4. 
   
   
   
   





