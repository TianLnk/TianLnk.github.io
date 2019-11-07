title: Java数组
author: 田亮
abbrlink: d18e
tags:
  - Java
categories:
  - Java
date: 2019-04-10 19:01:00
---
数组用来存储固定大小的同类型元素。
<font color="#DF3A01">程序 = 算法 + 数据结构</font>
> 所谓数据结构,就是把数据按照特定的某种结构来保存
算法:解决问题的步骤/流程
数组就是最基本的一种数据结构

# 什么是数组
数组就是相同数据类型的元素组成的集合
元素按照线性顺序排列(参考一根线穿过N个球)每个元素都有一个位置信息:下标 并且是唯一的.根据下标来找到相应的元素
下标从0开始,-1是最后一个
{1,234,567,2,134,43,3456,543} 这就是数组,必须是相同类型,不能在其中插入字符串等类型
数据类型 [] 数组名称 = new 数据类型[长度];
<!--more-->
- 数组可以是一维数组、二维数组或多维数组。
- 数值数组元素的默认值为 0，而引用元素的默认值为 null。
- 交错数组是数组的数组，因此，它的元素是引用类型，初始化为 null。交错数组元素的维度和大小可以不同。
- 数组的索引从 0 开始，如果数组有 n 个元素，那么数组的索引是从 0 到（n-1）。
- 数组元素可以是任何类型，包括数组类型。


```Java
int a[] = {1,23,4,567,543,234,765}; //声明一个数组,并且赋值   第一中方法
int[] b =new int[4]; //声明长度为4的数组,不赋值  第二种方法
b[0]=1;
b[1]=11;
b[2]=111;
b[3]=1111; 
int c[] =new int[]{1,2,4,6}; // 声明一个数组,并且立即赋值  第三种方法

for (int i = 0; i < a.length; i++) { // 数组需要使用循环来输出
    System.out.println(a[i]);
}
```


# 如何使用数组
数组的默认值:byte,short,char,int,long为0;
float,double为0.0;
boolean为false;
通过 **数组名.length** 可以获取数组的长度. 这是最常用的一个方法
```Java
int a[] = {1,23,4,567,543,234,765};
	System.out.println(a.length); //输出:7
    
 int[] a = new int [100];//声明一个数组,有100个元素
			for (int i = 0; i < a.length; i++) {
				a[i] = (int)(Math.random()*100);//获取100以内的随机数并赋值给a数组
				System.out.print(a[i]+"  ");
				if(i%10==0)//每输出10个换行
					System.out.println();
			}
```
# 数组获取最大值,最小值
```Java
int[] a = new int[100];
int max = a[0]; // 假设最大值为第一位
int min = 100;
for (int i = 0; i < a.length; i++) {
	a[i] = (int)(Math.random()*100);
	System.out.print(a[i]+"  ");
	if(i%10==0&&i!=0) {
		System.out.println();
	}
}
for (int i = 0; i < a.length; i++) {
	if (a[i]>max) { //找最大值
		max=a[i];
	}
	if(min>a[i]) { //找最小值
		min=a[i];
	}
}
	System.out.println();
	System.out.println("最大值:"+max);
	System.out.println("最小值:"+min);
```
# 数组的复制
使用方法: *System.arraycopy()*方法实现数组的复制
System.arraycopy(arg0, arg1, arg2, arg3, arg4);
arg0:源数组
arg1:源数组中的起始位置
arg2:目标数组
arg3:目标数组中的起始位置
arg4:要复制数组元素的数量

```Java
int[] a = {1,2,3,4,5,6,7,8,9};
		int []b = {11,12,13,14,15,16,17,18}; 
		System.arraycopy(a, 0, b, 3, 5);
		for (int i = 0; i < b.length; i++) {
			System.out.print(a[i]+"  ");
		}
		System.out.println();
		for (int i = 0; i < b.length; i++) {
			System.out.print(b[i]+" ");
		}
//输出:
1  2  3  4  5  6  7  8 9
11 12 13 1 2 3 4 5 
```
使用方法:*Arrays.copyOf()*实现数组的复制
Arrays.copyOf(arg0, arg1);
arg0:源数组
arg1:要复制数组元素的数量
```Java
import java.util.Arrays; //引用类
int[] a = {1,2,3,4,5,6,7,8,9};
		int []b = Arrays.copyOf(a, 4);
		for (int i = 0; i < a.length; i++) {
			System.out.print(a[i]+"  ");
		}
		System.out.println();
		for (int i = 0; i < b.length; i++) {
			System.out.print(b[i]+" ");
		}
//相对于上面的方法,这个更加简单
//输出:
1  2  3  4  5  6  7  8  9  
1 2 3 4 
```

