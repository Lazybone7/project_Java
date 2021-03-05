#   一、Java集合框架概述

​	一方面，面向对象语言对事物的体现都是以对象的形式，为了方便对多个对象的操作，就要对对象进行存储。另一方面，使用Array存储对象方面具有一些弊端，而Java集合就像一个容器，可以动态地把多个对象的应用放入容器中

Java集合简称Java容器

说明：此时的存储，主要指的是内存层面上的存储，不涉及到持久化的存储（.text,.jpg,.avi）;

**数组在存储多个数据方面的特点：**

1.  ​	一旦初始化后，其长度就确定了
2.  ​	一旦定义好，其元素的类型也就确定了。我们也就只能操作指定类型的数据了。比如String[] arr;int[] arr1;Object[] arr2

**数组在存储多个数据方面的缺点：**

1.  一旦初始化以后，其长度就不可修改
2.  数组中提供的方法非常有限，对于添加、删除、插入数据等操作，非常不便。同时效率不高
3.  获取数组中实际元素的个数的需求，数组没有现成的属性或方法可用
4.  数组存储数据的特点：有序、可重复。对于无序、不可重复的需求不能满足

java集合可分为Collection和Map两种体系

​	**Collection接口**：单列集合，定义了存取一组**对象**的方法的集合

​		List接口：元素有序，可重复的数据 ---“动态”数组

​					--ArrayList、LinkedList、Vector

​		Set接口：元素无序，不可重复的数据 

​					-- HashSet、LinkedHashSet、TreeSet

​	**Map接口**：双列数据，保存具有映射关系“key-value对”的集合。存储一对的数据

​				--- HashMap、LinkedHashMap、TreeMap、Hashtable、Properties

## Collection接口继承树

![image-20210305103810314](E:\JAVA\JavaSE\Java高级部分\Java集合\note\note.assets\image-20210305103810314.png)

## Map接口继承树

![image-20210305103854412](E:\JAVA\JavaSE\Java高级部分\Java集合\note\note.assets\image-20210305103854412.png)

#  二、Collection接口中的API的使用

**说明**：向Collection接口的实现类的对象中添加数据obj时，要求obj所在类要重写equals()

add(Object e)：将元素e添加到集合coll中

size(): 获取添加元素的个数

addAll(Collection coll1): 将coll1添加到当前集合中

clear():清空集合元素

isEmpty(): 判断当前集合是否为空

contains(Object obj): 判断当前集合中是否包含obj。在判断时会调用obj对象所在类的equals方法

containsAll(Collection coll1): 判断形参coll1中的所有元素**是否都存在于**当前集合中。

remove(Object obj): 从当前集合中移除coll1中所有的元素

removeAll(Collection coll1): 差集： 从当前集合中移除coll1所有的元素

retainAll(Colletcion coll1): 获取两个集合的交集，并返回给当前集合

equals(Object obj): 判断当前集合和形参集合的元素是否都相同，是否按顺序要根据判断当前集合的类型

hashCode():返回当前对象的哈希值

toArray(): 集合——> 数组

asList(): 数组——>集合 调用Arrays类的静态方法

iterator(): 返回Iterator接口的实例，用于遍历集合元素

##  Iterator迭代器接口

​	Iterator对象成为迭代器(设计模式的一种)，主要用于遍历Collection集合中的元素

​	GOF给迭代器模式的定义为：提供一种方法访问一个容器对象中各个元素，而又不需暴露该对象的内部细节。迭代器模式就是为容器而生。

​	Iterator仅用于遍历集合

​	集合对象每次调用iterator()方法都得到一个全新的迭代器对象，默认游标都在集合的第一个元素之前

语法：

```java
Iterator iterator = coll1.iterator();

while(iterator.hasNext()){
  //next():①指针下移 ②将下移以后集合位置上的元素返回
	System.out.println(iterator.next());
}
```

