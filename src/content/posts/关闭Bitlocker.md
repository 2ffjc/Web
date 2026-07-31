---
title: Windows 关闭 Bitlocker
published: 2026-07-30
pinned: false
draft: false
image: https://i.postimg.cc/zXHJ7WLN/image.png
description: Win7/8/10/11关闭Bitlocker的通用方法
tags: [Windows, Bitlocker]
category: 科技
slug: 关闭Bitlocker
---

# Bitlocker是什么？

## 开启Bitlocker的影响

BitLocker 是 Windows 系统自带的磁盘加密功能，很多Win10/11家庭版上面出厂时默认是开启的。
当系统检测到安全风险或硬件变更时，会要求输入‌48位恢复密钥‌才能解锁驱动器。

<center class ='img'>
<img title="BitLocker恢复界面" src="https://i.postimg.cc/W35zkvdL/1.png" width="80%" alt="BitLocker恢复界面" border="0" />BitLocker恢复界面
</center>

如果是用户自行设定的BitLocker密钥还好，主要用户自己都完全不知情，只有等到电脑出现问题，想恢复数据时，才发现有BitLocker加密。
微软官方无法直接提供或重置丢失的密钥，用户需通过预留的备份渠道自行查找。
本意是想保障用户和企业的数据安全。很多电脑默认开启了Bitlocker，导致用户在使用过程中遇到了很多问题，总之**普通用户关闭Bitlocker利大于弊**。

<center class ='img'>
<img title="自行设定时的备份恢复秘钥界面" src="https://i.postimg.cc/W1cNt358/2.png" width="80%" alt="自行设定时的备份恢复秘钥界面" border="0" />自行设定时的备份恢复秘钥界面
</center>

## 判断是否开启了Bitlocker

最简单的方法就是打开文件资源管理器，点击驱动器图标，查看是否有BitLocker图标:

<center class ='img'>
<img title="Win7驱动器上开启了Bitlocker的图标" src="https://i.postimg.cc/VkjzQ8BB/3-Win7.png" width="80%" alt="Win7驱动器上开启了Bitlocker的图标" border="0" />Win7驱动器上开启了Bitlocker的图标
<img title="Win10驱动器上开启了Bitlocker的图标" src="https://i.postimg.cc/JzbRVLcd/3-Win10.png" width="80%" alt="Win10驱动器上开启了Bitlocker的图标" border="0" />Win10驱动器上开启了Bitlocker的图标
<img title="Win11驱动器上开启了Bitlocker的图标" src="https://i.postimg.cc/52wfdVqP/3-Win11.png" width="30%" alt="Win11驱动器上开启了Bitlocker的图标" border="0" />Win11驱动器上开启了Bitlocker的图标
</center>

成功关闭BitLocker加密后，驱动器图标上的所有特殊标识（如锁、感叹号）会完全消失，恢复为普通磁盘图标。这是加密被正确移除的明确标志。如果你发现关闭后锁图标依然存在，通常意味着加密并未完全关闭，可能仍处于解密过程中或其他中间状态。

## 判断使用条件是否需要关闭Bitlocker

1. 关闭加密后，该驱动器上的所有数据将失去BitLocker保护。一旦设备丢失或被盗，他人可以像访问普通磁盘一样直接读取你的文件，存在隐私泄露风险。
请仅在可信的安全环境下（如家庭或办公室个人电脑）考虑关闭此功能。

2. 不管决定关闭与否，都务必提前备份恢复密钥：在进行任何可能影响系统TPM（可信平台模块）或硬件的操作之前，
例如重装操作系统、更换主板、升级BIOS/UEFI固件，甚至更换硬盘，
都必须确保你已经将BitLocker恢复密钥备份到了安全的地方（如Microsoft账户、U盘或打印成纸质文件）。
否则，上述操作极有可能触发系统安全机制，导致驱动器被永久锁死，若无密钥则数据无法挽回。

3. 在许多预装Win10/11的新设备上，尤其是使用微软账户登录时，“设备加密”（基于BitLocker）功能可能会被自动启用。
即使你手动关闭了它，在后续的重大系统更新或系统检测到硬件配置变化时，该功能仍有可能被再次自动触发。因此，建议在关闭后不定期检查磁盘状态。

## 解析Bitlocker图标状态

1. 黄色感叹号（三角感叹号）：这通常表示驱动器已启用BitLocker加密，但处于“等待激活”或“待机”状态。此时，系统已经为加密搭建好框架，
但尚未对数据进行实际加密，你仍可以正常读写文件。这种状态常出现在对新磁盘分区后，或符合条件的新电脑在首次使用微软账户登录时被自动触发。

2. 锁图标（未解锁）：当驱动器显示一个锁形图标时，意味着它已被BitLocker完全加密且当前处于锁定状态。你需要输入正确的密码或48位数字恢复密钥才能访问其中的数据。

3. 金色锁与银色锁的区别：根据微软官方的解释，这两种锁图标代表了不同的解锁状态。金色锁代表磁盘已被BitLocker加密，且正处于锁定状态；
银色锁则代表磁盘已被加密，属于暂时已经输入密码成功解锁的状态，文件可以直接访问，但加密保护仍然存在。

需要区分“控制面板图标消失”，这与驱动器图标是两回事。若在系统控制面板里找不到“BitLocker驱动器加密”的设置项，可能因为“BitLocker Drive Encryption Service”
系统服务被禁用。

