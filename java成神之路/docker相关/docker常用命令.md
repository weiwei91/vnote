# docker常用命令

# 镜像相关
```

docker rmi 【id】  删除镜像
docker commit 【容器id】 【镜像名字】  将本地的容器提交为镜像

```

# 容器相关
```

docker run --name yourappname -e POSTGRES\_PASSWORD=mysecretpassword -e POSTGRES\_USER=xxx -d -p xxxx:5432 postgres
docker rm [id/name]
docker exec [id] /bin/bash
dokcer ps      查看当前运行的容器
docker pa -a   查看所有容器包括停止的
docker start   启动之前停止的容器 
docker stop $(docker ps -a -q)  停止所有运行的容器
docker update --restart always/no 【容器名字】   设置容器开机自启动

```

