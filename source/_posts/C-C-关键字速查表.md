title: C/C++关键字速查表
author: 田亮
abbrlink: bc59
tags:
  - C
categories:
  - C
date: 2019-04-22 09:02:00
---
## 语法速查表
<!--more-->

|关键字|用法|解释|其它|
|:-:|:-:|:-:|:-:|
|printf|printf("%d",a)|打印到控制台|无
|scanf|scanf("%d,%d",a,b)|用户输入|%d,%d 中间的逗号可以是任意字符,但是用户在输入中必须有这个逗号
|putchar|putchar(c)|打印一个字符到控制台|为char类型定制
|getchar|char a = getchar()|只输出用户输入的第一个字符,忽略其它|为char类型定制
|return|return 0|返回一个数给调用它的|无
|puts|puts(a)|输出字符串,并且识别转义字符|可以输出char类型数组
|gets|gets(str)|输入字符串|为char类型定制
|strcat|strcat(str,str2)|字符串连接|使用%s类型
|strcmp|strcmp(str,str2)|字符串比较|使用%s类型输出
||||
||||
||||
||||
||||
||||