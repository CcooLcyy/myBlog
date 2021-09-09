---
title: Pywin32
date: 2021-08-30 01:43:31
tags: Python
---
没接触过windows编程真的是很难搞，这些api在c++中使用的很多，微软的官方文档也都是用c/c++的头文件来写的，不过功能应该是一样的。
很多文档都是英文的，我这垃圾英语水平只能糊弄着看了，这里记录的就是当时看的理解。
格式就不用看了，因为全是C++实现
# win32api
## GetAsyncKeyState
调用函数的时候会检测一个键的状态（按下或者没按），以及这个键在上一次调用这个api的时候是否按下。
### 参数
有一个vkey，virtual-key code，就是键盘上各个键的对应代码详见[Virtual Key Codes](https://docs.microsoft.com/en-us/windows/desktop/inputdev/virtual-key-codes)。
### 返回值
1. 如果函数调用成功，则返回值取决于上次这个键上次是否调用了函数，以及这个键当前按下与否。
2. 最高有效位被设置时，按下键，最低有效位被设置时，这个键会在上次调用函数之后被按下，但是不应该以来第二种方法。

---
在以下情况会返回0值：
1. 当前窗口并非活动窗口
2. 前台线程属于其他进程，并且桌面不允许钩子或者日志记录
