# 解决Windows和Linux双系统引导丢失

系统本来是Windows系统，然后再装Linux系统，安装完后开机时引导只有Linux，找不到Windows的引导入口。启动 Linux 系统，打开终端，执行命令

```shell
sudo update-grub
```

命令会搜索系统存在的引导，并把搜索到的引导打印到终端上，执行完重启电脑就可以看到丢失Windows的引导入口了。此方法在Ubuntu和Deepin已测试可用。

# 搭建Samba服务器

安装samba

```shell
sudo apt-get install samba
```

修改配置文件，在最后写入

```shell
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

```shell
\\192.168.0.1\share # windows
smb://192.168.0.1/share # linux
```

# 使终端支持256位色值

打开home目录下的配置文件.bashrc

```shell
vim ~/.bashrc
```

在文件最后加上

```shell
export TERM=xterm-256color
```

保存退出，重启终端就可以使终端支持256位色了。

# 配置Java环境变量

配置环境变量需要修改/etc/profile文件，假设jdk路径为/opt/jdk1.8.0_102，首先打开/etc/profile文件

```shell
vim /etc/profile
```

在文件最后加上

```shell
export JAVA_HOME=/opt/jdk1.8.0_102
export CLASSPATH=.:JAVA_HOME/lib/dt.jar:JAVA_HOME/lib/tools.jar
export PATH=JAVA_HOME/bin:PATH
```

# Shell变量

设置变量

```shell
VARIABLE_NAME=value
```

删除变量

```shell
unset VARIABLE_NAME
```

