---
title: Java面试题之集合篇
date: 2019-10-22 15:08:23
tags: [Java,List]
---

## Java 集合体系结构（List、Set、Collection、Map 的区别和联系）

1. Collection 接口存储一组不唯一，无序的对象
2. List 接口存储一组不唯一，有序（插入顺序）的对象
3. Set 接口存储一组唯一，无序的对象
4. Map 接口存储一组键值对象，提供 key 到 value 的映射。Key 无序，唯一。value 不要求有序，允许重复。（如果只使用 key 存储，而不使用value，那就是 Set）


## Vector 和 ArrayList 的区别和联系
- 相同点：
1. 实现原理相同---底层都使用数组
2. 功能相同---实现增删改查等操作的方法相似
3. 都是长度可变的数组结构，很多情况下可以互用
- 不同点：
1. Vector 是早期 JDK 版本提供，ArrayList 是新版本替代 Vector 的
2. Vector 线程安全，ArrayList 重速度轻安全，线程非安全长度需增长时，Vector 默认增长一倍，ArrayList 增长 50%

## ArrayList 和 LinkedList 的区别和联系

- 相同点：两者都实现了 List 接口，都具有 List 中元素有序、不唯一的特点。
- 不同点：ArrayList 实现了长度可变的数组，在内存中分配连续空间。遍历元素和随机访问元素的效率比较高；
|0|1|2|3|4|
| :---: |  :---: |  :---: |  :---: |  :---: | 
|a|b|c|d|e|


## HashMap 和 Hashtable 的区别和联系

- 相同点：实现原理相同，功能相同，底层都是哈希表结构，查询速度快，在很多情况下可以互用
- 不同点：
1. Hashtable 是早期提供的接口，HashMap 是新版 JDK 提供的接口
2. Hashtable 继承 Dictionary 类，HashMap 实现 Map 接口
3. Hashtable 线程安全，HashMap 线程非安全
4. Hashtable 不允许 null 值，HashMap 允许 null 值


## HashSet 的使用和原理（hashCode()和 equals())
1. 哈希表的查询速度特别快，时间复杂度为 O（1）。
2. HashMap、Hashtable、HashSet 这些集合采用的是哈希表结构，需要用到 hashCode 哈希码，hashCode 是一个整数值。
3. 系统类已经覆盖了 hashCode 方法 自定义类如果要放入 hash 类集合，必须重写 hashcode。如果不重写，调用的是 Object 的 hashcode，而Object 的 hashCode 实际上是地址。
4. 向哈希表中添加数据的原理：当向集合 Set 中增加对象时，首先集合计算要增加对象的 hashCode 码，根据该值来得到一个位置用来存放当前对象，如在该位置没有一个对象存在的话，那么集合 Set   
认为该对象在集合中不存在，直接增加进去。如果在该位置有一个对象存在的话，接着将准备增加到集合中的对象与该位置上的对象进行 equals 方法比较，如果该 equals 方法返回 false,那么集合认为  
集合中不存在该对象，在进行一次散列，将该对象放到散列后计算出的新地址里。如果 equals 方法返回 true，那么集合认为集合中已经存在该对象了，不会再将该对象增加到集合中了。
5. 在哈希表中判断两个元素是否重复要使用到 hashCode()和 equals()。hashCode决定数据在表中的存储位置，而equals判断是否存在相同数据。
6. Y=K(X) ：K 是函数，X 是哈希码，Y 是地址

## TreeSet 的原理和使用（Comparable 和 comparator）


1. TreeSet 集合，元素不允许重复且有序(自然顺序)
2. TreeSet 采用树结构存储数据，存入元素时需要和树中元素进行对比，需要指定比较策略。
3. 可以通过 Comparable(外部比较器)和 Comparator(内部比较器)来指定比较策略，实现了 Comparable 的系统类可以顺利存入 TreeSet。自定义类可以实现 Comparable 接口来指定比较策略。
4. 可创建 Comparator 接口实现类来指定比较策略，并通过 TreeSet 构造方法参数传入。这种方式尤其对系统类非常适用。



## 集合和数组的比较（为什么引入集合）

- 数组不是面向对象的，存在明显的缺陷，集合完全弥补了数组的一些缺点，比数组更灵活更实用，可大大提高软件的开发效率而且不同的集合框架类可适用于不同场合。具体如下：

