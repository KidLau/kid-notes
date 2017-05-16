# 搭建 samba 服务器

安装 samba

```shell
sudo apt-get install samba
```

打开配置文件

```shell
sudo vim /etc/samba/smb.conf
```

在最后写入

```shell
[share] # 访问名称
comment = share # 说明
path = /home/server/Public # 服务器文件夹路径
public = yes
writable = yes # 写权限
browseable = yes
guest ok = yes
```

保存退出

```shell
:wq
```

重启 samba 服务

```shell
service smbd restart
```

如服务器 IP 为 192.168.0.1，使用文件管理器访问地址

```shell
\\192.168.0.1\share # windows
smb://192.168.0.1/share # linux
```