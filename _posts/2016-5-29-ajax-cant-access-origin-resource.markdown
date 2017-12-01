---
layout:     	post
title:      	Ajax 跨域访问
subtitle:   	ajax access origin resource
card-image: 	
date:       	2016-05-29 21:00:00
tags:       	code
post-card-type: article
---

##问题现象

当出现跨域访问的时候， ajax 通常会报类似如下错误：

>
XMLHttpRequest cannot load http://localhost:8000/simple/api/users/me/login. Response to preflight request doesn't pass access control check: No 'Access-Control-Allow-Origin' header is present on the requested resource. Origin 'http://localhost:8080' is therefore not allowed access.

## 解决办法

### Tomcat设置允许跨域访问

这里描述以Tomcat为Web服务器情况下的解决办法，在JavaWeb项目中WEB-INF文件夹下的web.xml中加入如下配置即可。

```xml
<!-- cors filter -->
<filter>
	<filter-name>CorsFilter</filter-name>
	<filter-class>org.apache.catalina.filters.CorsFilter</filter-class>
</filter>
<filter-mapping>
	<filter-name>CorsFilter</filter-name>
	<url-pattern>/*</url-pattern>
</filter-mapping>
```

**注意:** org.apache.catalina.filters.CorsFilter 下面有好几个配置选项，上面没有配置时就采用系统的默认配置。在实际生产环境要根据需要进行配置来提高安全性。比如 cors.allowed.origins 配置入汛访问的源地址，默认为所有，即 * 。此外还有 fors.allowed.methods ，cors.allowed.headers 等等。具体配置细节可以参考 [https://tomcat.apache.org/tomcat-7.0-doc/config/filter.html](https://tomcat.apache.org/tomcat-7.0-doc/config/filter.html) 中 CORS Filter 章节。