1. 数组的效率高于集合类.
2. 数组能存放基本数据类型和对象，而集合类中只能放对象。
3. 数组容量固定且无法动态改变，集合类容量动态改变。
4. 数组无法判断其中实际存有多少元素，length 只告诉了 array 的容量。
5. 集合有多种实现方式和不同的适用场合，而不像数组仅采用顺序表方式。
6. 集合以类的形式存在，具有封装、继承、多态等类的特性，通过简单的方法和属性调用即可实现各种复杂操作，大大提高软件的开发效率。



## Collection 和 Collections 的区别]

1. Collection 是 Java 提供的集合接口，存储一组不唯一，无序的对象。它有两个子接口 List 和 Set。 
2. Java 中还有一个 Collections 类，专门用来操作集合类 ，它提供一系列静态方法实现对各种集合的搜索、排序、线程安全化等操作。

## Java 的 HashMap 和 Hashtable 有什么区别 HashSet 和HashMap 有什么区别？使用这些结构保存的数需要重载的方法是哪些？

- HashMap 与 Hashtable 实现原理相同，功能相同，底层都是哈希表结构，查询速度快，在很多情况下可以互用
- 两者的主要区别如下
1. Hashtable 是早期 JDK 提供的接口，HashMap 是新版 JDK 提供的接口
2. Hashtable 继承 Dictionary 类，HashMap 实现 Map 接口
3. Hashtable 线程安全，HashMap 线程非安全
4. Hashtable 不允许 null 值，HashMap 允许 null 值
- HashSet 与 HashMap 的区别
1. HashSet底层是采用 HashMap 实现的。HashSet 的实现比较简单，HashSet 的绝大部分方法都是通过调用 HashMap 的方法来实现的，因此HashSet 和 HashMap 两个集合在实现本质上是相同的。
2. HashMap 的 key 就是放进 HashSet 中对象，value 是 Object 类型的。
3. 当调用 HashSet 的 add 方法时，实际上是向 HashMap 中增加了一行(key-value 对)，该行的 key 就是向 HashSet 增加的那个对象，该行的value 就是一个 Object 类型的常量。

## 列出 Java 中的集合类层次结构？

- Java中集合主要分为两种：Collection 和 Map。Collection 是 List 和 Set 接口的父接口；ArrayList 和 LinkedList 是 List 的实现类；HashSet 和 TreeSet 是 Set 的实现类；LinkedHashSet是  
 HashSet 的子类。HashMap 和 TreeMap 是 Map 的实现类；LinkedHashMap 是 HashMap 的子类。

## List，Set，Map 各有什么特点

- List 接口存储一组不唯一，有序（插入顺序）的对象。
- Set 接口存储一组唯一，无序的对象。
- Map 接口存储一组键值对象，提供 key 到 value 的映射。key 无序，唯一。value 不要求有序，允许重复。（如果只使用 key 存储，而不使用 value，那就是 Set）。


## Map 的实现类中，哪些是有序的，哪些是无序的，有序的是如何保证其有序性，你觉得哪个有序性性能更高，你有没有更好或者更高效的实现方式？

1. Map 的实现类有 HashMap,LinkedHashMap,TreeMap
2. HashMap 是有无序的，LinkedHashMap 和 TreeMap 都是有序的（LinkedHashMap记录了添加数据的顺序；TreeMap默认是自然升序）
3. LinkedHashMap 底层存储结构是哈希表+链表，链表记录了添加数据的顺序
4. TreeMap 底层存储结构是二叉树，二叉树的中序遍历保证了数据的有序性
5. LinkedHashMap 有序性能比较高，因为底层数据存储结构采用的哈希表

##  TreeMap 和 TreeSet 在排序时如何比较元素？Collections工具类中的 sort（）方法如何比较元素？

TreeSet 要求存放的对象所属的类必须实现 Comparable 接口，该接口提供了比较元素的 compareTo()方法，当插入元素时会 回调该方法比较元素的大小。TreeMap 要求存放的键值对映射的键必须实现  
Comparable接口从而根据键对元素进行排序。Collections 工具类的 sort 方法有两种重载的形式，第一种要求传入的待排序容器中存放的对象比较实现Comparable 接口以实现元素的比较；第二种不强制  
性的要求容器中的元素必须可比较，但是要求传入第二个参数，参数是 Comparator 接口的子类型（需要重写 compare 方法实现元素的比较），相当于一个临时定义的排序规则，其实就是是通过接口注入比  
较元素大小的算法，也是对回调模式的应用。



## List 里面如何剔除相同的对象？请简单用代码实现一种方法


