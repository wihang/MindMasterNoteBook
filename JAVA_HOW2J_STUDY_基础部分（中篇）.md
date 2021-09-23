#  JAVA_HOW2J_STUDY_基础部分（中篇）

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

变量有两种类型 基本类型 和类类型



 步骤 **1** : 

##### 基本类型传参

[**顶**](https://how2j.cn/k/class-object/class-object-parameter/293.html#)[**折**](https://how2j.cn/k/class-object/class-object-parameter/293.html#nowhere)

基本类型传参
在方法内，无法修改方法外的基本类型参数

代码比较复制代码

```java
public class Hero {
        
    String name; //姓名
        
    float hp; //血量
        
    float armor; //护甲
        
    int moveSpeed; //移动速度
     
    public Hero(){
         
    }
     
    //回血
    public void huixue(int xp){
        hp = hp + xp;
        //回血完毕后，血瓶=0
        xp=0;
    }
      
    public Hero(String name,float hp){
        this.name = name;
        this.hp = hp;
    }
 
    public static void main(String[] args) {
        Hero teemo =  new Hero("提莫",383);
        //血瓶，其值是100
        int xueping = 100;
         
        //提莫通过这个血瓶回血
         
        teemo.huixue(xueping);
         
        System.out.println(xueping);
         
    }
      
}
```



 步骤 **2** : 

##### 引用与=

[**顶**](https://how2j.cn/k/class-object/class-object-parameter/293.html#)[**折**](https://how2j.cn/k/class-object/class-object-parameter/293.html#nowhere)

如果一个变量是基本类型
比如 int hp = 50;
我们就直接管hp叫变量
**=表示赋值的意思**。
如果一个变量是类类型
比如 Hero h = new Hero();
我们就管h叫做**引用**。
**=不再是赋值的意思**
**=表示指向的意思**
比如 Hero h = new Hero();
这句话的意思是
引用h，指向一个Hero对象



 步骤 **3** : 

##### 类类型传参

[**顶**](https://how2j.cn/k/class-object/class-object-parameter/293.html#)[**折**](https://how2j.cn/k/class-object/class-object-parameter/293.html#nowhere)

**类类型又叫引用**
第24行的引用 **teemo**与 第17行的引用**hero**，**是不同的引用**
通过调用garen.attack(teemo, 100); 使得这**两个引用都指向了同一个对象**
所以在第18行hero.hp = hero.hp - damage; 就使得该对象的hp值，发生了变化
因此第25行，打印该对象的Hp值就是变化后的值

![类类型传参](https://stepimagewm.how2j.cn/595.png)

代码比较复制代码

```java
public class Hero {
 
    String name; // 姓名
 
    float hp; // 血量
 
    float armor; // 护甲
 
    int moveSpeed; // 移动速度
 
    public Hero(String name, float hp) {
        this.name = name;
        this.hp = hp;
    }
 
    // 攻击一个英雄，并让他掉damage点血
    public void attack(Hero hero, int damage) {
        hero.hp = hero.hp - damage;
    }
 
    public static void main(String[] args) {
        Hero teemo = new Hero("提莫", 383);
        Hero garen = new Hero("盖伦", 616);
        garen.attack(teemo, 100);
        System.out.println(teemo.hp);
    }
 
}
```



 步骤 **4** : 

##### 练习-传参 

  [**顶**](https://how2j.cn/k/class-object/class-object-parameter/293.html#)[**折**](https://how2j.cn/k/class-object/class-object-parameter/293.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/class-object/class-object-parameter/293.html#nowhere)

在方法中，使参数引用指向一个新的对象

外面的引用是指向原来的对象？还是新的对象？

代码比较复制代码

```java
public class Hero {
        
    String name; //姓名
        
    float hp; //血量
        
    float armor; //护甲
        
    int moveSpeed; //移动速度
     
    public Hero(){
         
    }
     
    public Hero(String name,float hp){
        this.name = name;
        this.hp = hp;
    }
 
    //复活
    public void revive(Hero h){
        h = new Hero("提莫",383);
    }
 
    public static void main(String[] args) {
        Hero teemo =  new Hero("提莫",383);
         
        //受到400伤害，挂了
        teemo.hp = teemo.hp - 400;
         
        teemo.revive(teemo);
         
        //问题： System.out.println(teemo.hp); 输出多少？ 怎么理解？
         
    }
      
}
```

---

#### 包

把比较接近的类，规划在同一个包下

 步骤 **1** : 

##### 把比较接近的类，规划在同一个包下

[**顶**](https://how2j.cn/k/class-object/class-object-package/299.html#)[**折**](https://how2j.cn/k/class-object/class-object-package/299.html#nowhere)

Hero,ADHero 规划在一个包，叫做charactor（角色）
Item,Weapon规划在另一个包下，叫做 property(道具)
在最开始的地方声明该类所处于的包名

![把比较接近的类，规划在同一个包下](https://stepimagewm.how2j.cn/600.png)

代码比较复制代码

```java
package charactor; //在最开始的地方声明该类所处于的包名
public class Hero {
        
    String name; //姓名
        
    float hp; //血量
        
    float armor; //护甲
        
    int moveSpeed; //移动速度
     
}
```



 步骤 **2** : 

##### 使用其他包下的类，必须import

[**顶**](https://how2j.cn/k/class-object/class-object-package/299.html#)[**折**](https://how2j.cn/k/class-object/class-object-package/299.html#nowhere)

使用同一个包下的其他类，直接使用即可
但是要使用其他包下的类，必须import

代码比较复制代码

```java
package charactor;
 
//Weapon类在其他包里，使用必须进行import
import property.Weapon;
 
public class Hero {
        
    String name; //姓名
        
    float hp; //血量
        
    float armor; //护甲
        
    int moveSpeed; //移动速度
     
    //装备一把武器
    public void equip(Weapon w){
         
    }
        
}
```



 步骤 **3** : 

##### 练习-包 

  创建一个新的包charactor1,并且让[练习-治疗类](https://how2j.cn/k/class-object/class-object-overload/291.html#step2206)：Support 声明在这个包下

#### 访问修饰符

成员变量有四种修饰符
**private** 私有的
**package**/friendly/default 不写
**protected** 受保护的
**public** 公共的

比如public 表示公共的

```tex
public String name;
```

而maxHP 没有修饰符即代表package/friendly/default

```tex
float maxHP
```

 示例 **1** : 

##### 类之间的关系

[**顶**](https://how2j.cn/k/class-object/class-object-modifier/295.html#)[**折**](https://how2j.cn/k/class-object/class-object-modifier/295.html#nowhere)

类和类之间的关系有如下几种:
以Hero为例
**自身：**指的是Hero自己
**同包子类：**ADHero这个类是Hero的子类，并且和Hero处于**同一个包下**
**不同包子类：**Support这个类是Hero的子类，但是在**另一个包下**
**同包类：** GiantDragon 这个类和Hero是**同一个包**，但是彼此**没有继承关系**
**其他类：**Item这个类，**在不同包**，也没有继承关系的类

![类之间的关系](https://stepimagewm.how2j.cn/605.png)



 示例 **2** : 

##### private 私有的

[**顶**](https://how2j.cn/k/class-object/class-object-modifier/295.html#)[**折**](https://how2j.cn/k/class-object/class-object-modifier/295.html#nowhere)

使用private修饰属性
自身：是可以访问的
同包子类：不能继承
不同包子类：不能继承
同包类：不能访问
其他包类：不能访问

**注：** 红色字体，表示不可行

![private 私有的](https://stepimagewm.how2j.cn/604.png)

代码比较复制代码

```java
package charactor;
 
import property.Weapon;
 
public class Hero {
 
    //属性id是private的，只有Hero自己可以访问
    //子类不能继承
    //其他类也不能访问
    private int id;
     
    String name;
 
    float hp;
 
    float armor;
 
    int moveSpeed;
 
    public void equip(Weapon w) {
 
    }
 
}
```



 示例 **3** : 

##### package/friendly/default 不写

[**顶**](https://how2j.cn/k/class-object/class-object-modifier/295.html#)[**折**](https://how2j.cn/k/class-object/class-object-modifier/295.html#nowhere)

没有修饰符即代表package/friendly/default
float maxHP; 血量上限

![package/friendly/default 不写](https://stepimagewm.how2j.cn/609.png)

代码比较复制代码

```java
package charactor;
 
import property.Weapon;
 
public class Hero {
    private int id;
 
    String name;
 
    // 无修饰符的属性 hp
    // 自己可以访问
 
    // 同包子类可以继承
    // 不同包子类不能继承
 
    // 同包类可以访问
    // 不同包类不能访问
    float hp;
 
    float armor;
 
    int moveSpeed;
 
    public void equip(Weapon w) {
 
    }
 
}
```



 示例 **4** : 

##### protected 受保护的

[**顶**](https://how2j.cn/k/class-object/class-object-modifier/295.html#)[**折**](https://how2j.cn/k/class-object/class-object-modifier/295.html#nowhere)

受保护的修饰符
protected float hp; 血量

![protected 受保护的](https://stepimagewm.how2j.cn/610.png)

代码比较复制代码

```java
package charactor;
 
import property.Weapon;
 
public class Hero {
    private int id;
 
    String name;
 
    // protected饰符的属性 hp
    // 自己可以访问
 
    // 同包子类可以继承
    // 不同包子类可以继承
 
    // 同包类可以访问
    // 不同包类不能访问
    protected float hp;
 
    float armor;
 
    int moveSpeed;
 
    public void equip(Weapon w) {
 
    }
 
}
```



 示例 **5** : 

##### public 公共的

[**顶**](https://how2j.cn/k/class-object/class-object-modifier/295.html#)[**折**](https://how2j.cn/k/class-object/class-object-modifier/295.html#nowhere)

公共的修饰符
public String name; 姓名
任何地方，都可以访问

![public 公共的](https://stepimagewm.how2j.cn/611.png)

代码比较复制代码

```java
package charactor;
 
import property.Weapon;
 
public class Hero {
    private int id;
 
    // public的属性 name
    // 自己可以访问
 
    // 同包子类可以继承
    // 不同包子类可以继承
 
    // 同包类可以访问
    // 不同包类可以访问
    public String name;
 
    protected float hp;
 
    float armor;
 
    int moveSpeed;
 
    public void equip(Weapon w) {
 
    }
 
}
```



 示例 **6** : 

##### 总结

[**顶**](https://how2j.cn/k/class-object/class-object-modifier/295.html#)[**折**](https://how2j.cn/k/class-object/class-object-modifier/295.html#nowhere)

![总结](https://stepimagewm.how2j.cn/612.png)

 示例 **7** : 

##### 那么什么情况该用什么修饰符呢？

[**顶**](https://how2j.cn/k/class-object/class-object-modifier/295.html#)[**折**](https://how2j.cn/k/class-object/class-object-modifier/295.html#nowhere)

那么什么情况该用什么修饰符呢？
从作用域来看，public能够使用所有的情况。 但是大家在工作的时候，又不会真正全部都使用public,那么到底什么情况该用什么修饰符呢？

\1. 属性通常使用private封装起来
\2. 方法一般使用public用于被调用
\3. 会被子类继承的方法，通常使用protected
\4. package用的不多，一般新手会用package,因为还不知道有修饰符这个东西

再就是**作用范围最小原则**
简单说，能用private就用private，不行就放大一级，用package,再不行就用protected，最后用public。 这样就能把数据尽量的封装起来，没有必要**露出来的**，就不用**露出来**了

#### 类属性

当一个属性被**static**修饰的时候，就叫做**类属性**，又叫做**静态属性**
当一个属性被声明成类属性，那么**所有的对象，都共享一个值**
与对象属性对比：
不同对象的 对象属性 的值都可能不一样。
比如盖伦的hp 和 提莫的hp 是不一样的。
但是所有对象的类属性的值，都是一样的

 步骤 **1** : 

##### 类属性

[**顶**](https://how2j.cn/k/class-object/class-object-class-attribute/296.html#)[**折**](https://how2j.cn/k/class-object/class-object-class-attribute/296.html#nowhere)

**类属性：** 又叫做静态属性
**对象属性：** 又叫实例属性，非静态属性
如果一个属性声明成类属性，那么所有的对象，都共享这么一个值
给英雄设置一个类属性叫做“版权" (copyright), 无论有多少个具体的英雄，所有的英雄的版权都属于 Riot Games公司。

代码比较复制代码

```java
package charactor;
 
public class Hero {
    public String name; //实例属性，对象属性，非静态属性
    protected float hp;
    static String copyright;//类属性,静态属性
     
    public static void main(String[] args) {
           Hero garen =  new Hero();
           garen.name = "盖伦";
            
           Hero.copyright = "版权由Riot Games公司所有";
            
           System.out.println(garen.name);
           System.out.println(garen.copyright);
            
           Hero teemo =  new Hero();
           teemo.name = "提莫";
           System.out.println(teemo.name);    
           System.out.println(teemo.copyright);
         
    }
     
}
```



 步骤 **2** : 

##### 访问类属性

[**顶**](https://how2j.cn/k/class-object/class-object-class-attribute/296.html#)[**折**](https://how2j.cn/k/class-object/class-object-class-attribute/296.html#nowhere)

访问类属性有两种方式
\1. 对象.类属性

 

teemo.copyright

 


\2. 类.类属性

 

Hero.copyright

 



这两种方式都可以访问类属性，访问即修改和获取，但是建议使用第二种 **类.类属性** 的方式进行，这样更符合语义上的理解



 步骤 **3** : 

##### 什么时候使用对象属性，什么时候使用类属性

[**顶**](https://how2j.cn/k/class-object/class-object-class-attribute/296.html#)[**折**](https://how2j.cn/k/class-object/class-object-class-attribute/296.html#nowhere)

如果一个属性，每个英雄都不一样，比如name，这样的属性就应该设计为对象属性，因为它是**跟着对象走的**，每个对象的name都是不同的

如果一个属性，**所有的英雄都共享**，都是一样的，那么就应该设计为类属性。比如血量上限，所有的英雄的血量上限都是 9999，不会因为英雄不同，而取不同的值。 这样的属性，就适合设计为类属性



 步骤 **4** : 

##### 练习-类属性 

  [**顶**](https://how2j.cn/k/class-object/class-object-class-attribute/296.html#)[**折**](https://how2j.cn/k/class-object/class-object-class-attribute/296.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/class-object/class-object-class-attribute/296.html#nowhere)

通过garen.copyright修改其值

 

garen.copyright = "Blizzard Entertainment Enterprise";

 


然后打印teemo.copyright，观察是否有变化

#### 类方法

**类方法：** 又叫做静态方法

**对象方法：** 又叫实例方法，非静态方法

访问一个对象方法，必须**建立在有一个对象**的前提的基础上
访问类方法，**不需要对象**的存在，直接就访问

 步骤 **1** : 

##### 类方法

[**顶**](https://how2j.cn/k/class-object/class-object-class-method/306.html#)[**折**](https://how2j.cn/k/class-object/class-object-class-method/306.html#nowhere)

**类方法：** 又叫做静态方法

**对象方法：** 又叫实例方法，非静态方法

访问一个对象方法，必须**建立在有一个对象**的前提的基础上
访问类方法，**不需要对象**的存在，直接就访问

代码比较复制代码

```java
package charactor;
 
public class Hero {
    public String name;
    protected float hp;
 
    //实例方法,对象方法，非静态方法
    //必须有对象才能够调用
    public void die(){
        hp = 0;
    }
     
    //类方法，静态方法
    //通过类就可以直接调用
    public static void battleWin(){
        System.out.println("battle win");
    }
     
    public static void main(String[] args) {
           Hero garen =  new Hero();
           garen.name = "盖伦";
           //必须有一个对象才能调用
           garen.die();
            
           Hero teemo =  new Hero();
           teemo.name = "提莫";
            
           //无需对象，直接通过类调用
           Hero.battleWin();
         
    }
}
```



 步骤 **2** : 

##### 调用类方法

[**顶**](https://how2j.cn/k/class-object/class-object-class-method/306.html#)[**折**](https://how2j.cn/k/class-object/class-object-class-method/306.html#nowhere)

和[访问类属性](https://how2j.cn/k/class-object/class-object-class-attribute/296.html#step2259)一样，调用类方法也有两种方式
\1. 对象.类方法

 

garen.battleWin();

 


\2. 类.类方法

 

Hero.battleWin();

 



这两种方式都可以调用类方法，但是建议使用第二种 类.类方法 的方式进行，这样更符合语义上的理解。
并且在很多时候，并没有实例，比如在前面练习的时候用到的[随机数的获取办法](https://how2j.cn/k/array/array-create/280.html#step2182)

 

Math.random()

 


random()就是一个类方法，直接通过类Math进行调用，并没有一个Math的实例存在。



 步骤 **3** : 

##### 什么时候设计对象方法，什么时候设计类方法

[**顶**](https://how2j.cn/k/class-object/class-object-class-method/306.html#)[**折**](https://how2j.cn/k/class-object/class-object-class-method/306.html#nowhere)

如果在某一个方法里，调用了对象属性，比如

 

​    public String getName(){

​    	return name;

​    }

 


name属性是对象属性，只有存在一个具体对象的时候，name才有意义。 如果方法里访问了对象属性，那么这个方法，就必须设计为对象方法

如果一个方法，没有调用任何对象属性，那么就可以考虑设计为类方法，比如

 

​    public static void printGameDuration(){

​    	System.out.println("已经玩了10分50秒");

​    }

 


printGameDuration 打印当前玩了多长时间了，不和某一个具体的英雄关联起来，所有的英雄都是一样的。 这样的方法，更带有**功能性**色彩
就像取随机数一样，random()是一个功能用途的方法

 

Math.random()

 



 步骤 **4** : 

##### 练习-类方法 

  [**顶**](https://how2j.cn/k/class-object/class-object-class-method/306.html#)[**折**](https://how2j.cn/k/class-object/class-object-class-method/306.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/class-object/class-object-class-method/306.html#nowhere)

在一个类方法中，直接调用一个对象方法，
比如在battleWin中调用die()
能否直接调用？ 为什么？

---

#### 属性初始化

步骤 **1** : 

##### 对象属性初始化

[**顶**](https://how2j.cn/k/class-object/class-object-init/297.html#)[**折**](https://how2j.cn/k/class-object/class-object-init/297.html#nowhere)

对象属性初始化有3种
\1. 声明该属性的时候初始化
\2. 构造方法中初始化
\3. 初始化块

代码比较复制代码

```java
package charactor;
 
public class Hero {
    public String name = "some hero"; //声明该属性的时候初始化
    protected float hp;
    float maxHP;
     
    {
        maxHP = 200; //初始化块
    }  
     
    public Hero(){
        hp = 100; //构造方法中初始化
         
    }
     
}
```



 步骤 **2** : 

##### 类属性初始化

[**顶**](https://how2j.cn/k/class-object/class-object-init/297.html#)[**折**](https://how2j.cn/k/class-object/class-object-init/297.html#nowhere)

类属性初始化有2种
\1. 声明该属性的时候初始化
\2. 静态初始化块

代码比较复制代码

```java
package charactor;
 
public class Hero {
    public String name;
    protected float hp;
    float maxHP;
     
    //物品栏的容量
    public static int itemCapacity=8; //声明的时候 初始化
     
    static{
        itemCapacity = 6;//静态初始化块 初始化
    }
     
    public Hero(){
         
    }
     
    public static void main(String[] args) {
        System.out.println(Hero.itemCapacity);
    }
     
}
```



 步骤 **3** : 

##### 练习-属性初始化 

  [**顶**](https://how2j.cn/k/class-object/class-object-init/297.html#)[**折**](https://how2j.cn/k/class-object/class-object-init/297.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/class-object/class-object-init/297.html#nowhere)

对象属性的初始化有三种方式
故意把初始化块，放在构造方法下面，问题：

这三种方式，谁先执行？谁后执行？

代码比较复制代码

```java
package charactor;
 
public class Hero {
    public String name = "some hero"; 
     
    public Hero(){
        name = "one hero";
    }
    {
        name = "the hero";
    }
     
}
```

---

#### 单例模式

[步骤 **1** : 单例模式  ](https://how2j.cn/k/class-object/class-object-singleton/349.html#step5904)
[步骤 **2** : 饿汉式单例模式  ](https://how2j.cn/k/class-object/class-object-singleton/349.html#step753)
[步骤 **3** : 懒汉式单例模式  ](https://how2j.cn/k/class-object/class-object-singleton/349.html#step2216)
[步骤 **4** : 什么时候使用饿汉式，什么时候使用懒汉式  ](https://how2j.cn/k/class-object/class-object-singleton/349.html#step2257)
[步骤 **5** : 单例模式三元素  ](https://how2j.cn/k/class-object/class-object-singleton/349.html#step2263)
[步骤 **6** : 练习-单例模式     ](https://how2j.cn/k/class-object/class-object-singleton/349.html#step2217)
[步骤 **7** : 答案-单例模式   ](https://how2j.cn/k/class-object/class-object-singleton/349.html#step2264)



 步骤 **1** : 

##### 单例模式

[**顶**](https://how2j.cn/k/class-object/class-object-singleton/349.html#)[**折**](https://how2j.cn/k/class-object/class-object-singleton/349.html#nowhere)

单例模式又叫做 Singleton模式，指的是一个类，在一个JVM里，只有一个实例存在。



 步骤 **2** : 

##### 饿汉式单例模式

[**顶**](https://how2j.cn/k/class-object/class-object-singleton/349.html#)[**折**](https://how2j.cn/k/class-object/class-object-singleton/349.html#nowhere)

GiantDragon 应该只有一只，通过私有化其构造方法，使得外部无法通过new 得到新的实例。
GiantDragon 提供了一个public static的getInstance方法，外部调用者通过该方法获取12行定义的对象，而且每一次都是获取同一个对象。 从而达到单例的目的。
这种单例模式又叫做**饿汉式**单例模式，无论如何都会创建一个实例

- [GiantDragon.java](https://how2j.cn/k/class-object/class-object-singleton/349.html#nowhere)

  - ```java
    package charactor;
     
    public class GiantDragon {
     
        //私有化构造方法使得该类无法在外部通过new 进行实例化
        private GiantDragon(){
             
        }
     
        //准备一个类属性，指向一个实例化对象。 因为是类属性，所以只有一个
     
        private static GiantDragon instance = new GiantDragon();
         
        //public static 方法，提供给调用者获取12行定义的对象
        public static GiantDragon getInstance(){
            return instance;
        }
         
    }
    ```

- [TestGiantDragon.java](https://how2j.cn/k/class-object/class-object-singleton/349.html#nowhere)

  - ```java
    package charactor;
     
    public class TestGiantDragon {
     
        public static void main(String[] args) {
            //通过new实例化会报错
    //      GiantDragon g = new GiantDragon();
             
            //只能通过getInstance得到对象
             
            GiantDragon g1 = GiantDragon.getInstance();
            GiantDragon g2 = GiantDragon.getInstance();
            GiantDragon g3 = GiantDragon.getInstance();
             
            //都是同一个对象
            System.out.println(g1==g2);
            System.out.println(g1==g3);
        }
    }
    ```

 步骤 **3** : 

##### 懒汉式单例模式

[**顶**](https://how2j.cn/k/class-object/class-object-singleton/349.html#)[**折**](https://how2j.cn/k/class-object/class-object-singleton/349.html#nowhere)

**懒汉式**单例模式与**饿汉式**单例模式不同，只有在调用getInstance的时候，才会创建实例

- [GiantDragon.java](https://how2j.cn/k/class-object/class-object-singleton/349.html#nowhere)

  - ```java
    package charactor;
     
    public class GiantDragon {
      
        //私有化构造方法使得该类无法在外部通过new 进行实例化
        private GiantDragon(){       
        }
      
        //准备一个类属性，用于指向一个实例化对象，但是暂时指向null
        private static GiantDragon instance;
          
        //public static 方法，返回实例对象
        public static GiantDragon getInstance(){
            //第一次访问的时候，发现instance没有指向任何对象，这时实例化一个对象
            if(null==instance){
                instance = new GiantDragon();
            }
            //返回 instance指向的对象
            return instance;
        }
          
    }
    ```

- [TestGiantDragon.java](https://how2j.cn/k/class-object/class-object-singleton/349.html#nowhere)

  - ```java
    package charactor;
     
    public class TestGiantDragon {
     
        public static void main(String[] args) {
            //通过new实例化会报错
    //      GiantDragon g = new GiantDragon();
             
            //只能通过getInstance得到对象
             
            GiantDragon g1 = GiantDragon.getInstance();
            GiantDragon g2 = GiantDragon.getInstance();
            GiantDragon g3 = GiantDragon.getInstance();
             
            //都是同一个对象
            System.out.println(g1==g2);
            System.out.println(g1==g3);
        }
    }

 步骤 **4** : 

##### 什么时候使用饿汉式，什么时候使用懒汉式

[**顶**](https://how2j.cn/k/class-object/class-object-singleton/349.html#)[**折**](https://how2j.cn/k/class-object/class-object-singleton/349.html#nowhere)

**饿汉式**是立即加载的方式，无论是否会用到这个对象，都会加载。
如果在构造方法里写了性能消耗较大，占时较久的代码，比如建立与数据库的连接，那么就会在启动的时候感觉稍微有些卡顿。

**懒汉式**，是延迟加载的方式，只有使用的时候才会加载。 并且有[线程安全](https://how2j.cn/k/thread/thread-synchronized/355.html#step793)的考量(鉴于同学们学习的进度，暂时不对线程的章节做展开)。
使用懒汉式，在启动的时候，会感觉到比饿汉式略快，因为并没有做对象的实例化。 但是在第一次调用的时候，会进行实例化操作，感觉上就略慢。

看业务需求，如果业务上允许有比较充分的启动和初始化时间，就使用饿汉式，否则就使用懒汉式



 步骤 **5** : 

##### 单例模式三元素

[**顶**](https://how2j.cn/k/class-object/class-object-singleton/349.html#)[**折**](https://how2j.cn/k/class-object/class-object-singleton/349.html#nowhere)

这个是面试的时候经常会考的点，面试题通常的问法是:

 

什么是单例模式？

 


回答的时候，要答到三元素
\1. 构造方法私有化
\2. 静态属性指向实例
\3. public static的 getInstance方法，返回第二步的静态属性



 步骤 **6** : 

##### 练习-单例模式 

  [**顶**](https://how2j.cn/k/class-object/class-object-singleton/349.html#)[**折**](https://how2j.cn/k/class-object/class-object-singleton/349.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/class-object/class-object-singleton/349.html#nowhere)

使用饿汉式单例模式, 把Hero类改造成为单例模式

使用懒汉式单例模式，把Item类改造成为单例模式

---

#### 枚举类型

 步骤 **1** : 

##### 预先定义的常量

[**顶**](https://how2j.cn/k/class-object/class-object-enum/678.html#)[**折**](https://how2j.cn/k/class-object/class-object-enum/678.html#nowhere)

枚举enum是一种特殊的类(还是类)，使用枚举可以很方便的定义常量
比如设计一个枚举类型 季节，里面有4种常量



 

public enum Season {

​	SPRING,SUMMER,AUTUMN,WINTER

}

 



一个常用的场合就是[switch](https://how2j.cn/k/control-flow/control-flow-switch/272.html)语句中，使用枚举来进行判断

**注：**因为是常量，所以一般都是全大写

- [HelloWorld.java](https://how2j.cn/k/class-object/class-object-enum/678.html#nowhere)

  - ```java
    public class HelloWorld {
        public static void main(String[] args) {
            Season season = Season.SPRING;
            switch (season) {
            case SPRING:
                System.out.println("春天");
                break;
            case SUMMER:
                System.out.println("夏天");
                break;
            case AUTUMN:
                System.out.println("秋天");
                break;
            case WINTER:
                System.out.println("冬天");
                break;
            }
        }
    }
    ```

- [Season.java](https://how2j.cn/k/class-object/class-object-enum/678.html#nowhere)

  - ```java
    public enum Season {
        SPRING,SUMMER,AUTUMN,WINTER
    }
    ```

 步骤 **2** : 

##### 使用枚举的好处

[**顶**](https://how2j.cn/k/class-object/class-object-enum/678.html#)[**折**](https://how2j.cn/k/class-object/class-object-enum/678.html#nowhere)

假设在使用[switch](https://how2j.cn/k/control-flow/control-flow-switch/272.html)的时候，不是使用枚举，而是使用int，而int的取值范围就不只是1-4，有可能取一个超出1-4之间的值，这样判断结果就似是而非了。（因为只有4个季节）

但是使用枚举，就能把范围死死的限定在这四个当中

 

SPRING,SUMMER,AUTUMN,WINTER

 


而不会出现奇怪的 **第5季**

代码比较复制代码

```java
public class HelloWorld {
    public static void main(String[] args) {
        int season = 5;
        switch (season) {
        case 1:
            System.out.println("春天");
            break;
        case 2:
            System.out.println("夏天");
            break;
        case 3:
            System.out.println("秋天");
            break;
        case 4:
            System.out.println("冬天");
            break;
        }
    }
}
```



 步骤 **3** : 

##### 遍历枚举

[**顶**](https://how2j.cn/k/class-object/class-object-enum/678.html#)[**折**](https://how2j.cn/k/class-object/class-object-enum/678.html#nowhere)

借助[增强型for循环](https://how2j.cn/k/array/array-foreach/330.html#step707)，可以很方便的遍历一个枚举都有哪些常量

代码比较复制代码

```java
public class HelloWorld {
    public static void main(String[] args) {
        for (Season s : Season.values()) {
            System.out.println(s);
        }
    }
}
```



 步骤 **4** : 

##### 练习-枚举 

  [**顶**](https://how2j.cn/k/class-object/class-object-enum/678.html#)[**折**](https://how2j.cn/k/class-object/class-object-enum/678.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/class-object/class-object-enum/678.html#nowhere)

英雄联盟中有这么一些分类
TANK (坦克)
WIZARD (法师 )
ASSASSIN (刺客)
ASSIST (辅助)
WARRIOR (近战)
RANGED (远程 )
PUSH (推进)
FARMING (打野)
设计一个枚举类型HeroType,使用上述分类作为常量

再编写一段switch语句，把每种枚举常量输出为中文字符串

```java
/*英雄联盟中有这么一些分类
        TANK (坦克)
        WIZARD (法师 )
        ASSASSIN (刺客)
        ASSIST (辅助)
        WARRIOR (近战)
        RANGED (远程 )
        PUSH (推进)
        FARMING (打野)
        设计一个枚举类型HeroType,使用上述分类作为常量
 
        再编写一段switch语句，把每种枚举常量输出为中文字符串*/
public enum HeroType {
    TANK, WIZARD,ASSASSIN,ASSIST,WARRIOR,RANGED,PUSH,FARMING
}
class Ok{
    public static void main(String[] args){
        for(HeroType jhn: HeroType.values()){
        switch(jhn) {
            case TANK:
                System.out.println("坦克");
                break;
            case WIZARD:
                System.out.println("法师");
                break;
            case ASSASSIN:
                System.out.println("刺客");
                break;
            case ASSIST:
                System.out.println("辅助");
                break;
            case WARRIOR:
                System.out.println("近战");
                break;
            case RANGED:
                System.out.println("远程");
                break;
            case PUSH:
                System.out.println("推进");
                break;
            case FARMING:
                System.out.println("打野");
                break;
        }
        }
    }
}
```

---

### 接口与继承

#### 接口

在设计LOL的时候，进攻类英雄有两种，一种是进行物理系攻击，一种是进行魔法系攻击

这时候，就可以使用**接口**来实现这个效果。

**接口就像是一种约定**，我们约定某些英雄是物理系英雄，那么他们就一定能够进行物理攻击。

 步骤 **1** : 

##### 物理攻击接口

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-interface/289.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-interface/289.html#nowhere)

创建一个接口 File->New->Interface
AD ，声明一个方法 physicAttack 物理攻击，但是没有方法体，是一个“**空**”方法

![物理攻击接口](https://stepimagewm.how2j.cn/586.png)

代码比较复制代码

```java
package charactor;
 
public interface AD {
        //物理伤害
    public void physicAttack();
}
```



 步骤 **2** : 

##### 设计一类英雄，能够使用物理攻击

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-interface/289.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-interface/289.html#nowhere)

设计一类英雄，能够使用物理攻击，这类英雄在LOL中被叫做AD
类：ADHero
继承了Hero 类，所以继承了name,hp,armor等属性

**实现某个接口，就相当于承诺了某种约定**

所以，**实现**了**AD**这个接口，就**必须**提供AD接口中声明的方法**physicAttack()**
**实现**在语法上使用关键字 **implements**

代码比较复制代码

```java
package charactor;
 
public class ADHero extends Hero implements AD{
 
    @Override
    public void physicAttack() {
        System.out.println("进行物理攻击");
    }
 
}	
```



 步骤 **3** : 

##### 魔法攻击接口

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-interface/289.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-interface/289.html#nowhere)

创建一个接口 File->New->Interface
AP ，声明一个方法 magicAttack 魔法攻击，但是没有方法体，是一个“空”方法

代码比较复制代码

```java
package charactor;
 
public interface AP {
 
    public void magicAttack();
}
```



 步骤 **4** : 

##### 设计一类英雄，只能使用魔法攻击

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-interface/289.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-interface/289.html#nowhere)

设计一类英雄，只能使用魔法攻击，这类英雄在LOL中被叫做AP
类：APHero
继承了Hero 类，所以继承了name,hp,armor等属性
同时，实现了**AP**这个接口，就**必须**提供AP接口中声明的方法magicAttack()
**实现**在语法上使用关键字 **implements**

代码比较复制代码

```java
package charactor;
 
public class APHero extends Hero implements AP{
 
    @Override
    public void magicAttack() {
        System.out.println("进行魔法攻击");
    }
 
}
```



 步骤 **5** : 

##### 设计一类英雄，既能进行物理攻击，又能进行魔法攻击

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-interface/289.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-interface/289.html#nowhere)

一种英雄，能够同时进行物理攻击和魔法攻击
比如伊泽瑞尔，皮城女警凯特琳

代码比较复制代码

```java
package charactor;
  
//同时能进行物理和魔法伤害的英雄
public class ADAPHero extends Hero implements AD,AP{
  
    @Override
    public void magicAttack() {
        System.out.println("进行魔法攻击");
    }
  
    @Override
    public void physicAttack() {
        System.out.println("进行物理攻击");
    }
  
}
```



 步骤 **6** : 

##### 什么样的情况下该使用接口?

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-interface/289.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-interface/289.html#nowhere)

如上的例子，似乎要接口，不要接口，都一样的，那么接口的意义是什么呢

学习一个知识点，是由浅入深得进行的。 这里呢，只是引入了接口的概念，要真正理解接口的好处，需要更多的实践，以及在较为复杂的系统中进行大量运用之后，才能够真正理解，比如在学习了[多态](https://how2j.cn/k/interface-inheritance/interface-inheritance-polymorphic/315.html)之后就能进一步加深理解。

刚刚接触一个概念，就希望达到炉火纯青的学习效果，这样的学习目标是不科学的。



 步骤 **7** : 

##### 练习-接口 

  [**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-interface/289.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-interface/289.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/interface-inheritance/interface-inheritance-interface/289.html#nowhere)

设计一个治疗者接口：Healer

该接口声明有方法： heal()

设计一个Support类，代表辅助英雄，继承Hero类，同时实现了Healer这个接口

#### 对象转型

示例 **1** : 

##### 明确引用类型与对象类型的概念

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-casting/308.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-casting/308.html#nowhere)

首先，明确引用类型与对象类型的概念
在这个例子里，有一个对象 new ADHero(), 同时也有一个引用ad
对象是有类型的， 是ADHero
引用也是有类型的，是ADHero
通常情况下，引用类型和对象类型是一样的
接下来要讨论的类型转换的问题，指的是**引用类型和对象类型**不一致的情况下的转换问题

![明确引用类型与对象类型的概念](https://stepimagewm.how2j.cn/636.png)

代码比较复制代码

```java
package charactor;
 
public class Hero {
    public String name;
    protected float hp;
     
    public static void main(String[] args) {
         
        ADHero ad = new ADHero();
         
    }
}
```



 示例 **2** : 

##### 子类转父类(向上转型) 

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-casting/308.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-casting/308.html#nowhere)

所谓的转型，是指当**引用类型**和**对象类型**不一致的时候，才需要进行类型转换
类型转换有时候会成功，有时候会失败(参考[基本类型的类型转换](https://how2j.cn/k/variable/variable-transfer/264.html))

到底能否转换成功？ 教大家一个很简单的判别办法
**把右边的当做左边来用**，看说得通不



 

Hero h = new Hero();

ADHero ad = new ADHero();

h = ad;

 



右边ad**引用所指向的对象的类型**是 物理攻击英雄
左边h**引用的类型**是 普通英雄
把物理攻击英雄 当做 普通英雄，说不说得通？ 说得通，就可以转

所有的**子类转换为父类**，都是说得通的。比如你身边的例子

苹果手机 继承了 手机，把苹果手机当做普通手机使用
怡宝纯净水 继承了 饮品， 把怡宝纯净水 当做饮品来使用
苍老师 继承了动物， 把苍老师 。。。

![子类转父类(向上转型)](https://stepimagewm.how2j.cn/624.png)

代码比较复制代码

```java
package charactor;
 
public class Hero {
    public String name;
    protected float hp;
     
    public static void main(String[] args) {
         
        Hero h = new Hero();
         
        ADHero ad = new ADHero();
         
        //类型转换指的是把一个引用所指向的对象的类型，转换为另一个引用的类型
         
        //把ad引用所指向的对象的类型是ADHero
        //h引用的类型是Hero
        //把ADHero当做Hero使用，一定可以
         
        h = ad;
         
    }
}
```





 示例 **3** : 

##### 父类转子类(向下转型)

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-casting/308.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-casting/308.html#nowhere)

父类转子类，有的时候行，有的时候不行，所以必须进行强制转换。
强制转换的意思就是 转换有风险，风险自担。

**什么时候行呢？**

 

\1.        Hero h =new Hero();

\2.        ADHero ad = new ADHero();

\3.        h = ad;

\4.        ad = (ADHero) h;

 


第3行，是子类转父类，一定可以的
第4行，就是父类转子类，所以要进行强转。
h这个引用，所指向的对象是ADHero, 所以第4行，就会把ADHero转换为ADHero，就能转换成功。

**什么时候转换不行呢？**

 

\1.        Hero h =new Hero();

\2.        ADHero ad = new ADHero();

\3.        Support s =new Support();

\4.        h = s;

\5.        ad = (ADHero)h;

 


第4行，是子类转父类，是可以转换成功的
第5行，是把h引用所指向的对象 Support，转换为ad引用的类型ADHero。 从语义上讲，把物理攻击英雄，当成辅助英雄来用，说不通，所以会强制转换失败，并且抛出[异常](https://how2j.cn/k/exception/exception-tutorial/332.html)

**以下是对完整的代码的关键行分析**
14行： 把ad当做Hero使用，一定可以
转换之后，h引用指向一个ad对象
15行： h引用有可能指向一个ad对象，也有可能指向一个support对象
所以把h引用转换成AD类型的时候，就有可能成功，有可能失败
因此要进行强制转换，换句话说转换后果自负
到底能不能转换成功，要看引用**h到底指向的是哪种对象**
在这个例子里，h指向的是一个ad对象，所以转换成ADHero类型，是可以的
16行：把一个support对象当做Hero使用，一定可以
转换之后，h引用指向一个support对象
17行：这个时候，h指向的是一个support对象，所以转换成ADHero类型，会失败。
失败的表现形式是抛出异常 ClassCastException 类型转换异常

![父类转子类(向下转型)](https://stepimagewm.how2j.cn/625.png)

代码比较复制代码

```java
package charactor;
  
import charactor1.Support;
  
public class Hero {
    public String name;
    protected float hp;
      
    public static void main(String[] args) {
        Hero h =new Hero();
        ADHero ad = new ADHero();
        Support s =new Support();
          
        h = ad;
        ad = (ADHero) h;
        h = s;
        ad = (ADHero)h;
    }
      
}
```



 示例 **4** : 

##### 没有继承关系的两个类，互相转换

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-casting/308.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-casting/308.html#nowhere)

没有继承关系的两个类，互相转换，一定会失败
虽然ADHero和APHero都继承了Hero，但是彼此没有互相继承关系
"**把魔法英雄当做物理英雄来用**",在语义上也是说不通的

![没有继承关系的两个类，互相转换](https://stepimagewm.how2j.cn/626.png)

代码比较复制代码

```java
package charactor;
 
public class Hero {
    public String name;
    protected float hp;
 
    public static void main(String[] args) {
        ADHero ad = new ADHero();
 
        APHero ap = new APHero();
 
        // 没有继承关系的类型进行互相转换一定会失败，所以会出现编译错误
        ad = (ADHero) ap;
 
    }
 
}
```



 示例 **5** : 

##### 实现类转换成接口(向上转型)

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-casting/308.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-casting/308.html#nowhere)

引用ad指向的对象是ADHero类型，这个类型实现了AD接口
10行： 把一个ADHero类型转换为AD接口
从语义上来讲，把一个ADHero当做AD来使用，而AD接口只有一个physicAttack方法，这就意味着转换后就有可能要调用physicAttack方法，而ADHero一定是有physicAttack方法的，所以转换是能成功的。

![实现类转换成接口(向上转型)](https://stepimagewm.how2j.cn/627.png)

代码比较复制代码

```java
package charactor;
   
public class Hero {
    public String name;
    protected float hp;
       
    public static void main(String[] args) {
        ADHero ad = new ADHero();
          
        AD adi = ad;
          
    }
       
}
```



 示例 **6** : 

##### 接口转换成实现类(向下转型)

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-casting/308.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-casting/308.html#nowhere)

10行： ad引用指向ADHero， 而adi引用是接口类型：AD，实现类转换为接口，是向上转型，所以无需强制转换，并且一定能成功
12行: adi实际上是指向一个ADHero的，所以能够转换成功
14行： adi引用所指向的对象是一个ADHero，要转换为ADAPHero就会失败。

**假设能够转换成功**，那么就可以使用**magicAttack**方法，而adi引用所指向的对象**ADHero****是****没有magicAttack**方法的。

![接口转换成实现类(向下转型)](https://stepimagewm.how2j.cn/628.png)

代码比较复制代码

```java
package charactor;
     
public class Hero {
    public String name;
    protected float hp;
         
    public static void main(String[] args) {
        ADHero ad = new ADHero();
            
        AD adi = ad;
   
        ADHero adHero = (ADHero) adi;
            
        ADAPHero adapHero = (ADAPHero) adi;
        adapHero.magicAttack();
    }
         
}
```



 示例 **7** : 

##### instanceof

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-casting/308.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-casting/308.html#nowhere)

instanceof Hero 判断一个引用所指向的对象，是否是Hero类型，或者Hero的子类

代码比较复制代码

```java
package charactor;
  
public class Hero {
    public String name;
    protected float hp;
      
    public static void main(String[] args) {
        ADHero ad = new ADHero();
        APHero ap = new APHero();
         
        Hero h1= ad;
        Hero h2= ap;
         
        //判断引用h1指向的对象，是否是ADHero类型
        System.out.println(h1 instanceof ADHero);
         
        //判断引用h2指向的对象，是否是APHero类型
        System.out.println(h2 instanceof APHero);
         
        //判断引用h1指向的对象，是否是Hero的子类型
        System.out.println(h1 instanceof Hero);
    }
}
```



 示例 **8** : 

##### 练习-类型转换 

  [**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-casting/308.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-casting/308.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/interface-inheritance/interface-inheritance-casting/308.html#nowhere)

如下转换能否成功？
如果不能，是哪一行会出错？
为什么会出错

代码比较复制代码

```java
package charactor;
 
public class Hero {
    public String name;
    protected float hp;
 
    public static void main(String[] args) {
        ADHero ad = new ADHero();
        Hero h = ad;
        AD adi = (AD) h;
        APHero ap = (APHero) adi;
    }
}
```

#### 重写

子类可以继承父类的对象方法

在继承后，重复提供该方法，就叫做方法的重写

又叫覆盖 override

步骤 **1** : 

##### 父类Item

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-override/309.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-override/309.html#nowhere)

父类Item有一个方法，叫做effect

代码比较复制代码

```java
package property;
 
public class Item {
    String name;
    int price;
 
    public void buy(){
        System.out.println("购买");
    }
    public void effect() {
        System.out.println("物品使用后，可以有效果");
    }
 
}
```



 步骤 **2** : 

##### 子类LifePotion

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-override/309.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-override/309.html#nowhere)

子类LifePotion继承Item,同时也提供了方法effect

代码比较复制代码

```java
package property;
 
public class LifePotion extends Item{
     
    public void effect(){
        System.out.println("血瓶使用后，可以回血");
    }
     
}
```



 步骤 **3** : 

##### 调用重写的方法

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-override/309.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-override/309.html#nowhere)

调用重写的方法
调用就会执行重写的方法，而不是从父类的方法
所以LifePotion的effect会打印：
"血瓶使用后，可以回血"

代码比较复制代码

```java
package property;
 
public class Item {
    String name;
    int price;
     
    public void effect(){
        System.out.println("物品使用后，可以有效果");
    }
     
    public static void main(String[] args) {
        Item i = new Item();
        i.effect();
         
        LifePotion lp =new LifePotion();
        lp.effect();
    }
     
}
```



 步骤 **4** : 

##### 如果没有重写这样的机制怎么样？

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-override/309.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-override/309.html#nowhere)

如果没有重写这样的机制，也就是说LifePotion这个类，一旦继承了Item，所有方法都不能修改了。

但是LifePotion又希望提供一点不同的功能，为了达到这个目的，只能**放弃继承Item**,重新编写所有的属性和方法，然后在编写effect的时候，做一点小改动.

这样就增加了开发时间和维护成本

- [Item.java](https://how2j.cn/k/interface-inheritance/interface-inheritance-override/309.html#nowhere)
- [LifePotion.java](https://how2j.cn/k/interface-inheritance/interface-inheritance-override/309.html#nowhere)

代码比较复制代码

```java
package property;
 
public class Item {
    String name;
    int price;
 
    public void buy(){
        System.out.println("购买");
    }
    public void effect() {
        System.out.println("物品使用后，可以有效果");
    }
 
}
```



 步骤 **5** : 

##### 练习-重写 

  [**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-override/309.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-override/309.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/interface-inheritance/interface-inheritance-override/309.html#nowhere)

设计一个类MagicPotion 蓝瓶，继承Item, 重写effect方法
并输出 “蓝瓶使用后，可以回魔法”

#### 多态

操作符的多态
\+ 可以作为算数运算，也可以作为字符串连接

类的多态
父类引用指向子类对象



 示例 **1** : 

##### 操作符的多态

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-polymorphic/315.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-polymorphic/315.html#nowhere)

同一个操作符在不同情境下，具备不同的作用
如果+号两侧都是整型，那么**+代表 数字相加**
如果+号两侧，任意一个是字符串，那么**+代表字符串连接**

```java
package charactor;
   
public class Hero {
    public String name;
    protected float hp;
 
    public static void main(String[] args) {
         
        int i = 5;
        int j = 6;
        int k = i+j; //如果+号两侧都是整型，那么+代表 数字相加
         
        System.out.println(k);
         
        int a = 5;
        String b = "5";
         
        String c = a+b; //如果+号两侧，任意一个是字符串，那么+代表字符串连接
        System.out.println(c);
         
    }
       
}
```

 示例 **2** : 

##### 观察类的多态现象

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-polymorphic/315.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-polymorphic/315.html#nowhere)

观察类的多态现象：
\1. i1和i2都是Item类型
\2. 都调用effect方法
\3. 输出不同的结果

多态: 都是同一个类型，调用同一个方法，却能呈现不同的状态

![观察类的多态现象](https://stepimagewm.how2j.cn/2272.png)

- [Item.java](https://how2j.cn/k/interface-inheritance/interface-inheritance-polymorphic/315.html#nowhere)

  - ```java
    package property;
     
    public class Item {
        String name;
        int price;
     
        public void buy(){
            System.out.println("购买");
        }
        public void effect() {
            System.out.println("物品使用后，可以有效果 ");
        }
         
        public static void main(String[] args) {
            Item i1= new LifePotion();
            Item i2 = new MagicPotion();
            System.out.print("i1  是Item类型，执行effect打印:");
            i1.effect();
            System.out.print("i2也是Item类型，执行effect打印:");
            i2.effect();
        }
     
    }
    ```

- [LifePotion.java](https://how2j.cn/k/interface-inheritance/interface-inheritance-polymorphic/315.html#nowhere)

  - ```java
    package property;
     
    public class LifePotion extends Item {
        public void effect(){
            System.out.println("血瓶使用后，可以回血");
        }
    }
    ```

- [MagicPotion.java](https://how2j.cn/k/interface-inheritance/interface-inheritance-polymorphic/315.html#nowhere)

  - ```java
    package property;
     
    public class MagicPotion extends Item{
     
        public void effect(){
            System.out.println("蓝瓶使用后，可以回魔法");
        }
    }
    ```

 示例 **3** : 

##### 类的多态条件

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-polymorphic/315.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-polymorphic/315.html#nowhere)

要实现类的多态，需要如下条件
\1. 父类（接口）引用指向子类对象
\2. 调用的方法有[重写](https://how2j.cn/k/interface-inheritance/interface-inheritance-override/309.html)
那么多态有什么作用呢？ 通过比较[不使用多态](https://how2j.cn/k/interface-inheritance/interface-inheritance-polymorphic/315.html#step643)与[使用多态](https://how2j.cn/k/interface-inheritance/interface-inheritance-polymorphic/315.html#step645)来进一步了解



 示例 **4** : 

##### 类的多态-不使用多态

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-polymorphic/315.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-polymorphic/315.html#nowhere)

**如果不使用多态**，
假设英雄要使用血瓶和魔瓶，就需要为Hero设计两个方法
useLifePotion
useMagicPotion


除了血瓶和魔瓶还有很多种物品，那么就需要设计很多很多个方法，比如
usePurityPotion 净化药水
useGuard 守卫
useInvisiblePotion 使用隐形药水
等等等等

代码比较复制代码

```java
package charactor;
 
import property.LifePotion;
import property.MagicPotion;
   
public class Hero {
    public String name;
    protected float hp;
 
    public void useLifePotion(LifePotion lp){
        lp.effect();
    }
    public void useMagicPotion(MagicPotion mp){
        mp.effect();
    }
 
    public static void main(String[] args) {
         
        Hero garen =  new Hero();
        garen.name = "盖伦";
     
        LifePotion lp =new LifePotion();
        MagicPotion mp =new MagicPotion();
         
        garen.useLifePotion(lp);
        garen.useMagicPotion(mp);
         
    }
       
}
```





 示例 **5** : 

##### 类的多态-使用多态

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-polymorphic/315.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-polymorphic/315.html#nowhere)

如果物品的种类特别多，那么就需要设计很多的方法
比如useArmor,useWeapon等等

这个时候采用多态来解决这个问题
设计一个方法叫做useItem，其参数类型是Item
如果是使用血瓶，调用该方法
如果是使用魔瓶，还是调用该方法
无论英雄要使用什么样的物品，**只需要一个方法**即可

代码比较复制代码

```java
package charactor;
 
import property.Item;
import property.LifePotion;
import property.MagicPotion;
   
public class Hero {
    public String name;
    protected float hp;
 
    public void useItem(Item i){
        i.effect();
    }
 
    public static void main(String[] args) {
         
        Hero garen =  new Hero();
        garen.name = "盖伦";
     
        LifePotion lp =new LifePotion();
        MagicPotion mp =new MagicPotion();
         
        garen.useItem(lp);
        garen.useItem(mp);     
         
    }
       
}
```



 示例 **6** : 

##### 练习-多态 

  [**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-polymorphic/315.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-polymorphic/315.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/interface-inheritance/interface-inheritance-polymorphic/315.html#nowhere)

 

immortal是不朽的，不死的意思

mortal就是终有一死的，凡人的意思

 


\1. 设计一个接口
接口叫做Mortal,其中有一个方法叫做die
\2. 实现接口
分别让ADHero,APHero,ADAPHero这三个类，实现Mortal接口，不同的类实现die方法的时候，都打印出不一样的字符串
\3. 为Hero类，添加一个方法,在这个方法中调用 m的die方法。

 

public void kill(Mortal m)

 


\4. 在主方法中
首先实例化出一个Hero对象:盖伦
然后实例化出3个对象，分别是ADHero,APHero,ADAPHero的实例
然后让盖伦 kill 这3个对象

#### 隐藏

与重写类似，方法的**重写是**子类覆盖父类的**对象方法**

**隐藏**，就是子类覆盖父类的**类方法**

 步骤 **1** : 

##### 父类

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-hide/310.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-hide/310.html#nowhere)

父类有一个类方法 ：battleWin

代码比较复制代码

```java
package charactor;
  
public class Hero {
    public String name;
    protected float hp;
  
    //类方法，静态方法
    //通过类就可以直接调用
    public static void battleWin(){
        System.out.println("hero battle win");
    }
      
}
```



 步骤 **2** : 

##### 子类隐藏父类的类方法

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-hide/310.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-hide/310.html#nowhere)

子类隐藏父类的类方法

代码比较复制代码

```java
package charactor;
  
public class ADHero extends Hero implements AD{
  
    @Override
    public void physicAttack() {
        System.out.println("进行物理攻击");
    }
     
    //隐藏父类的battleWin方法
    public static void battleWin(){
        System.out.println("ad hero battle win");
    }   
     
    public static void main(String[] args) {
        Hero.battleWin();
        ADHero.battleWin();
    }
  
}
```



 步骤 **3** : 

##### 练习-隐藏 

  [**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-hide/310.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-hide/310.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/interface-inheritance/interface-inheritance-hide/310.html#nowhere)

 

Hero h =new ADHero();

 


h.battleWin(); //battleWin是一个类方法
h是父类类型的引用
但是指向一个子类对象
h.battleWin(); 会调用父类的方法？还是子类的方法？

#### super

 步骤 **1** : 

##### 准备一个显式提供无参构造方法的父类

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-super/311.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-super/311.html#nowhere)

准备显式提供无参构造方法的父类
在实例化Hero对象的时候，其构造方法会打印
“Hero的构造方法 "

```java
package charactor;
 
import property.Item;
 
public class Hero {
        
    String name; //姓名
        
    float hp; //血量
        
    float armor; //护甲
        
    int moveSpeed; //移动速度
     
    public void useItem(Item i){
        System.out.println("hero use item");
        i.effect();
    }
     
    public Hero(){
        System.out.println("Hero的构造方法 ");
    }
     
    public static void main(String[] args) {
        new Hero();
    }
      
}
```



 步骤 **2** : 

##### 实例化子类，父类的构造方法一定会被调用

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-super/311.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-super/311.html#nowhere)

实例化一个ADHero(), 其构造方法会被调用
其**父类的构造方法也会被调用**
并且是父类构造方法**先调用**
子类构造方法会默认调用父类的 无参的构造方法

![实例化子类，父类的构造方法一定会被调用](https://stepimagewm.how2j.cn/662.png)

代码比较复制代码

```java
package charactor;
  
public class ADHero extends Hero implements AD{
  
    @Override
    public void physicAttack() {
        System.out.println("进行物理攻击");
    }
     
    public ADHero(){
         
        System.out.println("AD Hero的构造方法");
    }
     
    public static void main(String[] args) {
 
        new ADHero();
         
    }
  
}
```



 步骤 **3** : 

##### 父类显式提供两个构造方法

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-super/311.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-super/311.html#nowhere)

分别是无参的构造方法和带一个参数的构造方法

代码比较复制代码

```java
package charactor;
 
import property.Item;
 
public class Hero {
        
    String name; //姓名
        
    float hp; //血量
        
    float armor; //护甲
        
    int moveSpeed; //移动速度
     
    public void useItem(Item i){
        System.out.println("hero use item");
        i.effect();
    }   
     
    public Hero(){
        System.out.println("Hero的无参的构造方法 ");
    }
     
    public Hero(String name){
        System.out.println("Hero的有一个参数的构造方法 ");
        this.name = name;
    }
     
    public static void main(String[] args) {
        new Hero();
    }
      
}
```



 步骤 **4** : 

##### 子类显式调用父类带参构造方法

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-super/311.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-super/311.html#nowhere)

使用关键字**super** 显式调用父类带参的构造方法

代码比较复制代码

```java
package charactor;
  
public class ADHero extends Hero implements AD{
  
    @Override
    public void physicAttack() {
        System.out.println("进行物理攻击");
    }
     
    public ADHero(String name){
        super(name);
        System.out.println("AD Hero的构造方法");
    }
     
    public static void main(String[] args) {
        new ADHero("德莱文");
    }
  
}
```



 步骤 **5** : 

##### 调用父类属性

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-super/311.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-super/311.html#nowhere)

通过super调用父类的moveSpeed属性
ADHero也提供了属性moveSpeed

 

public int getMoveSpeed(){

   return this.moveSpeed;

}

public int getMoveSpeed2(){

   return super.moveSpeed;

}

 

代码比较复制代码

```java
package charactor;
  
public class ADHero extends Hero implements AD{
 
    int moveSpeed=400; //移动速度
 
    @Override
    public void physicAttack() {
        System.out.println("进行物理攻击");
    }
     
    public int getMoveSpeed(){
        return this.moveSpeed;
    }
     
    public int getMoveSpeed2(){
        return super.moveSpeed;
    }
     
    public static void main(String[] args) {
        ADHero h= new ADHero();
         
        System.out.println(h.getMoveSpeed());
        System.out.println(h.getMoveSpeed2());
         
    }
  
}
```





 步骤 **6** : 

##### 调用父类方法

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-super/311.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-super/311.html#nowhere)

ADHero重写了useItem方法，并且在useItem中**通过super调用父类的useItem方法**

代码比较复制代码

```java
package charactor;
 
import property.Item;
import property.LifePotion;
 
public class ADHero extends Hero implements AD {
 
    int moveSpeed = 400; // 移动速度
 
    @Override
    public void physicAttack() {
        System.out.println("进行物理攻击");
    }
 
    public int getMoveSpeed() {
        return this.moveSpeed;
    }
 
    public int getMoveSpeed2() {
        return super.moveSpeed;
    }
 
    // 重写useItem，并在其中调用父类的userItem方法
    public void useItem(Item i) {
        System.out.println("adhero use item");
        super.useItem(i);
    }
 
    public static void main(String[] args) {
        ADHero h = new ADHero();
 
        LifePotion lp = new LifePotion();
 
    }
 
}
```



 步骤 **7** : 

##### 练习-super 

  [**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-super/311.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-super/311.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/interface-inheritance/interface-inheritance-super/311.html#nowhere)

父类Hero提供了一个有参的构造方法:

 

public Hero(String name){

  this.name = name;

}

 


但是没有提供无参的构造方法
子类应该怎么处理？

代码比较复制代码

```java
package charactor;
   
public class Hero {
    public String name;
    protected float hp;
   
    public Hero(String name){
        this.name = name;
    }
     
//    故意不提供无参的构造方法
//    public Hero(){
//     
//    }
     
    public static void main(String[] args) {
     
    }
       
}
```

#### object类

Object类是所有类的父类



 步骤 **1** : 

##### Object类是所有类的父类

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-object/312.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-object/312.html#nowhere)

声明一个类的时候，默认是继承了Object
public class Hero **extends Object**

代码比较复制代码

```java
package charactor;
 
import property.Item;
 
public class Hero extends Object {
        
    String name; //姓名
        
    float hp; //血量
        
    float armor; //护甲
        
    int moveSpeed; //移动速度
     
    public void useItem(Item i){
        System.out.println("hero use item");
        i.effect();
    }   
     
    public Hero(){
        System.out.println("Hero的无参的构造方法 ");
    }
     
    public Hero(String name){
        System.out.println("Hero的有一个参数的构造方法 ");
        this.name = name;
    }
     
    public static void main(String[] args) {
        new Hero();
    }
      
}
```





 步骤 **2** : 

##### toString()

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-object/312.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-object/312.html#nowhere)

Object类提供一个toString方法，所以所有的类都有toString方法
toString()的意思是返回当前对象的**字符串表达**
通过 System.out.println 打印对象就是打印该对象的toString()返回值

代码比较复制代码

```java
package charactor;
  
public class Hero {
    public String name;
    protected float hp;
      
    public String toString(){
        return name;
    }
      
    public static void main(String[] args) {
         
        Hero h = new Hero();
        h.name = "盖伦";
        System.out.println(h.toString());
        //直接打印对象就是打印该对象的toString()返回值
        System.out.println(h);
    }
}
```



 步骤 **3** : 

##### finalize()

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-object/312.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-object/312.html#nowhere)

当一个对象没有任何引用指向的时候，它就满足垃圾回收的条件

当它被垃圾回收的时候，它的finalize() 方法就会被调用。

finalize() 不是开发人员主动调用的方法，而是由虚拟机JVM调用的。

![finalize() ](https://stepimagewm.how2j.cn/2285.png)

代码比较复制代码

```java
package charactor;
  
public class Hero {
    public String name;
    protected float hp;
      
    public String toString(){
        return name;
    }
     
    public void finalize(){
        System.out.println("这个英雄正在被回收");
    }
      
    public static void main(String[] args) {
        //只有一引用
        Hero h;
        for (int i = 0; i < 100000; i++) {
            //不断生成新的对象
            //每创建一个对象，前一个对象，就没有引用指向了
            //那些对象，就满足垃圾回收的条件
            //当，垃圾堆积的比较多的时候，就会触发垃圾回收
            //一旦这个对象被回收，它的finalize()方法就会被调用
            h = new Hero();
        }
 
    }
}
```





 步骤 **4** : 

##### equals()

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-object/312.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-object/312.html#nowhere)

equals() 用于判断两个对象的内容是否相同

假设，当两个英雄的hp相同的时候，我们就认为这两个英雄相同

代码比较复制代码

```java
package charactor;
  
public class Hero {
    public String name;
    protected float hp;
      
    public boolean equals(Object o){
        if(o instanceof Hero){
            Hero h = (Hero) o;
            return this.hp == h.hp;
        }
        return false;
    }
      
    public static void main(String[] args) {
        Hero h1= new Hero();
        h1.hp = 300;
        Hero h2= new Hero();
        h2.hp = 400;
        Hero h3= new Hero();
        h3.hp = 300;
         
        System.out.println(h1.equals(h2));
        System.out.println(h1.equals(h3));
    }
}
```



 步骤 **5** : 

##### ==

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-object/312.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-object/312.html#nowhere)

这不是Object的方法，但是用于判断两个对象是否相同
**更准确的讲**，用于判断两个引用，是否指向了同一个对象

代码比较复制代码

```java
package charactor;
  
public class Hero {
    public String name;
    protected float hp;
      
    public boolean equals(Object o){
        if(o instanceof Hero){
            Hero h = (Hero) o;
            return this.hp == h.hp;
        }
        return false;
    }
      
    public static void main(String[] args) {
        Hero h1= new Hero();
        h1.hp = 300;
        Hero h2= new Hero();
        h2.hp = 400;
        Hero h3= new Hero();
        h3.hp = 300;
         
        System.out.println(h1==h2);
        System.out.println(h1==h3);
         
    }
}
```





 步骤 **6** : 

##### hashCode()

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-object/312.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-object/312.html#nowhere)

hashCode方法返回一个对象的哈希值，但是在了解哈希值的意义之前，讲解这个方法没有意义。

hashCode的意义，将放在[hashcode 原理](https://how2j.cn/k/collection/collection-hashcode/371.html)章节讲解



 步骤 **7** : 

##### 线程同步相关方法

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-object/312.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-object/312.html#nowhere)

Object还提供线程同步相关方法
wait()
notify()
notifyAll()
这部分内容的理解需要建立在对线程安全有足够的理解的基础之上，所以会放在[线程交互](https://how2j.cn/k/thread/thread-wait-notify/358.html) 的章节讲解



 步骤 **8** : 

##### getClass()

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-object/312.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-object/312.html#nowhere)

getClass()会返回一个对象的[类对象](https://how2j.cn/k/reflection/reflection-class/108.html)，属于高级内容，不适合初学者过早接触，关于类对象的详细内容请参考[反射机制](https://how2j.cn/k/reflection/reflection-reflection/107.html)



 步骤 **9** : 

##### 练习-Object 

  [**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-object/312.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-object/312.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/interface-inheritance/interface-inheritance-object/312.html#nowhere)

重写Item的 toString(), finalize()和equals()方法
toString() 返回Item的name + price
finalize() 输出当前对象正在被回收
equals(Object o) 首先判断o是否是Item类型，然后比较两个Item的price是否相同

#### final

final修饰类，方法，基本类型变量，引用的时候分别有不同的意思。 示例 **1** : 

##### final修饰类

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-final/313.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-final/313.html#nowhere)

当Hero被修饰成final的时候，表示Hero不能够被继承
其子类会出现编译错误

![final修饰类](https://stepimagewm.how2j.cn/653.png)

代码比较复制代码

```java
package charactor;
 
public final class Hero extends Object {
        
    String name; //姓名
        
    float hp; //血量
        
}
```



 示例 **2** : 

##### final修饰方法

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-final/313.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-final/313.html#nowhere)

Hero的useItem方法被修饰成final,那么该方法在ADHero中，不能够被重写

![final修饰方法](https://stepimagewm.how2j.cn/654.png)

代码比较复制代码

```java
package charactor;
 
import property.Item;
 
public class Hero extends Object {
        
    String name; //姓名
        
    float hp; //血量
        
    float armor; //护甲
        
    int moveSpeed; //移动速度
     
    public final void useItem(Item i){
        System.out.println("hero use item");
        i.effect();
    }   
     
    public Hero(){
        System.out.println("Hero的无参的构造方法 ");
    }
     
    public Hero(String name){
        System.out.println("Hero的有一个参数的构造方法 ");
        this.name = name;
    }
     
    public static void main(String[] args) {
        new Hero();
    }
      
}
```



 示例 **3** : 

##### final修饰基本类型变量

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-final/313.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-final/313.html#nowhere)

final修饰基本类型变量，表示该变量只有一次赋值机会
16行进行了赋值，17行就不可以再进行赋值了

代码比较复制代码

```java
package charactor;
 
public class Hero extends Object {
        
    String name; //姓名
        
    float hp; //血量
        
    float armor; //护甲
        
    int moveSpeed; //移动速度
     
    public static void main(String[] args) {
 
        final int hp;
        hp = 5;
        hp = 6;
         
    }
}
```



 示例 **4** : 

##### final修饰引用

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-final/313.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-final/313.html#nowhere)

final修饰引用
h引用被修饰成final，表示该引用只有**1**次指向对象的机会
所以17行会出现编译错误
但是，依然通过h引用修改对象的属性值hp，因为hp并没有final修饰

代码比较复制代码

```java
package charactor;
 
public class Hero extends Object {
        
    String name; //姓名
        
    float hp; //血量
        
    float armor; //护甲
        
    int moveSpeed; //移动速度
     
    public static void main(String[] args) {
 
        final Hero h;
        h  =new Hero();
        h  =new Hero();
         
        h.hp = 5;
         
    }
      
}
```



 示例 **5** : 

##### 常量

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-final/313.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-final/313.html#nowhere)

常量指的是可以公开，直接访问，不会变化的值
比如 itemTotalNumber 物品栏的数量是6个

代码比较复制代码

```java
package charactor;
 
public class Hero extends Object {
     
    public static final int itemTotalNumber = 6;//物品栏的数量
        
    String name; //姓名
        
    float hp; //血量
        
    float armor; //护甲
        
    int moveSpeed; //移动速度
     
    public static void main(String[] args) {
 
        final Hero h;
        h  =new Hero();
         
        h.hp = 5;
         
    }
      
}
```



 示例 **6** : 

##### 练习-final 

  [**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-final/313.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-final/313.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/interface-inheritance/interface-inheritance-final/313.html#nowhere)

设计一个类SomeString,继承 String类。 能否继承？



## 

#### 抽象类

在类中声明一个方法，这个方法没有实现体，是一个“空”方法

这样的方法就叫抽象方法，使用修饰符“abstract"

当一个类有抽象方法的时候，该类必须被声明为抽象类



 步骤 **1** : 

##### 抽象类

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-abstract-class/314.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-abstract-class/314.html#nowhere)

为Hero增加一个**抽象方法 attack**，并且把Hero声明为abstract的。
APHero,ADHero,ADAPHero是Hero的子类，继承了Hero的属性和方法。
但是各自的攻击手段是不一样的，所以继承Hero类后，这些**子类就必须提供**不一样的attack方法实现。

- [Hero.java](https://how2j.cn/k/interface-inheritance/interface-inheritance-abstract-class/314.html#nowhere)

  - ```java
    package charactor;
     
    public abstract class Hero {
        String name;
     
        float hp;
     
        float armor;
     
        int moveSpeed;
     
        public static void main(String[] args) {
     
        }
     
        // 抽象方法attack
        // Hero的子类会被要求实现attack方法
        public abstract void attack();
     
    }
    ```

- [ADHero.java](https://how2j.cn/k/interface-inheritance/interface-inheritance-abstract-class/314.html#nowhere)

  - ```java
    package charactor;
     
    public class ADHero extends Hero implements AD {
     
        public void physicAttack() {
            System.out.println("进行物理攻击");
        }
     
        @Override
        public void attack() {
            physicAttack();
        }
     
    }
    ```

- [APHero.java](https://how2j.cn/k/interface-inheritance/interface-inheritance-abstract-class/314.html#nowhere)

  - ```java
    package charactor;
     
    public class APHero extends Hero implements AP {
     
        @Override
        public void magicAttack() {
            System.out.println("进行魔法攻击");
        }
     
        @Override
        public void attack() {
            magicAttack();
        }
     
    }
    ```

- [ADAPHero.java](https://how2j.cn/k/interface-inheritance/interface-inheritance-abstract-class/314.html#nowhere)

  - ```java
    package charactor;
     
    public class ADAPHero extends Hero implements AD, AP {
     
        @Override
        public void attack() {
     
            System.out.println("既可以进行物理攻击，也可以进行魔法攻击");
        }
     
        public void magicAttack() {
            System.out.println("进行魔法攻击");
        }
     
        public void physicAttack() {
            System.out.println("进行物理攻击");
        }
     
    }
    ```

    

 步骤 **2** : 

##### 抽象类可以没有抽象方法

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-abstract-class/314.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-abstract-class/314.html#nowhere)

Hero类可以在不提供抽象方法的前提下，声明为抽象类
一旦一个类被声明为抽象类，就不能够被直接实例化

代码比较复制代码

```java
package charactor;
   
public abstract class Hero {
    String name;
          
    float hp;
          
    float armor;
          
    int moveSpeed;
       
    public static void main(String[] args) {
        //虽然没有抽象方法，但是一旦被声明为了抽象类，就不能够直接被实例化
        Hero h= new Hero();
    }
          
}
```



 步骤 **3** : 

##### 抽象类和接口的区别

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-abstract-class/314.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-abstract-class/314.html#nowhere)

区别1：
子类只能继承一个抽象类，不能继承多个
子类可以实现**多个**接口
区别2：
抽象类可以定义
public,protected,package,private
静态和非静态属性
final和非final属性
但是接口中声明的属性，只能是
public
静态
final的
即便没有显式的声明
**
注:** 抽象类和接口都可以有实体方法。 接口中的实体方法，叫做[默认方法](https://how2j.cn/k/interface-inheritance/interface-inheritance-default-method/676.html)

代码比较复制代码

```java
package charactor;
  
public interface AP {
  
    public static final int resistPhysic = 100;
     
    //resistMagic即便没有显式的声明为 public static final
    //但依然默认为public static final
    int resistMagic = 0;
     
    public void magicAttack();
}
```



 步骤 **4** : 

##### 练习-抽象类 

  [**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-abstract-class/314.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-abstract-class/314.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/interface-inheritance/interface-inheritance-abstract-class/314.html#nowhere)

有的物品使用之后就消失了，比如血瓶

有的物品使用了之后还会继续存在，比如武器

为Item类设计一个抽象方法

 

public abstract boolean disposable()

 



不同的子类，实现disposable后，会返回不同的值。
比如LifePotion就会返回true，因为是会消失了。
而Weapon,Armor 就会返回false,因为是不会消失了

#### 内部类

内部类分为四种：
非静态内部类
静态内部类
匿名类
本地类 步骤 **1** : 

##### 非静态内部类

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-inner-class/322.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-inner-class/322.html#nowhere)

非静态内部类 BattleScore “战斗成绩”
非静态内部类可以直接在一个类里面定义

比如：
战斗成绩只有在一个英雄对象存在的时候才有意义
所以实例化BattleScore 的时候，必须建立在一个存在的英雄的基础上
语法: **new 外部类().new 内部类()**
作为Hero的非静态内部类，是可以直接访问外部类的**private**实例属性name的

代码比较复制代码

```java
package charactor;
 
public class Hero {
    private String name; // 姓名
 
    float hp; // 血量
 
    float armor; // 护甲
 
    int moveSpeed; // 移动速度
 
    // 非静态内部类，只有一个外部类对象存在的时候，才有意义
    // 战斗成绩只有在一个英雄对象存在的时候才有意义
    class BattleScore {
        int kill;
        int die;
        int assit;
 
        public void legendary() {
            if (kill >= 8)
                System.out.println(name + "超神！");
            else
                System.out.println(name + "尚未超神！");
        }
    }
 
    public static void main(String[] args) {
        Hero garen = new Hero();
        garen.name = "盖伦";
        // 实例化内部类
        // BattleScore对象只有在一个英雄对象存在的时候才有意义
        // 所以其实例化必须建立在一个外部类对象的基础之上
        BattleScore score = garen.new BattleScore();
        score.kill = 9;
        score.legendary();
    }
 
}
```



 步骤 **2** : 

##### 静态内部类

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-inner-class/322.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-inner-class/322.html#nowhere)

在一个类里面声明一个静态内部类
比如敌方水晶，当敌方水晶没有血的时候，己方所有英雄都取得胜利，而不只是某一个具体的英雄取得胜利。
与非静态内部类不同，**静态内部类**水晶类的实例化 **不需要一个外部类的实例为基础**，可以直接实例化
语法：**new 外部类.静态内部类();**
因为没有一个外部类的实例，所以在静态内部类里面**不可以访问外部类的实例属性和方法**
除了可以访问外部类的**私有静态成员外**，静态内部类和普通类没什么大的区别

代码比较复制代码

```java
package charactor;
  
public class Hero {
    public String name;
    protected float hp;
  
    private static void battleWin(){
        System.out.println("battle win");
    }
     
    //敌方的水晶
    static class EnemyCrystal{
        int hp=5000;
         
        //如果水晶的血量为0，则宣布胜利
        public void checkIfVictory(){
            if(hp==0){
                Hero.battleWin();
                 
                //静态内部类不能直接访问外部类的对象属性
                System.out.println(name + " win this game");
            }
        }
    }
     
    public static void main(String[] args) {
        //实例化静态内部类
        Hero.EnemyCrystal crystal = new Hero.EnemyCrystal();
        crystal.checkIfVictory();
    }
  
}
```



 步骤 **3** : 

##### 匿名类

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-inner-class/322.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-inner-class/322.html#nowhere)

匿名类指的是在**声明一个类的同时实例化它**，使代码更加简洁精练
通常情况下，要使用一个接口或者抽象类，都必须创建一个子类

有的时候，为了快速使用，直接实例化一个抽象类，并“**当场**”实现其抽象方法。
既然实现了抽象方法，那么就是一个新的类，只是这个类，没有命名。
这样的类，叫做匿名类

![匿名类](https://stepimagewm.how2j.cn/687.png)

代码比较复制代码

```java
package charactor;
   
public abstract class Hero {
    String name; //姓名
          
    float hp; //血量
          
    float armor; //护甲
          
    int moveSpeed; //移动速度
      
    public abstract void attack();
      
    public static void main(String[] args) {
          
        ADHero adh=new ADHero();
        //通过打印adh，可以看到adh这个对象属于ADHero类
        adh.attack();
        System.out.println(adh);
          
        Hero h = new Hero(){
            //当场实现attack方法
            public void attack() {
                System.out.println("新的进攻手段");
            }
        };
        h.attack();
        //通过打印h，可以看到h这个对象属于Hero$1这么一个系统自动分配的类名
          
        System.out.println(h);
    }
      
}
```



 步骤 **4** : 

##### 本地类

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-inner-class/322.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-inner-class/322.html#nowhere)

本地类可以理解为有名字的匿名类
内部类与匿名类不一样的是，内部类必须声明在成员的位置，即与属性和方法平等的位置。
本地类和匿名类一样，直接声明在代码块里面，可以是主方法，for循环里等等地方

代码比较复制代码

```java
package charactor;
   
public abstract class Hero {
    String name; //姓名
          
    float hp; //血量
          
    float armor; //护甲
          
    int moveSpeed; //移动速度
      
    public abstract void attack();
      
    public static void main(String[] args) {
          
        //与匿名类的区别在于，本地类有了自定义的类名
        class SomeHero extends Hero{
            public void attack() {
                System.out.println( name+ " 新的进攻手段");
            }
        }
         
        SomeHero h  =new SomeHero();
        h.name ="地卜师";
        h.attack();
    }
      
}
```



 步骤 **5** : 

##### 在匿名类中使用外部的局部变量

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-inner-class/322.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-inner-class/322.html#nowhere)

在匿名类中使用外部的局部变量，外部的局部变量必须修饰为final

为什么要声明为final，其机制比较复杂，请参考第二个Hero代码中的解释

**注：**在jdk8中，已经不需要强制修饰成final了，如果没有写final，不会报错，因为编译器**偷偷的**帮你加上了看不见的final

- [Hero.java](https://how2j.cn/k/interface-inheritance/interface-inheritance-inner-class/322.html#nowhere)

  - ```java
    package charactor;
       
    public abstract class Hero {
     
        public abstract void attack();
          
        public static void main(String[] args) {
     
            //在匿名类中使用外部的局部变量，外部的局部变量必须修饰为final
            final int damage = 5;
             
            Hero h = new Hero(){
                public void attack() {
                    System.out.printf("新的进攻手段，造成%d点伤害",damage );
                }
            };
     
        }
          
    }
    ```

  - 

- [Hero.java](https://how2j.cn/k/interface-inheritance/interface-inheritance-inner-class/322.html#nowhere)

  - ```java
    package charactor;
       
    public abstract class Hero {
     
        public abstract void attack();
          
        public static void main(String[] args) {
     
            //在匿名类中使用外部的局部变量damage 必须修饰为final
            int damage = 5;
             
            //这里使用本地类AnonymousHero来模拟匿名类的隐藏属性机制
             
            //事实上的匿名类，会在匿名类里声明一个damage属性，并且使用构造方法初始化该属性的值
            //在attack中使用的damage，真正使用的是这个内部damage，而非外部damage
             
            //假设外部属性不需要声明为final
            //那么在attack中修改damage的值，就会被暗示为修改了外部变量damage的值
             
            //但是他们俩是不同的变量，是不可能修改外部变量damage的
            //所以为了避免产生误导，外部的damage必须声明为final,"看上去"就不能修改了
            class AnonymousHero extends Hero{
                int damage;
                public AnonymousHero(int damage){
                    this.damage = damage;
                }
                public void attack() {
                    damage = 10;
                    System.out.printf("新的进攻手段，造成%d点伤害",this.damage );
                }
            }
             
            Hero h = new AnonymousHero(damage);
             
        }
          
    }
    ```

  - 

 步骤 **6** : 

##### 练习-内部类 

  [**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-inner-class/322.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-inner-class/322.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/interface-inheritance/interface-inheritance-inner-class/322.html#nowhere)

创建一个Item的匿名类

Item有抽象方法disposable(), 就像[抽象类练习](https://how2j.cn/k/interface-inheritance/interface-inheritance-abstract-class/314.html#step2301) 中要求的那样。

#### 默认方法

 步骤 **1** : 

##### 什么是默认方法

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-default-method/676.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-default-method/676.html#nowhere)

默认方法是JDK8新特性，指的是接口也可以提供具体方法了，而不像以前，只能提供抽象方法

Mortal 这个接口，增加了一个**默认方法** revive，这个方法有实现体，并且被声明为了**default**

代码比较复制代码

```java
package charactor;
 
public interface Mortal {
    public void die();
 
    default public void revive() {
        System.out.println("本英雄复活了");
    }
}
```



 步骤 **2** : 

##### 为什么会有默认方法

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-default-method/676.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-default-method/676.html#nowhere)

假设没有默认方法这种机制，那么如果要为Mortal增加一个新的方法revive,那么所有实现了Mortal接口的类，都需要做改动。

但是引入了默认方法后，原来的类，不需要做任何改动，并且还能**得到**这个默认方法

通过这种手段，就能够很好的扩展新的类，并且做到不影响原来的类



 步骤 **3** : 

##### 练习-默认方法 

  [**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-default-method/676.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-default-method/676.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/interface-inheritance/interface-inheritance-default-method/676.html#nowhere)

为AD接口增加一个默认方法 attack()
为AP接口也增加一个默认方法 attack()
问： ADAPHero同时实现了AD,AP接口，那么 ADAPHero 对象调用attack()的时候，是调用哪个接口的attack()?

---



#### 综合练习

 步骤 **1** : 

##### UML 图 —— 类之间的关系

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-practise/679.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-practise/679.html#nowhere)

UML-Unified Module Language
统一建模语言，可以很方便的用于描述类的属性，方法，以及类和类之间的关系

![UML 图 —— 类之间的关系](https://stepimagewm.how2j.cn/2305.png)



 步骤 **2** : 

##### 解释UML-类图

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-practise/679.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-practise/679.html#nowhere)

![解释UML-类图](https://stepimagewm.how2j.cn/2318.png)

 步骤 **3** : 

##### 解释UML-接口图

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-practise/679.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-practise/679.html#nowhere)

![解释UML-接口图](https://stepimagewm.how2j.cn/2319.png)

 步骤 **4** : 

##### 解释UML-继承关系

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-practise/679.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-practise/679.html#nowhere)

带箭头的实线，表示 Spider，Cat, Fish都继承于Animal这个父类.
**注：** 模糊是表示，此时不需要关注模糊的那部分内容。 请不要再发图片是模糊的纠正信息了，站长特意这么做的。。。

![解释UML-继承关系](https://stepimagewm.how2j.cn/2320.png)



 步骤 **5** : 

##### 解释UML-实现关系

[**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-practise/679.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-practise/679.html#nowhere)

表示 Fish实现了 Pet这个接口

![解释UML-实现关系](https://stepimagewm.how2j.cn/2321.png)



 步骤 **6** : 

##### 练习-Animal类 

  [**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-practise/679.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-practise/679.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/interface-inheritance/interface-inheritance-practise/679.html#nowhere)

\1. 创建Animal类，它是所有动物的抽象父类。
\2. 声明一个受保护的整数类型属性legs，它记录动物的腿的数目。
\3. 定义一个受保护的构造器，用来初始化legs属性。
\4. 声明抽象方法eat。
\5. 声明具体方法walk来打印动物是如何行走的（包括腿的数目）。

 步骤 **8** : 

##### 练习-Spider类 

  [**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-practise/679.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-practise/679.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/interface-inheritance/interface-inheritance-practise/679.html#nowhere)

\1. Spider继承Animal类。
\2. 定义默认构造器，它调用父类构造器来指明所有蜘蛛都是8条腿。
\3. 实现eat方法



 步骤 **10** : 

##### 练习-Pet接口 

  [**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-practise/679.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-practise/679.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/interface-inheritance/interface-inheritance-practise/679.html#nowhere)

根据UML类创建pet（宠物）接口
\1. 提供getName() 返回该宠物的名字
\2. 提供setName(String name) 为该宠物命名
\3. 提供 play()方法



 步骤 **12** : 

##### 练习-Cat类 

  [**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-practise/679.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-practise/679.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/interface-inheritance/interface-inheritance-practise/679.html#nowhere)

\1. 该类必须包含String属性来存宠物的名字。
\2. 定义一个构造器，它使用String参数指定猫的名字；该构造器必须调用超类构造器来指明所有的猫都是四条腿。
\3. 另定义一个无参的构造器。该构造器调用前一个构造器（用this关键字）并传递一个空字符串作为参数
\4. 实现Pet接口方法。
\5. 实现eat方法。

 步骤 **14** : 

##### 练习-Fish类 

  [**顶**](https://how2j.cn/k/interface-inheritance/interface-inheritance-practise/679.html#)[**折**](https://how2j.cn/k/interface-inheritance/interface-inheritance-practise/679.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/interface-inheritance/interface-inheritance-practise/679.html#nowhere)

\1. 创建Fish类，它继承Animal类
\2. 重写Animal的walk方法以表明鱼不能走且没有腿。
\3. 实现Pet接口
\4. 无参构造方法
\5. 提供一个private 的name属性

