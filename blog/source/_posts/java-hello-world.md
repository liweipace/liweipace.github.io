---
title: 'JAVA Hello World'
date: 2020-06-04 19:58:58
tags: 
- JAVA
- Hello World
---
# Java Hello World
## 基本类型和操作
  1. Class类：描述一类对象的行为和状态。Java一定要有一个和文件名完全相同的类。
  2. Method方法：方法就是行为，一个类可以有很多方法。逻辑运算、数据修改以及所有动作都是在方法中完成的。相当于python的函数。
  3. Object对象：对象是类的一个实例，有状态和行为。例如，一条狗是一个对象，它的状态有：颜色、名字、品种；行为有：摇尾巴、叫、吃等。
  4. 实例变量：每个对象都有独特的实例变量，对象的状态由这些实例变量的值决定。
  * 编译		`javac hello.java`
  * 执行编译后的文件	`java hello`
  * 所有的语句以`;`结尾
## 变量类型
所有相关信息参考[Python数据类型](https://www.runoob.com/java/java-basic-datatypes.html)
### 类型
```java
int a, b, c;         			// 声明三个int型整数：a、 b、c
int d = 3, e = 4, f = 5; 		// 声明三个整数并赋予初值
short smax = 32767, smin = -32768;	// 声明short类型的最大最小
long l = 23344242;			// 声明long类型
byte z = 22;     			// 声明并初始化 z
boolean bt = true, bf = false;		// 和python不同，都不大写
String s = "runoob";  			// 声明并初始化字符串 s
float f = 3.14;				// 声明单精度浮点型变量
double pi = 3.14159; 			// 声明了双精度浮点型变量 pi
char x = 'x';        			// 声明变量 x 的值是字符 'x'。
```
这里只有**String**是首字母大写

### 类型转换
```
低  ------------------------------------>  高

byte, short, char —> int —> long—> float —> double
```

## String的一些方法methods

```java
String str1 = "anything";
String str2 = "else";
System.out.println(str.length());	// 获得字符串长度
System.out.println(str1.concat(str2));	// 两个字符串的链接
System.out.println(str1.indexOf('a'));	// 获得字符在字符串中的位置，0是第一位
System.out.println(str1.charAt(0));	// 获得在某个index的字符
System.out.println(str1.toUpperCase());	// 大写
System.out.println(str1.toLowerCase());	// 小写
System.out.println(str1.equals(str2)); 	// 判断一致性
/*
==是等于，完全一致，一般用于原生基本类型的判断，但是equals方法是相同，拥有一致的含义，可以用于任意对象和引用性类型比如String
*/
```
## Arrays and ArrayLists 数组和动态数组
### 数组
```
int[] age = {20, 21, 30};	#初始化数组
int[] marks = new int[3]; 	#初始化空数组
marks[0] = 50;			#给数组赋值	
marks[1] = 70;
marks[2] = 93;
```


