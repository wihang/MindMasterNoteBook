# JAVA-中级-集合框架

[toc]

## ArrayList

集合框架 与数组的区别

 示例 **1** : 

### 使用数组的局限性

如果要存放多个对象，可以使用数组，但是数组有局限性
比如 声明长度是10的数组
不用的数组就浪费了
超过10的个数，又放不下

- [TestCollection.java](https://how2j.cn/k/collection/collection-arraylist/363.html#nowhere)

  - ```java
    package collection;
     
    import charactor.Hero;
     
    public class TestCollection {
        public static void main(String[] args) {
            //数组的局限性
            Hero heros[] = new Hero[10];
            //声明长度是10的数组
            //不用的数组就浪费了
            //超过10的个数，又放不下
            heros[0] = new Hero("盖伦");
                    //放不下要报错
            heros[20] = new Hero("提莫");
             
        }
         
    }
    ```

  - 

- [重写了toString的Hero](https://how2j.cn/k/collection/collection-arraylist/363.html#nowhere)

  - ```java
    package charactor;
     
    public class Hero {
        public String name;
        public float hp;
     
        public int damage;
     
        public Hero() {
     
        }
     
        // 增加一个初始化name的构造方法
        public Hero(String name) {
     
            this.name = name;
        }
     
        // 重写toString方法
        public String toString() {
            return name;
        }
     
    }
    ```

 示例 **2** : 

### ArrayList存放对象

[**顶**](https://how2j.cn/k/collection/collection-arraylist/363.html#)[**折**](https://how2j.cn/k/collection/collection-arraylist/363.html#nowhere)

为了解决数组的局限性，引入容器类的概念。 最常见的容器类就是
ArrayList
[容器的容量](https://how2j.cn/k/number-string/number-string-stringbuilder/328.html#step724)"capacity"会随着对象的增加，自动增长
只需要不断往容器里增加英雄即可，不用担心会出现数组的边界问题。

代码比较复制代码

```java
package collection;
 
import java.util.ArrayList;
 
import charactor.Hero;
 
public class TestCollection {
    @SuppressWarnings("rawtypes")
    public static void main(String[] args) {
        //容器类ArrayList，用于存放对象
        ArrayList heros = new ArrayList();
        heros.add( new Hero("盖伦"));
        System.out.println(heros.size());
         
        //容器的容量"capacity"会随着对象的增加，自动增长
        //只需要不断往容器里增加英雄即可，不用担心会出现数组的边界问题。
        heros.add( new Hero("提莫"));
        System.out.println(heros.size());
         
    }
     
}
```



## 集合框架 常用的方法

|          |                              |
| -------- | ---------------------------- |
| add      | 增加                         |
| contains | 判断是否存在                 |
| get      | 获取指定位置的对象           |
| indexOf  | 获取对象所处的位置           |
| remove   | 删除                         |
| set      | 替换                         |
| size     | 获取大小                     |
| toArray  | 转换为数组                   |
| addAll   | 把另一个容器所有对象都加进来 |
| clear    | 清空                         |

 步骤 **1** : 

### 增加

**add** 有两种用法
第一种是直接add对象，把对象加在最后面

 

heros.add(new Hero("hero " + i));

 


第二种是在指定位置加对象

 

heros.add(3, specialHero);

 

![增加](https://stepimagewm.how2j.cn/2453.png)

- [TestCollection.java](https://how2j.cn/k/collection/collection-arraylist-method/685.html#nowhere)

  - ```java
    package collection;
     
    import java.util.ArrayList;
     
    import charactor.Hero;
     
    public class TestCollection {
        public static void main(String[] args) {
            ArrayList heros = new ArrayList();
     
            // 把5个对象加入到ArrayList中
            for (int i = 0; i < 5; i++) {
                heros.add(new Hero("hero " + i));
            }
            System.out.println(heros);
     
            // 在指定位置增加对象
            Hero specialHero = new Hero("special hero");
            heros.add(3, specialHero);
     
            System.out.println(heros.toString());
     
        }
     
    }
    ```

  - 

- [重写了toString的Hero](https://how2j.cn/k/collection/collection-arraylist-method/685.html#nowhere)

  - ```java
    package charactor;
      
    public class Hero {
        public String name;
        public float hp;
      
        public int damage;
      
        public Hero() {
      
        }
      
        // 增加一个初始化name的构造方法
        public Hero(String name) {
      
            this.name = name;
        }
      
        // 重写toString方法
        public String toString() {
            return name;
        }
      
    }
    ```

 步骤 **2** : 

### 判断是否存在

[**顶**](https://how2j.cn/k/collection/collection-arraylist-method/685.html#)[**折**](https://how2j.cn/k/collection/collection-arraylist-method/685.html#nowhere)

通过方法**contains** 判断一个对象是否在容器中
判断标准： 是否是同一个对象，而不是name是否相同

![判断是否存在](https://stepimagewm.how2j.cn/2454.png)

代码比较复制代码

```java
package collection;
 
import java.util.ArrayList;
 
import charactor.Hero;
 
public class TestCollection {
    public static void main(String[] args) {
        ArrayList heros = new ArrayList();
 
        // 初始化5个对象
        for (int i = 0; i < 5; i++) {
            heros.add(new Hero("hero " + i));
        }
        Hero specialHero = new Hero("special hero");
        heros.add(specialHero);
 
        System.out.println(heros);
        // 判断一个对象是否在容器中
        // 判断标准： 是否是同一个对象，而不是name是否相同
        System.out.print("虽然一个新的对象名字也叫 hero 1，但是contains的返回是:");
        System.out.println(heros.contains(new Hero("hero 1")));
        System.out.print("而对specialHero的判断，contains的返回是:");
        System.out.println(heros.contains(specialHero));
    }
 
}
```



 步骤 **3** : 

### 获取指定位置的对象

[**顶**](https://how2j.cn/k/collection/collection-arraylist-method/685.html#)[**折**](https://how2j.cn/k/collection/collection-arraylist-method/685.html#nowhere)

通过get获取指定位置的对象，如果输入的下标越界，一样会报错

![获取指定位置的对象](https://stepimagewm.how2j.cn/2455.png)

代码比较复制代码

```java
package collection;
 
import java.util.ArrayList;
 
import charactor.Hero;
 
public class TestCollection {
    public static void main(String[] args) {
        ArrayList heros = new ArrayList();
 
        // 初始化5个对象
        for (int i = 0; i < 5; i++) {
            heros.add(new Hero("hero " + i));
        }
        Hero specialHero = new Hero("special hero");
        heros.add(specialHero);
         
        //获取指定位置的对象
        System.out.println(heros.get(5));
        //如果超出了范围，依然会报错
        System.out.println(heros.get(6));
 
    }
 
}
```



 步骤 **4** : 

获取对象所处的位置

[**顶**](https://how2j.cn/k/collection/collection-arraylist-method/685.html#)[**折**](https://how2j.cn/k/collection/collection-arraylist-method/685.html#nowhere)

**indexOf**用于判断一个对象在ArrayList中所处的位置
与[contains](https://how2j.cn/k/collection/collection-arraylist-method/685.html#step2454)一样，判断标准是对象是否相同，而非对象的name值是否相等

![获取对象所处的位置](https://stepimagewm.how2j.cn/2456.png)

代码比较复制代码

```java
package collection;
 
import java.util.ArrayList;
 
import charactor.Hero;
 
public class TestCollection {
    public static void main(String[] args) {
        ArrayList heros = new ArrayList();
 
        // 初始化5个对象
        for (int i = 0; i < 5; i++) {
            heros.add(new Hero("hero " + i));
        }
        Hero specialHero = new Hero("special hero");
        heros.add(specialHero);
 
        System.out.println(heros);
        System.out.println("specialHero所处的位置:"+heros.indexOf(specialHero));
        System.out.println("新的英雄，但是名字是\"hero 1\"所处的位置:"+heros.indexOf(new Hero("hero 1")));
 
    }
}
```





 步骤 **5** : 

### 删除

[**顶**](https://how2j.cn/k/collection/collection-arraylist-method/685.html#)[**折**](https://how2j.cn/k/collection/collection-arraylist-method/685.html#nowhere)

**remove**用于把对象从ArrayList中删除
remove可以根据下标删除ArrayList的元素

 

heros.remove(2);

 


也可以根据对象删除

 

heros.remove(specialHero);

 

![删除](https://stepimagewm.how2j.cn/2457.png)

代码比较复制代码

```java
package collection;
 
import java.util.ArrayList;
 
import charactor.Hero;
 
public class TestCollection {
    public static void main(String[] args) {
        ArrayList heros = new ArrayList();
 
        // 初始化5个对象
        for (int i = 0; i < 5; i++) {
            heros.add(new Hero("hero " + i));
        }
        Hero specialHero = new Hero("special hero");
        heros.add(specialHero);
         
        System.out.println(heros);
        heros.remove(2);
        System.out.println("删除下标是2的对象");
        System.out.println(heros);
        System.out.println("删除special hero");
        heros.remove(specialHero);
        System.out.println(heros);
         
    }
}
```





 步骤 **6** : 

### 替换

[**顶**](https://how2j.cn/k/collection/collection-arraylist-method/685.html#)[**折**](https://how2j.cn/k/collection/collection-arraylist-method/685.html#nowhere)

**set**用于替换指定位置的元素

![替换](https://stepimagewm.how2j.cn/2458.png)

代码比较复制代码

```java
package collection;
 
import java.util.ArrayList;
 
import charactor.Hero;
 
public class TestCollection {
    public static void main(String[] args) {
        ArrayList heros = new ArrayList();
 
        // 初始化5个对象
        for (int i = 0; i < 5; i++) {
            heros.add(new Hero("hero " + i));
        }
        Hero specialHero = new Hero("special hero");
        heros.add(specialHero);
         
        System.out.println(heros);
        System.out.println("把下标是5的元素，替换为\"hero 5\"");
        heros.set(5, new Hero("hero 5"));
        System.out.println(heros);
    }
}
```



 步骤 **7** : 

### 获取大小

[**顶**](https://how2j.cn/k/collection/collection-arraylist-method/685.html#)[**折**](https://how2j.cn/k/collection/collection-arraylist-method/685.html#nowhere)

**size** 用于获取ArrayList的大小

![获取大小](https://stepimagewm.how2j.cn/2459.png)

代码比较复制代码

```java
package collection;
 
import java.util.ArrayList;
 
import charactor.Hero;
 
public class TestCollection {
    public static void main(String[] args) {
        ArrayList heros = new ArrayList();
 
        // 初始化5个对象
        for (int i = 0; i < 5; i++) {
            heros.add(new Hero("hero " + i));
        }
        Hero specialHero = new Hero("special hero");
        heros.add(specialHero);
        System.out.println(heros);
        System.out.println("获取ArrayList的大小：");
        System.out.println(heros.size());
    }
}
```



 步骤 **8** : 

### 转换为数组

[**顶**](https://how2j.cn/k/collection/collection-arraylist-method/685.html#)[**折**](https://how2j.cn/k/collection/collection-arraylist-method/685.html#nowhere)

**toArray**可以把一个ArrayList对象转换为数组。
需要注意的是，如果要转换为一个Hero数组，那么需要传递一个Hero数组类型的对象给toArray()，这样toArray方法才知道，你希望转换为哪种类型的数组，否则只能转换为Object数组

![转换为数组](https://stepimagewm.how2j.cn/2460.png)

代码比较复制代码

```java
package collection;
 
import java.util.ArrayList;
 
import charactor.Hero;
 
public class TestCollection {
    public static void main(String[] args) {
        ArrayList heros = new ArrayList();
 
        // 初始化5个对象
        for (int i = 0; i < 5; i++) {
            heros.add(new Hero("hero " + i));
        }
        Hero specialHero = new Hero("special hero");
        heros.add(specialHero);
        System.out.println(heros);
        Hero hs[] = (Hero[])heros.toArray(new Hero[]{});
        System.out.println("数组:" +hs);
 
    }
}
```





 步骤 **9** : 

### 把另一个容器所有对象都加进来

[**顶**](https://how2j.cn/k/collection/collection-arraylist-method/685.html#)[**折**](https://how2j.cn/k/collection/collection-arraylist-method/685.html#nowhere)

**addAll** 把另一个容器所有对象都加进来

![把另一个容器所有对象都加进来](https://stepimagewm.how2j.cn/2461.png)

代码比较复制代码

```java
package collection;
 
import java.util.ArrayList;
 
import charactor.Hero;
 
public class TestCollection {
    public static void main(String[] args) {
        ArrayList heros = new ArrayList();
 
        // 初始化5个对象
        for (int i = 0; i < 5; i++) {
            heros.add(new Hero("hero " + i));
        }
 
        System.out.println("ArrayList heros:\t" + heros);
          
        //把另一个容器里所有的元素，都加入到该容器里来
        ArrayList anotherHeros = new ArrayList();
        anotherHeros.add(new Hero("hero a"));
        anotherHeros.add(new Hero("hero b"));
        anotherHeros.add(new Hero("hero c"));
        System.out.println("anotherHeros heros:\t" + anotherHeros);
        heros.addAll(anotherHeros);
        System.out.println("把另一个ArrayList的元素都加入到当前ArrayList:");
        System.out.println("ArrayList heros:\t" + heros);
         
    }
}
```





 步骤 **10** : 

### 清空

[**顶**](https://how2j.cn/k/collection/collection-arraylist-method/685.html#)[**折**](https://how2j.cn/k/collection/collection-arraylist-method/685.html#nowhere)

**clear** 清空一个ArrayList

![清空](https://stepimagewm.how2j.cn/2462.png)

代码比较复制代码

```java
package collection;
 
import java.util.ArrayList;
 
import charactor.Hero;
 
public class TestCollection {
    public static void main(String[] args) {
        ArrayList heros = new ArrayList();
 
        // 初始化5个对象
        for (int i = 0; i < 5; i++) {
            heros.add(new Hero("hero " + i));
        }
 
        System.out.println("ArrayList heros:\t" + heros);
        System.out.println("使用clear清空");
        heros.clear();
        System.out.println("ArrayList heros:\t" + heros);
          
    }
}
```



#### ==笔记==

```java
package com.xiao.zhongji.collecion;

import java.util.ArrayList;

public class TestCollection02 {

    public static void main(String[] args) {

        ArrayList heros = new ArrayList();
        for (int i = 0; i <= 5; i++) {
            heros.add(new Hero("hero" + i));
        }
        System.out.println(heros);

        //在指定的位置增加对象
        Hero specialHero = new Hero("special hero");
        heros.add(3, specialHero);
        System.out.println(heros);

        // 判断一个对象是否在容器中
        // 判断标准： 是否是同一个对象，而不是name是否相同
        System.out.print("虽然一个新的对象名字也叫 hero 1，但是contains的返回是:");
        System.out.println(heros.contains(new Hero("hero 1")));
        System.out.print("而对specialHero的判断，contains的返回是:");
        System.out.println(heros.contains(specialHero));

        System.out.println(heros.get(5));   //获取指定位置的对象
        //获取该对象对应的位置
        System.out.println(heros);
        System.out.println(heros.indexOf(specialHero));
        System.out.println(heros.indexOf(new Hero("hero 1")));
        //删除对象
        System.out.println(heros.remove(specialHero));
        System.out.println(heros.contains(specialHero));
        //替换
        System.out.println(heros.set(5, new Hero("hero 5")));
        System.out.println(heros);

        //获取大小
        System.out.println(heros.size());

        //转换为数组
        Hero[] hs = (Hero[]) heros.toArray(new Hero[]{});
        System.out.println("数组" + hs);

        //把另一个容器所有的对象加起来
        ArrayList anotherHero = new ArrayList();
        anotherHero.add(new Hero("anotherHero 01"));
        anotherHero.add(new Hero("anotherHero 02"));
        anotherHero.add(new Hero("anotherHero 03"));

        System.out.println("anotherHero" + anotherHero);
        heros.addAll(anotherHero);
        System.out.println(heros);

        //清空
        System.out.println(heros);
        System.out.println("使用clear清空");
        heros.clear();
        System.out.println("清空后的数据: " + heros);
        

    }
}

```





 步骤 **11** : 

### 练习-判断是否相同 

如果就是要判断集合里是否存在一个 name等于 "hero 1"的对象，应该怎么做？

![练习-判断是否相同](https://stepimagewm.how2j.cn/2463.png)



 步骤 **12** : 

### 答案-判断是否相同 

查看答案 在查看答案前，尽量先自己完成，碰到问题再来查看答案，收获会更多

 步骤 **13** : 

### 练习-MyStringBuffer 

做一个一样的[MyStringBuffer](https://how2j.cn/k/number-string/number-string-mystringbuilder/331.html)练习，但是不使用字符数组，而是使用ArrayList来实现





集合框架 List接口

集合框架 泛型Generic

集合框架 遍历



## List接口

步骤 **1** : 

### ArrayList和List

ArrayList实现了接口List
常见的写法会把引用声明为接口List类型
注意：是**java.util.List**,而**不是**java.awt.List

![ArrayList和List](https://stepimagewm.how2j.cn/808.png)

```java
package collection;
  
import java.util.ArrayList;
import java.util.List;
 
import charactor.Hero;
  
public class TestCollection {
 
    public static void main(String[] args) {
        //ArrayList实现了接口List
         
        //常见的写法会把引用声明为接口List类型
        //注意：是java.util.List,而不是java.awt.List
        //接口引用指向子类对象（多态）
         
        List heros = new ArrayList();
        heros.add( new Hero("盖伦"));
        System.out.println(heros.size());
         
    }
      
}
```

 步骤 **2** : 

### List接口的方法

因为ArrayList实现了List接口，所以List接口的方法ArrayList都实现了。
在[ArrayList 常用方法](https://how2j.cn/k/collection/collection-arraylist-method/685.html)章节有详细的讲解，在此不作赘述

## 泛型Generic

 步骤 **1** : 

### 泛型 Generic

不指定泛型的容器，可以存放任何类型的元素
指定了泛型的容器，只能存放指定类型的元素以及其子类

- [Item.java](https://how2j.cn/k/collection/collection-arraylist-generic/687.html#nowhere)

  - ```java
    package property;
     
    public class Item {
        String name;
        int price;
         
        public Item(){
             
        }
         
        //提供一个初始化name的构造方法
        public Item(String name){
            this.name = name;
        }
         
        public void effect(){
            System.out.println("物品使用后，可以有效果");
        }
         
    }
    ```

- [TestCollection.java](https://how2j.cn/k/collection/collection-arraylist-generic/687.html#nowhere)

  - ```java
    package collection;
       
    import java.util.ArrayList;
    import java.util.List;
      
    import property.Item;
    import charactor.APHero;
    import charactor.Hero;
       
    public class TestCollection {
      
        public static void main(String[] args) {
              
            //对于不使用泛型的容器，可以往里面放英雄，也可以往里面放物品
            List heros = new ArrayList();
              
            heros.add(new Hero("盖伦"));
              
            //本来用于存放英雄的容器，现在也可以存放物品了
            heros.add(new Item("冰杖"));
              
            //对象转型会出现问题
            Hero h1=  (Hero) heros.get(0);
            //尤其是在容器里放的对象太多的时候，就记不清楚哪个位置放的是哪种类型的对象了
            Hero h2=  (Hero) heros.get(1);
              
            //引入泛型Generic
            //声明容器的时候，就指定了这种容器，只能放Hero，放其他的就会出错
            List<Hero> genericheros = new ArrayList<Hero>();
            genericheros.add(new Hero("盖伦"));
            //如果不是Hero类型，根本就放不进去
            //genericheros.add(new Item("冰杖"));
              
            //除此之外，还能存放Hero的子类
            genericheros.add(new APHero());
             
            //并且在取出数据的时候，不需要再进行转型了，因为里面肯定是放的Hero或者其子类
            Hero h = genericheros.get(0);
             
        }
           
    }
    ```

  - 

 步骤 **2** : 

### 泛型的简写

[**顶**](https://how2j.cn/k/collection/collection-arraylist-generic/687.html#)[**折**](https://how2j.cn/k/collection/collection-arraylist-generic/687.html#nowhere)

[**纠**](https://how2j.cn/k/collection/collection-arraylist-generic/687.html#nowhere)[**问**](https://how2j.cn/k/collection/collection-arraylist-generic/687.html#nowhere)

为了不使编译器出现警告，需要前后都使用泛型，像这样：

 

List<Hero> genericheros = new ArrayList<Hero>();

 


不过JDK7提供了一个可以略微减少代码量的泛型简写方式

 

List<Hero> genericheros2 = new ArrayList<>();

 


后面的泛型可以用<>来代替，聊胜于无吧

代码比较复制代码

```java
package collection;
   
import java.util.ArrayList;
import java.util.List;
 
import charactor.Hero;
   
public class TestCollection {
  
    public static void main(String[] args) {
        List<Hero> genericheros = new ArrayList<Hero>();
        List<Hero> genericheros2 = new ArrayList<>();
      
    }
       
}
```



 步骤 **3** : 

### 泛型的系统学习

泛型的知识还包含 [支持泛型的类](https://how2j.cn/k/generic/generic-generic-class/374.html) [泛型转型](https://how2j.cn/k/generic/generic-casting/375.html) [通配符](https://how2j.cn/k/generic/generic-wildcard/376.html) 这些内容都在[泛型章节](https://how2j.cn/k/generic/generic-generic/373.html)详细展开



 步骤 **4** : 

### 练习-支持泛型的ArrayList 

借助泛型和前面学习的面向对象的知识，设计一个ArrayList，使得这个ArrayList里，又可以放Hero，又可以放Item,但是除了这两种对象，其他的对象都不能放

## 遍历

 步骤 **1** : 

### 用for循环遍历



通过前面的学习，知道了可以用size()和get()分别得到大小，和获取指定位置的元素，结合for循环就可以遍历出ArrayList的内容

![用for循环遍历](https://stepimagewm.how2j.cn/2469.png)

代码比较复制代码

```java
package collection;
 
import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;
 
import charactor.Hero;
 
public class TestCollection {
 
    public static void main(String[] args) {
        List<Hero> heros = new ArrayList<Hero>();
 
        // 放5个Hero进入容器
        for (int i = 0; i < 5; i++) {
            heros.add(new Hero("hero name " + i));
        }
 
        // 第一种遍历 for循环
        System.out.println("--------for 循环-------");
        for (int i = 0; i < heros.size(); i++) {
            Hero h = heros.get(i);
            System.out.println(h);
        }
 
    }
 
}
```



 步骤 **2** : 

### 迭代器遍历

使用迭代器Iterator遍历集合中的元素

![迭代器遍历](https://stepimagewm.how2j.cn/806.png)

代码比较复制代码

```java
package collection;
 
import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;
 
import charactor.Hero;
  
public class TestCollection {
 
    public static void main(String[] args) {
        List<Hero> heros = new ArrayList<Hero>();
         
        //放5个Hero进入容器
        for (int i = 0; i < 5; i++) {
            heros.add(new Hero("hero name " +i));
        }
         
        //第二种遍历，使用迭代器
        System.out.println("--------使用while的iterator-------");
        Iterator<Hero> it= heros.iterator();
        //从最开始的位置判断"下一个"位置是否有数据
        //如果有就通过next取出来，并且把指针向下移动
        //直到"下一个"位置没有数据
        while(it.hasNext()){
            Hero h = it.next();
            System.out.println(h);
        }
        //迭代器的for写法
        System.out.println("--------使用for的iterator-------");
        for (Iterator<Hero> iterator = heros.iterator(); iterator.hasNext();) {
            Hero hero = (Hero) iterator.next();
            System.out.println(hero);
        }
         
    }
      
}
```



 步骤 **3** : 

### 用增强型for循环

使用增强型for循环可以非常方便的遍历ArrayList中的元素，这是很多开发人员的首选。

不过增强型for循环也有不足：
无法用来进行ArrayList的初始化
无法得知当前是第几个元素了，当需要只打印单数元素的时候，就做不到了。 必须再自定下标变量。

![用增强型for循环](https://stepimagewm.how2j.cn/2470.png)

代码比较复制代码

```java
package collection;
 
import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;
 
import charactor.Hero;
 
public class TestCollection {
 
    public static void main(String[] args) {
        List<Hero> heros = new ArrayList<Hero>();
 
        // 放5个Hero进入容器
        for (int i = 0; i < 5; i++) {
            heros.add(new Hero("hero name " + i));
        }
 
        // 第三种，增强型for循环
        System.out.println("--------增强型for循环-------");
        for (Hero h : heros) {
            System.out.println(h);
        }
 
    }
 
}
```



 步骤 **4** : 

练习-删除ArrayList中的数据 

  [**顶**](https://how2j.cn/k/collection/collection-arraylist-iterator/688.html#)[**折**](https://how2j.cn/k/collection/collection-arraylist-iterator/688.html#nowhere)

[**纠**](https://how2j.cn/k/collection/collection-arraylist-iterator/688.html#nowhere)[**问**](https://how2j.cn/k/collection/collection-arraylist-iterator/688.html#nowhere)

 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/collection/collection-arraylist-iterator/688.html#nowhere)

首先初始化一个Hero集合，里面放100个Hero对象，名称分别是从
hero 0
hero 1
hero 2
...
hero 99.

通过遍历的手段，删除掉名字编号是8的倍数的对象

## LinkedList

序列分先进先出FIFO,先进后出FILO
FIFO在Java中又叫Queue 队列
FILO在Java中又叫Stack 栈



 示例 **1** : 

### LinkedList 与 List接口

与[ArrayList](https://how2j.cn/k/collection/collection-arraylist-method/685.html)一样，LinkedList也实现了List接口，诸如add,remove,contains等等方法。 详细使用，请参考 [ArrayList 常用方法](https://how2j.cn/k/collection/collection-arraylist-method/685.html)，在此不作赘述。

接下来要讲的是LinkedList的一些特别的地方



 示例 **2** : 

### 双向链表 - Deque

除了实现了List接口外，LinkedList还实现了**双向链表结构**Deque，可以很方便的在头尾插入删除数据

什么是链表结构: 与数组结构相比较，数组结构，就好像是电影院，每个位置都有标示，每个位置之间的间隔都是一样的。 而链表就相当于佛珠，每个珠子，只连接前一个和后一个，不用关心除此之外的其他佛珠在哪里。

![双向链表 - Deque](https://stepimagewm.how2j.cn/809.png)

代码比较复制代码

```java
package collection;
 
import java.util.LinkedList;
 
import charactor.Hero;
 
public class TestCollection {
 
    public static void main(String[] args) {
         
        //LinkedList是一个双向链表结构的list
        LinkedList<Hero> ll =new LinkedList<Hero>();
         
        //所以可以很方便的在头部和尾部插入数据
        //在最后插入新的英雄
        ll.addLast(new Hero("hero1"));
        ll.addLast(new Hero("hero2"));
        ll.addLast(new Hero("hero3"));
        System.out.println(ll);
         
        //在最前面插入新的英雄
        ll.addFirst(new Hero("heroX"));
        System.out.println(ll);
         
        //查看最前面的英雄
        System.out.println(ll.getFirst());
        //查看最后面的英雄
        System.out.println(ll.getLast());
         
        //查看不会导致英雄被删除
        System.out.println(ll);
        //取出最前面的英雄
        System.out.println(ll.removeFirst());
         
        //取出最后面的英雄
        System.out.println(ll.removeLast());
         
        //取出会导致英雄被删除
        System.out.println(ll);
         
    }
      
}
```





 示例 **3** : 

### 队列 - Queue

LinkedList 除了实现了List和Deque外，还实现了**Queue**接口(队列)。
Queue是先进先出队列 **FIFO**，常用方法：
**offer** 在最后添加元素
**poll** 取出第一个元素
**peek** 查看第一个元素

![队列 - Queue](https://stepimagewm.how2j.cn/810.png)

代码比较复制代码

```java
package collection;
  
import java.util.LinkedList;
import java.util.List;
import java.util.Queue;
  
import charactor.Hero;
  
public class TestCollection {
  
    public static void main(String[] args) {
        //和ArrayList一样，LinkedList也实现了List接口
        List ll =new LinkedList<Hero>();
          
        //所不同的是LinkedList还实现了Deque，进而又实现了Queue这个接口
        //Queue代表FIFO 先进先出的队列
        Queue<Hero> q= new LinkedList<Hero>();
          
        //加在队列的最后面
        System.out.print("初始化队列：\t");
        q.offer(new Hero("Hero1"));
        q.offer(new Hero("Hero2"));
        q.offer(new Hero("Hero3"));
        q.offer(new Hero("Hero4"));
          
        System.out.println(q);
        System.out.print("把第一个元素取poll()出来:\t");
        //取出第一个Hero，FIFO 先进先出
        Hero h = q.poll();
        System.out.println(h);
        System.out.print("取出第一个元素之后的队列:\t");
        System.out.println(q);
          
        //把第一个拿出来看一看，但是不取出来
        h=q.peek();
        System.out.print("查看peek()第一个元素:\t");
        System.out.println(h);
        System.out.print("查看并不会导致第一个元素被取出来:\t");
        System.out.println(q);
          
    }
       
}
```



 示例 **4** : 

### ArrayList 与 LinkedList的区别

[**顶**](https://how2j.cn/k/collection/collection-linkedlist/370.html#)[**折**](https://how2j.cn/k/collection/collection-linkedlist/370.html#nowhere)

[**纠**](https://how2j.cn/k/collection/collection-linkedlist/370.html#nowhere)[**问**](https://how2j.cn/k/collection/collection-linkedlist/370.html#nowhere)

ArrayList 与 LinkedList的区别是面试常常会问到的考题
具体区别，详见 [ArrayList 与 LinkedList的区别](https://how2j.cn/k/collection/collection-arraylist-vs-linkedlist/690.html)



 示例 **5** : 

### 练习-使用LinkedList实现Stack栈 

  [**顶**](https://how2j.cn/k/collection/collection-linkedlist/370.html#)[**折**](https://how2j.cn/k/collection/collection-linkedlist/370.html#nowhere)

[**纠**](https://how2j.cn/k/collection/collection-linkedlist/370.html#nowhere)[**问**](https://how2j.cn/k/collection/collection-linkedlist/370.html#nowhere)

 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/collection/collection-linkedlist/370.html#nowhere)

与**FIFO**(先入先出的)**队列**类似的一种数据结构是**FILO**先入后出**栈**Stack
根据接口Stack ：
实现类：MyStack

 

public class MyStack implements Stack

 


并向这个栈中，压入5个英雄，接着弹出5个英雄

再解释一下栈: 栈的结构，就像给弹夹添加子弹一样，先添加的子弹，就放在了最下面，**打手枪**的时候，只能从最上面取子弹。

![练习-使用LinkedList实现Stack栈](https://stepimagewm.how2j.cn/2475.png)

代码比较复制代码

```java
package collection;
 
import charactor.Hero;
 
public interface Stack {
 
    //把英雄推入到最后位置
    public void push(Hero h);
    //把最后一个英雄取出来
    public Hero pull();
    //查看最后一个英雄
    public Hero peek();
}
```

---

## 二叉树 (未看)

 示例 **1** : 

### 二叉树概念

[**顶**](https://how2j.cn/k/collection/collection-tree/476.html#)[**折**](https://how2j.cn/k/collection/collection-tree/476.html#nowhere)

[**纠**](https://how2j.cn/k/collection/collection-tree/476.html#nowhere)[**问**](https://how2j.cn/k/collection/collection-tree/476.html#nowhere)

二叉树由各种**节点**组成
二叉树特点：
每个节点都可以有**左子**节点，**右子**节点
每一个节点都有一个**值**

![二叉树概念](https://stepimagewm.how2j.cn/1008.png)

代码比较复制代码

```java
package collection;
 
public class Node {
    // 左子节点
    public Node leftNode;
    // 右子节点
    public Node rightNode;
    // 值
    public Object value;
}
```



 示例 **2** : 

### 二叉树排序-插入数据

假设通过二叉树对如下10个随机数进行排序
67,7,30,73,10,0,78,81,10,74
排序的第一个步骤是把数据插入到该二叉树中
插入基本逻辑是，**小、相同的放左边**，**大的放右边**
\1. 67 放在根节点
\2. 7 比 67小，放在67的左节点
\3. 30 比67 小，找到67的左节点7，30比7大，就放在7的右节点
\4. 73 比67大， 放在67的右节点
\5. 10 比 67小，找到67的左节点7，10比7大，找到7的右节点30，10比30小，放在30的左节点。
...
...
\9. 10比67小，找到67的左节点7，10比7大，找到7的右节点30，10比30小，找到30的左节点10，10和10一样大，放在左边

![二叉树排序-插入数据](https://stepimagewm.how2j.cn/1009.png)

代码比较复制代码

```java
package collection;
  
public class Node {
    // 左子节点
    public Node leftNode;
    // 右子节点
    public Node rightNode;
  
    // 值
    public Object value;
  
    // 插入 数据
    public void add(Object v) {
        // 如果当前节点没有值，就把数据放在当前节点上
        if (null == value)
            value = v;
  
        // 如果当前节点有值，就进行判断，新增的值与当前值的大小关系
        else {
            // 新增的值，比当前值小或者相同
             
            if ((Integer) v -((Integer)value) <= 0) {
                if (null == leftNode)
                    leftNode = new Node();
                leftNode.add(v);
            }
            // 新增的值，比当前值大
            else {
                if (null == rightNode)
                    rightNode = new Node();
                rightNode.add(v);
            }
  
        }
  
    }
  
    public static void main(String[] args) {
  
        int randoms[] = new int[] { 67, 7, 30, 73, 10, 0, 78, 81, 10, 74 };
  
        Node roots = new Node();
        for (int number : randoms) {
            roots.add(number);
        }
  
    }
}
```



 示例 **3** : 

### 二叉树排序-遍历

通过上一个步骤的插入行为，实际上，数据就已经排好序了。 接下来要做的是看，把**这些已经排好序的数据**，遍历成我们常用的List或者数组的形式

二叉树的遍历分左序，中序，右序
**左序**即： 中间的数遍历后放在**左边**
**中序**即： 中间的数遍历后放在**中间**
**右序**即： 中间的数遍历后放在**右边**
如图所见，我们希望遍历后的结果是从小到大的，所以应该采用**中序遍历**

![二叉树排序-遍历](https://stepimagewm.how2j.cn/1010.png)

代码比较复制代码

```java
package collection;
 
import java.util.ArrayList;
import java.util.List;
 
public class Node {
    // 左子节点
    public Node leftNode;
    // 右子节点
    public Node rightNode;
  
    // 值
    public Object value;
  
    // 插入 数据
    public void add(Object v) {
        // 如果当前节点没有值，就把数据放在当前节点上
        if (null == value)
            value = v;
  
        // 如果当前节点有值，就进行判断，新增的值与当前值的大小关系
        else {
            // 新增的值，比当前值小或者相同
             
            if ((Integer) v -((Integer)value) <= 0) {
                if (null == leftNode)
                    leftNode = new Node();
                leftNode.add(v);
            }
            // 新增的值，比当前值大
            else {
                if (null == rightNode)
                    rightNode = new Node();
                rightNode.add(v);
            }
  
        }
  
    }
  
 // 中序遍历所有的节点
    public List<Object> values() {
        List<Object> values = new ArrayList<>();
  
        // 左节点的遍历结果
        if (null != leftNode)
            values.addAll(leftNode.values());
  
        // 当前节点
        values.add(value);
  
        // 右节点的遍历结果
        if (null != rightNode)
  
            values.addAll(rightNode.values());
  
        return values;
    }
  
    public static void main(String[] args) {
  
        int randoms[] = new int[] { 67, 7, 30, 73, 10, 0, 78, 81, 10, 74 };
  
        Node roots = new Node();
        for (int number : randoms) {
            roots.add(number);
        }
  
        System.out.println(roots.values());
  
    }
}
```



 示例 **4** : 

### 练习-英雄二叉树 

 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/collection/collection-tree/476.html#nowhere)

根据上面的学习和理解，设计一个Hero二叉树，HeroNode.
可以向这个英雄二叉树插入不同的Hero对象，并且按照Hero的**血量倒排序**。

随机生成10个Hero对象，每个Hero对象都有不同的血量值，插入这个HeroNode后，把排序结果打印出来。

![练习-英雄二叉树](https://stepimagewm.how2j.cn/2511.png)



 示例 **5** : 

### 答案-英雄二叉树 

查看答案(消耗积分) 查看本答案会花费**4**个积分，您目前总共有**35**点积分。查看相同答案不会花费额外积分。 [积分增加办法](https://how2j.cn/frontscoreProducePage) 或者[一次性购买](https://how2j.cn/frontshopPage?product.id=14)JAVA 中级总计**0个答案** (总共需要0积分)

 示例 **6** : 

### 练习-比较冒泡法，选择法以及二叉树排序的性能区别 

创建4万个随机数，然后用分别用[冒泡法](https://how2j.cn/k/array/array-sort/282.html#step574)，[选择法](https://how2j.cn/k/array/array-sort/282.html#step573)，[二叉树](https://how2j.cn/k/collection/collection-tree/476.html)3种排序算法进行排序，比较哪种更快

## HashMap

 示例 **1** : 

### HashMap的键值对

HashMap储存数据的方式是—— 键值对

代码比较复制代码

```java
package collection;
   
import java.util.HashMap;
   
public class TestCollection {
    public static void main(String[] args) {
        HashMap<String,String> dictionary = new HashMap<>();
        dictionary.put("adc", "物理英雄");
        dictionary.put("apc", "魔法英雄");
        dictionary.put("t", "坦克");
         
        System.out.println(dictionary.get("t"));
    }
}
```



 示例 **2** : 

### 键不能重复，值可以重复

对于HashMap而言，key是唯一的，不可以重复的。
所以，以相同的key 把不同的value插入到 Map中会导致旧元素被覆盖，只留下最后插入的元素。
不过，同一个对象可以作为值插入到map中，只要对应的key不一样

代码比较复制代码

```java
package collection;
  
import java.util.HashMap;
  
import charactor.Hero;
  
public class TestCollection {
    public static void main(String[] args) {
        HashMap<String,Hero> heroMap = new HashMap<String,Hero>();
         
        heroMap.put("gareen", new Hero("gareen1"));
        System.out.println(heroMap);
         
        //key为gareen已经有value了，再以gareen作为key放入数据，会导致原英雄，被覆盖
        //不会增加新的元素到Map中
        heroMap.put("gareen", new Hero("gareen2"));
        System.out.println(heroMap);
         
        //清空map
        heroMap.clear();
        Hero gareen = new Hero("gareen");
         
        //同一个对象可以作为值插入到map中，只要对应的key不一样
        heroMap.put("hero1", gareen);
        heroMap.put("hero2", gareen);
         
        System.out.println(heroMap);
         
    }
}
```



 示例 **3** : 

### 练习-查找内容性能比较 

准备一个ArrayList其中存放3000000(三百万个)Hero对象，其名称是随机的,格式是hero-[4位随机数]
hero-3229
hero-6232
hero-9365
...

因为总数很大，所以几乎每种都有重复，把名字叫做 hero-5555的所有对象找出来
要求使用两种办法来寻找
\1. 不使用HashMap，直接使用for循环找出来，并统计花费的时间
\2. 借助HashMap，找出结果，并统计花费的时间



## HashSet

 示例 **1** : 

### 元素不能重复

Set中的元素，不能重复

代码比较复制代码

```java
package collection;
  
import java.util.HashSet;
  
public class TestCollection {
    public static void main(String[] args) {
         
        HashSet<String> names = new HashSet<String>();
         
        names.add("gareen");
         
        System.out.println(names);
         
        //第二次插入同样的数据，是插不进去的，容器中只会保留一个
        names.add("gareen");
        System.out.println(names);
    }
}
```



 示例 **2** : 

### 没有顺序

[**顶**](https://how2j.cn/k/collection/collection-hashset/364.html#)[**折**](https://how2j.cn/k/collection/collection-hashset/364.html#nowhere)

Set中的元素，没有顺序。
严格的说，是没有按照元素的插入顺序排列

HashSet的具体顺序，既不是按照插入顺序，也不是按照hashcode的顺序。关于hashcode有专门的章节讲解: [hashcode 原理](https://how2j.cn/k/collection/collection-hashcode/371.html)。

以下是**HashSet源代码**中的部分注释

 

/**

 \* It makes no guarantees as to the iteration order of the set; 

 \* in particular, it does not guarantee that the order will remain constant over time. 

*/

 



 

不保证Set的迭代顺序; 确切的说，在不同条件下，元素的顺序都有可能不一样

 



换句话说，同样是插入0-9到HashSet中， 在JVM的不同版本中，看到的顺序都是不一样的。 所以在开发的时候，不能依赖于某种**臆测的顺序**，这个顺序本身是**不稳定的**

![没有顺序](https://stepimagewm.how2j.cn/823.png)

```java
package collection;
 
import java.util.HashSet;
 
public class TestCollection {
    public static void main(String[] args) {
        HashSet<Integer> numbers = new HashSet<Integer>();
 
        numbers.add(9);
        numbers.add(5);
        numbers.add(1);
 
        // Set中的元素排列，不是按照插入顺序
        System.out.println(numbers);
 
    }
}
```



 示例 **3** : 

### 遍历

[**顶**](https://how2j.cn/k/collection/collection-hashset/364.html#)[**折**](https://how2j.cn/k/collection/collection-hashset/364.html#nowhere)

Set不提供get()来获取指定位置的元素
所以遍历需要用到迭代器，或者增强型for循环

代码比较复制代码

```java
package collection;
  
import java.util.HashSet;
import java.util.Iterator;
  
public class TestCollection {
    public static void main(String[] args) {
        HashSet<Integer> numbers = new HashSet<Integer>();
         
        for (int i = 0; i < 20; i++) {
            numbers.add(i);
        }
         
        //Set不提供get方法来获取指定位置的元素
        //numbers.get(0)
         
        //遍历Set可以采用迭代器iterator
        for (Iterator<Integer> iterator = numbers.iterator(); iterator.hasNext();) {
            Integer i = (Integer) iterator.next();
            System.out.println(i);
        }
         
        //或者采用增强型for循环
        for (Integer i : numbers) {
            System.out.println(i);
        }
         
    }
}
```





 示例 **4** : 

### HashSet和HashMap的关系

[**顶**](https://how2j.cn/k/collection/collection-hashset/364.html#)[**折**](https://how2j.cn/k/collection/collection-hashset/364.html#nowhere)

通过观察HashSet的源代码（[如何查看源代码](https://how2j.cn/k/helloworld/helloworld-eclipse-tips/300.html#step706)）
可以发现HashSet自身并没有独立的实现，而是在里面封装了一个Map.
HashSet是作为Map的key而存在的
而value是一个命名为PRESENT的static的Object对象，因为是一个类属性，所以只会有一个。

 

private static final Object PRESENT = new Object();

 

代码比较复制代码

```java
package collection;
 
import java.util.AbstractSet;
import java.util.HashMap;
import java.util.Iterator;
import java.util.Set;
 
public class HashSet<E>
    extends AbstractSet<E>
    implements Set<E>, Cloneable, java.io.Serializable
{
    //HashSet里封装了一个HashMap
    private  HashMap<E,Object> map;
 
    private static final Object PRESENT = new Object();
 
    //HashSet的构造方法初始化这个HashMap
    public HashSet() {
        map = new HashMap<E,Object>();
    }
 
    //向HashSet中增加元素，其实就是把该元素作为key，增加到Map中
    //value是PRESENT，静态，final的对象，所有的HashSet都使用这么同一个对象
    public boolean add(E e) {
        return map.put(e, PRESENT)==null;
    }
 
    //HashSet的size就是map的size
    public int size() {
        return map.size();
    }
 
    //清空Set就是清空Map
    public void clear() {
        map.clear();
    }
     
    //迭代Set,就是把Map的键拿出来迭代
    public Iterator<E> iterator() {
        return map.keySet().iterator();
    }
 
}
```





 示例 **5** : 

### 练习-HashSet 

  [**顶**](https://how2j.cn/k/collection/collection-hashset/364.html#)[**折**](https://how2j.cn/k/collection/collection-hashset/364.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/collection/collection-hashset/364.html#nowhere)

在[比较字符串](https://how2j.cn/k/number-string/number-string-compare/326.html#step2366)章节，有一个同样的练习
创建一个长度是100的字符串数组
使用长度是2的随机字符填充该字符串数组
统计这个字符串数组里**重复的字符串有多少种**
使用HashSet来解决这个问题

![练习-HashSet](https://stepimagewm.how2j.cn/2386.png)

## Collection是一个接口

 步骤 **1** : 

### Collection

[**顶**](https://how2j.cn/k/collection/collection-collection/366.html#)[**折**](https://how2j.cn/k/collection/collection-collection/366.html#nowhere)

Collection是 Set List Queue和 Deque的接口
Queue: 先进先出队列
Deque: 双向链表

**注：**Collection和Map之间没有关系，Collection是放一个一个对象的，Map 是放键值对的
**注：**Deque 继承 Queue,间接的继承了 Collection

![Collection](https://stepimagewm.how2j.cn/830.png)

## Collections

Collections是一个类，容器的工具类,就如同Arrays是数组的工具类

| 关键字           | 简介       |
| :--------------- | :--------- |
| reverse          | 反转       |
| shuffle          | 混淆       |
| sort             | 排序       |
| swap             | 交换       |
| rotate           | 滚动       |
| synchronizedList | 线程安全化 |

 步骤 **1** : 

### 反转

[**顶**](https://how2j.cn/k/collection/collection-collections/369.html#)[**折**](https://how2j.cn/k/collection/collection-collections/369.html#nowhere)

**reverse** 使List中的数据发生翻转

![反转](https://stepimagewm.how2j.cn/2498.png)

```java
package collection;
   
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;
   
public class TestCollection {
    public static void main(String[] args) {
        //初始化集合numbers
        List<Integer> numbers = new ArrayList<>();
         
        for (int i = 0; i < 10; i++) {
            numbers.add(i);
        }
         
        System.out.println("集合中的数据:");
        System.out.println(numbers);
         
        Collections.reverse(numbers);
         
        System.out.println("翻转后集合中的数据:");
        System.out.println(numbers);
         
    }
}
```



 步骤 **2** : 

### 混淆

**shuffle** 混淆List中数据的顺序

![混淆](https://stepimagewm.how2j.cn/2501.png)

代码比较复制代码

```java
package collection;
   
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;
   
public class TestCollection {
    public static void main(String[] args) {
        //初始化集合numbers
        List<Integer> numbers = new ArrayList<>();
         
        for (int i = 0; i < 10; i++) {
            numbers.add(i);
        }
         
        System.out.println("集合中的数据:");
        System.out.println(numbers);
         
        Collections.shuffle(numbers);
         
        System.out.println("混淆后集合中的数据:");
        System.out.println(numbers);
         
    }
}
```



 步骤 **3** : 

### 排序

[**顶**](https://how2j.cn/k/collection/collection-collections/369.html#)[**折**](https://how2j.cn/k/collection/collection-collections/369.html#nowhere)

**sort** 对List中的数据进行排序

![排序](https://stepimagewm.how2j.cn/2499.png)

```java
package collection;
   
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;
   
public class TestCollection {
    public static void main(String[] args) {
        //初始化集合numbers
        List<Integer> numbers = new ArrayList<>();
         
        for (int i = 0; i < 10; i++) {
            numbers.add(i);
        }
         
        System.out.println("集合中的数据:");
        System.out.println(numbers);
 
        Collections.shuffle(numbers);
        System.out.println("混淆后集合中的数据:");
        System.out.println(numbers);
 
        Collections.sort(numbers);
        System.out.println("排序后集合中的数据:");
        System.out.println(numbers);
         
    }
}
```



 步骤 **4** : 

### 交换

[**顶**](https://how2j.cn/k/collection/collection-collections/369.html#)[**折**](https://how2j.cn/k/collection/collection-collections/369.html#nowhere)

**swap** 交换两个数据的位置

![交换](https://stepimagewm.how2j.cn/2500.png)

```java
package collection;
   
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;
   
public class TestCollection {
    public static void main(String[] args) {
        //初始化集合numbers
        List<Integer> numbers = new ArrayList<>();
         
        for (int i = 0; i < 10; i++) {
            numbers.add(i);
        }
         
        System.out.println("集合中的数据:");
        System.out.println(numbers);
 
        Collections.swap(numbers,0,5);
        System.out.println("交换0和5下标的数据后，集合中的数据:");
        System.out.println(numbers);
         
    }
}
```



 步骤 **5** : 

### 滚动

[**顶**](https://how2j.cn/k/collection/collection-collections/369.html#)[**折**](https://how2j.cn/k/collection/collection-collections/369.html#nowhere)

**rotate** 把List中的数据，向右滚动指定单位的长度

![滚动](https://stepimagewm.how2j.cn/2497.png)

```java
package collection;
   
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;
   
public class TestCollection {
    public static void main(String[] args) {
        //初始化集合numbers
        List<Integer> numbers = new ArrayList<>();
         
        for (int i = 0; i < 10; i++) {
            numbers.add(i);
        }
         
        System.out.println("集合中的数据:");
        System.out.println(numbers);
 
        Collections.rotate(numbers,2);
        System.out.println("把集合向右滚动2个单位，标的数据后，集合中的数据:");
        System.out.println(numbers);
         
    }
}
```



 步骤 **6** : 

### 线程安全化

[**顶**](https://how2j.cn/k/collection/collection-collections/369.html#)[**折**](https://how2j.cn/k/collection/collection-collections/369.html#nowhere)

**synchronizedList** 把非线程安全的List转换为线程安全的List。 因为截至目前为止，还没有学习[线程安全](https://how2j.cn/k/thread/thread-synchronized/355.html#step793)的内容，暂时不展开。 线程安全的内容将在[多线程](https://how2j.cn/k/thread/thread-start/353.html)章节展开。

```java
package collection;
 
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;
 
public class TestCollection {
    public static void main(String[] args) {
        List<Integer> numbers = new ArrayList<>();
 
        System.out.println("把非线程安全的List转换为线程安全的List");
        List<Integer> synchronizedNumbers = (List<Integer>) Collections.synchronizedList(numbers);
 
    }
}
```



 步骤 **7** : 

### 练习-统计概率 

首先初始化一个List,长度是10，值是0-9。
然后不断的shuffle，直到前3位出现
3 1 4

shuffle 1000,00





## ArrayList 和 HashSet

 示例 **1** : 

### 是否有顺序

[**顶**](https://how2j.cn/k/collection/collection-arraylist-vs-hashset/367.html#)[**折**](https://how2j.cn/k/collection/collection-arraylist-vs-hashset/367.html#nowhere)

ArrayList: 有顺序
HashSet: 无顺序

HashSet的具体顺序，既不是按照插入顺序，也不是按照hashcode的顺序。关于hashcode有专门的章节讲解: [hashcode 原理](https://how2j.cn/k/collection/collection-hashcode/371.html)。

以下是**HasetSet源代码**中的部分注释

 

/**

 \* It makes no guarantees as to the iteration order of the set; 

 \* in particular, it does not guarantee that the order will remain constant over time. 

*/

 



 

不保证Set的迭代顺序; 确切的说，在不同条件下，元素的顺序都有可能不一样

 



换句话说，同样是插入0-9到HashSet中， 在JVM的不同版本中，看到的顺序都是不一样的。 所以在开发的时候，不能依赖于某种**臆测的顺序**，这个顺序本身是**不稳定的**

![是否有顺序](https://stepimagewm.how2j.cn/798.png)

代码比较复制代码

```java
package collection;
   
import java.util.ArrayList;
import java.util.HashSet;
    
public class TestCollection {
    public static void main(String[] args) {
           
        ArrayList<Integer> numberList =new ArrayList<Integer>();
        //List中的数据按照插入顺序存放
        System.out.println("----------List----------");
        System.out.println("向List 中插入 9 5 1");
        numberList.add(9);
        numberList.add(5);
        numberList.add(1);
        System.out.println("List 按照顺序存放数据:");
        System.out.println(numberList);
        System.out.println("----------Set----------");
        HashSet<Integer> numberSet =new HashSet<Integer>();
        System.out.println("向Set 中插入9 5 1");
        //Set中的数据不是按照插入顺序存放
        numberSet.add(9);
        numberSet.add(5);
        numberSet.add(1);
        System.out.println("Set 不是按照顺序存放数据:");
        System.out.println(numberSet);
           
    }
}
```



 示例 **2** : 

### 能否重复

[**顶**](https://how2j.cn/k/collection/collection-arraylist-vs-hashset/367.html#)[**折**](https://how2j.cn/k/collection/collection-arraylist-vs-hashset/367.html#nowhere)

List中的数据可以重复
Set中的数据不能够重复
重复判断标准是:
首先看hashcode是否相同
如果hashcode不同，则认为是不同数据
如果hashcode相同，再比较equals，如果equals相同，则是相同数据，否则是不同数据
更多关系hashcode，请参考[hashcode原理](https://how2j.cn/k/collection/collection-hashcode/371.html)

![能否重复](https://stepimagewm.how2j.cn/2513.png)

代码比较复制代码

```java
package collection;
   
import java.util.ArrayList;
import java.util.HashSet;
    
public class TestCollection {
    public static void main(String[] args) {
           
        ArrayList<Integer> numberList =new ArrayList<Integer>();
        //List中的数据可以重复
        System.out.println("----------List----------");
        System.out.println("向List 中插入 9 9");
        numberList.add(9);
        numberList.add(9);
        System.out.println("List 中出现两个9:");
        System.out.println(numberList);
        System.out.println("----------Set----------");
        HashSet<Integer> numberSet =new HashSet<Integer>();
        System.out.println("向Set 中插入9 9");
        //Set中的数据不能重复
        numberSet.add(9);
        numberSet.add(9);
        System.out.println("Set 中只会保留一个9:");
        System.out.println(numberSet);
           
    }
}
```





 示例 **3** : 

### 练习-不重复的随机数 

  [**顶**](https://how2j.cn/k/collection/collection-arraylist-vs-hashset/367.html#)[**折**](https://how2j.cn/k/collection/collection-arraylist-vs-hashset/367.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/collection/collection-arraylist-vs-hashset/367.html#nowhere)

生成50个 0-9999之间的随机数，要求不能有重复的

![练习-不重复的随机数](https://stepimagewm.how2j.cn/2520.png)

## ArrayList 和 LinkedList

 步骤 **1** : 

### ArrayList和LinkedList的区别

[**顶**](https://how2j.cn/k/collection/collection-arraylist-vs-linkedlist/690.html#)[**折**](https://how2j.cn/k/collection/collection-arraylist-vs-linkedlist/690.html#nowhere)

ArrayList **插入，删除数据慢**
LinkedList， **插入，删除数据快**
ArrayList是顺序结构，所以**定位很快**，指哪找哪。 就像电影院位置一样，有了电影票，一下就找到位置了。
LinkedList 是链表结构，就像手里的一串佛珠，要找出第99个佛珠，必须得一个一个的数过去，所以**定位慢**

![ArrayList和LinkedList的区别](https://stepimagewm.how2j.cn/799.png)



 步骤 **2** : 

### 插入数据

[**顶**](https://how2j.cn/k/collection/collection-arraylist-vs-linkedlist/690.html#)[**折**](https://how2j.cn/k/collection/collection-arraylist-vs-linkedlist/690.html#nowhere)

![插入数据](https://stepimagewm.how2j.cn/2507.png)

代码比较复制代码

```java
package collection;
 
import java.util.ArrayList;
import java.util.LinkedList;
import java.util.List;
 
public class TestCollection {
    public static void main(String[] args) {
        List<Integer> l;
        l = new ArrayList<>();
        insertFirst(l, "ArrayList");
 
        l = new LinkedList<>();
        insertFirst(l, "LinkedList");
 
    }
 
    private static void insertFirst(List<Integer> l, String type) {
        int total = 1000 * 100;
        final int number = 5;
        long start = System.currentTimeMillis();
        for (int i = 0; i < total; i++) {
            l.add(0, number);
        }
        long end = System.currentTimeMillis();
        System.out.printf("在%s 最前面插入%d条数据，总共耗时 %d 毫秒 %n", type, total, end - start);
    }
 
}
```



 步骤 **3** : 

### 定位数据

[**顶**](https://how2j.cn/k/collection/collection-arraylist-vs-linkedlist/690.html#)[**折**](https://how2j.cn/k/collection/collection-arraylist-vs-linkedlist/690.html#nowhere)

![定位数据](https://stepimagewm.how2j.cn/2508.png)

代码比较复制代码

```java
package collection;
 
import java.util.ArrayList;
import java.util.LinkedList;
import java.util.List;
 
public class TestCollection {
    public static void main(String[] args) {
        List<Integer> l;
        l = new ArrayList<>();
        modify(l, "ArrayList");
 
        l = new LinkedList<>();
        modify(l, "LinkedList");
 
    }
 
    private static void modify(List<Integer> l, String type) {
        int total = 100 * 1000;
        int index = total/2;
        final int number = 5;
        //初始化
        for (int i = 0; i < total; i++) {
            l.add(number);
        }
         
        long start = System.currentTimeMillis();
 
        for (int i = 0; i < total; i++) {
             int n = l.get(index);
             n++;
             l.set(index, n);
        }
        long end = System.currentTimeMillis();
        System.out.printf("%s总长度是%d，定位到第%d个数据，取出来，加1，再放回去%n 重复%d遍，总共耗时 %d 毫秒 %n", type,total, index,total, end - start);
        System.out.println();
    }
 
}
```





 步骤 **4** : 

### 练习-在后面插入数据 

  [**顶**](https://how2j.cn/k/collection/collection-arraylist-vs-linkedlist/690.html#)[**折**](https://how2j.cn/k/collection/collection-arraylist-vs-linkedlist/690.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/collection/collection-arraylist-vs-linkedlist/690.html#nowhere)

比较 ArrayList和LinkedList **在最后面插入**100000条数据，谁快谁慢？为什么？



### 练习-在中间插入数据 

在List的中间位置，插入数据，比较ArrayList快，还是LinkedList快，并解释为什么？

几种Set

 步骤 **1** : 

## HashSet LinkedHashSet TreeSet

[**顶**](https://how2j.cn/k/collection/collection-sets/691.html#)[**折**](https://how2j.cn/k/collection/collection-sets/691.html#nowhere)

HashSet： 无序
LinkedHashSet： 按照插入顺序
TreeSet： 从小到大排序

代码比较复制代码

```java
package collection;
  
import java.util.HashSet;
import java.util.LinkedHashSet;
import java.util.TreeSet;
  
public class TestCollection {
    public static void main(String[] args) {
        HashSet<Integer> numberSet1 =new HashSet<Integer>();
        //HashSet中的数据不是按照插入顺序存放
        numberSet1.add(88);
        numberSet1.add(8);
        numberSet1.add(888);
          
        System.out.println(numberSet1);
          
        LinkedHashSet<Integer> numberSet2 =new LinkedHashSet<Integer>();
        //LinkedHashSet中的数据是按照插入顺序存放
        numberSet2.add(88);
        numberSet2.add(8);
        numberSet2.add(888);
          
        System.out.println(numberSet2);
        TreeSet<Integer> numberSet3 =new TreeSet<Integer>();
        //TreeSet 中的数据是进行了排序的
        numberSet3.add(88);
        numberSet3.add(8);
        numberSet3.add(888);
          
        System.out.println(numberSet3);
          
    }
}
```



 步骤 **2** : 

### 练习-既不重复，又有顺序 

利用LinkedHashSet的既不重复，又有顺序的特性，把Math.PI中的数字，按照出现顺序打印出来，相同数字，只出现一次
