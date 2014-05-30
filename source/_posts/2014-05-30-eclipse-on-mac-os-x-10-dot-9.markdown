---
layout: post
title: "eclipse on Mac OS X 10.9"
date: 2014-05-30 17:52:52 +0800
comments: true
categories: ['TOOL', 'mac']
---

MAC os upgrade 到 10.9 後, 因為沒有 jre, 所以 eclipse 開不起來
但下載 java 1.7 後, eclispe 居然說找不到 jre 1.6
<!--more-->
解法如下
```
vi /Library/Java/JavaVirtualMachines/jdk1.7.0_45.jdk/Contents/Info.plist
```
把
``` xml
<key>JVMCapabilities</key>
 <array>
  <string>CommandLine</string> <!--這行換掉-->
 </array>
```
換成
``` xml
<key>JVMCapabilities</key>
 <array>
  <!--換成以下五行-->
  <string>JNI</string>
  <string>BundledApp</string>
  <string>WebStart</string>
  <string>Applets</string>
  <string>CommandLine</string>
  <!--換成以上五行-->
 </array>
```
ref : http://stackoverflow.com/questions/19563766/eclipse-kepler-for-os-x-mavericks-request-java-se-6
<br/>