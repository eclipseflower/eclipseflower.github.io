---
layout: post
title: "Java编程思想读书笔记（第三章）"
date: 2015-03-17 14:12:45 +0800
description: "Java编程思想第三章读书笔记"
keywords: Java
comments: true
categories: [Java, 读书笔记]
toc: true
tocstartlv: 3
---
参考书目：《Java编程思想》（第四版，中文版）
###3.7 关系操作符
####3.7.1 测试对象的等价性
<!-- more -->
关系操作符==和!=也适用于所有对象。下面是一个例子：

``` java Equivalence.java
//: operators/Equivalence.java
public class Equivalence {
	public static void main(String[] args) {
		Integer n1 = new Integer(47);
		Integer n2 = new Integer(47);
		System.out.println(n1 == n2);
		System.out.println(n1 != n2);
	}
} /* Output:
false
true
*///:~
```

这里我们可以发现，尽管对象的内容相同，然而对象的引用却是不同的，而==和!=比较的就是对象的引用。所以输出结果先是false再是true。

如果想比较两个对象的实际内容是否相同，就应该使用方法**equals()**。举例说明：

``` java EqualsMethod.java
//: operators/EqualsMethod.java
public class EqualsMethod {
	public static void main(String[] args) {
		Integer n1 = new Integer(47);
		Integer n2 = new Integer(47);
		System.out.println(n1.equals(n2));
	}
} /* Output:
true
*///:~
```

结果正如我们预料的那样。但是，假如你创建了**自己的类**，就像下面这样：

``` java EqualsMethod2.java
//: operators/EqualsMethod2.java
// Default equals() does not compare contents.
class Value {
	int i;
}
public class EqualsMethod2 {
	public static void main(String[] args) {
		Value v1 = new Value();
		Value v2 = new Value();
		v1.i = v2.i = 100;
		System.out.println(v1.equals(v2));
	}
} /* Output:
false
*///:~
```

结果又是false！这是由于equals()的默认行为是比较引用。所以我们需要在自己的新类中覆盖equals()方法。
