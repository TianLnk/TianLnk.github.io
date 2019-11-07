title: Java运算符
author: 田亮
abbrlink: b497
tags:
  - Java
categories:
  - Java
date: 2019-04-06 15:18:55
---
# 算术运算符
Java算数运算符中,常用的运算符有:加(+),减(-)乘(×)除(/).取模运算(%),自增(++),自减(-)
*取模运算表示取余数,适用于整数,char类型和浮点数*
>取余只能整数除以整数，若除数比被除数大，被除数就是余数啊
使用浮点数进行取余,会损失精度,一般不使用浮点数取余比如:
>>double b = 50.53;
System.out.println(b%5); //余数为:0.5300000000000011
<!--more-->

```Java
public class inta {

	public static void main(String[] args) {
		int a = 55;
		System.out.println(a%10);  // 55÷10=5.5 余数为5
		System.out.println(a%5);  // 55÷5=11,没有余数
		System.out.println(a%100); //被除数大于除数的余就是除数本身
		
	}
}
```
自增和自减相当于本身+1或本身-1.比如:*a = a+1;等同于a+=1 *
```java
public class inta {

	public static void main(String[] args) {
		int a = 55;
		a+=10; // 每次递增10 同 a=a+10
		System.out.println(a); // a = 65
		a=a+10;
		System.out.println(a); //a = 75
		a-=20;
		System.out.println(a); //a = 55
	}
}
```
自增和自减有2种写法:
`--a 或者 a--`
**两者如果单独使用,没有任何区别.如果用作计算,有差别**
>a--是先运算在赋值，而--a是先赋值在运算！！
或者:如果写在变量前表示在使用这个变量之前-1,如果写在变量之后表示在使用这个变量之后-1

```Java
public class inta {

	public static void main(String[] args) {
		int a = 55;
		int b = 55;
		int c = --a; //先减1,在将减去的赋值给c
		// 相当于: int c = a -=1
		int d = b--; //先赋值给d,再-1
		System.out.println(a); //54   
		System.out.println(b); //54
		System.out.println(c); //54
		System.out.println(d); //55
		
		int a1 = 55;
		int a2 = 55;
		System.out.println(); 
		System.out.println(++a1); //56
		System.out.println(a1); //56
		System.out.println(a2++); //55 先打印出a2现在的值,再进行运算
		System.out.println(a2); //56
	}
}
```
# 关系运算符
关系运算符用于判断数据之间的大小关系.
大于 小于 大于等于 小于等于 等于 等等于 不等于
关系运算符的结果为布尔型,如果关系成立为true,否则为false
```Java
public class inta {

	public static void main(String[] args) {
		int a = 10;
		int b = 20;
		boolean c = a>b;
		System.out.println(c); //输出 false 因为a不大于b
		System.out.println(a<b); //输出true
		
	}
}
```
# 逻辑运算符
逻辑与(&&) 逻辑或(||) 逻辑非(!)
其中 && 和 || 是双目运算符，实现逻辑与、逻辑或；！是单目运算符，实现逻辑非
逻辑运算建立在关系运算符的基础之上的
逻辑运算返回的结果也是布尔值
逻辑运算符的优先级为：！运算级别最高，&& 运算高于 || 运算。！运算符的优先级高于算术运算符，而 && 和 || 运算则低于关系运算符。结合方向是：逻辑非（单目运算符）具有右结合性，逻辑与和逻辑或（双目运算符）具有左结合性。

>一个代码块,由一个条件控制的,使用关系运算符
 由多个条件控制的,使用逻辑运算符
 
 逻辑与:所有条件必须同时成立,返回true,否则返回false
 逻辑或:所有条件中,有一个条件成立,返回true,都不成立才返回false
 逻辑非:所有条件中,都不等于所设条件,返回true,否则返回false
 ```Java
 public class inta {

	public static void main(String[] args) {
		int a = 10;
		int b = 20;
		
		System.out.println(a>b&&a<b); //结果为false 因为 对于逻辑与这个条件来说 这个运算符是矛盾的
		System.out.println(a>b||a<b); //返回true,因为逻辑或是有一个条件成立就成立
		System.out.println(a!=b); //结果为true  因为确实不等于
		System.out.println(a<b&&a>5||a==10); // 结果为true,因为逻辑与的条件全部成立,逻辑或不论是否成立都会返回true
		
		
	}
}
```
# 赋值运算符
"="称之为赋值运算符,用于对变量的赋值
关于赋值运算符,除了将右边的表达式计算出来并赋值给左边之外还具备:
赋值表达式本身也有值,其本身的值为所赋的值
赋值运算符:+=,-=,*=,/=,%=
 ```java
 public class inta {

	public static void main(String[] args) {
		int a=5;
		System.out.println(a*=3); // 相当于: int a = 5*3
		
	}
}
```
# 三目运算符
三目运算符也叫条件运算符
语法为:boolean? 条件1:条件2
 ```java
 public class inta {

	public static void main(String[] args) {
		int a=220;
		int b=110;
		int max=a>b?a:b; //假设a>b,如果a确实大于b返回第二个a,否则返回第二个b
		System.out.println(max); //结果为:220
	}
}
```
 