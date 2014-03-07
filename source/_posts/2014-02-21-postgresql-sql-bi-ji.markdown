---
layout: post
title: "PostgreSQL sql 筆記"
date: 2014-02-21 14:48:32 +0800
comments: true
categories: ['DATABASE', 'pgsql', 'mysql']
---

#### 查看執行中 sql 的方法
``` sql
select * from pg_stat_activity
```
<br/>

#### base64 encode 欄位 - encode()
``` sql
select encode(convert_to(fname,'utf-8'), 'base64') as url
  from media
 where media_type in(1,2)
```
<!--more--><br/>

#### 取 hd - &
``` sql
select * from media where fmt & 2 = 2
```
<br/>

#### 取出當日的資料 - now()::date, interval '1h' 是指當天的 01:00
``` sql
select now()::date, media_id, title
  from media
 where uid = '238574878'
   and from = 'Wretch'
   and ctime >= now()::date + interval '1h'
 order by crt_datetime
```
<br/>

#### 依月份列出上傳量, 由 2012-10 開始算 - date_trunc()
``` sql
select count(mid), date_trunc('month', ctime) as month
  from media
 where ctime >= '2012-10-01 00:00:00'
 group by month
 order by month
```
![](https://dl-web.dropbox.com/get/Public/pic/Screenshot%202014-02-21%2014.53.13.png?_subject_uid=33912440&w=AABCHDNTIAy5NqY8eLmP0WESo2Ld6M1zwR1UdACGIjpPQQ)
<br/>

#### 依年份列出有在使用的人數 - date_trunc()
``` sql
select count(uid), date_trunc('year', last_upload_time) as total
  from member
 where (audio_cnt > 0 or video_cnt > 0)
   and used_quota > 0
 group by total
 order by total
```
<br/>

#### 檢查 wretch 來的, 是否有重覆的 media - not in, min(), group by
``` sql
select media_id
  from media
 where uid='236335446'
   and media_type in(1,2)
   and from='Wretch'
   and public <> 100
   and mid not in (
     select min(mid)
       from media
      where uid='236335446'
        and media_type in(1,2)
        and from='Wretch'
        and public <> 100
      group by srcpath
)
```
<br/>

#### 字串取代 - --row_number() OVER / 在結果加上序號 - replace()
``` sql
select replace(fname, '.flv', '.mp4')||row_number() OVER (ORDER BY title)||'.mp4' as cmd
  from media
 where uid = 'xxx'
   and from = 'cb'
 order by title
```
<br/>

#### 去除重覆的資料 (for 抽獎應用) - distinct on
``` sql
select distinct on (fieldname) * from tablename
```
#### 去除重覆的資料 (for 抽獎應用) - mysql, 利用 group by
``` sql
select name, sex, born_year, born_date, mobile, zone, addr, email
  from receipt_reg
 group by mobile
```
ref : http://www.jinnsblog.com/2013/09/sql-distinct-group-by-for-mysql-postgresql.html
<br/>

