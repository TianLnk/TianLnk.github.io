title: Scanner用户输入
author: 田亮
abbrlink: '4608'
tags:
  - Java
categories:
  - Java
date: 2019-04-05 21:53:00
---
scanner用来获取用户输入的值.并且进入scanner方法里程序会暂停
# scanner使用方法
1. 需要在代码最上面(main方法前面)导入scanner的包,导入语句:*import java.util.Scanner;*
2. 在main方法体内声明scanner:*Scanner scan=new Scanner(System.in);*
3. 使用scanner方法:*int a=scan.nextInt();* 

```java
import java.util.Scanner;
public class inta {

	public static void main(String[] args) {
		Scanner scan=new Scanner(System.in);
		System.out.println("请输入一个数字:");
		int a=scan.nextInt(); // 获取用户输如的数字
	}
}
```
<!--more-->