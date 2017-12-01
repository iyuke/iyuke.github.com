---
layout:         post
title:          使用免费 SSL 证书 Let's Encrypt(certbot) 搭建 Https
subtitle:       build up https server with nginx and Let's Encrypt
card-image:     https://ws1.sinaimg.cn/mw690/906cb9dbgw1fb57wb1qh4j21ao0iwdik.jpg
date:           2016-12-25 19:00:00
tags:           code
post-card-type: image
---

Let's Encrypt 是很火的一个免费 SSL 证书发行项目，自动化发行证书，证书有 90 天的有效期。适合个人使用或者临时使用，不用再忍受自签发证书不受浏览器信赖的提示。

去年 VPS 侦探曾经说过 Let's Encrypt 的使用教程，但是 Let's Encrypt 已经发布了新的工具 certbot，虽然是新的工具，但是生成证书的使用方法和参数是基本一致的，证书续期更简单了。但是目前看 certbot 在一些老版本的Linux发行版上的兼容性还是有问题的，特别是在 CentOS 5 上因为 python 版本过低是无法用的，CentOS 6 上需要先安装 epel 才行，当然也有很多第三方的工具你也可以自己去尝试一下。

## 配置

如果是 CentOS 6、7，先执行

```
$ yum install epel-release
$ mkdir encrypt && cd encrypt
$ wget https://dl.eff.org/certbot-auto --no-check-certificate
$ chmod +x ./certbot-auto
$ ./certbot-auto -n
```

**注意** ```/certbot-auto -n``` 只是用来安装依赖包的，也可以跳过直接到下面的生成证书的步骤，国内 VPS 或服务器上使用的话建议先修改为国内的 pip 源。

### 单域名生成证书

```shell
$ ./certbot-auto certonly --email 79657392@qq.com --agree-tos --webroot -w /root/workspace/www.wnglmng.com -d wnglmng.com
```

### 多域名多目录生成多个证书(即一次生成多个域名的多个证书)

```shell
$ ./certbot-auto certonly --email 79657392@qq.com --agree-tos --webroot -w /root/workspace/www.wnglmng.com -d wnglmng.com -d blog.wnglmng.com
```

最后提示

```
IMPORTANT NOTES:
 - Congratulations! Your certificate and chain have been saved at
   /etc/letsencrypt/live/www.wnglmng.com/fullchain.pem. Your cert will
   expire on 2017-03-26. To obtain a new or tweaked version of this
   certificate in the future, simply run certbot-auto again. To
   non-interactively renew *all* of your certificates, run
   "certbot-auto renew"
 - If you like Certbot, please consider supporting our work by:

   Donating to ISRG / Let's Encrypt:   https://letsencrypt.org/donate
   Donating to EFF:                    https://eff.org/donate-le
```

就是生成成功。

生成的证书会存在 /etc/letsencrypt/live/www.wnglmng.com/ 目录下

我的项目是部署在 Nginx 下，简单配置如下

```
http {
    # HTTP server
    server {
        listen       80;
        server_name  wnglmng.com;

	    location / {
	        rewrite ^(.*) https://$server_name$1 permanent;
    	}
    }

    # HTTPS server
    server {
        listen       443 ssl;
        server_name  wnglmng.com;

        ssl_certificate      /etc/letsencrypt/live/www.wnglmng.com/fullchain.pem;
        ssl_certificate_key  /etc/letsencrypt/live/www.wnglmng.com/privkey.pem;

        ssl_session_cache    shared:SSL:1m;
        ssl_session_timeout  5m;

        ssl_ciphers  HIGH:!aNULL:!MD5;
        ssl_prefer_server_ciphers  on;

        location / {
            root   /root/workspace/www.wnglmng.com;
            index  index.html index.htm;
        }
    }
}
```

重新启动 Nginx ``` $ nginx -s reload ```

这就尴尬了，绿了！！！有木有！！！

![](https://ws2.sinaimg.cn/mw690/906cb9dbgw1fb58vs7lesj21kw0u31kx.jpg)

## 证书续期

cerrbot 的续期比原来的更加简单，因为证书只有90天，所以建议使用crontab进行自动续期。

crontab 里加上如下规则：

```
0 3 */5 * * /encrypt/certbot-auto renew --renew-hook "nginx -s reload"
```

这样每5天就会执行一次所有域名的续期操作。当然时间也可以自行进行调整，建议别太频繁，因为他们都有请求次数的限制，如果需要强制更新可以在前面命令上加上 --force-renew 参数。

---

转自 [免费SSL证书Let's Encrypt(certbot)安装使用教程](https://www.vpser.net/build/letsencrypt-certbot.html)
