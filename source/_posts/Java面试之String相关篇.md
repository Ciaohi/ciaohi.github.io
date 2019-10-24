---
title: Java面试之String相关篇
date: 2019-10-22 10:13:46
tags: [Java,String]
---
## Java substring() 方法
- substring() 方法返回字符串的子字符串。

### 语法
```bash
public String substring(int beginIndex)
```
或者
```bash
public String substring(int beginIndex, int endIndex)
```
### 参数
- beginIndex -- 起始索引（包括）, 索引从 0 开始。
- endIndex -- 结束索引（不包括）。
### 返回值

字符串

### 实例

```java

public class Test {
    public static void main(String args[]) {
        String Str = new String("ciaohi.github.io");
 
        System.out.print("返回值 :" );
        System.out.println(Str.substring(4) );
 
        System.out.print("返回值 :" );
        System.out.println(Str.substring(4, 10) );
    }
}


```
### 怎样将 GB2312 编码的字符串转换为 ISO-8859-1 编码的字符串？

- 代码如下所示:
```bash
String s1 = "你好";
String s2 = newString(s1.getBytes("GB2312"), "ISO-8859-1");
```

## 实现 String 类的 replaceAll 方法

- replaceAll 方法的本质是使用正则表达式进行匹配，最终调用的其实是 Matcher 对象的 replaceAll 方法。

## 是否可以继承 String 类?

- 不可以，因为 String 类有 final 修饰符，而 final 修饰的类是不能被继承的，实现细节不允许改变。

```bash
public final class String implements java.io.Serializable, 
Comparable<String>, CharSequence
```

## 给定两个字符串 s 和 t， 写一个函数来决定是否 t 是 s 的重组词。你可以假设字符串只包含小写字母。


```java
public class solution {
    public boolean isAnagram(String s, String t) {
        if(s.length()!=t.length())
            return false;
        int bit[] = new int[26];
        for(int i=0;i<s.length();i++){
            bit[s.charAt(i)-'a']++;
        }
        for(int i=0;i<s.length();i++){
            if(--bit[t.charAt(i)-'a']<0)
                return false;
        }
        return true;
    }


}

```

## String s=new String(“abc”);创建了几个 String 对象。

两个或一个，”abc”对应一个对象，这个对象放在字符串常量缓冲区，常量”abc”不管出现多少遍，都是缓冲区中的那一个。New String 每写一遍，就创建一个新的对象，它一句那个常量”abc”对象的内容来  
创建出一个新String 对象。如果以前就用过’abc’，这句代表就不会创建”abc”自己了，直接从缓冲区拿。


## 字符串如何转换为 int 类型

```java
public class Test {
	public static void main(String[] args) {
	//方式一
	int num=Integer.parseInt("123");
	//方式二
	int num2=Integer.valueOf("123");
	System.out.println(num+" "+num2);
	} 
}

```


## String 是最基本的数据类型吗?

- 不是 。Java 中的基本数据类型只有 8 个：byte、short、int、long、float、double、char、boolean；除了基本类型（primitive type）和枚举类型（enumeration type），剩下的都是引用类型  
（reference type）。

## String 和 StringBuilder、StringBuffer 的区别?

- Java 平台提供了两种类型的字符串：String 和 StringBuffer / StringBuilder

相同点：它们都可以储存和操作字符串，同时三者都使用 final 修饰，都属于终结类不能派生子类，操作的相关方法也类似例如获取字符串长度等；不同点：其中 String 是只读字符串，也就意味着   
String 引用的字符串内容是不能被改变的，而 StringBuffer 和 StringBuilder 类表示的字符串对象可以直接进行修改，在修改的同时地址值不会发生改变。StringBuilder 是 JDK 1.5 中引入的，它和   
StringBuffer 的方法完全相同，区别在于它是在单线程环境下使用的，因为它的所有方面都没有被 synchronized 修饰，因此它的效率也比 StringBuffer 略高。在此重点说明一下，String、StringBuffer、
StringBuilder 三者类型不一样，无法使用 equals()方法比较其字符串内容是否一样！

- 补充 1：有一个面试题问：有没有哪种情况用+做字符串连接比调用StringBuffer / StringBuilder 对象的 append 方法性能更好？如果连接后得到的字符串在静态存储区中是早已存在的，那么用+做字符串连  接是优于
StringBuffer / StringBuilder 的 append 方法的。
- 下面也是一个面试题，问程序的输出，看看自己能不能说出正确答案。

## String 类为什么是 final 的

