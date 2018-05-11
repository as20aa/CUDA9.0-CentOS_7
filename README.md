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
* 安装显卡驱动
** 需要先对源进行更新，换用清华源，可百度“清华yum源”
** 更换为清华源后安装epel源，CentOS直接yum install epel-release 即可，或进入官网  http://fedoraproject.org/wiki/EPEL 按照提示操作
** 添加elrepo源，官网网址：http://elrepo.org/tiki/tiki-index.php，直接按照操作复制粘贴代码即可
** 更新yum，运行 yum clean all,再运行 yum makecache即可
** 下载nVidia的本地rpm包，网址：
