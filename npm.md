# 配置下载源

## 临时配置

在安装时指定下载源：

```shell
npm install --registry=https://registry.npm.taobao.org --verbose
```

* -registry 用于指定下载源
* https://registry.npm.taobao.org 淘宝的下载源
* --verbose 打印出整个下载过程

## 永久配置

把下载源写到配置文件，以后用npm安装就会自动使用配置的源

```shell
echo registry = https://registry.npm.taobao.org >> ~/.npmrc
```