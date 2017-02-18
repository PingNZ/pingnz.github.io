---
title: Hexo 添加网易悦音乐歌曲和歌单
date: 2017-02-16 08:05:53
tags: Music
categories: 音乐

---

## 单首歌曲 ##

https已经不能插入网易云音乐，所以就只能借用 music.daoapp.io 来实现。

在网易云音乐的网页搜索歌曲然后拷贝歌曲ID，例如 天黑黑， id是287749，然后更改成如下， 如果不想让它自动播放，把autoplay设置成0
<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=330 height=86 src="https://music.daoapp.io/iframe?song=287749&qssl=1&qlrc=0&qnarrow=0&autoplay=0"></iframe>

## 歌单 ##
在网易云音乐的网页搜索歌单然后拷贝歌单ID，然后改成如下，注意把song改成playlist
<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=330 height=350 src="https://music.daoapp.io/iframe?playlist=378324005&qssl=1&qlrc=0&qnarrow=0&autoplay=0"></iframe>
