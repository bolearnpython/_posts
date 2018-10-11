---
title: Python 多进程与多线程
tags: 多线程，多进程
---
# Python 多进程与多线程
## concurrent
```
import concurrent                   #进程ProcessPoolExecutor

def func(nb):
    print(str(nb))
with concurrent.futures.ThreadPoolExecutor(10) as executor:
    for arg in list(range(99)):
        executor.submit(func, arg)
```
## tomorrow
```
from  tomorrow import threads

@threads(10)
def func(nb):
    print(str(nb))
for i in range(99):
    func(i)
```