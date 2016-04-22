---
title: Python用pip升级所有包
category: 学习笔记
date: 2016-04-22 13:09:10
tags: Python
---

* 列出安装的包
```bash
pip list
```

<!--more-->

* 列出可升级的包
```bash
pip list --outdate
```

* 列出已安装的最新版本的包
```bash
pip list --uptodate
```

* 升级一个包
```bash
pip install --upgrade <package-name>
```

pip当前内建命令并不支持升级所有包，但可以使用下面的命令来升级所有包
```bash
pip freeze --local | grep -v '^-e' | cut -d = -f 1 | xargs -n1 pip install -U
```
