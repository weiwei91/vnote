# jdk环境搭建
- 下载得到文件：jdk-8u171-linux-x64.tar.gz
- 解压缩文件：tar -zxvf jdk-8u171-linux-x64.tar.gz -C /usr/local/java
- 配置路径: vim /etc/profile

```
export JAVA_HOME=/usr/local/java/jdk1.8.0_171
export JRE_HOME=${JAVA_HOME}/jre
export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib
export PATH=${JAVA_HOME}/bin:$PATH

```

- 配置文件生效：source /etc/profile