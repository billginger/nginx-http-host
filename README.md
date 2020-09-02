# Nginx HTTP Host

a http host based on Nginx

## How to use

### Clone this project to your server

```
git clone https://github.com/billginger/nginx-http-host.git
```

### Configuration

Edit `server.conf` file:

```
/YOUR_PATH/nginx-http-host/conf/server.conf
```

### Use Docker

#### Pull Nginx image

```
docker pull nginx
```

#### Run Nginx

以挂载本地目录和配置文件的方式运行容器：

```
docker run --name nginx -d --network host -v /YOUR_PATH/nginx-http-host:/etc/nginx nginx
```

> 请注意：这里 nginx 容器使用了宿主网络，不需要映射端口，访问其它容器暴露的端口也会比较方便。

#### When the configuration file is modified

重启容器使新的配置文件生效（不建议）：

```
docker restart nginx
```

进入容器，先验证配置文件，再重载配置文件：

```
docker exec -it nginx bash
nginx -t
nginx -s reload
```

在容器外，先验证配置文件，再重载配置文件：

```
docker exec nginx bash -c "nginx -t"
docker exec nginx bash -c "nginx -s reload"
```
