# JAVA_HOW2J_STUDY_基础部分（下篇）

[toc]



## JAVA基础

### 类和对象

#### 引用

引用的概念，如果一个变量的类型是 类类型，而非基本类型，那么该变量又叫做引用。

 步骤 **1** : 

##### 引用和指向

[**顶**](https://how2j.cn/k/class-object/class-object-reference/307.html#)[**折**](https://how2j.cn/k/class-object/class-object-reference/307.html#nowhere)

 

new Hero();

 


代表**创建**了一个Hero对象
但是也仅仅是创建了一个对象，没有办法访问它
为了访问这个对象，会使用**引用**来**代表**这个对象

 

Hero h = new Hero();

 


h这个变量是Hero类型，又叫做引用
=的意思指的h这个引用**代表**右侧创建的对象
“**代表**” 在面向对象里，又叫做“**指向**”

![引用和指向](https://stepimagewm.how2j.cn/618.png)

代码比较复制代码

```java
public class Hero {
      
    String name; //姓名
      
    float hp; //血量
      
    float armor; //护甲
      
    int moveSpeed; //移动速度
      
    public static void main(String[] args) {
        //创建一个对象
        new Hero();
         
        //使用一个引用来指向这个对象
        Hero h = new Hero();
         
    }  
      
}
```



 步骤 **2** : 

##### 多个引用，一个对象

[**顶**](https://how2j.cn/k/class-object/class-object-reference/307.html#)[**折**](https://how2j.cn/k/class-object/class-object-reference/307.html#nowhere)

引用有多个，但是对象只有一个。
在这个例子里，所有引用都指向了同一个对象。
对象就像 "房产"， 引用就像"房产证"
房产证的复印件可以有多张，但是真正的"房产" 只有这么一处

![多个引用，一个对象](https://stepimagewm.how2j.cn/617.png)

代码比较复制代码

```java
public class Hero {
      
    String name; //姓名
      
    float hp; //血量
      
    float armor; //护甲
      
    int moveSpeed; //移动速度
      
    public static void main(String[] args) {
         
        //使用一个引用来指向这个对象
        Hero h1 = new Hero();
        Hero h2 = h1;  //h2指向h1所指向的对象
        Hero h3 = h1;
        Hero h4 = h1;
        Hero h5 = h4;
         
        //h1,h2,h3,h4,h5 五个引用，都指向同一个对象
         
    }  
      
}
```





 步骤 **3** : 

##### 一个引用，多个对象

[**顶**](https://how2j.cn/k/class-object/class-object-reference/307.html#)[**折**](https://how2j.cn/k/class-object/class-object-reference/307.html#nowhere)

第8行，引用garen指向新创建的对象（对象1）
第9行，同一个引用garen指向新创建的对象（对象2）
这个时候，对象1，就没有任何引用指向了
换句话说，就没有任何手段控制和访问该对象，那么该对象就变得没有意义。

![一个引用，多个对象](https://stepimagewm.how2j.cn/619.png)

代码比较复制代码

```java 
package charactor;
 
public class Hero {
    public String name;
    protected float hp;
 
    public static void main(String[] args) {
           Hero garen =  new Hero();
           garen =  new Hero();
    }
}
```



 步骤 **4** : 

##### 练习-引用 

  [**顶**](https://how2j.cn/k/class-object/class-object-reference/307.html#)[**折**](https://how2j.cn/k/class-object/class-object-reference/307.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/class-object/class-object-reference/307.html#nowhere)

如代码，问题:
h4所指向的对象和h2所指向的对象，是否是同一个对象？

代码比较复制代码

```java
package charactor;
  
public class Hero {
    public String name;
    protected float hp;
  
    public static void main(String[] args) {
           Hero h1 =  new Hero();
           Hero h2 =  new Hero();
           Hero h3;
           Hero h4;
           h3 = h1;
           h4 = h3;
    }
}
```

#### 继承

在LOL中，武器是物品的一种，也是有名称和价格的
所以在设计类的时候，可以让武器继承物品，从而继承名称和价格属性

 步骤 **1** : 

##### 物品类Item

[**顶**](https://how2j.cn/k/class-object/class-object-extends/288.html#)[**折**](https://how2j.cn/k/class-object/class-object-extends/288.html#nowhere)

物品类Item 有属性 name,price

代码比较复制代码

```java
public class Item {
    String name;
    int price;
}
```



 步骤 **2** : 

##### 武器类Weapon（不继承）

[**顶**](https://how2j.cn/k/class-object/class-object-extends/288.html#)[**折**](https://how2j.cn/k/class-object/class-object-extends/288.html#nowhere)

武器类： Weapon**不继承Item**的写法
独立设计 name和price属性
同时多了一个属性 damage 攻击力

代码比较复制代码

```java
public class Weapon{
    String name;
    int price;
    int damage; //攻击力
 
}
```



 步骤 **3** : 

##### 武器类Weapon（继承类Item）

[**顶**](https://how2j.cn/k/class-object/class-object-extends/288.html#)[**折**](https://how2j.cn/k/class-object/class-object-extends/288.html#nowhere)

这一次Weapon**继承Item**
虽然Weapon自己没有设计name和price,但是通过继承Item类，也具备了name和price属性

代码比较复制代码

```java
public class Weapon extends Item{
    int damage; //攻击力
     
    public static void main(String[] args) {
        Weapon infinityEdge = new Weapon();
        infinityEdge.damage = 65; //damage属性在类Weapon中新设计的
         
        infinityEdge.name = "无尽之刃";//name属性，是从Item中继承来的，就不需要重复设计了
        infinityEdge.price = 3600;
         
    }
     
}
```



 步骤 **4** : 

##### 练习-护甲 

  [**顶**](https://how2j.cn/k/class-object/class-object-extends/288.html#)[**折**](https://how2j.cn/k/class-object/class-object-extends/288.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/class-object/class-object-extends/288.html#nowhere)

设计一个类Armor护甲
继承Item类，并且额外提供一个属性ac: 护甲等级 int类型

实例化出两件护甲
名称 价格 护甲等级
布甲 300 15
锁子甲 500 40

#### 方法重载

方法的重载指的是方法名一样，但是参数类型不一样

 步骤 **1** : 

##### attack方法的重载

[**顶**](https://how2j.cn/k/class-object/class-object-overload/291.html#)[**折**](https://how2j.cn/k/class-object/class-object-overload/291.html#nowhere)

有一种英雄，叫做物理攻击英雄 ADHero
为ADHero 提供三种方法



public void attack()

public void attack(Hero h1)

public void attack(Hero h1, Hero h2)

 


方法名是一样的，但是参数类型不一样
在调用方法attack的时候，会根据传递的参数类型以及数量，自动调用对应的方法

![attack方法的重载](https://stepimagewm.how2j.cn/590.png)

代码比较复制代码

```java
public class ADHero extends Hero {
    public void attack() {
        System.out.println(name + " 进行了一次攻击 ，但是不确定打中谁了");
    }
 
    public void attack(Hero h1) {
        System.out.println(name + "对" + h1.name + "进行了一次攻击 ");
    }
 
    public void attack(Hero h1, Hero h2) {
        System.out.println(name + "同时对" + h1.name + "和" + h2.name + "进行了攻击 ");
    }
 
    public static void main(String[] args) {
        ADHero bh = new ADHero();
        bh.name = "赏金猎人";
 
        Hero h1 = new Hero();
        h1.name = "盖伦";
        Hero h2 = new Hero();
        h2.name = "提莫";
 
        bh.attack(h1);
        bh.attack(h1, h2);
    }
 
}
```



 步骤 **2** : 

##### 可变数量的参数

[**顶**](https://how2j.cn/k/class-object/class-object-overload/291.html#)[**折**](https://how2j.cn/k/class-object/class-object-overload/291.html#nowhere)

如果要攻击更多的英雄，就需要设计更多的方法，这样类会显得很累赘，像这样：

 

public void attack(Hero h1)

public void attack(Hero h1,Hero h2)

public void attack(Hero h1,Hero h2,Hero h3)

 


这时，可以采用可变数量的参数
**只需要设计一个方法**
public void attack(Hero **...**heros)
即可代表上述所有的方法了
在方法里，使用操作数组的方式处理参数heros即可

代码比较复制代码

```java
public class ADHero extends Hero {
 
    public void attack() {
        System.out.println(name + " 进行了一次攻击 ，但是不确定打中谁了");
    }
 
    // 可变数量的参数
    public void attack(Hero... heros) {
        for (int i = 0; i < heros.length; i++) {
            System.out.println(name + " 攻击了 " + heros[i].name);
 
        }
    }
 
    public static void main(String[] args) {
        ADHero bh = new ADHero();
        bh.name = "赏金猎人";
 
        Hero h1 = new Hero();
        h1.name = "盖伦";
        Hero h2 = new Hero();
        h2.name = "提莫";
 
        bh.attack(h1);
        bh.attack(h1, h2);
 
    }
 
}
```



 步骤 **3** : 

##### 练习-治疗 

  [**顶**](https://how2j.cn/k/class-object/class-object-overload/291.html#)[**折**](https://how2j.cn/k/class-object/class-object-overload/291.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/class-object/class-object-overload/291.html#nowhere)

设计一个类Support (辅助英雄)继承Hero，提供一个heal(治疗)方法
对Support的heal方法进行重载
heal()
heal(Hero h) //为指定的英雄加血
heal(Hero h, int hp) //为指定的英雄加了hp的血

---

#### 构造方法

通过一个类创建一个对象，这个过程叫做**实例化**

实例化是通过调用**构造方法**(又叫做**构造器**)实现的

 步骤 **1** : 

##### 什么是构造方法

[**顶**](https://how2j.cn/k/class-object/class-object-constructor/292.html#)[**折**](https://how2j.cn/k/class-object/class-object-constructor/292.html#nowhere)

方法名和类名一样（包括大小写）
**没有返回类型**
实例化一个对象的时候，必然调用构造方法

代码比较复制代码

```java
public class Hero {
 
    String name;
 
    float hp;
 
    float armor;
 
    int moveSpeed;
 
    // 方法名和类名一样（包括大小写）
    // 没有返回类型
    public Hero() {
        System.out.println("实例化一个对象的时候，必然调用构造方法");
    }
     
    public static void main(String[] args) {
        //实例化一个对象的时候，必然调用构造方法
        Hero h = new Hero();
    }
 
}
```



 步骤 **2** : 

##### 隐式的构造方法

[**顶**](https://how2j.cn/k/class-object/class-object-constructor/292.html#)[**折**](https://how2j.cn/k/class-object/class-object-constructor/292.html#nowhere)

Hero类的构造方法是

 

public Hero(){  

}

 


这个无参的构造方法，如果不写，就会默认提供一个

代码比较复制代码

```java
public class Hero {
     
    String name; //姓名
     
    float hp; //血量
     
    float armor; //护甲
     
    int moveSpeed; //移动速度
     
    //这个无参的构造方法，如果不写，
    //就会默认提供一个无参的构造方法
    //  public Hero(){ 
    //      System.out.println("调用Hero的构造方法");
    //  }
 
    public static void main(String[] args) {
        Hero garen =  new Hero();
        garen.name = "盖伦";
        garen.hp = 616.28f;
        garen.armor = 27.536f;
        garen.moveSpeed = 350;
         
        Hero teemo =  new Hero();
        teemo.name = "提莫";
        teemo.hp = 383f;
        teemo.armor = 14f;
        teemo.moveSpeed = 330;
    }  
     
}
```



 步骤 **3** : 

##### 如果提供了一个有参的构造方法

[**顶**](https://how2j.cn/k/class-object/class-object-constructor/292.html#)[**折**](https://how2j.cn/k/class-object/class-object-constructor/292.html#nowhere)

一旦提供了一个有参的构造方法
同时又**没有显式**的提供一个无参的构造方法
那么默认的无参的构造方法，就“木有了“

代码比较复制代码

```java
public class Hero {
      
    String name; //姓名
      
    float hp; //血量
      
    float armor; //护甲
      
    int moveSpeed; //移动速度
      
    //有参的构造方法
    //默认的无参的构造方法就失效了
    public Hero(String heroname){ 
        name = heroname;
    }
      
    public static void main(String[] args) {
        Hero garen =  new Hero("盖伦"); 
          
        Hero teemo =  new Hero(); //无参的构造方法“木有了”
    }  
      
}
```



 步骤 **4** : 

##### 构造方法的重载

[**顶**](https://how2j.cn/k/class-object/class-object-constructor/292.html#)[**折**](https://how2j.cn/k/class-object/class-object-constructor/292.html#nowhere)

和普通方法一样，构造方法也可以重载

代码比较复制代码

```java
public class Hero {
       
    String name; //姓名
       
    float hp; //血量
       
    float armor; //护甲
       
    int moveSpeed; //移动速度
       
    //带一个参数的构造方法
    public Hero(String heroname){ 
        name = heroname;
    }
     
    //带两个参数的构造方法
    public Hero(String heroname,float herohp){ 
        name = heroname;
        hp = herohp;
    }
       
    public static void main(String[] args) {
        Hero garen =  new Hero("盖伦"); 
        Hero teemo =  new Hero("提莫",383);
    }
     
}
```



 步骤 **5** : 

##### 练习-构造方法 

  [**顶**](https://how2j.cn/k/class-object/class-object-constructor/292.html#)[**折**](https://how2j.cn/k/class-object/class-object-constructor/292.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/class-object/class-object-constructor/292.html#nowhere)

为Hero设计4个参数的构造方法
这四个参数分别是
String heroName
float heroHP
float heroArmor
int heroMoveSpeed

---

#### this

this这个关键字，相当于普通话里的“**我**”

小明说 “我吃了” 这个时候，“**我**” 代表小明
小红说 “我吃了” 这个时候，“**我**” 代表小红
"**我**"代表当前人物

**this**这个关键字，相当于普通话里的“**我**”
**this即代表当前对象**

 步骤 **1** : 

##### this代表当前对象

[**顶**](https://how2j.cn/k/class-object/class-object-this/294.html#)[**折**](https://how2j.cn/k/class-object/class-object-this/294.html#nowhere)

![this代表当前对象](https://stepimagewm.how2j.cn/597.png)

代码比较复制代码

```java
public class Hero {
     
    String name; //姓名
     
    float hp; //血量
     
    float armor; //护甲
     
    int moveSpeed; //移动速度
 
    //打印内存中的虚拟地址
    public void showAddressInMemory(){
        System.out.println("打印this看到的虚拟地址："+this);
    }
     
    public static void main(String[] args) {
        Hero garen =  new Hero();
        garen.name = "盖伦";
        //直接打印对象，会显示该对象在内存中的虚拟地址
        //格式：Hero@c17164 c17164即虚拟地址，每次执行，得到的地址不一定一样
 
        System.out.println("打印对象看到的虚拟地址："+garen);
        //调用showAddressInMemory，打印该对象的this，显示相同的虚拟地址
        garen.showAddressInMemory();
         
        Hero teemo =  new Hero();
        teemo.name = "提莫";
        System.out.println("打印对象看到的虚拟地址："+teemo);
        teemo.showAddressInMemory();
    }  
     
}
```



 步骤 **2** : 

##### 通过this访问属性

[**顶**](https://how2j.cn/k/class-object/class-object-this/294.html#)[**折**](https://how2j.cn/k/class-object/class-object-this/294.html#nowhere)

通过this关键字访问对象的属性

代码比较复制代码

```java
public class Hero {
     
    String name; //姓名
     
    float hp; //血量
     
    float armor; //护甲
     
    int moveSpeed; //移动速度
 
    //参数名和属性名一样
    //在方法体中，只能访问到参数name
    public void setName1(String name){
        name = name;
    }
     
    //为了避免setName1中的问题，参数名不得不使用其他变量名
    public void setName2(String heroName){
        name = heroName;
    }
     
    //通过this访问属性
    public void setName3(String name){
        //name代表的是参数name
        //this.name代表的是属性name
        this.name = name;
    }
     
    public static void main(String[] args) {
        Hero  h =new Hero();
         
        h.setName1("teemo");
        System.out.println(h.name);
         
        h.setName2("garen");
        System.out.println(h.name);    
         
        h.setName3("死歌");
        System.out.println(h.name);    
    }
     
}
```



 步骤 **3** : 

##### 通过this调用其他的构造方法

[**顶**](https://how2j.cn/k/class-object/class-object-this/294.html#)[**折**](https://how2j.cn/k/class-object/class-object-this/294.html#nowhere)

如果要在一个构造方法中，调用另一个构造方法，可以使用this()

代码比较复制代码

```java
public class Hero {
        
    String name; //姓名
        
    float hp; //血量
        
    float armor; //护甲
        
    int moveSpeed; //移动速度
        
    //带一个参数的构造方法
    public Hero(String name){
        System.out.println("一个参数的构造方法");
        this.name = name;
    }
      
    //带两个参数的构造方法
    public Hero(String name,float hp){
        this(name);
        System.out.println("两个参数的构造方法");
        this.hp = hp;
    }
 
    public static void main(String[] args) {
        Hero teemo =  new Hero("提莫",383);
         
        System.out.println(teemo.name);
         
    }
      
}
```



 步骤 **4** : 

##### 练习-构造方法(this) 

  [**顶**](https://how2j.cn/k/class-object/class-object-this/294.html#)[**折**](https://how2j.cn/k/class-object/class-object-this/294.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/class-object/class-object-this/294.html#nowhere)

参考[练习-构造方法](https://how2j.cn/k/class-object/class-object-constructor/292.html#step2209) 设计一个构造方法,但是参数名称不太一样，分别是
String name
float hp
float armor
int moveSpeed

不仅如此，在这个构造方法中，调用这个构造方法

 

public Hero(String name,float hp)

---

#### 传参

#### 包

#### 访问修饰符

#### 类属性

#### 类方法

#### 属性初始化

#### 单例模式

#### 枚举类型