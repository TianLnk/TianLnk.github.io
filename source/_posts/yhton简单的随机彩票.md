title: Pyhton简单的随机彩票
author: 田亮
tags:
  - python
categories:
  - python
abbrlink: h7oa
date: 2019-10-31 11:42:00
---
```python
# 制作一个随机抽选彩票的小程序
import random # 随机函数
def jizhu(): # 获取用户要买几注
	j = int(input("你要买几注呢？ ：  "))
	jici(j)

def suiji(): # 获取随机彩票
	cishu = [7,1,1,1,1,1] # 共 5个红球
	cishuLan = [1]
	cai =[] # 存储彩票
	qiu = 0
	for cishu in cishu:
		qiu = random.randint(1,36)
		cai.append(qiu)
	for cishuLan in cishuLan:
		qiu = random.randint(1,13)
		cai.append(qiu)
	print(cai)
	xieru(cai)

def jici(j): # 循环运行彩票函数
	for j in range(j):
		suiji()
def xieru(cai): # 输出彩票到文件
	with open("caipiao.txt","a") as xr:
		xr.write(str(cai)+"\r")

jizhu() # 程序入口
```
<!--more-->
## 简介
陆陆续续学习Python快一年多了。真的是“陆陆续续”啊！
今天学一会儿Python，明天打一会儿游戏，后天、大后天又不想学习了。
真是多灾多难的历程
如果，我没有Java的基础，估计也就输出个*1+1=3*吧

## import random
这是一个非常简单的调用外部包。然而，我在做随机数处理时，忘记了。一直在写rande()。这，是随机数吗？而且，还忘记调用random包了/(ㄒoㄒ)/~~
这是一个非常简单的错误。表示我的基本功很差很差
`random.randint(1,36)` 这个，当时也困扰了我很久很久。获取的随机数明明是数字，为什么会是String类型呢？搞不明白。

## 获取随机数
`cishu = [7,1,1,1,1,1] # 共 6个红球`
这行代码应该写为`cishu = 6` 这个在Java上写没有任何问题。在Python上一直报错
`TypeError: 'int' object is not iterable`意思很明显，也没找到具体方法。能用且用吧

## 循环运行彩票
根据用户的输入，来决定循环多少次。这个方法应该挺简单的，却用了很久的时间。和上面一样。
对Python的循环理解太浅薄了
```python
for j in range(j):
	suiji()
```
上面代码很简单。j是从上一个del里面传过来的，记录要循环多少次。但当时我还是浪费的很久的时间。
或许，还停留在Java编程模式吧。
```java
for (int i=0;i<10;i++){
	suiji();
}
```
这样的循环更加简单明了。也不知道为什么Python要选择那种循环。
*头发短，见识更短*
## 输出到文件
`xr.write(str(cai)+"\r")
`
转换，还是转换。String转int，int转String....
## 其它
感觉，Python在某些方面确实很简单，但是，对于数据类型太过模糊。
还是，基本功不够扎实
<font color="red">*头发短，见识更短*</font>