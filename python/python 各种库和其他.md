---
title: python 各种库和其他
tags: 库
---
# python 各种库和其他
## sys
### 当前目录
```
sys.path[0]
```
## 断言
    assert 'wor' in demo_str
    assert demo_str.startswith('hello')
    assert hasattr(demo_str, '__sizeof__')
    assert 4 == 4.0
    assert 5 > 4
    assert re.match('hello \d+', 'hello 9527')
    assert 'x' in json.loads('{"x":1, "y":2}')
    assert True

## random
    random.sample(["I", "love", 3, "python", 66], 4)
    a = [3, 4, 5, 6]
    random.shuffle(a)
    random.randrange(0, 101, 2)  # 偶数
    random.randint(3, 8)
    random.uniform(4, 8)
    random.random()  # 0-1
    random.choice()

## pypinyin
    import pinyin
    pinyin.get('你 好')
    pinyin.get('你好', format="strip", delimiter=" ")
    pinyin.get('你好', format="numerical")
    pinyin.get_initial('你好')

    from pypinyin import pinyin, lazy_pinyin
    import pypinyin
    pinyin('qianxinan', style=pypinyin.FIRST_LETTER)
    pinyin('中心')
    [['zhōng'], ['xīn']]
    pinyin('中心', heteronym=True)  # 启用多音字模式
    [['zhōng', 'zhòng'], ['xīn']]
    pinyin('中心', style=pypinyin.FIRST_LETTER)  # 设置拼音风格
    [['z'], ['x']]
    pinyin('中心', style=pypinyin.TONE2, heteronym=True)
    [['zho1ng', 'zho4ng'], ['xi1n']]
    lazy_pinyin('中心')  # 不考虑多音字的情况
    ['zhong', 'xin']
    lazy_pinyin('你好☆☆', errors='ignore')
    ['ni', 'hao']
    lazy_pinyin('你好☆☆', errors=lambda x: 'star')
    ['ni', 'hao', 'star']
    # 自定义
    from pypinyin import lazy_pinyin, load_phrases_dict, TONE2
    hans = '桔子'
    lazy_pinyin(hans, style=TONE2)
    load_phrases_dict({'桔子': [['jú'], ['zǐ']]})
    lazy_pinyin(hans, style=TONE2)

## operator
    a + b               add(a, b)
    a - b               sub(a, b)
    a * b               mul(a, b)
    a / b               truediv(a, b)
    a // b              floordiv(a, b)

    a ** b              pow(a, b)
    a % b               mod(a, b)

    a @ b               matmul(a, b)
    - a                 neg(a)
    not a               not_(a)
    + a                 pos(a)

    a & b               and_(a, b)
    a ^ b               xor(a, b)
    ~ a                 invert(a)
    a | b               or_(a, b)
    a is b              is_(a, b)
    a is not b          is_not(a, b)
    a << b              lshift(a, b)
    a >> b              rshift(a, b)

    a < b               lt(a, b)
    a <= b              le(a, b)
    a == b              eq(a, b)
    a != b              ne(a, b)
    a >= b              ge(a, b)
    a > b               gt(a, b)

## pdb
    h(elp) 显示命令列表
    help command 显示命令的说明文档
    c(continue) 回复程序的执行
    q(uit) 退出调试器
    b(reak) number 在指定行设置断点
    s(tep) 单步进入(step into)函数
    n(next) 执行当前行(step over)，并进入下一行
    u(p) / d(own) 在函数调用栈中向上或向下移动
    a(rgs) 显示当前函数的参数
    debug statement 在新的调试器中调用语句statement
    l(ist) statement 显示当前行，以及当前栈级别上的上下文参考代码
    w(here) 打印当前位置的完整栈跟踪

## ipdb
    -m ipdb
    ENTER(重复上次命令)
    c(继续)
    l(查找当前位于哪里)
    s(进入子程序)
    r(运行直到子程序结束)
    !<python 命令 >
    h(帮助)
    a(rgs) 打印当前函数的参数
    j(ump) 让程序跳转到指定的行数
    l(ist) 可以列出当前将要运行的代码块
    n(ext) 让程序运行下一行，如果当前语句有一个函数调用，用 n 是不会进入被调用的函数体中的
    p(rint) 最有用的命令之一，打印某个变量
    q(uit) 退出调试
    r(eturn) 继续执行，直到函数体返回
    s(tep) 跟 n 相似，但是如果当前有一个函数调用，那么 s 会进入被调用的函数体中
