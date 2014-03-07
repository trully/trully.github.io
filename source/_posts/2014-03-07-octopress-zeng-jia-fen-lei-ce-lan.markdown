---
layout: post
title: "Octopress 增加分類側欄"
date: 2014-03-07 11:36:32 +0800
comments: true
categories: ['TECHNICAL', 'octopress']
---

原本是參考這篇 http://blog.eddie.com.tw/2011/12/05/add-catetories-to-sidebar-in-octopress/

但發現在 rake preview 會有重覆噴 category log 的問題<br/>
在底下的留言發現有人解決, 而且把 code 貢獻出來 (網路上的好人真多^^)<br/>
所以照著 https://github.com/tokkonopapa/octopress-tagcloud 的步驟來做

#### 1. 到 https://github.com/tokkonopapa/octopress-tagcloud 將 tag_cloud.rb, category_list.html, tag_cloud.html 抓回來放到以下位置
![](https://dl-web.dropbox.com/get/Public/pic/Screenshot%202014-03-07%2011.41.34.png?_subject_uid=33912440&w=AACD02dzjmreFe3am05ZJuMpb3QeF9SKYT-kONYfZdKN-g)
<br/>

#### 2. 修改 _config.yml 的 default_asides 設定
```
default_asides: [custom/asides/tag_cloud.html, custom/asides/category_list.html, asides/recent_posts.html, asides/github.html, asides/delicious.html, asides/pinboard.html, asides/googleplus.html]
```
<br/>

#### 3. 重新 rake generate 再 rake preview 即可看到結果~
<br/>

#### 註: 若要調整 css, 可以到 sass/custom/_styles.scss
<br/>