---
title: "Object类的方法"
date: 2020-07-01T16:25:10+08:00
draft: false
# tags: ["并发","多线程"]
categories: ["java基础"]
---

Object类中有众多方法，其中包括equals() hashcode() toString clone()等

## 为什么重写equals也必须要重写hashcode
我们知道，如果重写了equals,那么我们应该重写hashcode使得equals方法判定相同的两个对象的hashcode也必须相同，那么这是为什么呢?不重写会有什么问题？   

问题的关键在于HashMap等使用了对象的equals hashcode的方法。
在判断一个对象是否equals时，我们一般会先调用hashcode方法，因为相等的对象hashcode一定相同，而不相同的对象hashcode可能相同也可能不同，但是不同的hashcode的对象一定不同。  (这是一种规范，hashmap等容器遵循这种规范)

查看HashMap的源码，我们也可以看到这种逻辑, 可以看到hashmap在存放一个值时，会先看hashcode是否相同，如果不同会插入到链表尾部。假设我们定义了一个对象Person 包含id 姓名，我们重写了equals方法，认为id相同的person时equal的。但是如果我们没有重写hashcode方法，在插入时，就会存在两个相同id的person类而不是替换value，hashmap无法按我们的预想工作。
```java
    final V putVal(int hash, K key, V value, boolean onlyIfAbsent,
                   boolean evict) {
        Node<K,V>[] tab; Node<K,V> p; int n, i;
        if ((tab = table) == null || (n = tab.length) == 0)
            n = (tab = resize()).length;
        if ((p = tab[i = (n - 1) & hash]) == null)
            tab[i] = newNode(hash, key, value, null);
        else {
            Node<K,V> e; K k;
            if (p.hash == hash &&
                ((k = p.key) == key || (key != null && key.equals(k))))
                e = p;
            else if (p instanceof TreeNode)
                e = ((TreeNode<K,V>)p).putTreeVal(this, tab, hash, key, value);
            else {
                for (int binCount = 0; ; ++binCount) {
                    if ((e = p.next) == null) {
                        p.next = newNode(hash, key, value, null);
                        if (binCount >= TREEIFY_THRESHOLD - 1) // -1 for 1st
                            treeifyBin(tab, hash);
                        break;
                    }
                    if (e.hash == hash &&
                        ((k = e.key) == key || (key != null && key.equals(k))))
                        break;
                    p = e;
                }
            }
            if (e != null) { // existing mapping for key
                V oldValue = e.value;
                if (!onlyIfAbsent || oldValue == null)
                    e.value = value;
                afterNodeAccess(e);
                return oldValue;
            }
        }
        ++modCount;
        if (++size > threshold)
            resize();
        afterNodeInsertion(evict);
        return null;
    }

    final Node<K,V> getNode(Object key) {
        Node<K,V>[] tab; Node<K,V> first, e; int n, hash; K k;
        if ((tab = table) != null && (n = tab.length) > 0 &&
            (first = tab[(n - 1) & (hash = hash(key))]) != null) {
            if (first.hash == hash && // always check first node
                ((k = first.key) == key || (key != null && key.equals(k))))
                return first;
            if ((e = first.next) != null) {
                if (first instanceof TreeNode)
                    return ((TreeNode<K,V>)first).getTreeNode(hash, key);
                do {
                    if (e.hash == hash &&
                        ((k = e.key) == key || (key != null && key.equals(k))))
                        return e;
                } while ((e = e.next) != null);
            }
        }
        return null;
    }
```

#### 参考
https://zhuanlan.zhihu.com/p/50206657
https://www.51cto.com/article/694975.html