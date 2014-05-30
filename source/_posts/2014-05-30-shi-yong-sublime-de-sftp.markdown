---
layout: post
title: "使用 sublime 的 sftp"
date: 2014-05-30 18:05:17 +0800
comments: true
categories: ['TOOL', 'mac']
---
<!--more-->
## 安裝 sftp
* ref : https://sublime.wbond.net/installation
* 安裝 Package Control
  a. 把 console 打開 (ctrl + `)
  b. 貼上
 
```
import urllib.request,os; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); open(os.path.join(ipp, pf), 'wb').write(urllib.request.urlopen( 'http://sublime.wbond.net/' + pf.replace(' ','%20')).read()) 
```
* cmd + shift + p, 來安裝 sftp 的 plugin
<br/>

## 設定 sftp
* ref : http://wbond.net/sublime_packages/sftp/sidebar#SublimeSFTP
* 設定 project (/Users/trully/Documents/proj-stage)
* SFTP -> Map to Remote
* 設定以下項目
```
"save_before_upload": true,
"upload_on_save": true,
"sync_down_on_open": true,
"confirm_sync": false,
"ignore_regexes”: 這我沒改, 因為直接用 transmit download 要的 code, folder, 就沒有這問題
"extra_list_connections": 4,
"preserve_modification_times": true, 
```
* 用 transmit 下載 remote 的 code (這裡不要用 SFTP -> Download Folder, 會很久) 
<br/>

## 破解 sftp
* ref : http://xiaosong.me/share/reserved-sublime-text2-svn-sftp-plugin-ri

在
![](http://2.share.photo.xuite.net/trully/12a4d1b/19084527/1029215020_o.jpg)
填入以下內容
```
{
    "email": "hello@mail.com",
    "product_key": "c07bee-4382d0-b0cdbf-286096-3fa296"
} 
```
再重開 sublime 即可 (沒破解, save 10 次會出現叫你買的 dialog, 很煩) 
<br/>