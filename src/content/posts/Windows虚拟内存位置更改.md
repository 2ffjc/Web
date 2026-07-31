---
title: Windows 虚拟内存位置更改
published: 2026-07-29
tags: [Windows, 虚拟内存, C盘清理]
category: 科技
draft: false
slug: Windows-虚拟内存位置更改
---

# 建议更换场景

1. C盘空间严重不足
2. 电脑有多个盘并且其他盘满足是固态硬盘和空间足够
3. 并非只有一个系统盘，或者并非只有系统盘是固态硬盘

# 进入界面

右击桌面上的“此电脑”—“属性”—“高级系统设置”—“高级”-性能-下的“设置”，修改虚拟内存

<center class ='img'>
<img title="属性" src="https://s41.ax1x.com/2026/07/30/pmhNNzq.png" width="50%" alt="pmhNNzq.png" border="0" />属性
<img title="高级系统设置" src="https://s41.ax1x.com/2026/07/30/pmhNro4.png" width="90%" alt="pmhNro4.png" border="0" />高级系统设置
<img title="性能设置" src="https://s41.ax1x.com/2026/07/30/pmhNLlt.png" width="50%" alt="pmhNLlt.png" border="0" />性能设置
</center>




# 推荐容量设置

按照1GB=1024MB，通常内存设置**只能是4的倍数**，比如4MB、8MB、12MB、1GB等。

‌8G 及以下内存‌：建议初始值设为物理内存的 1.5 倍，最大值设为 3 倍，例如 8G 内存设初始 12GB、最大 24GB。

‌16G 内存‌：日常使用建议初始 16GB、最大 24GB；若常运行大型软件或游戏，最大值可提至 32GB。

‌32G 及以上内存‌：推荐保持开启系统自动管理，或者‌‌手动设初始 16GB、最大 32GB 即可‌。


# 更改方式

**注意：** 如果你的电脑只有一个系统盘，或者只有系统盘是固态硬盘，那么你不能将虚拟内存转到其他盘或者不建议更换虚拟内存的位置。请直接参考[推荐容量设置](#推荐容量设置)进行设置或放弃设置。

## 关闭C盘下的pagefile.sys

<center class ='img'>
<img title="自动管理所有驱动器的分页文件大小（A）" src="https://s41.ax1x.com/2026/07/30/pmhNO6P.png" width="45%" alt="pmhNO6P.png" border="0" />
关闭C盘下的pagefile.sys
</center>

## 更换到其他盘

1. 将`自动管理所有驱动器的分页文件大小（A）`取消勾选
2. 在上面的“驱动器[卷标]”位置选择你要`更换的盘符`，（如D\:、E\:等）点击下面的`自定义大小`，参考[推荐容量设置](#推荐容量设置)将GB换算成MB，例如 16GB = 16384MB填写上去。

<center class ='img'>
<img title="自定义其他盘虚拟内存大小" src="https://s41.ax1x.com/2026/07/31/pmhgNEn.png" width="45%" alt="pmhgNEn.png" border="0" />自定义其他盘虚拟内存大小
</center>

3. 改完退出的时候，每个窗口都一定记得点`确定`！！！否则不会生效

4. **这里一定要重启电脑**，重启后有可能会出现下面的系统提示，可以按照以下步骤继续操作

---

# 遇到Win10/11虚拟内存（页面文件）转到D盘报错问题解决


有时候按照上述方法改完虚拟内存的位置后，每次开机、重启时后系统提示”由于启动计算机时出现了页面文件配置问题，windows在你的计算机上创建了一个临时页面文件。所有磁盘驱动器的总页面文件大小可能稍大于你所指定的大小。“

是因为微软的BDE这个功能，也就是Bitlocker，微软的磁盘加密，很多Win10/11家庭版上面出厂时默认是开启的，开启了BDE之后，为了防止页面文件存放在非系统盘而可能未被加密导致用户信息泄露，默认禁止pagefile.sys更换到非系统盘，但设置的时候不给个提示。

如果你不在意pagefile.sys有泄露的风险，也可以在不关闭磁盘加密的情况下，将pagefle.sys更改到非系统盘，那么要如何操作呢?

当然也可以先[**关闭Bitlocker**](/posts/关闭Bitlocker/#关闭bitlocker) ，不过关闭它要对磁盘解密，这个解密的过程是十分漫长的。

1. Win10/11下按 Win键+R，输入`regedit`打开注册表编辑器，
<center class ='img'>
<img title="运行regedit" src="https://s41.ax1x.com/2026/07/31/pmhgj8f.png" width="70%" alt="pmhgj8f.png" border="0" />运行regedit
</center>

2. 找到：

```
HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\Session Manager\Memory Management
```

下面有两个键:

`PagefileOnOsvolume` 和 `ExistingPageFiles`

3. 将PagefileOnOsvolume 的值由默认的`1`改为`0`，ExistingPageFiles里面的`C:`改为你要更换的盘符名。


<center class ='img'>
<img title="设置界面" src="https://s41.ax1x.com/2026/07/31/pmh2F5q.png" alt="pmh2F5q.png"  width="100%" border="0" />设置界面
</center>


4. **这里一定要重启电脑**，重启后，C盘下的pagefile.sys已经没有用了或者消失了，开机也不会再提示那个令人讨厌的提示了。
 
---

我更改的最小值是10G，可以看到“已提交”总共的容量已经变成了31.4+10=41.4G了

<center class ='img'>
<img title="设置成功任务管理器界面" src="https://s41.ax1x.com/2026/07/31/pmhgTDH.png" width="90%" alt="pmhgTDH.png" border="0" />
设置成功任务管理器界面
</center>




































