title: Python基础
author: 田亮
tags:
  - python
  - 菜鸟笔记
categories:
  - python
abbrlink: 396e
date: 2019-03-27 21:56:00
---
# Python 标识符
在python中,标识符由字母,数字,下划线组成.所有的标识符都可以使用这些.但是不能以数字开头.使用下划线(_)开头有其他意义,对大小写敏感.(及不建议使用中文创建变量,函数等,毕竟是外国的东西嘛)
>以下划线开头的标识符是有特殊意义的。以单下划线开头（_foo）的代表不能直接访问的类属性，需通过类提供的接口进行访问，不能用“from xxx import *”而导入；以双下划线开头的（__foo）代表类的私有成员；以双下划线开头和结尾的（__foo__）代表python里特殊方法专用的标识，如__init__（）代表类的构造函数。
# Python保留字符
所有计算机语言都有保留字符,这些保留字符不能用做变量名,常数和任何其它标识符名称

|保留字|说明|保留字|说明|保留字|说明|
|:-:|-|:-:|-|:-:|-|
|and|用于表达式运算,逻辑与操作|exec|用于执行python语句|not|用于表达式逻辑或操作
|or|用于表达式运算,逻辑或操作|finally|用于异常语句,出现异常后执行,同except和try一同使用|assert|用于判断变量或条件表达式的值是否为真
|break|中断循环语句的执行|for|for循环语句|pass|占位符
|print|打印语句|from|用于导入模块,和import一同使用|class|用于定义类
|continue|跳出这次循环,继续执行下一次循环|global|定义全局变量|raise|异常抛出操作
|return|从函数返回结果|if|条件语句,同else,elif结合使用|del|删除变量或序列的值
|def|用于定义函数或方法|import|用于导入模块,与from结合使用|try|包含可能出现的异常语句,同except和finally一同使用
|while|while循环语句|in|判断变量是否在序列中|elif|条件语句,和if一同使用
|else|条件语句,和if一同使用|is|判断变量是否为某个类的实例|with|简化python语句
|yield|用于从函数依次返回值|lambda|定义佚名函数|except|包含可能出现的异常语句..同try和finally使用
```python   输出当前python版本所有保留字符
import keyword
print(keyword.kwlist)
```
<!--more-->
# 行和缩进
这是python和其它语言的最大区别之一.<br>python放弃了大多数语言使用的大括号"{}"来控制类,函数以及其它逻辑判断.
python使用缩进来进行模块的编写.缩进量是可以控制的,但缩进数必须一样.
```python
if True:
	print('true'); #缩进哪怕是100个字符也不影响python的运行,缩进只要一样即可
else:
	print("false");
```
# 多行语句
python一般以新行作为语句的结束符.但是我们可以使用斜杠(\)来进行多行显示.当然,这并不会影响输出的结果<br>
如果语句中包含大括号,小括号或者中括号中的一个就不需要使用多行连接符.会自动识别
```python
duohang="这是" \
        "多行" \
        "显示";
NUM=(222, # 不需要使用多行连接符
   333,
   444);
```
# 数字类型 number
python中有四种数字类型:整型,布尔,浮点数和复数

|类型|说明
|-|-|
|int|整数,如:1 .有且只有一种整数类型int,没有其它语言的long型
|bool|boolean 布尔型,如:True.首字母为大写.用于逻辑判断(与或非)
|float|浮点数,如:3.14  带小数点的数
|complex|复数.ru:1+2j,3.14j+3.14
```python
Int=10;# 整数
bool=True;#布尔
floa=3.14;#浮点数
comp=1+2j;# 复数
```
# 字符串 String
被单引号或者双引号括起来的就是字符串.使用三个引号可以指定一个多行字符串.字符串可以使用转义字符<br>转义字符使用反斜杠"\"来表示
Python 中的字符串有两种索引方式，从左往右以 0 开始，从右往左以 -1 开始.
python没有单独的字符类型,一个字符就是长度为1的字符串.使用 **变量[头下标:尾下标:步长]**进行截取
在大多数语言中,单引号和双引号的使用完全相同
```python
string="abcdefg";
print(string[2:7:1]); #头下标表示从哪里开始,尾下标表示从哪里结束.步长是一次进几位
print(string[2:5]); #步长可以省略.默认为1
print(string * 2);# 打印2遍
print(string[0]);# 输出第一个字符
print(string[:6]); # 输出前6位字符
print(string[6:]);# 输出6位以后所有字符
print(string[3:-1]); #输出三位以后和倒数第二位之间的字符
```
>转义字符串（Escape String），即字符实体（Character Entity）分成三部分：第一部分是一个&符号，英文叫ampersand；第二部分是实体（Entity）名字或者是#加上实体（Entity）编号；第三部分是一个分号。

# 等待用户输入 input
所有的编程语言都需要获取用户的输入.python也不例外<br>
当程序走到input这里时,程序便会暂停运行.等待用户的输入,如果用户不想输入,那么计算机也就不想在运行了.<br>
input函数接受一个标准输入数据.返回为String类型.
```python
input("随便输入点什么吧...\n")  # 其中,\n表示换行
```
# print输出
在python中print输出默认换行,如果不需要换行需要在变量末尾加上个 .end=''
```python
print('换行输出');
print('不换行输出',end='');
print('>>>');
```
# import与from...import
在python中,使用import或者from..import来导入相应的模块
```python
import sys; # 导入整个模块
from sys import prefix;# 导入模块中的某个函数
from sys import argv,api_version; #导入模块中的多个函数
from sys import *;# 导入某个模块中的所有函数
```









# format 格式化函数
**format 函数可以接受不限个参数，位置可以不按顺序。它增强了字符串格式化的功能<br>format 函数可以接受不限个参数，位置可以不按顺序。**
```python
print(('{} {} {}').format(2,4,5));# 不设置指定位置，按默认顺序
print(('{0} {1} {2}').format(2,4,5));# 设置指定位置
print(('{2} {0} {1}').format(2,4,5));# 设置指定位置
#输出:
#       2 4 5
#       2 4 5
#       5 2 4
# 九九乘法表
for i in range(1,10):
    l='';
    for k in range(1,i+1):
        l+='{} * {} = {:<4}'.format(k,i,(k*i));
    print(l);
```