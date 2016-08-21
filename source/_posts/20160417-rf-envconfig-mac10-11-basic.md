title: RF环境安装-mac-osx10.11-基础环境-安装指南
tags:
  - robotframework
categories:
  - 自动化测试
date: 2016-04-17 13:13:17
description:
---
本来这篇应该是在10.10的环境配置文章发布后再发的，但是考虑到广大使用mac-osx10.11的同学，还是在公众号里先发这篇。重复的部分请参考osx10.10那篇，10.10的那篇一起写好了，第二天发。

## 一、适用环境：
mac系列，osx10.10，自带Python

## 二、简要步骤：
1. 安装pip，mac自带Python环境，所以我们改成安装pip
2. 安装wxPython，此处我是拷贝的wxPython来用的。
3. 使用pip install安装robotframework
4. 使用pip install安装robotframework-ride
5. 完成基础环境安装，简单验证


===== 接下来多图预警，土豪随意 =====

<!-- more -->

## 三、详细步骤：

1. 安装pip
此内容请参考osx10.10的基础环境配置。


2. 安装wxPython
在10.10的时候我们是安装wxPython那个dmg文件就行了，如果你在10.10已经安装过了wxPython2.8.12.1，然后再升级到10.11，其实是没问题的。现在很多同学在10.11的环境里新安装wxPython2.8.12.1就遇到问题了。

找了一下解决方案：
http://stackoverflow.com/questions/33134896/install-wxpython-2-8-for-ride-on-osx-el-capitan

stackoverflow这里之前只有源码安装2.9.5的方案，后面群友补充了一个用homebrew安装wxPython3.0的方案，但是这两个方案都存在不好的地方，每次关掉RIDE打开都需要删除缓存文件，另外3.0的文本框实在是小的难以形容，希望以后RIDE2.0能解决这些问题。

但是现在光等也没用，前两天突然灵感一现，想到了一个方案。前面我说了，在10.10里安装wxPython然后升级10.11是没问题的，这一点是我之前亲身经历过的，当时升级到了10.11的beta版本，ride还是可以正常使用的，只是后来实在不喜欢10.11，我把硬盘格了装回10.10了，现在苹果还偷偷的帮我下了10.11让我升级，我暂时打死也不升级。。

扯远了，既然升级没问题，那么我就想，把10.10里的wxPython安装后的目录找到，直接放到10.11上，然后再解决引用wxPython的问题应该就可以解决了。于是我在iMac和虚拟机上都进行了试验，结果证实了我的方案是可行的，因此在这里分享给大家，如果解决了你的困扰，不用口头感谢我，用赞赏可劲儿的砸我就行了。

首先说一下方案思路，我先在10.10里找wxPython的安装目录，在windows里其实它是在Python的site-packages目录里，在mac里不是这样，mac的site-packages目录是Library/Python/2.7/site-packages/，在这里我只找到了wxredirect.pth这个文件，根据这个文件的内容，找到了wxPython的目录在
/usr/local/lib/wxPython-unicode-2.8.12.1/

所以我把pth文件和wxPython的目录都拷贝到10.11里，然后按一样的进行配置，就完成了wxPython的安装。

这里我共享了这两个文件，请在你的Mac里下载下来

在下载目录里双击wxPython-2.8.12.1.zip文件，等待它解压缩完成，解压后的目录是wxPython-unicode-2.8.12.1。

接着是操作步骤：
a. 拷贝pth文件到指定目录

sudo cp ~/Downloads/wxredirect.pth /Library/Python/2.7/site-packages/

b. 拷贝wxPython目录到指定目录

在执行命令之前，请先确保你的/usr/local/lib目录是存在的，如果lib目录没有请自己创建一个:
sudo mkdir /usr/local/lib
如果已经有lib目录就不用创建目录了，直接执行下面的语句
sudo cp -r ~/Downloads/wxPython-unicode-2.8.12.1/ /usr/local/lib/wxPython-unicode-2.8.12.1/
拷贝完成后，确保/usr/local/lib/wxPython-unicode-2.8.12.1/目录下是bin、include、lib、share四个目录。

这样就完成了wxPython的安装了，然后请自行完成ride的安装（或参考10.10的）。

因为wxPython2.9和3.0都是默认64位的，在运行ride.py时不会提示32位Python的（2.9我不太确认），而我们拷贝过来的2.8.12.1的版本是32位的，所以在完成wxPython安装后，运行ride.py会提示这个：
python should be executed in 32-bit mode with wxPython on OSX.

这个32位提示的解决方案请参考10.10的配置说明。

这里我们简单用一个命令处理一下，在终端运行命令：
`defaults write com.apple.versioner.python Prefer-32-Bit -bool yes`


3. 安装robotframework
此内容请参考osx10.10的基础环境配置。


4. 安装robotframework-ride
此内容请参考osx10.10的基础环境配置。


5. 完成基础环境安装，简单验证

确保wxPython安装完成后，在终端里输入ride.py

看到如下界面就是安装成功了。

接着写个简单的hello world

运行一下


看到绿色的标示就是成功了，案例状态也显示PASS了。

前面写脚本的时候字体有点小，这个可以在Tools-Preferences菜单里修改Grid Editor，修改后的效果

mac10.11的基本环境这里主要介绍了wxPython的安装，其他的估计大家问题不大，有问题的话看下一篇10.10的配置指南吧，希望能解决大家遇到的问题。
