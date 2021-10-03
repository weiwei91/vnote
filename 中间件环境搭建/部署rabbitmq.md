# 部署rabbitmq


# 安装依赖
yum -y install make gcc gcc-c++ m4 ncurses-devel openssl-devel unixODBC-devel

wget http://erlang.org/download/otp_src_19.3.tar.gz

tar xzf otp_src_19.3.tar.gz

mkdir /usr/local/erlang

cd otp_src_19.3
./configure --prefix=/usr/local/erlang --without-javac
make && make install


vi /etc/profile
添加配置,查看版本
export PATH=$PATH:/usr/local/erlang/bin
source /etc/profile
erl -version

https://github.com/rabbitmq/rabbitmq-server/releases
下载rabbitmq的安装包和签名
wget -P /root "https://www.rabbitmq.com/releases/rabbitmq-server/v3.6.9/rabbitmq-server-3.6.9-1.el7.noarch.rpm"

sudo rpm --import https://www.rabbitmq.com/rabbitmq-release-signing-key.asc
sudo yum install rabbitmq-server-3.6.9-1.el7.noarch.rpm

sudo systemctl enable rabbitmq-server
sudo systemctl start rabbitmq-server
sudo rabbitmqctl delete_user guest
sudo rabbitmqctl add_user <用户名> <密码>
sudo rabbitmqctl set_user_tags <用户名> administrator
sudo rabbitmqctl set_permissions -p / <用户名> "." "." ".*"
sudo rabbitmq-plugins enable rabbitmq_management

账号rabbitmq
密码rabbitmq

# 参考网址
[手册](https://developer.qiniu.com/qvm/7123/manual-deployment-of-the-rabbitmq-centos-7)