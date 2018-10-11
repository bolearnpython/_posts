---
title: BeautifulSoup
tags: BeautifulSoup，解析
---
# BeautifulSoup
## bs
    from bs4 import BeautifulSoup
    bs = BeautifulSoup(content, 'lxml')
    ['class']  # list
    ['id']  # str
    ['href']
    .name .head .body
    .attrs  # 字典
    .text  # 文档
    .contents  # 子list
    .children  # 生成器
    .descendants  # 所以子孙节点
## 节点
    使用 .next_sibling 和 .previous_sibling 属性来查询兄弟节点
    通过 .next_siblings 和 .previous_siblings 全部兄弟节点
    前进后退
    next_element 和 .previous_element
    通过 .next_elements 和 .previous_elements 所有前后节点
## text
    .string
    .strings和.stripped_strings
    [text for text in soup.stripped_strings]
    .get_text('|', strip=True)
## find_all
    find_all(name, attrs, recursive, text, **kwargs)  # recursive=False只搜索子节点

    def has_class_but_no_id(tag):
        return tag.has_attr('class') and not tag.has_attr('id')
    soup.find_all(has_class_but_no_id)
    soup.find_all(href=re.compile("elsie"), id='link1')
    soup.find_all(attrs={"data-foo": "value"}  # data-* 属性
    soup.find_all(text=["Tillie", "Elsie", "Lacie"])
    soup.find_all(id='link2')

    soup.find_all("a", limit=2)
    soup.find_all('a') - -soup(a)
## find
find(name, attrs, recursive, text, **kwargs)

    1 find(tagname)        # 直接搜索名为tagname的tag 如：find('head')
    2 find(list)           # 搜索在list中的tag，如: find(['head', 'body'])
    3 find(dict)           # 搜索在dict中的tag，如:find({'head':True, })
    4 find(re.compile('')) # 搜索符合正则的tag, 如:find(re.compile('^p'))
## select
    标签名不加任何修饰，类名前加点，id名前加
    soup.select('title')
    soup.select('.sister')
    soup.select('#link1')
    soup.select("head > title")  # 直接子标签查找
    不在同一节点的空格隔开，同一节点的不加空格
    soup.select('p a[href="http://example.com/elsie"]')
