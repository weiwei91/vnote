# 官方文档
https://arthas.aliyun.com/doc/

# 定位目标服务进程id
注意用户的权限问题，如果权限不够可能查不到

* su root
* jps -lvm | grep 'iland'

# 运行arthas，并选择对应的进程id

* java -jar arthas-boot.jar
* 48

# 定位可疑的方法[精细到方法]
相关的命令可以在官网查看，这里只举出部分例子

* watch 观察入参及返回
* jad 反编译已加载的类
* monitor 监控
watch com.hikvision.iland.util.SendMsgUtils sendSmsMessage "{params,returnObj}"  -x 2 -n 1

