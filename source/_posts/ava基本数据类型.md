title: Java基本数据类型
author: 田亮
abbrlink: '79e2'
tags:
  - Java
categories:
  - Java
date: 2019-04-03 22:24:00
---
# 8种基本数据类型
Java共有八种基本数据类型,分别用于存储整数,浮点数,字符类型和布尔类型数据


|整数类型|浮点类型(小数)|char(单字符)|Boolean(布尔)
|-|-|-|-|
|int|float|char|true
|long|double||false
|short| | |
|byte| | |

>short在Java中基本使用不到(只用来兼容其它语言),byte很少情况下使用
对于小数来说,double似乎是个更好的选择,float很少使用
char类型用来存储单个字符,比如性别
boolean用来判断

<!--more-->
数据类型不可乱用,够用就行,int能够装下没必要使用long

|类型名称|字节空间|使用场景|使用概率
|-|-|-|-|
|byte|1字节(8位)|存储字节数据|较常用
|short|2字节(16位)|兼容性考虑|极少使用
|int|4字节32(位)|存储整数|常用
|long|8字节64(位)|存储长整数|较常用,使用需要加L或小写l
|float|4字节32(位)|存储浮点数|较少使用
|double|8字节64(位)|存储双精度浮点数|常用
|char|2字节16(位)|存储一个字符|常用
|boolean|1字节8(位)|存储逻辑变量(true false)|常用

Java有默认类型,比如整数的默认类型为int.如果不进行声明而超出int的最大值(2147483647)或最小值(-2147483648)便会溢出.
```Java
int a = 1000000000;#报错,无法编译.因为超过int类型的最大值
int b = 100000000 * 1000;#不报错,可以编译,编译时报溢出错误

```

2个整数相除,得到的还是整数.小数位被舍去(非四舍五入).
## long和int的使用
对于存储比较大的数或者可能会越界的数不必犹豫,直接使用long属性
比如通过毫秒级进行时间的计算或者存储必须使用long.除非你能确定时间不会越界
>System.currentTimeMillis()方法,返回1997年1月1日零点到此时所经历的毫秒数,其数据类型为long,(超过了int的最大数).

```java
public class inta {

	public static void main(String[] args) {
		long a=100000000000L;  // long值需要在末尾加上l,表明是long类型
		int b=2147483647;  //最大值,加1溢出
		System.out.println(a-b);
	}
}
```
## double和float的使用
double或float = 浮点数 = 小数
double大多数用作与商品的价格或者数据计算
double与float的区别和int与long一样.double类型的精度是float类型的两倍.这是其"双精度"和"单精度"的来源
在大多数场合下,使用double表示浮点数或叫做小数
对于Java来说,频繁使用float没有直接使用double来得方便.因为Java默认的浮点值为double型,所以,float需要在数值末尾加上F后缀.
```Java
public class inta {

	public static void main(String[] args) {
		double a=3.14; 
		double a1=3.14E3; //表示3.14乘以10的三次方
		float b=3.14f; //需要在末尾加上 f.否则报错
		
	}
}
```
double在进行某些运算时会出现舍入误差.比如在十进制里**1/3=0.3333...**
所以,二进制表示十进制时会有一些误差,对于一些要求精度高的需求来说这是一个代码缺陷.只能放弃使用double或者float.
**在运算过程中,只要有一位是小数类型,结果为小数**
## boolean布尔值和char
布尔值只有也只能赋值为0和1两个值,分别为true(真)和false(假).
布尔类型只用于逻辑运算,用来判断某个条件是否成立
布尔值经常存储关系运算结果,比如比较大小,是否传入数据等

```Java
boolean a= true;
boolean b =false; //布尔类型只有这两个值
```
**char类型表示字符类型**
字符类型事实上是一个16位无符号(无负数)整数,这个值是对应字符的编码
Java使用国际通用的Unicode字符集编码,所有的字符都是16位
字符可以采用直接量赋值,也可以采用16位进制赋值
char类型需要使用单引号,双引号会报错
在char里面存储特殊符号需要使用转义字符
char本质上是0-65535之间的数字
```Java
char a='你'; 
char b = '\u4e2e'; //16进制
char c= 65; // 输出大写的A   范围在0 - 65535之间
char d =' '; //输出一个空格
```
# 基本数据类型转换
基本数据类型从小到大排序:byte,short,int,long,float,double,char可以互相转换
## 自动类型转换
从小打到大进行转换可以隐式转换
不需要特别声明,系统自动转换,不会缺失精度
多个类型转换,会自动转换为其中最大的类型
<font color='red'>byte,short,char类型进行运算时会转换成int类型在进行计算</font>
## 强制类型转换
从大到小进行转换为强制类型转换.
需要注意的是:从大到小转换不能超过转换后的数据类型上限
强制转换可能会丢失精度

```Java
	public static void main(String[] args) {
		
		int a=200; //声明整型变量a,赋值为200
		long b =a; //声明长整型变量b,赋值为a,从大到小,自动转换
		int c=(int)b; //声明整形变量c,赋值为长整型b.需要强制转换
		long d=250; //声明长整型变量d,赋值为250
		double e=250; //声明浮点类型e,赋值为250
		System.out.println(e); // 输出浮点类型e,输出为:250.0
		long f=10000000000l; //声明长整形变量f,赋值大数100亿,需要在末尾加L
		int g= (int) f; //声明整形变量 g,赋值长整型变量f,需要强制转换
		System.out.println(g);//输出整形变量g,输出:141006540   int最大值为:2147483647
		double h=2.5; //声明浮点型h,赋值为2.5
		int i =(int) h; //声明整形变量i,赋值浮点型h,需要强制转换
		System.out.println(i); //输出:2
		byte b1=4; //声明byte类型为4,输出为4
		byte b2='4'; //声明byte类型为'4',输出为52
		byte b3='\u0034'; //声明byte类型为'\u0034',输出为:52
	}
}
```
