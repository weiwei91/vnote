# centos配置

## 安装openssh-server
yum list installed | grep openssh-server

![](_v_images/20210411153158013_1731420759.png)

##配置sshd_config

cd /etc/ssh/ 

![](_v_images/20210411153529968_1585279663.png)

![](_v_images/20210411153631888_2113171359.png)


## 重启服务

sudo service sshd start

## 查看sshd服务是否正常开启

ps -e | grep sshd


虚拟机ip  192.168.50.151   网关 192.168.50.255

## 注意
虚拟机的网络需要配置成桥接网络

![](_v_images/20210411174348817_986476627.png)
