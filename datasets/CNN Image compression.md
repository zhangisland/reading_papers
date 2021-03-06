##### Related Work

- Integer Discrete Flows and Lossless Compression (NeurIPS 2019)
	- [jornpeters/integer_discrete_flows: Code release for Hoogeboom, Emiel, Jorn WT Peters, Rianne van den Berg, and Max Welling. "Integer Discrete Flows and Lossless Compression." Conference on Neural Information Processing Systems (2019). (github.com)](https://github.com/jornpeters/integer_discrete_flows)
- Deep Generative Video Compression (NeurIPS 2019)
- Compression with Flows via Local Bits-Back Coding (NeurIPS 2019)
  - https://github.com/hojonathanho/localbitsback.

- Joint Autoregressive and Hierarchical Priors for Learned Image Compression (NeurIPS 2018)
- Neural Proximal Gradient Descent for Compressive Imaging(NeurIPS 2018)
- Deep Generative Models for Distribution-Preserving Lossy Compression (NeurIPS 2018)

- Improving Inference for Neural Image Compression (NeurIPS 2020)
- High-Fidelity Generative Image Compression (NeurIPS 2020)
- Compressing Images by Encoding Their Latent Representations with Relative Entropy Coding (NeurIPS 2020)

- Saliency Driven Perceptual Image Compression (WACV 2021)
  - [datasets: 2AFC(下载的完整版BAPPS)](https://github.com/richzhang/PerceptualSimilarity)
- Compressed Video Contrastive Learning(NeurIPS 2021)
- Deep Contextual Video Compression(NeurIPS'21)
  - [Github: https://github.com/DeepMC-DCVC/DCVC](https://github.com/DeepMC-DCVC/DCVC)
- OSOA: One-Shot Online Adaptation of Deep Generative Models for Lossless Compression(NeurIPS'21)
  - **datasets: CIFAR10, ImageNet32, YFCC100M**
    - CIFAR 10: 
      - [在线导入，cifar-10-dataset (Hub)](https://docs.activeloop.ai/datasets/cifar-10-dataset)
      - [本地下载地址](https://www.cs.toronto.edu/~kriz/cifar.html)
    - ImageNet32: 
      - 除了Hub，TensorFlow也可以在线导入，[在线导入imagenet-dataset (Hub)](https://docs.activeloop.ai/datasets/imagenet-dataset#load-imagenet-dataset-training-subset-in-python)
      - 官网下载地址打不开，[https://image-net.org/request](https://image-net.org/request)
    - YFCC100M: 太大了，100 million的数据量，可以通过网页下载特定的图片，[YFCC100M-dataset (web)](http://projects.dfki.uni-kl.de/yfcc100m/?)
  - Q: OSOA为什么不需要存储模型？FineTune和PreTrain在OSOA中充当什么成分（如果是包括在OSOA之中，为什么图片评估的时候，要把OSOA和FineTune/PreTrain的性能做比较）？
  - bpd(bits per dimension)越高效果越好
  - 基于在节省空间和时间开销之间的权衡，实验结果是更适用于数据备份和冷数据存储，而不是实时视频流
- Compressive Visual Representations(NeurIPS'21)
- Pragmatic Image Compression for Human-in-the-Loop Decision-Making(NeurIPS'21)
  - [https://github.com/rddy/pico](https://github.com/rddy/pico)
  - **datasets: MNIST, CelebA, LSUN Car**
    - MNIST: 
      - [在线导入，MNIST-dataset (Hub)](https://docs.activeloop.ai/datasets/mnist#load-mnist-dataset-training-subset-in-python)
      - [本地下载](http://yann.lecun.com/exdb/mnist/)
    - CelebA: 
      - [在线导入：CelebA-dataset (Hub)](https://docs.activeloop.ai/datasets/celeba-dataset#load-celeba-dataset-training-subset-in-python)
      - [下载地址](http://mmlab.ie.cuhk.edu.hk/projects/CelebA.html)
      
    - LSUN Car: 
      - [直接本地下载（文件太大了，173GB）](http://dl.yf.io/lsun/objects/car.zip)
      - [命令下载，python3 download.py -c car](https://github.com/fyu/lsun)
- Universal Rate-Distortion-Perception Representations for Lossy Compression(NeurIPS'21)
  - [datasets: SVHN, digits](http://ufldl.stanford.edu/housenumbers/)
- 