---
layout: post
title: "php 匯出 csv 轉成 big5 編碼"
date: 2014-03-07 17:48:21 +0800
comments: true
categories: ['PROGRAMMING', 'php']
---

重點: fwrite($fh, iconv('UTF-8', 'BIG5//IGNORE', $line));
<!-- more -->
``` php
$line = "\"編號\",\"姓名\",\"性別\",\"出生年\",\"出生月日\",\"聯絡電話\",\"郵遞區號 縣市\",\"地址\",\"E-Mail\",\"白色沙瓦\",\"蘋果\",\"白桃\",\"葡萄沙瓦\",\"蜂蜜檸檬\",\"檸檬薑汁\",\"冬橘\",\"通路\",\"發票號碼\",\"填寫時間\"".chr(13);
# 寫檔
$fh = fopen($filePath, 'w+');
fwrite($fh, iconv('UTF-8', 'BIG5', $line));

$cnt = 1;
foreach ($result['result'] as $row) {
    $no         = $cnt;
    $name       = $util->readFromDB($row['name']);
    $sex        = $util->readFromDB($row['sex']);
    $bornYear   = $util->readFromDB($row['bornYear']);
    $bornDate   = $util->readFromDB($row['bornDate']);
    $mobile     = $util->readFromDB($row['mobile']);
    $drink0     = $row['drink0'] == 1 ? '白色沙瓦' : '';
    $drink1     = $row['drink1'] == 1 ? '蘋果' : '';
    $drink2     = $row['drink2'] == 1 ? '白桃' : '';
    $drink3     = $row['drink3'] == 1 ? '葡萄沙瓦' : '';
    $drink4     = $row['drink4'] == 1 ? '蜂蜜檸檬' : '';
    $drink5     = $row['drink5'] == 1 ? '檸檬薑汁' : '';
    $drink6     = $row['drink6'] == 1 ? '冬橘' : '';

    # 要用 \" 跳脫一下特殊符號
    $line = "\"$no\",\"$name\",\"$sex\",\"$bornYear\",\"$bornDate\",\"$mobile\",\"$zone\",\"$addr\",\"$email\",\"$drink0\",\"$drink1\",\"$drink2\",\"$drink3\",\"$drink4\",\"$drink5\",\"$drink6\",\"$channel\",\"$receiptNo\",\"$ctime\"".chr(13);
    # 將 utf-8 轉換為 big5, 沒辦法, 因為是 ms 的東西
    fwrite($fh, iconv('UTF-8', 'BIG5//IGNORE', $line));
    $cnt++;
}
fclose($fh);
```