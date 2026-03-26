---
layout: post
title: openCV安装
subtitle: openCV-python的安装
cover-img: #
thumbnail-img: /assets/img/opencv安装.png
share-img: #
tags: [openCV安装]
作者: yuguang guo
---

## openCV安装

个人一直在用VSCode来编写代码，而且有Python基础，所以比较习惯用pip来安装openCV。
有几种方法可以安装openCV。我个人使用的第二个。
- pip install opencv-python
- pip install opencv-contrib-python (opencv加其他模块)

### 激活opencv虚拟环境
输入python -m venv .venv设置虚拟环境

### 运行以下代码查看opencv版本

~~~python
import cv2 as cv
print(cv.__version__)
~~~

### 第一段opencv代码实例
请看下面这段基本代码。
~~~python
import cv2 as cv
from pathlib import Path

img_input = Path("D:/Opencv Tutorial/interpreter.jpg")
output_path = Path("D:/Opencv Tutorial/edited images")
output_path.mkdir(parents=True, exist_ok=True)


img = cv.imread(str(img_input))
if img is None:
    print("the image doesn't exist")
    exit()
else:
    img = cv.imshow("interpreting in the conference room", img)
    k = cv.waitKey(0)
    if k == ord("s"):
        final_output = output_path/"guoyuguang.jpg"
        cv.imwrite(str(final_output), img)  #这行代码也容易忘记
    else:
        print("the image unsaved!")
cv.destroyAllWindows() #这行代码容易忘记，功能是关闭窗口疼出内存。
~~~