# /etc/rc.d/rc.local配置

## 给文件赋予执行权限
chmod +x /etc/rc.d/rc.local

## 编辑文件
在文件的最后一行添加执行脚本路径：/home/runJar2.sh

## 给执行脚本赋予执行权限
chmod +x /home/runJar2.sh

## 编写开机自动执行脚本

```
#!/bin/bash

cd /opt/test
nohup java -jar WebSSH.jar &

```



