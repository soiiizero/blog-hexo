---
title: 安装并使用WSL
date: 2024-04-12 22:51:35
top_img: /img/OS.2(1).jpg
cover: /img/OS.2(1).jpg
tags:
  - OS
  - WSL
  - Ubuntu
  - Linux
categories: 
  - OS
---

> 在上一篇文章中学习了Ubuntu和Linux的相关知识，那必须要在本机实践操作一下。

## 1. 关于在Windows中使用Linux的方法

### 1.1 双系统

鉴于本机还是以生活使用为主，以及对项目部署在Linux上没有太大需求，暂时不装双系统，切来切去太麻烦。但是留个坑，有空了补上。

### 1.2 虚拟机

本人使用的是VWware虚拟机，在此之前安装过了Centos7和openEuler22.03，主要是用来学习的。

此次安装Ubuntu也不打算用虚拟机，因为太慢了而且占空间多。

### 1.3 WSL

WSL是微软和Ubuntu母公司开发的一款用于在Windows系统上使用Linux发行版作为子系统的组件。win10以上可以使用，最新的是WSL2。



## 2. 使用WSL安装Linux

https://learn.microsoft.com/zh-cn/windows/wsl/install

* 查看可用的发行版

  ```powershell
  wsl -l -o
  ```

  本人选择的是Ubuntu-22.04

* 安装（管理员模式下）

  ```powershell
  wsl --install -d Ubuntu-22.04
  ```

* 查看已安装的发行版

  ```powershell
  wsl -l -v
  ```

  Version为2指的是WSL2



## 3. 启动Ubuntu

### 3.1 关于启动的目录

> 由于本人安装了Ubuntu和ArchLinux，发现这两个的启动目录不一样，结构和权限也不一样（对于Arch也留个坑，以后仔细研究）。
>

* Ubuntu：
  * 命令输入wsl后默认启动的是Ubuntu，可以看到进到的目录是/mnt/c/Users/(我的用户名,以下用soiiizero代替)。这个目录肯定很眼熟了，就是本地电脑默认的位置，用ls命令查看了也确实是和本地一样的内容。
  * 上级用cd ..命令查看，一直查看到/mnt的上级目录，是/，根目录。
  * 使用cd ~查看主目录，是/下面的root，里面就包含一个snap，snap里面是Ubuntu-desktop-installer。
* Arch：
  * 启动目录是主目录，是根目录下的home下的soiiisero，显示没有内容
  * root无权限访问

### 3.2 解决WSL2的小问题

启动wsl后会看到控制台输出“wsl: 检测到 localhost 代理配置，但未镜像到 WSL。NAT 模式下的 WSL 不支持 localhost 代理“，解决方法如下(只适用于wsl2)

* 创建WSL配置文件

  * 在本机C:/用户/soiiisero下创建.wslconfig，输入以下内容

    ```bash
    [experimental]
    autoMemoryReclaim=gradual  
    networkingMode=mirrored
    dnsTunneling=true
    firewall=true
    autoProxy=true
    ```

* 命令行执行wsl --shutdown

* 重启wsl

  
