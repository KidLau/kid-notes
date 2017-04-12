# 反向代理

打开nginx配置文件

```shell
vim /etc/nginx/sites-enabled/default
```

把文件根路由改成如下配置

```shell
location / {
  proxy_http_version 1.1;
  proxy_set_header X-Real-IP $remote_addr;
  proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
  proxy_set_header Host $http_host;
  proxy_set_header X-NginX-Proxy true;
  proxy_set_header Upgrade $http_upgrade;
  proxy_set_header Connection "upgrade";
  proxy_pass http://127.0.0.1:8001$request_uri;
  proxy_redirect off;
}
```

proxy_pass就是要代理的服务器地址，上面配置是对本地8001端口的服务器进行反向代理，配置完保存退出并重启nginx服务器。

```shell
sudo /etc/init.d/nginx restart
```

重启后反向代理就配置成功了。