比如**Win10/11家庭版就默认缺少此Windows功能**，从而导致在控制面板或者各种设置项里找不到“BitLocker驱动器加密”的设置项，或者因为安装的是移除了此功能的精简版Windows系统。
推荐从[家庭版升级到专业版](/posts/升级Windows家庭版到专业版/#升级步骤)（文章还没写好），以获得完整的BitLocker功能，从而方便关闭BitLocker加密。

---

# 关闭Bitlocker

> [!WARNING] WARNING
> 在关闭BitLocker之前，充分了解其影响并做好准备工作至关重要，这能有效避免数据丢失风险。必要时请提前备份重要数据，本人不承担任何数据丢失责任。
>
> 请注意，关闭加密实质是一个解密过程，**需要时间**且消耗系统资源（电脑变慢），期间可正常使用电脑。请确保电脑**连接电源并保持开机**，‌切勿强制关机或休眠‌直至解密完成。
>
> 解密具体时间由电脑配置和数据量决定，一般在10-30分钟之间。请根据实际情况合理安排时间。

如果你确认需要关闭BitLocker，可以根据自身习惯选择以下任一种方法：

## 方法一：通过Windows设置（Win10/11、推荐新手使用）

这是最直观的图形化操作方式。在Win10/11中，按下 Win + I 键，进入“设置”。

在Win10中，依次进入“更新和安全”->“设备加密”。

在Win11中，则进入“隐私和安全性”->“设备加密”。

也可以直接在设置顶部的搜索框中输入“管理BitLocker”快速进入。在打开的界面中，找到已加密的驱动器，点击“关闭BitLocker”即可。

## 方法二：通过文件资源管理器→控制面板（Win7/Win10/11）

打开“此电脑”，右键点击显示有锁或感叹号图标的驱动器。在弹出的菜单中（若为Win11，可能需要点击“显示更多选项”）。
选择“管理BitLocker”，这将直接跳转到BitLocker管理界面，可以在此选择关闭对应驱动器的加密。

<center class ='img'>
<img title="BitLocker管理界面" src="https://i.postimg.cc/HL5wG36X/5.png" width="80%" alt="BitLocker管理界面" border="0" />BitLocker管理界面
</center>

点击“关闭BitLocker”即可。在弹出的确认对话框中，输入密码或48位数字恢复密钥，即可关闭BitLocker加密。

## 方法三：控制面板（Win7/Win8/Win10）

> 如果控制面板找不到BitLocker设置：首先检查系统服务。按Win+R键，输入services.msc 并确定。
在服务列表中找到“BitLocker Drive Encryption Service”，右键选择“属性”，
将启动类型设置为“自动”，然后点击“启动”按钮。完成后再尝试以下方法。

按下 win + R，打开运行对话框。输入“control”并按回车，即可打开控制面板。在右上角将“查看方式”切换为“小图标”，找到“BitLocker驱动器加密”设置项。

<center class ='img'>
<img title="控制面板界面" src="https://i.postimg.cc/25vQpT0n/4.png" width="80%" alt="控制面板界面" border="0" />控制面板界面
</center>

点击同样会进入BitLocker管理界面，可以在此选择关闭对应驱动器的加密。

## 方法四：使用命令提示符（通用、适合高级用户）

可以输入 Win + R 键，输入“cmd”并按住Ctrl + Shift + 回车，以管理员身份运行命令提示符(CMD)。

检查驱动器是否已加密：
```bat title="CMD"
manage-bde -status
```
假设关闭的是C盘的BitLocker加密，命令如下：
```bat title="CMD"
manage-bde -unlock C: -RecoveryPassword <你的恢复密钥路径(C:\path\to\save\recoverykey.txt)>
```
按回车后，系统会开始解密。你可以随时输入以下命令来查看解密的详细进度。
```bat title="CMD"
manage-bde -status
```

## 方法五：使用 Windows PowerShell（Win10/11）

以管理员身份运行PowerShell。可以输入 Win + R 键，输入“powershell”并按住Ctrl + Shift + 回车，即可管理员身份运行PowerShell。

假设关闭的是C盘的BitLocker加密，命令如下：
```cmd title="PowerShell"
Disable-BitLocker -MountPoint "C:"
```
执行后，可以通过以下命令查看状态，当保护状态显示为“Off”时，表示加密已关闭
```cmd title="PowerShell"
Get-BitLockerVolume
```

<center>
<img title="BitLocker状态" src="https://i.postimg.cc/Zqd6pj3z/6.png" width="90%" alt="BitLocker状态" border="0" />BitLocker状态
</center>

## 延伸阅读与常见问题（FAQ）

**Q：** 为什么我什么都没做，电脑却自己显示了BitLocker图标？

**A：** 这通常是由系统自动策略触发的。常见场景包括：在新购买的电脑上首次使用微软账户登录；
Windows系统（特别是Win11 24H2及之后版本）更新后默认策略更激进；
系统检测到硬件配置发生重大变更（如主板、TPM状态变化）；
或者你对磁盘进行了分区操作，新分区进入了“等待激活”状态。

**Q：** 关闭BitLocker后，我的数据会丢失吗?

**A：** 不会丢失。关闭（解密）过程是安全的数据转换操作，你的原始文件会被完整保留，只是移除了外层的加密保护壳，数据本身不会被删除。

**Q：** 关闭加密后图标消失了，但感觉系统变卡了，正常吗？

**A：** 在解密过程进行中，系统需要读取整个加密盘的数据并进行解密运算，这会占用大量的磁盘IO和CPU资源，
导致系统响应变慢。这是正常现象。建议在电脑空闲时执行关闭操作，并耐心等待其完成，完成后系统性能就会恢复正常。

---

本期部分图片素材来自网络，非本人所有，仅用于学习和参考