## 模板编写
     ${PROJECT_NAME} - 当前Project名称;

     ${NAME} - 在创建文件的对话框中指定的文件名;

     ${USER} - 当前用户名;

     ${DATE} - 当前系统日期;

     ${TIME} - 当前系统时间;

     ${YEAR} - 年;

     ${MONTH} - 月;

     ${DAY} - 日;

     ${HOUR} - 小时;

     ${MINUTE} - 分钟；

     ${PRODUCT_NAME} - 创建文件的IDE名称;

     ${MONTH_NAME_SHORT} - 英文月份缩写, 如: Jan, Feb, etc;

     ${MONTH_NAME_FULL} - 英文月份全称, 如: January, February, etc；

     # -*- coding: utf-8 -*-
    """
    -------------------------------------------------
       File Name：     ${NAME}
       Description :
       Author :       ${USER}
       date：          ${DATE}
    -------------------------------------------------
       Change Activity:
                       ${DATE}:
    -------------------------------------------------
    """
    __author__ = '${USER}'
## python执行命令
    os.system("命令加参数")
    stream = os.popen("命令和参数")
    subprocess模块的管道Popen.
    subprocess.Popen("echo Hello World",shell=True,stdout=PIPE).stdout.read()
    os.popen("echo Hello World").read()
    subprocess.call("echo Hello World", shell=True)
    subprocess.check_call(["ls", "-l"])
    # shell = True 必须为字符串 shell = False 必须为序列
    # check_output 返回命令的执行结果
    # check_all 如果结果为0则返回0 如果命令执行出错则抛出异常
    # 执行python命令，进入python解释器，stdin标准输入、stdout标准输出、stderr错误输出，universal_newlines=True自动输入换行符
    obj = subprocess.Popen(["python"], stdin=subprocess.PIPE, stdout=subprocess.PIPE, stderr=subprocess.PIPE, universal_newlines=True)

## csv
    import csv
    import datetime

    # 数据
    data = [
        [1, "a,bc", 19.353, datetime.datetime(2001, 3, 17)],
        [2, "ei,f", 13.287, datetime.datetime(2011, 4, 27)],
        [3, "q\"ij", 15.852, datetime.datetime(2003, 7, 14)],
        [4, "zh'n", 11.937, datetime.datetime(2012, 1, 9)],
        [5, "i\'op", 12.057, datetime.datetime(2009, 5, 18)],
    ]

    # 写文件
    with open("test.csv", "w") as file:
        writer = csv.writer(file, dialect="excel")
        # writer.writerows(data)
        for item in data:
            writer.writerow(item)

    # 读文件
    with open("test.csv", "r") as file:
        reader = csv.reader(file, dialect="excel")
        for item in reader:
            print(item)

    # 读文件
    with open("test.csv", "r") as file:
        reader = csv.DictReader(file, fieldnames=["id", "name", "float", "datetime"], dialect="excel")
        data = [item for item in reader]
        print(data)

    # 写文件
    with open("test.csv", "w") as file:
        writer = csv.DictWriter(file, fieldnames=["id", "name", "float", "datetime"], dialect="excel")
        writer.writeheader()
        for item in data:
            writer.writerow(item)
## itertools
    import itertools
    for i in itertools.count(10,2):                 #开始，步数
        print(i)
        if i>100:
            break
    for i,j in enumerate(itertools.cycle('Abc')):
        print(j)
        if i>16:
            break
    for item in itertools.repeat('hi',5):
        print(item)

    num=itertools.chain([3,4],(5,6),{3,4},[3,[5,9]])#可迭代连接
    list(itertools.compress('abcdef',[0,1,0,0,0,0]))# b
    from itertools import dropwhile
    list(dropwhile(lambda x:x<5,[2,3,4,5,7,2,3]))   #返回 不满足的至最后
    from itertools import takewhile
    list(takewhile(lambda x:x<5,[2,3,4,5,7,2,3]))   #返回 0:满足
    from itertools import filterfalse
    list(filterfalse(lambda x:x<5,[2,3,4,5,7,2,3])) # 返回不满足的

    from itertools import groupby
    for i,j in groupby('abdcdfffggeehhhaa'):
        print(i,':',list(j))
    data=['a','bb','ccc','dd','ee','f']
    for i,j in groupby(data,len):
        print(i,':',list(j))

    from itertools import zip_longest
    for i in zip_longest('abcd','xy',fillvalue='--'):
        print(i)

    for item in itertools.product('abcd','xy'):
        print(item)
    list(itertools.product('xy','12','ab'))

    from itertools import permutations
    list(''.join(i)for i in permutations('abcd',4))
## collections
### nametuple
    from collections import namedtuple

    websites = [
        ('Sohu', 'http://www.google.com/', u'张朝阳'),
        ('Sina', 'http://www.sina.com.cn/', u'王志东'),
        ('163', 'http://www.163.com/', u'丁磊')
    ]

    Website = namedtuple('Website', ['name', 'url', 'founder'])
    for website in websites:
        website = Website._make(website)
        print (website)

