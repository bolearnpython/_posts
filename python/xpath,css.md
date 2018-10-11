---
title: xpath,css
tags: xpath,css,scrapy
grammar_cjkRuby: true
---
[TOC]
##  例子
### 文本一
    response.xpath('//title/text()').extract()
    response.css('title::text').extract()
### 文本 包括子节点
    sel.xpath("//a[1]//text()").extract()
### 文本 包括子节点 合并
    sel.xpath("string(//a[1])").extract()
### 属性
    response.xpath('//img/@src').extract()
    response.css('img::attr(src)').extract()
### 混合
    response.css('img').xpath('@src').extract()
    response.xpath('//img').css('::attr(src)').extract()
### 精确
    response.xpath('//div[@id="images"]/a/text()').extract()
    response.css('div#images a::text').extract()
### 模糊
    response.xpath('//div[contains(@id, "image")]/a/text()').extract()
    response.css('div[id*=image] a::text').extract()
### 正则
    response.xpath('//a[contains(@href, "image")]/text()').re(r'Name:\s*(.*)')
###第一个
    response.xpath('//div[@id="images"]/a/text()').extract_first()
###默认值
    response.xpath('//div[@id="not-exists"]/text()').extract_first(default='not-found')


## XPath建议

### 使用text作为条件时
避免使用`.//text()`,直接使用`.`
```
>>> sel.xpath("//a[contains(., 'Next Page')]").extract()
[u'<a href="#">Click here to go to the <strong>Next Page</strong></a>']
```

### //node[1]和(//node)[1]区别

* //node[1]: 选择所有位于第一个子节点位置的node节点
* (//node)[1]: 选择所有的node节点，然后返回结果中的第一个node节点
```
sel = Selector(text=doc, type="html")
xp = lambda x: sel.xpath(x).extract()
xp("(//li)[1]")
xp("//ul/li[1]")    #多个
xp("(//ul/li)[1]")  #一个
```
### [CSS](http://www.w3school.com.cn/cssref/css_selectors.asp)


![enter description here][1]
```
p                        选择所有 <p> 元素。
.intro                   选择 class="intro" 的所有元素
#firstname               选择 id="firstname" 的所有元素。
::attr(src) ::text       选择被用户选取的元素部分
a[src^="https"]          选择其 src 属性值以 "https" 开头的每个 <a> 元素。
a[src$=".pdf"]           选择其 src 属性以 ".pdf" 结尾的所有 <a> 元素。
a[src*="abc"]            选择其 src 属性中包含 "abc" 子串的每个 <a> 元素。

div,p                    选择所有 <div> 元素和所有 <p> 元素。
div p                    选择 <div> 元素内部的所有 <p> 元素。
div>p                    选择父元素为 <div> 元素的所有 <p> 元素。
div+p                    选择紧接在 <div> 元素之后的所有 <p> 元素。

[target]                 选择带有 target 属性所有元素。
[target=_blank]          选择 target="_blank" 的所有元素。
[title~=flower]          选择 title 属性包含单词 "flower" 的所有元素

:not(p)                  选择非 <p> 元素的每个元素。
p~ul                     选择前面有 <p> 元素的每个 <ul> 元素。
```
### [Xpath](http://www.w3school.com.cn/xpath/)
`
XPath相对路径 不使用`/`开头的
`
```
/       从根元素选取
//      从全文档选取
.       当前元素
..      父元素
@       属性

*       匹配任何元素
@*      匹配任何属性
node()  匹配任何类型元素

last()
not()
p[not(contains(@class, ‘title’))]

#轴
ancestor            选取当前节点的所有先辈（父、祖父等）。
ancestor-or-self    选取当前节点的所有先辈（父、祖父等）以及当前节点本身。
attribute           选取当前节点的所有属性。
child               选取当前节点的所有子元素。
descendant          选取当前节点的所有后代元素（子、孙等）。
descendant-or-self  选取当前节点的所有后代元素（子、孙等）以及当前节点本身。
following           选取文档中当前节点的结束标签之后的所有节点。
namespace            选取当前节点的所有命名空间节点。
parent              选取当前节点的父节点。
preceding           选取文档中当前节点的开始标签之前的所有节点。
preceding-sibling   选取当前节点之前的所有同级节点。
self                选取当前节点。

#运算
|
+
-
*
div
=
!=
<
<=
>
>=
or
and
mod #计算除法的余数
```


  [1]: ./images/css%E9%80%89%E6%8B%A9%E5%99%A8_1.png "css选择器"