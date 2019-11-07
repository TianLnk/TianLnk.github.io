title: C/C++定义和使用结构体变量
author: 田亮
abbrlink: 9cdb
tags:
  - C
categories:
  - C
date: 2019-04-27 14:07:00
---
在某些情况下,有些数据是成组出现的,而且相互关联.比如一个学生的学号,年龄,性别等都属于学生类
```C
#include <stdio.h>
int main(){
	struct a //声明结构体类型
	{
		int num; 
		char name[20];
		float chengji;
	}a1,a2;//定义2个结构体变量  分号不能缺
    

	printf("diyige\n");
	scanf("%d%s%f",&a1.num,a1.name,&a1.chengji);//因为name是数组,本身代表地址,所以无需再加&
	printf("dierge\n"); 
	scanf("%d%s%f",&a2.num,a2.name,&a2.chengji);
	if(a1.chengji>a2.chengji){
		printf("%d  %s  %6.2f\n",a1.num,a1.name,a1.chengji);
	}else if(a1.chengji<a2.chengji){
		printf("%d  %s  %6.2f\n",a2.num,a2.name,a2.chengji);
	}else{
		printf("%d  %s  %f\n",a1.num,a1.name,a1.chengji);
		printf("%d  %s  %f\n",a2.num,a2.name,a2.chengji);
	}
}
```
<!--more-->
## 定义结构体数组
```C
#include <stdio.h>
int main(){
	struct a//声明结构体类型
	{
		int num; 
		char name[20];
	}b[3]={{0,"张三"},{0,"李四"},{0,"王五"}};//定义结构体数组并且初始化
	int i,t=0;
	char c[20];//姓名

	while(t<5){
		t++;
		printf("投票给:\n");
		scanf("%s",c);
		for(i=0;i<3;i++){
		if(strcmp(c,b[i].name)==0){
			b[i].num++;
			break;
			}
		}
	}
	printf("投票结果如下:\n");
	for(i=0;i<3;i++){
		printf("姓名:%s,共计%d票\n",b[i].name,b[i].num);
	}

}
```
## 指向结构体变量的指针
指向结构体对象的指针的变量既可以指向结构体变量也可以指向结构体数组中的元素.指针变量的基类型必须与结构体变量的类型相同
```C
#include <stdio.h>
#include <string.h>
int main(){
	struct a{
		long num;
		char name[20];
	};
	struct a b;//定义a类型的变量b
	struct a *c;//定义a类型的指针变量c
	c=&b;//c指向b
	b.num=2333.233;
	strcpy(b.name,"xiaosan");//字符串复值函数给b.name赋值
	printf("%d  %s\n",(*c).num,b.name);//使用指针输出必须要括起来.因为"."的优先级最高
}
```
## 指向运算符
**为了使用方便,C语言允许把(\*p).num用 p ->num表示
->表示一个箭头,p->num表示p所指向的结构体变量中的num成员**
## 指向结构体数组的指针
```C
#include <stdio.h>
struct a{
	int age;
	char name[20];
	char sex;//性别
};
struct a b[3]={{18,"斩杀",'m'},{11,"拉拉",'m'},{22,"哈哈",'m'}};
//结构体可以写在函数外面哦
int main(){
	struct a *c;
	c=b;//指向b
	int i;
	printf("年龄   名字   性别\n");
	for (c;c<b+3;c++)
	{
		printf("%3d %7s %4c\n",c->age,c->name,c->sex);
	}
	/*for (i=0;i<3;i++) //等同于上面
	{
		printf("%3d %7s %4c\n",(c+i)->age,(c+i)->name,(c+i)->sex);
	}*/

}
```
## 建立的简单的静态链表
**链表根据需要 开辟内存单元**
声明一个结构体类型, 包括多个 变量,其中有一个指针变量
所有节点都是在程序中定义的,也不能用完后释放.这种称之为"静态链表"

