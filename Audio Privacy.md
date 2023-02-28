### 音频分析

更多偏向对音频本身（信号处理的方向）的处理，不从语音的内容考虑

#### 隐私检测 (Privacy Detection)

不从说话的内容出发，仅从声音特征和表达方式提取信息（非DL方式，更偏向信号处理）

* [Privacy Implications of Voice and Speech Analysis – Information Disclosure by Inference](https://link.springer.com/chapter/10.1007/978-3-030-42504-3_16#Sec3)

  * 在先进的数据分析方法的帮助下，可以从录制音频中的人类语音和其他声学元素中获得敏感信息片段的概述。

  * 除了讲话的语言内容外，说话者的声音特征和表达方式可能隐含着丰富的个人信息，包括暗示说话者的生物特征、个性、身体特征、地理来源、情绪、醉酒和困倦程度、年龄、性别和健康状况的线索，甚至一个人的社会经济地位。

#### 隐私保护 (Privacy Perserving)

* [WaveFuzz: A Clean-Label Poisoning Attack to Protect Your Voice](https://arxiv.org/pdf/2203.13497.pdf)

  * **目标**: 防止第三方音频模型从语音数据中构建涉及用户隐私的功能。

  * **方法**: 从MFCC入手，最大化不受保护的(干净的)语音数据和受保护的(有毒的)语音数据之间的**特征距离（feature distance)**，并最小化它们的**输入距离 (input distance)。**

  * - **特征距离**: 指扰动后的MFCC距离和原始音频的MFCC距离
    - **输入距离**: 指扰动后的原始音频waveform和原始音频waveform

  <img src="https://raw.githubusercontent.com/oraccc/Research-Notes/master/imgs/wavefuzz.png" width = 450>

* [Audio Privacy: Reducing Speech Intelligibility while Preserving Environmental Sounds](https://dl.acm.org/doi/pdf/10.1145/1459359.1459472)
  
  * 该方法基于识别语音区域，并将这些区域的声道传递函数替换为预先录制的元音的传递函数，其中替换元音的标识独立于口语音节的标识。
  * 在这篇论文中描述了一种自动降低语音的可理解性的方法，同时保留韵律和非语音环境声音。通过可解性研究评估了我们的方法，结果表明在允许识别其他声音的同时，显著降低了语音的可解性。
  
* [A Privacy-Preserving Multipurpose Watermarking Scheme for Audio Authentication and Protection](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8455891)

  * 首先对加密音频进行加密域离散小波变换，得到加密系数。采用扩频方法将鲁棒水印和脆弱水印嵌入到不同的子带中。在此基础上，提出了从加密水印音频中提取鲁棒水印和脆弱水印的算法。通过实验验证了该方案的有效性和可行性。结果表明，该方案具有良好的鲁棒性、脆弱性和篡改定位性能。

  <img src="https://raw.githubusercontent.com/oraccc/Research-Notes/master/imgs/audio-watermark.png" width = 650>