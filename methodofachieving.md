# 项目实现方式

郑州大学 通信工程3班 严根 毕设项目 cosz@foxmail.com

----------------------------------------------------

*本网站仅用于部分成果展示  By cosz*

## 功能实现

1. ### 视频处理

视频处理采用opencv对图像进行预处理（以固定间隔进行帧获取），随后送入MTCNN中进行人脸检测，并以一定比例进行扩充，以保留足够的信息以供分析。与此同时，通过Yolov5搭建了另一套视频处理方法，以满足一定情况下的轻量化和实时性需求。

2. ### 虚假检验

虚假检验采用ConvNeXt作为CNNblock。不同于先前大部分团队使用的CNN，在transformer进入cv领域后，传统CNN被颠覆。ConvNeXt作为2022年1月最新提出的用以追赶transformer的block，在准确率、速度等各个方面都有极大提升。同时使用efficientNetv2另行搭建了一套，以用作对比试验。

3. ### 自我训练

通过BeautifulSoup自动爬取网站源码，在此基础上通过正则匹配爬取图床链接，以div标签进行自动分类，并自动输出到训练目录。通过linux定时任务自动调取daily_train实现增量训练。



## 参考文献

 [1]. Liu, Z., et al., A ConvNet for the 2020s. arXiv e-prints, 2022: p. arXiv:2201.03545.

 [2]. Dosovitskiy, A., et al., An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale. arXiv e-prints, 2020: p. arXiv:2010.11929.

 [3]. He, K., et al., Deep Residual Learning for Image Recognition. arXiv e-prints, 2015: p. arXiv:1512.03385.

 [4]. Jiang, L., et al., DeeperForensics Challenge 2020 on Real-World Face Forgery Detection: Methods and Results. arXiv e-prints, 2021: p. arXiv:2102.09471.

 [5]. McCloskey, S. and M. Albright, Detecting GAN-generated Imagery using Color Cues. arXiv e-prints, 2018: p. arXiv:1812.08247.

 [6]. Peng, B., et al., DFGC 2021: A DeepFake Game Competition. arXiv e-prints, 2021: p. arXiv:2106.01217.

 [7]. N., R., et al. Distinguishing computer graphics from natural images using convolution neural networks. in 2017 IEEE Workshop on Information Forensics and Security (WIFS). 2017.

 [8]. Tan, M. and Q.V. Le, EfficientNet: Rethinking Model Scaling for Convolutional Neural Networks. arXiv e-prints, 2019: p. arXiv:1905.11946.

 [9]. Tan, M. and Q.V. Le, EfficientNetV2: Smaller Models and Faster Training. arXiv e-prints, 2021: p. arXiv:2104.00298.

[10]. Xin, Y., et al., Exposing GAN-synthesized Faces Using Landmark Locations. CoRR, 2019. abs/1904.00167.

[11]. Zhang, K., et al., Joint Face Detection and Alignment Using Multitask Cascaded Convolutional Networks. IEEE Signal Processing Letters, 2016. 23: p. 1499-1503.

[12]. Bochkovskiy, A., C. Wang and H.M. Liao, YOLOv4: Optimal Speed and Accuracy of Object Detection. arXiv e-prints, 2020: p. arXiv:2004.10934.