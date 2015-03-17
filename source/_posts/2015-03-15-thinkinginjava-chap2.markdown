---
layout: post
title: "Java编程思想读书笔记（第二章）"
date: 2015-03-15 19:11:02 +0800
description: "Java编程思想第二章读书笔记"
keywords: Java
comments: true
categories: [Java, 读书笔记]
toc: true
tocstartlv: 3
---
参考书目：《Java编程思想》（第四版，中文版）
###2.3 永远不需要销毁对象
####2.3.2 对象的作用域
Java对象不具备和基本类型一样的生命周期。当用*new*创建一个Java对象时，它可以存活于作用域之外。例如：

	{
		String s = new String("a string");
	} // End of scope

不过与C++不同的是，在外界引用该Java对象时，不用担心它被销毁，就是说，这样做是安全的。由*new*创建的对象，只要你需要，就会一直保留下去。
<!-- more -->
###2.8 注释和嵌入式文档
####2.8.2 语法
所有javadoc命令都只能在“/\*\*"注释中出现，和通常一样，注释结束于“\*/”。*文档标签*是一些以“@”字符开头的命令。
####2.8.5 文档示例
``` java HelloDate.java
//: object/HelloDate.java
import java.util.*;
/** The first Thinking in Java example program.
* Displays a string and today’s date.
* @author Bruce Eckel
* @author www.MindView.net
* @version 4.0
*/
public class HelloDate {
/** Entry point to class & application.
* @param args array of string arguments
* @throws exceptions No exceptions thrown
*/
	public static void main(String[] args) {
		System.out.println("Hello, it’s: ");
		System.out.println(new Date());
	}
} /* Output: (55% match)
Hello, it’s:
Wed Oct 05 14:39:36 MDT 2005
*///:~
```
