---
title: QQNT很卡可能有用的解决方案
published: 2026-09-14
pinned: false
description: 总感觉最近的QQ动效很卡，9.9.35-52892版本。尝试过添加启动参数，兼容模式，更改显卡设置，最终解决了
tags: [QQ, 优化]
category: 科技
slug: QQNT很卡可能有用的解决方案
---
# 问题

9.9.35-52892版本的QQ，在使用中感觉上下滑动消息的时候只有10帧左右，原来还不是这样子的

后面我探索了多种可能的方法，按照可能的概率大小整理出了解决的思路

# 解决方法

- **更改完以下设置，不要忘记重启QQ**

## 方法一：添加启动参数
我是通过这个方法解决的
1. 找到QQ的安装位置，一般默认安装在`C:\Program Files\Tencent\QQ`目录下

2. 打开QQ.exe的属性窗口（或者我建议在同级目录添加一个快捷方式：右击QQ.exe，选择`添加快捷方式`，然后进入快捷方式的属性窗口进行修改）

3. 在`目标(T)`框中空一格，添加`--disable-gpu`参数，点击`确定`
![添加启动参数](https://i.postimg.cc/fbjsvx0g/4.png)

原理：QQ NT 的 Electron 渲染管线 + NVIDIA 驱动/Windows GPU 合成兼容性有问题，导致卡顿。
直接绕开 NVIDIA 驱动、MPO、垂直同步、Electron GPU 合成这一整条容易出问题的链路，所以滑动和截图动画就稳了。

## 方法二：以兼容模式运行

同样来到属性窗口，点击`兼容性`选项卡，选择`以兼容模式运行这个程序`，选择Windows 7
![以兼容模式运行](https://i.postimg.cc/PxsB0N1d/5.png)
更改完别忘记点击`确定`

## 方法三：更改显卡设置
有独立显卡的，也可以试试

1. 在Windows设置中，将显示输出设置为`集成图形/节能`

![先添加桌面应用，选择QQ.exe的文件位置](https://i.postimg.cc/65RsBr57/2.png)

![然后选择QQ.exe的GPU首选项为节能](https://i.postimg.cc/vH9RGrH4/3.png)

2. 或者在NVIDIA控制面板中，将显示输出设置为`集成图形`
![记得点`应用（A）`](https://i.postimg.cc/yY9q7mY3/1.png)

后面看还会不会有什么新的问题和解决方案
