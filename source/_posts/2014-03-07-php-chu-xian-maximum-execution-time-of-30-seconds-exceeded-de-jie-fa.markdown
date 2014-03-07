---
layout: post
title: "php 出現 Maximum execution time of 30 seconds exceeded 的解法"
date: 2014-03-07 17:16:37 +0800
comments: true
categories: ['PROGRAMMING', 'php']
---
有以下二個方法
#### 1.修改 php.ini; 把 max_execution_time 的 30 改成自己想要的
#### 2.或在 code 裡宣告
``` php
set_time_limit(int $seconds) # If set to zero, no time limit is imposed
```
<br>

ref : http://registerboy.pixnet.net/blog/post/24489954-maximum-execution-time-of-30-seconds-exceeded-in%E7%9A%84%E8%A7%A3%E6%B1%BA%E8%BE%A6
