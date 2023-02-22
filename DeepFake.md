## :one:Concept: GAN and DeepFake

### GAN





### Deep Fakes

“Deep Fakes”是一种流行的基于人工智能的图像合成技术。 它比传统的图像到图像转换更强大，因为它可以在没有给定配对训练数据的情况下生成图像。

 “Deep Fakes”的目标是从**现有图像集合中捕捉共同特征**，并找出一种方法使其他图像具有这些特征，例如形状和样式。 生成对抗网络 (GAN) 为我们提供了一种实施“Deep Fakes”的可用方法



从视觉角度，deepfake一般可划分四类：**重现（reenactment）**、**替换（replacement）**、**编辑（editing）**、**合成（synthesis）**。

尽管人脸编辑和合成研究火热，但重现和替换才是最大的隐患，它们可以让攻击者控制身份和欺骗。

* `重现（reenactment）`: 重现使用源身份Xs驱动目标身份Xt，使得Xt的**行为**和Xs一样，包括表情、嘴部、眼部、头部及躯干。

  > 表情重现、嘴部重现、眼部重现、头部重现、 身体重现

* `替换（replacement）`：替换使用源身份Xs的内容替换目标身份 Xt，使得目标**身份**变成了源身份Xs。

  > 转移、交换

* `编辑（editing）`：编辑是指添加、更改或删除目标身份的**属性**，比如，更换目标对象的发型、衣服、胡须、年龄、体重、颜值、眼镜和种族等属性。
* `合成（synthesis）`：合成是指在**没有目标身份作为基础**的情况下创建deepfake角色，类似直接用GAN或者其它生成模型生成人脸，没有明确的target。人脸和身体合成技术可以创建影视素材，生成电影和游戏角色。





## :two:Survey

### GAN-generated Faces Detection: A Survey and New Perspectives

