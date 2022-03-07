# Abstract
HVS：human vision system
基于人眼视觉系统的

利用HVS模型降低相同质量下的视频比特率。
视觉掩蔽模型可被用于准确描述HVS，视觉上无法区分且无需编码的频率将在可见性阈值内移除。

# 1 Introduction
去除感知冗余和适应现实场景的感知优化一直是视频压缩领域的一个活跃领域。


滤波器

HVS模型有助于准确测量人眼看不到的内容，用于估计失真信号和原始信号之间的可见度差，然后进行计算处理，去除冗余。
包括以下元素：计算绝对亮度的非线性灵敏度（non-linear sensitivity to calculate absolute luminance），对视觉频率的对比度灵敏度（contrast sensitivity to visual frequencies）、倾斜效应和视觉通道的子带分解（oblique effect and sub-band decomposition into visual channels）、掩蔽效应（masking effect）、心理测量功能和误差池（psychometric function and error pooling）

使用以上工具在可见性阈值内从源视频中删除或添加信息。

冗余信息可以从JND内的源中移除，以执行预处理算法。

