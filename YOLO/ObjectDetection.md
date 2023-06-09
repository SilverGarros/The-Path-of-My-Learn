# YOLO

## Object Detection 目标检测/物体检测

ObjectDetection = What, Where

+ Localization定位->Where?

  ​	Bounding box 最小外接矩形

+ Recognition识别->What?

  1) Category label 类别标签
  1) Confidence score 置信度得分

- Single object
  - Classification 分类
  - Classification+Localization 分类定位
- Multiple objects
  - Object Detection 目标检测
  - Instance Segmentation 实例分割

定位与检测：
`定位`是找到检测图像中带有一个给定标签的`单个目标`
`检测`是找到图像中带有给定标签的`所有目标`

## 目标检测数据集

+ **PASCAL VOC**

  [目标检测数据集PASCAL VOC详解](https://zhuanlan.zhihu.com/p/362044555)

  [**![img](.\assets\v2-186906b9d87652f0b10ee9e593e0bdfb_720w.webp)**](https://zhuanlan.zhihu.com/p/362044555)    

+ [**MS COCO**](https://cocodataset.org/)

  Microsoft Common Objects in Context
  [目标检测数据集MSCOCO详解](https://zhuanlan.zhihu.com/p/362049720)

## 目标检测性能指标

1) #### 检测精度

   1) Precision, Recall, F1 score
   1) IoU(Intersection over Union)
   1) P-R curve(Precison-Recall curve)
   1) AP(Average Precision)
   1) mAP(mean Average Precision)

1) #### 检测速度

   1) 前传耗时
   1) 每秒帧数FPS(Frames Per Second)
   1) FLOPS 浮点运算量(floating-point-operations per second)

#### 检测精度

###### ConfusionMartix混淆矩阵

![image-20230609205856832](.\assets\image-20230609205856832.png)

+ **精度Precision(查准率)**是评估预测的准不准确（看预测列）
+ **召回率Recall(查全率)**是评估找的全不全 （看实际行）

![image-20230609210152060](.\assets\image-20230609210152060.png)

![image-20230609210407451](.\assets\image-20230609210407451.png)

![img](.\assets\wps1.jpg)

**An loU of 1 implies that predicted and the ground-truth bounding boxes perfectly overlap.**
You can set a threshold value for the loU to determine if the object detection is valid or not.Let's say you set loU to 0.5, in that case

+ if loU ≥0.5, classify the object detection as **True Positive(TP)**

+ if loU <0.5, then it is a wrong detection and classify it as **False Positive(FP)**

+ When a ground truth is present in the image and model failed to detect the object, classifyit as **False Negative(FN)**.

+ **True Negative(TN)**: TN is every part of the image where we did not predict an object. Thismetrics is not useful for object detection, hence we ignore TN.

AP衡量的是学习出来的模型在每个类别上的好坏
mAP衡量的是学出的模型在所有类别上的好坏。mAP就是取所有类别上的AP的平均值。
![image-20230609211118674](.\assets\image-20230609211118674.png)

###### AP（Average Precision）in PASCAL VOC challenge

对于PASCAL VOC，如果IoU>0.5，则预测为正样本(TP)。但是，如果检测到同一目标的多个检测，则视第一个检测为正样本(TP)，而视其余检测为负样本(FP)。

###### AP&mAP in COCO

![image-20230609211424377](.\image-20230609211424377.png)

![image-20230609211612094](.\assets\image-20230609211612094.png)

![image-20230609211704149](.\assets\image-20230609211704149.png)

 ![image-20230609211849793](.\assets\image-20230609211849793.png)

##### AP的计算

![image-20230609211943842](.\assets\image-20230609211943842.png)

![image-20230609212201223](.\assets\image-20230609212201223.png)

###### 11点计算AP值

![image-20230609212234922](.\assets\image-20230609212234922.png)

###### 积分法

![image-20230609212326230](.assets\image-20230609212326230.png)

![image-20230609212359361](.\assets\image-20230609212359361.png)

+ Pascal VOC2007 uses 11Recall points on PR curve.
+ Pascal VOC2010-2012 uses(all points) Area Under Curve(AUC) on PR curve.
+ MS COCO uses 101 Recall points on PR curve as well as different IoU thresholds.

#### 检测速度

+ 前传帧数(ms)：从输入一张图像到输出最终结果所消耗的时间，包括前处理耗时（如图像归一化）、网络前传耗时、后处理耗时(如非极大值抑制)
+ FPS每秒帧数：每秒钟能处理的图像数量
+ FLOPS浮点运算量：处理一张图像所需要的浮点运算数量，根具体的软硬件没有关系，可以公平地比较不同算法之间的检测速度
