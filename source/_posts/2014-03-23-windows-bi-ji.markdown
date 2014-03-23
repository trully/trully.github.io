---
layout: post
title: "Windows 筆記"
date: 2014-03-23 17:06:02 +0800
comments: true
categories: ['WINDOWS']
---

###設定 xp 3 秒後關機###
```
Shutdown.exe -s -t 3 
```
<!--more--><br/>

###用 chrome 下載 mega 的檔案會暫存在###
```
C:\Documents and Settings\Administrator\Local Settings\Application Data\Google\Chrome\User Data\Default\File System
```
需要自行手動清除, 不然很佔空間

而 mac 會暫存在
```
/Users/trully/Library/Application Support/Google/Chrome/Default/File System/003/t/00
```
可以用 du 看一下, 不一定是 003
<br/>

