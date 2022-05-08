
- [图片数据集](#图片数据集)
  - [1. BPAAS](#1-bpaas)
  - [2. CIFAR10(可能用不了了)](#2-cifar10可能用不了了)
  - [3. ImageNet32](#3-imagenet32)
  - [4. YFCC100M](#4-yfcc100m)
  - [5. MNIST](#5-mnist)
  - [6. CelebA](#6-celeba)
  - [7. LSUN](#7-lsun)
  - [8. Kodak](#8-kodak)
  - [9. Tecnick](#9-tecnick)
  - [10. CLIC2020](#10-clic2020)
  - [11. DIV2K](#11-div2k)
- [视频数据集](#视频数据集)
  - [1. Vimeo-90K](#1-vimeo-90k)
  - [2. HEVC Class B(1080P), C(480P), D(240P), E(720P)](#2-hevc-class-b1080p-c480p-d240p-e720p)
  - [3. MLC-JCV](#3-mlc-jcv)
  - [4. UVG](#4-uvg)
  - [5. UCF101](#5-ucf101)
  - [6. Sprites(2D Video Game Character Sprites)](#6-sprites2d-video-game-character-sprites)
  - [7. BAIR robot pushing dataset](#7-bair-robot-pushing-dataset)
  - [8. Kinetics600](#8-kinetics600)

# 图片数据集

## 1. BPAAS
- Citation: [Zhang R, Isola P, Efros A A, et al. The unreasonable effectiveness of deep features as a perceptual metric[C]//Proceedings of the IEEE conference on computer vision and pattern recognition. 2018: 586-595.](https://arxiv.org/abs/1801.03924)
- Main Features:
  - 人类感知相似性判断数据集；
  - 均为256x256，包括各种类型的图像，比如人像、建筑、自然；
  - 大部分图像应用了filter，比如模糊、扭曲、噪声；
  - [![OlgkKP.md.png](https://s1.ax1x.com/2022/05/07/OlgkKP.md.png)](https://imgtu.com/i/OlgkKP)

- [Project Page](https://richzhang.github.io/PerceptualSimilarity/)
- 使用该数据集的论文:
  - Saliency Driven Perceptual Image Compression (WACV 2021)

## 2. CIFAR10(可能用不了了)
- Citation: Learning Multiple Layers of Features from Tiny Images, Alex Krizhevsky, 2009.
- Main Features:
  - CIFAR-10是 80 million tiny images dataset的子集，但是[原作者在2020年已经要求撤回这个源数据集](http://groups.csail.mit.edu/vision/TinyImages/)
  - 分成十类图像，每一类之间没有重叠，一共60000张32x32的彩色图像（50000 training images and 10000 test images）
  - [![Olg1K0.md.png](https://s1.ax1x.com/2022/05/07/Olg1K0.md.png)](https://imgtu.com/i/Olg1K0)
- [Project Page](http://www.cs.toronto.edu/~kriz/cifar.html)
- 使用该数据集的论文:
  - OSOA: One-Shot Online Adaptation of Deep Generative Models for Lossless Compression(NeurIPS'21)
  - Compressing Images by Encoding Their Latent Representations with Relative Entropy Coding (NeurIPS 2020)
  - Integer Discrete Flows and Lossless Compression (NeurIPS 2019)
  - Compression with Flows via Local Bits-Back Coding (NeurIPS 2019)

## 3. ImageNet32
- Citation: [Chrabaszcz P, Loshchilov I, Hutter F. A Downsampled Variant of ImageNet as an Alternative to the CIFAR datasets[J]. arXiv preprint arXiv:1707.08819, 2017.](https://arxiv.org/abs/1707.08819)
  - 新的注重隐私保护的ImageNet，将偶然出现的人像进行模糊处理： [Yang K, Yau J, Fei-Fei L, et al. A study of face obfuscation in imagenet[J]. arXiv preprint arXiv:2103.06191, 2021.](https://arxiv.org/abs/2103.06191https://arxiv.org/abs/2103.06191)
- Main Features:
  - ImageNet32是ImageNet的下采样版本（分辨率均为32x32），与源数据集相比，图片数量和类别保持一致，但经下采样能加快训练速度，且the characteristics of the downsampled datasets with respect to **optimal hyperparameters appear to remain similar**.
  - 和ImageNet一样，包括各种类型的图像，共分为1000类，每个类的训练图像数目从732到1300不等，每个类有50张验证图像，图像格式与CIFAR一致；
  - 即使图片分辨率降到32x32，仍能准确预测标签；
  - [![Olg3rV.md.png](https://s1.ax1x.com/2022/05/07/Olg3rV.md.png)](https://imgtu.com/i/Olg3rV)
- [Project Page](https://patrykchrabaszcz.github.io/Imagenet32/)
- [Github](https://github.com/PatrykChrabaszcz/Imagenet32_Scripts)
- 使用该数据集的论文:
  - OSOA: One-Shot Online Adaptation of Deep Generative Models for Lossless Compression(NeurIPS'21)
  - 用的ImageNet：Compressive Visual Representations(NeurIPS'21)
  - Compressing Images by Encoding Their Latent Representations with Relative Entropy Coding (NeurIPS 2020)
  - 用的ImageNet32和64: Integer Discrete Flows and Lossless Compression (NeurIPS 2019)
  - 用的ImageNet32和64: Compression with Flows via Local Bits-Back Coding (NeurIPS 2019)


## 4. YFCC100M
- Citation: [Thomee, Bart, et al. "YFCC100M: The new data in multimedia research." Communications of the ACM 59.2 (2016): 64-73.](https://dl.acm.org/doi/abs/10.1145/2812802)
- Main Features:
  - 100 million级数据，其中大约99.2 million是图片（压缩包11TB），0.8 million的视频文件（压缩包1TB），元数据20GB左右
  - 大部分由专业相机拍摄得到，包括各种类型的图像：people, animals, objects, food, events, architecture, and scenery...
  - [![Olgt54.png](https://s1.ax1x.com/2022/05/07/Olgt54.png)](https://imgtu.com/i/Olgt54)
- [Project Page](http://www.multimediacommons.org/)
- 使用该数据集的论文:
  - OSOA: One-Shot Online Adaptation of Deep Generative Models for Lossless Compression(NeurIPS'21)



## 5. MNIST
- Citation: Yann LeCun. The MNIST database of handwritten digits, 1998.
- Main Features:
  - 一个**手写数字**数据集，固定分辨率28x28，60000张训练图像，10000张测试图像；
- [Project Page](http://yann.lecun.com/exdb/mnist/)
- 使用该数据集的论文:
  - Pragmatic Image Compression for Human-in-the-Loop Decision-Making(NeurIPS'21)



## 6. CelebA
- Citation: [Liu, Ziwei and Luo, Ping and Wang, Xiaogang and Tang, Xiaoou. Deep Learning Face Attributes in the Wild. Proceedings of International Conference on Computer Vision (ICCV), 2015.](https://arxiv.org/abs/1411.7766)
- Main Features:
  - 人脸属性数据集，202,599张名人图像，每张图像都有40个属性注释，包含大量姿势变换和混乱背景；
  - 提供两类尺寸的图像，一类原始图像，另一类经align&cropped，分辨率均为218x178；
  - [![OlgYaF.md.png](https://s1.ax1x.com/2022/05/07/OlgYaF.md.png)](https://imgtu.com/i/OlgYaF)
- [Project Page](https://mmlab.ie.cuhk.edu.hk/projects/CelebA.html)

- 使用该数据集的论文:
  - Pragmatic Image Compression for Human-in-the-Loop Decision-Making(NeurIPS'21)
  - Deep Generative Video Compression (NeurIPS 2019)
  - Neural Proximal Gradient Descent for Compressive Imaging(NeurIPS 2018)



## 7. LSUN
- Citation: [Fisher Yu, Yinda Zhang, Shuran Song, Ari Seff, and Jianxiong Xiao. LSUN: Construction of a large-scale image dataset using deep learning with humans in the loop. arXiv preprint arXiv:1506.03365, 2015.](https://arxiv.org/abs/1506.03365)
- Main Features:
  - It contains around **one million labeled images for each** of **10 scene categories** (bedroom, bridge, church_outdoor, classroom, conference_room, dining_room, kitchen, living_room, restaurant, tower) and **20 object categories** (airplane, bicycle, bird, boat, bottle, bus, car, cat, chair, cow, dining table, dog, horse, motorbike, person, potted plant, sheep, sofa, train, tv-monitor).
  - 图像尺寸约256（the smaller dimension），object类文件大小从15GB到477GB不等，scene类以LMDB格式存储，压缩文件大小从2.3GB到43GB不等，[http://dl.yf.io/lsun/](http://dl.yf.io/lsun/)
  - [![OlgQvq.md.png](https://s1.ax1x.com/2022/05/07/OlgQvq.md.png)](https://imgtu.com/i/OlgQvq)
- [Project Page](https://www.yf.io/p/lsun)
- [Github](https://github.com/fyu/lsun)
- 使用该数据集的论文:
  - Pragmatic Image Compression for Human-in-the-Loop Decision-Making(NeurIPS'21)
  - Deep Generative Video Compression (NeurIPS 2019)


## 8. Kodak
- Citation: E.Kodak. Kodak lossless true color image suite (PhotoCD PCD0992).
- Main Features:
  - Total 25 uncompressed PNG true color images of size 768 × 512 pixels. (24 bits per pixel, aka "full color")
  - 经典的作为benchmark的**未压缩**数据集，包含landscape and portrait
  - [![O327mq.md.png](https://s1.ax1x.com/2022/05/08/O327mq.md.png)](https://imgtu.com/i/O327mq)
- [Project Page](http://www.cs.albany.edu/~xypan/research/snr/Kodak.html)
- 使用该数据集的论文：
  - Improving Inference for Neural Image Compression (NeurIPS 2020)
  - High-Fidelity Generative Image Compression (NeurIPS 2020)
  - Compressing Images by Encoding Their Latent Representations with Relative Entropy Coding (NeurIPS 2020)
  - Joint Autoregressive and Hierarchical Priors for Learned Image Compression (NeurIPS 2018)


## 9. Tecnick
- Citation: ASUNI N, GIACHETTI A, "TESTIMAGES: A Large Data Archive For Display and Algorithm Testing", Journal of Graphics Tools, Volume 17, Issue 4, 2015, pages 113-125, DOI:10.1080/2165347X.2015.1024298
- Main Features:
  - 包括16 bit-depth reference images and different downscaled versions of reference high-resolution images.
  - 根据不同的研究目的又分为以下的子数据集： 
    1. **SAMPLING**: 主要目的是利用所提供的natural images用于测试re-sampling algorithm（比如线性插值、缩放、enlargement和超分）。 This dataset uniquely provides **a base of 40 RBG 2400x2400 reference images with a bit-depth of 16bpp and high dynamic range (HDR)**. The reference images were processed to obtain different sub-resolutions and variation with 8bpp and grayscale, for **a total of more 220K images**.<br>   

    2. **COLORS**: 包括8bpp和16bpp，多种分辨率的RGB图像。 The main purpose of this dataset is providing images **to test the color rendering on different displays and facilitate color adjustments.** 多种分辨率：114 standard and non-standard resolutions for computer monitors, televisions, cinema projectors, mobile phone screens, camera sensors and other generic displays:<br>

    3. **PATTERNS**: 包括8bpp和16bpp，多种分辨率（和COLORS一致）的RGB图像。 The main purpose of this dataset is providing images **to test the rendering of standard geometrical patterns by displays, monitors, televisions and projectors.**<br>

    4. **SAMPLING_PATTERNS**: 属于SAMPLING的扩展版本，8bpp和16bpp，多种分辨率，超过400张人工灰度参考图像，含2448x2448。The main purpose of this dataset is **to test in isolation specific features of resampling algorithms.**<br>
    
  - [![O3TakR.md.png](https://s1.ax1x.com/2022/05/08/O3TakR.md.png)](https://imgtu.com/i/O3TakR)
- [Project Page](https://testimages.org/)
- [Download Link](https://sourceforge.net/projects/testimages/files/)
- 使用该数据集的论文：
  - Improving Inference for Neural Image Compression (NeurIPS 2020)
  - 用的100张1200x1200: Joint Autoregressive and Hierarchical Priors for Learned Image Compression (NeurIPS 2018)

## 10. CLIC2020
- Citation: George Toderici, Lucas Theis, Nick Johnston, Eirikur Agustsson, Fabian Mentzer, Johannes Ballé, Wenzhe Shi, and Radu Timofte. CLIC 2020: Challenge on Learned Image Compression, 2020. http://compression.cc.
- Main Features:
  - 像是比赛数据集，每年更新（以下为2022的说明），包括三类
    - Image Compression: 30张图像，PNG格式，Images resized such that the longer side is 2048. 涉及风景、人物、动物、建筑等多类图像。
    - Video Compression: 292 videos, split into 3 sets: 4 near lossless, 40 webcam, 248 general. mp4格式，视频均为720p或1080p，单个视频时长10s，帧率从15fps到60fps不等，但大部分处于25-30fps。
    - Perceptual Metrics: 提供一对图像（one original, the other distorted image），利用所设计的感知度量给图像打分。在这个track中，提供了超过130GB的图像数据集，同样是各种类型的场景。
  - [![O3zEeP.md.png](https://s1.ax1x.com/2022/05/08/O3zEeP.md.png)](https://imgtu.com/i/O3zEeP)
- [Project Page](http://compression.cc/tasks/)
- 使用该数据集的论文：
  - High-Fidelity Generative Image Compression (NeurIPS 2020)

## 11. DIV2K
- Citation: [Eirikur Agustsson and Radu Timofte. Ntire 2017 challenge on single image super-resolution: Dataset and study. In The IEEE Conference on Computer Vision and Pattern Recognition (CVPR) Workshops, July 2017.]()
- Main Features:
  - RGB, 1000张2K分辨率的图像，内容多样，分成三个子数据集，800张用于train，100张valid，100张test，再分别下采样增大图像数量。
- [Project Page](https://data.vision.ee.ethz.ch/cvl/DIV2K/)
- 使用该数据集的论文：
  - High-Fidelity Generative Image Compression (NeurIPS 2020)



# 视频数据集

## 1. Vimeo-90K
- Citation: [T. Xue, B. Chen, J. Wu, D. Wei, and W. T. Freeman, “Video enhancement with task-oriented flow,” International Journal of Computer Vision (IJCV), vol. 127, no. 8, pp. 1106–1125, 2019.](https://link.springer.com/article/10.1007/s11263-018-01144-2)
- Main Features:
  - 大规模、高质量的视频数据集：涉及不同主题，由专业摄像机拍摄，包括4278个视频（含89800个clips from vimeo.com），涵盖多种场景和动作，固定分辨率448x256；
  - 该数据集进一步将89800个clips分成两个子集，分别用于temporal frame interpolation(33GB) and for video denoising, deblocking, and super-resolution(82GB).
  - [![Olgd2R.md.png](https://s1.ax1x.com/2022/05/07/Olgd2R.md.png)](https://imgtu.com/i/Olgd2R)
- [Project Page](http://toflow.csail.mit.edu/)，提供完整数据集的下载方法
- 使用该数据集的论文:
  - Deep Contextual Video Compression(NeurIPS'21)

## 2. HEVC Class B(1080P), C(480P), D(240P), E(720P)
- Citation: F. Bossen et al., “Common test conditions and software reference configurations,” in JCTVC-L1100, vol. 12, 2013.
- Main Features:
  - Test sequences are available on ftp://hevc@ftp.tnt.uni-hannover.de/orig-cfp/ (please contact the JCT-VC chairs for login information).
- 使用该数据集的论文：
  - Deep Contextual Video Compression(NeurIPS'21)


## 3. MLC-JCV
- Citation: [H. Wang, W. Gan, S. Hu, J. Y. Lin, L. Jin, L. Song, P. Wang, I. Katsavounidis, A. Aaron, and C.-C. J. Kuo, “MCL-JCV: a JND-based H. 264/AVC video quality assessment dataset,” in 2016 IEEE International Conference on Image Processing (ICIP), pp. 1509–1513, IEEE, 2016.](https://ieeexplore.ieee.org/abstract/document/7532610/)
- Main Features:
  - 采集自30个源视频，均为1920x1080，每个视频时长5s，但帧率不同，基于源视频clips，采用不同的QP进行x264编码，得到的MLC-JCV数据集拥有30x52=1560个视频序列；
  - [![OlgJVU.md.png](https://s1.ax1x.com/2022/05/07/OlgJVU.md.png)](https://imgtu.com/i/OlgJVU)
  - [![Olg8bT.md.png](https://s1.ax1x.com/2022/05/07/Olg8bT.md.png)](https://imgtu.com/i/Olg8bT)
- 使用该数据集的论文：
  - Deep Contextual Video Compression(NeurIPS'21)


## 4. UVG
- Citation: [A. Mercat, M. Viitanen, and J. Vanne, “UVG dataset: 50/120fps 4K sequences for video codec analysis and development,” in Proc. ACM Multimedia Syst. Conf., Istanbul, Turkey, June 2020.]()
- Main Features:
  - 16 versatile 4K(3840x2160) test video sequences captured at 50/120 fps. 均包括YUV RAW文件，部分视频分辨率包含1080p。
  - [![OlgUPJ.md.png](https://s1.ax1x.com/2022/05/07/OlgUPJ.md.png)](https://imgtu.com/i/OlgUPJ)
- [Project Page](http://ultravideo.fi/#testsequences)
- 使用该数据集的论文：
  - Deep Contextual Video Compression(NeurIPS'21)

## 5. UCF101
- Citation: [Khurram Soomro, Amir Roshan Zamir, and Mubarak Shah. Ucf101: A dataset of 101 human actions classes from videos in the wild. arXiv preprint arXiv:1212.0402, 2012.](https://arxiv.org/abs/1212.0402)
- Main Features:
  - UCF101 dataset is an extension of UCF50 and consists of **13,320 video clips**, which are classified into **101 categories**. The videos in **101 action categories are grouped into 25 groups**, where each group can consist of 4-7 videos of an action. The videos from the same group may share some common features, such as similar background, similar viewpoint, etc. These 101 categories can be classified into **5 types (Body motion, Human-human interactions, Human-object interactions, Playing musical instruments and Sports)**. The total length of these video clips is over 27 hours. All the videos are collected from YouTube and have **a fixed frame rate of 25 FPS with the resolution of 320 × 240.**
  - 
  - [![O3Y1HI.md.png](https://s1.ax1x.com/2022/05/08/O3Y1HI.md.png)](https://imgtu.com/i/O3Y1HI)
- [Project Page](https://www.crcv.ucf.edu/research/data-sets/ucf101/)
- 使用该数据集的论文：
  - Compressed Video Contrastive Learning(NeurIPS 2021)



## 6. Sprites(2D Video Game Character Sprites)
- Citation: [Reed, Scott E., et al. "Deep visual analogy-making." Advances in neural information processing systems 28 (2015).](https://proceedings.neurips.cc/paper/2015/hash/e07413354875be01a996dc560274708e-Abstract.html)
- Main Features:
  - The Sprites dataset contains 60 pixel color images of animated characters (sprites). There are 672 sprites, 500 for training, 100 for testing and 72 for validation. Each sprite has 20 animations and 178 images, so the full dataset has 120K images in total. There are many changes in the appearance of the sprites, they differ in their body shape, gender, hair, armor, arm type, greaves, and weapon.
  - [![O8nX3n.md.png](https://s1.ax1x.com/2022/05/09/O8nX3n.md.png)](https://imgtu.com/i/O8nX3n)
- 使用该数据集的论文：
  - Deep Generative Models for Distribution-Preserving Lossy Compression (NeurIPS 2018)

## 7. BAIR robot pushing dataset
- Citation: [Finn, Chelsea, Ian Goodfellow, and Sergey Levine. "Unsupervised learning for physical interaction through video prediction." Advances in neural information processing systems 29 (2016).](https://proceedings.neurips.cc/paper/2016/hash/d9d4f495e875a2e075a1a4a6e1b9770f-Abstract.html)
- Main Features:
  - 描述真实世界中机器与物体交互场景的视频数据集
  - The Robotic Pushing Dataset is a dataset for video prediction for real-world interactive agents which consists of 59,000 robot interactions involving pushing motions, including a test set with novel objects. 
- 使用该数据集的论文：
  - Deep Generative Models for Distribution-Preserving Lossy Compression (NeurIPS 2018)

## 8. Kinetics600
- Citation: [Carreira, Joao, et al. "A short note about kinetics-600." arXiv preprint arXiv:1808.01340 (2018).](https://arxiv.org/abs/1808.01340)
- Main Features:
  - The Kinetics-600 is a large-scale action recognition dataset which consists of around 480K videos from 600 action categories. The 480K videos are divided into 390K, 30K, 60K for training, validation and test sets, respectively. Each video in the dataset is a 10-second clip of action moment annotated from raw YouTube video. It is an extensions of the Kinetics-400 dataset.
- [Project Page](https://www.deepmind.com/open-source/kinetics)
- 使用该数据集的论文：
  - Deep Generative Models for Distribution-Preserving Lossy Compression (NeurIPS 2018)







