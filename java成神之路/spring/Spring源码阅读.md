# Spring源码阅读

## 源码编译
### 安装gradle

下载gadle
https://services.gradle.org/distributions/

配置
sudo vi ~/.bash_profile

/Library/Internet Plug-Ins/JavaAppletPlugin.plugin/Contents/Home/bin/java


mac 需要配置环境
maven
gradle
jdk

编译的时候报错：
> Kotlin could not find the required JDK tools in the Java installation '/Library/Internet Plug-Ins/JavaAppletPlugin.plugin/Contents/Home' used by Gradle. Make sure Gradle is running on a JDK, not JRE.

mac安装jdk之后

/Library/Java/JavaVirtualMachines/jdk1.8.0_281.jdk/Contents/Home

/Users/wei/dev/apache-maven-3.8.1

如果基础命令失效
export PATH=/usr/bin:/usr/sbin:/bin:/sbin:/usr/X11R6/bin

/usr/local/apache-maven-3.8.1

/usr/local/gradle-5.6.3

配置完成

```
JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_291.jdk/Contents/Home
PATH=$JAVA_HOME/bin:$PATH:.
CLASSPATH=$JAVA_HOME/lib/tools.jar:$JAVA_HOME/lib/dt.jar:.
export JAVA_HOME
export PATH
export CLASSPATH

export M2_HOME=/usr/local/apache-maven-3.8.1
export PATH=$PATH:$M2_HOME/bin

GRADLE_HOME=/usr/local/gradle-5.6.3
export GRADLE_HOME
export PATH=$PATH:$GRADLE_HOME/bin


```

## 源码编译成功
```
wei@weideiMac spring-framework % ./gradlew :spring-oxm:compileTestJava
Starting a Gradle Daemon, 2 incompatible Daemons could not be reused, use --status for details

> Task :spring-beans:compileTestJava
注: 某些输入文件使用或覆盖了已过时的 API。
注: 有关详细信息, 请使用 -Xlint:deprecation 重新编译。
注: 某些输入文件使用了未经检查或不安全的操作。
注: 有关详细信息, 请使用 -Xlint:unchecked 重新编译。

> Task :spring-context:compileTestJava
注: 某些输入文件使用了未经检查或不安全的操作。
注: 有关详细信息, 请使用 -Xlint:unchecked 重新编译。

> Task :spring-oxm:genCastor
[ant:javac] : warning: 'includeantruntime' was not set, defaulting to build.sysclasspath=last; set to false for repeatable builds

> Task :spring-oxm:genJaxb
[ant:javac] : warning: 'includeantruntime' was not set, defaulting to build.sysclasspath=last; set to false for repeatable builds

BUILD SUCCESSFUL in 54s
59 actionable tasks: 57 executed, 2 up-to-date


```
