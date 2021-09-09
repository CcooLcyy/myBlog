---
title: keras
date: 2021-08-30 00:01:46
tags: AI, Python
---
# Sequential顺序模型
将网络层实例传递给Sequential构造器，创建一个顺序模型
```python
import keras

model = Sequential([
	Dense(32, input_shape(784,)),
	Activation('relu')
	Dense(10),
	Activation('softmax')
])
```
或者使用add来添加各层到模型中
```python
import keras

model = Sequential()
model.add(Dense(32, input_shape = (784, )))
model.Activation('relu')
```
## 数据的尺寸
在第一层需要输入尺寸，其他层可以自动推算尺寸方法如下：
1. 传递`input_shape`参数给第一层，这是一个由整数组成的元组，None可以表示任何数，并且不包含batch的大小
2. Dense之类的二维层可以使用`input_dim`，指定输入尺寸
3. 指定batch大小的时候，可以传递`batch_size`参数给第一个层，如果同时传递`input_shape(6, 8)`和`batch_size = 32`时，输入的尺寸会变为(32, 6, 8)
当传递一维层的时候`input_shape = (784,)`时与`input_dim = 784`作用相同，代码等价
## 在训练之前的配置
我们需要配置学习的过程，这个方法通过`compile`方法实现，参数如下：
1. `optimizer = 'rmsprop'`优化器，传入的是字符
2. `loss = 'mse'`损失函数，传入字符，或者时目标函数
3. `metrics = ['accuracy']`，评估标准，传入一个列表，也可以自定义评估函数
### 将标签转换为one_hot编码
```python
labels = keras.utils.to_categorical(labels, num_classes = 10)
```
## 进行训练
在数据和标签的numpy矩阵上进行训练，使用`fit`函数，`model.fit(data, labels, epochs = 10, batch_size = 32)`，每32个数据为一捆进行迭代，次数10次
# 函数式API

