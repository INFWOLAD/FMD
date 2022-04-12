# FMD项目源码目录

郑州大学 通信工程3班 严根 毕设项目 cosz@foxmail.com

--------------------------------------------------

*本网站仅用于部分成果展示  By cosz*

## 代码查看

相关文件点击即可跳转查看



| [**model.py**](https://fmd.netlify.app/code/model)       | [**predict.py**](https://fmd.netlify.app/code/predict)       |
| -------------------------------------------------------- | ------------------------------------------------------------ |
| [**train.py**](https://fmd.netlify.app/code/train)       | [**crop_face.py**](https://fmd.netlify.app/code/crop_face)   |
| [**StartNow.py**](https://fmd.netlify.app/code/startnow) | [**my_dataset.py**](https://fmd.netlify.app/code/my_dataset) |
| [**utils.py**](https://fmd.netlify.app/code/utils)       |                                                              |



## 文件结构

```python
│  README.md  # 说明文档
│  StartNow.py  # 主程序
│          
├─block  # CNNBlock相关文件存放位置
│  │  class_indices.json  # 用于储存分类类别
│  │  model.py  # ConvNeXt model文件
│  │  predict.py  # 预测程序
│  │  train.py  # 训练程序
│          
├─detection  # 通过StartNow调用检测文件存放位置
│  │  crop.txt  # 裁剪信息
│  │  
│  ├─pre  # 检测视频存放位置
│  │      
│  └─process  # 检测视频经过裁剪后图片存放位置
│          
├─runs  # 训练日志存放位置
│           
├─tools  # 视频处理、数据集处理工具存放位置
│  │  crop_face.py  # 人脸裁剪模块
│  │  my_dataset.py  # 数据集模块
│  │  utils.py  # 损失率等信息模块
│          
├─weights  #权重信息存放位置
│  │  best_model.pth  # 训练后最优权重
│  │  convnext_tiny_1k_224_ema.pth  # 官方预训练权重
│          
```

