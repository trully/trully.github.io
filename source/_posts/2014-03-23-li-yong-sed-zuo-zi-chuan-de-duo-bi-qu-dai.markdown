---
layout: post
title: "利用 sed 做字串的多筆取代"
date: 2014-03-23 17:16:57 +0800
comments: true
categories: ['LINUX', 'cmd']
---

argv=$(echo ${MOBILES} | **sed "s/ /@@/g”**)
```
MOBILES="0988222784 0911070610 0916928508 0910081920"
# 將號嗎間的空白改由 @@ 取代, 這樣多筆才能順利傳進 php 裡
#argv=${MOBILES/ /@@} 這樣寫只能取代一次
argv=$(echo ${MOBILES} | sed "s/ /@@/g”) 
```
<br/>