```java
public class Test {
	public static void main(String[] args) {
	List<String> li1 = new ArrayList<String>();
	li1.add("8");
	li1.add("8");
	li1.add("9");
	li1.add("9");
	li1.add("0");
	System.out.println(li1);
	//方法:将List中数据取出来来存到Set中
	HashSet<String> set = new HashSet<String>(); 
	for(int i=0;i<li1.size();i++){
		set.add(li1.get(i));
		}
	System.out.println(set);
	}

}



```

## Java.util.Map 的实现类有

1. HashMap
2. Hashtable
3. LinkedHashMap
4. TreeMap

## List、Set、Map 是否继承自 Collection 接口？

- List、Set 的父接口是 Collection，Map 不是其子接口，而是与Collection 接口是平行关系，互不包含。


- Map 是键值对映射容器，与 List 和 Set 有明显的区别，而 Set 存储的零散的元素且不允许有重复元素（数学中的集合也是如此），List 是线性结构的容器，适用于按数值索引访问元素的情形。



## 说出 ArrayList、Vector、LinkedList 的存储性能和特性？

- ArrayList 和 Vector 都是使用数组方式存储数据，此数组元素数大于实际存储的数据以便增加和插入元素，它们都允许直接按序号索引元素，但是插入元素要涉及数组元素移动等内存操作，所以索引数据  
快而插入数据慢，Vector由于使用了synchronized 方法（线程安全），通常性能上较ArrayList差，而 LinkedList 使用双向链表实现存储（将内存中零散的内存单元通过附加的引用关联起来，形成一个可  
以按序号索引的线性结构，这种链式存储方式与数组的连续存储方式相比，其实对内存的利用率更高），按序号索引数据需要进行前向或后向遍历，但是插入数据时只需要记录本项的前后项即可，所以插入  
速度较快。Vector 属于遗留容器（早期的 JDK 中使用的容器，除此之外 Hashtable、Dictionary、BitSet、Stack、Properties 都是遗留容器），现在已经不推荐使用，但是由于 ArrayList 和 LinkedListed  
都是非线程安全的，如果需要多个线程操作同一个容器，那么可以通过工具类Collections 中的 synchronizedList 方法将其转换成线程安全的容器后再使用（这其实是装潢模式最好的例子，将已有对象传入  
另一个类的构造器中创建新的对象来增加新功能）。补充：遗留容器中的 Properties 类和 Stack 类在设计上有严重的问题，Properties 是一个键和值都是字符串的特殊的键值对映射，在设计上应该是
关联一个 Hashtable 并将其两个泛型参数设置为 String 类型，但是 Java API中的 Properties 直接继承了 Hashtable，这很明显是对继承的滥用。这里复用代码的方式应该是 HAS-A 关系而不是 IS-A 关系，  
另一方面容器都属于工具类，继承工具类本身就是一个错误的做法，使用工具类最好的方式是HAS-A 关系（关联）或 USE-A 关系（依赖） 。同理，Stack 类继承 Vector也是不正确的。


## List、Map、Set 三个接口，存取元素时，各有什么特点？
List 以特定索引来存取元素，可有重复元素。Set 不能存放重复元素（用对象的 equals()方法来区分元素是否重复） 。Map 保存键值对（key-value pair）映射，映射关系可以是一对一或多对一。
Set 和 Map 容器都有基于哈希存储和排序树（红黑树）的两种实现版本，基于哈希存储的版本理论存取时间复杂度为 O(1)，而基于排序树版本的实现在插入或删除元素时会按照元素或元素的键（key）  
构成排序树从而达到排序和去重的效果。


## TreeMap 和 TreeSet 在排序时如何比较元素？Collections工具类中的 sort()方法如何比较元素？

- TreeSet 要求存放的对象所属的类必须实现 Comparable 接口，该接口提供了比较元素的 compareTo()方法，当插入元素时会回调该方法比较元素的大小。
- TreeMap 要求存放的键值对映射的键必须实现 Comparable 接口从而根据键对元素进行排序。
- Collections 工具类的 sort 方法有两种重载的形式，第一种要求传入的待排序容器中存放的对象比较实现 Comparable 接口以实现元素的比较；第二种不强制性的要求容器中的元素必须可比较，但是  
要求传入第二个参数，参数是 Comparator 接口的子类型（需要重写 compare 方法实现元素的比较），相当于一个临时定义的排序规则，其实就是是通过接口注入比较元素大小的算法，也是对回调模式的应用。




















