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

### 练习-删除ArrayList中的数据 

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
