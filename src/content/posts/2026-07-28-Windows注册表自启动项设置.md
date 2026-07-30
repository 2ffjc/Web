---
title: Windows 注册表自启动项设置
published: 2026-07-28
tags: [Windows, 注册表, 自启动项]
category: 科技
draft: true
slug: Windows-注册表自启动项设置
---

第一篇博客教程，相信以后会越写越好

在 Windows 系统中，可以通过修改注册表来添加或删除开机自启动项，从而实现程序在系统启动时自动运行，这里提供一种添加启动项和两种删除启动项的方法。

# 注意事项

避免添加过多自启动项，以免影响系统启动速度。

不要添加来源不明的程序，以防恶意软件运行。

# 添加开机自启动项

打开注册表编辑器 按下 Win + R，输入 `regedit`，然后按回车键。

根据需要选择导航到以下路径之一： 

当前用户的自启动项： 
```txt
HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run
```

 所有用户的自启动项： 

- 修改 HKEY_LOCAL_MACHINE 时需要管理员权限

 ```txt
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Run
```

新建字符串值 在右侧窗口中右键单击，选择 新建 -> 字符串值。 将新建的值命名为程序名称（例如：MyApp）。

设置程序路径 双击新建的字符串值，在“数值数据”字段中输入程序的完整路径，例如： 
```txt
"C:\Program Files\MyApp\MyApp.exe" /background
```
> 如果需要后台运行，可在路径后添加 /background 参数。
> 确保输入的程序路径无误，否则无法正常启动。

点击“确定”保存更改，关闭注册表编辑器。

# 删除开机自启动项

## 方法一：注册表
依旧 Win + R 打开 `regedit`。

找到程序所在的注册表路径:

```txt
HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run
```

 所有用户的自启动项： 
 ```txt
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Run
```

删除键值 右键单击对应的键值（程序名称），选择“删除”。

确认操作 点击“是”确认删除。

## 方法二：任务管理器

按下 Ctrl + Shift + Esc，或右键单击任务栏上的空白区域，选择“任务管理器”。

在左侧找到“启动应用”选项卡。

在这里不仅可以删除对应的自启动项，还能选择启用状态。

点击“确定”确认删除。


