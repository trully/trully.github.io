---
layout: post
title: "使用 gsh 對多台 server 下指令"
date: 2014-05-28 10:15:56 +0800
comments: true
categories: ['LINUX', 'cmd']
---

* 安裝 gst

```
wget http://outflux.net/unix/software/gsh/download/gsh-1.0.2.tar.gz
tar zxf gsh-1.0.2.tar.gz
cd gsh-1.0.2
perl Makefile.PL
make
make install
```
<!--more-->
* vi /etc/ghosts
```
# 第一個欄位: hostname or ip
# 第二個欄位之後: tag, 用以定義群組
vst-31 vst tag1
vst-32 vst tag1
vst-33 vst tag2
vst-34 vst tag2
vst-35 vst tag2
```
* 執行方式

```
# 含有 vst 的 server
gsh vst "df -h"
# 含有 tag2 的 server
gsh tag2 "df -h"
# 含有 vst 但排除 tag1 的 server
gsh vst-tag1 "tail -f error.log"
```

<br/>
ref : http://jamyy.us.to/blog/2014/05/6415.html
