---
title: "Docker创建运行容器命令"
date: 2021-10-23T21:27:54+08:00
draft: false
---

### 创建docker网络别名，用于网络连接

``` bash
docker network create docker_net
```

### 进入容器

``` bash 
docker exec -it container_name bash
```

### MySQL
``` shell
#拉取mysql的镜像
docker pull mysql
#创建容器
docker run --name mysql_dev -v /Users/george/Documents/docker/mysql/conf.d:/etc/mysql/conf.d -e MYSQL_ROOT_PASSWORD=123456 -p 3306:3306 --network docker_net --network-alias mysql_net -d mysql
```

### Redis
``` shell
 docker pull redis

 docker run -it --name redis_dev -p 6379:6379 --network docker_net --network-alias redis_net -d redis
```