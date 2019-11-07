title: Java对象和类
author: 田亮
abbrlink: 2e5c
tags:
  - Java
categories:
  - Java
date: 2019-04-11 21:04:00
---
Java作为一种面向对象语言。支持以下基本概念：
多态,继承,封装,抽象,类,对象,实例,方法,重载
> 对象：对象是类的一个实例，有状态和行为。例如，一条狗是一个对象，它的状态有：颜色、名字、品种；行为有：摇尾巴、叫、吃等。
类：类是一个模板，它描述一类对象的行为和状态。
<a href="http://www.runoob.com/java/java-object-classes.html">菜鸟教程</a>
<!--more-->
## 什么是类,什么是对象
将不同类型的数据的集合封装为一个整体用来描述一种新的事物
比如人:有年龄,身高,体重,名字等
张三,李四,婉儿等这些都叫做对象,他们都是人.而人叫做类
由多个对象组成一个类
1. 现实世界是由很多对象组成,基于对象抽出类
  - 对象:真实存在的单个的个体
2. 类中可以包含所有对象所共有的特征或属性---叫做变量
3. 类中可以包含所有对象所共有的行为---叫做方法
4. 一个类可以创建多个对象
5. 一个类的多个对象 结构相同,数据不同

## 类的创建
自己创造的数据类型叫做类
一个类可以包含以下类型变量：
局部变量：在方法、构造方法或者语句块中定义的变量被称为局部变量。变量声明和初始化都是在方法中，方法结束后，变量就会自动销毁。
成员变量：成员变量是定义在类中，方法体之外的变量。这种变量在创建对象的时候实例化。成员变量可以被类中方法、构造方法和特定类的语句块访问。
类变量：类变量也可以声明在类中，方法体之外，但必须声明为static类型。
一个类可以拥有多个方法
```Java
public class inta {

	public static void main(String[] args) {
	
		ren r = new ren();  //先声明创建的类
		System.out.println(r.age);//输出
	}
}
 class ren{ //类要写在最最最下面   
	int age=12;
	String name="aa";
	double shengao=166.6;
	//...
	static int a(int i) { //public 写不写无所谓,因为他是默认值
		return i;
	}
}
```
## 定义类的成员变量
类的定义包括"成员变量"的定义和"方法"的定义.其中"成员变量"用于描述该类型对象共同的数据结构
```
class 类名{ // 类名的首字母大写 
	成员变量类型 变量名称;
   int       a ;
   
}
```
对象创建后,其成员变量按照默认的方式初始化.默认的初始值:
数值类型(int,byte,short,long,float,double)默认值;0
boolean 默认值:false
char 默认值:/u0000
引用类型 默认值:null

## 构造方法
构造器,构造函数,构建器
用于给成员变量赋初始值,构造方法必须与类同名,并且没有返回类型(没有void或其它类型)
在创建对象时被自动调用(new时被动调用)
构造方法时必须的.如果自己不写,系统会自动生成一个无参构造方法
```Java
public class lei {
	int age;
	String name;
	double shengao;
	lei(int a){ //构造方法
		a=age;
      //...
	}
```
**构造方法可以减轻代码量,使代码更加清晰**
```Java
public static void main(String[] args) {
		// TODO Auto-generated method stub

		不使用构造 no = new 不使用构造(); 
		no.a=10;
		no.b=20;
		no.c=30;
		System.out.println(no.a+no.b+no.c);
		
		使用构造 yes = new 使用构造(10, 20, 30); 
	}

}


class 不使用构造{
	int a; //成员变量
	int b;
	int c;
}
class 使用构造{
	int a;
	int b;
	int c;
	
	使用构造(int a,int b,int c){ //局部变量
		this.a = a;
		this.b = b;
		c = c; // 不加 this 也可以,但是会让人捉摸不透.
		System.out.println(a+b+c);
	}
}
```

## this方法
this 指代当前对象,谁调用方法,所指的就是那个.比如调用a()方法,a方法里面有个变量int b;this.b就是调用这个b
this只能在方法里面使用
在方法中访问成员变量之前默认都有个this,
用法:
1. this.成员变量名--访问成员变量
2. this.方法名()--调用方法
3. this()--调用构造方法

## 定义数组方法
搞了半天,原来很简单😭
数组的元素可以是任何类型,包括数组类型
```Java

public class 数组 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		shuzu[] s = new shuzu[4];
		s[0] = new shuzu(1);
		s[1] = new shuzu(2);
		s[2] = new shuzu(3);
		s[3] = new shuzu(4);
	}
}
class shuzu{
	shuzu(int a){
		int b[] = new int[4];
		for (int i = 0; i < b.length; i++) {
			b[i] = a;
			System.out.println(b[i]);
		}
	}
}
```
## 内存管理,垃圾回收
内存由Java中的JVM里的GC进行自动垃圾管理.
1. 堆:用于存储所有new出来的对象.(包括成员变量)
	1.1.成员变量的生命周期:创建对象时存在堆中,当对象被回收时一并回收
