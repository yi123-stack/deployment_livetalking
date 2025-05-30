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

4. 原项目中，将LLM的api_key添加到系统变量中进行调用，云服务器上未添加环境变量，可以修改llm.py中代码，替换成自己的api_key
   ![image](https://github.com/user-attachments/assets/3cc3bbb8-d66d-4975-94dc-8b59fdba21db)

5. 上述工作完成后，即可启动服务，运行：python app.py --transport webrtc --model wav2lip --avatar_id wav2lip256_avatar1
   由于在云服务器中运行，本地无法访问8010端口，因此需要进行端口转发将8010端口转发到本地
   在本地电脑终端cmd中执行代理命令：ssh -CNg -L 8010:127.0.0.1:8010 root@服务器ip -p 服务器端口号。
   在本地浏览器中 输入http://127.0.0.1:8010/dashboard.html，即可访问服务
   <img width="1150" alt="a7d4f11c4b93271f7f61c120241bcda" src="https://github.com/user-attachments/assets/f627728a-17ca-4fdd-ba0e-ec7a2f408c22" />
6.点击开始连接，如果出现del nerfreals[sessionid] KeyError：这样的报错
![image](https://github.com/user-attachments/assets/6892155d-17f1-4f51-ab41-d1d3f21476ee)
   开启stun服务即可正常连接
   ![image](https://github.com/user-attachments/assets/0732e10d-8bca-4b92-8e7f-399b8a555f30)

7. 至此，基础版的LiveTalking正式部署完成

**更换TTS、添加ASR、更换人物.....coming soon**


   
   


   