```C
#include <stdio.h>
struct student 
	{
		int age;
		float chengji;
		struct student * next;
	}; 
int main()
{
	struct student a,b,c,*d,*e,*f;
	a.age=18;
	a.chengji=88;

	b.age=22;
	b.chengji=90;

	c.age=12;
	c.chengji=60;

	d=&a; //将节点a的起始地址给指针d
	a.next=&b; //将节点b的起始地址赋值给a节点的next成员
	b.next=&c; //将节点c的起始地址赋值给b节点的next成员
	c.next=NULL; //c节点的next成员不存放其它结点地址
	e = d; //使e也指向a节点
	do{
		printf("%d     %f \n",e ->age,d ->chengji );
		e=e->next;
	}while(e!=NULL);//如果为空,表示这是链表的最后(链表结束)

}
```
## 共用体类型
同一段内存存放不同类型的变量,叫做共用体类型
结构体变量所占的内存长度是各成员所占的内存长度之和.而共用体变量所占的内存长度等于最长的成员长度.
**同一个内存段可以用来存放几种不同类型的成员,但在每一个瞬时只能存放其中一个成员而不是同时存放几个**
```C
#include <stdio.h>
int main(){
	union a{
		int c;
		char b;
	}x,y,z;
	x.b=55;//赋值给a共用体所有的变量.并且不能同时初始化3个成员
	printf("%d\n",x.c);//输出55
	printf("%d\n",x.b);//输出55
	printf("%f\n",x.b);//输出0.0000
	printf("%c\n",x.b);//输出7
}
```
进阶
```C
#include <stdio.h>
struct{//定义一个无名构造体函数
	char name[20];//姓名
	char sex;//性别
	int job;//职业 学生为1 老师为2
	union{
		int clas;//班级
		char zhiwu[10];//职务
	}a;//共用体变量a
}p[2];//定义结构体数组
int main(){
	int i;
	for(i=0;i<2;i++){
		printf("请输入相关信息:\n");
		scanf("%s %c %d",&p[i].name,&p[i].sex,&p[i].job);
		if(p[i].job==1){
			printf("输入:\n");
			scanf("%d",&p[i].a.clas);
		}else if(p[i].job==2){
			printf("输入2:\n");
			scanf("%s",&p[i].a.zhiwu);
		}else{
			printf("错误\n");
		}
	}
	for(i=0;i<2;i++){
		printf("%s,%c,%d,%d\n",p[i].name,p[i].sex,p[i].job,p[i].a.clas);
	}
}
```
## 枚举类型
如果一个变量只有几种可能的值,则可以定义为**枚举类型**.所谓枚举,就是指把可能的值一一列举出来,变量的值只限于列举出来的值范围
c语言对枚举类型的枚举元素按常量处理,故称之为**枚举常量**不要因为它们是标识符(有名字)就把它们当作变量,不能对他们进行赋值
**enum[枚举名]{美剧元素表};**
```C
# include <stdio.h>
int main(){
	enum meiju{a,b,c,d,e,f,g}mm;
	printf("%d\n",mm);//输出7 因为它有7个元素
}
```
进阶
```C
# include <stdio.h>
int main(){
	//口袋中有五种颜色的球,每次从口袋中取出3个,请问有多少种组合条件
	enum yanse{red,yellow,blue,white,black};//声明枚举类型
	enum yanse i,j,k,p;//定义枚举变量
	int n=0,loop;
	for(i=red;i<=black;i++)//循环5次
	{
		for(j=red;j<=black;j++){
			if(i!=j){ //如果两个球不同色
				for(k=red;k<=black;k++){
					if((k!=i)&&(k!=j)){//如果三个球不同色
						n++;
						printf("%-4d",n);//输出当前是第几个符合条件的组合
						for(loop=1;loop<=3;loop++){
							switch(loop){
								case 1:
									p=i;
									break;
								case 2:
									p=j;
									break;
								case 3:
									p=k;
									break;
								default:
									break;
							}
							switch(p){
								case red:
									printf("%-10s","red");
									break;
								case yellow:
									printf("%-10s","yellow");
									break;
								case blue:
									printf("%-10s","blue");
									break;
								case white:
									printf("%-10s","white");
									break;
								case black:
									printf("%-10s","black");
									break;
								default:
									break;
							}
						}
						printf("\n");
					}
				}
			}
		}
	}
printf("共计:%d个\n",n);
}
```
## 用typedef声明新类型名
除了可以使用c语言规定的标准类型名外,还可以自定义类型名
比如:
```C
# include <stdio.h>
int main(){
	typedef int a;//这样a就会被系统认为是int
	a b=10;
	int c=10;
	printf("%d\n",b);//输出10
	printf("%d\n",c);//输出10
	printf("%d\n",b+c);//输出20
}
```
















