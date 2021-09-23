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

#### 数学方法

#### 格式化输出

#### 字符

#### 字符串

#### 操纵字符串

#### 比较字符串

#### StringBuffer

#### MyStringBuffer