---
layout: post
title: "Java编程思想读书笔记（第四章）"
date: 2015-03-19 15:25:36 +0800
description: "Java编程思想第四章读书笔记"
keywords: Java
comments: true
categories: [Java, 读书笔记]
toc: true
tocstartlv: 3
---
参考书目：《Java编程思想》（第四版，中文版）
###4.7 臭名昭著的goto
尽管goto仍是Java中的一个保留字，但在语言中并未使用它；Java没有goto。然而，Java也能完成一些类似于跳转的操作，这与break和continue这两个关键词有关。它们其实不是一个跳转，而是中断迭代语句的一种方法。
<!-- more -->
如果随同标签一起使用，它们会中断循环，直到标签所在的地方：

	label1:
	outer-iteration {
		inner-iteration {
			//...
			break; // (1)
			//...
			continue; // (2)
			//...
			continue label1; // (3)
			//...
			break label1; // (4)
		}
	}

在（1）中， **break** 中断内部迭代，回到外部迭代。在（2）中， **continue** 使执行点移回内部迭代的起始处。在（3）中， **continue label1** 同时中断内部迭代以及外部迭代，直接转到 **label1** 处；随后，它实际上是继续迭代过程，但却从外部迭代开始。在（4）中，**break label1** 也会中断所有迭代，并回到 **label1** 处，但并不重新进入迭代。也就是说，它实际是完全终止了两个迭代。

在Java中，需要使用标签的唯一理由就是因为有循环嵌套存在，而且想从多层嵌套中break或continue。