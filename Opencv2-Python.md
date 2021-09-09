---
title: Opencv2-Python
date: 2021-08-28 20:59:54
tags: Python
tags: OpenCV
---


cv有1和2，这里记录cv2的使用，导入的时候`import cv2`，如果想导入cv1`import cv2.cv`。
# 基础知识
## 读写图像
```python
import cv2
im = cv.imread('image.png')
h, w = im.shape[:2]
print(h, w)
```
以上的代码导入了cv2的包，并且读入了一张image.png的照片，读入的方式是通过numpy数组，赋值给im，获取数组前两个元素也就是高和宽，打印出这两个元素。
```python
cv.imwrite('result.png', im)
```
将im作为图片保存到`result.png`中
## 颜色空间
图像是按照BGR的顺序存储，并不是传统的RGB顺序。不过我们有一些转换函数可以使用
```python
im = cv2.imread('image.png')
gray = cv2.cvtColor(im, cv2.COLOR_BGR2GRAY)
```
将原图像保存为灰度图
## 显示结果
`cv2.imshow('title', im)`使用这个可以实时显示图像，在运行时的图像。
### waitkey()函数
`cv2.waitkey()`参数为`delay = None`，这个参数是延迟。
参数为0表示无限等待，在图像的时候通常设置为0，这样的意思可以理解为按下任意键继续的意思，但是在显示视频的时候不能设置为0，因为会在第一个视频帧一直等待输入，视频不会播放。
在传入视频的时候，一定要设置为大于零的数，这样就会不断的显示下一个视频帧，这个数字是等待时间，单位是毫秒，如果`cv2.waitkey(10)`，表示等待10ms的输入，10ms之后没有输入就会显示下一个视频帧。
这个函数的返回值是输入的按键。
```python
key = waitkey(10) # 延迟为10ms，没有输入显示下一个视频帧
if key == 27: # ESC的ASCII码为27
	break	# 中断显示，也就是退出窗口
if key == ord(' '): # 如果输入的是空格就是执行操作
	cv2.imwrite('cap.jpg', im)
```
27是ESC键的ASCII码，按下ESC就可以退出窗口，按下空格键就可以保存图像。
## 处理摄像头
使用`cap = cv2.videoCapture(0)`来捕获视频，通过一个整数进行初始化，这个整数时计算机上连接的摄像头，从0开始计数。
捕获视频之后使用`read()`方法解码视频并返回下一帧，`ret, im = cap.read()`，`ret`是判断视频帧是否读入成功，第二个则是实际的图像数组。
```python
import cv2

cap = cv2.VideoCapture(0)
while True:
  ret, im = cap.read()
  cv2.imshow('video', im)
  key = cv2.waitKey(1)
  if key == 27:
    break
  if key == ord(' '):
    cv2.imwrite('result.jpg', im)

```
获取摄像头的视频， 并且按ESC退出，按空格保存截图为`result.jpg`。
