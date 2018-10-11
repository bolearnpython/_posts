---
title: 安装scrapy
tags: 安装，scrapy
grammar_cjkRuby: true
---

## 安装scrapy

环境是linux

先安装一些依赖软件
```
yum install python-devel
yum install libffi-devel
yum install openssl-devel
```

然后安装pyopenssl库
```
pip install pyopenssl
```

安装xlml
```
yum install python-lxml
yum install libxml2-devel
yum install libxslt-devel
```

安装service-identity
```
pip install service-identity
```

安装twisted
```
pip install scrapy
```

安装scrapy
```
pip install scrapy -U
```
环境 window
```
pip install (pywin32_downloaded_from_ldf).whl
pip install (twisted_downloaded_from_lfd).whl
pip install twisted-win
python C:\Python35\Scripts\pywin32_postinstall.py -install
pip install scrapy
```