> [arXiv](https://arxiv.org/abs/2202.07145) 2022

<img src="https://raw.githubusercontent.com/oraccc/Research-Notes/master/imgs/fakeface-timeline.png" width="1050" >



#### GAN Generation of Highly Realistic Faces

#### GAN-face Detection Methods

我们将现有的GAN人脸检测文献分为四类

* **Deep Learning-based Methods**

  * 基于深度学习的GAN人脸检测方法提取信号级特征，以训练深度神经网络（DNN）分类器，以在端到端学习框架中区分假人脸和真人脸。

    * `Do et al., 2018` 使用**VGG Net**进行GAN人脸检测，其中VGG-16架构与VGG人脸的预训练权重一起使用。
    * `Mo et al., 2018` 发现**残差场** (residual field) 中的信号可以作为区分真实人脸和GAN人脸的有效特征。他们首先用高通滤波器对输入人脸进行处理，所得残差被送入深度网络用于GAN人脸检测。
    * `Li et al., 2020` 通过分析**色度颜色成分**识别了GAN人脸。他们首先提取了一个特征集来捕获彩色图像统计，然后使用连接的特征来训练GAN人脸分类器。
    * `Chen et al., 2021` 发现**亮度和色度线索**对于改进GAN人脸检测都是有用的。
    * `Guo et al., 2022` 提出了一种基于注意力的方法，通过分析眼睛不一致性来识别GAN生成的人脸，具体来说，该模型通过**定位和比较虹膜伪影**来识别不一致的眼睛成分。

  * 总之，基于深度学习的方法在GAN人脸检测上取得了令人印象深刻的性能。然而，很难将学习模型的决策过程解释为黑匣子。真实世界中的假脸检测除了整体准确性外，**还具有可解释性**，人们更关心用例

    > 例如“这张图片看起来像我认识的人，如果人工智能算法告诉它是假的还是真的，那么推理是什么，我应该信任什么？” 

* **Physical-based Methods**

  * 基于物理的方法通过寻找人脸和物理世界之间的伪影或不一致来识别GAN人脸，例如**透视中的照明和反射**。
    * `Hu et al., 2021` 的方法寻找两只眼睛之间的不一致性，以识别GAN生成的人脸。具体而言，检测并对准眼睛的角膜镜面高光，以进行逐像素联合交点（IoU）比较。假设在肖像设置下由相机拍摄的真实人眼应该在两只眼睛之间的角膜镜面高光之间表现出强烈的相似性。相比之下，这种假设对于GAN合成眼睛来说是不正确的，其中的不一致包括不同的数量、不同的几何形状或镜面高光的不同相对位置
  * 总之，基于物理的检测方法对对抗性攻击更为鲁棒，预测结果为人类用户提供了直观的解释 

* **Physiological-based Methods**

  * 基于生理学的方法研究人脸的语义方面，包括对称性、虹膜颜色、瞳孔形状等线索，其中识别的伪影用于暴露GAN人脸。 
    * GAN可以生成具有高度逼真细节的面部部位（例如，眼睛、鼻子、皮肤、嘴巴），但对这些部位在面部的位置没有明确的限制。换句话说，与真实面孔相比，GAN面孔的面部部分可能**看起来不连贯或自然**。他们指出，可以使用面部标志点（例如，眼、鼻和嘴的尖端）的位置来揭示GAN面部中面部部分配置的这些异常，这可以使用自动算法来有效检测。 
    * `Guo et al., 2022` 中提出了一种相对新的基于生理学的GAN人脸检测方法，其动机是简单观察到GAN人脸呈现出不规则瞳孔形状的共同伪影。具体来说，真实人脸上的瞳孔应该是一个光滑的圆或椭圆；相比之下，GAN脸上的瞳孔可以呈现出不规则的形状或边界。该伪影适用于迄今为止所有已知的GAN模型
  * 总之，基于生理学的方法具有更强的可解释性。然而，与其他法医方法一样，环境限制（如遮挡和眼睛从面部图像中的可见性）仍然是一个主要限制。如果利用端到端学习的力量来改进模型训练，这仍然是一个悬而未决的问题。 

* **Human Visual Performance**

  * 尽管已经开发了许多自动GAN人脸检测算法，但尚未充分研究识别和暴露GAN人脸的人类视觉性能。与图像识别等其他AI问题相比，GAN人脸检测对人眼来说是一个更具挑战性的问题。因此，研究人眼如何识别GAN人脸以及相关的社会影响和伦理问题非常重要。
  * 用于评估自动算法在检测GAN人脸方面的有效性的标准度量包括ROC分析和精确召回。虽然这些指标可以用于研究人类的感知表现，但它们并不直接适用于反映普通大众高度真实的GAN面孔的真实欺骗性。人类的视觉表现在很大程度上是有偏见的，如果有微弱但适当的提示（例如寻找正确的生理线索），人类识别假脸的能力会大大提高。 



## :three:Dataset

### Real Face

#### FFHQ(Flickr-Faces-HQ)

[Dataset Link](https://www.kaggle.com/datasets/arnaud58/flickrfaceshq-dataset-ffhq?select=00000.png)

**Flickr-Faces-HQ (FFHQ)** 由 70,000 张分辨率为 1024×1024 的高质量 PNG 图像组成，在年龄、种族和图像背景方面包含相当大的差异。 

图片是从 Flickr 抓取的，因此继承了该网站的所有Biases，并使用 dlib 自动对齐和裁剪。 

仅收集许可许可下的图像。 使用各种自动过滤器来修剪集合，最后使用 Amazon Mechanical Turk 去除偶尔出现的雕像、绘画或照片。

> Samples
>
> <center class="half"> <img src="https://raw.githubusercontent.com/oraccc/Research-Notes/master/imgs/ffhq-1.png" width="200"/><img src="https://raw.githubusercontent.com/oraccc/Research-Notes/master/imgs/ffhq-2.png" width="200"/><img src="https://raw.githubusercontent.com/oraccc/Research-Notes/master/imgs/ffhq-3.png" width="200"/><img src="https://raw.githubusercontent.com/oraccc/Research-Notes/master/imgs/ffhq-4.png" width="200"/></center>



#### CelebA

[Dataset Link](https://www.kaggle.com/datasets/jessicali9530/celeba-dataset)

**CelebFaces Attributes Dataset (CelebA)** 是一个大规模的人脸属性数据集，拥有超过 **200K** 名人图像，每张都有 **40** 属性注释。 该数据集中的图像涵盖了大的姿势变化和背景杂乱。 CelebA 多样性大，数量大，注释丰富，包括

- **10,177** 个身份
- **202,599** 人脸图像
- **5** 个地标位置，**40** 个二进制属性以及每张图片的注释。

> Samples
>
> <center class="half"> <img src="https://raw.githubusercontent.com/oraccc/Research-Notes/master/imgs/celeb-1.jpg" width="200"/><img src="https://raw.githubusercontent.com/oraccc/Research-Notes/master/imgs/celeb-2.jpg" width="200"/><img src="https://raw.githubusercontent.com/oraccc/Research-Notes/master/imgs/celeb-3.jpg" width="200"/><img src="https://raw.githubusercontent.com/oraccc/Research-Notes/master/imgs/celeb-4.jpg" width="200"/></center>

### GAN Face

`StyleGAN、StyleGAN2、PGGAN、DCGAN、ProGAN`

#### StyleGAN3

<center class="half"> <img src="https://raw.githubusercontent.com/oraccc/Research-Notes/master/imgs/stylegan3-1.png" width="200"/><img src="https://raw.githubusercontent.com/oraccc/Research-Notes/master/imgs/stylegan3-2.png" width="200"/><img src="https://raw.githubusercontent.com/oraccc/Research-Notes/master/imgs/stylegan3-3.png" width="200"/><img src="https://raw.githubusercontent.com/oraccc/Research-Notes/master/imgs/stylegan3-4.png" width="200"/></center>

### A Survey on Generative Adversarial Networks: Variants, Applications, and Training

> [ACM Computing Surveys](https://dl.acm.org/toc/csur/2022/54/8) 2021



