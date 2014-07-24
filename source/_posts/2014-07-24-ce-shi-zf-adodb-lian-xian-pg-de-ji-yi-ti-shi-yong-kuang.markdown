---
layout: post
title: "測試 zf, adodb 連線 pg 的記憶體使用情況"
date: 2014-07-24 15:16:59 +0800
comments: true
categories: ['TECHNICAL ', 'php', 'pgsql', 'zf']
---

<!--more-->
測試 100,000 筆資料

#### 1. 全部使用 adodb (create connection & query data)
記憶體目前用掉 1,870,736 ; 最多用掉 1,925,872 ; spend 8.2004950046539 sec.<br/>
記憶體目前用掉 1,871,400 ; 最多用掉 1,931,320 ; spend 73.63036608696 sec.

#### 2. 全部使用 adodb, 但 include zf 所需要的東西
記憶體目前用掉 7,469,520 ; 最多用掉 7,535,048 ; spend 8.332573890686 sec.<br/>
記憶體目前用掉 6,362,752 ; 最多用掉 6,431,688 ; spend 81.987900018692 sec.

#### 3. 使用 ado 建立 connection, 使用 zf query data
記憶體目前用掉 8,403,432 ; 最多用掉 8,689,672 ; spend 16.01734495163 sec.<br/>
記憶體目前用掉 8,404,256 ; 最多用掉 8,695,968 ; spend 153.99401402473 sec.

#### 4. 全部使用 zendframe work (create connection & query data)
記憶體目前用掉 84,069,368 ; 最多用掉  84,092,800 ; spend 10.299237966537 sec.<br/>
記憶體目前用掉 84,072,296 ; 最多用掉 161,899,552 ; spend 101.24145317078 sec. 101211

結果實作時, 連一天份的 multimedia media 都跑不完 memory 就爆了
```
PHP Fatal error:  Allowed memory size of 134217728 bytes exhausted (tried to allocate 32 bytes) in .../library/Zend/Cache/Core.php on line 312
```
看起來跟 cache 有關, 所以把用到的 model 的 cache 全關了再重跑一次, 就順利執行完了 (4013 筆)

看起來跑大量資料, 每次都要去調 model 不用 cache 也很麻煩,

結論 => 使用 adodb + 自己兜 sql, 不要使用任何 zendframe work 的東西, 這樣最省 memory
<br/>