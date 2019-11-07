title: 'Java分支结构-if,switch'
author: 田亮
abbrlink: 81df
tags:
  - Java
categories:
  - Java
date: 2019-04-06 17:51:00
---
任何复杂的逻辑都可以通过“顺序”、“分支”、“循环”三种基本的程序结构来实现。
1. 顺序结构:从上往下顺序执行,每个语句 执行一遍 以if为代表
2. 分支结构:程序在运行中，根据不同的条件执行不同的语句。以switch为代表
3. 循环结构:进入到特定代码块时循环运行N次.以while,for为代表

![分支结构](http://114.116.121.172/img/fenzhijiegou.png)
<!--more-->
## if语句语法
if 选择结构是根据条件判断之后再做处理的一种语法结构。默认情况下，if 语句控制着下方紧跟的一条语句的执行。不过，通过语句块，if 语句可以控制多个语句。
```
if ( 条件表达式)
{
    语句块;
}
```
条件表达式：条件表达式可以是任意一种逻辑表达式，最后返回的结果必须是一个布尔值。取值可以是一个单纯的布尔变量或常量，也可以是使用关系或布尔运算符的表达式。如果条件为真，那么执行语句块；如果条件为假，则语句块将被绕过而不被执行。
语句块：该语句块可以是一条语句也可以是多条语句。如果仅有一条语句，可省略条件语句中的大括号{}。
<img src="http://c.biancheng.net/uploads/allimg/180928/3-1P92Q50459617.jpg">

## if else 结构
与单结构if语句差不多.多了一个判断条件.
else表示所有if条件都不成立则运行else
```Java
public class inta {

	public static void main(String[] args) {
		int a=10;
		if(a>=10) {
			System.out.println("如果a大于等于10就进入这里面");
		}else {
			System.out.println("嗯,a小于10,所以进入到这里面了");
		}
	}
}
```
**if之间可以相互嵌套,多个if语句同时使用等.下面是if的简单运用:**

# 简单收银台程序
```Java
public class shouyintai {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		/*
		 * 简易收银台程序
		 * */
		double qian = 1000; // 初始会员卡余额
		double jg[] = {234.8,199.9,233.3,120.5,888.8,256.8}; //商品价格集合
		double jiage = 0; //总共消费多少元
		
		Scanner scanner = new Scanner(System.in); 
		System.out.println("-----欢迎来到喵喵超市-----");
		
		System.out.println("你要买点什么嘛?");
		System.out.println("1.电饭锅 234.8元\r2.烤面包机199.9元\r3.面条机233.3元\r4.豆浆机120.5元\r5.净水器888.8元\r6.微波炉256.8元\r0.买完了");
		System.out.println("------");
		while(true) { //死循环,一直运行
			System.out.println("请输入你要购买的商品代码:");
			int a = scanner.nextInt(); //获取用户输入
			if(a<=6&&a!=0) { //判断用户输入是否正确
				jiage+=jg[a-1]; //因为Java是从0开始计数,所以要-1
				System.out.println("目前共花费:"+jiage);
			}
			if(a>6&&a!=0) { //如果用户输入大于6的数字,提示没有此商品
				System.out.println("没有此商品");
			}
			if(a==0) { //如果用户输入0,则表示购买完毕,销毁while循环
				System.out.println("你共消费"+jiage+"元");
				if(qian<jiage) { //如果会员卡余额不足以支付进入充值程序
					System.out.println("你的余额不足请充值");
					while(true) { // 因为if语句是从上至下运行,所以设立一个死循环,判断用户充值是否足够
						System.out.println("请输入充值金额:");
						double cz=scanner.nextDouble(); //获取用户充值金额
						qian+=cz; //进行充值
						System.out.println("会员卡余额:"+qian);
						if(qian>=jiage) { //判断会员卡余额是否足以抵消此次消费
							break; // 结束死循环
						}
					}
				}
				if(jiage>500) { // 判断消费是否大于500,大于500打八折
					qian-=jiage*0.8; 
					System.out.println("恭喜你获得了本店满500打八折活动,实际收取"+jiage*0.8+"会员卡余额:"+qian+"\r期待您的下次光临");
				}
				break; //结束大循环
			}
		}
	}
	

}
```

## switch..case
switch是切换的意思，case是例子，事实的意思。那根据什么切换呢？就是switch中的变量，变量是多少，就会匹配到具体的case中，只要匹配到了某一个case，就会一直执行到方法结束，这是switch的特性。
**注意**case中是不能写变量的，必须是常量.它的效率更高,结构清晰
default:就是你的变量没有被任何case匹配到，那它就执行default的程序，相当于默认的逻辑
>switch 语句中的变量类型可以是： byte、short、int 或者 char。从 Java SE 7 开始，switch 支持字符串 String 类型了，同时 case 标签必须为字符串常量或字面量。
switch 语句可以拥有多个 case 语句。每个 case 后面跟一个要比较的值和冒号。
case 语句中的值的数据类型必须与变量的数据类型相同，而且只能是常量或者字面常量。
当变量的值与 case 语句的值相等时，那么 case 语句之后的语句开始执行，直到 break 语句出现才会跳出 switch 语句。
当遇到 break 语句时，switch 语句终止。程序跳转到 switch 语句后面的语句执行。case 语句不必须要包含 break 语句。如果没有 break 语句出现，程序会继续执行下一条 case 语句，直到出现 break 语句。
switch 语句可以包含一个 default 分支，该分支一般是 switch 语句的最后一个分支（可以在任何位置，但建议在最后一个）。default 在没有 case 语句的值和变量值相等的时候执行。default 分支不需要 break 语句。
引用自<a href="http://www.runoob.com/java/java-switch-case.html">菜鸟教程</a>

<font color="red">**注意:case一定要加上break;否则会将符合条件和符合条件下面的所有分支全部运行**</font>

# 简单银行业务操作程序
```Java

import java.util.Scanner;
public class inta {

	public static void main(String[] args) {
		/*
		 * 简易银行程序
		 * */
		Scanner scan=new Scanner(System.in);
		System.out.println("-----欢迎来到喵喵银行-----");
		System.out.println("你需要办理什么业务呢?\r1.存钱\r2.取钱\r3.挂失or解冻\r4.人工服务\r0.退出");
		double yhk=100; //初始银行卡余额
		boolean guashi=true; //检测是否挂失
		boolean tuichu = true; //为false不再循环
		while(tuichu) {
			System.out.println("1.存钱  2.取钱  3.挂失or解冻  4.人工服务  0.退出");
			System.out.println("请输入你要办理的业务:");
			int a = scan.nextInt(); //获取用户输入
		switch (a) {
		case 0:
			System.out.println("欢迎下次光临~");
			System.out.println("你的银行卡余额为:"+yhk);
			tuichu = false; //终止whlie循环
			break; // 跳出本次循环
		case 1:
			if(guashi==true) { //判断是否挂失
				System.out.println("请输入存钱金额:");
				double cunqian=scan.nextDouble(); //获取存多少钱
				yhk+=cunqian;
				System.out.println("存钱成功,你的银行卡余额为:"+yhk);
			}else {
				System.out.println("已经挂失,无法操作");
			}
			break;
		case 2:
			if(guashi==true) { //判断是否挂失
				System.out.println("请输入取钱金额:");
				double quqian=scan.nextDouble();//获取取钱
				if(yhk<quqian) { //判断银行卡余额是否足够
					System.out.println("银行卡余额不足,请充值后再取");
				}else {
					yhk-=quqian;
					System.out.println("取钱成功,银行汇款余额为:"+yhk);
				}
			}else {
				System.out.println("已经挂失,无法操作");
			}
			break;
		case 3:
			if(guashi==true) {
				guashi = false;
				System.out.println("挂失成功,其它操作冻结");
			}else {
				guashi = true;
				System.out.println("解冻成功,其它操作解冻");
			}
			break;
		case 4:
			System.out.println("人工服务无法连接");
			break;
		default: //如果输入的内容非上面case里的,执行这里
			System.out.println("输入错误");
			break;
		}
		
	}
	}
}
```