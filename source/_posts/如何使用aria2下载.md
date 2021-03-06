---
title: 如何使用aria2下载
date: 2017-01-19 11:20:15
tags: aria2
categories: IT相关

---

# 背景介绍

Aria2 是一个轻量的多协议多源命令行下载工具，支持 HTTP/HTTPS, FTP, SFTP, BitTorrent and Metalink 等协议下的下载。aria2 可通过内置的 JSON-RPC 及 XML-RPC interfaces 来进行操作，可通过 web 界面管理下载。

```bash
aria2 is a lightweight multi-protocol & multi-source 
command-line download utility. It supports HTTP/HTTPS, 
FTP, SFTP, BitTorrent and Metalink. aria2 can be 
manipulated via built-in JSON-RPC and XML-RPC 
interfaces.

```

Aria2 项目官网为 https://aria2.github.io/。aria2 早期是维护在 sourceforge 上的，但目前已转移至 GitHub：https://github.com/aria2/aria2，sourceforge 上提供的下载链接留在较老的版本上。

下载最新版的 aria2 请访问 aria2 GitHub 的 release 页面：https://github.com/aria2/aria2/releases。

# 命令行模式及配置文件

Aria2 有两种下载模式，一种是命令行下载模式，一种是 RPC Server 模式。建议使用 RPC Server 模式，同时配合 webui 来管理和使用。
更详细的配置选项等可以参考官方 Aria2 Manual。

## 配置文件
建议使用配置文件的方式管理配置（可以添加 -D 选项以后台运行）：

```bash
aria2c --conf-path=aria2.conf
```

## 命令行模式

我们可以在命令行中非常简单地调用 aria2 进行多种协议的下载操作。例如：
下载网络文件：

```bash
$ aria2c http://example.org/mylinux.iso
```

下载多个文件：

```bash
$ aria2c http://a/f.iso ftp://b/f.iso
```

下载时每个host使用两个连接：

```bash
$ aria2c -x2 http://a/f.iso
```

使用 BitTorrent 协议下载：

```bash
$ aria2c http://example.org/mylinux.torrent
```

使用磁力链接（Magnet URI）进行下载：

```bash
$ aria2c 'magnet:?xt=urn:btih:248D0A1CD08284299DE78D5C1ED359BB46717D8C'
```

Metalink：

```bash
$ aria2c http://example.org/mylinux.metalink
```

下载 text 文本文件中的链接：

```bash
$ aria2c -i uris.txt
```

# Windows 下 aria2 的使用方式
下载 aria2

访问 aria2 的 GitHub release 页面，下拉找到 latest release 的 Downloads 部分，下载 64 位或 32 位的 zip 包：

