---
layout: post
title: "用 tr 指令移除換行符號和取代字元"
date: 2014-08-13 16:48:51 +0800
comments: true
categories: ['LINUX', 'cmd']
---

ex : 把 /tmp/log 的斷行, 取代為空白, 寫入 /tmp/log2 裡
```
tr "\r\n" " " < /tmp/log > /tmp/log2
```
ref : http://www.arthurtoday.com/2013/11/ubuntu-tr-replace-string-new-line.html#.U9hIHo2SxyE
<br/>