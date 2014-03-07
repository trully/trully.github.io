---
layout: post
title: "Git 簡易筆記"
date: 2014-03-07 16:31:03 +0800
comments: true
categories: ['PROGRAMMING', 'git']
---

### 環境設定
```
git config user.name trully
git config user.email username@email.com
git config --global user.name "trully"
git config --global user.email "username@email.com"
git config --global color.diff auto # git diff 要顯示顏色
git config --global color.status auto # git status 要顯示顏色
git config --global color.branch auto
git config --global color.log auto # git log --graph 會很漂亮
cat .git/config
```
<!-- more -->

### 常用指令
```
git clone git@trac.team.xuite.net:vlog/php.git HiNet_Vlog
git clone git@trac.team.xuite.net:vlog/java.git VlogJMSConsumer

git status # 或 gst
git diff # 或 gd
git log
git add [code path]
git commit # commit add 的 code
git push # push 回 resp

git remote -v

# 回復未 commit 的變更 (同 svn revert)
git checkout [codepath]

# 還原已 commit 的檔案
git revert 18ead0a60740a74fd568dd885dda3b6836e582dc 

# 與 trac mapping link 的方式
changeset:1072fa5/vlog/php 
```

### 尋找已 git rm 的 code
```
git log --name-status

# ex: 尋找 dir 或 file
git log --name-status net/xuite/jms/consumer
git log --name-status net/xuite/jms/consumer/EncodeAudio.java

# ex: 把 m4a 關鍵字的前後 5 行都列出來看
git log --name-status | grep -A 5 -B 5 m4a
```

### 要忽略的 code list, 寫在 .gitignore 裡
```
cat ./.gitignore
/scripts/log
/scripts/patch
/backend/template/compile
```

若用 vi 輸入 comment, 會出現 error: There was a problem with the editor 'vi'. Please supply the message using either -m or -F option. 的錯誤, 解法如下(未測)
```
git config --global core.editor /usr/bin/vim
```
<br>

ref : <br>
http://blog.longwin.com.tw/2009/05/git-initial-env-setup-2009/
http://ihower.tw/blog/archives/2591
