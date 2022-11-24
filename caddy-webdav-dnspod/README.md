自用 dnspod&webdav caddy 镜像


**⚠️以下内容未更新⚠️**

## 使用方法

配置文件见 [Caddyfile](./Caddyfile)
大部分配置不用修改，但是对外使用一定要修改密码，创建方式见下：


#### Docker 启动镜像
```
docker run -d --name caddy-webdav --restart unless-stopped -p 9080:80 -v /mnt/nfs-172_21_0_99:/caddyroot epurs/caddy:webdav
```

其中 `/mnt/nfs-172_21_0_99` 为宿主机挂载的路径。
`9080` 为启动容器暴露的端口，可以自定义修改任意，`/caddyroot` 为配置文件中 root 指定地址，这两个如果不理解不需要改动。

#### 修改密码
```
docker exec -it caddy-webdav caddy hash-password
```
输入两次密码后会生成 hash 字串，复制到配置文件中，替换默认密码。
```
docker cp caddy-webdav:/etc/caddy/Caddyfile ./Caddyfile
bdocker exec -it  caddy-webdav vi /etc/caddy/Caddyfile
```
密码配置格式：
```
    basicauth {
      # username  [hash mima]
        admin     JDJhJDE0JFIxRkowLjAudm04cHlDMUxtSTVtQk9HVXFudHZUbWQuc3A2UlNPWDdnVzlzVTFHaU1pSU95
    }
```
