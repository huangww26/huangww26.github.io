---
title: 普通用户用Vim打开root权限的文件
date: 2016-04-18 10:12:21
category: 学习笔记
tags: Vim
---

## 问题描述
在Linux上以普通用户用Vim打开一个root权限文件，当需要保存更改时会提示
```
E45: 'readonly' option is set (add ! to override)
```
<!--more-->
## 解决方案
```
:w !sudo tee %
```

## 关于```tee```命令
用维基百科上的一幅图来解释吧：
{% asset_img Tee.svg  %}
