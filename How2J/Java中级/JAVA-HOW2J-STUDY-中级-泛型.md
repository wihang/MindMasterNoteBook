# JAVA-中级-泛型/Lambda

[toc]

## 集合中的泛型

 示例 **1** : 

### 不使用泛型

不使用泛型带来的问题
ADHero（物理攻击英雄） APHero（魔法攻击英雄）都是Hero的子类
ArrayList 默认接受Object类型的对象，所以所有对象都可以放进ArrayList中
所以get(0) **返回的类型是Object**
接着，需要进行强制转换才可以得到APHero类型或者ADHero类型。
如果软件开发人员记忆比较好，能**记得哪个是哪个**，还是可以的。 但是开发人员会犯错误，比如第20行，会记错，把第0个对象转换为ADHero,这样就会出现类型转换异常

代码比较复制代码

```java
package generic;
 
import java.util.ArrayList;
 
import charactor.ADHero;
import charactor.APHero;
 
public class TestGeneric {
 
    public static void main(String[] args) {
         
        ArrayList heros = new ArrayList();
         
        heros.add(new APHero());
        heros.add(new ADHero());
         
        APHero apHero =  (APHero) heros.get(0);
        ADHero adHero =  (ADHero) heros.get(1);
         
        ADHero adHero2 =  (ADHero) heros.get(0);
    }
}
```



 示例 **2** : 

### 使用泛3型

使用泛型的好处：
泛型的用法是在容器后面添加<Type>
Type可以是类，抽象类，接口
泛型表示这种容器，**只能存放APHero**，ADHero就放不进去了。

代码比较复制代码

```java
package generic;
 
import java.util.ArrayList;
 
import charactor.APHero;
 
public class TestGeneric {
 
    public static void main(String[] args) {
        ArrayList<APHero> heros = new ArrayList<APHero>();
         
        //只有APHero可以放进去    
        heros.add(new APHero());
         
        //ADHero甚至放不进去
        //heros.add(new ADHero());
         
        //获取的时候也不需要进行转型，因为取出来一定是APHero
        APHero apHero =  heros.get(0);
         
    }
}
```



 示例 **3** : 

### 子类对象

假设容器的泛型是Hero,那么**Hero的子类**APHero,ADHero**都可以放进去**
和Hero无关的类型Item还是放不进去

代码比较复制代码

```java
package generic;
 
import java.util.ArrayList;
 
import property.Item;
 
import charactor.ADHero;
import charactor.APHero;
import charactor.Hero;
 
public class TestGeneric {
 
    public static void main(String[] args) {
        ArrayList<Hero> heros = new ArrayList<Hero>();
         
        //只有作为Hero的子类可以放进去     
        heros.add(new APHero());
        heros.add(new ADHero());
         
        //和Hero无关的类型Item还是放不进去
        //heros.add(new Item());
         
    }
}
```





 示例 **4** : 

### 泛型的简写

为了不使编译器出现警告，需要前后都使用泛型，像这样：

 

ArrayList<Hero> heros = new ArrayList<Hero>();

 


不过JDK7提供了一个可以略微减少代码量的泛型简写方式

 

ArrayList<Hero> heros2 = new ArrayList<>();

 


后面的泛型可以用<>来代替，聊胜于无吧

代码比较复制代码

```java
package generic;
  
import java.util.ArrayList;
 
import charactor.Hero;
  
public class TestGeneric {
  
    public static void main(String[] args) {
        ArrayList<Hero> heros = new ArrayList<Hero>();
        //后面可以只用<>
        ArrayList<Hero> heros2 = new ArrayList<>();
         
    }
}
```



 示例 **5** : 

### 练习-泛型 

 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/generic/generic-generic/373.html#nowhere)

