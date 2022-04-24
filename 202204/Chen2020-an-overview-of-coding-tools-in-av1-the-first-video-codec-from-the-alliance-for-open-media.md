# 文献精读2022-04-05

## 文献信息

**标题：An overview of coding-tools-in-av1-the-first-video-codec-from-the-alliance-for-open-media**

**DOI(url):https://doi.org/10.1017/ATSIP.2020.2**

**发表日期：2022-02-24**

**发表杂志：APSIPA Transactions on Signal and Information Processing**

**关键词：Video compression, Open-source video coding, AV1, Alliance for Open Media**

## 文献概述
AOMedia旨在开发一个性能超越现在最先进的视频编解码器的、开源免版权的、保持实际的解码复杂度，同时对硬件适用性和现代设备的可伸缩性进行优化，基于此推出了AV1编解码器。  

本文对AV1的关键技术进行了综述，同时将libaom AV1的编码性能测试结果与libvpx VP9的进行了验证，还在AOM的测试集与公开4k数据集上对HEVC（x265和HM）和VVC的参考软件进行了比较。  

AV1成型于2018年底，包含了许多新的压缩工具、高层句法以及为特定用例的并行化特点。  

libaom通过机器学习支持的搜索空间修剪和提前终止(machine learning powered search space pruning and early termination)实现了大幅的加速，以及自适应量化(adaptive quantization)和改进的未来参考帧生成/结构(future reference frame generation/structure)实现了额外比特率的节约。  

## 文献笔记
1. 提到了多种基于AV1的编解码器，包括 AOM/Google 维护的 libaom，AOM/Intel 维护的 SVT-AV1，Google 推出的尤其面向 Android 设备的 libgav1，以及由 VideoLAN、FFmpeg 开源社区维护、AOM 资助的 dav1d。

2. AV1的调色板中的颜色索引在熵编码中采用基于邻域的上下文(the neighborhood-based context).  

3. AV1有基于机器学习的变换模式快速决策  

4. 基于帧距离的复合预测：帧距离指绝对时间差（时间戳）


5. 变换编码中的IDTX(identity transform)，可以跳过变换


6. IBC的块矢量为什么必须是整像素精度，因为屏幕内容是整像素精度  


### **文章亮点**

### **和我相关**
还要进行libaom AV1 与 SVT-AV1的比较  

帧内块拷贝：如何得知是相同的文字(字符)

### **我的疑问**

## 相关文献