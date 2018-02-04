---
layout: post
title: How I Rest From Work
date: 2018-02-01 13:32:20 +0300
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: i-rest.jpg # Add image post (optional)
tags: [academic]
---
synchronized实现原理：synchronized可以保证某个时刻，只有一个线程可以执行某个方法或者某个代码块。synchronized有三种用法，

修饰实例方法时，进入代码时要获得实例对象的锁，修饰静态方法时，进入同步代码前要获得类对象的锁，修饰同步代码块时，

要指定相应的锁对象。synchronized修饰同步方法和同步代码块，底层实现是不一样的。当修饰同步代码块时，synchronized关键字经过编译后，

会在同步代码块前后分别形成monitorenter和monitorexit这两个字节码的指令，并且这两个指令都需要一个refenence类型的参数来指名

要锁定和解锁的对象。当执行monitorenter指令的时，首先要尝试获取对象的锁。如果这个对象还没有被锁定，或者当前线程已经拥有了那个对象的锁，

把锁的计数器＋1，相应的在执行monitorexit时，会将锁计数器－1，当计数器是0时，锁就释放了。如果获取对象锁失败，则当前线程阻塞。

synchronized修饰方法时，无需通过字节码指令来完成，它实现在方法调用和返回之中，JVM可以从常量池中的方法表结构中

的ACC_SYNCHRONIZED访问标志来区别一个方法是不是同步方法。当方法调用时，调用指令会检查方法的ACC_SYNCHRONIZED访问标志是否被设置，

如果设置了，线程将先持有monitor，再执行方法，执行完之后，释放monitor。在方法执行期间，如果一个线程持有了monitor，

其他线程将无法再获取同一个monitor，如果一个同步方法在执行期间抛出了异常，并且内部无法处理，那这个同步方法所持有的monitor将在异常抛到同步方法之外时自动释放。