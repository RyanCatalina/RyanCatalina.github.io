# Git 中branch

## 页面跳转

[返回网站首页](https://ryancatalina.github.io/)

[返回git 主页](/index.md)

## branch 介绍

分支是为了将修改记录的整体流程分叉保存，分叉后的分支不受其他分支的影响，所以在同一数据库里可以同时进行多个修改。
分叉的分支可以合并。

![](img/git1.jpg)

## Merge 分支

Merge分支是为了可以随时发布release而创建的分支，它还能作为Topic分支的源分支使用。保持分支稳定的状态是很重要的。如果要进行更改，通常先创建Topic分支，而针对该分支，可以使用Jenkins之类的CI工具进行自动化编译以及测试。

通常，大家会将master分支当作Merge分支使用。

## Topic 分支

Topic分支是为了开发新功能或修复Bug等任务而建立的分支。若要同时进行多个的任务，请创建多个的Topic分支。

Topic分支是从稳定的Merge分支创建的。完成作业后，要把Topic分支合并回Merge分支。

## 建立分支

创建newbranch 分支

git branch newbranch

## 查看branch 列表

git branch

## 切换HEAD 到指定的branch

git checkout <branch>

切换待newbranch 分支
git checkout newbranch

在checkout 命令指定-b 选项执行，可以创建分支并进行切换

```
git checkout -b <branch>
```

## 合并分支

合并分支是向HEAD 指向的分支合并，一般先切换到主分支
git checkout master
再merge 分支
git merge newbranch

## 删除分支

在branch 命令指定-d 选项执行，以删除分支

git branch -d <branchname>

例如执行以下的命令删除newbranch 分支

git branch -d newbranch

## 解决合并的冲突

先分别创建两个分支，再进行添加修改删除等操作，最后通过git add/commit 等命令完成分支编写。

最后切换到master 分支，使用git merge 执行合并，一般第一次合并为fast-forward(快进)合并，
接下来的一般是non fast-forward 合并。

## fetch 命令

执行pull，远程数据库的内容就会自动合并。而使用fetch 则不会合并，执行fetch 就可以取得远程数据库的最新历史记录，取得的提交会导入到没有名字的分支，这个分支可以从名为FETCH_HEAD 的退出。

合并后，历史记录会和pull 相同，实际上pull 的内容是fetch + merge 组成的。