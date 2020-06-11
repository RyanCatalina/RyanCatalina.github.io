@[toc]
# 配置git

## 页面跳转

[返回网站首页](https://ryancatalina.github.io/)

[返回git 主页](/index.md)

# 配置git


## 正文开始

git 中全局设置用户名、邮箱的操作如下，当然这一切的前提条件是已经安装好git 的客户端
程序。

## 查看git 所有的配置信息

git config --list

## 查看git 用户名

git config user.name

## 查看邮箱配置

git config user.email

## 全局配置用户名

git config --global user.name "youName"

## 全局配置邮箱

git config --global user.email "email@qq.com"

# 上传至GitHub 远程仓库

## 建立git 本地仓库

git init

## 创建你的文件

并在文件中修改、添加

## 将项目的所有文件添加到暂存区(stage)

git add .

## 将暂存区文件提交到数据目录

git commit -m "注释语句"

## 将本地仓库关联到GitHub上的仓库地址

git remote add origin https://github.com/你的github仓库地址

## 上传之前先pull，并确定修改

git pull origin master
或
git pull

## 上传

如果第一次上传会让你输入账户密码，之后就不用了

git push -u origin master
或
git push


## 更新代码

## 查看git 仓库状态

git status

## 更新全部

git add *

## 提交stage 至数据目录

git commit -m "尝试更新"

## 更新至远程仓库

git push -u origin master
或
git push