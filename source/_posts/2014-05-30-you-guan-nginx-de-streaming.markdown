---
layout: post
title: "有關 Nginx 的 Streaming"
date: 2014-05-30 17:58:52 +0800
comments: true
categories: ['TECHNICAL', 'nginx']
---

隨手記一下~
<!--more-->
不管 flash or html5 player, 當頻寬很低時(10KB)都播幾秒就跳結束了<br/>
後來比對 vimeo 的 request header, 發覺他們的 response header 多了<br/>
**Connection: keep-alive**

於是試著把 /home/nginx/conf/nginx.conf 裡的
``` 
#keepalive_timeout        0; 原本是 0
keepalive_timeout        20;
```
重啟後, 就都播得完了~
<br/>