# High Frame Rate Screen Video Coding for Screen Sharing Applications

*Dan Miao 2014*  

---
## 摘要
在本文中，我们提出了一个高帧率的屏幕视频压缩方案，旨在改善屏幕共享应用程序的交互用户体验。所提出的屏幕视频压缩采用两层编码:使用传统视频编解码器的基层编码和使用所提出的开环编码方案的增强层编码。为了有效的帧级层选择和压缩，通过全局运动检测来评估每一帧的内容更新。具有显著内容更新的屏幕帧在底层馈送给传统的视频编码器。增强层对更新较少的帧进行压缩，其中重复的内容用全局运动矢量和跳跃标记表示，更新后的内容则根据其固有的局部特征用不同的内模式编码。实验结果表明，对于包含交互的屏幕视频，所提出的编码方案可以达到3.09ms/帧编码率和2.33ms/帧解码率，并具有有效的码率失真性能。  

---
## 关键词
NULL  

---
## 研究方法
正如我们所知，标准视频编解码器被广泛应用于许多视频传输系统中，因为它得到了软件(如X264、FFMPEG、MSFT)和硬件等优化实现的良好支持。虽然在硬件加速下可以实现实时编解码，但由于混合编码框架的高复杂度代价，对于更高的帧率编码仍是一个挑战。此外，屏幕视频包含大量的文本/图形内容，具有很强的各向异性特征，而基于变换的视频编码方案不能很好地处理各向异性相关性。  

对于不运动的稳定区域，将当前的块内容与原帧中同位置的块内容进行比较。如果没有区别，则将该块设置为skip块。为了检测受全局运动影响的块，我们采用了基于特征检测和映射[9]的全局运动检测算法。唯一且容易识别的特征首先在当前块中被扫描，然后在前一帧中搜索匹配特征点，并围绕该特征点扩展匹配块。如果当前块与匹配块相同，则识别为块间inter block，记录运动矢量。除以上两种情况外，其他块均视为有新内容更新的内块intra block。  

在此基础上，我们将内块分为三种类型:文本/图形区域、图像边缘区域和图像平滑区域。在实现中，首先量化内部块，如下所示。选取直方图值峰值的颜色作为基色。然后，在直方图中使用大小相等的窗口将主要颜色附近的颜色聚类。窗口中的所有像素都量化为同一窗口中的基本颜色。的确，一些像素可能会从集群窗口中逃逸出来。如果转义像素的数量在一个阈值内，则该块将被视为文本/图形块。否则它就是一个图像块。或基于每个块的梯度值的边缘区域块，梯度值是相邻像素之间的绝对差值的和。如果超过阈值，则认为该块为边缘区域块。否则为平滑区域块。  

对于所有YUV信道，文本/图形区域内的块采用像素域编码。量化后，块可以用索引图和其余转义像素的基本颜色表示。每个块的基色是由前一帧对应的基色进行预测后的熵编码。索引映射和转义像素使用可变长度编码进行压缩。与文本/图形内容相比，基于变换的编码方案使图像部分的边缘更加规则，并能有效地利用空间相关性。因此，采用基于JPEG的intra编码对图像进行分块压缩。考虑到色度下采样引起的色差，对边缘图像区域的三个YUV分量进行编码，不进行下采样。为了有效的表示和压缩，在压缩前对平滑区域的色度通道进行水平和垂直两个方向的下采样。  

---
## 实验结果
对于典型的屏幕视频（Bing， Amazon， pdf-editing），在较宽的比特率下，提出的方案比x264和参考方案能获得更好的R-D（速率失真，rate-distortion）性能。

---
## 亮点  
将典型图形/文字与自然视频分开处理，转到增强层编码，有效提升帧率。  

对于典型的屏幕视频（Bing， Amazon， pdf-editing），在较宽的比特率下，提出的方案比x264和参考方案[8]能获得更好的R-D（速率失真，rate-distortion）性能。 

帧级选择算法：

---
## 不足/可改进

---
## Conclusion
在本文中，我们提出了一种分层压缩方案来实现屏幕视频的高帧率编码。为了降低编码复杂度，提出了**帧级选择算法**，并采用设计的编码方式对内容更新少的屏幕视频帧进行高效编码。仿真结果表明，该方案能够实现高帧率编码，并具有高效的RD性能。  

