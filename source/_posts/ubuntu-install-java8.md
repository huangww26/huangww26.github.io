---
title: Ubuntu下安装java8
category: 学习笔记
date: 2016-06-30 22:12:40
tags: [Ubuntu, java] 
---

### 1. 使用ppa安装
#### 添加ppa
```bash
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
```
<!--more-->

#### 安装oracle-java8-installer
```bash
sudo apt-get install oracle-java8-installer
```
安装过程会提示你容易oracle的服务条款，可以用下面命令默认同意条款
```bash
echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | sudo /usr/bin/debconf-set-selections
```

#### 设置环境变量
```bash
sudo apt-get install oracle-java8-set-default
```

### 2. 直接解压缩安装包
未完待续！
