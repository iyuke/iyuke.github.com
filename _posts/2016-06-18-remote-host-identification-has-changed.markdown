---
layout:         post
title:          REMOTE HOST IDENTIFICATION HAS CHANGED
subtitle:   
card-image:     https://ww3.sinaimg.cn/large/906cb9dbgw1fb2xyzt1mij20wk0duwmv.jpg
date:           2016-6-18 23:35:00
tags:           code
post-card-type: image
---

```
$ ssh 45.127.97.64
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
SHA256:9lxVjf0Tk3qXvmW0UQ9E7cSFN0ITpVzH8RZhT1UAR1M.
Please contact your system administrator.
Add correct host key in /Users/WngLMng/.ssh/known_hosts to get rid of this message.
Offending RSA key in /Users/WngLMng/.ssh/known_hosts:12
RSA host key for 45.127.97.64 has changed and you have requested strict checking.
Host key verification failed.
```

删除 ~/.ssh/known_hosts 中的关于 Ip 为 45.127.97.64 的相关信息。

OK!
