# JAVA-HOW2J-STUDY-中级（上篇）

[toc]

## JAVA中级

### 异常处理

#### 什么是异常

异常定义：
导致程序的正常流程被中断的事件，叫做异常

 步骤 **1** : 

##### 文件不存在异常

[**顶**](https://how2j.cn/k/exception/exception-tutorial/332.html#)[**折**](https://how2j.cn/k/exception/exception-tutorial/332.html#nowhere)

比如要打开d盘的LOL.exe文件，这个文件是有可能不存在的
Java中通过 new FileInputStream(f) 试图打开某文件，就有可能抛出**文件不存在异常FileNotFoundException**
如果不处理该异常，就会有编译错误
处理办法参见 [异常处理](https://how2j.cn/k/exception/exception-trycatch/336.html)

代码比较复制代码

```java
package exception;
  
import java.io.File;
import java.io.FileInputStream;
  
public class TestException {
  
    public static void main(String[] args) {
          
        File f= new File("d:/LOL.exe");
          
        //试图打开文件LOL.exe，会抛出FileNotFoundException，如果不处理该异常，就会有编译错误
        new FileInputStream(f);
          
    }
}
```



 步骤 **2** : 

##### 练习-异常 

罗列出学习到目前为止，都接触过了哪些异常，分别在什么情况下会出现

---

#### 异常处理

异常处理常见手段： try catch finally throws



 步骤 **1** : 

##### try catch

[**顶**](https://how2j.cn/k/exception/exception-trycatch/336.html#)[**折**](https://how2j.cn/k/exception/exception-trycatch/336.html#nowhere)

1.将可能抛出FileNotFoundException **文件不存在异常**的代码放在try里
2.如果文件存在，就会顺序往下执行，并且不执行catch块中的代码
\3. 如果文件不存在，try 里的代码会立即终止，程序流程会运行到对应的catch块中
\4. e.printStackTrace(); 会打印出方法的调用痕迹，如此例，会打印出异常开始于TestException的第16行，这样就便于定位和分析到底哪里出了异常

![try catch](https://stepimagewm.how2j.cn/735.png)

代码比较复制代码

```java
package exception;
 
import java.io.File;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
 
public class TestException {
 
    public static void main(String[] args) {
         
        File f= new File("d:/LOL.exe");
         
        try{
            System.out.println("试图打开 d:/LOL.exe");
            new FileInputStream(f);
            System.out.println("成功打开");
        }
        catch(FileNotFoundException e){
            System.out.println("d:/LOL.exe不存在");
            e.printStackTrace();
        }
         
    }
}
```



 步骤 **2** : 

##### 使用异常的父类进行catch

[**顶**](https://how2j.cn/k/exception/exception-trycatch/336.html#)[**折**](https://how2j.cn/k/exception/exception-trycatch/336.html#nowhere)

FileNotFoundException是Exception的子类，使用Exception也可以catch住FileNotFoundException

代码比较复制代码

```java
package exception;
  
import java.io.File;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
  
public class TestException {
  
    public static void main(String[] args) {
          
        File f= new File("d:/LOL.exe");
          
        try{
            System.out.println("试图打开 d:/LOL.exe");
            new FileInputStream(f);
            System.out.println("成功打开");
        }
         
        catch(Exception e){
            System.out.println("d:/LOL.exe不存在");
            e.printStackTrace();
        }
          
    }
}
```



 步骤 **3** : 

##### 多异常捕捉办法1

[**顶**](https://how2j.cn/k/exception/exception-trycatch/336.html#)[**折**](https://how2j.cn/k/exception/exception-trycatch/336.html#nowhere)

有的时候一段代码会抛出多种异常，比如

 

new FileInputStream(f);

Date d = sdf.parse("2016-06-03");

 


这段代码，会抛出 文件不存在异常 FileNotFoundException 和 解析异常ParseException
解决办法之一是分别进行catch

 

catch (FileNotFoundException e) {

​    System.out.println("d:/LOL.exe不存在");

​    e.printStackTrace();

} catch (ParseException e) {

​    System.out.println("日期格式解析错误");

​    e.printStackTrace();

}

 

代码比较复制代码

```java
package exception;
 
import java.io.File;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.Date;
 
public class TestException {
 
    public static void main(String[] args) {
 
        File f = new File("d:/LOL.exe");
 
        try {
            System.out.println("试图打开 d:/LOL.exe");
            new FileInputStream(f);
            System.out.println("成功打开");
            SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd");
            Date d = sdf.parse("2016-06-03");
        } catch (FileNotFoundException e) {
            System.out.println("d:/LOL.exe不存在");
            e.printStackTrace();
        } catch (ParseException e) {
            System.out.println("日期格式解析错误");
            e.printStackTrace();
        }
    }
}
```



 步骤 **4** : 

##### 多异常捕捉办法2

[**顶**](https://how2j.cn/k/exception/exception-trycatch/336.html#)[**折**](https://how2j.cn/k/exception/exception-trycatch/336.html#nowhere)

另一个种办法是把多个异常，放在一个catch里统一捕捉

 

catch (FileNotFoundException | ParseException e) {

 


这种方式从 JDK7开始支持，好处是捕捉的代码**更紧凑**，不足之处是，一旦发生异常，**不能确定到底是哪种异常**，需要通过instanceof 进行判断具体的异常类型

 

if (e instanceof FileNotFoundException)

​	System.out.println("d:/LOL.exe不存在");

if (e instanceof ParseException)

​	System.out.println("日期格式解析错误");

 

代码比较复制代码

```java
package exception;
 
import java.io.File;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.Date;
 
public class TestException {
 
    public static void main(String[] args) {
 
        File f = new File("d:/LOL.exe");
 
        try {
            System.out.println("试图打开 d:/LOL.exe");
            new FileInputStream(f);
            System.out.println("成功打开");
            SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd");
            Date d = sdf.parse("2016-06-03");
        } catch (FileNotFoundException | ParseException e) {
            if (e instanceof FileNotFoundException)
                System.out.println("d:/LOL.exe不存在");
            if (e instanceof ParseException)
                System.out.println("日期格式解析错误");
 
            e.printStackTrace();
        }
 
    }
}
```



 步骤 **5** : 

##### finally

[**顶**](https://how2j.cn/k/exception/exception-trycatch/336.html#)[**折**](https://how2j.cn/k/exception/exception-trycatch/336.html#nowhere)

无论是否出现异常，finally中的代码都会被执行

代码比较复制代码

```java
package exception;
 
import java.io.File;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
 
public class TestException {
 
    public static void main(String[] args) {
         
        File f= new File("d:/LOL.exe");
         
        try{
            System.out.println("试图打开 d:/LOL.exe");
            new FileInputStream(f);
            System.out.println("成功打开");
        }
        catch(FileNotFoundException e){
            System.out.println("d:/LOL.exe不存在");
            e.printStackTrace();
        }
        finally{
            System.out.println("无论文件是否存在， 都会执行的代码");
        }
    }
}
```



 步骤 **6** : 

##### throws

[**顶**](https://how2j.cn/k/exception/exception-trycatch/336.html#)[**折**](https://how2j.cn/k/exception/exception-trycatch/336.html#nowhere)

考虑如下情况：
主方法调用method1
method1调用method2
method2中打开文件

method2中需要进行异常处理
但是method2**不打算处理**，而是把这个异常通过**throws****抛出去**
那么method1就会**接到该异常**。 处理办法也是两种，要么是try catch处理掉，要么也是**抛出去**。
method1选择本地try catch住 一旦try catch住了，就相当于把这个异常消化掉了，主方法在调用method1的时候，就不需要进行异常处理了

代码比较复制代码

```java
package exception;
 
import java.io.File;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
 
public class TestException {
 
    public static void main(String[] args) {
        method1();
 
    }
 
    private static void method1() {
        try {
            method2();
        } catch (FileNotFoundException e) {
            // TODO Auto-generated catch block
            e.printStackTrace();
        }
 
    }
 
    private static void method2() throws FileNotFoundException {
 
        File f = new File("d:/LOL.exe");
 
        System.out.println("试图打开 d:/LOL.exe");
        new FileInputStream(f);
        System.out.println("成功打开");
 
    }
}
```



 步骤 **7** : 

##### throw和throws的区别

[**顶**](https://how2j.cn/k/exception/exception-trycatch/336.html#)[**折**](https://how2j.cn/k/exception/exception-trycatch/336.html#nowhere)

throws与throw这两个关键字接近，不过意义不一样，有如下区别：
\1. throws 出现在方法声明上，而throw通常都出现在方法体内。
\2. throws 表示出现异常的一种可能性，并不一定会发生这些异常；throw则是抛出了异常，执行throw则一定抛出了某个异常对象。



 步骤 **8** : 

##### 练习-异常处理 

假设有一个方法 public int method()， 会返回一个整数
在这个方法中有try catch 和 finally.
try 里返回 1
catch 里 返回 2
finally 里 返回3
那么，这个方法到底返回多少？

#### 异常分类

 步骤 **1** : 

##### 可查异常

[**顶**](https://how2j.cn/k/exception/exception-category/333.html#)[**折**](https://how2j.cn/k/exception/exception-category/333.html#nowhere)

可查异常： CheckedException
可查异常即**必须进行处理的异常**，要么try catch住,要么往外抛，谁调用，谁处理，比如 FileNotFoundException
如果不处理，编译器，就不让你通过

代码比较复制代码

```java
package exception;
  
import java.io.File;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
  
public class TestException {
  
    public static void main(String[] args) {
          
        File f= new File("d:/LOL.exe");
          
        try{
            System.out.println("试图打开 d:/LOL.exe");
            new FileInputStream(f);
            System.out.println("成功打开");
        }
        catch(FileNotFoundException e){
            System.out.println("d:/LOL.exe不存在");
            e.printStackTrace();
        }
          
    }
}
```





 步骤 **2** : 

##### 运行时异常

[**顶**](https://how2j.cn/k/exception/exception-category/333.html#)[**折**](https://how2j.cn/k/exception/exception-category/333.html#nowhere)

运行时异常RuntimeException指： **不是必须进行try catch的异常**
**常见运行时异常:**
除数不能为0异常:ArithmeticException
下标越界异常:ArrayIndexOutOfBoundsException
空指针异常:NullPointerException
在编写代码的时候，依然可以使用try catch throws进行处理，与可查异常不同之处在于，**即便不进行try catch，也不会有编译错误**
Java之所以会设计运行时异常的原因之一，是因为下标越界，空指针这些运行时异常**太过于普遍**，如果都需要进行捕捉，代码的可读性就会变得很糟糕。

代码比较复制代码

```java
package exception;
  
public class TestException {
  
    public static void main(String[] args) {
         
        //任何除数不能为0:ArithmeticException
        int k = 5/0;
         
        //下标越界异常：ArrayIndexOutOfBoundsException
        int j[] = new int[5];
        j[10] = 10;
         
        //空指针异常：NullPointerException
        String str = null;
        str.length();
   }
}
```



 步骤 **3** : 

##### 错误

[**顶**](https://how2j.cn/k/exception/exception-category/333.html#)[**折**](https://how2j.cn/k/exception/exception-category/333.html#nowhere)

错误Error，指的是**系统级别的异常**，通常是内存用光了
在**默认设置下**，一般java程序启动的时候，最大可以使用16m的内存
如例不停的给StringBuffer追加字符，很快就把内存使用光了。抛出**OutOfMemoryError**
与运行时异常一样，错误也是不要求强制捕捉的

代码比较复制代码

```java
package exception;
  
public class TestException {
  
    public static void main(String[] args) {
     
        StringBuffer sb =new StringBuffer();
         
        for (int i = 0; i < Integer.MAX_VALUE; i++) {
            sb.append('a');
        }
         
    }
 
}
```



 步骤 **4** : 

##### 三种分类

[**顶**](https://how2j.cn/k/exception/exception-category/333.html#)[**折**](https://how2j.cn/k/exception/exception-category/333.html#nowhere)

总体上异常分三类：
\1. 错误
\2. 运行时异常
\3. 可查异常

![三种分类](https://stepimagewm.how2j.cn/2412.png)



 步骤 **5** : 

##### 练习-异常分类 

  [**顶**](https://how2j.cn/k/exception/exception-category/333.html#)[**折**](https://how2j.cn/k/exception/exception-category/333.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/exception/exception-category/333.html#nowhere)

运行时异常 RuntimeException，能否被捕捉？

错误Error，能否被捕捉？

**面试题常问题：** 运行时异常与非运行时异常的区别

#### Throwable

 步骤 **1** : 

##### Throwable

[**顶**](https://how2j.cn/k/exception/exception-throwable/334.html#)[**折**](https://how2j.cn/k/exception/exception-throwable/334.html#nowhere)

Throwable是类，Exception和Error都继承了该类
所以在捕捉的时候，也可以使用Throwable进行捕捉
如图： 异常分**Error**和**Exception**
Exception里又分**运行时异常**和**可查异常**。

![Throwable](https://stepimagewm.how2j.cn/742.png)

代码比较复制代码

```java
package exception;
 
import java.io.File;
import java.io.FileInputStream;
 
public class TestException {
 
    public static void main(String[] args) {
 
        File f = new File("d:/LOL.exe");
 
        try {
            new FileInputStream(f);
            //使用Throwable进行异常捕捉
        } catch (Throwable t) {
            // TODO Auto-generated catch block
            t.printStackTrace();
        }
 
    }
}
```



 步骤 **2** : 

##### 练习-Throwable 

  [**顶**](https://how2j.cn/k/exception/exception-throwable/334.html#)[**折**](https://how2j.cn/k/exception/exception-throwable/334.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/exception/exception-throwable/334.html#nowhere)

在方法声明上，可以抛出指定的异常，比如FileNotFoundException
那么能否抛出Throwable这个类？

这个方法的调用者又该如何处理？



 步骤 **3** : 

#### 自定义异常

 示例 **1** : 

##### 创建自定义异常

[**顶**](https://how2j.cn/k/exception/exception-custom/337.html#)[**折**](https://how2j.cn/k/exception/exception-custom/337.html#nowhere)

一个英雄攻击另一个英雄的时候，如果发现另一个英雄已经挂了，就会抛出EnemyHeroIsDeadException
创建一个类EnemyHeroIsDeadException，并继承Exception
提供两个构造方法
\1. 无参的构造方法
\2. 带参的构造方法，并调用父类的对应的构造方法

代码比较复制代码

```java
class EnemyHeroIsDeadException extends Exception{
     
    public EnemyHeroIsDeadException(){
         
    }
    public EnemyHeroIsDeadException(String msg){
        super(msg);
    }
}
```



 示例 **2** : 

##### 抛出自定义异常

[**顶**](https://how2j.cn/k/exception/exception-custom/337.html#)[**折**](https://how2j.cn/k/exception/exception-custom/337.html#nowhere)

在Hero的attack方法中，当发现敌方英雄的血量为0的时候，抛出该异常
\1. 创建一个EnemyHeroIsDeadException实例
\2. 通过**throw** 抛出该异常
\3. 当前方法通过 **throws** 抛出该异常

在外部调用attack方法的时候，就需要进行捕捉，并且捕捉的时候，可以通过e.getMessage() 获取当时出错的具体原因

![抛出自定义异常](https://stepimagewm.how2j.cn/744.png)

代码比较复制代码

```java
package charactor;
  
public class Hero {
    public String name;
    protected float hp;
 
    public void attackHero(Hero h) throws EnemyHeroIsDeadException{
        if(h.hp == 0){
            throw new EnemyHeroIsDeadException(h.name + " 已经挂了,不需要施放技能" );
        }
    }
 
    public String toString(){
        return name;
    }
     
    class EnemyHeroIsDeadException extends Exception{
         
        public EnemyHeroIsDeadException(){
             
        }
        public EnemyHeroIsDeadException(String msg){
            super(msg);
        }
    }
      
    public static void main(String[] args) {
         
        Hero garen =  new Hero();
        garen.name = "盖伦";
        garen.hp = 616;
 
        Hero teemo =  new Hero();
        teemo.name = "提莫";
        teemo.hp = 0;
         
        try {
            garen.attackHero(teemo);
             
        } catch (EnemyHeroIsDeadException e) {
            // TODO Auto-generated catch block
            System.out.println("异常的具体原因:"+e.getMessage());
            e.printStackTrace();
        }
         
    }
}
```



 示例 **3** : 

##### 练习-自定义异常 

  [**顶**](https://how2j.cn/k/exception/exception-custom/337.html#)[**折**](https://how2j.cn/k/exception/exception-custom/337.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/exception/exception-custom/337.html#nowhere)

对[MyStringBuffer](https://how2j.cn/k/number-string/number-string-mystringbuilder/331.html)的插入和删除方法中的边界条件判断，用抛出异常来解决
例: insert(int pos, String b) , 当pos 是负数的时候，抛出**自定义异常**
需要实现自定义两种异常
IndexIsNagetiveException 下标为负异常
IndexIsOutofRangeException 下标超出范围异常
以下是需要调用这些异常的场景：

 ```tex
 pos<0
 抛出 IndexIsNagetiveException
  
 pos>length
 抛出 IndexIsOutofRangeException
 
 null==b
 抛出 NullPointerException
  
 start<0 
 抛出 IndexIsNagetiveException
 
 start>length
 抛出 IndexIsOutofRangeException
  
 end<0 
 抛出 IndexIsNagetiveException
  
 end>length
 抛出 IndexIsOutofRangeException 
 
 start>=end
 抛出 IndexIsOutofRangeException
 ```

**注意：** 接口IStringBuffer中声明的方法需要抛出异常



---



#### 综合练习

 步骤 **1** : 

##### 练习-异常综合1 

  [**顶**](https://how2j.cn/k/exception/exception-practise/338.html#)[**折**](https://how2j.cn/k/exception/exception-practise/338.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/exception/exception-practise/338.html#nowhere)

这是一个类图
Account类： 银行账号
属性： balance 余额
方法： getBalance() 获取余额
方法： deposit() 存钱
方法： withdraw() 取钱
OverdraftException： 透支异常，继承Exception
属性： deficit 透支额

![练习-异常综合1](https://stepimagewm.how2j.cn/745.png)

 步骤 **3** : 

##### 练习-异常综合2 

  [**顶**](https://how2j.cn/k/exception/exception-practise/338.html#)[**折**](https://how2j.cn/k/exception/exception-practise/338.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/exception/exception-practise/338.html#nowhere)

类： CheckingAccount 支票账户，具备透支额度，继承Account
属性：overdraftProtection 透支额度

![练习-异常综合2](https://stepimagewm.how2j.cn/746.png)

```java
------------------------练习1：Account ---------------------------
public class Account {
    /**
     * 余额
     */
    private double balance;
 
    public double getBalance() {
        System.out.println("当前余额为：" + balance);
        return balance;
    }
 
    public void deposit(double money) {
        balance += money;
        System.out.println("存款成功，余额为：" + balance);
    }
 
    public void withdraw(double money) throws OverdraftException {
        if ((balance - money) >= 0) {
            balance -= money;
            System.out.println("取款成功，余额为: " + balance);
        } else {
            balance -= money;
            //透支金额
            double deficit = balance;
            throw new OverdraftException("余额不足，取款失败！\n超支金额：" + deficit);
        }
    }
 
    static class OverdraftException extends Exception {
        public OverdraftException(String msg) {
            super(msg);
        }
    }
 
    public static void main(String[] args) {
        Account account = new Account();
        account.deposit(651.50);
        account.getBalance();
        try {
            account.withdraw(661);
        } catch (OverdraftException e) {
            e.printStackTrace();
        }
    }
}
 
------------------------练习2 ：overdraftProtection---------------------------
 
public class CheckingAccount extends Account {
    public void setOverdraftProtection(double overdraftProtection) {
        this.overdraftProtection = overdraftProtection;
    }
 
    public double getOverdraftProtection() {
        System.out.println("可用透支额度为： " + overdraftProtection);
        return overdraftProtection;
    }
 
    /**
     * 透支额度
     */
    private double overdraftProtection;
 
 
 
    @Override
    public void withdraw(double money) throws OverdraftException {
        double balance = getBalance();
        double overBalance = getOverdraftProtection();
        if ((balance - money) >= 0){
            balance -= money;
            System.out.println("取款成功，余额为: " + balance);
        } else if (((balance + overBalance) - money) >=0){
            balance -= money;
            overBalance += balance;
            System.out.println("取款成功，余额为: " + balance + "; " +
                    "\n剩余透支额度为：" + overBalance
                    );
        } else {
            balance += overBalance;
            balance -= money;
            //透支金额
            throw new OverdraftException("余额不足，取款失败！\n 超支金额：" + balance);
        }
    }
 
    public static void main(String[] args) {
        CheckingAccount checkingAccount = new CheckingAccount();
        checkingAccount.deposit(1988.50);
        checkingAccount.setOverdraftProtection(100);
        try {
            checkingAccount.withdraw(3000);
        } catch (OverdraftException e) {
            e.printStackTrace();
        }
    }
}
```





