---
layout: post
title: OpenCV模块
subtitle: OpenCV模块
gh-repo: 
gh-badge: 
tags: [OpenCV模块]
comments: true
mathjax: true
author: yuguangguo
---

{: .box-success}

OpenCV这个计算机视觉库里其实包含多个模块，每个模块的功能还不一样。在[OpenCV安装](https://yuguangguo.com/opencv-introduction/)之后，我们应该了解常见的模块。
常见的OpenCV模块如下：
### cv2.core模块
该模块是图像处理的基础功能。
提供cv核心功能，包含矩阵操作、基本数据结构操作、绘图函数等。主要类和函数包括：
- Mat: 用于存储图像和矩阵。
- Scalar: 表示颜色或像素值；
- Point / Size / Rect分别表示点、尺寸和矩形。
- 基本绘图函数有cv.line() / cv.circle() / cv.rectangle() / cv.putText()等。 

### cv.imgproc模块
该模块是提供图像的各种操作，如滤波、几何变换、颜色空间转换等。主要类和函数包括：
- 图像滤波： cv.blue() / cv.GaussianBlur() / cv.medianBlur()
- 几何变换： cv.resize() / cv.warpAffine() / cv.warpPerspective()
- 颜色空间转换: cv.cvtColor() 
- 阈值处理： cv.threshold() / cv.adaptiveThreshold()
- 边缘检测: cv.Canny() / cv.Sobel() / cv.Laplacian() 
  

### cv.highgui模块
图形用户界面模块，包含显示图像和视频的功能，如媒体资源的输入输出，用于图像的显示和交互。
主要类和函数有：
- 图像显示： cv.imshow() / cv.waitKey() / cv.destroyAllWindows() 
- 视频捕获： cv.VideoCapture() / cv.VideoWriter() 
- 鼠标和键盘操作：cv.setMouseCallback() 

### cv.video模块
提供视频处理功能，包含视频捕捉、**运动检测、目标跟踪**视频流的处理等。
涉及到的类和函数有：
- 背景减除： cv.createBackgroundSubtractorMoG2() / cv.createBackgroundSubtractorKNN() 
- 光流法： cv.calcOpticalFlowPyrLK()
- 目标跟踪：cv.TrackerKCF_create() / cv.TrackerMOSSE_create() 
### cv.features2d模块
特征检测与匹配模块，包含了角点、边缘、关键点检测等
### cv.ml模块
机器学习模块，可进行图像分类、回归、聚类等操作。
### cv.calib3d模块
相机校准和3D重建模块。
### cv.objdetect模块
目标检测模块，提供目标检测功能
主要类和函数有：
- Haar特征分类器： cv.CascadeClassifier() 用于人脸检测
- HOG特征分类器： 用于行人检测

### cv.dnn模块
深度神经网络模块，支持加载和运行预训练的深度学习模型。
可用于图像分类、目标检测和语义分割。
主要类和函数有：
- 模型加载： cv.dnn.readNetFromCaffe() / cv.dnn.readNetFromTensorflow() 
- 前向传播：net.forward()
