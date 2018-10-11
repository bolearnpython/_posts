---
title: 注册表 pyregedit
tags: 注册表
---
# 注册表 pyregedit
## pyregedit
    import win32api
    import win32con
    import os

    # 权限设置
    REG_FLAGS = win32con.WRITE_OWNER | win32con.KEY_WOW64_64KEY | win32con.KEY_ALL_ACCESS

    #root (根节点)
    HKEY_CLASSES_ROOT = win32con.HKEY_CLASSES_ROOT
    HKEY_CURRENT_USER = win32con.HKEY_CURRENT_USER
    HKEY_LOCAL_MACHINE = win32con.HKEY_LOCAL_MACHINE
    HKEY_USERS = win32con.HKEY_USERS
    HKEY_CURRENT_CONFIG = win32con.HKEY_CURRENT_CONFIG

    # value type (值类型)
    REG_SZ = win32con.REG_SZ
    REG_BINARY = win32con.REG_BINARY
    REG_DWORD = win32con.REG_DWORD
    REG_QWORD = win32con.REG_QWORD
    REG_MULTI_SZ = win32con.REG_MULTI_SZ
    REG_EXPAND_SZ = win32con.REG_EXPAND_SZ

    class RegEdit():
        def __init__(self, root, path):
            """init method (key root, key path)"""
            self.root = root
            self.path = path

        # 判断键是否存在
        def check_key(self):
            """check key is exist or not"""
            try:
                key = self.get_key()
                key.close()
                return True
            except Exception as e:
                return False

        # 获取键
        def get_key(self):
            """get key object"""
            key = win32api.RegOpenKeyEx(self.root, self.path, 0, REG_FLAGS)
            return key

        # 获取子键名称
        def get_sub_keys(self):
            """get key's sub keys"""
            key = self.get_key()

            for item in win32api.RegEnumKeyEx(key):
                yield item[0]
            key.close()

        # 获取全部值
        def get_values(self):
            """get key's values"""
            key = self.get_key()

            try:
                i = 0
                while True:
                    # 循环枚举值
                    yield win32api.RegEnumValue(key, i)
                    i += 1
            except Exception as e:
                pass
            finally:
                key.close()

        # 根据名称获取值
        def get_value(self, value_name):
            """get value by name"""
            key = self.get_key()
            value, value_type = win32api.RegQueryValueEx(key, value_name)
            return value, value_type

        # 创建键
        def create_key(self):
            """create and return a key"""
            key, _ = win32api.RegCreateKeyEx(self.root, self.path, REG_FLAGS)
            return key

        # 创建子键
        def create_sub_key(self, sub_key_name):
            """create a sub key"""
            sub_key_path = os.path.join(self.path, sub_key_name)
            sub_key, _ = win32api.RegCreateKeyEx(
                self.root, sub_key_path, REG_FLAGS)
            return sub_key

        # 创建值
        def create_value(self, value_name, value_type=REG_SZ, value_value=''):
            """create value"""
            key = self.create_key()
            win32api.RegSetValueEx(key, value_name, 0, value_type, value_value)

            key.close()
            return True

        # 删除当前键
        def delete_current_key(self):
            """delete current key"""
            parent, key_name = os.path.split(self.path)
            key_parent = win32api.RegOpenKeyEx(self.root, parent, 0, REG_FLAGS)
            win32api.RegDeleteKeyEx(key_parent, key_name)

            key_parent.close()
            return True

        # 删除子键
        def delete_sub_key(self, sub_key_name):
            """delete sub key"""
            key = self.get_key()
            win32api.RegDeleteKeyEx(key, sub_key_name)

            key.close()
            return True

        # 删除值
        def delete_value(self, value_name):
            """delete a value item"""
            key = self.get_key()
            win32api.RegDeleteValue(key, value_name)

            key.close()
            return True
## 操作
    import pyregedit
    root = pyregedit.HKEY_LOCAL_MACHINE
    path = r"SYSTEM\CurrentControlSet\Control\Class\{4D36E972-E325-11CE-BFC1-08002bE10318}\0002"
    reg = pyregedit.RegEdit(root, path)
    #判断键是否存在
    if reg.check_key():
        #获取键(可用于其他操作)
        key = reg.get_key()
    else:
        #创建键
        key = reg.create_key()

    #创建值
    reg.create_value('NetworkAddress', pyregedit.REG_SZ, '020E2637D888')

    #创建子键
    reg.create_sub_key('sub_test')

    #获取子键名称列表
    print(list(reg.get_sub_keys()))

    #获取全部值
    print(list(reg.get_values()))

    #根据具体名称获取某个值的数据
    print(reg.get_value('NetworkAddress'))

    #删除值
    reg.delete_value('test_name')

    #删除子键
    reg.delete_sub_key('sub_test')

    #删除当前键
    reg.delete_curretn_key()

## 改mac
    import random
    def randomMAC():
        mac = [ 0x52, 0x54, 0x00,
            random.randint(0x00, 0x7f),
            random.randint(0x00, 0xff),
            random.randint(0x00, 0xff) ]
        return ''.join(map(lambda x: "%02x" % x, mac)).upper()
    import pyregedit
    root = pyregedit.HKEY_LOCAL_MACHINE
    path = r"SYSTEM\CurrentControlSet\Control\Class\{4D36E972-E325-11CE-BFC1-08002bE10318}\0002"
    reg = pyregedit.RegEdit(root, path)
    mac=randomMAC()
    #创建值
    reg.create_value('NetworkAddress', pyregedit.REG_SZ, mac)
    print(reg.get_value('NetworkAddress'))

    import shutil
    shutil.rmtree(r'C:\Users\Administrator\AppData\Roaming\Lantern')
    print ('ok')
    import requests
    r=requests.get('http://192.168.0.1/goform/SysToolReboot',timeout=4)