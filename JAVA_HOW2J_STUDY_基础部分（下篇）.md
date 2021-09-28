# JAVA_HOW2J_STUDY_基础部分（下篇）

[toc]



## JAVA基础

### 数字与字符串

#### 装箱拆箱

 步骤 **1** : 

##### 封装类

[**顶**](https://how2j.cn/k/number-string/number-string-wrap/22.html#)[**折**](https://how2j.cn/k/number-string/number-string-wrap/22.html#nowhere)

所有的**基本类型**，都有对应的**类类型**
比如int对应的类是Integer
这种类就叫做封装类

代码比较复制代码

```java
package digit;
 
public class TestNumber {
 
    public static void main(String[] args) {
        int i = 5;
         
        //把一个基本类型的变量,转换为Integer对象
        Integer it = new Integer(i);
        //把一个Integer对象，转换为一个基本类型的int
        int i2 = it.intValue();
         
    }
}
```



 步骤 **2** : 

##### Number类

[**顶**](https://how2j.cn/k/number-string/number-string-wrap/22.html#)[**折**](https://how2j.cn/k/number-string/number-string-wrap/22.html#nowhere)

数字封装类有
Byte,Short,Integer,Long,Float,Double
这些类都是抽象类Number的子类

![Number类](https://stepimagewm.how2j.cn/672.png)

代码比较复制代码

```java
package digit;
 
public class TestNumber {
 
    public static void main(String[] args) {
        int i = 5;
         
        Integer it = new Integer(i);
        //Integer是Number的子类，所以打印true
        System.out.println(it instanceof Number);
    }
}
```



 步骤 **3** : 

##### 基本类型转封装类

[**顶**](https://how2j.cn/k/number-string/number-string-wrap/22.html#)[**折**](https://how2j.cn/k/number-string/number-string-wrap/22.html#nowhere)

代码比较复制代码

```java
package digit;
 
public class TestNumber {
 
    public static void main(String[] args) {
        int i = 5;
 
        //基本类型转换成封装类型
        Integer it = new Integer(i);
         
    }
}
```



 步骤 **4** : 

##### 封装类转基本类型

[**顶**](https://how2j.cn/k/number-string/number-string-wrap/22.html#)[**折**](https://how2j.cn/k/number-string/number-string-wrap/22.html#nowhere)

代码比较复制代码

```java
package digit;
 
public class TestNumber {
 
    public static void main(String[] args) {
        int i = 5;
 
        //基本类型转换成封装类型
        Integer it = new Integer(i);
         
        //封装类型转换成基本类型
        int i2 = it.intValue();
         
    }
}
```



 步骤 **5** : 

##### 自动装箱

[**顶**](https://how2j.cn/k/number-string/number-string-wrap/22.html#)[**折**](https://how2j.cn/k/number-string/number-string-wrap/22.html#nowhere)

不需要调用构造方法，**通过=符号****自动**把 基本类型 转换为 类类型 就叫装箱

代码比较复制代码



```java
package digit;
 
public class TestNumber {
 
    public static void main(String[] args) {
        int i = 5;
 
        //基本类型转换成封装类型
        Integer it = new Integer(i);
         
        //自动转换就叫装箱
        Integer it2 = i;
         
    }
}
```



 步骤 **6** : 

##### 自动拆箱

[**顶**](https://how2j.cn/k/number-string/number-string-wrap/22.html#)[**折**](https://how2j.cn/k/number-string/number-string-wrap/22.html#nowhere)

不需要调用Integer的intValue方法，通过=就自动转换成int类型，就叫拆箱

代码比较复制代码

```java
package digit;
  
public class TestNumber {
  
    public static void main(String[] args) {
        int i = 5;
  
        Integer it = new Integer(i);
          
        //封装类型转换成基本类型
        int i2 = it.intValue();
         
        //自动转换就叫拆箱
        int i3 = it;
          
    }
}
```



 步骤 **7** : 

##### int的最大值，最小值

[**顶**](https://how2j.cn/k/number-string/number-string-wrap/22.html#)[**折**](https://how2j.cn/k/number-string/number-string-wrap/22.html#nowhere)

int的最大值可以通过其对应的封装类Integer.MAX_VALUE获取

代码比较复制代码

```java
package digit;
  
public class TestNumber {
  
    public static void main(String[] args) {
 
        //int的最大值
        System.out.println(Integer.MAX_VALUE);
        //int的最小值      
        System.out.println(Integer.MIN_VALUE);
          
    }
}
```



 步骤 **8** : 

##### 练习-装箱拆箱 

  [**顶**](https://how2j.cn/k/number-string/number-string-wrap/22.html#)[**折**](https://how2j.cn/k/number-string/number-string-wrap/22.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/number-string/number-string-wrap/22.html#nowhere)

\1. 对byte,short,float,double进行自动拆箱和自动装箱

\2. byte和Integer之间能否进行自动拆箱和自动装箱

\3. 通过Byte获取byte的最大值

#### 字符串转换

 步骤 **1** : 

##### 数字转字符串

[**顶**](https://how2j.cn/k/number-string/number-string-parse/317.html#)[**折**](https://how2j.cn/k/number-string/number-string-parse/317.html#nowhere)

方法1： 使用String类的静态方法valueOf
方法2： 先把基本类型装箱为对象，然后调用对象的toString

代码比较复制代码

```java
package digit;
  
public class TestNumber {
  
    public static void main(String[] args) {
        int i = 5;
         
        //方法1
        String str = String.valueOf(i);
         
        //方法2
        Integer it = i;
        String str2 = it.toString();
         
    }
}
```



 步骤 **2** : 

##### 字符串转数字

[**顶**](https://how2j.cn/k/number-string/number-string-parse/317.html#)[**折**](https://how2j.cn/k/number-string/number-string-parse/317.html#nowhere)

调用Integer的静态方法parseInt

代码比较复制代码

```java
package digit;
  
public class TestNumber {
  
    public static void main(String[] args) {
 
        String str = "999";
         
        int i= Integer.parseInt(str);
         
        System.out.println(i);
         
    }
}
```



 步骤 **3** : 

##### 练习-字符串转换 

  [**顶**](https://how2j.cn/k/number-string/number-string-parse/317.html#)[**折**](https://how2j.cn/k/number-string/number-string-parse/317.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/number-string/number-string-parse/317.html#nowhere)

参考上述步骤
把浮点数 3.14 转换为 字符串 "3.14"
再把字符串 “3.14” 转换为 浮点数 3.14

如果字符串是 3.1a4，转换为浮点数会得到什么？

#### 数学方法

java.lang.Math提供了一些常用的数学运算方法，并且都是以静态方法的形式存在

 步骤 **1** : 

##### 四舍五入, 随机数，开方，次方，π，自然常数

[**顶**](https://how2j.cn/k/number-string/number-string-math/319.html#)[**折**](https://how2j.cn/k/number-string/number-string-math/319.html#nowhere)

代码比较复制代码

```java
package digit;
  
public class TestNumber {
  
    public static void main(String[] args) {
        float f1 = 5.4f;
        float f2 = 5.5f;
        //5.4四舍五入即5
        System.out.println(Math.round(f1));
        //5.5四舍五入即6
        System.out.println(Math.round(f2));
         
        //得到一个0-1之间的随机浮点数（取不到1）
        System.out.println(Math.random());
         
        //得到一个0-10之间的随机整数 （取不到10）
        System.out.println((int)( Math.random()*10));
        //开方
        System.out.println(Math.sqrt(9));
        //次方（2的4次方）
        System.out.println(Math.pow(2,4));
         
        //π
        System.out.println(Math.PI);
         
        //自然常数
        System.out.println(Math.E);
    }
}
```



 步骤 **2** : 

##### 练习-数学方法 

  [**顶**](https://how2j.cn/k/number-string/number-string-math/319.html#)[**折**](https://how2j.cn/k/number-string/number-string-math/319.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/number-string/number-string-math/319.html#nowhere)

这个图是自然对数的计算方式。
借助Math的方法，把自然对数计算出来，看看经过自己计算的自然对数和Math.E的区别有多大

![练习-数学方法](https://stepimagewm.how2j.cn/2326.png)



 步骤 **3** : 

##### 答案-数学方法 

[**顶**](https://how2j.cn/k/number-string/number-string-math/319.html#)[**折**](https://how2j.cn/k/number-string/number-string-math/319.html#nowhere)

查看答案 在查看答案前，尽量先自己完成，碰到问题再来查看答案，收获会更多

 步骤 **4** : 

##### 练习-质数 

  [**顶**](https://how2j.cn/k/number-string/number-string-math/319.html#)[**折**](https://how2j.cn/k/number-string/number-string-math/319.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/number-string/number-string-math/319.html#nowhere)

统计找出一千万以内，一共有多少质数

质数概念: 只能被1和自己整除的数
举例:
5只能被 1和5整除，所以是质数
8可以被2整除，所以不是质数

![练习-质数](https://stepimagewm.how2j.cn/2331.png)

#### 格式化输出

 步骤 **1** : 

##### 格式化输出

[**顶**](https://how2j.cn/k/number-string/number-string-foramt/320.html#)[**折**](https://how2j.cn/k/number-string/number-string-foramt/320.html#nowhere)

如果不使用格式化输出，就需要进行字符串连接，如果变量比较多，拼接就会显得繁琐
使用格式化输出，就可以简洁明了

%s 表示字符串
%d 表示数字
%n 表示换行

代码比较复制代码

```java
package digit;
  
public class TestNumber {
  
    public static void main(String[] args) {
 
        String name ="盖伦";
        int kill = 8;
        String title="超神";
         
        //直接使用+进行字符串连接，编码感觉会比较繁琐，并且维护性差,易读性差
        String sentence = name+ " 在进行了连续 " + kill + " 次击杀后，获得了 " + title +" 的称号";
         
        System.out.println(sentence);
         
        //使用格式化输出
        //%s表示字符串，%d表示数字,%n表示换行
        String sentenceFormat ="%s 在进行了连续 %d 次击杀后，获得了 %s 的称号%n";
        System.out.printf(sentenceFormat,name,kill,title);
         
    }
}
```



 步骤 **2** : 

##### printf和format

[**顶**](https://how2j.cn/k/number-string/number-string-foramt/320.html#)[**折**](https://how2j.cn/k/number-string/number-string-foramt/320.html#nowhere)

printf和format能够达到一模一样的效果，[如何通过eclipse查看java源代码](https://how2j.cn/k/helloworld/helloworld-eclipse-tips/300.html#step706) 可以看到，在printf中直接调用了format

![printf和format](https://stepimagewm.how2j.cn/680.png)

代码比较复制代码

```java
package digit;
  
public class TestNumber {
  
    public static void main(String[] args) {
 
        String name ="盖伦";
        int kill = 8;
        String title="超神";
         
        String sentenceFormat ="%s 在进行了连续 %d 次击杀后，获得了 %s 的称号%n";
        //使用printf格式化输出
        System.out.printf(sentenceFormat,name,kill,title);
        //使用format格式化输出
        System.out.format(sentenceFormat,name,kill,title);
         
    }
}
```



 步骤 **3** : 

##### 换行符

[**顶**](https://how2j.cn/k/number-string/number-string-foramt/320.html#)[**折**](https://how2j.cn/k/number-string/number-string-foramt/320.html#nowhere)

**换行符**就是另起一行 --- '\n' 换行（newline）
**回车符**就是回到一行的开头 --- '\r' 回车（return）
在eclipse里敲一个回车，实际上是**回车换行符**
Java是跨平台的编程语言，同样的代码，可以在不同的平台使用，比如Windows,Linux,Mac
然而在不同的操作系统，换行符是不一样的
（1）在DOS和Windows中，每行结尾是 “\r\n”；
（2）Linux系统里，每行结尾只有 “\n”；
（3）Mac系统里，每行结尾是只有 "\r"。
为了使得同一个java程序的换行符在所有的操作系统中都有一样的表现，使用%n，就可以做到平台无关的换行

代码比较复制代码

```java
package digit;
  
public class TestNumber {
  
    public static void main(String[] args) {
 
        System.out.printf("这是换行符%n");
        System.out.printf("这是换行符%n");
         
    }
}
```



 步骤 **4** : 

##### 总长度，左对齐，补0，千位分隔符，小数点位数，本地化表达

[**顶**](https://how2j.cn/k/number-string/number-string-foramt/320.html#)[**折**](https://how2j.cn/k/number-string/number-string-foramt/320.html#nowhere)

其他常用的格式化方式

![总长度，左对齐，补0，千位分隔符，小数点位数，本地化表达](https://stepimagewm.how2j.cn/683.png)

代码比较复制代码

```java
package digit;
  
import java.util.Locale;
   
public class TestNumber {
   
    public static void main(String[] args) {
        int year = 2020;
        //总长度，左对齐，补0，千位分隔符，小数点位数，本地化表达
          
        //直接打印数字
        System.out.format("%d%n",year);
        //总长度是8,默认右对齐
        System.out.format("%8d%n",year);
        //总长度是8,左对齐
        System.out.format("%-8d%n",year);
        //总长度是8,不够补0
        System.out.format("%08d%n",year);
        //千位分隔符
        System.out.format("%,8d%n",year*10000);
  
        //小数点位数
        System.out.format("%.2f%n",Math.PI);
          
        //不同国家的千位分隔符
        System.out.format(Locale.FRANCE,"%,.2f%n",Math.PI*10000);
        System.out.format(Locale.US,"%,.2f%n",Math.PI*10000);
        System.out.format(Locale.UK,"%,.2f%n",Math.PI*10000);
          
    }
}
```





 步骤 **5** : 

##### 练习-黄鹤 

  [**顶**](https://how2j.cn/k/number-string/number-string-foramt/320.html#)[**折**](https://how2j.cn/k/number-string/number-string-foramt/320.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/number-string/number-string-foramt/320.html#nowhere)

借助[Scanner](https://how2j.cn/k/operator/operator-scanner/658.html) 读取字符串数据，然后用格式化输出下面

**浙江温州**最大**皮革厂****江南皮革厂**倒闭了，王八蛋老板**黄鹤**吃喝嫖赌，欠下了**3.5**个亿，带着他的小姨子跑了!我们没有办法，拿着**钱包**抵工资!原价都是一**百**多、两**百**多、三**百**多的**钱包**，现在全部只卖二十块，统统只要二十块!**黄鹤**王八蛋，你不是人!我们辛辛苦苦给你干了大半年，你不发工资，你还我血汗钱，还我血汗钱!

![练习-黄鹤](https://stepimagewm.how2j.cn/2199.png)

#### 字符

 示例 **1** : 

##### 保存一个字符的时候使用char

[**顶**](https://how2j.cn/k/number-string/number-string-character/323.html#)[**折**](https://how2j.cn/k/number-string/number-string-character/323.html#nowhere)

代码比较复制代码

```java
package character;
 
public class TestChar {
 
    public static void main(String[] args) {
        char c1 = 'a';
        char c2 = '1';//字符1,而非数字1
        char c3 = '中';//汉字字符
        char c4 = 'ab'; //只能放一个字符
         
    }
}
```



 示例 **2** : 

##### char对应的封装类

[**顶**](https://how2j.cn/k/number-string/number-string-character/323.html#)[**折**](https://how2j.cn/k/number-string/number-string-character/323.html#nowhere)

char对应的封装类是Character
装箱拆箱概念，参考 [拆箱装箱](https://how2j.cn/k/number-string/number-string-wrap/22.html)

代码比较复制代码

```java
package character;
 
public class TestChar {
 
    public static void main(String[] args) {
        char c1 = 'a';
        Character c = c1; //自动装箱
        c1 = c;//自动拆箱
         
    }
}
```



 示例 **3** : 

##### Character常见方法

[**顶**](https://how2j.cn/k/number-string/number-string-character/323.html#)[**折**](https://how2j.cn/k/number-string/number-string-character/323.html#nowhere)

代码比较复制代码

```java
package character;
 
public class TestChar {
 
    public static void main(String[] args) {
         
        System.out.println(Character.isLetter('a'));//判断是否为字母
        System.out.println(Character.isDigit('a')); //判断是否为数字
        System.out.println(Character.isWhitespace(' ')); //是否是空白
        System.out.println(Character.isUpperCase('a')); //是否是大写
        System.out.println(Character.isLowerCase('a')); //是否是小写
         
        System.out.println(Character.toUpperCase('a')); //转换为大写
        System.out.println(Character.toLowerCase('A')); //转换为小写
 
        String a = 'a'; //不能够直接把一个字符转换成字符串
        String a2 = Character.toString('a'); //转换为字符串
         
    }
}
```



 示例 **4** : 

##### 常见转义

[**顶**](https://how2j.cn/k/number-string/number-string-character/323.html#)[**折**](https://how2j.cn/k/number-string/number-string-character/323.html#nowhere)

![常见转义](https://stepimagewm.how2j.cn/696.png)

代码比较复制代码

```java
package character;
  
public class TestChar {
  
    public static void main(String[] args) {
        System.out.println("使用空格无法达到对齐的效果");
        System.out.println("abc def");
        System.out.println("ab def");
        System.out.println("a def");
          
        System.out.println("使用\\t制表符可以达到对齐的效果");
        System.out.println("abc\tdef");
        System.out.println("ab\tdef");
        System.out.println("a\tdef");
         
        System.out.println("一个\\t制表符长度是8");
        System.out.println("12345678def");
          
        System.out.println("换行符 \\n");
        System.out.println("abc\ndef");
 
        System.out.println("单引号 \\'");
        System.out.println("abc\'def");
        System.out.println("双引号 \\\"");
        System.out.println("abc\"def");
        System.out.println("反斜杠本身 \\");
        System.out.println("abc\\def");
    }
}
```



 示例 **5** : 

##### 练习-Character 

  [**顶**](https://how2j.cn/k/number-string/number-string-character/323.html#)[**折**](https://how2j.cn/k/number-string/number-string-character/323.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/number-string/number-string-character/323.html#nowhere)

通过[Scanner](https://how2j.cn/k/operator/operator-scanner/658.html#step2330)从控制台读取字符串，然后把[字符串转换为字符数组](https://how2j.cn/k/number-string/number-string-manipulate/325.html#step719)
参考的转换方式:

 

String str = "abc123";

char[] cs = str.toCharArray(); 

 



转换为字符数组后，筛选出控制台读取到的字符串中的大写字母和数字，并打印出来

![练习-Character](https://stepimagewm.how2j.cn/2328.png)

#### 字符串

 示例 **1** : 

##### 创建字符串

[**顶**](https://how2j.cn/k/number-string/number-string-string/324.html#)[**折**](https://how2j.cn/k/number-string/number-string-string/324.html#nowhere)

字符串即字符的组合，在Java中，字符串是一个类，所以我们见到的字符串都是对象
常见创建字符串手段：
\1. 每当有一个**字面值**出现的时候，虚拟机就会创建一个字符串
\2. 调用String的构造方法创建一个字符串对象
\3. 通过+加号进行字符串拼接也会创建新的字符串对象

代码比较复制代码

```java
package character;
 
public class TestString {
 
    public static void main(String[] args) {
        String garen ="盖伦"; //字面值,虚拟机碰到字面值就会创建一个字符串对象
         
        String teemo = new String("提莫"); //创建了两个字符串对象
         
        char[] cs = new char[]{'崔','斯','特'};
         
        String hero = new String(cs);//  通过字符数组创建一个字符串对象
         
        String hero3 = garen + teemo;//  通过+加号进行字符串拼接
    }
}
```



 示例 **2** : 

##### final

[**顶**](https://how2j.cn/k/number-string/number-string-string/324.html#)[**折**](https://how2j.cn/k/number-string/number-string-string/324.html#nowhere)

String 被修饰为final,所以是不能被继承的

代码比较复制代码

```java
package character;
 
public class TestString {
 
    public static void main(String[] args) {
        MyString str = new MyString();
         
    }
     
        /*这里会报错，因为String不能被继承*/
    static class MyString extends String{
         
    }
     
}
```



 示例 **3** : 

##### immutable

[**顶**](https://how2j.cn/k/number-string/number-string-string/324.html#)[**折**](https://how2j.cn/k/number-string/number-string-string/324.html#nowhere)

immutable 是指不可改变的
比如创建了一个字符串对象
String garen ="盖伦";
**不可改变**的具体含义是指：
不能增加长度
不能减少长度
不能插入字符
不能删除字符
不能修改字符
一旦创建好这个字符串，里面的内容 **永远** 不能改变

String 的表现就像是一个**常量**

代码比较复制代码

```java
package character;
  
public  class TestString {
  
    public static void main(String[] args) {
        String garen ="盖伦";
         
    }
}
```



 示例 **4** : 

##### 字符串格式化

[**顶**](https://how2j.cn/k/number-string/number-string-string/324.html#)[**折**](https://how2j.cn/k/number-string/number-string-string/324.html#nowhere)

如果不使用字符串格式化，就需要进行字符串连接，如果变量比较多，拼接就会显得繁琐
使用**字符串格式化**，就可以**简洁明了**
更多的格式化规则，参考[格式化输出](https://how2j.cn/k/number-string/number-string-foramt/320.html)

代码比较复制代码

```java
package character;
   
public class TestString {
   
    public static void main(String[] args) {
  
        String name ="盖伦";
        int kill = 8;
        String title="超神";
          
        //直接使用+进行字符串连接，编码感觉会比较繁琐，并且维护性差,易读性差
        String sentence = name+ " 在进行了连续 " + kill + " 次击杀后，获得了 " + title +" 的称号";
          
        System.out.println(sentence);
         
        //格式化字符串
        //%s表示字符串，%d表示数字,%n表示换行
        String sentenceFormat ="%s 在进行了连续 %d 次击杀后，获得了 %s 的称号%n";
         
        String sentence2 = String.format(sentenceFormat, name,kill,title);
         
        System.out.println(sentence2);
         
    }
}
```



 示例 **5** : 

##### 字符串长度

[**顶**](https://how2j.cn/k/number-string/number-string-string/324.html#)[**折**](https://how2j.cn/k/number-string/number-string-string/324.html#nowhere)

length方法返回当前字符串的长度
可以有长度为0的字符串,即空字符串

代码比较复制代码

```java
package character;
   
public class TestString {
   
    public static void main(String[] args) {
  
        String name ="盖伦";
         
        System.out.println(name.length());
         
        String unknowHero = "";
         
        //可以有长度为0的字符串,即空字符串
        System.out.println(unknowHero.length());
          
    }
}
```



 示例 **6** : 

##### 练习-随机字符串 

  [**顶**](https://how2j.cn/k/number-string/number-string-string/324.html#)[**折**](https://how2j.cn/k/number-string/number-string-string/324.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/number-string/number-string-string/324.html#nowhere)

创建一个长度是5的随机字符串，随机字符有可能是数字，大写字母或者小写字母

**给点提示:** 数字和字符之间可以通过互相转换

 

```tex
char c = 'A';

short s = (short) c;
```



 


通过这个手段就能够知道字符 a-z A-Z 0-9 所对应的数字的区间了

需要用到[ASCII码](https://how2j.cn/k/io/io-bytestream/340.html#step766)对照表



 示例 **7** : 

##### 答案-随机字符串 

[**顶**](https://how2j.cn/k/number-string/number-string-string/324.html#)[**折**](https://how2j.cn/k/number-string/number-string-string/324.html#nowhere)

查看答案 在查看答案前，尽量先自己完成，碰到问题再来查看答案，收获会更多

 示例 **8** : 

##### 练习-字符串数组排序 

  [**顶**](https://how2j.cn/k/number-string/number-string-string/324.html#)[**折**](https://how2j.cn/k/number-string/number-string-string/324.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/number-string/number-string-string/324.html#nowhere)

创建一个长度是8的字符串数组
使用8个长度是5的随机字符串初始化这个数组
对这个数组进行排序，按照每个字符串的首字母排序(无视大小写)

**注**1： 不能使用Arrays.sort() 要自己写
**注**2： 无视大小写，即 Axxxx 和 axxxxx 没有先后顺序



 示例 **9** : 

##### 答案-字符串数组排序 

[**顶**](https://how2j.cn/k/number-string/number-string-string/324.html#)[**折**](https://how2j.cn/k/number-string/number-string-string/324.html#nowhere)

查看答案 在查看答案前，尽量先自己完成，碰到问题再来查看答案，收获会更多

 示例 **10** : 

##### 练习-穷举法破解密码 

  [**顶**](https://how2j.cn/k/number-string/number-string-string/324.html#)[**折**](https://how2j.cn/k/number-string/number-string-string/324.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/number-string/number-string-string/324.html#nowhere)

\1. 生成一个长度是3的[随机字符串](https://how2j.cn/k/number-string/number-string-string/324.html#step2361)，把这个字符串作为当做密码

\2. 使用穷举法生成长度是3个字符串，匹配上述生成的密码

要求： 分别使用多层for循环 和 递归解决上述问题





#### 操纵字符串

#### 比较字符串

#### StringBuffer

#### MyStringBuffer