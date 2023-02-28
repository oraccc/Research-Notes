## Video Call Dataset Survey



### 1-Dataset for Real and Virtual Backgrounds of Video Calls

[dataset link](https://zenodo.org/record/5572910#.Y5iE-HZBxEZ)

> We recorded different video conferencing videos with diverse real and virtual backgrounds, changing subjects, and lighting. The frames are then extracted from the videos and stored in JPEG format with QF = 100 and resolution of 1280 × 720.

包含了实际背景和虚拟背景（该数据集的主要是用于区别背景是否是虚拟的，因此数据集的视频中人物没有移动，也没有暴露虚拟背景后面的真实场景信息）

一些统计信息

Training: 9个视频（5个实际背景与4个虚拟背景）

Test: 9个视频（2个实际背景与7个虚拟背景）

各个视频之间人物、穿着、采光等等方面有差异

真实背景：

<center class="half"> <img src="https://raw.githubusercontent.com/oraccc/Research-Notes/master/imgs/vcbg-1.png" width="350"><img src="https://raw.githubusercontent.com/oraccc/Research-Notes/master/imgs/vcbg-2.png" width="350"></center>

虚拟背景：

<center class="half"> <img src="https://raw.githubusercontent.com/oraccc/Research-Notes/master/imgs/vcbg-3.png" width="350"><img src="https://raw.githubusercontent.com/oraccc/Research-Notes/master/imgs/vcbg-4.png" width="350"></center>



---



### 2-Dataset from Future Video Conferencing (FVC)

**The 1st Future Video Conferencing Workshop** in conjunction with CVPR 2021

TRACK1: Human-centric video matting

> ... aims to perform efficient and accurate portrait matting in videos, To this end, we collect 320 videos from real-world video conferencing scenarios using **VooV Meeting** and annotate the alpha matte at 5~6 fps. This portrait matting dataset covers a wide range of scenarios from **both indoor scenes (e.g., office, bedroom) and outdoor scenes (e.g., park, street)**. 
>
> ...
>
> The dataset can be downloaded from both [GoogleDrive](https://drive.google.com/file/d/14pLlM7h5jxSn3xy3byHVQPNdCTerEpUL/view?usp=sharing) and [Baidu Cloud](https://pan.baidu.com/s/130xTgmxu26a5EViEKm-l9A)(extract code: f1o7). More details can be found at https://competitions.codalab.org/competitions/30523

用于Video-Matting的数据集，全是真实背景，没有虚拟背景，分为室内和室外两种

样例，一个短的视频，再加上一些帧的划分：

<img src="https://raw.githubusercontent.com/oraccc/Research-Notes/master/imgs/fvc-sample.png" width="650" >



背景更加随意

室外背景可以看出文字、建筑物、车辆甚至二维码等信息

<center class="half"> <img src="https://raw.githubusercontent.com/oraccc/Research-Notes/master/imgs/fvc-1.png" width="350"><img src="https://raw.githubusercontent.com/oraccc/Research-Notes/master/imgs/fvc-2.png" width="350"></center>



室内场景可以看到背景的主要物品，例如超市的货架、柜子

<center class="half"> <img src="https://raw.githubusercontent.com/oraccc/Research-Notes/master/imgs/fvc-3.png" width="350"><img src="https://raw.githubusercontent.com/oraccc/Research-Notes/master/imgs/fvc-4.png" width="350"><img src="https://raw.githubusercontent.com/oraccc/Research-Notes/master/imgs/fvc-5.png" width="350"><img src="https://raw.githubusercontent.com/oraccc/Research-Notes/master/imgs/fvc-6.png" width="350"></center>

TRACK2: Human-centric video coding for action analysis

> 使用的数据集并不合适，为PKU-MMD，非Video-Call





#### 一些方向的思考：

自建数据集？

针对没有采用虚拟背景的Video Call（可以不局限于视频会议，视频通话也是常见的场景，并且视频通话不开虚拟背景的可能性更高）的隐私信息提取（目前暂且没有找到相关的研究）

采用上述的数据集尝试进行一些初步信息的提取：文字信息占很大一部分，还有目标定位，之后再尝试分析

在提取信息之前需要使用图像扣取技术先将人脸部分去除？