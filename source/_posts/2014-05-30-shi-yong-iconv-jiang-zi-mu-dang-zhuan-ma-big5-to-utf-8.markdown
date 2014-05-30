---
layout: post
title: "使用 iconv 將字幕檔轉碼 (Big5 to UTF-8)"
date: 2014-05-30 17:33:18 +0800
comments: true
categories: ['TOOL', 'cmd']
---

環境 : MAC OS X 10.9.3


```
# -f 來源編碼 big5
# -t 目的編碼 utf-8
iconv -f big5 -t utf-8 Non-Stop.srt > Non-Stop.src
```

ref : http://blog.lyhdev.com/2012/12/mac-os-x-srt-big5-to-utf-8-iconv.html
<br/>