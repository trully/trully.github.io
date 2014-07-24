---
layout: post
title: "Linux 指令雜記"
date: 2014-07-24 14:49:04 +0800
comments: true
categories: ['LINUX', 'cmd', 'mac']
---

#### 1. 更新 /etc/hosts, 想要立即生效, 執行
```
source /etc/hosts
```
<br/>

#### 2. 在 mac os 刪除無回應的程式 ex:Coccinellida
```
ps -A | grep Coccinellida | awk '{print $1}' | xargs kill -9
```
<!--more--><br/>

#### 3. awk 的 sample
```
cat log.log | awk 'BEGIN{FS=":"}; {print $2}' > log2.log
```
<br/>

#### 4. 用 ps 查看 process 的幾個方法
4.1 pgrep -f CloudboxConsumer.php (僅列出 pid)<br/>
![](https://dl-web.dropbox.com/get/Public/pic/Screenshot%202014-07-24%2015.02.06.png?_subject_uid=33912440&w=AACMCOlJ1dNRulEhI7N8k4yliJcoH_Q00Up1pvBb1gzfLA)

4.2 ps aux | grep CloudboxConsumer.php (可以查看佔用的 memory)<br/>
![](https://dl-web.dropbox.com/get/Public/pic/Screenshot%202014-07-24%2015.02.23.png?_subject_uid=33912440&w=AAAyRlheBYkjpPAdR8d8Ml03t8DTBhSxqe6i2lXPQEhwGQ)
VSZ : 該 process 使用掉的虛擬記憶體量 (Kbytes) (值: 51240, 93568 的部份)<br/>
RSS : 該 process 佔用的固定的記憶體量 (Kbytes) (值: 448, 9120 的部份)

4.3 ps -ef | grep CloudboxConsumer.php<br/>
![](https://dl-web.dropbox.com/get/Public/pic/Screenshot%202014-07-24%2015.02.41.png?_subject_uid=33912440&w=AADTTBC4z8GoMCnSR8Wi1kV9JbSe89TeLdlxogg0TveNWA)
<br/>
