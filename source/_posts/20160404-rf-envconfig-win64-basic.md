title: RF环境安装-windows64位-基础环境-安装指南
tags:
  - robotframework
categories:
  - 自动化测试
date: 2016-04-04 14:31:56
description:
---

这篇内容其实和前一篇差不多，只是在几个关键的地方换成64位的文件即可。所以安装步骤就不详细说了，顺手说一下pip。

## 一、适用环境：
Windows系列，64位Python

## 二、简要步骤：
1. 安装Python，此处我下载的版本是Python-2.7.11.amd64.msi
2. 安装wxPython，此处我下载的版本是wxPython2.8-win64-unicode-2.8.12.1-py27.exe
3. 使用pip install安装robotframework
4. 使用pip install安装robotframework-ride
5. 完成基础环境安装，简单验证

<!-- more -->

## 三、详细步骤：

由于这篇和前一篇内容是差不多的，所以简单步骤其实是一样的，只是下载的2个文件是需要64位的。
![](https://codingstyle-cn.b0.upaiyun.com/photo/2016/c25f8ff9ac43201129c7ca32914be1ab.png)

第一个是Python的文件，这里下载的文件是python-2.7.11.amd64.msi，比前一篇下载的文件多了amd64几个字，这个标明是适用于64位操作系统的。

第二个是wxPython的文件，确认名字是wxPython2.8-win64-unicode-2.8.12.1-py27.exe，不要有差错。
win64是因为Python是64位的，unicode是必须的，2.8.12.1是RIDE稳定支持的版本，py27是Python2.7系列的，因为Python是64位的，所以其他配套的程序都要以Python为准，也要64位的。

后面的安装步骤和32位的没有什么差异，步骤都一样就没必要再搞一遍多图了，具体步骤请参考前一篇32位的。

[32位安装指南](/2016/03/31/20160331-rf-envconfig-win32-basic/)

## 四、pip
那么我们顺便来说一下pip吧，以前的版本都要自己单独安装pip，单独安装pip我其实比较推荐去下载源码包的方式，pip官网（pip.pypa.io）倒是提供了一个get-pip.py文件的方式，我之前用过一次，貌似不知什么原因安装完成后pip命令还是用不了，后来还是用源码包安装解决了，所以反正都是要下载个文件，不如一步到位吧。

pip是从Python2.7.9开始集成到Python安装包里了，不过版本略旧，需要升级一下，上次我们升级pip用的是下面这个命令

`python -m pip install --upgrade pip`

也可以简化一些：

`pip install --upgrade pip`

如果还想再少打几个字，可以把--upgrade换成-U，即：

`pip install -U pip`

通常来说，新安装一个包，pip的语法是：

`pip install pkgname`

比如我们安装Robotframework的时候就是下面的命令

`pip install robotframework`

当时我们还加了==3.0，这是指定要pip安装这个包的特定版本号的，有些时候新出来的包还有问题，那就可以用这种方式安装旧的版本。

如果后面你要升级一个包，pip的语法是：

`pip install --upgrade pkgname`

`pip install -U pkgname`

前面pip的升级就是例子了。

在我的新书里，其实最开始我对pip用的并不多，主要是因为当时在公司的网络环境限制，pip无法发挥它的作用，在我写书的后半段因为用Mac电脑，用pip真是得心应手，所以后面有些章节我也推荐大家使用pip安装，特别是rf-demos（github.com/qitaos/rf-demos）里。

如果你的网络环境受限制，pip用不了，那么你只能很悲催手动下载源码包安装了，而且遇到有依赖的时候，更是要一个个依赖下载下来，我以前经历过这种痛苦，所以pip极大地解决了这个痛苦。

希望这里的安装说明对大家有用。