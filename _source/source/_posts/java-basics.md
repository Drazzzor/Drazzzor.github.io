---
title: Java初学
date: 2023-08-05 21:01:55
tags:
  - Java
  - 面向对象
  - 学习笔记
categories:
  - 编程学习
description: Java 入门时在 JDK、环境变量和面向对象上的学习经历。
---

## 环境配置

学完 C 之后转向 Java，虽然语法逻辑有诸多相像，但Java运行还要先配置环境。

Java 的运行需要 JDK。我下载完装好，命令行敲 `java -version` 提示找不到命令。搜了才知道要配环境变量：`JAVA_HOME` 指向安装目录，再把 `%JAVA_HOME%\bin` 加进 `PATH`。

配置大概是这样：

```text
JAVA_HOME = C:\Program Files\Java\jdk-17
PATH      = %JAVA_HOME%\bin;其他原有内容
```

配好之后重启命令行才生效。

##  C 和 Java 的差别

第一节课写的是这个：

```java
public class Hello {
    public static void main(String[] args) {
        System.out.println("Hello");
    }
}
```

一个简单的输出，外面套了这么多层。当时我的疑问是：`public` 是什么，`static` 是什么，为什么类名和文件名必须一样。

老师的回答是可以先照着写，后面会讲。老实说我照着写了一段时间之后才慢慢理解：Java 的一切都装在类里，`main` 是程序的入口，`static` 表示它不需要先创建对象就能运行。

## 面向对象

在 C 里，数据和处理数据的函数是分开的；在 Java 里，它们被装进同一个类。

```java
public class Student {
    private String name;
    private int age;

    public Student(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public void sayHello() {
        System.out.println("我是 " + name);
    }
}
```

## 几个具体收获

- **文件名必须和 public 类名一致**。不一致直接编译不过，这一点 Java 比 C 严格。
- **字符串用 `equals` 比较**。用 `==` 比的是地址而不是内容。
- **数组越界会抛异常**。这比 C 友好，至少程序会明确告诉你哪里出错。

## 一点体会

面向对象的思想就像是指挥某人去做某事。

Java 的代码比 C 长，写起来啰嗦，但换来的是更少的低级错误。编译器和虚拟机处理了很多问题。

Java的类库真的丰富。
