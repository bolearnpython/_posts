---
title: ipython 
tags: ipython,快捷键
---
# ipython
## 基本使用
    . % run命令
    ipython - -pylab
    Tab键
    内省?
## 快捷键
    Ctrl - P    或上箭头键 后向搜索命令历史中以当前输入的文本开头的命令
    Ctrl - N   或下箭头键 前向搜索命令历史中以当前输入的文本开头的命令
    Ctrl - R   按行读取的反向历史搜索（部分匹配）
    Ctrl - Shift - v   从剪贴板粘贴文本
    Ctrl - C   中止当前正在执行的代码
    Ctrl - A   将光标移动到行首
    Ctrl - E   将光标移动到行尾
    Ctrl - K   删除从光标开始至行尾的文本
    Ctrl - U   清除当前行的所有文本译注12
    Ctrl - F   将光标向前移动一个字符
    Ctrl - b   将光标向后移动一个字符
    Ctrl - L   清屏
## 魔法
    %quickref 显示IPython的快速参考
    %magic 显示所有魔术命令的详细文档
    %debug 从最新的异常跟踪的底部进入交互式调试器
    %hist 打印命令的输入（可选输出）历史
    %pdb 在异常发生后自动进入调试器
    %paste 执行剪贴板中的Python代码
    %cpaste 打开一个特殊提示符以便手工粘贴待执行的Python代码
    %reset 删除interactive命名空间中的全部变量 / 名称
    %page OBJECT 通过分页器打印输出OBJECT
    %run script.py 在IPython中执行一个Python脚本文件
    %prun statement 通过cProfile执行statement，并打印分析器的输出结果
    %time statement 报告statement的执行时间
    %timeit statement 多次执行statement以计算系综平均执行时间。对那些执行时  间非常小的代码很有用
    %who、% who_ls、% whos 显示interactive命名空间中定义的变量，信息级别 / 冗余度可变
    %xdel variable 删除variable，并尝试清除其在IPython中的对象上的一切引用

## 搜索并重用命令历史
    上箭头键：搜索出命令历史中第一个与你输入的字符相匹配的命令。多次按将会在历史中不断搜索。
    下箭头键：子命令历史中向前搜索。
    Ctrl - R：部分增量搜素，循环在命令历史中搜素与输入相符的行。
## 输入和输出变量
    %hist 打印输入历史
    %reset 清空interactive命名空间，可选择是否清空输入和输出缓存
    %xdel 从IPython中移除特定对象的一切引用
## 记录输入和输出
    执行 % logstart能够开始记录控制台回话，包括输入和输出。与之配合的命令有：% logoff、% logon、% logstate、% logstop
## 与系统相关的命令：
    !cmd 在系统shell中执行cmd
    output =!cmd args 执行cmd，并将结果放在output中
    %bookmark 使用IPython的目录书签系统
    %cd directory 更改工作目录
    %pwd 返回系统当前工作目录
    %env 以字典形式返回系统环境变量
## shell
    在IPython中以感叹号(!)开头的命令表示其后的所有内容将会在系统shell中执行。
    使用！时，还允许使用当前环境中定义的Python值，只需在变量名前加上美元($)符号即可：
    foo = '54678'
    !mkdir $foo
## 书签
    %bookmark pys 'C:/User/xxx/PyWorkSpace'
    定义好书签之后，就可以在执行魔术命令 % cd时使用这些书签了：
    cd pys
    列出所有书签：
    %bookmark - l
    书签名与目录冲突
    %bookmark - b pys  # 强制使用书签目录