2. GC:垃圾回收器. 会不定时到堆中进行扫描,看到垃圾则自动回收
	2.1	垃圾:没有任何引用所指向的对象
   2.2 System.gc();调用GC尽快进行垃圾回收
3. 内存泄漏:不再使用的对象没有被及时的回收(系统认为它不是垃圾,而不进行回收)
	3.1 解决方法:当对象不再使用时,及时将引用对象设置为null
    ```Java
    a b = new a();
    b = null; //设置为null,不再指向刚分配的对象空间,成员变量失效.被GC回收
    ```
4. 栈:jvm在其内存里开辟一个名为"栈"的空间.
	4.1 这部分空间用于存储程序运行时在方法里声明的所有局部变量
   4.2 只存储正在运行的局部变量,调用结束时,栈帧消失,局部变量直接消失
   4.3 调用方法时,在栈中为该方法分配一块对应的栈帧,栈帧中包含所有局部变量,包括变量的参数

>jvm为每个新创建的线程都分配一个堆栈。堆栈以帧为单位保存线程的状态。jvm对堆栈只进行两种操作：以帧为单位的压栈和出栈操作。
栈帧(Stack Frame)是用于支持虚拟机进行方法调用和方法执行的数据结构，它是虚拟机运行时数据区的虚拟机栈(Virtual Machine Stack)的栈元素。栈帧存储了方法的局部变量表，操作数栈，动态连接和方法返回地址等信息。第一个方法从调用开始到执行完成，就对应着一个栈帧在虚拟机栈中从入栈到出栈的过程。
每一个栈帧都包括了局部变量表，操作数栈，动态连接，方法返回地址和一些额外的附加信息。在编译代码的时候，栈帧中需要多大的局部变量表，多深的操作数栈 都已经完全确定了，并且写入到了方法表的Code属性中，因此一个栈帧需要分配多少内存，不会受到程序运行期变量数据的影响，而仅仅取决于具体虚拟机的实 现
摘录自:<a href="https://www.cnblogs.com/minisculestep/articles/4934947.html"> java 栈和栈帧</a>

5. 局部变量的生命周期:调用结束,死亡    
    

## 成员变量和局部变量的取别
**成员变量**
1. 变量在类里面,在方法外
2. new时存在堆中,对象被回收时消失
3. 有默认值

**局部变量**
1. 在方法中
2. 调方法时存在于栈中,方法调用结束时与栈帧一同消失
3. 无默认值
```Java
class shuzu{
	int b; // 有默认值
	shuzu(){
		int c; //无默认值
		System.out.println(b);  //输出默认值 0
		System.out.println(c);	//报错,必须赋值
	}
}
```
## 继承
继承,字面意思.可以将别人的东西拿来当作自己的
1. 可以节省大量重复代码.如下代码:如果不使用继承,姓名,年龄等需要重复编
2. 通过extends声明继承
3. 父类:所有子类所共有的属性和行为
4. 子类:子类所特有的属性和行为
	4.1 子类可以访问父类,反之不行
   4.2 子类继承父类后具有:子类+父类 (可以同时使用这两个)
5. 一个子类只能继承一个父类,一个父类可以有多个子类
6. 继承具有传递性  比如a,b,c都只有1个属性,b继承a变成2个属性,c再继承b便有3个属性
7. 子类可以继承父类的成员变量以及成员方法.同时也可以定义自己的成员变量和方法

```Java

public class 继承 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		laoshi ls = new laoshi("老师",52,'男',10086,2333.33);
		xuesheng xs = new xuesheng("小兰", 17, '女', 2333, "花痴");
	}
}
class jicheng{ // 被别人继承不需要特别声明
	String name;
	int age;
	char xb;
	int dh;
} 
class laoshi extends jicheng{ 
	laoshi(String name, int age, char xb, int dh,double gongzi) { //extends 继承 将 jicheng类下的所有元素拿过来自己用
		System.out.println("我是一名"+name+"今年"+age+"岁了,工资为"+gongzi+" ...");
		
	}
}

class xuesheng extends jicheng{
	 xuesheng(String name, int age, char xb, int dh,String ahao) {
		 System.out.println("我叫"+name+"今年"+age+"岁了,性别"+xb+"爱好是:"+ahao+" ...");
	}
}
```
## super
*super和this差不多,不写也有一个默认的*
指代当前的对象的父类对象
super.成员方法变量名  ---访问父类的成员变量
super.方法名()  ---调用父类的方法
super()  --调用父类的构造方法
```Java
class jicheng{

	jicheng(){
		
	}
	jicheng(int a){
		
	}
} 

class ab extends jicheng{

	ab() {
		super(); //调用父类的无参构造方法  必须在代码中的第一位否则报错
		// TODO Auto-generated constructor stub
	}
	ab(int a){
		super(a); //调用父类的有参构造方法
	}
}
```