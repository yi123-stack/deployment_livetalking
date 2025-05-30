![image](https://github.com/user-attachments/assets/15cba821-e346-480f-bb72-54300f1358ad)# deployment_livetalking
如何在云平台部署自己的livetalking
平台：优云智算
系统：Ubuntu 22.04
python:3.10
1. 使用pip安装torch2.0.0：pip install torch==2.0.0 torchvision==0.15.1 torchaudio==2.0.1 -i https://pypi.tuna.tsinghua.edu.cn/simple
手动卸载numpy并重装numpy==1.26.4
安装完成后即可安装其他库：pip install -r requirements.txt

2. 下载wav2lip模型，这一步同官方文档：
   下载模型
夸克云盘https://pan.quark.cn/s/83a750323ef0
GoogleDriver https://drive.google.com/drive/folders/1FOC_MD6wdogyyX_7V1d4NDIO7P9NlSAJ?usp=sharing
将wav2lip256.pth拷到本项目的models下, 重命名为wav2lip.pth;
将wav2lip256_avatar1.tar.gz解压后整个文件夹拷到本项目的data/avatars下

3. 项目运行需要用到FFMPEG，而安装FFMPEG又需要安装yasm，具体安装步骤参照这篇：https://blog.csdn.net/Aarstg/article/details/122668586。
   过程繁琐，主要涉及添加系统环境变量，耐心等待即可。
   安装完成后，输入ffmpeg -version检查是否安装成功，出现如下图信息即为安装成功：
   ![image](https://github.com/user-attachments/assets/cc0b0aa0-6546-4de1-9a3f-2fee1ac415e4)

   
