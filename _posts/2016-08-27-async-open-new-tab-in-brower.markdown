---
layout:         post
title:          浏览器中异步打开新标签页
subtitle:       async open a new tab in brower
card-image:     
date:           2016-08-27 19:00:00
tags:           code
post-card-type: article
---

最近在做项目，需要异步获取服务器端返回的URL，然后在新的标签页中打开该URL（不要问我为什么不在当前页面加载，因为种种原因，用户不希望这个页面消失，只想在新标签页中处理工作，和我们的需求有很大关系）。然后发现各种问题，有的浏览器可以，但是有的浏览器被拦截，甚至有的浏览器既不被拦截又一点反应没有。

主要原因是，当 window.open 为用户触发事件内部或者加载时，不会被拦截，一旦将弹出代码移动到 ajax 或者一段异步代码内部，马上就出现被拦截的表现了，因为浏览器认为这是不安全的行为，默认都会被拦截。

在网上找了些资料，多多少少会有些问题，可能是我的姿势不对。

最后实现代码如下：

```javascript
// open a new blank tab
var createNewInterviewTab = window.open('about:blank', '_blank');
$.ajax({
    // ...
}).done(function(result) {
    if (result.status == 0) {
        var url = result.data.redirect;
        // async open a new tab
        setTimeout(function() {
            createNewInterviewTab.location.href = url;
        }, 100);
    } else {
        // close the blank tab
        createNewInterviewTab.close();
    }
});
```

到这里就结束了，就酱。

**参考**

* [window.open被浏览器拦截的解决方案](http://itindex.net/detail/52877-window.open-%E6%B5%8F%E8%A7%88%E5%99%A8)
