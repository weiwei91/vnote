# docker安装redis
```
docker run --name first-mysql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 -d mysql

```
慢日志在容器中的位置
/var/lib/mysql/bed3d31c9c03-slow.log


注意挂载的文件路径

docker run --restart=always --privileged=true  \
-v /opt/mysql/data/:/var/lib/mysql \
-v /opt/mysql/logs/:/var/log/mysql \
-v /opt/mysql/conf/:/etc/mysql \
-v /opt/mysql/my.cnf:/etc/mysql/my.cnf  \
-p 3306:3306 --name mysql \
-e MYSQL_ROOT_PASSWORD=123456 -d mysql




docker run -itd --name mysql -v /Users/weiwei/dev/docker-volumes/mysql-data:/var/lib/mysql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=Abc123++ mysql:5.7