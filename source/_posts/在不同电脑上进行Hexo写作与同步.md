---
title: 在不同电脑上进行Hexo写作与同步
date: 2017-01-17 21:44:40
tags: Hexo
categories: Hexo

---

如果你有多台电脑，而且每台电脑你都有可能会写博客。那么这个时候就需要对Hexo进行版本控制了。
版本控制的主要目的是方便在不同的电脑维护Hexo及写作。这里利用github的分支来保存hexo框架的相关文件(hexo配置、md、主题等文件)到github page仓库。
这里假设已经在github上建好page仓库，也就是”yourname.github.io”名字的仓库，以及在自己电脑上已经搭建好git、hexo、nodejs环境

## 新建Hexo分支
page仓库的master分支用来存放网站文件的，这是GitHub Page的要求，所以只好新建分支来保存Hexo原始文件，在下图的输入框输入分支名并按回车即完成分支创建。

![alt text](https://leroyli.github.io/2016/11/07/hexo-more-PC/branch1.png)

## 设置默认分支
因为我们写博客更多的是更新这个分支，网站文件所在的master分支则由hexo d命令发布文章的时候进行推送，所以我们将hexo分支>设置为默认分支，这样我们在新的电脑环境下git clone该仓库时，自动切到hexo`分支。按下图进行操作。

![alt text](https://leroyli.github.io/2016/11/07/hexo-more-PC/branch2.png)

## 站点配置hexo deploy参数

``` bash
deploy:
  type: git
  repo: https://github.com/pingnz/pingnz.github.io.git
  branch: master
  
```

然后使用部署命令hexo g -d就会自动渲染Markdown文件生成静态文件并部署到yourname.github.io仓库的master分支上，这时再访问http://yourname.github.io 就可以看到博客页面了。
此时博客页面是部署保存了，但hexo配置、md、主题等文件还没有保存，在heox目录下使用以下命令将文件推送到hexo分支上

``` bash
git remote add origin https://github.com/pingnz/pingnz.github.io.git
git add .
git commit -m "提交描述" #如果主题是英文，这里就是 git commit 
-m “change description”
git push origin hexo_blog

```
下面来说说不同环境下的操作

## 已有环境
如果在电脑上已经写过博客，那么可以在已有的工作目录下同步之前写的博客。
在你的仓库目录下右键’git bash shell’，起来bash命令行，然后

```
git pull

```
这样你的状态就更新了，之后就是 hexo命令写文章啦。。。
写完hexo g -d部署好后，使用

``` bash
git add .
git commit -m "提交描述" #如果主题是英文，这里就是 git commit 
-m “change description”
git push origin hexo_blog

```
推送上去.

## 新环境

到了新的电脑上时，我们需要将项目先下载到本地，然后再进行hexo初始化。

```bash
git clone https://github.com/pingnz/pingnz.github.io.git
cd yourname.github.io
npm install hexo
npm install
npm install hexo-deployer-git –save

```
之后开始写博客，写好部署好之后，别忘记 git add , ….git push origin hexo…推上去

``` bash
git add .
git commit -m "提交描述" #如果主题是英文，这里就是 git commit 
-m “change description”
git push origin hexo_blog

```

