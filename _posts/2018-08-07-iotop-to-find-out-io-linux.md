---
layout: post
title: "每天学习一个命令：iotop 查看 Linux 下每个进程 IO 占用"
tagline: ""
description: ""
category: 学习笔记
tags: [io, iotop, top, linux, htop, ]
last_updated:
---

[iotop](http://guichaz.free.fr/iotop/) 是一个用来监控磁盘 I/O 的类似 top 的工具，Linux 下 IO 统计工具，比如 iostat， nmon 等只能统计到每个设备的读写情况，如果想要知道哪一个进程占用比较高的 IO 就要使用 iotop。 iotop 使用 Python 语言编写，要求 Python >= 2.5，Linux Kernel >= 2.6.20.

使用这个命令最主要的一个原因就是快速找到 IO 占用比较高的程序，以便进行排查。

## 安装

    sudo apt install iotop
    sudo yum install iotop

## 快捷键

- 交互式快捷键，`a` 用来切换累积使用量和 IO 读写速率。
- 左右箭头用来改变排序，默认按照 IO 排序，可以切换为读或者写排序等等。
- `r` 改变排序顺序
- `o` 只显示有 IO 输出的进程
- `q` 退出

## reference

- <http://guichaz.free.fr/iotop/>