# 数组的扩容
数组的长度在创建之后是无法改变的,就像一个盒子,里面只有10个格子,只能放10个东西,如果想要放下更多的东西只能更换一个更大的盒子
所谓扩容就是指创建一个更大的新数组并将原有数组的数据复制到其中
可以使用*Arrays.copyOf()*方法,简便实现数组的扩展
```Java
int[] a = {1,2,3,4,5,6,7,8,9};
		int []b = Arrays.copyOf(a, a.length+3); //复制a到b并且增加3个默认值为0的数据
		System.out.println();
		for (int i = 0; i < b.length; i++) {
			System.out.print(b[i]+" ");
		}
//输出:
1 2 3 4 5 6 7 8 9 0 0 0 
```
将数组中的最大数放到最后一位,并且不替换原本的数组
```Java
int[] a= {1,5,4,8,2,65,234};
		int max = a[0]; //获取最大值
		int[] b = Arrays.copyOf(a,a.length+max);// 扩容max数组
		for (int i = 0; i < a.length; i++) {
			if (max<a[i]) {
				max=a[i];
			}
		}
		b[b.length-1]=max; //将最大值赋值给最后一位
		for (int j = 0; j < b.length; j++) { //输出数组
			System.out.println(b[j]);
		}
```

# 数组的排序
排序是对数组施加的最常用的算法
所谓排序,就是指将数组从大到小或从小到大进行有序的排列.
对于比较大的数组,排序的算法尤其重要
**一般情况下,通过排序过程中数组元素的交换次数来衡量排序算法的优劣**
常用的排序算法有:冒泡排序,快速排序,插入排序等
## *Arrays.sort()* 方法进行数组排序
这是Java JDK 提供的方法封装了数组的排序算法
```Java
int[] a= {3,1,677,2,567,9432,55,215,5675454,356,452523};
		Arrays.sort(a); //直接调用,非常方便 做升序排列,效率很高
		for (int i = 0; i < a.length; i++) {
			System.out.print(a[i]+"  ");
		}
```
听说这个方法的效率是非常高的.我做了个亿级别的实验,挺快的
```Java
long time = System.currentTimeMillis(); //获取时间
		System.out.println(time);
		int[] a=new int[100000000]; //获取一个亿级别的数组
		for (int i = 0; i < a.length; i++) {
			a[i]=(int)(Math.random()*100);//分配随机数给数组,,,不可能自己慢慢写一亿个吧
		}
		Arrays.sort(a); //进行升序排序(从小到大)
		long time2 = System.currentTimeMillis(); //获取时间
		System.out.println(time2);
		//做个死,输出到控制台
		for (int i = 0; i < a.length; i++) {
			System.out.print(a[i]+"  ");
			if(i%20==0) {
				System.out.println();
			}
		}
		long time3 = System.currentTimeMillis(); //获取时间
		System.out.println(time3);
// 并没有输出到控制台,因为输出到一半我才发现控制台存储的内容有限,无法全部显示
```
## 冒泡排序
冒泡排序是最早出现也是最经典的一种排序算法.但是效率有点低下

```
int[] a = {23,12,45,78}; //升序
第一轮:23和12比:变成 12,23,45,78
	  23和45比:变成 12,23,45,78
     45和78比:变成 12,23,45,78
     得到最后一位数78
第二轮:12和23比:变成 12,23,45,78
	  23和45比:变成 12,23,45,78
     得到第三位数45
第三轮:12和23比:变成 12,23,45,78
     得到第二位数23
结果:12,23,5,78
```

代码实战:
```Java
int[] a={1,4,32,56,31,14,56};
for (int i = 0; i < a.length-1; i++) {//控制论数
	for (int j = 0; j < a.length-1-i; j++) {//控制每轮次数
		if(a[j]>a[j+1]) {//每次都是和它的下一个数比较  大于是升序,小于是降序哦
			int t = a[j]; //初始化一个t,假设第一位数是最小的
			a[j]=a[j+1]; //替换,a[0]比a[0+1]大,所以替换成a[0+1]
			a[j+1]=t; //再将替换的赋值给t
		}
	}
}
for (int i = 0; i < a.length; i++) {
	System.out.print(a[i]+"  ");
}
// 输出:
1  4  14  31  32  56  56  
```
所以,相比较于*Arrays.sort()*冒泡排序显得更加繁琐(~~咋不说冒泡排序比较难呢~~)