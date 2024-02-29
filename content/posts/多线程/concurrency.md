---
title: "java中的锁"
date: 2022-08-14T10:40:10+08:00
draft: false
tags: ["并发","多线程"]
categories: ["并发"]
---
## synchronized
synchronized是java虚拟机层面实现的锁,
一般的使用：
```java
synchronized (lock) {
    //
    while() {
        lock.wait();
    }
    //
    lock.notify();//lock.notifyAll();
}
```
在写一个程序时报错，java.lang.IllegalMonitorStateException。分析代码后发现时因为把Boolean类用作了锁。
原因是类似Integer Boolean等基本类型的包装类的值是不可变的,而假设对一个Integer进行++类似的操作，实际上所引用的对象已经发生了改变。
```java
private final int value;
```
在写https://leetcode.cn/problems/fizz-buzz-multithreaded/submissions/ 
这道题时出现了一个诡异的错误，明明正确打印了所有的字符串，但是却始终报超时
我的代码如下：
```java
class FizzBuzz {
    private int n;

    public FizzBuzz(int n) {
        this.n = n;
    }
    
    private volatile int i = 1;

    public void fizz(Runnable printFizz) throws InterruptedException {
        while (i <= n)
            synchronized (this) {
                while (!(i % 3 == 0 && i % 5 != 0)) {
                    this.wait();
                }
                if (i <= n && i % 3 == 0 && i % 5 != 0) {
                    printFizz.run();
                    i ++;
                }
                this.notifyAll();
            }
    }

    // printBuzz.run() outputs "buzz".
    public void buzz(Runnable printBuzz) throws InterruptedException {
        while (i <= n)
            synchronized (this) {
                while (!(i % 5 == 0 && i % 3 != 0)) {
                    this.wait();
                }
                if (i <= n && i % 5 == 0 && i % 3 != 0) {
                    printBuzz.run();
                    i ++;
                }
                this.notifyAll();
            }
    }

    // printFizzBuzz.run() outputs "fizzbuzz".
    public void fizzbuzz(Runnable printFizzBuzz) throws InterruptedException {
        while (i <= n)
            synchronized (this) {
                while (!(i % 5 == 0 && i % 3 == 0)) {
                    this.wait();
                }
                if (i <= n && i % 5 == 0 && i % 3 == 0) {
                    printFizzBuzz.run();
                    i ++;
                }
                this.notifyAll();
            }
    }

    // printNumber.accept(x) outputs "x", where x is an integer.
    public void number(IntConsumer printNumber) throws InterruptedException {
        while (i <= n)
            synchronized (this) {
                while (i % 5 == 0 || i % 3 == 0) {
                    this.wait();
                }
                if (i <= n && !(i % 5 == 0 || i % 3 == 0)) {
                    printNumber.accept(i);
                    i ++;
                }
                this.notifyAll();
            }
    }
}
```
那么虽然正确地同步了线程，但是却无法正常退出，分析可知，唯一可能的原因在于这段代码：
```java
                while (i % 5 == 0 || i % 3 == 0) {
                    this.wait();
                }
```
对于四个线程都是一样，当其他线程满足退出了，之前正在等待的线程由于i无法再更新，会一直卡在这个地方，无法正常退出，修改的方式也很简单，只需要在判断添加中加上i <= n；这样当程序结束不会再循环等待。