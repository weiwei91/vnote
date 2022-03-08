# docker安装rabbitmq

docker run --name rabbitmq -d -p 15672:15672 -p 5672:5672 4b23cfb64730(镜像名字)

docker exec -i -t 0f1 bin/bash

rabbitmqctl add_user root Abc123++

rabbitmqctl set_permissions -p / root ".*" ".*" ".*"

rabbitmqctl set_user_tags root administrator

