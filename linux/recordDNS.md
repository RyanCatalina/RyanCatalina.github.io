# DNS 中的record

## 页面跳转

[返回网站首页](https://ryancatalina.github.io/)

[返回Linux 的主页](/index.md)

## DNS 中的记录有哪些

A、C name、NS(nameserver)、MX(Mail Exchanger record)、PTR、SPF、TXT 等记录。

## A（Address）记录

使用来指定域名（或主机名）对应的IP 地址记录。用户可以将该域名下的网站服务器指向到自己的web server 上，同时也可以设置你域名的二级域名。

## 别名（CNAME）记录

也常常被称为规范名字。这种记录允许你将多个名字映射到同一台计算机。通常用于同时提供www 和mail 服务的计算机。例如，有一台计算机有一条A 记录：“host.mydomain.com”。它同时提供www 和mail 服务，以便于用户访问服务。可以为该计算机设置两个别名（CNAME）：www 和mail。这两个别名的全称就是“www.mydomain.com”和“mail.domain.com”。实际上它们都指向“host.mydomain.com”。同样的方法可以用于当你拥有多个域名需要指向同一服务器IP，此时您就可以将一个域名做A 记录指向服务器IP然后将其他的域名做别名到之前做A 记录的域名上，那么当你的服务器IP 地址变更时你就可以不必麻烦的一个一个域名更改指向了，只需要更改做A 记录的哪个域名其他做别名的哪些域名的指向也将自动更改到新的IP 地址上了。

使用"nslookup -q=cname 对应的域名或二级域名"，即可检测出cname 记录。

## NS 记录

NS 记录全称为Name Server 是一种域名服务器记录，用来明确当前你的域名是由哪个DNS 服务器来解析的。

## MX 记录

Mail Exchanger 记录，是邮件交换记录，它指向一个邮件服务器，用于电子邮件系统发邮件时根据收信人的地址后缀来定位邮件服务器。例如，当Internet 上的某用户要发一封信给user@mydomain.com 时，该用户的邮件系统通过DNS 查找mydomain.com 这个域名的MX 记录，如果MX 记录存在，用户计算机就将邮件发送到MX 记录所指定的邮件服务器上。

## TXT 记录

TXT记录一般指为某个主机名或域名设置的说明，如：

    1）admin IN TXT "jack, mobile:13800138000"

    2）mail IN TXT "邮件主机, 存放在xxx ,管理人：AAA"，Jim IN TXT "contact: abc@mailserver.com"

也就是您可以设置 TXT ，以便使别人联系到您。

输入命令" nslookup -q=txt 这里填写对应的域名或二级域名"，查看TXT 记录。

## PTR

反向解析是从 IP 地址到域名的映射，相对于将域名映射到 IP 地址的正向解析。

因为一个IP可能被多个域名使用，所以在进行反向解析时要先验证一个 IP 地址是否对应一个或者多个域名。若从 IP 出发遍历整个DNS系统来验证，将会因工程浩大而无法实现。因此，RFC1035 定义了 PTR（Pointer Record）记录。PTR 记录将 IP 地址指向域名。

## SPF

SPF是为了防范垃圾邮件而提出来的一种DNS记录类型，它是一种TXT类型的记录，它用于登记某个域名拥有的用来外发邮件的所有IP地址。

例如:dig TXT 21cn.com

21cn.com. 27970 IN TXT "v=spf1 ip4:202.105.45.0/24 ip4:61.140.60.0/24 ip4:202.123.79.206 ip4:220.232.167.218 ip4:221.192.129.0/24 ip4:59.36.102.0/24 -all"

## banner 信息

一、什么是banner 信息

* Banner 信息，欢迎语，在banner 信息中可以得到软件开发商、软件名称、版本、服务类型等信息，通过这些信息可以使用某些工具去使用相对应的exp 去攻击

* 前提条件：需要和目标建立链接，只有建立了链接，我们才能获取对应的banner 信息

* 目标服务器上可以对banner 进行隐藏或禁止读取

二、收集方法

使用NC （netcat，瑞士军刀）

```
    nc -nv 192.168.1.1 21
        -n 表示以数字形式显示IP
        -v 显示详细信息
```

此外还有很多种方法

## bind 信息

1984年，加州大学伯克利分校的几个学生完成了Unix名称服务的实现，起名叫做Berkeley Internet Name Domain（BIND）。
目前，它是互联网上使用最为广泛的DNS服务软件。

bind的发行版一般包含三个部分：域名服务器、域名解析器库、软件测试工具。

如何获取DNS服务器的版本信息

向某个DNS服务器发送下面的请求即可获得版本信息

```
    dig @115.124.17.156 version.bind chaos txt
```
