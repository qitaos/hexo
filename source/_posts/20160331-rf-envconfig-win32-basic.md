title: RF环境安装-windows32位-基础环境-安装指南
tags:
  - robotframework
  - windows
categories:
  - 自动化测试
date: 2016-03-31 21:00:08
description:
---

前面该说的都说了，下面开始正式进入基础环境安装指南。

## 一、适用环境：
Windows系列，32位Python

## 二、简要步骤：
1. 安装Python，此处我下载的版本是Python2.7.11.msi
2. 安装wxPython，此处我下载的版本是wxPython2.8-win32-unicode-2.8.12.1-py27.exe
3. 使用pip install安装robotframework
4. 使用pip install安装robotframework-ride
5. 完成基础环境安装，简单验证

===== 接下来多图预警，土豪随意 =====

<!-- more -->

## 三、详细步骤：

1. 安装Python

访问Python的下载地址：https://www.python.org/downloads/release/python-2711/
![](https://codingstyle-cn.b0.upaiyun.com/photo/2016/93a7ffbeb4c426c23d51c20645d6c973.png)
如果以后有新版可以在官网首页看一下是什么版本了，我们需要下载Python2.7系列的，现在最新的是2.7.11，所以我下载Python2.7.11.msi文件，这个是32位的。

下载后双击文件运行
![](https://codingstyle-cn.b0.upaiyun.com/photo/2016/d1f57d8a3372aa4b24bad73fd5748b67.png)

这里直接点Next就行了
![](https://codingstyle-cn.b0.upaiyun.com/photo/2016/ec549f739de84a656750e2a97d0b73f2.png)

这里设置Python的目录，默认是C:\Python27\，你可以改成D盘或其他盘，但是最好不要选择有中文或空格的目录（比如Program Files），因为以后你安装其他库会遇到问题（尤其是AutoItLibrary）。设置好之后点Next继续
![](https://codingstyle-cn.b0.upaiyun.com/photo/2016/eee8865b0f1df5340f1d697e9d26c8cd.png)

看到这个界面，把上面的滚动条拉到最下面，有一个Add Python.exe to Path，默认左边的图标是红色的叉，也就是不会在安装时执行。以前都是让大家手动添加，很多人容易漏加Scripts目录，这里安装的时候会自动帮你装好。
我们点击这一项左边的下拉箭头，选择第一项：“Will be installed on local hard drive”。
顺带提一句，这里倒数第三项的pip非常好，不需要自己单独下载了，接下来用处很大。之后就一路Next完成安装即可。
![](https://codingstyle-cn.b0.upaiyun.com/photo/2016/d6247e59aca92575e7206d4e8b3c41d6.png)

安装完成后我们可以看一下环境变量，这里已经帮我们添加好需要添加的两个路径了。
![](https://codingstyle-cn.b0.upaiyun.com/photo/2016/12f7a5eee3a2dd336de91cb719d97e17.png)

2. 安装wxPython
为了用到后面的RIDE，我们需要先安装wxPython，虽然RIDE已经在2.0alpha版本开始用3.0的，但是貌似新版还有很多坑，先别急着踩坑了，还是用稳定的wxPython2.8.12.1吧。
下载地址：https://sourceforge.net/projects/wxpython/files/wxPython/2.8.12.1/
![](https://codingstyle-cn.b0.upaiyun.com/photo/2016/136cbe5a161ad78fe94891991c93b84a.png)

由于文件名字太长，需要把鼠标悬浮到每一个文件上看完整的文件名，确认名字是wxPython2.8-win32-unicode-2.8.12.1-py27.exe，不要有差错。
win32是因为Python是32位的，unicode是必须的，不要下载ansi版本，2.8.12.1是RIDE稳定支持的版本，py27是Python2.7系列的，不要下错2.6的。
![](https://codingstyle-cn.b0.upaiyun.com/photo/2016/c70039699d0669b47af6601bb5909d2a.png)

双击下载exe文件
![](https://codingstyle-cn.b0.upaiyun.com/photo/2016/80749d446f174536013dd8a79f3b4802.png)

点击Next
![](https://codingstyle-cn.b0.upaiyun.com/photo/2016/b7a5c313acfc219068f2ce5c160c8867.png)

选择I accept那一项，点击Next
![](https://codingstyle-cn.b0.upaiyun.com/photo/2016/5a92807b8271d3ecd212a982baf44cf0.png)

这里不用管，直接一路Next安装完成就行。

3. 安装robotframework
Python2.7.11这个版本自带了pip（我不记得从哪个版本开始有pip的，印象里之前的版本都没有的），所以安装好Python后就不需要单独安装pip了，我们直接在打开运行，输入cmd
![](https://codingstyle-cn.b0.upaiyun.com/photo/2016/3ecf1f3bfbc0af2373e27b223efae294.png)

点击确定后进入命令行界面，先输入pip list看看都安装了什么，貌似pip版本比较旧了
![](https://codingstyle-cn.b0.upaiyun.com/photo/2016/e09b9612d786164e3b23150a3d2278f7.png)

按照提示输入以下命令升级一下pip：
`python -m pip install --upgrade pip`

![](https://codingstyle-cn.b0.upaiyun.com/photo/2016/214fc31e6ad1f0ba6727730c205af107.png)

看到Successfully这一句就是表示升级安装完成了，在用pip list看一下，pip的版本已经升级到8.1.1了。
接下来我们用pip来安装Robotframework：

`pip install robotframework==3.0`

![](https://codingstyle-cn.b0.upaiyun.com/photo/2016/5d488654037e82b88e09ddc924c2ff30.png)

一般情况下后面的 ==3.0 这部分不需要输入的，这是指定特定版本安装的语法，如果不加也没问题，默认是安装最新的版本。
![](https://codingstyle-cn.b0.upaiyun.com/photo/2016/c935fa0851255316e020bb0707113c19.png)

看到Successfully就是安装完成了。
如果没有看到Successfully，有可能你的网络有问题，因为这种安装方式都是依赖网络的。

如果你的网络无法安装，那么只能先去下载Robotframework的源码包，这里提供两个地址：
https://github.com/robotframework/robotframework/releases
https://pypi.python.org/pypi/robotframework

两个地方都有最新的包，以3.0版本为例，robotframework-3.0.tar.gz文件就是我们需要下载的，下载后解压缩，从命令行进入解压缩后的目录（有setup.py文件的那一层），输入命令：

`python setup.py install`

如果失败，很可能是你当前的目录不在setup.py文件那一层。这种方式就没单独准备图了。

4. 安装robotframework-ride

输入安装命令：
`pip install robotframework-ride`

![](https://codingstyle-cn.b0.upaiyun.com/photo/2016/a80702ba7523720dc35e22eec4193d75.png)

比如这次我们没有输入特定版本号，他就安装了最新的1.5.2.1版本。
![](https://codingstyle-cn.b0.upaiyun.com/photo/2016/9c55c7b7e4ae99a8404315feeaf26992.png)

同样看到Successfully就是安装成功了。

如果没有成功的话，请参考Robotframework下载源码安装的方式，下载ride的源码，同样提供两个地址：
https://pypi.python.org/pypi/robotframework-ride
https://github.com/robotframework/RIDE/releases

这里不推荐使用exe安装的，虽然有快捷图标，但是其实命令行运行也很方便的，并且有问题的时候命令行能看到错误日志。当然，如果你很喜欢快捷图标的话，后面的文章我会写一下怎么自己做一个。

5. 完成基础环境安装，简单验证

此时基础环境基本上都安装好了，我们来简单验证一下。
在命令行输入ride.py：
![](https://codingstyle-cn.b0.upaiyun.com/photo/2016/0c0e75fd5108be9e8fac6bef464a91f8.png)

看到如下界面就是安装成功了。
![](https://codingstyle-cn.b0.upaiyun.com/photo/2016/06ae4e97a0a559fa60ad59506216b35b.png)

我的电脑在打开RIDE的同时出现了防火墙阻拦，直接点击允许访问就好了。
![](https://codingstyle-cn.b0.upaiyun.com/photo/2016/210e92eddedd5c990f26c2cc127cc53f.png)

接着写个简单的hello world吧
![](https://codingstyle-cn.b0.upaiyun.com/photo/2016/1cb2e555033fc05bcdddd650bde7fdfb.png)

运行一下
![](https://codingstyle-cn.b0.upaiyun.com/photo/2016/dc2bec22131f58730aa0bb62fa0ec242.png)

看到绿色的标示就是成功了，案例状态也显示PASS了。

至此Windows-32位的基础环境就安装好了，希望你们也一样顺利的完成安装。

>可惜我的公众号不能认证，发url什么的不能直接变成链接，太不方便了。
