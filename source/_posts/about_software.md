---
title: Linux软件包管理
date: 2024-04-13 22:04:35
top_img: /img/OS.2(2).jpg
cover: /img/OS.2(2).jpg
tags:
  - OS
  - Ubuntu
  - Linux
  - Software
categories: 
  - OS
---

## 4. 安装一个软件

> 本人有兴趣折腾Ubuntu的主要原因就是界面戳我，以及刷到那种命令行窗口显示Linux发行版的很有逼格的图案。后来知道这个软件叫Neofetch，或者screenfetch也可以。

### 4.1 安装过程

* neofetch已经被官方收录，应当是可以以直接安装的，先尝试一下

  ```powershell
  sudo apt install neofetch
  ```

* 显示不可安装，说明本地软件包索引中还没有

* 更新索引和官方软件源同步

  ```powershell
  sudo apt update
  ```

* 再执行install命令，安装成功
* 启动neofetch

### 4.2 关于软件包

> 众所周知一般人用win都是打开浏览器去官网下载软件到本地，然后吭哧吭哧安装一通。Linux系有别于win，使用包管理工具来高效统一地管理软件包的安装升级卸载等一列操作。

* 包管理工具

  































