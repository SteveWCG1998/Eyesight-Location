# Eyesight-Location简介
本程序主要目标是在智能眼镜使用场景下，通过智能眼镜处理所得的视频判断视频中人眼注释点在屏幕上的实际位置。主程序主要由三部分构成分别是视频逐帧处理程序，图像修正程序，视点定位程序。

# 2021.1.3 v0.1 更新日志
本次完成了EL程序的基本架构，实现了三部分的基本功能，完成了修正后识别误差率低于10%的目标，初步实现了批处理的功能，在Video文件夹导入相关的视频通过运行本程序可以实现对于视点在屏幕上位置的定位和视点大小的估算，但是在第一版本实现之中也存在着较多的问题，比如在视频修正的过程中没有添加异常值检测和处理的功能，导致了在修正过程中部分图片会出现较大的偏差，导致修正失败。同时批处理的过程中仍然利用预设的文件夹，没有添加temp文件夹的生成和销毁步骤，在程序运行的时间复杂度上也没有进行相应的优化，导致处理时间过长，大约300张图片的处理时长在2min左右，面对大量视频输入逐帧分析的方法不仅影响时间复杂度，大约两倍于输入视频大小的临时文件也会对空间复杂度具有较大的影响。最重要的一点，由于图片修正出现的问题，导致数据写入过程出现问题（缺少参数，部分内容无法写入导致程序中断），目前没有实现将逐帧数据写入到txt文件中

·技术要点
目前主要应用了opencv中的二值化处理+高斯滤波+边缘提取+透视变换等功能，提取屏幕范围，并利用现下流行的通过四个象限找离中心点最远距离点来定位角点的方式完成屏幕四点的定位，进而完成后续的透视变换，同时，利用了opencv中的视频处理功能，完成了逐帧内容的提取，同时，利用霍夫变换识别圆形并定点圆心，达到了识别的根本目的。

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

