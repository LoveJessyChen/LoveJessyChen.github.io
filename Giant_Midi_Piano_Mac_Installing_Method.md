# Giant Midi Piano Mac 安装方法

Giant Midi Piano Mac Installing Method



## 1. 安装HomeBreew，安装wget

/bin/zsh -c "$(curl -fsSL https://gitee.com/cunkai/HomebrewCN/raw/master/Homebrew.sh)"

brew install wget



## 1.5 将文件note_F1=0.9677_pedal_F1=0.9186.pth放到下列目录: (没有就建立)
\Users\你的账户名称\piano_transcription_inference_data\


## 2. 安装python3.7.3，从官网直接下载安装包
https://www.python.org/downloads/
检测python安装是否成功:终端---键入python3回车,显示python版本为3.7.3. 关闭该窗口.



## 3.安装pip


在终端依次输入以下命令：
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py

python3 get-pip.py
安装完成后，可以查看一下 pip3 的版本：

pip3 -V


## 4.安装pytorch:

（也可以从这里下载：https://download.pytorch.org/whl/torch_stable.html）

python3 -m pip install torch torchvision -i https://pypi.tuna.tsinghua.edu.cn/simple

等待安装完毕 关闭窗口

同时升级pip版本(后面要用)
Python3 -m pip install --upgrade pip


## 5.安装ffmpeg
brew install ffmpeg


### *为ffmpeg设置mac下的环境变量：
1.在finder中 按下组合快捷键command+shift+g，打开~/Documents 
在当前的文档文件夹下，新建文件夹FFmpeg，进入文件夹内再新建文件夹bin。
2.把ffmpeg、ffplay、ffprobe三个解压出来的二进制文件复制到bin里边。
3.在finder中 按下组合快捷键command+shift+g，打开~/
4.再在当前窗口处按下command+shift+. 目的是为了显示所有的隐藏文件，
之后我们看到了.bash_profile,

## 5.在此文件末尾处添加下面的内容：
FFMPEG_HOME=/Users/admin/Documents/FFmpeg/bin
export FFMPEG_HOME
export PATH=$PATH:$FFMPEG_HOME/bin

admin换成你自己的用户名
最后刷新一下：

source .bash_profile


## 6.安装软件需求

Python3 -m pip install -r requirements.txt
耐心等待依赖库安装完毕 这一步建议找个梯子 不然速度可能很慢。
如果这一步安装失败,可能因为网络原因.
解决方案:
重复键入pip install -r requirements.txt 执行直到出现上图successfully 字样。


## 7.关于setup.py文件的说明：
在Mac下，文件的音频输入以及mid文件输出的路径需要写完整路径。

## 最后，在Mac下运行的方法是
Python3 ./setup.py







# Tips:

## 1.此项目的音频转换曲谱的过程大约需要2G左右RAM（运行内存）,注意内存占用.

## 2.默认使用CUDA转换,可以在start.py中改为Cpu模式,两者的速度会因硬件环境不同而不同,
 
将cuda改为cpu即可.注意虚拟机中一般不能使用cuda.
电脑不太好的情况下建议使用cpu模式。

Cuda是显卡模式，cpu是中央处理器运算模式
