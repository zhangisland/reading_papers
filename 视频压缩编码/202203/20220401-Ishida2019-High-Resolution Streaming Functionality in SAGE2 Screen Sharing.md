# High-Resolution Streaming Functionality in SAGE2 Screen Sharing

*Kazuya Ishida 2019*  

---
## 摘要
在Tiled Display Wall(TDW)上可视化是在研究员之间共享大量科学数据的一种有效方式。SAGE2(Scalable Amplified Group Environment)是组织多个显示器的内容到TDW的一个中间件，SAGE2能提供屏幕共享的功能，但是，当前共享屏幕中存在这样的问题：它与连接到用户PC的显示器设备的分辨率有差距，这种不足降低了科学数据的可视化性能。  

本文将帧流技术结合到屏幕共享，以实现高分辨率流的功能。

---
## 关键词
Visualization, Tiled display wall, SAGE2, Screen sharing  

---
## 研究方法
主要讨论的背景是合作的科研项目中不同研究院远程共享实验数据，需要高分辨率。  
为了更好地在TDW中（可视化）共享数据，本文讨论了已开发的中间件，包括SAGE2、GGLX（cross platform cluster graphics library）、DisplayCluster。因为SAGE2支持本地和远程联机共享屏幕，而且不需要调用特定的API改变源码再编译（即非侵入式地利用已有的应用程序），所以应用更广泛。  

问题在于在TDW上的应用程序窗口不能以任意分辨率进行显示，因为它需要在用户PC上捕捉视频帧然后传输到TDW，而这些视频帧的分辨率由用户PC的帧缓冲区大小决定，而帧缓冲区大小与硬件设备有关，所以如果显示屏支持的分辨率比TDW低，那么在TDW上显示的应用程序窗口的分辨率也会降低。  

本文提出的帧流方法允许通过屏幕共享显示高分辨率的应用程序窗口，而不受限于显示设备的配置，并在一定程度上提高了帧率。  

SAGE2 is cloud and web-browser-based technology, which is implemented with HTML5, JavaScript and WebGL.  

A SAGE2-based TDW consists of three components: the display clients(web page), the interaction client and the SAGE2 server(web server).  

SAGE2通过web API实现的屏幕共享目前有两个问题：分辨率限制和变换延迟。  

1. 分辨率限制：当用户PC和TDW的像素数相差过大，就会影响应用程序的可视度。问题就在于：如何在用户PC上使可变的framebuffer不受硬件设备限制。  
2. 




---
## 实验结果

---
## Conclusion

---
## 亮点

---
## 不足/可改进
