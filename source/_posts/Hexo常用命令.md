---
title: Hexo常用命令
date: 2017-01-16 12:28:31
tags: Hexo
categories: Hexo

---
我们希望对自己的博客进行修改或者需要发布新的文章时，可以按以下前三步进行。

```bash
$ hexo clean # 删除已经生成的静态页面
$ hexo generate
$ hexo deploy
hexo new "postName" #新建文章
hexo generate #生成静态页面至public目录
hexo server #开启预览访问端口（默认端口4000，'ctrl + c'关闭server）
hexo deploy #将.deploy目录部署到GitHub
hexo help  # 查看帮助
hexo version  #查看Hexo的版本

```

命令简写

```bash
hexo n == hexo new
hexo g == hexo generate
hexo s == hexo server
hexo d == hexo deploy

```
