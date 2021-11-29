---
title: Python
date: 2021-08-28 17:39:54
tags: Python
---
# 字符串

使用单引号或者双引号可以表示一个字符串。

```python
# 单双引号都可以用来表示字符串
s1 = 'hello, world'
s2 = "hello, world"
# 使用三个引号可以直接编辑多行字符串
s3 = '''
hello,
world
'''

print(s1, s2, s3)
```

## 转义字符

也就是反斜线`\`根据转义字符的不同进行不同的转义，这一点和C语言中的转义字符相同。

在python中如何不想使用转义字符可以在字符串之前加入`r`

```python
s1 = r'\nhello, world'
s2 = r"\n hello, world"

print(s1, s2)
```

## 字符运算

我们可以使用`+`和`*`对字符进行连接和重复。使用`in`和`not in`来判断一个字符串是否在另一个字符串中。

使用`[]`和`[:]`进行切片，切片相当于复制了一个字符串进行操作。`[start:end:step]`，从start开始到end-1结束，步长为1。

同样我们可以将步长改为-1，这样相当于倒序来复制数组。需要注意的是结束的地点为end-1，也就是说`[0:3:1]`，意味着从头开始到3-1的位置停下，每次移动1个，如果是从0到10排列的字符的话，以上分片就可以产生一个0，1，2的字符
如果start或者end中使用的是负数的话代表着倒数第几个，同样end也需要减一。

## 字符索引

字符串中可以使用类似数组的索引方式，但是不能改变字符串
```python
str = 'henny'
str[0] = 'p'
# 以上操作被禁止
```
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

## 字符操作（方法）

在字符串中的方法都是以点操作符进行使用的。

### join

1. 参数：内容是字符串的任何容器。字符串、数组、元组等等。

```python
insertStr = ','
targetStr = '123456'
result = insertStr.join(targetStr)
print(result) #1,2,3,4,5

insertStr = ','
targetStr = ['1','23','4','5','67']
result = insertStr.join(targetStr)
print(result) #1,23,4,5,67
```

可以使用插入字符依次插入每一个目标字符或者容器中。

### 大小写切换方法

这之中的所有方法都会获得的一个字符串的复制，也就是并不修改原先的字符串，以第一个开头大写为例。

1. capitalize()：参数无，获得字符串开头大写的字符串的复制（并不修改原先的字符串）

```python
str1 = 'hello, world'
result1 = str1.capitalize()
str2 = 'hello, ' + 'world'
result2 = str1.capitalize()

print(result1) #Hello, world
print(result2) #Hello, world
print(str1) #hello, world
print(str2) #hello, world

```

2. title()：参数无，将字符串中每个单词的开头都变为大写字符。
3. upper()：参数无，将字符串中所有的字符都变为大写字符。
4. lower()：参数无，将字符串中所有字符变为小写。

### startswith()和endswith()

参数：字符串

分别检查字符串中是否以指定的字符串开始或者结尾。

# 变量

尽量让变量作用在局部，防止对象长期占用内存导致垃圾无法回收。

如果想在函数结束之后依然能够使用它的值可以使用闭包。

## 变量的作用域

在哪里定义就作用在哪里，如果不在函数或者类中定义就定义为全局变量

# 循环控制流
在循环当中也有一些用法，比如说提前终止`break`和跳过本次循环，进行下次循环，但不终止循环的`continue`
## for循环
使用`for...in`循环如果明确知道要循环的次数，或者是需要对一个容器进行循环的时候我们可以使用这种循环方式。
## 使用while循环
如果并不明确知道应该循环的次数，但是有一个终止循环的条件的话，可以使用`while`循环，当条件判否的时候循环便终止。

# 列表（数组）
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
# 函数
在python中没有重载函数，也就是不能定义两个一样名字但是功能不同的函数。
函数同名的时候可以放入模块中分别调用。在调用模块的时候如果不仅有函数还有一些代码行的时候，可以使用
```python
def foo():
    pass
    
if __name__ == '__main__':
    do something
```
只有当单独运行文件时，名字才会是`__main__`，如果传入其他文件中作为模块的时候名字为其文件名。
# 内置函数

## len函数

这个函数返回容器的长度，比如数组、字符串。

## zip函数
将可迭代元素作为参数将参数打包成一个元组。如果每个迭代器的元素个数不相同，那么返回的长度与最短的对象相同。
```python
zip([iterable, ...])
```
在python3中返回值是一个对象，如果要显示可以使用`list(zipped)`。这时我们要将转换之后的对象解包可以使用`zip(*)`，但是解包之后返回的是元组，如果我们将数组zip操作，会返回一个元组，我们可以通过如下方法将元组转换数组。
```python
a = [1, 2, 3, 4]
b = [5, 6, 7, 8]

zipped = zip(a, b)
a1, a2 = zip(*zipped)
a1, a2 = list(a1), list(a2)

print(a1)
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
但是在打包好之后，如果源代码中有需要的外部文件，就算打包成了一个程序也要将文件放入对应的根目录下，否则会出现资源的缺失。比如说在源文件中需要图片，打包之后并不会将图片直接打包进程序，因此需要将图片放入到对应目录下。
| 参数 | 用途                            |
| --- | ------------------------------ |
| -F   | 只生成一个exe文件               |
| -D   | 会生成许多lib文件，这是默认选项 |
| -c   | 显示控制台，默认选项            |
| -w   | 不显示控制台                    |
| -i   | 改变生成程序的icon图标          |



