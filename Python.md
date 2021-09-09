---
title: Python
date: 2021-08-28 17:39:54
tags: Python
---
# 字符
字符串中可以使用类似数组的索引方式，但是不能改变字符串
```python
str = 'henny'
str[0] = 'p'
# 以上操作被禁止
```
不过我们可以使用你分片来改变字符，其实就是创建一个副本，索引的方式与数组也是一样的
`str[::]`，这里的方括号分别是`[start:end:step]`，从start开始到end-1结束，步长为1。
同样我们可以将步长改为-1，这样相当于倒序来复制数组。需要注意的是结束的地点为end-1，也就是说`[0:3:1]`，意味着从头开始到3-1的位置停下，每次移动1个，如果是从0到10排列的字符的话，以上分片就可以产生一个0，1，2的字符
如果start或者end中使用的是负数的话代表着倒数第几个，同样end也需要减一。
使用`len()`来获取长度，也就是个数。这个函数是个广义函数，可以在字符串中使用，也可以在数组或者其他地方使用。
使用`join()`进行合并，这个函数只能在字符串中使用，因此使用的方式是
```python
str = ','
str.join()
```
使用你str中的字符串来连接join后面的数组。
使用`split()`来分割字符串。在`split()`中传入的字符串是字符串中的符号，以这个符号位标准来分割字符串，将字符串变为一个列表。如果不指定分隔符，则默认使用空格，换行符制表符来分割。
使用`replace()`继续替换，这也是只能在字符串中使用的函数，这个函数传入三个参数，分别是：
1. 用于替换的字符串
2. 被替换的字符
3. 替换的字符个数

# 列表
有两种方式创建列表
```python
empty_list = []
empty_list = list()
```
将其他数据类型转换位列表，使用`list()`进行转换
```python
str = list('cat')
a_tuple = ('1', '2', '3')
list_tuple = list(a_tuple)
```
在列表的切片中，如果只有一个冒号，则表示冒号前为开始位，后位结束如，当有两个冒号的时候，第二个冒号后面的才是步长
使用`append()`添加元素到列表的最后
使用`+=extend()`连接两个列表，

```python
list_1 += list_2
list_1.extend(list_2)
```
使用`insert()`在特定位置插入元素，传入两个参数，第一个是位置，第二个是要插入的元素。
`del`是python中的函数，并不是列表的特有函数，因此，在使用此函数删除元素的时候
```python
del list[3]
```
这个函数会进行索引删除，还有一个`remove()`函数会特定删除，也就是删除作为参数的元素
```python
list.remove('removed')
```
使用`pop()`会删除元素，如果不指定的话会删除最后一个元素，在删除之后这个方法会返回被删除的元素
```pythonn
removed = list_1.pop(3)
```
## 打乱原列表的顺序
```python
from random import shuffle

arr = [i for i in range(1, 11)]
shuffle(arr)
```

# 系统

在os模块中提供了许多关于系统的函数，导入这个模块来使用

## 文件

### 创建文件与删除文件

使用open来创建一个文件，并且使用close关闭这个文件。

```python
file = open('oops.txt', 'wt')
file.close()
```
当文件创建之后可以使用`remove()`来删除文件
```python
import os
os.remove()
```
### 检查文件是否存在
使用`exitsts()`来检查文件是否存在，本级目录和上级目录都可以检查，并且都存在
```pythonn
os.path.exists('oops.txt')
```
### 检查是否为文件，目录，是否是绝对路径
这些函数都在`os.path`下，使用的时候要
```python
os.path.isfile()
```
使用`isfile()`来检查是否一个文件。
使用`isdir()`来检查是否是目录。
使用`isabs()`来检查是否是绝对路径
上述函数都需要传入一个字符串
### shutil模块
`copy()`函数来自`shutil`模块中，在使用的时候需要导入此模块
```python
import shutil
shutil.copy('oops.txt', 'ah.txt')
```
将oops.txt复制到ah.txt，第一个参数复制到第二个参数中

`move()`这个函数会删除源文件，并且复制一个文件
`rename()`将文件重命名
### 获取路径
`abspath()`将相对路径扩展为绝对路径
`realpath()`如果创建了符号连接，使用此函数会获取到符号连接的真实路径
## 使用enumerate生成索引序列
将一个可遍历的数据结构传入函数，返回索引和值，值是每个可遍历结构的值。当使用`[start = ]`参数的时候可以指定开始的索引，比如`[start = 1]`，将从1开始将进行索引
```python
arr = [range(1, 11, 1)]
for count, value in enumerate(arr):
	print(count)
	print(value)
```
## 错误与异常处理
使用`try:`来测试程序，如果没有发生异常，则在执行完try之后就结束程序，如果发生异常，则根据异常执行`except`中的程序。
# 生成二进制文件
要想让没有安装python的用户使用程序，需要生成一个二进制文件，这里使用python的`pyinstaller`生成。
首先需要安装pyinstaller,`pip install pyinstaller`，之后使用`pyinstaller file.py`进行封装。在封装的时候使用`-w`可以在运行的时候不显示终端，使用`-F`可以只生成一个文件，这样在文件中不会有其他的lib。
| 参数 | 用途                            |
| --- | ------------------------------ |
| -F   | 只生成一个exe文件               |
| -D   | 会生成许多lib文件，这是默认选项 |
| -c   | 显示控制台，默认选项            |
| -w   | 不显示控制台                    |
| -i   | 改变生成程序的icon图标          |



