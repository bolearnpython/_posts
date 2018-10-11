---
title: pep8
tags: pep8,命名
---
# pep8
## 命名
    lowercase 小写字母
    lower_case_with_underscores 使用下划线分隔的小写字母
    UPPERCASE 大写字母
    UPPER_CASE_WITH_UNDERSCORES 使用下划线分隔的大写字母
    CapitalizedWords
    类名: CamelCase ，缩写词大写（ HTTPWriter 而非 HttpWriter ）
    变量名: lowercase_with_underscores
    方法和函数名: lowercase_with_underscores
    常量: UPPERCASE_WITH_UNDERSCORES
    预编译正则表达式: name_re
    比如：day_of_week, hosts_to_reboot, expired_cards
    比如：port（端口号）、age（年龄）、radius（半径） 等等
    比如：user_id、host_id
    比如：length_of_username、max_length、users_count
    is_superuser： 『是否超级用户』，只会有两种值：是 / 不是
    has_error：    『有没有错误』，只会有两种值：有 / 没有
    allow_vip：    『是否允许 VIP』，只会有两种值：允许 / 不允许
    use_msgpack：  『是否使用 msgpack』，只会有两种值：使用 / 不使用
    debug：        『是否开启调试模式』，被当做 bool 主要是因为约定俗成
    异常名中使用后缀"Error"
    dont:
        相似的变量名，比如同时出现 users、users1、 user3 这种序列
        不要使用带否定含义的变量名，用 is_special 代替 is_not_normal
        永远不要用字符'l', 'O', 或'I'作为单字符的变量名.

## 空格/空行
    在 list, dict, tuple, set, 参数列表的, 后面加一个空格
    在 dict 的: 后面加一个空格
    在注释符号  # 后面加一个空格，但是 #!/usr/bin/python 的 # 后不能有空格
    操作符两端加一个空格，如 + , -, *, / , | , & , =
    接上一条，在参数列表里的 = 两端不需要空格
    括号（(), {}, []）内的两端不需要空格

    function 和 class 顶上两个空行

    class 的 method 之间一个空行
    函数内逻辑无关的段落之间空一行，不要过度使用空行
    不要把多个语句写在一行，然后用
    隔开
    if / for / while 语句中，即使执行语句只有一句，也要另起一行

## 最大行长度
    限制所有行最多79个字符。
    income = (gross_wages
              + taxable_interest
              + (dividends - qualified_dividends)
              - ira_deduction
              - student_loan_interest)
    折叠长行的首选方法是使用Pyhon支持的圆括号, 方括号(brackets)和花括号(braces)
    反斜杠\
        a = '1' + '2' + '3' + \
        '4' + '5'
    或者
    a = ('1' + '2' + '3' +
         '4' + '5')
## 导入
    import os
    import sys
    from subprocess import Popen, PIPE
    from sound.effects import echo

## 文档
    # 因为某种原因这个函数减慢程序执行。
    def foo():
        """This is a simple docstring"""

    def bar():
        """This is a longer docstring with so much information in there
        that it spans three lines.  In this case the closing triple quote
        is on its own line.
        """
