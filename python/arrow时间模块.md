---
title: arrow时间模块 
tags: arrow,时间模块
---
# Python 日期处理 arrow时间模块
## -- arrow
```
arrow.utcnow()
arrow.now()
arrow.now('US/Pacific')
arw=arrow.utcnow()
arw.datetime
arw.timestamp
arw.year
arw.time()
arw.date()
arw.tzinfo
arw.naive
```
## --arrow.get
```
arrow.get(2013, 5, 5)
arrow.get('2013-05-11T21:23:58.970460+00:00')
arrow.get('2013-09-30T15:34:00.000-07:00')
arrow.get('2013-05-05 12:30:45', 'YYYY-MM-DD HH:mm:ss')
arrow.get('June was born in May 1980', 'MMMM YYYY')
arrow.get(1367900664)
arrow.get(1367900664.152325)
arrow.get('1367900664')
arrow.get('1367900664.152325')
```
## --arrow.format
```
local=arrow.now()
local.format()
local.format('YYYY-MM-DD HH:mm:ss ZZ')
local.humanize()
local.humanize(locale='ko_kr')
arrow.utcnow().format('YYYY-MM-DD HH:mm:ss ZZ')
```
## --arrow -change
```
arw = arrow.utcnow()
arw.shift(weeks=+3)
arw.replace(hour=4, minute=40)
arw.replace(weeks=+3)
arw.replace(tzinfo='US/Pacific')
utc.to('local')
utc.to('local').to('utc')
```
## --arrow -span
```
arrow.utcnow().span('hour')
arrow.utcnow().floor('hour')
arrow.utcnow().ceil('hour')
```
## --arrow -range
```
start = arrow.get(2013, 5, 5, 12, 30)
end = arrow.get(2013, 5, 5, 17, 15)
for r in arrow.Arrow.span_range('hour', start, end):
    print(r)
    print(repr(r))
```