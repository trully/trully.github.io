---
layout: post
title: "在 php 程式裡看 server 的 error log"
date: 2014-03-07 17:44:10 +0800
comments: true
categories: ['PROGRAMMING', 'php']
---

在程式最前面加這二行
``` php
ini_set('display_errors', 'On');
error_reporting(E_ERROR | E_WARNING | E_PARSE);
```
