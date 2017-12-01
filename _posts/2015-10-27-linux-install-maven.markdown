---
layout:         post
title:          Linux下安装Maven
subtitle:       linux install maven
card-image:     https://ww1.sinaimg.cn/large/906cb9dbgw1f9ilpmreqhj21kw0zk151.jpg
date:           2015-10-26 19:00:00
tags:           code
post-card-type: article
---

## 简介

Apache Maven，是一个软件（特别是Java软件）项目管理及自动构建工具，由Apache软件基金会所提供。基于项目对象模型（POM）概念，Maven利用一个中央信息片断能管理一个项目的构建、报告和文档等步骤。曾是Jakarta项目的子项目，现为独立Apache项目。

## 准备

[Maven](http://maven.apache.org)（这里以最新的3.3版本为例。注意：如果使用3.3版本，那么你的JDK版本最低应为1.7，这些可以在官方网站中看到。）

## 开始

首先下载Maven3.3.3，你可以从官网直接下载，或在终端中使用命令下载，解压，然后移动到你想要安装的目录当中，例如我是移动到了/home/sunmoon/wnglmng/dev这个目录下：

```bash
sunmoon@sunmoon-io:~$ wget http://apache.fayea.com/maven/maven-3/3.3.3/binaries/apache-maven-3.3.3-bin.tar.gz
sunmoon@sunmoon-io:~$ tar vxf apache-maven-3.3.3-bin.tar.gz
sunmoon@sunmoon-io:~$ mv apache-maven-3.3.3 /home/sunmoon/wnglmng/dev
```

然后，用gedit打开/etc/profile文件：

```bash
sunmoon@sunmoon-io:~$ sudo gedit /etc/profile
```

在编辑器中末尾添加如下代码：

```
MAVEN_HOME=/home/sunmoon/wnglmng/dev/apache-maven-3.3.3
export MAVEN_HOME
export PATH=${PATH}:${MAVEN_HOME}/bin
```

然后ctrl+s保存，这个时候环境变量并未生效，在终端执行如下命令即可生效：

```bash
sunmoon@sunmoon-io:~$ source /etc/profile
```

检查是否生效，如果打印下面信息那么就是成功了：

```bash
sunmoon@sunmoon-io:~$ mvn -v
Apache Maven 3.3.3 (7994120775791599e205a5524ec3e0dfe41d4a06; 2015-04-22T19:57:37+08:00)
Maven home: /home/sunmoon/wnglmng/dev/apache-maven-3.3.3
Java version: 1.7.0_79, vendor: Oracle Corporation
Java home: /usr/lib/jvm/java-7-openjdk-i386/jre
Default locale: en_US, platform encoding: UTF-8
OS name: "linux", version: "3.13.0-66-generic", arch: "i386", family: "unix"
```

到这里我们就可简单修改一下Mavne的配置文件。找到apache-maven-3.3.3/conf/setting.xml文件，找到如下代码：

```xml
  <!-- localRepository
   | The path to the local repository maven will use to store artifacts.
   |
   | Default: ${user.home}/.m2/repository
  <localRepository>/path/to/local/repo</localRepository>
  -->
```

我们可以修改复制最后一行代码在注释的下面，并修改成你想要将Maven仓库存放的位置，如下：

```xml
  <!-- localRepository
   | The path to the local repository maven will use to store artifacts.
   |
   | Default: ${user.home}/.m2/repository
  <localRepository>/path/to/local/repo</localRepository>
  -->
  <localRepository>/home/sunmoon/wnglmng/dev/maven-repository</localRepository>
```

最后，在终端中敲并回车执：

```bash
sunmoon@sunmoon-io:~$ mvn help:system
```

这时候Maven就会从远程仓库开始下载一大堆依赖下来，可能会花费一段时间，你可以做些其他的。最后下载完成，你会发现/home/sunmoon/wnglmng/dev/maven-repository这个文件夹在你的磁盘上就出现了，这个就是Maven仓库。

这样，我们的Maven就按算完成了。
