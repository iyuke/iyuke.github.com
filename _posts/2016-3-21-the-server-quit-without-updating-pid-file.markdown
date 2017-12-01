---
layout:         post
title:          The server quit without updating PID file.
subtitle:   
card-image:     https://ww3.sinaimg.cn/mw690/906cb9dbgw1fayouoc4xij21kw0f5jxk.jpg
date:           2016-3-21 23:35:00
tags:           code
post-card-type: image
---


今天在命令行启动MySQL的时候, 报了一个错误, 无法启动. 如下.

```
.ERROR! The server quit without updating PID file (/usr/local/var/mysql/WngLMng-MacBook.local.pid).
```

![](https://ww3.sinaimg.cn/large/906cb9dbgw1f9ilmfmcqxj21hw0xogt3.jpg)

解决办法如下, 将MySQL下的对应的err文件删除即可.

```
$ rm -r /usr/local/var/mysql/WngLMng-MacBook.local.err
```

![](https://ww4.sinaimg.cn/large/906cb9dbgw1f9ilmv0cfej21ia0ykajp.jpg)

OK!
