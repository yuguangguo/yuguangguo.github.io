---
layout: post
title: OpenCV图像基础处理
subtitle: OpenCV图像基础处理
gh-repo: 
gh-badge: 
tags: [OpenCV图像基础处理]
comments: true
mathjax: true
author: yuguangguo
---

{: .box-success}
## 图像基础知识
了解了[OpenCV模块](https://yuguangguo.com/opencv-modules/)的相关知识，我们再看一下OpenCV图像基础处理部分的内容。注意：<br>
**<span style="color: red;">图像 = Numpy数组</span>**。

图像的属性包括以下主要3点：
- 尺寸，主要是width和height，通过**img.shape来获得所示信息的前两个数字就是图片长和宽**
- 颜色通道，一般是RGB三个通道，也可以是灰度图1个通道
- 数据类型，常见的有uint8，也可以是float32

### 读取图像(代码部分默认是import cv2 as cv)
图像的读取用cv.imread('img.jpg')，这里的图像格式用实际的格式替换。
打印出来的图像，如果是彩色图像，是3维的。


### 显示图像用以下代码
下面是显示图像的基础代码。
~~~python
cv.imshow("display window", img) #用于显示图像
cv.waitKey(0) #按键事件
cv.destroyAllWindows()  #关闭所有窗口
~~~

### 图像保存
图像保存是通过cv.imwrite()保存到特定路径。比如前面在[Opencv安装部分](https://yuguangguo.com/opencv-introduction/)提到的代码段：
~~~python
cv.imwrite("final_output", img)
~~~

### 图片复制
图片复制通过在原图添加`.copy()`实现。参考下面代码：
~~~python
import cv2 as cv

img = cv.imread("test.jpg")
duplicate = img.copy()
print(duplicate.shape)
~~~

### 图像像素改变
图像像素顺序是blue, green, red，并不是常规的RGB。
参考以下代码，查看像素改变情况。
~~~python
import cv2 as cv
from pathlib import Path

img_input = Path("D:/Opencv Tutorial/interpreter.jpg")

img = cv.imread(str(img_input))

print(img.shape)
print("-"*40)
new = img * 3
cv.imshow('new', new)
cv.imshow('original', img)
cv.waitKey(0)
cv.destroyAllWindows() 
~~~

### 图像区域（ROI，即region of interest）
所谓图像区域，其实就是我们只关心图片上的一片区域。
而这片区域有可能是：
- 人脸区域
- 缺陷区域
- 病变区域
- 车牌区域
而且，我们还可以更改图片上某一片的颜色，做法就是通过img[行数，列数] = [255, 255, 0]这样的方式进行改变。例如我们想将图片上的某个区域涂成蓝色，那么我们就可以采用以下方式：
~~~python
img_input = Path("D:/Opencv Tutorial/interpreter.jpg")

img = cv.imread(str(img_input))

roi[:] = [0, 255, 0]

cv.imshow('red dots', img)
cv.waitKey(0)
cv.destroyAllWindows()
~~~

#### **复制ROI**
复制ROI也比较简单，下面是对某个区域的复制。

请看以下代码。

~~~python
roi = img[100:300, 300:500]
dup_roi = img[100:300, 300:500].copy()
~~~

再看一下对该区域的复制，然后粘贴到别的区域。
代码如下：
~~~python
roi = img[100:300, 300:500]
dup_roi = img[100:300, 300:500].copy()
img[400:600, 600:800] = dup_roi
~~~
> 注意：这里的ROI区域操作不是复制图片，而是在原图上进行操作。有必要的话，我们需要先复制图片。
> 因为**更改图片的ROI，原图也会跟着改变。**

------------------------------------------------------------------
<details markdown="1">
<summary>下一章</summary>
[OpenCV分离和合并](https://yuguangguo.com/opencv-split-merge/){:target='_blank'}
</details>