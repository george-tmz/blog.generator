---
title: "Java多线程原理"
date: 2020-11-18T20:57:10+08:00
draft: false
categories:
- 硬核空间Java课学习笔记
tags:
- Java
- 多线程
---

### 什么是多线程
- 一个程序同时执行多个任务，每一个任务称为一个线程（Thread）,它是线程控制的简称。
- 可以同时运行一个以上线程的程序称为多线程程序（multithreaded）。

### 为什么会有多线程
- CUP运行速度太快了，完成一个任务到执行下一个任务需要等待很长时间。
- 现代CUP多个核心，可并发执行多个任务。（CPU多核心是为了解决性能越高，发热量越大的瓶颈）
- Java的执行模型是同步的、阻塞的
- 默认情况下只有一个线程。处理问题自然，但有严重的性能问题。

### Thread类
 使用new操作符创建新的线程。`new Thread(r)`，该线程还没有开始运行，处于新创建状态。要使其运行调用
 `start()`方法。
``` java
new Thread(()->{
    System.out.println("这是一个新线程");
}).start();
```
thread是Java中唯一代表线程的东西。每多开一个线程，就多一个执行流。执行流中的方法栈（局部变量）是线程私有的。
静态变量、类变量是被所有线程共享的。

### 多线程带来了的麻烦
多线程提升了程序的性能，提升了使用体验。同时也带来了麻烦，使用它是有难度的。

因为多线程是以乱序执行的。一个可运行的线程可能正在运行也可能没有运行，这取决于操作系统给线程提供运行的时间。线程不会始终保持运行，
会被操作系统终端，让其他线程获得运行机会。
抢占式调度系统给每一个可运行线程一个时间片来执行任务。当时间片用完，操作系统剥夺该线程的运行权，并给另一个线程运行机会。

其实际问题是，多个线程同时操作，共享的数据。
``` java
public class testThread
{
    private static int i = 0;

    public static void main(String[] args) {
        for (int j = 0; j < 10; j++) {
            new Thread(testThread::add).start();
        }
    }

    private static void add() {
        try {
            Thread.sleep(1000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        i++;
        System.out.println(i);
    }
}
/**
1
1
1
2
4
3
7
6
5
8
*/
```
### 多线程的使用场景
- IO密集型应用
  - 网络IO
  - 文件IO



