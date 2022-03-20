# Abstract
HVS：human vision system
人类视觉系统

利用HVS模型降低相同质量下的视频比特率。
视觉掩蔽模型可被用于准确描述HVS，视觉上无法区分且无需编码的频率将在可见性阈值内移除。

**Luma**：代表着图片的亮度
**chrominance**：图片的色度
对于无色图像，luma代表亮度，chroma代表色度（色彩信息），从而将RGB源转换成luma和chroma，用于色度二次采样（因为相对色度差，人眼对亮度差更敏感），视频系统可以以较低的分辨率存储和传输彩色信息，从而优化特定带宽下的感知细节。

**滤波器**：去除信号中不想要的成分或增强所需的成分。

这篇论文主要是提出了一种新的感知预处理滤波器HVSPP（Perceptual Pre-Processing），该滤波器将这种HVS模型用于Luma，并将自适应低通滤波器用于JND阈值内的色度。

**JND**：可认为是一种评估方法，在同一JDN等级范围内，人眼会认为其图像几乎无差别。

**CSF**：contrast sensitivity function。

**Luma工作流程**：在Luma组件的预处理步骤中应用了不同的HVS工具，在基于形态学运算的滤波器中应用了色度分量，再对最终的HVSPP信号进行编码，而不是源信号。

HVSPP算法以分块方式进行，以实现硬件目标。
1. 将亮度块转换为物理亮度值（这篇用的${cd/m^2}$为单位，衡量发光强度的，$1\ nit=1\ cd/m^2$）
2. 计算视觉通道模型（模仿人眼模型的亮度，我感觉是仿真人眼，包括一些眼内的光散射、光受体灵敏度等等）
3. 通过可控制金字塔的多尺度表示 分解视觉通道模型（为了避免在实值金字塔中引入重构误差，遂采用可控制金字塔的复杂表示）
4. 计算每个比例和方向的对比度遮罩
5. 对在每个尺度和方向上计算的对比度掩蔽进行归一化计算
6. 将以上应用于亮度的多尺度分解
7. 在每个尺度和方向上预处理块被重建回亮度和色度
![[Pasted image 20220307222801.png]]
在每个频带中可以去除的总体信息被建模为信号相关噪声（神经噪声{nMask}）和信号无关噪声（视觉掩蔽{CSF}）的总和。
与信号无关的噪声是CSF。

${Barten's\ CSF\ model:\ \rho 以周期每度为单位的空间频率，p_1到p_3是适应光强度的拟合参数}$
![[Pasted image 20220307232513.png]]

# HVS Tools
HVS模型有助于准确测量人眼看不到的内容，用于估计失真信号和原始信号之间的可见度差，然后进行计算处理，去除冗余。
包括以下元素：计算
1. 绝对亮度的非线性灵敏度（non-linear sensitivity to calculate absolute luminance）、
2. 对视觉频率的对比度灵敏度（contrast sensitivity to visual frequencies）、
3. 倾斜效应和视觉通道的子带分解（oblique effect and sub-band decomposition into visual channels）、
4. 掩蔽效应（masking effect）、
5. 心理测量功能和误差池（psychometric function and error pooling）

使用以上工具在可见性阈值内从源视频中删除或添加信息。
冗余信息可以从JND内的源中移除，以执行预处理算法。

