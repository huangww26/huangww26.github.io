---
title: Vim默认打开标签页
category: 学习笔记
date: 2016-04-29 15:58:48
tags: Vim
---

默认情况下Vim会在新窗口打新文件，修改注册表可以让Vim默认在新标签页中打开新文件

1. 双击时打开新标签页
 `/HKEY_CLASSES_ROOT/Applications/gvim.exe/shell/edit/command`
 `/HKEY_CLASSES_ROOT/Applications/gvim.exe/shell/open/command`
 将上述两项的值改为&ldquo;d:\Program Files (x86)\Vim\vim74\gvim.exe&rdquo;-p \-\-remote-tab-silent&ldquo;%1&rdquo;
<!--more-->

2. 右键菜单打开新标签页
 新建`HKEY_CLASSES_ROOT/*/shell/Edit with Vim(&E)/command`
 将其默认值设为&ldquo;d:\Program Files (x86)\Vim\vim74\gvim.exe&rdquo;-p \-\-remote-tab-silent&ldquo;%1&rdquo;
