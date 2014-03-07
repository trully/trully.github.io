---
layout: post
title: "用 GitHub 寫文章的步驟"
date: 2014-02-21 14:06:26 +0800
comments: true
categories: ['TECHNICAL', 'github', 'octopress']
---

```
cd ~/apps/octopress
rake new_post
```
會得到文章的檔名
![](https://dl-web.dropbox.com/get/Public/pic/Screenshot%202014-01-09%2015.05.52.png?_subject_uid=33912440&w=AADM-OzBAPShKp2JZR0hLNaLp78DnA1Aera34urEixKWlg)
<!--more-->
再用 Mou 或 vi 編輯內容
```
open -a Mou source/_posts/2014-01-09-first-article.markdown 
# or
open source/_posts/2014-01-09-first-article.markdown 
# or
vi source/_posts/2014-01-09-first-article.markdown
# 可以打開 Mou 的說明頁參考 markdown 語法
open /Applications/Mou.app/Contents/Resources/help.md
```
內容 sample
```
---
layout: post
title: "first article"
date: 2014-01-09 15:03:44 +0800
comments: true
categories: 'Technical'
tags: ['github', 'octopress']
---
this is my first article @ github by octopress
* line1
* line2
```
文章寫完後執行
```
rake generate # 沒做似乎也可以
rake preview # for local preview
```
沒問題的話就 push 到 github 
```
git add .
git commit -m "first article"
git push origin source
rake deploy
```

到線上看結果
http://trully.github.io/
