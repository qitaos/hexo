title: RF环境安装-mac-osx10.10-基础环境-安装指南
tags:
  - robotframework
  - mac
categories:
  - 自动化测试
date: 2016-04-17 13:13:04
description:
---
接着说mac的基础环境安装，本篇以osx10.10为例进行介绍。

## 一、适用环境：
mac系列，osx10.10，自带Python

## 二、简要步骤：
1. 安装pip，mac自带Python环境，所以我们改成安装pip
2. 安装wxPython，此处我下载的版本是wxPython2.8-osx-unicode-2.8.12.1-universal-py2.7.dmg
3. 使用pip install安装robotframework
4. 使用pip install安装robotframework-ride
5. 完成基础环境安装，简单验证

===== 接下来多图预警，土豪随意 =====

<!-- more -->

## 三、详细步骤：

1. 安装pip
mac自带Python环境，可以打开Finder-前往-实用工具，打开终端，输入命令
`python -V`
所以我们只需要安装pip就好了，pip安装有很多方法，我这里推荐一种最保险的。
访问这个地址：https://pypi.python.org/pypi/pip

下载最新版本的pip的tar.gz包，写本文时最新的pip版本是8.1.1，所以我们下载pip-8.1.1.tar.gz，下载后双击文件自动解压缩，然后我们在终端里进入解压缩后的目录，

`cd Downloads/pip-8.1.1
sudo python setup.py install`

mac里记得要加sudo提权，执行完成后别关窗口，后面还有用。


2. 安装wxPython
当前这个操作系统的版本osx10.10还是可以安装wxPython2.8.12.1的。
下载地址：https://sourceforge.net/projects/wxpython/files/wxPython/2.8.12.1/

把鼠标悬浮到每一个文件上看完整的文件名，确认名字是wxPython2.8-osx-unicode-2.8.12.1-universal-py2.7.dmg，不要有差错。
osx是给mac用的，unicode是必须的，不要下载ansi版本，2.8.12.1是RIDE稳定支持的版本，py27是Python2.7系列的，不要下错2.6的。


3. 安装robotframework

我们继续在终端里执行命令，来安装Robotframework：

`sudo -H pip install robotframework`

其实加sudo就够了，不过有时候会有警告，建议加上-H。

看到Successfully就是安装完成了。
如果没有看到Successfully，有可能你的网络有问题，因为这种安装方式都是依赖网络的。

如果你的网络无法安装，那么只能先去下载Robotframework的源码包，安装方法可以参考前面pip安装或者看一下windows32位环境安装里面的安装Robotframework这一块内容。


4. 安装robotframework-ride

继续在终端安装ride，执行命令：

`sudo -H pip install robotframework-ride`

安装成功后，在终端执行ride.py


python should be executed in 32-bit mode with wxPython on OSX.

如果看到这一句，是因为默认mac下的Python是以64位模式运行的，但是wxPython必须要在32位Python模式运行，这里具体方式有两种: 
a.在终端里执行下面这句`defaults write com.apple.versioner.python Prefer-32-Bit -bool yes`
b.或者在~/.bash_profile里增加下面这句: `export VERSIONER_PYTHON_PREFER_32_BIT=yes`
保存退出后运行source ~/.bash_profile后就可以正常打开RIDE了。

5. 完成基础环境安装，简单验证

在终端里输入ride.py

看到如下界面就是安装成功了。

接着写个简单的hello world

运行一下


看到绿色的标示就是成功了，案例状态也显示PASS了。

mac10.10的基本环境就安装好了，有问题的话请留言提问。
