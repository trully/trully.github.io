---
layout: post
title: "PostgreSQL server 設定筆記"
date: 2014-02-21 14:41:28 +0800
comments: true
categories: ['DATABASE', 'pgsql']
---

#### log 位置
```
/home/logs/pg/
/net/home0/_vlog/logs/db/
```
<!--more--><br/>

#### 設定檔位置
```
/net/pgsql/9.2.4/data/postgresql.conf
```

#### 若要紀錄所有執行的 sql, 在 postgresql.conf 做以下設定
```
log_statement = 'all' # none, ddl, mod, all
```

#### 若要紀錄執行時間 > 3 秒的 sql
```
# -1 is disabled, 0 logs all statements
# and their durations, > 0 logs only statements running at least 
# this number of milliseconds
log_min_duration_statement = 3000
```
ref : http://www.rhyous.com/2010/09/10/how-to-log-all-sql-statements-in-postgresql-running-on-freebsd/