1. 为了效率。若允许被继承，则其高度的被使用率可能会降低程序的性能。
2. 为了安全。JDK 中提供的好多核心类比如 String，这类的类的内部好多方法的实现都不是 java 编程语言本身编写的，好多方法都是调用的操作系统本地的 API，这就是著名的“本地方法调用”，也只有这样  
才能做事，这种类是非常底层的，和操作系统交流频繁的，那么如果这种类可以被继承的话，如果我们再把它的方法重写了，往操作系统内部写入一段具有恶意攻击性质的代码什么的，这不就成了核心病毒了  
么？不希望别人改，这个类就像一个工具一样，类的提供者给我们提供了， 就希望我们直接用就完了，不想让我们随便能改，其实说白了还是安全性，如果随便能改了，那么 java 编写的程序肯定就很不稳定  
，你可以保证自己不乱改， 但是将来一个项目好多人来做，管不了别人，再说有时候万一疏忽了呢？他也不是估计的， 所以这个安全性是很重要的，java 和 C++相比，优点之一就包括这一点。

## String s="Hello";s=s+"world!";执行后，是否是对前面 s指向空间内容的修改？


- 不是对前面 s 指向空间内容的直接修改。

- 因为 String 被设计成不可变(immutable)类，所以它的所有对象都是不可变对象。在这段代码中，s 原先指向一个 String 对象，内容是 "Hello"，然后我们对 s 进行了+操作，那么 s 所指向的那个对象  
是否发生了改变呢？答案是没有。这时，s 不指向原来那个对象了，而指向了另一个 String 对象，内容为"Hello world!"，原来那个对象还存在于内存之中，只是 s 这个引用变量不再指向它了。


- 通过上面的说明，我们很容易导出另一个结论，如果经常对字符串进行各种各样的修改，或者说，不可预见的修改，那么使用 String 来代表字符串的话会引起很大的内存开销。因为 String 对象建立之后  
不能再改变，所以对于每一个不同的字符串，都需要一个 String 对象来表示。这时，应该考虑使用StringBuffer 类，它允许修改，而不是每个不同的字符串都要生成一个新的对象。并且，这两种类的对象转换  
十分容易。同时，我们还可以知道，如果要使用内容相同的字符串，不必每次都 new一个 String。例如我们要在构造器中对一个名叫 s 的 String 引用变量进行初始化，把它设置为初始值，应当这样做：


```java

public class Demo {
	private String s;
	...
	public Demo { s = "Initial Value";
	}
	...
	}


```



而非


```bash
	s = new String("Initial Value");
```


- 后者每次都会调用构造器，生成新对象，性能低下且内存开销大，并且没有意义，因为 String 对象不可改变，所以对于内容相同的字符串，只要一个String 对象来表示就可以了。也就说，多次调用上面  
的构造器创建多个对象，他们的 String 类型属性 s 都指向同一个对象。上面的结论还基于这样一个事实：对于字符串常量，如果内容相同，Java认为它们代表同一个 String 对象。而用关键字 new 调用 
构造器，总是会创建一个新的对象，无论内容是否相同。至于为什么要把 String 类设计成不可变类，是它的用途决定的。其实不只String，很多 Java 标准类库中的类都是不可变的。在开发一个系统的时候，
我们有时候也需要设计不可变类，来传递一组相关的值，这也是面向对象思想的体现。不可变类有一些优点，比如因为它的对象是只读的，所以多线程并发访问也不会有任何问题。当然也有一些缺点，比如每  
个不同的状态都要一个对象来代表，可能会造成性能上的问题。所以 Java 标准类库还提供了一个可变版本，即 StringBuffer。



## 下面这条语句一共创建了多少个对象：String s="a"+"b"+"c"+"d";


- 对于如下代码：

```java
String s1 = "a";
String s2 = s1 + "b";
String s3 = "a" + "b";
System.out.println(s2 == "ab");
System.out.println(s3 == "ab");

```

- 第一条语句打印的结果为 false，第二条语句打印的结果为 true，这说明javac 编译可以对字符串常量直接相加的表达式进行优化，不必要等到运行期去进行加法运算处理，而是在编译时去掉其中的加号，  
直接将其编译成一个这些常量相连的结果。题目中的第一行代码被编译器在编译时优化后，相当于直接定义一个”abcd”的字符串，所以，上面的代码应该只创建了一个 String 对象。
- 写如下两行代码，


```java
String s = "a" + "b" + "c" + "d";
System.out.println(s == "abcd");
```


- 最终打印的结果应该为 true。









