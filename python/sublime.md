---
title: sublime
tags: sublime,编辑器
---
# sublime
## 快捷键
### 快捷键一：
    Ctrl + KK 删除光标位置至行尾部分内容
    Ctrl + K + Delete 删除光标位置至行首部分内容

    Ctrl + ] 增加缩进
    Ctrl + [ 减少缩进
    Ctrl + / 行注释、取消行注释
    Ctrl + Shift + / 块注释、取消块注释

    Ctrl + D 选择单词，重复按下选中相同单词
    Ctrl + Shift + L：选择多行
    Alt + F3：选择所有相同的词
    Ctrl + X 剪切
    ctrl + j 合并

    Ctrl + Alt + Up 向上列选择
    Ctrl + Alt + Down 向下列选择
    Ctrl + ↑/↓移动当前显示区域，
    Ctrl + Shift + ↑/↓移动当前行

    Alt + R : 开启正则表达式功能
    Alt + Enter: 找到匹配目标后全部选择
    Ctrl + O可以实现头文件和源文件之间的快速切换
    Ctrl + Shift + W：关闭所有打开文件
    Shift + 右键拖动：光标多不，用来更改或插入列内容鼠标的前进后退键可切换Tab文件
    Ctrl + Enter 当前行后一行插入
    Ctrl + Shift + Enter 当前行前一行插入

    Ctrl + M 跳转到右括号，重复按下跳转至左括号
    Ctrl + Shift + M 选中当前括号中的所有内容
    Ctrl + Y 重做，或重复上一个快捷键操作
    Ctrl + Shift + V 粘贴并缩进
    Ctrl + Space 选择下一个自动完成提示
    Ctrl + U 软撤销，重复操作回到撤销前的最后一次修改。
    Alt + Shift + W 选择部分使用html标签包裹
### 导航及跳转
    Ctrl + P 通过文件名快速打开
    Ctrl + R 跳转至符号
    Ctrl + ; 当前文件内单词跳转
    Ctrl + G 当前文件内行跳转
### 全局
    Ctrl + Shift + P 命令行
    Ctrl + KB 显示隐藏边栏
    Ctrl + Shift + Alt + P 状态浮层显示范围
### 查找替换
    Ctrl + F 查找
    Ctrl + H 替换
    Ctrl + Shift + F 全局查找
### 标签
    Ctrl + Shift + T 打开最后关闭标签
    Ctrl + PgUp 向上循环Tab
    Ctrl + PgDn 向下循环Tab
    Ctrl + Left/Right 文件内查找
    Ctrl + W 关闭当前标签
    Alt + [数字] 切换到数字对应Tab，数字要小于等于当前Tab的数量
    Alt + . 关闭当前html标签
### 分割窗口 and 屏幕
    Alt + Shift + 1 单列视图
    Alt + Shift + 2 双列视图
    Alt + Shift + 3 三列视图
    Alt + Shift + 4 四列视图
    Alt + Shift + 5 四格视图
    Alt + Shift + 8 两行视图
    Ctrl + [数字] 跳转到对应分组，数字范围1~4
    Ctrl + Shift + [数字] 文件移动到对应分组，数字范围1~4
    Ctrl + N：新建窗口
    F11：全屏
    Shift + F11：全屏免打扰模式，只编辑当前文件
### 书签
    Ctrl + F2 添加/取消书签
    F2 下一个书签
    Shift + F2 上一个书签
    Ctrl + Shift + F2 清除书签

### 大小写转换

    Ctrl + KU 转换为大写
    Ctrl + KL 转换为小写

## sublime插件
### anaconda
    {
        "auto_complete_triggers":
        [{"selector": "source.python - string - comment - constant.numeric", "characters": ""}],
        "auto_complete_selector": "-",
        "pep8_ignore": ["E501", "W292", "E303", "W391", "E225", "E302", "W293", "E402"],
        "python_interpreter": "C:/Program Files/Anaconda3/python.exe",
        "anaconda_linting": false,
        "complete_parameters": false,
        //保存文件后自动pep8格式化
        "auto_formatting": true,
        //库函数的提示
        "enable_signatures_tooltip": true,
        "merge_signatures_and_doc":true,
        "anaconda_linting_behaviour": "save-only",
        "anaconda_gutter_theme": "hard",
        "anaconda_linter_show_errors_on_save": true,
        "extra_paths":
        [
            "C:\\Program Files\\Anaconda3",
            "C:\\Program Files\\Anaconda3\\DLLs",
            "C:\\Program Files\\Anaconda3\\Lib",
            "C:\\Program Files\\Anaconda3\\Lib/lib-tk",
            "C:\\Program Files\\Anaconda3\\Lib/site-packages"
        ]
    }
### SublimeREPL
    [
        { "keys": ["f1"], "caption": "SublimeREPL: Python - RUN current file", "command": "run_existing_window_command", "args": {"id": "repl_python_run", "file": "config/Python/Main.sublime-menu"}},
        { "keys": ["f2"], "caption": "SublimeREPL: Python - PDB current file", "command": "run_existing_window_command", "args": {"id": "repl_python_pdb", "file": "config/Python/Main.sublime-menu"}},
        { "keys": ["f3"], "caption": "SublimeREPL: IPython - IPython", "command": "run_existing_window_command", "args": {"id": "repl_python", "file": "config/Python/Main.sublime-menu"}},

    ]
### SublimeTmpl
    ctrl+alt+h html
    ctrl+alt+j javascript
    ctrl+alt+c css
    ctrl+alt+p php
    ctrl+alt+r ruby
    ctrl+alt+shift+p python
    settings-user中设置上自己的信息
    在key bindings-user中添加了以下信系
    [
        {
            "caption": "Tmpl: Create python", "command": "sublime_tmpl",
            "keys": ["ctrl+alt+p"], "args": {"type": "python"}
        },
    ]
    {
                "disable_keymap_actions": false, // "all"; "html,css"
                "date_format" : "%Y-%m-%d %H:%M:%S",
                "attr": {
                    "author": "mx",
                    "email": "mengxiang@xiangcloud.com.cn",
                    "link": "http://www.xiangcloud.com.cn/"
                }
            }
### Package Control
    ctrl+`
打开控制台
```
import urllib.request,os,hashlib; h = 'df21e130d211cfc94d9b0905775a7c0f' + '1e3d39e33b79698005270310898eea76'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)
```
### 其他插件
GBK
chinese
###  setting
```
{
    "dpi_scale": 1.0,#中文乱码
    "font_size": 17,
    "highlight_line": true,
    "highlight_modified_tabs": true,
    "ignored_packages":
    [
        "Vintage"
    ],
    "scroll_past_end": true,
    "translate_tabs_to_spaces": true,
    "trim_trailing_white_space_on_save": true
}
```

