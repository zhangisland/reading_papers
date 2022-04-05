# Overview of Screen Content Coding in Recently Developed Video Coding Standards

*Xu Xiaozhong 2021*  

这篇好难读，救


---
## 摘要
对近年发展起来的几种视频编码标准（HEVC、VVC、AVS3、AV1、EVC）的屏幕内容编码（SCC, screen content coding）技术进行了综述和比较研究。除了技术介绍，还讨论了SCC工具的性能和设计/实现的复杂性。

---
## 关键词

---
## 研究方法
### Intra Block Copy
IBC是基于块的预测技术，原理类似于图间运动补偿（MC），但本质区别在于IBC的参考样本来自当前图像（重构部分）的内部。
![Fig. 1](../pics/Xu2022-Fig1-Comparision%20of%20IBC%20and%20inter%20motion%20compensation2.png)  
被正式列入HEVC SCC。

HEVC SCC中的IBC模式设计几乎与HEVC帧间运动补偿相同，使用相同的语法结构、解码过程几乎相同。为了做到这一点，当启动IBC模式为当前图片进行编码时，在内环(in-loop)滤波过程（包括deblocking和SAO）之前，当前（部分）解码的图片被视为参考图片。这样将基于块的运动补偿和基于块的样本内拷贝统一起来。对于inter模式下的编码块，如果参考索引指向当前解码的图片，则启用IBC模式，否则使用普通的inter模式。

### Deblocking Modifications  
直观来说，deblocking机制（在块边缘使一个或多个像素平滑）对于屏幕内容可能并不太适用，因为在块内或边界经常有尖锐边缘或突然变化。据说完全禁掉deblocking操作能带来编码效益，然而deblocking滤波通常是在图片级别进行控制，这对于处理屏幕和相机混合的视频内容很困难（这是两种类型）。   

AVS3对上述问题有改进。  


---
## 实验结果

---
## Conclusion

---
## 亮点

---
## 不足/可改进