![] (http://zxjsdp1.qiniudn.com/aria2_github_latest_release.png)

## 配置 aria2

将 zip 包内的文件解压至本地目录，如 C:\Apps\aria2\，并在此目录下新建 4 个纯文本文件：

```bash
aria2.log         （日志，空文件就行）
aria2.session     （下载历史，空文件就行）
aria2.conf        （配置文件）
HideRunAria2.vbs  （隐藏cmd窗口运行用到的）
```

1. aria2.log
此文件为 aria2 运行的日志文件。
2. aria2.session
此文件用于记录和读取下载历史，保证在断电和重启时下载任务不会丢失。如果有时aria2不能启动，可以尝试清空此文件中的内容。
3. aria2.conf
此文件为 aria2 的配置文件。

配置文件中，需要根据当前存放 aria2 的目录的路径，修改若干选项：

```bash
# 下载文件保存路径
dir=D:\Downloads\aria2\

# 日志文件，如果不需要日志，这一行可去掉，如果需要，路径D:\Program Files\aria2\改为你安装aria2的路径
log=C:\Apps\aria2\aria2.log

# 这两个是记录和读取下载历史用的，断电和重启时保证下载任务不会丢失
# 如果有时aria2不能启动，清空这里面的内容就行了，路径D:\Program Files\aria2\改为你安装aria2的路径
input-file=C:\Apps\aria2\aria2.session
save-session=C:\Apps\aria2\aria2.session
```
若没有定制需要，其他选项可使用如下实例配置：

```bash
dir=D:\Downloads\aria2\
log=C:\Apps\aria2\aria2.log
input-file=C:\Apps\aria2\aria2.session
save-session=C:\Apps\aria2\aria2.session

save-session-interval=60
force-save=true
log-level=error

# see --split option
max-concurrent-downloads=5
continue=true
max-overall-download-limit=0
max-overall-upload-limit=50K
max-upload-limit=20

# Http/FTP options
connect-timeout=120
lowest-speed-limit=10K
max-connection-per-server=10
max-file-not-found=2
min-split-size=1M
split=5
check-certificate=false
http-no-cache=true

# FTP Specific Options

# BT/PT Setting
bt-enable-lpd=true
#bt-max-peers=55
follow-torrent=true
enable-dht6=false
bt-seed-unverified
rpc-save-upload-metadata=true
bt-hash-check-seed
bt-remove-unselected-file
bt-request-peer-speed-limit=100K
seed-ratio=0.0

# Metalink Specific Options

# RPC Options
enable-rpc=true
pause=false
rpc-allow-origin-all=true
rpc-listen-all=true
rpc-save-upload-metadata=true
rpc-secure=false

# Advanced Options
daemon=true
disable-ipv6=true
enable-mmap=true
file-allocation=falloc
max-download-result=120
#no-file-allocation-limit=32M
force-sequential=true
parameterized-uri=true
```

若需要指定其他选项，例如 `rpc-user` 及 `rpc-passwd` 等，可参考其他的配置文件，例如：[使用Aria2下载百度网盘和115的资源。](https://blog.icehoney.me/posts/2015-01-31-Aria2-download)

4.HideRunAria2.vbs

此 vbs 脚本用于无 cmd 窗口运行 aria2c。可点击此文件直接后台启动 aria2 并加载配置，无需每次输入 
`aria2 --conf-path=aria2.conf`。

使用文本编辑器打开此文件，编辑内容如下：

`CreateObject("WScript.Shell").Run "C:\Apps\aria2\aria2c.exe --conf-path=aria2.conf",0`

其中，`C:\Apps\aria2\aria2c.exe` 应替换为你的 `aria2c.exe` 绝对路径。

若需要开机启动，可将 `HideRunAria2.vbs` 的快捷方式放置于：`C:\Users\用户名\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup`。

## 使用 webui 下载管理界面管理下载的内容
我们可以使用 webui-aria2 来通过 RPC 方式管理下载内容。 [webui-aria2](https://github.com/ziahamza/webui-aria2) 项目主页为：https://github.com/ziahamza/webui-aria2。

在 Windows 下有两种使用方式：

*  访问 http://ziahamza.github.io/webui-aria2/。若本地已成功运行 aria2，则可以直接使用。

* 访问 [webui-aria2 项目 GitHub 页面](http://ziahamza.github.io/webui-aria2/)，clone 至本地，使用浏览器打开 index.html。

## 如何使用 aria2 下载百度云链接

推荐使用 [BaiduExporter](https://github.com/acgotaku/BaiduExporter) ，可将百度网盘的下载地址导出到 aria2/aria2-rpc，支持 YAAW。BaiduExporter 支持：

* Chrome（[BaiduExporter for Chrome](https://chrome.google.com/webstore/detail/baiduexporter/mjaenbjdjmgolhoafkohbhhbaiedbkno)）
* Firefox（[BaiduExporter@Addons page](https://addons.mozilla.org/zh-CN/firefox/addon/baiduexporter), [BaiduExporter.xpi 文件](https://raw.githubusercontent.com/acgotaku/BaiduExporter/master/firefox/BaiduExporter.xpi)）
* Safari（[BaiduExporter forSafari](https://raw.githubusercontent.com/acgotaku/BaiduExporter/master/safari/BaiduExporter.safariextz)）

## 下载迅雷离线等内容

可以尝试在 [Greasy Fork](https://greasyfork.org/) 及 [Gist](https://gist.github.com/) 等处寻找其他 yaaw 下载的脚本。例如：[ThunderLixianExporter](https://greasyfork.org/zh-CN/scripts/5376-thunderlixianexporter) 等。

# Mac OS X 下 aria2 的使用方式

## 使用 Aria2GUI

在 Mac OS X 下，有一个非常不错的 Aria2 用户界面项目 [Aria2GUI](https://github.com/yangshun1029/aria2gui)，GitHub 链接为：https://github.com/yangshun1029/aria2gui。Aria2GUI 自身集成了 aria2，在下载 dmg 文件并安装后，即可使用，无需进行其他繁琐的配置。并且支持多线程。

Aria2GUI 的最新 release 版本请到 GitHub 的 release 页面下载：https://github.com/yangshun1029/aria2gui/releases。
![](http://zxjsdp1.qiniudn.com/Aria2GUI_screenshot.png)

## YAAW-for-Chrome 插件

使用 [YAAW-for-Chrome](https://github.com/acgotaku/YAAW-for-Chrome) 插件，可以接管 Chrome 浏览器的下载到 Aria2GUI。YAAW-for-Chrome 的 GitHub 链接为：https://github.com/acgotaku/YAAW-for-Chrome，Chrome store 的安装链接为：https://chrome.google.com/webstore/detail/yaaw-for-chrome/dennnbdlpgjgbcjfgaohdahloollfgoc。

## 导出百度网盘的资源

在 Mac OS X 下，下载百度云上的资源体验较差，没有类似 Windows 上百度云管家类似的原生客户端，使用浏览器下载速度非常慢。因此可以安装 [BaiduExporter](https://github.com/acgotaku/BaiduExporter)，在百度云的下载页面上，将下载链接导出到 Aria2GUI 中下载，将能够得到接近带宽极限的满速体验。
