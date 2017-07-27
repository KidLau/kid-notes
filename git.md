# windows 使用 Git Bash 中文显示乱码（八进制编码）解决方法

在 Git Bash 里面执行命令

```shell
git config --global core.quotepath false
```

# 使用 http/https 时协议保存用户名和密码

* 缓存密码（默认15分钟）

```shell
git config --global credential.helper cache
```

* 自定义时间（timeout 单位是秒）

```shell
git config credential.helper 'cache --timeout=3600'
```

* 永久保存密码

```shell
git config --global credential.helper store
```
