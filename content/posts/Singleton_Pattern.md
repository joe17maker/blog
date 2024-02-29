---
title: "单例模式"
date: 2022-09-14T16:40:17+08:00
draft: false
tags: ["设计模式"]
categories: ["设计模式"]
---
单例模式只允许创建一个对象，因此节省内存，加快对象访问速度，因此对象需要被公用的场合适合使用，如多个模块使用同一个数据源连接对象等等。如： 
1. 需要频繁实例化然后销毁的对象。 
2. 创建对象时耗时过多或者耗资源过多，但又经常用到的对象。 
3. 有状态的工具类对象。 
4. 频繁访问数据库或文件的对象。  

以下都是单例模式的经典使用场景： 
1. 资源共享的情况下，避免由于资源操作时导致的性能或损耗等。如上述中的日志文件，应用配置。 
2. 控制资源的情况下，方便资源之间的互相通信。如线程池等。
## 从饿汉式写法到懒汉式写法

饿汉式就是用类变量存储初始化的实例。
```java
public class Singleton {
    private static volatile Singleton singleton;
    private Singleton() {
    }
    public static Singleton getSingletonInstance(){
        return singleton;
    }
}

```
{{< admonition >}}
饿汉式的缺点是假设不需要用到这个类的实例，但是它仍然初始化了。实际应用中这并不是一个大问题。
{{< /admonition >}}
懒汉式的写法最完美的是双重判断加锁，同时使用volatile保证可见性。
```java
public class Singleton {
    private static volatile Singleton singleton;
    private Singleton() {
    }
    public static Singleton getSingletonInstance(){
        if (singleton == null) {
            //可能两个线程同时判断通过
            synchronized (Singleton.class) {
                try {
                    Thread.sleep(1);
                } catch (InterruptedException e) {
                    throw new RuntimeException(e);
                }
                if (singleton == null) {
                    singleton = new Singleton();
                }
            }
        }
        return singleton;
    }
    public static void main(String[] args) {
        for (int i = 0; i < 1000; i ++) {
            new Thread(() -> {
                System.out.println(Singleton.getInstance().hashCode());
            }).start();
        }
    }
}

```

## 内部类
在类中创建一个内部类，比懒汉式优雅，需要更高的jdk版本支持。
```java
public class Singleton {
    private Singleton() {
    }
    private class SingletonInstance{
        private final static Singleton INSTANCE= new Singleton();
    }
    public static Singleton getInstance() {
        return SingletonInstance.INSTANCE;
    }
    public static void main(String[] args) {
        for (int i = 0; i < 1000; i ++) {
            new Thread(() -> {
                System.out.println(Singleton.getInstance().hashCode());
            }).start();
        }
    }
}
```


## 枚举
最简单的当然还是枚举类了，在枚举类中，每个实例的类型就是该枚举类。如下面代码，INSTANCE的类型为SingletonEnum。
并且枚举类在jvm层面线程安全，还可以防止序列化和反射攻击，应该说是一种最佳实践,写法相当优雅。
```java
public enum SingletonEnum{
    INSTANCE;

    //测试代码
    public static void main(String[] args) {
        for (int i = 0; i < 1000; i ++) {
            new Thread(() -> {
                System.out.println(SingletonEnum.INSTANCE.hashCode());
            }).start();
        }
    }
}
```