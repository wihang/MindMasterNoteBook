# 多线程

[toc]



## 启动一个线程

多线程即在同一时间，可以做多件事情。

创建多线程有3种方式，分别是[继承线程类](https://how2j.cn/k/thread/thread-start/353.html#step778),[实现Runnable接口](https://how2j.cn/k/thread/thread-start/353.html#step779),[匿名类](https://how2j.cn/k/thread/thread-start/353.html#step780)



 步骤 **1** : 

### 线程概念

[**顶**](https://how2j.cn/k/thread/thread-start/353.html#)[**折**](https://how2j.cn/k/thread/thread-start/353.html#nowhere)

首先要理解进程(Processor)和线程(Thread)的区别
**进程：**启动一个LOL.exe就叫一个进程。 接着又启动一个DOTA.exe，这叫两个进程。
**线程：**线程是在进程内部同时做的事情，比如在LOL里，有很多事情要同时做，比如"盖伦” 击杀“提莫”，**同时**“赏金猎人”又在击杀“盲僧”，这就是由多线程来实现的。


此处代码演示的是**不使用多线程的情况**：
只有在盖伦杀掉提莫后，赏金猎人才开始杀盲僧

![线程概念](https://stepimagewm.how2j.cn/777.png)

- [Hero.java](https://how2j.cn/k/thread/thread-start/353.html#nowhere)

  - ```java
    package charactor;
     
    import java.io.Serializable;
      
    public class Hero{
        public String name;
        public float hp;
         
        public int damage;
         
        public void attackHero(Hero h) {
            try {
                //为了表示攻击需要时间，每次攻击暂停1000毫秒
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                // TODO Auto-generated catch block
                e.printStackTrace();
            }
            h.hp-=damage;
            System.out.format("%s 正在攻击 %s, %s的血变成了 %.0f%n",name,h.name,h.name,h.hp);
             
            if(h.isDead())
                System.out.println(h.name +"死了！");
        }
     
        public boolean isDead() {
            return 0>=hp?true:false;
        }
     
    }
    ```

  - 

- [TestThread.java](https://how2j.cn/k/thread/thread-start/353.html#nowhere)

  - ```java
    package multiplethread;
     
    import charactor.Hero;
     
    public class TestThread {
     
        public static void main(String[] args) {
             
            Hero gareen = new Hero();
            gareen.name = "盖伦";
            gareen.hp = 616;
            gareen.damage = 50;
     
            Hero teemo = new Hero();
            teemo.name = "提莫";
            teemo.hp = 300;
            teemo.damage = 30;
             
            Hero bh = new Hero();
            bh.name = "赏金猎人";
            bh.hp = 500;
            bh.damage = 65;
             
            Hero leesin = new Hero();
            leesin.name = "盲僧";
            leesin.hp = 455;
            leesin.damage = 80;
             
            //盖伦攻击提莫
            while(!teemo.isDead()){
                gareen.attackHero(teemo);
            }
     
            //赏金猎人攻击盲僧
            while(!leesin.isDead()){
                bh.attackHero(leesin);
            }
        }
         
    }
    ```

  - 

代码比较复制代码



 步骤 **2** : 

### 创建多线程-继承线程类

[**顶**](https://how2j.cn/k/thread/thread-start/353.html#)[**折**](https://how2j.cn/k/thread/thread-start/353.html#nowhere)

使用多线程，就可以做到盖伦在攻击提莫的**同时**，赏金猎人也在攻击盲僧
设计一个类KillThread **继承Thread**，**并且重写run方法**
启动线程办法： 实例化一个KillThread对象，并且调用其**start**方法
就可以观察到 赏金猎人攻击盲僧的**同时**，盖伦也在攻击提莫

![创建多线程-继承线程类](https://stepimagewm.how2j.cn/778.png)

- [KillThread.java](https://how2j.cn/k/thread/thread-start/353.html#nowhere)

  - ```java
    package multiplethread;
     
    import charactor.Hero;
     
    public class KillThread extends Thread{
         
        private Hero h1;
        private Hero h2;
     
        public KillThread(Hero h1, Hero h2){
            this.h1 = h1;
            this.h2 = h2;
        }
     
        public void run(){
            while(!h2.isDead()){
                h1.attackHero(h2);
            }
        }
    }
    ```

  - 

- [TestThread.java](https://how2j.cn/k/thread/thread-start/353.html#nowhere)

  - ```java
    package multiplethread;
     
    import charactor.Hero;
     
    public class TestThread {
     
        public static void main(String[] args) {
             
            Hero gareen = new Hero();
            gareen.name = "盖伦";
            gareen.hp = 616;
            gareen.damage = 50;
     
            Hero teemo = new Hero();
            teemo.name = "提莫";
            teemo.hp = 300;
            teemo.damage = 30;
             
            Hero bh = new Hero();
            bh.name = "赏金猎人";
            bh.hp = 500;
            bh.damage = 65;
             
            Hero leesin = new Hero();
            leesin.name = "盲僧";
            leesin.hp = 455;
            leesin.damage = 80;
             
            KillThread killThread1 = new KillThread(gareen,teemo);
            killThread1.start();
            KillThread killThread2 = new KillThread(bh,leesin);
            killThread2.start();
             
        }
         
    }
    ```

  - 



 步骤 **3** : 

### 创建多线程-实现Runnable接口

[**顶**](https://how2j.cn/k/thread/thread-start/353.html#)[**折**](https://how2j.cn/k/thread/thread-start/353.html#nowhere)

创建类Battle，实现Runnable接口
启动的时候，首先创建一个Battle对象，然后再根据该battle对象创建一个线程对象，并启动

 

Battle battle1 = new Battle(gareen,teemo);

new Thread(battle1).start();

 


battle1 对象实现了Runnable接口，所以有run方法，但是直接调用run方法，并不会启动一个新的线程。
必须，借助一个线程对象的start()方法，才会启动一个新的线程。
所以，在创建Thread对象的时候，把battle1作为构造方法的参数传递进去，这个线程启动的时候，就会去执行battle1.run()方法了。



- [Battle.java](https://how2j.cn/k/thread/thread-start/353.html#nowhere)

  - ```java
    package multiplethread;
     
    import charactor.Hero;
     
    public class Battle implements Runnable{
         
        private Hero h1;
        private Hero h2;
     
        public Battle(Hero h1, Hero h2){
            this.h1 = h1;
            this.h2 = h2;
        }
     
        public void run(){
            while(!h2.isDead()){
                h1.attackHero(h2);
            }
        }
    }
    ```

  - 

- [TestThread.java](https://how2j.cn/k/thread/thread-start/353.html#nowhere)

  - ```java
    package multiplethread;
     
    import charactor.Hero;
     
    public class TestThread {
     
        public static void main(String[] args) {
             
            Hero gareen = new Hero();
            gareen.name = "盖伦";
            gareen.hp = 616;
            gareen.damage = 50;
     
            Hero teemo = new Hero();
            teemo.name = "提莫";
            teemo.hp = 300;
            teemo.damage = 30;
             
            Hero bh = new Hero();
            bh.name = "赏金猎人";
            bh.hp = 500;
            bh.damage = 65;
             
            Hero leesin = new Hero();
            leesin.name = "盲僧";
            leesin.hp = 455;
            leesin.damage = 80;
             
            Battle battle1 = new Battle(gareen,teemo);
             
            new Thread(battle1).start();
     
            Battle battle2 = new Battle(bh,leesin);
            new Thread(battle2).start();
     
        }
         
    }
    ```

  -  步骤 **4** : 

### 创建多线程-匿名类

[**顶**](https://how2j.cn/k/thread/thread-start/353.html#)[**折**](https://how2j.cn/k/thread/thread-start/353.html#nowhere)

使用[匿名类](https://how2j.cn/k/interface-inheritance/interface-inheritance-inner-class/322.html#step687)，继承Thread,重写run方法，直接在run方法中写业务代码
匿名类的一个好处是可以很方便的访问外部的局部变量。
前提是外部的局部变量需要被声明为final。(JDK7以后就不需要了)

代码比较复制代码

```java
package multiplethread;
  
import charactor.Hero;
  
public class TestThread {
  
    public static void main(String[] args) {
          
        Hero gareen = new Hero();
        gareen.name = "盖伦";
        gareen.hp = 616;
        gareen.damage = 50;
  
        Hero teemo = new Hero();
        teemo.name = "提莫";
        teemo.hp = 300;
        teemo.damage = 30;
          
        Hero bh = new Hero();
        bh.name = "赏金猎人";
        bh.hp = 500;
        bh.damage = 65;
          
        Hero leesin = new Hero();
        leesin.name = "盲僧";
        leesin.hp = 455;
        leesin.damage = 80;
          
        //匿名类
        Thread t1= new Thread(){
            public void run(){
                //匿名类中用到外部的局部变量teemo，必须把teemo声明为final
                //但是在JDK7以后，就不是必须加final的了
                while(!teemo.isDead()){
                    gareen.attackHero(teemo);
                }              
            }
        };
         
        t1.start();
          
        Thread t2= new Thread(){
            public void run(){
                while(!leesin.isDead()){
                    bh.attackHero(leesin);
                }              
            }
        };
        t2.start();
         
    }
      
}
```



 步骤 **5** : 

### 创建多线程的三种方式

把上述3种方式再整理一下：

\1. 继承Thread类
\2. 实现Runnable接口
\3. 匿名类的方式

注： 启动线程是start()方法，run()并不能启动一个新的线程



 步骤 **6** : 

### 练习-同步查找文件内容 

把 [练习-查找文件内容](https://how2j.cn/k/io/io-filecopy-foldercopy/344.html#step2491) 改为多线程查找文件内容
原练习的思路是遍历所有文件，当遍历到文件是 .java的时候，查找这个文件的内容，查找完毕之后，再遍历下一个文件

现在通过多线程调整这个思路：
遍历所有文件，当遍历到文件是.java的时候，创建一个线程去查找这个文件的内容，不必等待这个线程结束，继续遍历下一个文件

---

## 常见线程的方法

 示例 **1** : 

### 当前线程暂停

[**顶**](https://how2j.cn/k/thread/thread-methods/354.html#)[**折**](https://how2j.cn/k/thread/thread-methods/354.html#nowhere)

Thread.sleep(1000); 表示当前线程暂停1000毫秒 ，其他线程不受影响
Thread.sleep(1000); 会抛出InterruptedException 中断异常，因为当前线程sleep的时候，有可能被停止，这时就会抛出 InterruptedException

代码比较复制代码

```java
package multiplethread;
 
public class TestThread {
 
    public static void main(String[] args) {
         
        Thread t1= new Thread(){
            public void run(){
                int seconds =0;
                while(true){
                    try {
                        Thread.sleep(1000);
                    } catch (InterruptedException e) {
                        // TODO Auto-generated catch block
                        e.printStackTrace();
                    }
                    System.out.printf("已经玩了LOL %d 秒%n", seconds++);
                }              
            }
        };
        t1.start();
         
    }
     
}
```



 示例 **2** : 

### 加入到当前线程中

[**顶**](https://how2j.cn/k/thread/thread-methods/354.html#)[**折**](https://how2j.cn/k/thread/thread-methods/354.html#nowhere)

首先解释一下**主线程**的概念
所有进程，至少会有一个线程即主线程，即main方法开始执行，就会有一个**看不见**的主线程存在。
在42行执行t.join，即表明**在主线程中加入该线程**。
主线程会等待该线程结束完毕， 才会往下运行。

代码比较复制代码

```java
package multiplethread;
  
import charactor.Hero;
  
public class TestThread {
  
    public static void main(String[] args) {
          
        final Hero gareen = new Hero();
        gareen.name = "盖伦";
        gareen.hp = 616;
        gareen.damage = 50;
  
        final Hero teemo = new Hero();
        teemo.name = "提莫";
        teemo.hp = 300;
        teemo.damage = 30;
          
        final Hero bh = new Hero();
        bh.name = "赏金猎人";
        bh.hp = 500;
        bh.damage = 65;
          
        final Hero leesin = new Hero();
        leesin.name = "盲僧";
        leesin.hp = 455;
        leesin.damage = 80;
          
        Thread t1= new Thread(){
            public void run(){
                while(!teemo.isDead()){
                    gareen.attackHero(teemo);
                }              
            }
        };
          
        t1.start();
 
        //代码执行到这里，一直是main线程在运行
        try {
            //t1线程加入到main线程中来，只有t1线程运行结束，才会继续往下走
            t1.join();
        } catch (InterruptedException e) {
            // TODO Auto-generated catch block
            e.printStackTrace();
        }
 
        Thread t2= new Thread(){
            public void run(){
                while(!leesin.isDead()){
                    bh.attackHero(leesin);
                }              
            }
        };
        //会观察到盖伦把提莫杀掉后，才运行t2线程
        t2.start();
          
    }
      
}
```





 示例 **3** : 

### 线程优先级

[**顶**](https://how2j.cn/k/thread/thread-methods/354.html#)[**折**](https://how2j.cn/k/thread/thread-methods/354.html#nowhere)

当线程处于竞争关系的时候，优先级高的线程会有更大的几率获得CPU资源
为了演示该效果，要把暂停时间去掉，多条线程各自会尽力去占有CPU资源
同时把英雄的血量增加100倍，攻击减低到1，才有足够的时间观察到优先级的演示
如图可见，线程1的优先级是MAX_PRIORITY，所以它争取到了更多的CPU资源执行代码

![线程优先级](https://stepimagewm.how2j.cn/783.png)

- [Hero.java](https://how2j.cn/k/thread/thread-methods/354.html#nowhere)

  - ```java
    package charactor;
      
    import java.io.Serializable;
       
    public class Hero{
        public String name;
        public float hp;
          
        public int damage;
          
        public void attackHero(Hero h) {
            //把暂停时间去掉，多条线程各自会尽力去占有CPU资源
            //线程的优先级效果才可以看得出来
    //        try {
    //           
    //            Thread.sleep(0);
    //        } catch (InterruptedException e) {
    //            // TODO Auto-generated catch block
    //            e.printStackTrace();
    //        }
            h.hp-=damage;
            System.out.format("%s 正在攻击 %s, %s的血变成了 %.0f%n",name,h.name,h.name,h.hp);
              
            if(h.isDead())
                System.out.println(h.name +"死了！");
        }
      
        public boolean isDead() {
            return 0>=hp?true:false;
        }
      
    }
    ```

  - 

- [TestThread.java](https://how2j.cn/k/thread/thread-methods/354.html#nowhere)

  - ```java
    package multiplethread;
      
    import charactor.Hero;
      
    public class TestThread {
      
        public static void main(String[] args) {
              
            final Hero gareen = new Hero();
            gareen.name = "盖伦";
            gareen.hp = 6160;
            gareen.damage = 1;
      
            final Hero teemo = new Hero();
            teemo.name = "提莫";
            teemo.hp = 3000;
            teemo.damage = 1;
              
            final Hero bh = new Hero();
            bh.name = "赏金猎人";
            bh.hp = 5000;
            bh.damage = 1;
              
            final Hero leesin = new Hero();
            leesin.name = "盲僧";
            leesin.hp = 4505;
            leesin.damage = 1;
              
            Thread t1= new Thread(){
                public void run(){
     
                    while(!teemo.isDead()){
                        gareen.attackHero(teemo);
                    }              
                }
            };
              
            Thread t2= new Thread(){
                public void run(){
                    while(!leesin.isDead()){
                        bh.attackHero(leesin);
                    }              
                }
            };
             
            t1.setPriority(Thread.MAX_PRIORITY);
            t2.setPriority(Thread.MIN_PRIORITY);
            t1.start();
            t2.start();
              
        }
          
    }
    ```

  -  示例 **4** : 

### 临时暂停

[**顶**](https://how2j.cn/k/thread/thread-methods/354.html#)[**折**](https://how2j.cn/k/thread/thread-methods/354.html#nowhere)

当前线程，临时暂停，使得其他线程可以有更多的机会占用CPU资源

代码比较复制代码

```java
package multiplethread;
  
import charactor.Hero;
  
public class TestThread {
  
    public static void main(String[] args) {
          
        final Hero gareen = new Hero();
        gareen.name = "盖伦";
        gareen.hp = 61600;
        gareen.damage = 1;
  
        final Hero teemo = new Hero();
        teemo.name = "提莫";
        teemo.hp = 30000;
        teemo.damage = 1;
          
        final Hero bh = new Hero();
        bh.name = "赏金猎人";
        bh.hp = 50000;
        bh.damage = 1;
          
        final Hero leesin = new Hero();
        leesin.name = "盲僧";
        leesin.hp = 45050;
        leesin.damage = 1;
          
        Thread t1= new Thread(){
            public void run(){
 
                while(!teemo.isDead()){
                    gareen.attackHero(teemo);
                }              
            }
        };
          
        Thread t2= new Thread(){
            public void run(){
                while(!leesin.isDead()){
                    //临时暂停，使得t1可以占用CPU资源
                    Thread.yield();
                     
                    bh.attackHero(leesin);
                }              
            }
        };
         
        t1.setPriority(5);
        t2.setPriority(5);
        t1.start();
        t2.start();
          
    }
      
}
```



 示例 **5** : 

### 守护线程

[**顶**](https://how2j.cn/k/thread/thread-methods/354.html#)[**折**](https://how2j.cn/k/thread/thread-methods/354.html#nowhere)

守护线程的概念是： 当一个进程里，所有的线程都是守护线程的时候，结束当前进程。

就好像一个公司有销售部，生产部这些和业务挂钩的部门。
除此之外，还有后勤，行政等这些支持部门。

如果一家公司销售部，生产部都解散了，那么只剩下后勤和行政，那么这家公司也可以解散了。

守护线程就相当于那些支持部门，如果一个进程只剩下守护线程，那么进程就会自动结束。

守护线程通常会被用来做日志，性能统计等工作。

代码比较复制代码

```java
package multiplethread;
  
public class TestThread {
  
    public static void main(String[] args) {
          
        Thread t1= new Thread(){
            public void run(){
                int seconds =0;
                 
                while(true){
                    try {
                        Thread.sleep(1000);
                    } catch (InterruptedException e) {
                        // TODO Auto-generated catch block
                        e.printStackTrace();
                    }
                    System.out.printf("已经玩了LOL %d 秒%n", seconds++);
                     
                }              
            }
        };
        t1.setDaemon(true);
        t1.start();
          
    }
      
}
```



 示例 **6** : 

### 练习-英雄充能 

  [**顶**](https://how2j.cn/k/thread/thread-methods/354.html#)[**折**](https://how2j.cn/k/thread/thread-methods/354.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/thread/thread-methods/354.html#nowhere)

英雄有可以放一个技能叫做: 波动拳-a du gen。
每隔一秒钟，可以发一次，但是只能连续发3次。

发完3次之后，需要充能5秒钟，充满，再继续发。

借助本章节学习到的知识点，实现这个效果

![练习-英雄充能](https://stepimagewm.how2j.cn/2589.png)

```java
public static void main(String[] args) {
        Thread bpq = new Thread(){
//            int second = 0;
          public void run(){
              try {
                  for (int i = 1; i <= 3; i++) {
                      System.out.printf("使用了 %d 次波动拳%n", i);
                      Thread.sleep(1000);
                      if (i >= 3) {
                          i = 0;
                          System.out.printf("使用了3次充能攻击,正在进行CD冷却...%n");
                          Thread.sleep(5000);
                          System.out.printf("技能冷却完毕,进行充能攻击 %n");
                          run();
                      }
                  }
              } catch (InterruptedException e) {
                  e.printStackTrace();
              }
          }
        };
        bpq.start();
    }
```



### 练习-破解密码 

  [**顶**](https://how2j.cn/k/thread/thread-methods/354.html#)[**折**](https://how2j.cn/k/thread/thread-methods/354.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/thread/thread-methods/354.html#nowhere)

\1. 生成一个长度是3的[随机字符串](https://how2j.cn/k/number-string/number-string-string/324.html#step2361)，把这个字符串当作 **密码**

\2. 创建一个破解线程，使用穷举法，匹配这个密码

\3. 创建一个日志线程，打印都用过哪些字符串去匹配，这个日志线程设计为守护线程

**提示**： 破解线程把穷举法生成的**可能密码**放在一个容器中，日志线程不断的从这个容器中拿出可能密码，并打印出来。 如果发现容器是空的，就休息1秒，如果发现不是空的，就不停的取出，并打印。

参考： [穷举法破解密码](https://how2j.cn/k/number-string/number-string-string/324.html#step2607)

---

## 多线程-同步

多线程的同步问题指的是多个线程同时修改一个数据的时候，可能导致的问题

多线程的问题，又叫**Concurrency** 问题

 步骤 **1** : 

### 演示同步问题

[**顶**](https://how2j.cn/k/thread/thread-synchronized/355.html#)[**折**](https://how2j.cn/k/thread/thread-synchronized/355.html#nowhere)

假设盖伦有10000滴血，并且在基地里，同时又被对方多个英雄攻击
就是**有多个线程在减少盖伦的hp**
同时又有**多个线程在恢复盖伦的hp**
假设线程的数量是一样的，并且每次改变的值都是1，那么所有线程结束后，盖伦应该还是10000滴血。
但是。。。

**注意**： 不是每一次运行都会看到错误的数据产生，多运行几次，或者增加运行的次数

![演示同步问题](https://stepimagewm.how2j.cn/786.png)

- [Hero.java](https://how2j.cn/k/thread/thread-synchronized/355.html#nowhere)

  - ```java
    package charactor;
      
    public class Hero{
        public String name;
        public float hp;
         
        public int damage;
         
        //回血
        public void recover(){
            hp=hp+1;
        }
         
        //掉血
        public void hurt(){
            hp=hp-1;
        }
         
        public void attackHero(Hero h) {
            h.hp-=damage;
            System.out.format("%s 正在攻击 %s, %s的血变成了 %.0f%n",name,h.name,h.name,h.hp);
            if(h.isDead())
                System.out.println(h.name +"死了！");
        }
      
        public boolean isDead() {
            return 0>=hp?true:false;
        }
      
    }
    ```

  - 

- [TestThread.java](https://how2j.cn/k/thread/thread-synchronized/355.html#nowhere)

  - ```java
    package multiplethread;
        
    import charactor.Hero;
        
    public class TestThread {
        
        public static void main(String[] args) {
                
            final Hero gareen = new Hero();
            gareen.name = "盖伦";
            gareen.hp = 10000;
               
            System.out.printf("盖伦的初始血量是 %.0f%n", gareen.hp);
               
            //多线程同步问题指的是多个线程同时修改一个数据的时候，导致的问题
               
            //假设盖伦有10000滴血，并且在基地里，同时又被对方多个英雄攻击
               
            //用JAVA代码来表示，就是有多个线程在减少盖伦的hp
            //同时又有多个线程在恢复盖伦的hp
               
            //n个线程增加盖伦的hp
               
            int n = 10000;
       
            Thread[] addThreads = new Thread[n];
            Thread[] reduceThreads = new Thread[n];
               
            for (int i = 0; i < n; i++) {
                Thread t = new Thread(){
                    public void run(){
                        gareen.recover();
                        try {
                            Thread.sleep(100);
                        } catch (InterruptedException e) {
                            // TODO Auto-generated catch block
                            e.printStackTrace();
                        }
                    }
                };
                t.start();
                addThreads[i] = t;
                   
            }
               
            //n个线程减少盖伦的hp
            for (int i = 0; i < n; i++) {
                Thread t = new Thread(){
                    public void run(){
                        gareen.hurt();
                        try {
                            Thread.sleep(100);
                        } catch (InterruptedException e) {
                            // TODO Auto-generated catch block
                            e.printStackTrace();
                        }
                    }
                };
                t.start();
                reduceThreads[i] = t;
            }
               
            //等待所有增加线程结束
            for (Thread t : addThreads) {
                try {
                    t.join();
                } catch (InterruptedException e) {
                    // TODO Auto-generated catch block
                    e.printStackTrace();
                }
            }
            //等待所有减少线程结束
            for (Thread t : reduceThreads) {
                try {
                    t.join();
                } catch (InterruptedException e) {
                    // TODO Auto-generated catch block
                    e.printStackTrace();
                }
            }
               
            //代码执行到这里，所有增加和减少线程都结束了
               
            //增加和减少线程的数量是一样的，每次都增加，减少1.
            //那么所有线程都结束后，盖伦的hp应该还是初始值
               
            //但是事实上观察到的是：
                       
            System.out.printf("%d个增加线程和%d个减少线程结束后%n盖伦的血量变成了 %.0f%n", n,n,gareen.hp);
               
        }
            
    }
    ```

  - 

 步骤 **2** : 

### 分析同步问题产生的原因

[**顶**](https://how2j.cn/k/thread/thread-synchronized/355.html#)[**折**](https://how2j.cn/k/thread/thread-synchronized/355.html#nowhere)

\1. 假设**增加线程**先进入，得到的hp是10000
\2. 进行增加运算
\3. 正在做增加运算的时候，**还没有来得及修改hp的值**，**减少线程**来了
\4. 减少线程得到的hp的值也是10000
\5. 减少线程进行减少运算
\6. 增加线程运算结束，得到值10001，并把这个值赋予hp
\7. 减少线程也运算结束，得到值9999，并把这个值赋予hp
hp，最后的值就是9999
虽然经历了两个线程各自增减了一次，本来期望还是原值10000，但是却得到了一个9999
这个时候的值9999是一个错误的值，在业务上又叫做**脏数据**

![分析同步问题产生的原因](https://stepimagewm.how2j.cn/787.png)



 步骤 **3** : 

### 解决思路

[**顶**](https://how2j.cn/k/thread/thread-synchronized/355.html#)[**折**](https://how2j.cn/k/thread/thread-synchronized/355.html#nowhere)

总体解决思路是： 在增加线程访问hp期间，其他线程不可以访问hp
\1. 增加线程获取到hp的值，并进行运算
\2. 在运算期间，减少线程试图来获取hp的值，但是**不被允许**
\3. 增加线程运算结束，并成功修改hp的值为10001
\4. 减少线程，在增加线程做完后，才能访问hp的值，即10001
\5. 减少线程运算，并得到新的值10000

![解决思路](https://stepimagewm.how2j.cn/788.png)



 步骤 **4** : 

### synchronized 同步对象概念

[**顶**](https://how2j.cn/k/thread/thread-synchronized/355.html#)[**折**](https://how2j.cn/k/thread/thread-synchronized/355.html#nowhere)

解决上述问题之前，先理解
**synchronized**关键字的意义
如下代码：

 

Object someObject =new Object();

synchronized (someObject){

  //此处的代码只有占有了someObject后才可以执行

}

 



**synchronized表示当前线程，独占 对象 someObject**
当前线程**独占** 了对象someObject，如果有**其他线程****试图占有对象**someObject，**就会等待**，直到当前线程释放对someObject的占用。
someObject 又叫同步对象，所有的对象，都可以作为同步对象
为了达到同步的效果，必须使用同一个同步对象

**释放同步对象**的方式： synchronized 块自然结束，或者有异常抛出

![synchronized 同步对象概念](https://stepimagewm.how2j.cn/789.png)

```java
package multiplethread;
  
import java.text.SimpleDateFormat;
import java.util.Date;
   
public class TestThread {
     
    public static String now(){
        return new SimpleDateFormat("HH:mm:ss").format(new Date());
    }
     
    public static void main(String[] args) {
        final Object someObject = new Object();
          
        Thread t1 = new Thread(){
            public void run(){
                try {
                    System.out.println( now()+" t1 线程已经运行");
                    System.out.println( now()+this.getName()+ " 试图占有对象：someObject");
                    synchronized (someObject) {
                          
                        System.out.println( now()+this.getName()+ " 占有对象：someObject");
                        Thread.sleep(5000);
                        System.out.println( now()+this.getName()+ " 释放对象：someObject");
                    }
                    System.out.println(now()+" t1 线程结束");
                } catch (InterruptedException e) {
                    // TODO Auto-generated catch block
                    e.printStackTrace();
                }
            }
        };
        t1.setName(" t1");
        t1.start();
        Thread t2 = new Thread(){
  
            public void run(){
                try {
                    System.out.println( now()+" t2 线程已经运行");
                    System.out.println( now()+this.getName()+ " 试图占有对象：someObject");
                    synchronized (someObject) {
                        System.out.println( now()+this.getName()+ " 占有对象：someObject");
                        Thread.sleep(5000);
                        System.out.println( now()+this.getName()+ " 释放对象：someObject");
                    }
                    System.out.println(now()+" t2 线程结束");
                } catch (InterruptedException e) {
                    // TODO Auto-generated catch block
                    e.printStackTrace();
                }
            }
        };
        t2.setName(" t2");
        t2.start();
    }
       
}
```

 

步骤 **5** : 

### 使用synchronized 解决同步问题

[**顶**](https://how2j.cn/k/thread/thread-synchronized/355.html#)[**折**](https://how2j.cn/k/thread/thread-synchronized/355.html#nowhere)

所有需要修改hp的地方，有要**建立在占有someObject的基础上**。
而对象 someObject在同一时间，只能被一个线程占有。 间接地，**导致同一时间，hp只能被一个线程修改。**

![使用synchronized 解决同步问题](https://stepimagewm.how2j.cn/790.png)

```java
package multiplethread;
   
import java.awt.GradientPaint;
 
import charactor.Hero;
   
public class TestThread {
   
    public static void main(String[] args) {
 
        final Object someObject = new Object();
         
        final Hero gareen = new Hero();
        gareen.name = "盖伦";
        gareen.hp = 10000;
          
        int n = 10000;
  
        Thread[] addThreads = new Thread[n];
        Thread[] reduceThreads = new Thread[n];
          
        for (int i = 0; i < n; i++) {
            Thread t = new Thread(){
                public void run(){
                     
                    //任何线程要修改hp的值，必须先占用someObject
                    synchronized (someObject) {
                        gareen.recover();
                    }
                     
                    try {
                        Thread.sleep(100);
                    } catch (InterruptedException e) {
                        // TODO Auto-generated catch block
                        e.printStackTrace();
                    }
                }
            };
            t.start();
            addThreads[i] = t;
              
        }
          
        for (int i = 0; i < n; i++) {
            Thread t = new Thread(){
                public void run(){
                    //任何线程要修改hp的值，必须先占用someObject
                    synchronized (someObject) {
                        gareen.hurt();
                    }
                     
                    try {
                        Thread.sleep(100);
                    } catch (InterruptedException e) {
                        // TODO Auto-generated catch block
                        e.printStackTrace();
                    }
                }
            };
            t.start();
            reduceThreads[i] = t;
        }
          
        for (Thread t : addThreads) {
            try {
                t.join();
            } catch (InterruptedException e) {
                // TODO Auto-generated catch block
                e.printStackTrace();
            }
        }
        for (Thread t : reduceThreads) {
            try {
                t.join();
            } catch (InterruptedException e) {
                // TODO Auto-generated catch block
                e.printStackTrace();
            }
        }
          
        System.out.printf("%d个增加线程和%d个减少线程结束后%n盖伦的血量是 %.0f%n", n,n,gareen.hp);
          
    }
       
}
```



 步骤 **6** : 

### 使用hero对象作为同步对象

[**顶**](https://how2j.cn/k/thread/thread-synchronized/355.html#)[**折**](https://how2j.cn/k/thread/thread-synchronized/355.html#nowhere)

既然任意对象都可以用来作为同步对象，而所有的线程访问的都是同一个hero对象，**索性就使用gareen来作为同步对象**
进一步的，对于Hero的hurt方法，加上：
synchronized (this) {
}
表示当前对象为同步对象，即也是gareen为同步对象

- [TestThread.java](https://how2j.cn/k/thread/thread-synchronized/355.html#nowhere)

  - ```java
    package multiplethread;
       
    import java.awt.GradientPaint;
     
    import charactor.Hero;
       
    public class TestThread {
       
        public static void main(String[] args) {
     
            final Hero gareen = new Hero();
            gareen.name = "盖伦";
            gareen.hp = 10000;
              
            int n = 10000;
      
            Thread[] addThreads = new Thread[n];
            Thread[] reduceThreads = new Thread[n];
              
            for (int i = 0; i < n; i++) {
                Thread t = new Thread(){
                    public void run(){
                         
                        //使用gareen作为synchronized
                        synchronized (gareen) {
                            gareen.recover();
                        }
                         
                        try {
                            Thread.sleep(100);
                        } catch (InterruptedException e) {
                            // TODO Auto-generated catch block
                            e.printStackTrace();
                        }
                    }
                };
                t.start();
                addThreads[i] = t;
                  
            }
              
            for (int i = 0; i < n; i++) {
                Thread t = new Thread(){
                    public void run(){
                        //使用gareen作为synchronized
                        //在方法hurt中有synchronized(this)
                        gareen.hurt();
                         
                        try {
                            Thread.sleep(100);
                        } catch (InterruptedException e) {
                            // TODO Auto-generated catch block
                            e.printStackTrace();
                        }
                    }
                };
                t.start();
                reduceThreads[i] = t;
            }
              
            for (Thread t : addThreads) {
                try {
                    t.join();
                } catch (InterruptedException e) {
                    // TODO Auto-generated catch block
                    e.printStackTrace();
                }
            }
            for (Thread t : reduceThreads) {
                try {
                    t.join();
                } catch (InterruptedException e) {
                    // TODO Auto-generated catch block
                    e.printStackTrace();
                }
            }
              
            System.out.printf("%d个增加线程和%d个减少线程结束后%n盖伦的血量是 %.0f%n", n,n,gareen.hp);
              
        }
           
    }
    ```

  - 

- [Hero.java](https://how2j.cn/k/thread/thread-synchronized/355.html#nowhere)

  - ```java
    package charactor;
      
    public class Hero{
        public String name;
        public float hp;
         
        public int damage;
         
        //回血
        public void recover(){
            hp=hp+1;
        }
         
        //掉血
        public void hurt(){
            //使用this作为同步对象
            synchronized (this) {
                hp=hp-1;   
            }
        }
         
        public void attackHero(Hero h) {
            h.hp-=damage;
            System.out.format("%s 正在攻击 %s, %s的血变成了 %.0f%n",name,h.name,h.name,h.hp);
            if(h.isDead())
                System.out.println(h.name +"死了！");
        }
      
        public boolean isDead() {
            return 0>=hp?true:false;
        }
      
    }
    ```

  - 

 步骤 **7** : 

### 在方法前，加上修饰符synchronized

[**顶**](https://how2j.cn/k/thread/thread-synchronized/355.html#)[**折**](https://how2j.cn/k/thread/thread-synchronized/355.html#nowhere)

在recover前，直接加上synchronized ，其所对应的同步对象，就是this
和hurt方法达到的效果是一样
外部线程访问gareen的方法，就不需要额外使用synchronized 了

- [Hero.java](https://how2j.cn/k/thread/thread-synchronized/355.html#nowhere)

  - ```java
    package charactor;
      
    public class Hero{
        public String name;
        public float hp;
         
        public int damage;
         
        //回血
        //直接在方法前加上修饰符synchronized
        //其所对应的同步对象，就是this
        //和hurt方法达到的效果一样
        public synchronized void recover(){
            hp=hp+1;
        }
         
        //掉血
        public void hurt(){
            //使用this作为同步对象
            synchronized (this) {
                hp=hp-1;   
            }
        }
         
        public void attackHero(Hero h) {
            h.hp-=damage;
            System.out.format("%s 正在攻击 %s, %s的血变成了 %.0f%n",name,h.name,h.name,h.hp);
            if(h.isDead())
                System.out.println(h.name +"死了！");
        }
      
        public boolean isDead() {
            return 0>=hp?true:false;
        }
      
    }
    ```

  - 

- [TestThread.java](https://how2j.cn/k/thread/thread-synchronized/355.html#nowhere)

  - ```java
    package multiplethread;
       
    import java.awt.GradientPaint;
     
    import charactor.Hero;
       
    public class TestThread {
       
        public static void main(String[] args) {
     
            final Hero gareen = new Hero();
            gareen.name = "盖伦";
            gareen.hp = 10000;
              
            int n = 10000;
      
            Thread[] addThreads = new Thread[n];
            Thread[] reduceThreads = new Thread[n];
              
            for (int i = 0; i < n; i++) {
                Thread t = new Thread(){
                    public void run(){
                         
                        //recover自带synchronized
                        gareen.recover();
                         
                        try {
                            Thread.sleep(100);
                        } catch (InterruptedException e) {
                            // TODO Auto-generated catch block
                            e.printStackTrace();
                        }
                    }
                };
                t.start();
                addThreads[i] = t;
                  
            }
              
            for (int i = 0; i < n; i++) {
                Thread t = new Thread(){
                    public void run(){
                        //hurt自带synchronized
                        gareen.hurt();
                         
                        try {
                            Thread.sleep(100);
                        } catch (InterruptedException e) {
                            // TODO Auto-generated catch block
                            e.printStackTrace();
                        }
                    }
                };
                t.start();
                reduceThreads[i] = t;
            }
              
            for (Thread t : addThreads) {
                try {
                    t.join();
                } catch (InterruptedException e) {
                    // TODO Auto-generated catch block
                    e.printStackTrace();
                }
            }
            for (Thread t : reduceThreads) {
                try {
                    t.join();
                } catch (InterruptedException e) {
                    // TODO Auto-generated catch block
                    e.printStackTrace();
                }
            }
              
            System.out.printf("%d个增加线程和%d个减少线程结束后%n盖伦的血量是 %.0f%n", n,n,gareen.hp);
              
        }
           
    }
    ```

  - 

 步骤 **8** : 

### 线程安全的类

[**顶**](https://how2j.cn/k/thread/thread-synchronized/355.html#)[**折**](https://how2j.cn/k/thread/thread-synchronized/355.html#nowhere)

如果一个类，其**方法都是有synchronized修饰的**，那么该类就叫做**线程安全的类**

同一时间，只有一个线程能够进入 **这种类的一个实例** 的去修改数据，进而保证了这个实例中的数据的安全(不会同时被多线程修改而变成脏数据)

比如StringBuffer和StringBuilder的区别
StringBuffer的方法都是有synchronized修饰的，StringBuffer就叫做线程安全的类
而StringBuilder就不是线程安全的类

![线程安全的类](https://stepimagewm.how2j.cn/793.png)



 步骤 **9** : 

### 练习-在类方法前面加修饰符synchronized 

[在对象方法前，加上修饰符synchronized](https://how2j.cn/k/thread/thread-synchronized/355.html#step792) ，同步对象是当前实例。
那么如果在类方法前，加上修饰符 synchronized，同步对象是什么呢？

提示：要完成本练习，需要[反射reflection](https://how2j.cn/k/reflection/reflection-reflection/107.html)的知识，如果未学习反射，可以暂时不做

 步骤 **11** : 

### 练习-线程安全的MyStack 

