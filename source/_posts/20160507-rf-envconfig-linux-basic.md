title: RF环境安装-linux-基础环境-安装指南
tags:
  - robotframework
categories:
  - 自动化测试
date: 2016-05-07 14:30:46
description:
---
今天来介绍一下Linux环境下Robotframework的环境安装，主要基于Ubuntu desktop版本，即有可视化操作界面的，其他版本如果有可视化界面请参考安装步骤进行安装，如果没有可视化界面，只有命令行的话，请跳过第2步和第4步（第5步只能用命令行运行pybot，以后在介绍）

## 一、适用环境：
Linux系列，Ubuntu，其他版本Linux可参考

## 二、简要步骤：
1. 安装pip，自带Python环境，所以我们改成安装pip
2. 安装wxPython，使用apt-get命令安装。
3. 使用pip install安装robotframework
4. 使用pip install安装robotframework-ride
5. 完成基础环境安装，简单验证


===== 接下来多图预警，土豪随意 =====

<!-- more -->

## 三、详细步骤：

1. 安装pip

接下来的操作都要在终端里进行，所以进入系统后第一件事情就是打开终端。

Linux一般都是默认安装了Python了，如果没有安装Python，建议使用如下命令安装：
`sudo apt-get install python-dev`

在Ubuntu和centos上都已经默认安装了Python，Ubuntu是Python2.7.5，centos7上是Python2.7.5，centos6上好像是2.6.6，查看当前Python版本的命令是：

`python -V`

推荐在Python2.7系列下进行安装，如果是2.6的可能会有问题，可以搜索一下如何把2.6替换成2.7的，这个替换如有需要改天我发一篇参考的。本文假定你的Python已经是2.7系列了。

安装pip的命令：

`sudo apt-get install python-pip`

2. 安装wxPython

不同于windows和mac系统，Linux可以用apt-get来安装wxPython，但是对于没有可视化界面的Linux系统来说，因为没有界面，基本上就不需要安装wxPython和RIDE了，这里我以Ubuntu为例继续介绍，具体命令为：

`sudo apt-get install python-wxgtk2.8`

这个安装的也是wxPython2.8的版本

3. 安装Robotframework

继续在终端里输入命令

`sudo pip install robotframework`



看到Successfully就是安装完成了。

4. 安装Robotframework-ride

继续在终端安装ride，执行命令：

`sudo pip install robotframework-ride`

看到Successfully就是安装完成了。

5. 简单验证

因为前面安装的时候可执行文件都配置好了，所以我们只需要在终端里输入ride.py

看到如下界面就是安装成功了。

接着写个简单的hello world

运行一下


看到绿色的标示就是成功了，案例状态也显示PASS了。

感谢网友antZ提供wxPython安装参考，按他的说法Ubuntu是最适合Robotframework的系统了，从界面看，确实比较好看，以后会不会有问题还不知道。

基础环境系列就差不多了，后面我们就针对各个测试库来介绍如何安装了。接下来第一个介绍的应该是数据库相关的，也就是DatabaseLibrary，这个库我会分别介绍Sqlite、Oracle、Mysql的测试库安装和使用。

