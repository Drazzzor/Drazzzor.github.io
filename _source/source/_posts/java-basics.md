---
title: Java初学：被环境配置绊了一个星期
date: 2023-08-05 21:00:00
tags:
  - Java
  - 面向对象
  - 学习笔记
categories:
  - 编程学习
description: Java 入门时在 JDK、环境变量和面向对象上的踩坑记录，给刚开始学的朋友一点参考。
---

## 开头就卡住了

学完 C 之后转向 Java，我原以为会轻松一些，结果第一周全花在环境配置上。

Java 的运行需要 JDK。我下载完装好，命令行敲 `java -version` 却提示找不到命令。查了很久才知道要配环境变量：`JAVA_HOME` 指向安装目录，再把 `%JAVA_HOME%\bin` 加进 `PATH`。

配置大概是这样：

```text
JAVA_HOME = C:\Program Files\Java\jdk-17
PATH      = %JAVA_HOME%\bin;其他原有内容
```

配好之后重启命令行才生效。这个细节当时没人告诉我，我反复敲命令反复失败，一度怀疑是装错了版本。

## 从 C 到 Java 的落差

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

## 面向对象：观念上的转变

真正让我不适应的是面向对象的写法。

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

`this` 这个关键字我一开始总忘，然后就出现参数和成员变量同名、赋值没有生效的情况。这类错误编译器不报，只是结果不对，找起来费劲。

## 几个具体收获

- **文件名必须和 public 类名一致**。不一致直接编译不过，这一点 Java 比 C 严格。
- **字符串用 `equals` 比较**。用 `==` 比的是地址而不是内容，我在这里错过一次，两个看着一样的字符串判等得到 `false`，当时完全懵了。
- **数组越界会抛异常**。这比 C 友好，至少程序会明确告诉你哪里出错了，而不是默默改坏别的内存。

## 一点体会

Java 的代码比 C 长，写起来啰嗦，但换来的是更少的低级错误。它把很多容易出问题的地方交给了编译器和虚拟机去管。

环境配置那一周的挫败感现在想起来还有点印象。但也正因为栽过，后来帮同学配环境时我能一眼看出是 `PATH` 没生效。初学阶段的时间，大概都花在这种地方。
