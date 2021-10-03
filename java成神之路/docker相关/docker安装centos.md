# docker安装centos

```
1,创建容器
docker run -d -p 5000:22 --name centos74 --privileged=true centos /usr/sbin/init
2，进入容器
docker exec -it centos74 /bin/bash
3，设置密码
passwd   ：weiwei9122
4，安装openssh
yum install passwd openssl openssh-server -y
5，修改ssh配置文件以下选项，去掉# 注释，将四个选项启用
vi /etc/ssh/sshd_config

port=22 #开启22端口
RSAAuthentication yes #启用 RSA 认证
PubkeyAuthentication yes #启用公钥私钥配对认证方式
AuthorizedKeysFile .ssh/authorized_keys #公钥文件路径（和上面生成的文件同）
PermitRootLogin yes #root能使用ssh登录

6，重启ssh服务，并设置开机启动
$ service sshd restart
$ chkconfig sshd on

7，退出容器
exit
8，达到目的
用ssh协议连接容器
root@localhost：5000   注意一点5000是本机的端口映射到容器的22端口

以后在本地有环境可以练习linux命令

```
# 遗留问题
在问题中学习是一种非常好的学习方式
1，容器能不能有自己的ip？
为什么要有自己的ip 和宿主机共享ip 不是很好吗？确实是的
2，下载文件
命令已经安装上了
3，将本地的容器保存
是可以的，退出容器。docker commit 【容器id】 【镜像名字】 
4，yum 安装软件怎样设置代理？不然一直被拦截
找到原因了，只要宿主机不打开代理，就可以用
5，能不能设置开机自动启动容器
可以设置 docker update --restart always/no 【容器名字】
6，centos修改主机名称
sysctl kernel.hostname=zzh
7，设置ssh登陆的欢迎页面
vim /etc/bashrc

```
c2="$(tput bold)$(tput setaf 2)"
echo "$c2  _     _            _                 ___ "
echo "$c2 | |   (_)          | |               / __)"
echo "$c2 | |  _ _  ____ ____| | _____ _____ _| |__ "
echo "$c2 | |_/ ) |/ ___) ___) || ___ (____ (_   __)"
echo "$c2 |  _ (| ( (__( (___| || ____/ ___ | | |   "
echo "$c2 |_| \_)_|\____)____)\_)_____)_____| |_|   "
echo "$(tput sgr0)"
```

8，怎样把自己的镜像上传至网上？

```

1、登录到docker hub （docker hub注册网址：https://hub.docker.com）
  #docker login
  Username: rhl  （docker hub上注册的账号）
  Password：    （docker hub上所注册账号的密码） 

2、使用docker tag 命令为本地镜像添加新的标签
  #docker tag image1:latest（本地镜像）rhl/image1:latest（新添加的镜像）

3、使用docker push 命令将新添加的镜像上传到docker hub
  #docker push rhl/image1:latest
  实际上在使用的过程中，push一个镜像有点复杂（很大），网速什么的都有限制

  

4、完成

```

