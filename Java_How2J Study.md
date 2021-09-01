# Java_How2J Study

[toc]

---



## Java基础

### HelloWorld

### 面向对象

### 变量

#### 什么是变量

#### 基本变量类型

---



#### 字面值

创建一个Hero对象会用到new关键字，但是给一个基本类型变量赋值却不是用new. 因为基本类型是Java语言里的一种内置的特殊数据类型，并不是某个类的对象。
给基本类型的变量赋值的方式叫做 **字面值**，如下所例：

​	float hp = 313f;

​	int armor = 24;

##### 整数字面值

当以l或者L结尾的时候，一个整数字面值是long类型，否则就是int类型。 建议使用**大写的L**而非小写的l，因为容易和1混淆。
byte,short,int和long的值都可以通过int类型的字面值来创建。整数的字面值可以用如下四种进制来表示：
十进制: 基 10, 包含从0-9的数字，**平常用的就是这种**
十六进制: 基 16, 包含从0-9的数字，和从A-F的字母。
八进制: 基 8, 包含从0-7的数字
二进制: 基 2, 包含0和1。（从 JAVA7开始就可以创建 二进制的字面值了）

```java
public class HelloWorld {
    public static void main(String[] args) {
        long val = 26L; //以L结尾的字面值表示long型
        int decVal = 26; //默认就是int型
        int hexVal = 0x1a; //16进制
        int oxVal = 032; //8进制
        int binVal = 0b11010; //2进制
        System.out.println(oxVal);
    }
}
```

##### 浮点数字面值

当以f或者F结尾的时候，就表示一个float类型的浮点数，否则就是double类型（以d或者D结尾，写不写都可以）。
浮点数还可以用E或者e表示（科学计数法）
e2表示10的二次方，即100
1.234e2 = 1.234x100

```java
public class HelloWorld {
 
    public static void main(String[] args) {
        float f1 = 123.4F;// 以F结尾的字面值表示float类型
        double d1 = 123.4;// 默认就是double类型
        double d2 = 1.234e2;// 科学计数法表示double
    }
}
```

##### 字符和字符串字面值

字符的字面值放在单引号中

**字符串**的字面值放在双引号中

需要注意的是，\表示转义，比如需要表示制表符，回车换行，双引号等就需要用 \t \r \n \" 的方式进行

```java
public class HelloWorld {
 
    public static void main(String[] args) {
        String name = "盖伦";
        char a= 'c';
 
        //以下是转义字符
        char tab = '\t'; //制表符
        char carriageReturn = '\r'; //回车
        char newLine = '\n'; //换行
        char doubleQuote = '\"'; //双引号
        char singleQuote = '\''; //单引号
        char backslash = '\\'; //反斜杠
         
    }
}
```



---



#### 类型转换

不同类型之间的数据可以互相转换，但是要满足一定的规则

##### 转换规则

转换规则如图所示
**精度高**的数据类型就像**容量大**的杯子，可以**放更大**的数据
**精度低**的数据类型就像**容量小**的杯子，只能**放更小**的数据
小杯子往大杯子里倒东西，大杯子**怎么都放得下**
大杯子往小杯子里倒东西，**有的时候放的下**，**有的时候就会有溢出**
需要注意的一点是
虽然short和char都是16位的，长度是一样的
但是彼此之间，依然需要进行强制转换

