
# CUDA9.0-CentOS_7
tutorial of installing cuda-9.0 on centos 7 (Nvidia Titan V)
## 环境介绍
* HP Z480 Workstation
* Nvidia Titan V
* Intel Xeon E5(x2)
* CentOS 7 64 bit
## 需安装环境
* Python3.6.5_rc1
* cuda-9.0
* Nvidia-driver-390
* cudnn-7.1
* tensorflow-gpu-1.8
## 安装流程
* 确认是否符合官网CUDA的要求
* 安装python3.6.5，奇怪的是安装python官网的python3.6.5.rc1没有问题，但是python3.6.5却出现找不到ssl模块的错误，注意是编译安装，官网的包是不能直接rpm安装的
* 安装显卡驱动
  * 需要先对源进行更新，换用清华源，可百度“清华yum源”
  * 更换为清华源后安装epel源，CentOS直接yum install epel-release 即可，或进入官网  http://fedoraproject.org/wiki/EPEL 按照提示操作
  * 添加elrepo源，官网网址：http://elrepo.org/tiki/tiki-index.php，直接按照操作复制粘贴代码即可
  * 更新yum，运行 yum clean all,再运行 yum makecache即可
  * 禁用自带的nouvea驱动，设置开机默认进入命令行模式
  * 下载nVidia的本地rpm包，网址：https://www.geforce.cn/drivers#，选择Linux 64-bit版本即可，找个稳定版，一般新的显卡找最新的驱动比较好
  * 运行该.run文件，一路选确定
  * 安装完之后运行nvidia-smi测试是否有正常输出
* 安装cuda
  * 下载cuda9.0，很多人说找不到cuda9.0的下载页面，只要bing或者baidu时搜索cuda9.0即可
  * 先本地rpm安装文件，这里其实是加入了cuda9.0的源，并非正式安装
  * 运行 yum install cuda
  * 输出完成之后添加必要路径，请见官方document中的post install？？？并且修改~/.bashrc文件
* 安装cuDNN 7.1
  * 搜索cudnn即可，前往官网注册账号并下载library for linux版本
  * 解压cudnn，并将文件复制到对应的文件夹下
  * 更改两个文件夹的权限
* 安装tensorflow-gpu
  * 运行 python3 -m pip install tensorflow-gpu
  * 输入python3，进入python环境，输入import tensorflow as tf看是否导入模块有问题，如无问题则运行官网示例代码，如运行后输出有显示titan v相关信息则安装成功
* 一些坑
  * tensorflow上说安装完cuda，cudnn之后要安装一些工具，实际上是不用的，这些在cuda-9.0安装的过程中已经是自动安装好了的
  * 基本上，对源进行补充完整之后安装软件会更好，谨防出现依赖包问题
  * 不要相信网上说安装nvidia的kmod-nvidia或者是rpm包直接安装，认定官网的Linux版本不动摇，运行.run文件不动摇，一路确定选yes不动摇
* 感慨
  * Nvidia的驱动，还是需要禁用原来源的自带的闭驱动，并且禁用掉，在禁用的过程中记得更改文件最好做一次备份
  * 网上Ubuntu安装cuda9.1等新版的较多，实际上CentOS的版本还是要旧的比较靠谱
  * 资源多不代表一定正确，注意硬件和系统配置，注意各软件的位数，不是amd64,而是x86_64
