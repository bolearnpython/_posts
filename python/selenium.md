---
title: selenium
tags: 浏览器,selenium
---
# selenium
## --隐式等待
```
driver.implicitly_wait(5)
driver.save_screenshot('e:\screenshot.png')
driver.set_page_load_timeout(10)
driver.set_script_timeout(10)
text = driver.page_source
COOKIES_ENABLES = False
driver.close()
driver.quit()
```
## --多层框架或窗口的定位：
```
switch_to_frame()
switch_to_window()
driver.switch_to_frame(driver.find_element_by_id``("topmenuFrame"))
driver.switch_to_default_content()
· text  获取该元素的文本
· submit  提交表单
· get_attribute  获得属性值
# --处理下拉框
switch_to_alert()
accept()
```
## --find
```
find_element_by_id
find_element_by_name
find_element_by_xpath
find_element_by_link_text
find_element_by_partial_link_text
find_element_by_tag_name
find_element_by_class_name
find_element_by_css_selector
```
## --cookies
```
cookie = [item["name"] + "=" + item["value"] for item in driver.get_cookies()]
cookiestr = ';'.join(item for item in cookie)
driver.get_cookies（）   获得cookie信息
add_cookie(cookie_dict)  向cookie添加会话信息
delete_cookie(name)      删除特定(部分)的cookie
delete_all_cookies()     删除所有cookie
```
## --input
```
from selenium.webdriver.common.keys import Keys
elem = driver.find_element_by_name("q")
elem.clear()
elem.send_keys("python")
# click
click()
context_click()  右击
double_click()   双击
drag_and_drop()  拖动
```
## --phantomjs
```
from selenium import webdriver
from selenium.webdriver.common.desired_capabilities import DesiredCapabilities
service_args = []
service_args.append('--load-images=no')  # 关闭图片加载
service_args.append('--disk-cache=yes')  # 开启缓存
service_args.append('--ignore-ssl-errors=true')  # 忽略https错误
dcap = dict(DesiredCapabilities.PHANTOMJS)
# 从USER_AGENTS列表中随机选一个浏览器头，伪装浏览器
dcap["phantomjs.page.settings"] = (
    {"User-Agent": "Mozilla/5.0 (Linux; Android 4.4.2; en-us; SAMSUNG SCH-I545 Build/KOT49H) AppleWebKit/537.36 (KHTML, like Gecko) Version/1.5 Chrome/28.0.1500.94 Mobile Safari/537.36"})
# 不载入图片，爬页面速度会快很多
dcap["phantomjs.page.settings.loadImages"] = False
driver = webdriver.PhantomJS(
    desired_capabilities=dcap, service_args=service_args)
driver.get_screenshot_as_file('01.png')
driver.quit()
```
## --调用js
```
driver.execute_async_script(js)
driver.execute_script(js)
```
# service_args
```
–user - data - dir =”[PATH]” 指定用户文件夹User Data路径，可以把书签这样的用户数据保存在系统分区以外的分区。
–disk - cache - dir =”[PATH]“ 指定缓存Cache路径
–disk - cache - size = 指定Cache大小，单位Byte
–first run 重置到初始状态，第一次运行
–incognito 隐身模式启动
–disable - javascript 禁用Javascript
--omnibox - popup - count = "num" 将地址栏弹出的提示菜单数量改为num个。我都改为15个了。
--user - agent = "xxxxxxxx" 修改HTTP请求头部的Agent字符串，可以通过about: version页面查看修改效果
--disable - plugins 禁止加载所有插件，可以增加速度。可以通过about: plugins页面查看效果
--disable - javascript 禁用JavaScript，如果觉得速度慢在加上这个
--disable - java 禁用java
--start - maximized 启动就最大化
--no - sandbox 取消沙盒模式
--single - process 单进程运行
--process - per - tab 每个标签使用单独进程
--process - per - site 每个站点使用单独进程
--in-process - plugins 插件不启用单独进程
--disable - popup - blocking 禁用弹出拦截
--disable - plugins 禁用插件
--disable - images 禁用图像
--incognito 启动进入隐身模式
--enable - udd - profiles 启用账户切换菜单
--proxy - pac - url 使用pac代理[via 1 / 2]
--lang = zh - CN 设置语言为简体中文
--disk - cache - dir 自定义缓存目录
--disk - cache - size 自定义缓存最大值（单位byte）
--media - cache - size 自定义多媒体缓存最大值（单位byte）
--bookmark - menu 在工具 栏增加一个书签按钮
--enable - sync 启用书签同步
```
## chrome
```
from selenium import webdriver
# 进入浏览器设置
options = webdriver.ChromeOptions()
# 设置中文
options.add_argument('lang=zh_CN.UTF-8')
chrome_options = webdriver.ChromeOptions()
chrome_options.add_argument('--headless')
chrome_options.add_argument('--disable-gpu')
# 更换头部
options.add_argument(
    'user-agent="Mozilla/5.0 (iPod; U; CPU iPhone OS 2_1 like Mac OS X; ja-jp) AppleWebKit/525.18.1 (KHTML, like Gecko) Version/3.1.1 Mobile/5F137 Safari/525.20"')
# 代理
service_args = ['--proxy=94.182.202.165:8080', '--proxy-type=http']
option.add_argument('--start-maximized')  # 最大化
option.add_argument('--user-data-dir=E:\\Chrome\\User Data')  # 设置成用户自己的数据目录
browser = webdriver.Chrome(executable_path='E:\\Chrome\\chromedriver.exe',
                           chrome_options=options, service_args=service_args)
url = "https://httpbin.org/get?show_env=1"
browser.get(url)
input("查看效果")
browser.quit()
# -chrome some crx
option.add_argument('--user-agent=iphone')
option.add_extension('d:\crx\AdBlock_v2.17.crx')

```
