# Docker基本概念

## 页面跳转

[返回首页](https://ryancatalina.github.io/)

## layer

Docker 和Docker Hub的关系就相当于Git 与GitHub 之间的关系。

Docker 在很多方面都借鉴了Github。

Docker 使用layer 的概念，你可能会发现，有许多个lay 的编号相同，每个layer 都有唯一的id。

## 拉取镜像

docker pull [image]

## 搜索镜像

语法：docker search [option] keyword

option:

    -f,--filter filter: 过滤输出内容
    --format string：格式化输出内容
    --limit int：限制输出结果个数，默认为25个
    --no-trunc：不截断输出结果

## 查看镜像信息

### 使用images 命令列出镜像

使用docker images或docker image ls 命令列出已有的镜像基本信息。

images 子命令支持的[options]

    -a, --all=true|false: 列出所有（包括临时文件）镜像文件，默认否
    --digests=true|false: 列出镜像的数字摘要值，默认为否
    -f,--filter=[]: 过滤列出的镜像，如dangling=true 只显示没有被使用的镜像；也可指定带有特定标注的镜像
    。。。。。。

更多可使用man docker-images 查看命令

### 使用tag 命令添加镜像标签

命令格式：docker tag [image:tag(修改前)]  [image:tag(修改后, image和tag 都可修改)]

### 使用inspect 命令查看详细信息

使用docker [image] inspect 命令可查看镜像详细信息,返回的json 格式，包括制作者、适应架构、各层的数字摘要等。

option:

    -f: 可指定想要的信息
    eg: docker [image] inspect -f {{".Architecture"}} ubuntu:18.04

### 使用history 命令查看镜像历史

命令格式：
    docker history [image:tag]

options:
    --no-trunc 输出查询结果中的完整命令

## 删除和清理镜像

### 使用标签删除镜像

使用docker rmi 或 docker image rm命令可以删除镜像，
命令格式：docker rmi IMAGE [IMAGE...],其中IMAGE可以为标签或ID。

options:

    -f,-force: 强制删除镜像，即使有容器依赖它
    -no-prune: 不清理未带标签的父镜像

注意：当镜像文件有多个标签的时候，会先删除标签，直到只有最后一个标签，才会彻底删除镜像文件。

### 使用镜像id 来删除镜像

命令格式：docker rmi 镜像id

option 可参考上一条

### 清理镜像

使用docker 一段时间后，系统中可能会遗留一些临时的镜像文件，以及一些被使用的镜像。

命令格式： docker image prune

option:

    -a,-all: 删除所有无用的镜像，而不光是临时镜像
    -filter filter: 只清理符合给定的过滤器对象
    -f,-force: 强制删除镜像，而不进行提示确认

