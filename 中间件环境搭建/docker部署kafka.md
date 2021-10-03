# docker部署kafka

# 下载镜像

docker pull zookeeper
docker pull wurstmeister/kafka

# 启动zookeeper容器

docker run -d --name zookeeper -p 2181:2181 -v /usr/local/zookeeper/data:/data -v /usr/local/zookeeper/log:/datalog zookeeper

# 启动kafka容器

docker run -d --name kafka --publish 9092:9092 link zookeeper --env KAFKA_ZOOKEEPER_CONNECT=192.168.50.53:2181 --env KAFKA_ADVERTISED_HOST_NAME=192.168.50.53 --env KAFKA_ADVERTISED_PORT=9092  --env KAFKA_LOG_DIRS=/kafka/kafka-logs-1 -v /usr/local/kafka/logs:/kafka/kafka-logs-1  wurstmeister/kafka