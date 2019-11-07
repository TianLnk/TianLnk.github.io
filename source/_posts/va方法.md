title: Java方法
author: 田亮
abbrlink: 415f
tags:
  - Java
categories:
  - Java
date: 2019-04-11 07:55:00
---
每种语言都有方法的概念,有的语言的叫法不同(函数或过程等)
方法用于封装一段特定的逻辑功能 即:一个功能封装在一个地方.需要时调用
- 可以随时调用,不使用不调用不运行,不占用内存
- 方法可以减少代码量,便于维护等
- 方法尽可能独立,一个方法只做一件事

<!--more-->
## 方法的定义
定义方法五要素:修饰符,返回值类型,方法名,参数列表,方法体
>修饰符：修饰符，这是可选的，告诉编译器如何调用该方法。定义了该方法的访问类型。
返回值类型 ：方法可能会返回值。returnValueType 是方法返回值的数据类型。有些方法执行所需的操作，但没有返回值。在这种情况下，returnValueType 是关键字void。
方法名：是方法的实际名称。方法名和参数表共同构成方法签名。
参数类型：参数像是一个占位符。当方法被调用时，传递值给参数。这个值被称为实参或变量。参数列表是指方法的参数类型、顺序和参数的个数。参数是可选的，方法可以不包含任何参数。
方法体：方法体包含具体的语句，定义该方法的功能。
摘录:<a href="http://www.runoob.com/java/java-methods.html">菜鸟教程</a>
```
修饰符 返回值类型 方法名(参数类型 参数名){
    ...
    方法体
    ...
    return 返回值;
}
```
## 定义参数和返回值
方法的参数:在调用时传递给方法,需要被方法处理的数据
方法可以有参数也可以无参数.有参数可以使方法处理更加灵活一些
在定义方法时,需要声明该方法所需要的参数变量]
在方法调用时,会将实际的参数值传递给方法的参数变量.必须保证传递的参数类型和个数符合方法的声明
void表示没有返回值
有返回值的必须要在方法里面加上一个return
```Java
public static void a(){}  //无参数,无返回值
public static void b(int a){} //有参数,无返回值
public static int c(int a){} //有参数,有返回值
```
方法调用结束后可以返回一个数据,称之为返回数
方法在声明时必须指定返回值类型
   - 若方法不需要返回数据,将返回值设置为void
   - 反之,将返回值设置为特定的数据类型

```Java
	public static void main(String[] args) {
	
		int c= 0;
		a(); // 无参无返回值的可以直接调用
		b(c); 
		System.out.println(c); //c 在b方法里面被改变,但是不影响主方法里面的c. 因为这是2个不同的c.重名罢了
		c = b(c);
		System.out.println(c); // 将返回值赋值给c
		c(100); 
	}
	public static void a() { // 无参无返回值
		System.out.println("这是a()方法");
	}
	
	public static int b(int c) { // 有参数有返回值
		for (int i = 0; i < 10; i++) {
			c++;
		}
		return c;
	}
	public static void c(int c) { //有参数无返回值
		System.out.println(c);
	}
```
## 方法重载
方法名称相同，参数的类型和个数不同。
在进行方法重载的时候有一个重要的规则：要求方法的返回值类型一定要相同。
重载很好理解,就是一个class里面有数个方法名一样但是返回数量不一样
```Java
	public static void main(String[] args) {
	
		int c= a(a(100));
		int c1=a(10, 20);
		System.out.println(c);
		System.out.println(c1);

	}
	public static int a(int a1) { // 我只有一个参数
		return a1;
	}
	public static int a(int a1,int a2) { //我有2个参数.我们的参数不一样,所以不要调用混了哦
		int jia=a1+a2;
		return jia;
	}
```
## 猜字母小游戏
```Java
import java.util.Random;
import java.util.Scanner;
public class 猜字母小游戏 {
	/**
	 * 猜字母小游戏
	 * 随机获取随即个字母
	 * 对系统生成的字母和用户输入的字母进行比较
	 * 显示用户猜对了几个字母
	 * 不可以限制用户输入的长度
	 * 显示用户一共猜了多少次
	 * */

	public static void main(String[] args) {
		huanying();//非常简便,主方法体只需要一句话便启动了整个程序
	}
	public static void huanying() { //仅用来开头的提示文字
		System.out.println("-----欢迎来到猜字母小游戏-----");
		System.out.println("规则:字母不区分大小写   长度随机   祝你好运~");
		cai(); //调用cai方法
	}
	
	
	public static void cai() { //开始游戏
		String[] suiji= {};//用于保存获取的随机数
		suiji=suijishu(suiji);//保存获取下来的随机数
		
		StringBuffer sb = new StringBuffer(); //将数组转换成字符串
		for(int i = 0; i < suiji.length; i++){ //获取数组的长度
		 sb. append(suiji[i]);
		}
		String s = sb.toString(); // 得到转换成字符串的 系统随机字母
		System.out.println(s);
		int i = 0; //猜的次数
		
		while (true) { // 正式开始游戏
			Scanner sc = new  Scanner(System.in); //用户输入
			System.out.println("请输入你的猜想:");
			String yhsr = sc.next(); //获取用户的输入
			i++;
			if(yhsr.equals(s)) { // 字符串的比较
				System.out.println("恭喜你猜对了.你一共猜测了"+i+"次");
           break;
			}else {
				int caidui = zhengquedu(s, yhsr);
				System.out.println("猜错了,这是你"+i+"次猜测,你目前猜对了"+caidui+"个字母");
			}
		}
	}
	
	
	
	public static String[] suijishu(String[] suiji2) { //用来获取随机数
		Random sj = new Random(); //随机数方法
		int a = sj.nextInt(10); //获取0-9之间的随机数
		String[] zimu = {"a","b","c","d","e","f","g","h","y","j","k","l","m","n","o","p","q","i","s","t","u","v","w","x","y","z"};
		String[] suiji =new String[(int)a];
		for (int i = 0; i < suiji.length; i++) {
			Random sj2 = new Random(); //随机数方法
			int sjs = sj2.nextInt(23); //获取0~23之间的随机数
			suiji[i]=zimu[sjs]; //看不懂慢慢想
		}
		return suiji; //返回获取的随机数(返回到调取此方法的方法体中)
		
	}
	
	
	public static int zhengquedu(String xt,String yh) { //比较用户输入几个正确答案
		String a=xt; //  用户输入
		String zq = yh; //正确答案
		char [] arr = a.toCharArray(); //注意返回值是char数组
		char [] arr2 = zq.toCharArray(); //注意返回值是char数组
		int caidui = 0;
		
		for (int i = 0; i < arr.length; i++) { //进行比较
			if (arr2.length<=i) {//如果用户输入的比正确答案的长度小,则不再比较
				break;
			}
			if (arr[i]==arr2[i]) {
				caidui ++;
			}
		}
		return caidui; //返回猜对了多少个字母
	}
	
}
//这个程序饶了一大圈,可以精简很多
```












