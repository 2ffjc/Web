---
title: C盘清理指南
published: 2026-08-05
pinned: false
draft: true
description: C盘清理指南
tags: [Windows, C盘清理]
category: 科技
slug: C盘清理指南
---

# Boot-Repair 工具简介

%appdata%\..\Local\Microsoft\Edge\User Data\Default\Service Worker\CacheStorage
%LocalAppData%\..\Local\Google\Chrome\User Data\Default\Service Worker\CacheStorage

由于 Service workers 是网页编程缓存的一部分，在清理浏览器的缓存、历史记录的时候是不会触及这一部分的。如果要清理某一个网站的 CacheStorage，就需要在对应的网址中唤起  F12 开发者工具，在应用程序-储存-清除网站数据这个地方来清理。具体是哪个网站产生的数据，在上图中的 index.txt 中可以看到。


