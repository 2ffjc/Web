---
title: Ubuntu和Windows双系统共存安装通用方法
published: 2026-08-05
pinned: false
draft: true
description: Ubuntu修改引导器工具Boot-Repair
tags: [Ubuntu, Linux系统安装, 引导]
category: 科技
slug: Ubuntu和Windows双系统共存安装通用方法
---

> [!NOTE] NOTE
> 由于本人的经验不足，以及每个人的硬件配置不同，本教程不能保证所有情况都能成功安装，请根据实际情况进行调整。本教程还会在未来持续更新。
>
> 据个人经验，硬件为Intel的CPU和NVIDIA的独立显卡在安装及使用过程中因为其兼容性好，遇到问题的概率要比AMD的CPU更低。新版本的Ubuntu要比旧版本的兼容性更好。
>
> 有些电脑硬件和Ubuntu中默认的驱动不兼容，可能会存在安装过程中无线网卡或者笔记本自带键盘或者触控板无法使用，显示分辨率有问题等，严重会直接导致安装失败。

# 建议前置条件

1. 拥有一个16GB的U盘，用于存储Ubuntu镜像。
2. 本地磁盘空间足够，日常使用建议至少60GB，开发环境建议至少120GB。



. 安装前备份重要数据，避免安装过程中丢失数据。 


# 安装步骤

1. 在[清华源](https://mirrors.tuna.tsinghua.edu.cn/ubuntu-releases/)下载Ubuntu镜像

选择你想要安装的版本，如果只是日常使用