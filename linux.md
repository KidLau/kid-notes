# 目录

1. [解决Windows和Linux双系统引导丢失](#1)
2. [搭建samba服务器](#2)

<h1 id="1">解决Windows和Linux双系统引导丢失</h1>
系统本来是Windows系统，然后再装Linux系统，安装完后开机时引导只有Linux，找不到Windows的引导入口。启动 Linux 系统，打开终端，执行命令

```shell
sudo update-grub
```	        

命令会搜索系统存在的引导，并把搜索到的引导打印到终端上，执行完重启电脑就可以看到丢失Windows的引导入口了。此方法在Ubuntu和Deepin已测试可用。

<h1 id="2">搭建samba服务器</h1>
安装samba

```shell
sudo apt-get install samba
```

修改配置文件，在最后写入

```
[share] # 访问名称
comment = share # 说明
path = /home/server/Public # 服务器文件夹路径
public = yes
writable = yes # 写权限
browseable = yes
guest ok = yes
```

重启samba

```shell
service smbd restart
```    

在文件管理器中访问，如服务器IP为192.168.0.1

```
\\192.168.0.1\share # windows
smb://192.168.0.1/share # linux
```