根据[数字类](https://how2j.cn/k/number-string/number-string-wrap/22.html#step672)的知识，设计一个集合，这个集合里即可以放整数，也可以放浮点数，但是不能放字符串

## 支持泛型的类

 步骤 **1** : 

### 不支持泛型的Stack

以[Stack栈](https://how2j.cn/k/collection/collection-linkedlist/370.html#step2475)为例子，如果不使用泛型
当需要一个只能放Hero的栈的时候，就需要设计一个HeroStack
当需要一个只能放Item的栈的时候，就需要一个ItemStack

- [HeroStack.java](https://how2j.cn/k/generic/generic-generic-class/374.html#nowhere)

  - ```java
    package generic;
       
    import java.util.LinkedList;
     
    import charactor.Hero;
       
    public class HeroStack {
       
        LinkedList<Hero> heros = new LinkedList<Hero>();
           
        public void push(Hero h) {
            heros.addLast(h);
        }
       
        public Hero pull() {
            return heros.removeLast();
        }
       
        public Hero peek() {
            return heros.getLast();
        }
           
        public static void main(String[] args) {
               
            HeroStack heroStack = new HeroStack();
            for (int i = 0; i < 5; i++) {
                Hero h = new Hero("hero name " + i);
                System.out.println("压入 hero:" + h);
                heroStack.push(h);
            }
            for (int i = 0; i < 5; i++) {
                Hero h =heroStack.pull();
                System.out.println("弹出 hero" + h);
            }
        }
       
    }
    ```

- [ItemStack.java](https://how2j.cn/k/generic/generic-generic-class/374.html#nowhere)

  - ```java
    package generic;
       
    import java.util.LinkedList;
     
    import property.Item;
       
    public class ItemStack {
       
        LinkedList<Item> Items = new LinkedList<Item>();
           
        public void push(Item h) {
            Items.addLast(h);
        }
       
        public Item pull() {
            return Items.removeLast();
        }
       
        public Item peek() {
            return Items.getLast();
        }
           
        public static void main(String[] args) {
               
            ItemStack ItemStack = new ItemStack();
            for (int i = 0; i < 5; i++) {
                Item item = new Item("Item name " + i);
                System.out.println("压入 Item:" + item);
                ItemStack.push(item);
            }
            for (int i = 0; i < 5; i++) {
                Item item =ItemStack.pull();
                System.out.println("弹出 Item" + item);
            }
        }
       
    }
    ```

  - 

步骤 **2** : 

### 支持泛型的Stack

设计一个支持泛型的栈MyStack
设计这个类的时候，在类的声明上，加上一个<T>，表示该类支持泛型。
T是type的缩写，也可以使用任何其他的合法的变量，比如A,B,X都可以，但是一般约定成俗使用T，代表类型。

```java
package generic;
   
import java.util.HashMap;
import java.util.LinkedList;
 
import charactor.Hero;
import property.Item;
   
public class MyStack<T> {
   
    LinkedList<T> values = new LinkedList<T>();
       
    public void push(T t) {
        values.addLast(t);
    }
   
    public T pull() {
        return values.removeLast();
    }
   
    public T peek() {
        return values.getLast();
    }
       
    public static void main(String[] args) {
        //在声明这个Stack的时候，使用泛型<Hero>就表示该Stack只能放Hero
        MyStack<Hero> heroStack = new MyStack<>();
        heroStack.push(new Hero());
        //不能放Item
        heroStack.push(new Item());
         
        //在声明这个Stack的时候，使用泛型<Item>就表示该Stack只能放Item
        MyStack<Item> itemStack = new MyStack<>();
        itemStack.push(new Item());
        //不能放Hero
        itemStack.push(new Hero());
    }
   
}
```

 步骤 **3** : 

### 练习-支持泛型的二叉树 

把[二叉树](https://how2j.cn/k/collection/collection-tree/476.html)中的Node类，改造成支持泛型

---

## 泛型-通配符

 示例 **1** : 

### ? extends

ArrayList heroList<? extends Hero> 表示这是一个Hero泛型或者其子类泛型
heroList 的泛型可能是Hero
heroList 的泛型可能是APHero
heroList 的泛型可能是ADHero
所以 可以确凿的是，**从heroList取出来的对象，一定是可以转型成Hero的**

但是，不能往里面放东西，因为
放APHero就不满足<ADHero>
放ADHero又不满足<APHero>

![? extends](https://stepimagewm.how2j.cn/837.png)

```java
package generic;
   
import java.util.ArrayList;
  
import charactor.ADHero;
import charactor.APHero;
import charactor.Hero;
   
public class TestGeneric {
   
    public static void main(String[] args) {
          
        ArrayList<APHero> apHeroList = new ArrayList<APHero>();
        apHeroList.add(new APHero());
         
        ArrayList<? extends Hero> heroList = apHeroList;
          
        //? extends Hero 表示这是一个Hero泛型的子类泛型
          
        //heroList 的泛型可以是Hero
        //heroList 的泛型可以使APHero
        //heroList 的泛型可以使ADHero
          
        //可以确凿的是，从heroList取出来的对象，一定是可以转型成Hero的
          
        Hero h= heroList.get(0);
          
        //但是，不能往里面放东西
        heroList.add(new ADHero()); //编译错误，因为heroList的泛型 有可能是APHero
          
    }
      
}
```

示例 **2** : 

### ? super

ArrayList heroList<? super Hero> 表示这是一个Hero泛型或者其父类泛型
heroList的泛型可能是Hero
heroList的泛型可能是Object

**可以往里面插入Hero以及Hero的子类**
但是取出来有风险，因为不确定取出来是Hero还是Object

![? super](https://stepimagewm.how2j.cn/838.png)

```java
package generic;
  
import java.util.ArrayList;
  
import charactor.ADHero;
import charactor.APHero;
import charactor.Hero;
  
public class TestGeneric {
    public static void main(String[] args) {
  
        ArrayList<? super Hero> heroList = new ArrayList<Object>();
          
        //? super Hero 表示 heroList的泛型是Hero或者其父类泛型
          
        //heroList 的泛型可以是Hero
        //heroList 的泛型可以是Object
          
        //所以就可以插入Hero
        heroList.add(new Hero());
        //也可以插入Hero的子类
        heroList.add(new APHero());
        heroList.add(new ADHero());
          
        //但是，不能从里面取数据出来,因为其泛型可能是Object,而Object是强转Hero会失败
        Hero h= heroList.get(0);
          
    }
  
}
```

 示例 **3** : 

### 泛型通配符?

泛型通配符? 代表任意泛型
既然?代表任意泛型，那么换句话说，这个容器什么泛型都有可能

所以只能以Object的形式取出来
并且不能往里面放对象，因为不知道到底是一个什么泛型的容器

![泛型通配符?](https://stepimagewm.how2j.cn/836.png)

代码比较复制代码

```java
package generic;
  
import java.util.ArrayList;
 
import property.Item;
import charactor.APHero;
import charactor.Hero;
  
public class TestGeneric {
  
    public static void main(String[] args) {
  
        ArrayList<APHero> apHeroList = new ArrayList<APHero>();
         
        //?泛型通配符，表示任意泛型
        ArrayList<?> generalList = apHeroList;
 
        //?的缺陷1： 既然?代表任意泛型，那么换句话说，你就不知道这个容器里面是什么类型
        //所以只能以Object的形式取出来
        Object o = generalList.get(0);
 
        //?的缺陷2： 既然?代表任意泛型，那么既有可能是Hero,也有可能是Item
        //所以，放哪种对象进去，都有风险，结果就什么什么类型的对象，都不能放进去
        generalList.add(new Item()); //编译错误 因为?代表任意泛型，很有可能不是Item
        generalList.add(new Hero()); //编译错误 因为?代表任意泛型，很有可能不是Hero
        generalList.add(new APHero()); //编译错误  因为?代表任意泛型，很有可能不是APHero
  
    }
}
```



 示例 **4** : 

### 总结

如果希望只取出，不插入，就使用? extends Hero
如果希望只插入，不取出，就使用? super Hero
如果希望，又能插入，又能取出，就不要用通配符？



 示例 **5** : 

### 练习- extends 

如代码所示，为了遍历不同泛型的3种集合，需要设计3个方法

借助? extends， 把代码减肥到只是用一种方法

代码比较复制代码

```java
package generic;
 
import java.util.ArrayList;
 
import charactor.ADHero;
import charactor.APHero;
import charactor.Hero;
 
public class TestGeneric {
 
    public static void iterate(ArrayList<Hero> list) {
        for (Hero hero : list) {
            System.out.println(hero.name);
        }
    }
 
    public static void iterateAP(ArrayList<APHero> list) {
        for (Hero hero : list) {
            System.out.println(hero.name);
        }
    }
 
    public static void iterateAD(ArrayList<ADHero> list) {
        for (Hero hero : list) {
            System.out.println(hero.name);
        }
    }
 
    public static void main(String[] args) {
        ArrayList<Hero> hs = new ArrayList<>();
        ArrayList<APHero> aphs = new ArrayList<>();
        ArrayList<ADHero> adhs = new ArrayList<>();
 
        iterate(hs);
        iterateAP(aphs);
        iterateAD(adhs);
    }
 
}
```



 示例 **7** : 

### 练习-二叉树 

把[练习-支持泛型的二叉树](https://how2j.cn/k/generic/generic-generic-class/374.html#step2536)改造成 支持泛型 <T extends Comparable>，并在比较的时候使用compare方法

---

## 泛型转型

 步骤 **1** : 

### 对象转型

根据面向对象学习的知识，[子类转父类](https://how2j.cn/k/interface-inheritance/interface-inheritance-casting/308.html#step624) 是一定可以成功的

代码比较复制代码

```java
package generic;
 
import charactor.ADHero;
import charactor.Hero;
 
public class TestGeneric {
 
    public static void main(String[] args) {
 
        Hero h = new Hero();
        ADHero ad = new ADHero();
        //子类转父类
        h = ad;
    }
 
}
```



 步骤 **2** : 

### 子类泛型转父类泛型

既然 子类对象 转 父类对象是可以成功的，那么子类泛型转父类泛型能成功吗？
如代码
hs的泛型是父类Hero
adhs 的泛型是子类ADHero

那么 把adhs转换为hs能成功吗？

代码比较复制代码

```java
package generic;
 
import java.util.ArrayList;
 
import charactor.ADHero;
import charactor.Hero;
 
public class TestGeneric {
 
    public static void main(String[] args) {
        ArrayList<Hero> hs =new ArrayList<>();
        ArrayList<ADHero> adhs =new ArrayList<>();
 
        //子类泛型转父类泛型
        hs = adhs;
    }
 
}
```



 步骤 **3** : 

### 假设可以转型成功

假设可以转型成功
引用hs指向了ADHero泛型的容器
作为Hero泛型的引用hs, 看上去是可以往里面加一个APHero的。
但是hs这个引用，实际上是指向的一个ADHero泛型的容器
如果能加进去，就变成了ADHero泛型的容器里放进了APHero，这就矛盾了

所以子类泛型**不可以**转换为父类泛型

![假设可以转型成功](https://stepimagewm.how2j.cn/835.png)

```java
package generic;
 
import java.util.ArrayList;
 
import charactor.ADHero;
import charactor.APHero;
import charactor.Hero;
 
public class TestGeneric {
 
    public static void main(String[] args) {
        ArrayList<Hero> hs =new ArrayList<>();
        ArrayList<ADHero> adhs =new ArrayList<>();
 
        //假设能转换成功
        hs = adhs;
         
        //作为Hero泛型的hs,是可以向其中加入APHero的
        //但是hs这个引用，实际上是指向的一个ADHero泛型的容器
        //如果能加进去，就变成了ADHero泛型的容器里放进了APHero，这就矛盾了
        hs.add(new APHero());
    }
 
}
```



 步骤 **4** : 

### 练习-父类泛型能否转换为子类泛型？ 

上面使用反证法分析了，子类泛型不能转换为父类泛型。

那么父类泛型又能否转换成子类泛型？ 为什么？

代码比较复制代码

```java
package generic;
  
import java.util.ArrayList;
  
import charactor.ADHero;
import charactor.Hero;
  
public class TestGeneric {
  
    public static void main(String[] args) {
        ArrayList<Hero> hs =new ArrayList<>();
        ArrayList<ADHero> adhs =new ArrayList<>();
  
        //父类泛型转子类泛型，能否成功？为什么？
        adhs = hs;
         
    }
  
}
```

## Lambda

假设一个情景： 找出满足条件的Hero
本教程将从使用**普通方法**，**匿名类**，以及**Lambda**这几种方式，逐渐的引入Lambda的概念



 步骤 **1** : 

### 普通方法

使用一个普通方法，在for循环遍历中进行条件判断，筛选出满足条件的数据

 

hp>100 && damage<50

 

![普通方法](https://stepimagewm.how2j.cn/2551.png)

- [TestLambda.java](https://how2j.cn/k/lambda/lambda-lamdba-tutorials/697.html#nowhere)

  - ```java
    package lambda;
      
    import java.util.ArrayList;
    import java.util.List;
    import java.util.Random;
      
    import charactor.Hero;
      
    public class TestLambda {
        public static void main(String[] args) {
            Random r = new Random();
            List<Hero> heros = new ArrayList<Hero>();
            for (int i = 0; i < 10; i++) {
                heros.add(new Hero("hero " + i, r.nextInt(1000), r.nextInt(100)));
            }
            System.out.println("初始化后的集合：");
            System.out.println(heros);
            System.out.println("筛选出 hp>100 && damange<50的英雄");
            filter(heros);
        }
      
        private static void filter(List<Hero> heros) {
            for (Hero hero : heros) {
                if(hero.hp>100 && hero.damage<50)
                    System.out.print(hero);
            }
        }
      
    }
    ```

  - 

- [Hero.java](https://how2j.cn/k/lambda/lambda-lamdba-tutorials/697.html#nowhere)

  - ```java
    package charactor;
         
    public class Hero implements Comparable<Hero>{
        public String name;
        public float hp;
            
        public int damage;
            
        public Hero(){
               
        }
           
        public Hero(String name) {
            this.name =name;
       
        }
           
        //初始化name,hp,damage的构造方法
        public Hero(String name,float hp, int damage) {
            this.name =name;
            this.hp = hp;
            this.damage = damage;
        }
       
        @Override
        public int compareTo(Hero anotherHero) {
            if(damage<anotherHero.damage)
                return 1; 
            else
                return -1;
        }
       
        @Override
        public String toString() {
            return "Hero [name=" + name + ", hp=" + hp + ", damage=" + damage + "]\r\n";
        }
           
    }
    ```

    步骤 **2** : 

### 匿名类方式

首先准备一个接口HeroChecker，提供一个test(Hero)方法
然后通过匿名类的方式，实现这个接口

 

HeroChecker checker = new HeroChecker() {

​	public boolean test(Hero h) {

​		return (h.hp>100 && h.damage<50);

​	}

};

 


接着调用filter，传递这个checker进去进行判断，这种方式就很像通过Collections.sort在对一个Hero集合排序，需要传一个[Comparator](https://how2j.cn/k/collection/collection-comparator-comparable/693.html#step828)的匿名类对象进去一样。



![匿名类方式](https://stepimagewm.how2j.cn/2552.png)

- [TestLambda.java](https://how2j.cn/k/lambda/lambda-lamdba-tutorials/697.html#nowhere)

  - ```java
    package lambda;
       
    import java.util.ArrayList;
    import java.util.List;
    import java.util.Random;
       
    import charactor.Hero;
       
    public class TestLambda {
        public static void main(String[] args) {
            Random r = new Random();
            List<Hero> heros = new ArrayList<Hero>();
            for (int i = 0; i < 5; i++) {
                heros.add(new Hero("hero " + i, r.nextInt(1000), r.nextInt(100)));
            }
            System.out.println("初始化后的集合：");
            System.out.println(heros);
            System.out.println("使用匿名类的方式，筛选出 hp>100 && damange<50的英雄");
            HeroChecker checker = new HeroChecker() {
                @Override
                public boolean test(Hero h) {
                    return (h.hp>100 && h.damage<50);
                }
            };
               
            filter(heros,checker);
        }
       
        private static void filter(List<Hero> heros,HeroChecker checker) {
            for (Hero hero : heros) {
                if(checker.test(hero))
                    System.out.print(hero);
            }
        }
       
    }
    ```

- [HeroChecker.java](https://how2j.cn/k/lambda/lambda-lamdba-tutorials/697.html#nowhere)

  - ```java
    package lambda;
     
    import charactor.Hero;
     
    public interface HeroChecker {
        public boolean test(Hero h);
    }
    ```

步骤 **3** : 

### Lambda方式

使用Lambda方式筛选出数据

 

filter(heros,(h)->h.hp>100 && h.damage<50);

 


同样是调用filter方法，从上一步的传递匿名类对象，变成了传递一个Lambda表达式进去

 

h->h.hp>100 && h.damage<50

 



咋一看Lambda表达式似乎不好理解，其实很简单，下一步讲解如何从一个匿名类一点点**演变成**Lambda表达式

![Lambda方式](https://stepimagewm.how2j.cn/2553.png)

代码比较复制代码

```java
package lambda;
 
import java.util.ArrayList;
import java.util.List;
import java.util.Random;
 
import charactor.Hero;
 
public class TestLamdba {
    public static void main(String[] args) {
        Random r = new Random();
        List<Hero> heros = new ArrayList<Hero>();
        for (int i = 0; i < 5; i++) {
            heros.add(new Hero("hero " + i, r.nextInt(1000), r.nextInt(100)));
        }
        System.out.println("初始化后的集合：");
        System.out.println(heros);
        System.out.println("使用Lamdba的方式，筛选出 hp>100 && damange<50的英雄");
        filter(heros,h->h.hp>100 && h.damage<50);
    }
 
    private static void filter(List<Hero> heros,HeroChecker checker) {
        for (Hero hero : heros) {
            if(checker.test(hero))
                System.out.print(hero);
        }
    }
 
}
```

 步骤 **4** : 

### 设置eclipse以支持Lambda

如果你的eclipse能够正常识别Lambda，那么就可以跳过这个章节了。
因为Lambda是JDK8的内容，除了JDK需要使用1.8以上版本外([在JDK环境变量配置](https://how2j.cn/k/helloworld/helloworld-jdk/141.html)下载的就是1.8了)，还需要在eclipse中把编译器设置为1.8才能够正常识别Lambda.

设置办法：
菜单->Window->Preferences->Java-Compiler->Compiler compliance leve: 设置为1.8即可

![设置eclipse以支持Lambda](https://stepimagewm.how2j.cn/2570.png)



 步骤 **5** : 

### 从匿名类演变成Lambda表达式

Lambda表达式可以看成是匿名类一点点**演变过来**
\1. 匿名类的正常写法

 

HeroChecker c1 = new HeroChecker() {

​    public boolean test(Hero h) {

​        return (h.hp>100 && h.damage<50);

​    }

};

 


\2. 把外面的壳子去掉
只保留**方法参数**和**方法体**
参数和方法体之间加上符号 **->**

 

HeroChecker c2 = (Hero h) ->{

​	return h.hp>100 && h.damage<50;

};

 



\3. 把return和{}去掉

 

HeroChecker c3 = (Hero h) ->h.hp>100 && h.damage<50;

 



\4. 把 参数类型和圆括号去掉(只有一个参数的时候，才可以去掉圆括号)

 

HeroChecker c4 = h ->h.hp>100 && h.damage<50;

 



\5. 把c4作为参数传递进去

 

filter(heros,c4);

 



\6. 直接把表达式传递进去

 

filter(heros, h -> h.hp > 100 && h.damage < 50);

 

代码比较复制代码

```java
package lambda;
 
import java.util.ArrayList;
import java.util.List;
import java.util.Random;
 
import charactor.Hero;
 
public class TestLamdba {
    public static void main(String[] args) {
        Random r = new Random();
        List<Hero> heros = new ArrayList<Hero>();
        for (int i = 0; i < 5; i++) {
            heros.add(new Hero("hero " + i, r.nextInt(1000), r.nextInt(100)));
        }
        System.out.println("初始化后的集合：");
        System.out.println(heros);
        System.out.println("使用匿名类的方式，筛选出 hp>100 && damange<50的英雄");
        // 匿名类的正常写法
        HeroChecker c1 = new HeroChecker() {
            @Override
            public boolean test(Hero h) {
                return (h.hp > 100 && h.damage < 50);
            }
        };
        // 把new HeroChcekcer，方法名，方法返回类型信息去掉
        // 只保留方法参数和方法体
        // 参数和方法体之间加上符号 ->
        HeroChecker c2 = (Hero h) -> {
            return h.hp > 100 && h.damage < 50;
        };
 
        // 把return和{}去掉
        HeroChecker c3 = (Hero h) -> h.hp > 100 && h.damage < 50;
 
        // 把 参数类型和圆括号去掉
        HeroChecker c4 = h -> h.hp > 100 && h.damage < 50;
 
        // 把c4作为参数传递进去
        filter(heros, c4);
         
        // 直接把表达式传递进去
        filter(heros, h -> h.hp > 100 && h.damage < 50);
    }
 
    private static void filter(List<Hero> heros, HeroChecker checker) {
        for (Hero hero : heros) {
            if (checker.test(hero))
                System.out.print(hero);
        }
    }
 
}
```



 步骤 **6** : 

### 匿名方法

与[匿名类](https://how2j.cn/k/interface-inheritance/interface-inheritance-inner-class/322.html#step687) 概念相比较，
Lambda 其实就是**匿名方法**，这是一种**把方法作为参数**进行传递的编程思想。

虽然代码是这么写

 

filter(heros, h -> h.hp > 100 && h.damage < 50);

 


但是，Java会在背后，悄悄的，把这些都还原成[匿名类方式](https://how2j.cn/k/lambda/lambda-lamdba-tutorials/697.html#step2552)。
引入Lambda表达式，会使得代码更加紧凑，而不是各种接口和匿名类到处飞。



 步骤 **7** : 

### Lambda的弊端

Lambda表达式虽然带来了代码的简洁，但是也有其局限性。
\1. 可读性差，与**啰嗦的**但是**清晰的**匿名类代码结构比较起来，Lambda表达式一旦变得比较长，就难以理解
\2. 不便于调试，很难在Lambda表达式中增加调试信息，比如日志
\3. 版本支持，Lambda表达式在JDK8版本中才开始支持，如果系统使用的是以前的版本，考虑系统的稳定性等原因，而不愿意升级，那么就无法使用。

Lambda比较适合用在简短的业务代码中，并不适合用在复杂的系统中，会加大维护成本。



 步骤 **8** : 

### 练习-Co3mparator 

把[比较器-Comparator](https://how2j.cn/k/collection/collection-comparator-comparable/693.html#step828) 章节中的代码，按照[从匿名类演变成Lambda表达式](https://how2j.cn/k/lambda/lambda-lamdba-tutorials/697.html#step2556)的步骤，改写为Lambda表达式