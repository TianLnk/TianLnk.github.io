title: 'Java分支结构-while,for'
author: 田亮
abbrlink: c740
tags:
  - Java
categories:
  - Java
date: 2019-04-07 13:08:00
---
**重复重复再重复,循环循环一直循环...**
Java有三种循环结构:while,do-while以及for循环.
循环的关键在于条件测试.即:结果必须是布尔值
循环三要素:
1. 循环变量的初始化
2. 循环的条件(以循环变量为基础)
3. 循环变量的改变(向着循环方向的改变)

循环变量:在循环过程中改变的量
注意:*不要将循环搞成死循环!不要将循环搞成死循环!!不要将循环搞成死循环!!!*
# while循环
while循环也称条件判断语句,它的循环方式为利用一个条件来控制是否要继续执行这个语句
while循环是这三种循环里面最简单的一种,也是最基础的
```Java
int a=0;
	while(a<10) {//当条件表达式的返回值为真(true)时,进入循环体.当循环体语句执行完毕后再次进行判断是否为真.....直到条件为false结束本次循环
		a++; // 每进入一次a+1
		System.out.println(a);
	}
```
<!--more-->

# do while 循环
do-while与while的区别在于:无论条件是否满足,都会执行一次
while先进行判断是否成立,如果条件成立则运行,反之退出
do-while先运行一次,再进行判断,如果条件不成立不再运行.反之继续

```Java
public class inta {

	public static void main(String[] args) {
		int a=0;
		do {
			System.out.println("本次条件不满足");
		} while (a==1);//分号必须要加上,
		
	}
}
```

# for循环
在Java中,for循环语句是最灵活也是最常用的循环结构.也是最难的一种结构
<img src="https://ss1.baidu.com/6ONXsjip0QIZ8tyhnq/it/u=2220818644,2509110513&fm=173&app=49&f=JPEG?w=640&h=121&s=01306C32C5366E325C7584DF0000C0B2" />
Java对for循环是非常放纵的,Java的放纵造就了for的死循环.一不留神一个死循环
```Java
for(;;){ //可以省略条件,不能省略分号
	System.out.println("不需要任何条件的典型死循环");
}
for (int i = 0; i < 1; i++) {
	i --; // 这个很可笑吗?其实在多层嵌套中这种情况很常见
	System.out.println("又一个死循环");
 }
for (int i = 0; i < 1; i--) { //又一个典型死循环  
	System.out.println("又又一个死循环");
}
for (int i =1, k = 1; i < 10; i += 1 ,k +=2) { //一个循环里面放入多个条件.Java对for是放纵的,只要有2个分号即可
	System.out.println(i+k+"@"+i+" "+k);
}

for (int i = 0; i < 10; i++) { // 非常正经的for语句
	System.out.println("hello Java"); //输出10遍hello Java
}
```
## 在循环中使用break
break用于循环,可使程序终止循环而执行循环后面的语句.常与条件语句一同使用
```Java
int k = 0;
			for (int i = 0; i < 100; i++) { 
				k++;
				if(i==50) { //当循环50+1次时,进入if语句然后跳出这个循环
					break;
				}
			}
			System.out.println(k); // 输出结果51
```
## 在循环中使用contiune
只能用在循环里面
用于跳过本次循环,但不会终止这个循环
```Java
for (int i = 0; i < 100; i++) { 
				if(i%3==0) { //当i是3的倍数时,跳出这次循环继续下一次循环
					continue;
				}
				System.out.println(i); // 永远不会得到3的倍数  输出:1 2 4 5 7...
			}
```
## 一个答题小游戏
```Java

import java.util.Scanner;

public class 答题游戏 {

	/**
	 * 制作一个答题小游戏
	 * 答对将一分,答错扣一分,跳过0分
	 * 总共10提,6分及格
	 * 当剩余题目总分减去以获得分数无法得到及格分,终止答题
	 * 连续错误3次后,还是错误,结束游戏
	 * */
	public static void main(String[] args) {
		
		int tishu = 0;
		int fenshu = 0; //获得总分
		int shengyu = 10; //剩余题数
		boolean tuichu = true; //提前退出条件
		int lxcw = 0 ; //当连续错误3次,游戏结束
		Scanner scan = new Scanner(System.in);
		System.out.println("-----欢迎来到喵喵答题游戏-----");
		while (tuichu==true) {
			final double d = Math.random();//获取0`1之间的小数
			final double d2 = Math.random();//获取0`1之间的小数
			tishu+=1;//题数++;
			if(lxcw>3) { // 连续错误3次后还错,结束游戏
				System.out.println("连续错误,提前结束");
				break;
			}
			if(fenshu+shengyu<6) { //如果以获得分数+剩余题数小于6分,则表明无法及格.提前退出
				System.out.println("你错的太多了,游戏结束");
				tuichu=false;
			}
			if(tishu>=10) {
				System.out.println("结束");
				break;
			}
			System.out.println("第"+tishu+"题开始:");
			final int suiji = (int)(d*1000); //强制转换成int,并且×1000 即,得到千位数的数值
			final int suiji2 = (int)(d2*1000); //获取第二位数值
			System.out.println(suiji+"+"+suiji2+"=");
			System.out.println("答案:");
			int daan = scan.nextInt();
			if(daan==0) {
				System.out.println("你选择了跳过");
			}else {
				if(daan==suiji+suiji2) {
					fenshu++;
					lxcw=0;
					System.out.println("答案正确,目前得分"+fenshu);
				}else {
					fenshu--;
					lxcw++;
					System.out.println("答案错误,扣一分.目前分数"+fenshu);
				}
			}
		}
		if(fenshu==10) {
			System.out.println("你是个天才!");
		}else if(fenshu>8&&fenshu<10) {
			System.out.println("还可以");
		}else if(fenshu>=6&&fenshu<10) {
			System.out.println("继续努力");
		}else if(fenshu<6&&fenshu>-7) {
			System.out.println("糟糕透了");
		}else {
			System.out.println("作弊可不好");
		}
	}
}
// 有个小漏洞,自己来发现吧.一个判断语句便可解决此漏洞~
// 虽然是个随机数,但是会不会随机出来2个0呢?这个概率有多少呢?使用0作为弃权合适吗?
// 使用for代替while会不会更好?需要怎么做呢?
```