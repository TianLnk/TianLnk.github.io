title: Python索引
author: 田亮
tags:
  - python
categories:
  - python
abbrlink: 83c1
date: 2019-11-06 16:11:00
---
## 序列
序列是一块用于存放多个值的连续的内存空间，并且按一定的顺序进行排列，可以通过索引取值
![upload successful](\images\pasted-6.png)
<!--more-->
```python
a = [123,45,67] # 序列 里面的数字通过索引获取
print(a[2]) # 输出第三个数值
print(a[-1]) # 输出最后一个数值

```
*索引从0开始"数数",也可以是负数*
## 切片
name[起始值:结束值:步长]
切片遵循前包后不包。
```python
num = [0,1,2,3,4,5,6,7]
print(num[2:5:1]) # 输出 2，3，4 省略了5  :1是步长的意思，默认为1可以不写
print(num[2:5:2]) # 步长为2 输出 2，4 
print(num[:5]) # 输出 0，1，2，3，4 省略号不可以省略
print(num[5:]) # 输出 5，6，7 数字可以省略，必须有省略号
print(num[:]) # 输出整个序列
```
## 序列相加
字面意思，可以将多个序列合并成一个序列
只能是同类型的序列才能相加。即：列表+列表，元组+元组等。不能是 列表+字符串这种形式
```python
num1 = [1,2,3]
num2 = [4,5,6]
num = num1 + num2 # 两个序列合并成1个 输出1，2，3，4，5，6

```
## 序列相乘
说话要说三遍。当某些序列需要输出大量重复内容
序列相乘并不是把里面的内容乘以多少，而是把序列输出N次
```python
num = [1,2,3]
print(num*3) # 输出1，2，3，1，2，3，1，2，3 并不会输出相乘的结果

name = ["haha"]*3
print(name) # 输出haha，haha，haha
```
## 检查序列
检查某个关键字是否存在于这个序列中
```python
num =[1,2,34,57,8,9]
print(1 in num) # 输出True 说明在这个元素里
print(3433 in num) # 输出False 因为它不在这个序列里面
print(2 not in num) # 输出 False 如果有输出false
i = 34
if i in num: # 同上
	print("true")
else:
	print("False")
```
## 序列计算
```python
num = [1,2,3,4,5]
print(len(num)) # 输出5 len计算数组的长度 也可以计算出 String类型长度。
print(max(num)) # 输出最大值
print(min(num)) # 输出最小值

```