### deque
    from collections import deque
    q = deque(['a', 'b', 'c'])
    appendleft()和popleft()

### defaultdict
    from collections import defaultdict
    colours = (
        ('Yasoob', 'Yellow'),
        ('Ali', 'Blue'),
        ('Arham', 'Green'),
        ('Ali', 'Black'),
        ('Yasoob', 'Red'),
        ('Ahmed', 'Silver'),
    )
    favourite_colours = defaultdict(list)
    for name, colour in colours:
        favourite_colours[name].append(colour)

    print(favourite_colours)

    tree = lambda: defaultdict(tree)
    some_dict = tree()
    some_dict['colours']['favourite'] = "yellow"
    import json
    print(json.dumps(some_dict))
    print(json.dumps(favourite_colours))

###  OrderedDict
    from collections import OrderedDict
    colours = OrderedDict([("Red", 198), ("Green", 170), ("Blue", 160)])
    for key, value in colours.items():
        print(key, value)

###  Counter
    from collections import Counter
    colours = (
        ('Yasoob', 'Yellow'),
        ('Ali', 'Blue'),
        ('Arham', 'Green'),
        ('Ali', 'Black'),
        ('Yasoob', 'Red'),
        ('Ahmed', 'Silver'),
    )
    favs = Counter(name for name, colour in colours)
    print(favs)

    with open('filename', 'rb') as f:
        line_count = Counter(f)
    print(line_count)

    word_counts = Counter()
    with open('') as f:
        for line in f:
            word_counts.update(line.strip().split(':'))

    for key, val in (word_counts.most_common(3)):
        print(key, ':', val)
## pyinstaller 转exe
```
pip install pyinstaller
pyinstaller yourprogram.py
```
## heapq 最大3个 最小3个
```
portfolio = [
    {'name': 'IBM', 'shares': 100, 'price': 91.1},
    {'name': 'AAPL', 'shares': 50, 'price': 543.22},
    {'name': 'FB', 'shares': 200, 'price': 21.09},
    {'name': 'HPQ', 'shares': 35, 'price': 31.75},
    {'name': 'YHOO', 'shares': 45, 'price': 16.35},
    {'name': 'ACME', 'shares': 75, 'price': 115.65}
]
cheap = heapq.nsmallest(3, portfolio, key=lambda s: s['price'])
expensive = heapq.nlargest(3, portfolio, key=lambda s: s['price'])
```
## url操作 furl
```
from furl import furl
f = furl('http://www.google.com/?one=1&two=2')
f.args['three'] = '3'
del f.args['one']
f.url
'http://www.google.com/?two=2&three=3'

f = furl('http://www.google.com/')
f.fragment.path.segments = ['two', 'directories']
f.fragment.args = {'one':'argument'}
f.url
'http://www.google.com/#two/directories?one=argument'

f = furl('http://www.google.com/')
f.path = 'some encoding here'
f.args['and some encoding'] = 'here, too'
f.url
'http://www.google.com/some%20encoding%20here?and+some+encoding=here,+too'
f.set(host=u'ドメイン.テスト', path=u'джк', query=u'☃=☺')
f.url
'http://xn--eckwd4c7c.xn--zckzah/%D0%B4%D0%B6%D0%BA?%E2%98%83=%E2%98%BA'
```
## 清理
```
import bleach
bleach.clean('an <script>evil()</script> example')
bleach.linkify('an http://example.com url')
```
## 时间解析
```
from dateparser import parse
parse('2016-4')
```
## 字符相似
```
from fuzzywuzzy import fuzz
from fuzzywuzzy import process
fuzz.ratio("this is a test", "this is a test!")
fuzz.partial_ratio("this is a test", "this is a test!")
fuzz.ratio("fuzzy wuzzy was a bear", "wuzzy fuzzy was a bear")
fuzz.token_sort_ratio("fuzzy wuzzy was a bear", "wuzzy fuzzy was a bear")
fuzz.token_sort_ratio("fuzzy was a bear", "fuzzy fuzzy was a bear")
fuzz.token_set_ratio("fuzzy was a bear", "fuzzy fuzzy was a bear")
choices = ["Atlanta Falcons", "New York Jets", "New York Giants", "Dallas Cowboys"]
process.extract("new york jets", choices, limit=2)
    [('New York Jets', 100), ('New York Giants', 78)]
process.extractOne("cowboys", choices)
    ("Dallas Cowboys", 90)
```
## 名字
```
from nameparser import HumanName
name = HumanName("Dr. Juan Q. Xavier de la Vega III (Doc Vega)")
name.last
name.as_dict()
str(name)
name.string_format = "{first} {last}"
str(name)
```
