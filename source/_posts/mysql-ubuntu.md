---
title: 在Ubuntu下使用MySQL
date: 2016-03-29 15:48:58
category: 学习笔记
tags: [Ubuntu, MySql]
---

## 安装MySQL

**1. 检查系统有没有安装MySQL**
```bash
sudo netstat -tap | grep mysql
```
如果没有提示，则表明没有安装。若有如下提示，则表明已安装。
{% asset_img is_installed.png  %}
<!--more-->
**2. 安装MySQL**

```bash
sudo apt-get install mysql-server mysql-client 
```
安装过程中会提示设置root账户密码
{% asset_img mysql_installation_pwd.png %}

**3. 设置远程访问**
默认情况下MySQL不允许远程访问，只能在本机访问，通过以下方法可以远程登录
- 方法一
``` bash
mysql -uroot -p                                 # 登录mysql

use mysql;                                      # 使用mysql这个表
update user set host = '%' where user = 'root';
```
- 方法二
使任何主机使用账户username和密码pwd连接到mysql
``` bash
grant all privileges on *.* to 'username'@'%' identified by 'pwd' with grant option;
flush privileges;
```
使IP为ip的主机使用账户username和密码pwd连接到mysql
``` bash
grant all privileges on *.* to 'username'@'ip' identified by 'pwd' with grant option;
flush privileges;
```

## 卸载MySQL
**1. 删除MySQL**
``` bash
sudo apt-get autoremove mysql-server
sudo apt-get remove mysql-common
```
**2. 清理残余数据**
```bash
dpkg -l |grep ^rc|awk '{print $2}' |sudo xargs dpkg -P
```

## Ubuntu下使用mysql
``` bash
/etc/init.d/mysql stop      # 停止MySQL服务
/etc/init.d/mysql start     # 启动MySQL服务
/etc/init.d/mysql restrat   # 重启MySQL服务

mysql -uroot -p             # 以root用户登陆MySQL

show databases;             # 列出数据库
use <database_name>;        # 切换到数据库<database_name>
show tables;                # 显示当前数据库中的所有表
describe <table_name>;      # 显示表<table_name>的结构
```

## 中文乱码问题
查看MySQL的编码
``` bash
show variable like 'character%';
```
{%asset_img mysql_character_set.png%}

现在需要将chararcter_set_database和character_set_server的编码改为utf8。在/etc/mysql/my.cnf中的和[mysqld]加上character-set-server = utf8，然后重启MySQL。

