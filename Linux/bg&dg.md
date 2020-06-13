@[toc]
# linux 中的bg 和dg 技巧

## 页面跳转

[返回网站首页](https://ryancatalina.github.io/)

[返回Linux 的主页](/index.md)

# 前言
Linux虐我千万遍，我待它如初恋。说到这个系统让我又爱又恨，今天安装leanote的时候在Linux命令上足足耗费了3个钟头，说到底还是当初的Linux课没有意识到这两个符号的意义啊，好后悔，所以准备写篇博客来让自己巩固这个知识点，所谓温故而知新，你说是不是。
# &、ctrl + z、ctrl+c、jobs、fg、bg理解
## & 经常被用到
这个用在命令的最后，可以把这个命令放到后台执行
## ctrl + z
将一个正在前台执行的任务放到后台，并且暂停，用术语讲就是**挂起**
## ctrl + c
将一个正在前台执行的任务终止执行，也就是常说的结束任务，术语：终止
## jobs
查看当前有多少在后台运行的命令
## fg
将后台中的任务、命令调至前台继续运行
如果后台中有多个命令，可以用 fg %jobnumber将选中的命令调出
## bg
将后台中暂停（挂起）的命令、任务调至前台继续运行
如果后台中有多个命令，可以用bg %jobnumber将选中的命令、任务调出执行
## 特别注意
%jobnumber是通过jobs命令查到在后台正在执行的任务的序号，注意它不是pid
# 实例
其实我们都知道，挂起、终止的意思，在Linux中Ctrl+Z式挂起的意思，跟中止一样的意思，按下之后终端的提示是：
```
[1]+ Stopped /root/bin/rsync.sh
```
[1]中的1为作业号
然后我们可以把程序从挂起状态调度到后台执行：（bg后面的数字是作业号）
```
#bg 1
[1]+ /root/bin/rsync.sh &
```
这里终端给出的反馈中有个&符号，它的意义是后台运行
可以用jobs命令查看正在运行的任务：
```
#jobs
[1]+ Running /root/bin/rsync.sh &
```
如果你想把它调回到前台运行可以用`fg 作业号`的形式，只不过这样就必须在控制台中等待其完成
```
#fg 1
/root/bin/rsync.sh
```
fg、bg、jobs、&、ctrl+z都是跟系统任务有关的，虽然现在基本上不怎么需要用到这些命令，但学会了也是很实用的，就拿今天的安装leanote来说，因为不清楚ctrl+z是挂起,ctrl+c是终止的意思和相关操作，而浪费了大量的时间，甚是可惜。
# 最后来一句slogan
"我们登上并非我们所选择的舞台，演绎并非我们选择的剧本"。
既然幕已拉起，那就应该把这出戏演好。
奥力给！！！！！！！！！