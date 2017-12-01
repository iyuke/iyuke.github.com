---
layout:         post
title:          Memcache简单介绍
subtitle:       
card-image:     https://ww4.sinaimg.cn/mw690/906cb9dbgw1fayofw6kcmj20jj099jsj.jpg
date:           2015-12-05 19:00:00
tags:           code
post-card-type: image
---

最近在学习有关缓存的一些知识，了解到有Memcache和Redis，那我先来介绍一下我目前了解到Memcache吧。有些人可能会在网上看到Memcache和Memcached这两个词，这两个个东西其实不必太在意，只不过Memcache是这个项目的名称，而Memcached是项目的服务端主程序名称。

##简介

[Memcached官网](http://memcached.org/)

Memcache是一个基于内存的，采用key-value的存储方式，能够存储任何二进制数据（比如视频，图片，文件等）的一个分布式缓存系统。通过Memcache，可以减少数据库的访问压力，简单的说，平时我们都是从数据库中读取数据，那么使用Memcache后，我们可以从Memcache中读取数据，从而减少了数据库访问这一过程，如果说Memcache中不存在我们想要的数据，那么再从数据库中读取数据，然后及时更新数据到Memcache中，那下次请求相同的数据就不必访问数据库了。

###特点

- 协议简单
- 基于libevent的事件处理
- 内置内存的存储方式
- memcached不相互通信的分布式

###存储方式

Memcache使用的存储方式是key-value的方式，每一个key都会对应一个value。Memcache可以看做一张大的hash表来存储数据的。每一个key都会被hash生成一个hash-key，用来存储，查找value数据的。

###LRU算法（最近未使用算法）

Memcached使用的算法是LRU。因为我们在开启Memcache服务的时候会分配指定的内存大小给它，当它存储的数据“爆表”后，当有新数据插入的时候，Memcache会删除最近未使用的数据，从而腾出空间给新来的数据。那它并不是实时监测哪些数据是要删除的，而是当有新数据出入，并且内存不够用的时候才会删除最近未使用的数据。

##安装

在Mac下安装则非常简单😂(让我哭一会，我想静静)，在终端中输入下面的命令即可，它会自动安装并下载它所依赖的libevent。

```bash
$ brew install memcached
```

brew是包的管理工具，没安装的可以参考[官网](http://brew.sh/)。

##命令

Memcached安装完后，可以在终端下尝试下面的一些命令。

```
$ memcached -d -m 512 -l 127.0.0.1 -p 11211
```

上面的命令，-d是启动Memcached服务，-m是分配512M的内存，-l则是本机ip，127.0.0.1，-p是端口，一般设置成11211。

更多命令如下：

```
-p 监听的端口
-l 连接的IP地址, 默认是本机
-d start 启动memcached服务
-d restart 重起memcached服务
-d stop|shutdown 关闭正在运行的memcached服务
-d install 安装memcached服务
-d uninstall 卸载memcached服务
-u 以的身份运行 (仅在以root运行的时候有效)
-m 最大内存使用，单位MB。默认64MB
-M 内存耗尽时返回错误，而不是删除项
-c 最大同时连接数，默认是1024
-f 块大小增长因子，默认是1.25-n 最小分配空间，key+value+flags默认是48
-h 显示帮助
```

##Memcached客户端

这里主要介绍一下Java的客户端，不好意思，我是搞Java的。

###Java客户端

- memcached client for java
- spymemcached
- xmemcached

###比较

- memcached client for java提出较早，使用广泛，稳定
- spymemcacheds比memcached client for java更高效
- xmemcached比spymemcached并发效果更好

以上三种可以根据自己的需要进行选择，如果不能很明确的进行判断的话，使用xmemcached也是一个不错的选择，在各个情况下都会表现的很好。

###github地址

- [memcached client for java](https://github.com/dustin/java-memcached-client)
- [spymemcached](https://github.com/killme2008/xmemcached)
- [xmemcached](https://github.com/gwhalin/Memcached-Java-Client)

###XMemcached的使用

客户端除了memcached client for java没有使用，其余两个都有使用过，最后选择了xmemecached，具体的代码我就不写了，我觉得这篇文章已经写的很详细了，详情可以可以查看[https://code.google.com/p/xmemcached/wiki/User_Guide_zh](https://code.google.com/p/xmemcached/wiki/User_Guide_zh)。
