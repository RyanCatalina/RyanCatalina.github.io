@[TOC](apt-get 补全)

# linux 中的apt-get 包管理技巧

## 页面跳转

[返回网站首页](https://ryancatalina.github.io/)

[返回Linux 的主页](/index.md)

# 为什么写这篇博客
因为今天使用apt-get 安装软件的时候，突然想到了要是名字记不清能不能使用tab 键补全或查看有多少预选命令。
经过一段时间的查找资料，终于解决了我心中的疑惑，写这篇博客主要是为了记录学习的历程
# apt-get 介绍
Advanced Package Tool，又名apt-get，是一款适用于Unix和Linux系统的应用程序管理器。最初于1998年发布，用于检索应用程序并将其加载到Debian Linux系统。Apt-get成名的原因之一在于其出色的解决软件依赖关系的能力。其通常使用.deb-formatted文件，但经过修改后可以使用apt-rpm处理红帽的Package Manager（RPM）文件。
　　Apt-get在Linux社区得到广泛使用，成为用来管理桌面、笔记本和网络的重要工具。随着Linux在企业中的普及，Windows和Mac用户了解如何使用apt-get加载应用程序有一定的好处。
　　另外，随着单片机设备如Raspberry Pi的热度增加，apt-get在这些平台上是比较便捷的应用加载方式。如果你想要加载的应用需要程序库或另一个应用程序才能正常工作，apt-get会帮你找到并加载所需的程序库或应用代码。apt-get当前的稳定版本是1.0.9.2，在2014年10月发布。
　　使用apt-get的主流Linux系统包括Debian和Ubuntu变异版本。大多数情况下，从命令行运行该工具。桌面上有几个图形前端可以使用，包括Synaptic Package Manager、Ubuntu Software Center、Aptitude和Kpackage。Raspberry Pi和Beaglebone Black nanoLinux版用户可以很容易地使用apt-get加载程序，因为这些系统通常来自Ubuntu或Debian代码。是debian，ubuntu发行版的包管理工具，与红帽中的yum工具非常类似。
apt-get命令一般需要root权限执行，所以一般跟着sudo命令。

# 安装bash-completion
```
sudo apt-get install bash-completion
```
# 编辑~/.bashrc 文件
使用`vim ~/.bashrc`命令，在最后添加以下命令。若是对vim不熟悉，可以参考这两篇文章：
[给我五分钟，让你会用Vim](https://blog.csdn.net/weixin_44350891/article/details/104759565)
[重新定义后时代超神器---Vim ](https://blog.csdn.net/weixin_44350891/article/details/104760153)
```
if [ -f /etc/bash_completion ]; then
. /etc/bash_completion
fi
```
然后再重新打开终端或者重新连接ssh服务。

# 与你共勉
岂能尽如人意，但求无愧我心