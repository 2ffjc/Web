---
title: Windows 虚拟内存位置更改
published: 2026-07-28
tags: [Windows, 虚拟内存, C盘清理]
category: 科技
draft: true
slug: Windows-虚拟内存位置更改
---

# 更改方式

右击桌面上的“此电脑”—“属性”—“高级系统设置”—“高级”-性能-下的“设置”，修改虚拟内存


# 遇到win11虚拟内存（页面文件）转到D盘报错问题解决


有时候按照上述方法改完虚拟内存的位置后，每次开机、重启时后系统提示”由于启动计算机时出现了页面文件配置问题，windows在你的计算机上创建了一个临时页面文件。所有磁盘驱动器的总页面文件大小可能稍大于你所指定的大小。“

是因为微软的BDE这个功能，也就是bitlocker这个东西，这是什么?微软的磁盘加密，不知道为什么win10家庭版上面出厂时默认是开启的，开启了BDE之后，为了防止页面文件存放在非系统盘而可能未被加密导致用户信息泄露，默认禁止pagefile.sys更换到非系统盘，但设置的时候不给个提示。

当然也可以
**[关闭Bitlocker](/posts/关闭Bitlocker/#关闭bitlocker)**
，不过关闭它要对磁盘解密，这个解密的过程是十分漫长的。

如果你不在意pagefile.sys有泄露的风险，也可以在不关闭磁盘加密的情况下，将pagefle.sys更改到非系统盘，那么要如何操作呢?

win10下按win键+R，输入:regedit 打开注册表编辑器，找到

HKEY LOCAL MACHINE\SYSTEM Controlset001\ControlSession Manager\Memory Management

下面有两个键:

PagefileOnOsvolume和ExistingPageFiles

将PagefileOnOsvolume 的值由默认的1改为0，ExistingPageFiles里面的C:改为你要更换的盘符名。

然后重启就可以，重启后，C盘下的pagefile.sys已经没有用，可以删除了，开机也不会再提示那个令人讨厌的提示了。

































