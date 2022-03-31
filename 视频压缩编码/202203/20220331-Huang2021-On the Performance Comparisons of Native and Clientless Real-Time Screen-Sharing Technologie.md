# On the Performance Comparisons of Native and Clientless Real-Time Screen-Sharing Technologies

*Huang ChunYing 2021*  

---
## 摘要
在本文中，我们研究了不同的屏幕共享技术的性能，它们可以分为本机和无客户端技术。原生软件要求用户安装特殊用途的软件，而无客户端软件则直接在网络浏览器中运行。  

特别是，我们在三个步骤中进行了广泛的实验。首先，我们确定了一套最具代表性的本地和无客户端屏幕共享技术。其次，我们提出了一个系统的测量方法来比较屏幕共享技术在不同和动态网络条件下使用不同的性能指标。最后，我们进行了广泛的实验，并进行了深入的分析，以量化无客户端和本地屏幕共享技术之间的性能差距。我们发现基于webrtc的实现实现了最好的整体性能。更准确地说，它在达到高译码率和提供良好的视频质量的同时，最大消耗3mbps带宽。在动态网络条件下，该算法具有稳定的高译码率和视频质量。通过首次对本地和无客户端屏幕共享技术进行严格的比较，本文将对新兴的无客户端屏幕共享技术进行更令人兴奋的研究。  


---
## 关键词
Live video streaming, real-time encoding, measurements, performance evaluations, performance optimization  

---
## 研究方法
首先，我们调查了有代表性的屏幕共享技术，它们大致可以分为两组:(i)本地的和(ii)无客户端的。本地技术要求用户在客户端安装专用软件;典型例子包括RDP (Remote Desktop Protocol)[24]、VNC[32]、GA (GamingAnywhere)[18]。无客户端技术利用网络浏览器来避免软件安装，实现更好的可移植性;典型例子包括FFmpeg[10]、noVNC[24]、WebRTC[40]。  

VNC、noVNC和RDP在网络条件不完善的情况下，容易出现时延变长、视频质量下降、解码率降低等问题。  
当丢包率较大时，GA的视频质量和解码率较低。  
WebRTC是在恶劣的网络条件下最健壮的技术，这可以归因于其内置的错误恢复机制。在最具挑战性的网络条件下，WebRTC的性能优于所有其他考虑的技术:它实现了更低的带宽消耗(< 3mbps)，更高的视频质量(峰值信噪比> 27db)，以及更高的解码率(>86%)。在动态网络条件下也可以观察到类似的优点。  

因此，对于大多数应用程序和使用场景，我们建议使用无客户机的WebRTC[40]。唯一的例外是:(i)网络带宽充足或(ii)需要极低的延迟。对于前一种情况，Chrome和Firefox现有的WebRTC实现在消耗更多的网络带宽以获得更高的视频质量方面还不够积极，这可以通过增加它们的速率控制算法来解决。对于后一种情况，由于web浏览器的额外延迟在编写时仍然太高。因此，我们推荐GA[18]，这是一种为云游戏和其他高度交互的应用程序量身定制的本地屏幕共享技术。  

他们的观察表明，在更静态的场景中，RDP和VNC消耗更少的资源;GA以更高的带宽消耗换取更短的延迟。这是意料之中的，因为GA是为云游戏设计的。  

屏幕共享技术可以测量当前网络的状况，如网络带宽、往返时间和丢包率，以更好地适应网络动态。也就是说，在糟糕的网络条件下，接收方通知发送方发送低质量的视频，以避免延迟和丢失包，以便顺利播放。例如，VNC客户端在接下来的几个帧中周期性地发送更新请求。因此，客户端可以根据当前的网络情况调整请求的频率。WebRTC还可以测量网络状况，并动态地打开/关闭前向纠错(FEC)，以获得更好的容错能力。最后，一些屏幕共享技术以反向通道发送用户输入。击键、鼠标移动、鼠标点击、惯性和其他传感器读数被输入处理器捕获并发送到服务器上的输入播放器。服务器将这些输入回放到应用程序。输入通常具有相当低的比特率，但需要可靠地交付。因此，输入主要通过TCP协议发送，这可能与视频/音频包不同。  

> GamingAnywhere (GA)是一个具有高扩展性、可移植性、可重构性和开放性的云游戏平台。它支持libavcodec库[18]中的几个视频/音频编解码器。  


我们在视频流化之前将帧号嵌入到视频中，以使客户端捕获的帧与服务器捕获的帧相匹配。  
因此，我们在下面提出了我们自己的颜色代码。我们提出的彩色码借用了QR码的本地化方法，但只编码很少的信息位，从而引入了高冗余。更具体地说，每个图案都用一个8位颜色填充，其中每个RGB组件编码两个可能的值:最小值(0)或最大值(255)。因此，每个颜色代码可以是23 = 8个可能值中的一个。考虑到测试视频的长度，我们决定使用5种颜色代码来表示帧号。为了进一步增强健壮性，我们添加了第六个颜色代码来对校验和进行编码。  

我们在每个颜色代码的中心周围定义一个感兴趣区域(Region-of-Interest, RoI)，并将感兴趣区域中最常出现的颜色转换为八进制数字。  

---
## 实验结果

---
## Conclusion

---
## 亮点

---
## 不足/可改进
未来的研究方向可能会解决上述两个局限性。例如，WebRTC可以使用更多的自适应编解码器，在理想的网络条件下利用可用带宽，以获得更好的屏幕共享性能。此外，针对云游戏提出的各种延迟减少机制，如基于图像的翘曲[35]和零缓冲机制[18]，可以集成到快节奏的游戏和WebRTC api中，实现极低的延迟。此外，可以设计更全面的测量实验来研究智能自适应算法。实验结果可以为进一步优化不同网络条件下不同应用和异构客户端(包括桌面和移动设备)的屏幕共享技术提供更多的见解。除了视频，音频流的性能也很重要，对于某些特定的应用程序(如游戏和电影)，值得评估。这是我们未来的方向之一。我们坚信，本文将激发出许多令人兴奋的工作，从而使无客户机屏幕共享技术适用于在更多样化的网络条件下的更交互式的应用程序。  

Several future research directions may address the above two limitations. For example, more adaptive codecs can be used in WebRTC to capitalize the available bandwidth in the ideal network condition for better screen-sharing performance. Besides, various latency reduction mechanisms proposed for cloud gaming, such as image-based warping [35] and the zero-buffering mechanism [18], can be integrated into fast-paced games and WebRTC APIs to achieve extremely low latency. Furthermore, more comprehensive measurement experiments can be designed to investigate the intelligent adaptation algorithms. The experiment results may provide more insights to further optimize the screen-sharing technologies for different applications under diverse network conditions and heterogeneous clients (including desktops and mobile devices). In addition to video, the performance of audio streaming is also important and worth to be evaluated for some particular applications, such as games and movies. This is one of our future directions. We firmly believe that this article will stimulate many exciting works, which in turn make clientless screen-sharing technologies applicable to more interactive applications under more diverse network conditions.