![转换规则](https://stepimagewm.how2j.cn/519.png)

```java
public class HelloWorld {
 
    public static void main(String[] args) {
 
        char c = 'A';
        short s = 80;
         
        //虽然short和char都是16位的，长度是一样的
        //但是彼此之间，依然需要进行强制转换
        c = (char) s;
        //直接进行转换，会出现编译错误
        s = c;
         
    }
}
```

##### 低精度向高精度转换

```tcl
long l = 50;
int i = 50;
```




l 是long类型的，其类型长度是64位
i 是int类型的，其类型长度是32位
所以l的精度，比i的精度要高
l = i;
**把i的值赋给l**， 首先l和i彼此的类型是不一样的，那么能否转换就取决于彼此的精度
这个例子，是低精度向高精度转换 是可以正常转换的
换句话说，int比较小，要放进比较大的long,随便怎么样，都放的进去

![低精度向高精度转换](https://stepimagewm.how2j.cn/517.png)

代码比较复制代码

```java
public class HelloWorld {
  
    public static void main(String[] args) {
  
        long l = 50;
        int i = 50;
         
        //int比较小，要放进比较大的long,随便怎么样，都放的进去
        l = i;
          
    }
}
```

##### 高精度向低精度转换

[**顶**](https://how2j.cn/k/variable/variable-transfer/264.html#)[**折**](https://how2j.cn/k/variable/variable-transfer/264.html#nowhere)

byte b = 5;

int i1 = 10;

int i2 = 300;

b = i1;

b=i2;


b的类型是byte,其长度是8，**最大只能放127**
i1 的类型是int, 其长度是32,最大，反正就是很大了，超过127
所以， 把int类型的数据转成为byte类型的数据，**是有风险的**
**有的时候是可以转换的**，比如 b = i1 (i1=10);
**有的时候不可以转换** 比如 b= i2 (i2=300) 因为放不下了
编译器就会提示错误
这个时候就只能采用**强制转换**，强制转换的意思就是，转是可以转的，但是不对转换之后的值负责。 风险自担，后果自负

![高精度向低精度转换](https://stepimagewm.how2j.cn/518.png)

---

#### 作用域

变量处于不同的位置，有不同的名称

分别是
字段，属性
参数
局部变量

不同名称的变量，其作用域是不一样的



##### 字段，属性，Field

当一个变量被声明在类下面
变量就叫做**字段** 或者**属性**、**成员变量**、**Field**
比如变量i,就是一个属性。
那么从第2行这个变量声明的位置开始，整个类都可以访问得到
所以其作用域就是从其声明的位置开始的整个类

代码比较复制代码

```java
public class HelloWorld {
    int i = 1;
    int j = i;  //其他的属性可以访问i
    public void method1(){
        System.out.println(i); //方法1里可以访问i
    }
    public void method2(){
        System.out.println(i); //方法2里可以访问i
    }
}
```



##### 参数

[**顶**](https://how2j.cn/k/variable/variable-scope/261.html#)[**折**](https://how2j.cn/k/variable/variable-scope/261.html#nowhere)

如果一个变量，是声明在一个方法上的，就叫做**参数**
参数的作用域即为该方法内的所有代码
其他方法不能访问该参数
类里面也不能访问该参数

```java
public class HelloWorld {
 
    public void method1(int i){ //参数i的作用域即方法method1
        System.out.println(i);
    }
    public void method2(){
 
        System.out.println(i); //method2 不能访问参数i
    }
     
    int j = i;  //类里面也不能访问参数i
}
```



 示例 **3** : 

##### 局部变量

[**顶**](https://how2j.cn/k/variable/variable-scope/261.html#)[**折**](https://how2j.cn/k/variable/variable-scope/261.html#nowhere)

声明在方法内的变量，叫做局部变量
其作用域在声明开始的位置，到其所处于的块结束位置

```java
public class HelloWorld {
 
    public void method1() {
        int i  = 5;  //其作用范围是从声明的第4行，到其所处于的块结束12行位置
        System.out.println(i);
        {            //子块
            System.out.println(i); //可以访问i
            int j = 6;
            System.out.println(j); //可以访问j
        }
        System.out.println(j); //不能访问j,因为其作用域到第10行就结束了
    }
 
}
```



 示例 **4** : 

##### 练习-作用域 

  [**顶**](https://how2j.cn/k/variable/variable-scope/261.html#)[**折**](https://how2j.cn/k/variable/variable-scope/261.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/variable/variable-scope/261.html#nowhere)

属性的作用域在方法中，参数的作用域也在方法中，如果属性和参数命名相同了的话？ 那么到底取哪个值？

```java
public class HelloWorld {
    int i = 1; //属性名是i
    public void method1(int i){ //参数也是i
        System.out.println(i);
    }
     
    public static void main(String[] args) {
        new HelloWorld().method1(5);
        //结果打印出来是 1还是5?
    }
}
```

---

#### 变量final

final 修饰一个变量，有很多种说法，比如不能改变等等
准确的描述是 当一个变量被final修饰的时候，该变量**只有一次赋值的机会**

 示例 **1** : 

##### 在声明的时候赋值

[**顶**](https://how2j.cn/k/variable/variable-final/262.html#)[**折**](https://how2j.cn/k/variable/variable-final/262.html#nowhere)

i在第4行已经被赋值过了，所以这里会出现编译错误

代码比较复制代码

```java
public class HelloWorld {
 
    public void method1() {
        final int i = 5;
         
        i = 10; //i在第4行已经被赋值过了，所以这里会出现编译错误
         
    }
 
}
```



 示例 **2** : 

##### 在声明的时候没有赋值

[**顶**](https://how2j.cn/k/variable/variable-final/262.html#)[**折**](https://how2j.cn/k/variable/variable-final/262.html#nowhere)

如果在声明的时候未赋值，那么可以在后面代码进行唯一的一次赋值

代码比较复制代码

```java
public class HelloWorld {
 
    public void method1() {
        final int i;
         
        i = 10; //i在第4行，只是被声明，但是没有被赋值，所以在这里可以进行第一次赋值
         
        i = 11; //i在第6行已经被赋值过了，所以这里会出现编译错误
         
    }
 
}
```



 示例 **3** : 

##### final 修饰其他

[**顶**](https://how2j.cn/k/variable/variable-final/262.html#)[**折**](https://how2j.cn/k/variable/variable-final/262.html#nowhere)

final 除了修饰变量，还可以[修饰类](https://how2j.cn/k/interface-inheritance/interface-inheritance-final/313.html#step653)，[修饰方法](https://how2j.cn/k/interface-inheritance/interface-inheritance-final/313.html#step654)，这些都在后续的章节展开



 示例 **4** : 

##### 练习-final 

  [**顶**](https://how2j.cn/k/variable/variable-final/262.html#)[**折**](https://how2j.cn/k/variable/variable-final/262.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/variable/variable-final/262.html#nowhere)

如果final修饰的是**参数**，能否在方法里给这个参数赋值？

代码比较复制代码

```java
public class HelloWorld {
 
    public void method1(final int j) {
        j = 5; //这个能否执行？
    }
}
 示例 5 : 答案-final 
```

---

#### 表达式

 步骤 **1** : 

##### 以;结尾的一段代码，即为一个表达式

[**顶**](https://how2j.cn/k/variable/variable-express/277.html#)[**折**](https://how2j.cn/k/variable/variable-express/277.html#nowhere)

表达式是由变量、操作符以及方法调用所构成的结构。如下所示：

 

int i = 5;  

System.out.println(5);

 


都是表达式

代码比较复制代码

```java
public class HelloWorld {
    public static void main(String[] args) {
        //每一句话都是一个表达式
        int i = 5; 
        System.out.println(5);
    }
}
```



 步骤 **2** : 



;

[**顶**](https://how2j.cn/k/variable/variable-express/277.html#)[**折**](https://how2j.cn/k/variable/variable-express/277.html#nowhere)

; 也是一个完整的表达式

代码比较复制代码

```java
public class HelloWorld {
    public static void main(String[] args) {
        //一个空;也是一个表达式
        ;
        ;
        ;      
        ;
    }
}
```

---

#### 语句块

##### 块

从**{** 开始 到对应的**}** 结束，即一个块

```java
public class HelloWorld { //类对应的块
    public static void main(String[] args) { //主方法对应的块
        System.out.println("abc");
    }
}
```

---

### 操作符

#### 算数操作符

基本的有 + - * %

自增 自减 ++	--

 示例 **1** : 

##### 基本算数操作符

[**顶**](https://how2j.cn/k/operator/operator-arithmetic/265.html#)[**折**](https://how2j.cn/k/operator/operator-arithmetic/265.html#nowhere)

\+ - * / 
基本的加 减 乘 除

代码比较复制代码

```java
public class HelloWorld {
    public static void main(String[] args) {
        int i = 10;
        int j = 5;
        int a = i+j;
        int b = i - j;
        int c = i*j;
        int d = i /j;
    }
}
```

 示例 **2** : 

##### 练习-求和 

  [**顶**](https://how2j.cn/k/operator/operator-arithmetic/265.html#)[**折**](https://how2j.cn/k/operator/operator-arithmetic/265.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/operator/operator-arithmetic/265.html#nowhere)

使用[Scanner](https://how2j.cn/k/operator/operator-scanner/658.html)从控制台获取两个数字，然后计算这两个数字的和

如果不会使用Scanner，请参考 [如何使用Scanner读取整数](https://how2j.cn/k/operator/operator-scanner/658.html)

![练习-求和](https://stepimagewm.how2j.cn/2141.png)

 示例 **4** : 

##### 任意运算单元的长度超过int

[**顶**](https://how2j.cn/k/operator/operator-arithmetic/265.html#)[**折**](https://how2j.cn/k/operator/operator-arithmetic/265.html#nowhere)

如果有任何运算单元的长度超过int,那么运算结果就按照最长的长度计算
比如
int a = 5;
long b = 6;
a+b -> 结果类型是long

代码比较复制代码

```java
public class HelloWorld {
    public static void main(String[] args) {
 
        int a = 5;
        long b = 6;
        int c = (int) (a+b); //a+b的运算结果是long型，所以要进行强制转换
        long d = a+b;
         
    }
}
```



 示例 **5** : 

##### 任意运算单元的长度小于int

[**顶**](https://how2j.cn/k/operator/operator-arithmetic/265.html#)[**折**](https://how2j.cn/k/operator/operator-arithmetic/265.html#nowhere)

如果任何运算单元的长度都不超过int,那么运算结果就按照int来计算
byte a = 1;
byte b= 2;
a+b -> int 类型

代码比较复制代码

```java
public class HelloWorld {
    public static void main(String[] args) {
        byte a = 1;
        byte b= 2;
        byte c = (byte) (a+b); //虽然a b都是byte类型，但是运算结果是int类型，需要进行强制转换
        int d = a+b;
    }
}
```



 示例 **6** : 

##### %取模

[**顶**](https://how2j.cn/k/operator/operator-arithmetic/265.html#)[**折**](https://how2j.cn/k/operator/operator-arithmetic/265.html#nowhere)

% 取余数，又叫取模
5除以2，余1

代码比较复制代码

```java
public class HelloWorld {
    public static void main(String[] args) {
 
        int i = 5;
        int j = 2;
        System.out.println(i%j); //输出为1
    }
}
```



 示例 **7** : 

##### 自增 自减

[**顶**](https://how2j.cn/k/operator/operator-arithmetic/265.html#)[**折**](https://how2j.cn/k/operator/operator-arithmetic/265.html#nowhere)

++
\--
在原来的基础上增加1或者减少1

代码比较复制代码

```java
public class HelloWorld {
    public static void main(String[] args) {
 
        int i = 5;
        i++;
        System.out.println(i);//输出为6
 
    }
}
```



 示例 **8** : 

##### 自增 自减操作符置前以及置后的区别

[**顶**](https://how2j.cn/k/operator/operator-arithmetic/265.html#)[**折**](https://how2j.cn/k/operator/operator-arithmetic/265.html#nowhere)

以++为例
int i = 5;
i++; **先取值，再运算**
++i; **先运算，再取值**

代码比较复制代码

```java
public class HelloWorld {
    public static void main(String[] args) {
        int i = 5;
        System.out.println(i++); //输出5
        System.out.println(i);   //输出6
         
        int j = 5;
        System.out.println(++j); //输出6
        System.out.println(j);   //输出6
    }
}
```



 示例 **9** : 

##### 练习-自增 

  [**顶**](https://how2j.cn/k/operator/operator-arithmetic/265.html#)[**折**](https://how2j.cn/k/operator/operator-arithmetic/265.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/operator/operator-arithmetic/265.html#nowhere)

 

int i = 1;

int j = ++i + i++ + ++i + ++i + i++;

 



问 j的结果是多少?

---



#### 关系操作符

关系操作符:比较两个变量之间的关系
\> 大于
\>= 大于或等于
< 小于
<= 小于或等于
== 是否相等
!= 是否不等





 示例 **1** : 

##### 关系操作符

[**顶**](https://how2j.cn/k/operator/operator-relational/266.html#)[**折**](https://how2j.cn/k/operator/operator-relational/266.html#nowhere)

\> 大于
\>= 大于或等于
< 小于
<= 小于或等于
== 是否相等
!= 是否不等

代码比较复制代码

```Java
public class HelloWorld {
    public static void main(String[] args) {
       int a = 5;
       int b = 6;
       int c = 5;
        
       System.out.println(a>b);  //返回 false
       System.out.println(a>=c);  //返回 true
        
       System.out.println(a==b); //返回false
       System.out.println(a!=b);//返回true
        
}
}
```



 示例 **2** : 

##### 练习-关系操作符 

  [**顶**](https://how2j.cn/k/operator/operator-relational/266.html#)[**折**](https://how2j.cn/k/operator/operator-relational/266.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/operator/operator-relational/266.html#nowhere)

借助[Scanner](https://how2j.cn/k/operator/operator-scanner/658.html)获取控制台输入的两个任意数字，然后使用
\> 大于
\>= 大于或等于
< 小于
<= 小于或等于
== 是否相等
!= 是否不等

判断两个值之间的关系

![练习-关系操作符](https://stepimagewm.how2j.cn/2147.png)

#### 逻辑操作符

##### 逻辑运算符

 示例 **1** : 

##### 长路与 和 短路与

[**顶**](https://how2j.cn/k/operator/operator-logic/267.html#)[**折**](https://how2j.cn/k/operator/operator-logic/267.html#nowhere)

无论长路与还是短路与
两边的运算单元都是布尔值
都为真时，才为真
任意为假，就为假
区别
长路与 两侧，都会被运算
短路与 只要第一个是false，第二个就不进行运算了

![长路与 和 短路与](https://stepimagewm.how2j.cn/537.png)

代码比较复制代码

```java
public class HelloWorld {
    public static void main(String[] args) {
        //长路与  无论第一个表达式的值是true或者false,第二个的值，都会被运算
        int i = 2;
        System.out.println( i== 1 & i++ ==2  ); //无论如何i++都会被执行，所以i的值变成了3
        System.out.println(i);
         
        //短路与 只要第一个表达式的值是false的，第二个表达式的值，就不需要进行运算了
        int j = 2;
        System.out.println( j== 1 && j++ ==2  );  //因为j==1返回false,所以右边的j++就没有执行了，所以j的值，还是2
        System.out.println(j);     
         
    }
}
```



 示例 **2** : 

##### 长路或 和 短路或

[**顶**](https://how2j.cn/k/operator/operator-logic/267.html#)[**折**](https://how2j.cn/k/operator/operator-logic/267.html#nowhere)

无论长路或还是短路或
两边的运算单元都是布尔值
都为假时，才为假
任意为真，就为真
区别
长路或 两侧都会被运算
短路或 只要第一个是true的，第二个就不进行运算了

![长路或 和 短路或](https://stepimagewm.how2j.cn/538.png)

代码比较复制代码

```java
public class HelloWorld {
    public static void main(String[] args) {
        //长路或  无论第一个表达式的值是true或者false,第二个的值，都会被运算
        int i = 2;
        System.out.println( i== 1 | i++ ==2  ); //无论如何i++都会被执行，所以i的值变成了3
        System.out.println(i);
         
        //短路或 只要第一个表达式的值是true的，第二个表达式的值，就不需要进行运算了
        int j = 2;
        System.out.println( j== 2 || j++ ==2  );  //因为j==2返回true,所以右边的j++就没有执行了，所以j的值，还是2
        System.out.println(j);     
         
    }
}
```



 示例 **3** : 

##### 取反

[**顶**](https://how2j.cn/k/operator/operator-logic/267.html#)[**折**](https://how2j.cn/k/operator/operator-logic/267.html#nowhere)

取反!
真变为假
假变为真

代码比较复制代码

```java 
public class HelloWorld {
    public static void main(String[] args) {
        boolean b = true;
         
        System.out.println(b); //输出true
        System.out.println(!b);//输出false
         
    }
}
```



 示例 **4** : 

##### 异或^

[**顶**](https://how2j.cn/k/operator/operator-logic/267.html#)[**折**](https://how2j.cn/k/operator/operator-logic/267.html#nowhere)

异或^
不同，返回真
相同，返回假

![异或^](https://stepimagewm.how2j.cn/540.png)

代码比较复制代码

```java
public class HelloWorld {
    public static void main(String[] args) {
        boolean a = true;
        boolean b = false;
         
        System.out.println(a^b); //不同返回真
        System.out.println(a^!b); //相同返回假
 
    }
}
```



 示例 **5** : 

##### 练习-逻辑操作符 

  [**顶**](https://how2j.cn/k/operator/operator-logic/267.html#)[**折**](https://how2j.cn/k/operator/operator-logic/267.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/operator/operator-logic/267.html#nowhere)

 ```tex
 int i = 1;
 
 boolean b = !(i++ == 3) ^ (i++ ==2) && (i++==3);
 
 System.out.println(b);
 
 System.out.println(i);
 ```

 

输出结果是？



##### 答案-逻辑操作符 

---

#### 位操作符

位操作符在实际工作中用的**并不常见**，但是同学们总是**很喜欢纠结**这些位操作。

所以本章节会给出每一个操作符的操作实例帮助大家理解其具体含义。

最后说，如果确实感兴趣，就看看，个人建议跳过这个章节。 真正工作用到了，再来看。



 示例 **1** : 

##### 一个整数的二进制表达

[**顶**](https://how2j.cn/k/operator/operator-bitwise/270.html#)[**折**](https://how2j.cn/k/operator/operator-bitwise/270.html#nowhere)

位操作都是对二进制而言的，但是我们平常使用的都是十进制比如5。
而5的二进制是101。
所以在开始学习之前，需要掌握一个整数的二进制表达是多少。
通过Integer.toBinaryString() 方法，将一个十进制整数转换为一个二进制字符串

![一个整数的二进制表达](https://stepimagewm.how2j.cn/1066.png)

代码比较复制代码

```JAVA
public class HelloWorld {
    public static void main(String[] args) {
        int i = 5;
        String b = (Integer.toBinaryString(i)); // 5的二进制的表达101
        System.out.println(i+" 的二进制表达是: "+b);
    }
}
```



 示例 **2** : 

##### 位或

[**顶**](https://how2j.cn/k/operator/operator-bitwise/270.html#)[**折**](https://how2j.cn/k/operator/operator-bitwise/270.html#nowhere)

5的二进制是101
6的二进制是110
所以 5|6 对每一位进行或运算，得到 111->7

代码比较复制代码

```java
public class HelloWorld {
    public static void main(String[] args) {
         
        int i  =5;
        int j = 6;
         
        System.out.println(Integer.toBinaryString(i)); //5的二进制是101
         
        System.out.println(Integer.toBinaryString(j)); //6的二进制是110
         
        System.out.println(i|j); //所以 5|6 对每一位进行或运算，得到 111->7
 
    }
}
```



 示例 **3** : 

##### 位与

[**顶**](https://how2j.cn/k/operator/operator-bitwise/270.html#)[**折**](https://how2j.cn/k/operator/operator-bitwise/270.html#nowhere)

5的二进制是101
6的二进制是110
所以 5&6 对每一位进行与运算，得到 100->4

代码比较复制代码

```java
public class HelloWorld {
    public static void main(String[] args) {
         
        int i  =5;
        int j = 6;
         
        System.out.println(Integer.toBinaryString(i)); //5的二进制是101
         
        System.out.println(Integer.toBinaryString(j)); //6的二进制是110
         
        System.out.println(i&j); //所以 5&6 对每一位进行与运算，得到 100->4
 
    }
}
```



 示例 **4** : 

##### 异或

[**顶**](https://how2j.cn/k/operator/operator-bitwise/270.html#)[**折**](https://how2j.cn/k/operator/operator-bitwise/270.html#nowhere)

5的二进制是101
6的二进制是110
所以 5^6 对每一位进行异或运算，得到 011->3

一些特别情况：
任何数和自己进行异或 都等于 0
任何数和0 进行异或 都等于自己

代码比较复制代码

```java
public class HelloWorld {
    public static void main(String[] args) {
        int i  =5;
        int j = 6;
        System.out.println(Integer.toBinaryString(i)); //5的二进制是 101
        System.out.println(Integer.toBinaryString(j)); //6的二进制是110
        System.out.println(i^j); //所以 5^6 对每一位进行或运算，得到 011->3
         
        System.out.println(i^0);
        System.out.println(i^i);
    }
}
```



 示例 **5** : 

##### 取非

[**顶**](https://how2j.cn/k/operator/operator-bitwise/270.html#)[**折**](https://how2j.cn/k/operator/operator-bitwise/270.html#nowhere)

5 的二进制是 00000101
所以取反即为 11111010
这个二进制换算成十进制即为-6

代码比较复制代码

```java
public class HelloWorld {
    public static void main(String[] args) {
        byte i  =5;
         
        System.out.println(Integer.toBinaryString(i)); //5的二进制是00000101,所以取非即为11111010,即为-6
         
        System.out.println(~i);
         
    }
     
}
```



 示例 **6** : 

##### 左移 右移

[**顶**](https://how2j.cn/k/operator/operator-bitwise/270.html#)[**折**](https://how2j.cn/k/operator/operator-bitwise/270.html#nowhere)

左移：根据一个整数的二进制表达，将其每一位都向左移动，最右边一位补0
右移：根据一个整数的二进制表达，将其每一位都向右移动

代码比较复制代码

```java
public class HelloWorld {
    public static void main(String[] args) {
        byte i  =6;
         
        //6的二进制是110
        System.out.println(Integer.toBinaryString(i));
        //6向左移1位后，变成1100，对应的10进制是12
        System.out.println(i<<1);
        //6向右移1位后，变成11，对应的10进制是3
        System.out.println(i>>1);
    }
     
}
```



 示例 **7** : 

##### 练习-快速计算2x16 

  [**顶**](https://how2j.cn/k/operator/operator-bitwise/270.html#)[**折**](https://how2j.cn/k/operator/operator-bitwise/270.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/operator/operator-bitwise/270.html#nowhere)

不用乘法符号(*) 计算 2x16



 示例 **8** : 

##### 答案-快速计算2x16 

[**顶**](https://how2j.cn/k/operator/operator-bitwise/270.html#)[**折**](https://how2j.cn/k/operator/operator-bitwise/270.html#nowhere)

查看答案 在查看答案前，尽量先自己完成，碰到问题再来查看答案，收获会更多

 示例 **9** : 

##### 带符号右移与无符号右移

[**顶**](https://how2j.cn/k/operator/operator-bitwise/270.html#)[**折**](https://how2j.cn/k/operator/operator-bitwise/270.html#nowhere)

**带符号右移 >>**
对于正数， 带符号右移 >> 会把所有的位右移，并在最前面补0
对于负数， 带符号右移 >> 会把所有的位右移，并在最前面补1
**无符号右移>>>**
如果是一个负数，那么对应的二进制的第一位是1
无符号右移>>>会把第一位的1也向右移动，导致移动后，第一位变成0
这样就会使得负数在无符号右移后，得到一个正数
**
简单的说：**
**带符号右移 >>** 移动后正的还是正的，负的还是负的,**符号不变**
**无符号右移>>>**移动后，**变正的了**

代码比较复制代码

[代码行数较多，请点击查看 ![img](https://static.how2j.cn/code.png)](https://how2j.cn/k/operator/operator-bitwise/270.html#nowhere)



 示例 **10** : 

##### 练习-位操作符 

  [**顶**](https://how2j.cn/k/operator/operator-bitwise/270.html#)[**折**](https://how2j.cn/k/operator/operator-bitwise/270.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/operator/operator-bitwise/270.html#nowhere)

 

int i = 3; // 二进制是11

int j = 2; // 二进制是10

int c = ((i | j) ^ (i & j)) << 2 >>> 1;

 



心算答案，不要一来就放在eclipse中计算结果

---

#### 赋值操作符

 示例 **1** : 

##### 赋值操作

[**顶**](https://how2j.cn/k/operator/operator-assignment/268.html#)[**折**](https://how2j.cn/k/operator/operator-assignment/268.html#nowhere)

赋值操作的操作顺序是从右到左
int i = 5+5;
首先进行5+5的运算，得到结果10，然后把10这个值，赋给i

代码比较复制代码

```java
public class HelloWorld {
    public static void main(String[] args) {
        int i = 5+5;
    }
}
```



 示例 **2** : 

##### 对本身进行运算，并赋值

[**顶**](https://how2j.cn/k/operator/operator-assignment/268.html#)[**折**](https://how2j.cn/k/operator/operator-assignment/268.html#nowhere)

+=即自加
i+=2;
等同于
i=i+2;
其他的 -= , *= , /= , %= , &= , |= , ^= , >>= , >>>= 都是类似，不做赘述

代码比较复制代码

```java
public class HelloWorld {
    public static void main(String[] args) {
        int i =3;
        i+=2;
        System.out.println(i);
         
        int j=3;
        j=j+2;
        System.out.println(j);     
 
    }
}
```



 示例 **3** : 

##### 练习-赋值操作符 

  [**顶**](https://how2j.cn/k/operator/operator-assignment/268.html#)[**折**](https://how2j.cn/k/operator/operator-assignment/268.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/operator/operator-assignment/268.html#nowhere)

 

int i = 1;

i+=++i;

 


心算i的值是？

---

#### 三元操作符

?:

 示例 **1** : 

##### 三元操作符

[**顶**](https://how2j.cn/k/operator/operator-ternary/269.html#)[**折**](https://how2j.cn/k/operator/operator-ternary/269.html#nowhere)

表达式?值1:值2
如果表达式为真 返回值1
如果表达式为假 返回值2

关于[if语句](https://how2j.cn/k/control-flow/control-flow-if/271.html)的详解讲解在[后面章节](https://how2j.cn/k/control-flow/control-flow-if/271.html)

代码比较复制代码

```java
public class HelloWorld {
    public static void main(String[] args) {
 
        int i = 5;
        int j = 6;
 
        int k = i < j ? 99 : 88;
 
        // 相当于
        if (i < j) {
            k = 99;
        } else {
            k = 88;
        }
 
        System.out.println(k);
 
    }
}
```



 示例 **2** : 

##### 练习-判断是否是工作日 

  [**顶**](https://how2j.cn/k/operator/operator-ternary/269.html#)[**折**](https://how2j.cn/k/operator/operator-ternary/269.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/operator/operator-ternary/269.html#nowhere)

通过[Scanner](https://how2j.cn/k/operator/operator-scanner/658.html)输入一个**1-7**之间的整数，使用三元操作符判断是工作日还是周末？

![练习-判断是否是工作日](https://stepimagewm.how2j.cn/2154.png)



 示例 **3** : 

## 

#### 操作符Scanner

