---
layout: post
title: "add custom route to VPN on Mac OS X"
date: 2014-08-13 16:41:26 +0800
comments: true
categories: ['TOOL', 'mac']
---

用 mac 走 adsl 收公司的信時, 因為網路的問題常會連不到

用 vpn 回家的方式來解決<!--more-->

在播通 vpn 後, 加一個自訂的 route, 指定連到 mail server 時, 要走 ppp0

vi /etc/ppp/ip-up
```
#!/bin/sh
/sbin/route add -net [mail server ip] -interface ppp0
#/sbin/route add [mail server ip] 192.168.1.1
```
ref : https://www.nickebo.net/adding-a-custom-route-to-a-vpn-in-mac-os-x/
<br/>