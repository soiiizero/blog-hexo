---
title: Linux软件包管理
date: 2024-04-13 22:54:35
top_img: /img/cover3.jpg
cover: /img/cover3.jpg
tags:
  - OS
  - Ubuntu
  - Linux
  - Software
categories: 
  - OS
---

> 本人有兴趣折腾Ubuntu的主要原因就是界面戳我，以及刷到那种命令行窗口显示Linux发行版的很有逼格的图案。后来知道这个软件叫Neofetch，或者screenfetch也可以。
## 1. 安装软件过程

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

## 2. 软件究竟是如何安装的

> 众所周知一般人用win都是打开浏览器去官网下载软件到本地，然后吭哧吭哧安装一通。Linux系有别于win，使用包管理工具来高效统一地管理软件包的安装升级卸载等一列操作。

### 2.1 概述

用户使用包管理工具通过软件源地址，访问软件源存储库下载并安装指定软件。

### 2.2 包管理工具

* 派系：Debian系的包格式是.deb，常用工具是apt；Red Hat系的包格式是.rpm，常用工具是yum或dnf

### 2.3 软件源地址

* 软件源地址存放在/etc/apt/sources.list中

* 文件内容：当前系统所有软件源地址。deb开头的行指的是软件包地址，deb-src指的是源代码地址

* 默认是官方软件源地址，可以自行添加第三方软件源地址。在Ubuntu中常用的有PPA。


### 2.4 软件存储库

* 软件在pool目录下，分为四种软件属性目录。
* 每个软件的目录下有.dsc元数据文件，.tar.gz源代码压缩包，.deb可执行的二进制文件
* apt首先下载.dsc，其中包含了指导编译和构建软件包的指令；接着下载源代码文件；根据.dsc中的指令，apt对源文件进行编译和构建，生成.deb文件，安装到系统中。



## 3. apt的使用

### 3.1 基本命令

```powershell
# 安装
sudo apt install 
# 移除 remove
# 根据存储库更新本地的索引 update
# 升级可升级的软件包 upgrade
# 列出包 list
# 显示软件包细节 show
```

### 3.2 apt和apt-get

* 在apt之前，包管理工具有apt-get，apt-cache，apt-config。由于常用的命令分散在这三个命令中，apt的引入就是整合了这三个命令的常见选项。目前推荐用apt。
* apt可以取代大部分之前的命令，但是不是全部，且有自己独有的命令比如list。































