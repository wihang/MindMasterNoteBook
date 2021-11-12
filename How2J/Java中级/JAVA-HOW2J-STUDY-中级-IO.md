# JAVA-HOW2J-STUDY-中级-IO

[toc]

## I/O文件对象

 步骤 **1** : 

### 创建一个文件对象

[**顶**](https://how2j.cn/k/io/io-file/345.html#)[**折**](https://how2j.cn/k/io/io-file/345.html#nowhere)

使用绝对路径或者相对路径创建File对象

![创建一个文件对象](https://stepimagewm.how2j.cn/756.png)

代码比较复制代码

```java
package file;
  
import java.io.File;
  
public class TestFile {
  
    public static void main(String[] args) {
        // 绝对路径
        File f1 = new File("d:/LOLFolder");
        System.out.println("f1的绝对路径：" + f1.getAbsolutePath());
        // 相对路径,相对于工作目录，如果在eclipse中，就是项目目录
        File f2 = new File("LOL.exe");
        System.out.println("f2的绝对路径：" + f2.getAbsolutePath());
  
        // 把f1作为父目录创建文件对象
        File f3 = new File(f1, "LOL.exe");
  
        System.out.println("f3的绝对路径：" + f3.getAbsolutePath());
    }
}
```



 步骤 **2** : 

### 文件常用方法1

[**顶**](https://how2j.cn/k/io/io-file/345.html#)[**折**](https://how2j.cn/k/io/io-file/345.html#nowhere)

**注意1：** 需要在D:\LOLFolder确实存在一个LOL.exe,才可以看到对应的文件长度、修改时间等信息

**注意2： \**renameTo\**方法用于对物理文件名称进行修改，但是并不会修改File对象的name属性。**

![文件常用方法1](https://stepimagewm.how2j.cn/757.png)

代码比较复制代码

```java
package file;
  
import java.io.File;
import java.util.Date;
  
public class TestFile {
  
    public static void main(String[] args) {
  
        File f = new File("d:/LOLFolder/LOL.exe");
        System.out.println("当前文件是：" +f);
        //文件是否存在
        System.out.println("判断是否存在："+f.exists());
         
        //是否是文件夹
        System.out.println("判断是否是文件夹："+f.isDirectory());
          
        //是否是文件（非文件夹）
        System.out.println("判断是否是文件："+f.isFile());
          
        //文件长度
        System.out.println("获取文件的长度："+f.length());
          
        //文件最后修改时间
        long time = f.lastModified();
        Date d = new Date(time);
        System.out.println("获取文件的最后修改时间："+d);
        //设置文件修改时间为1970.1.1 08:00:00
        f.setLastModified(0);
          
        //文件重命名
        File f2 =new File("d:/LOLFolder/DOTA.exe");
        f.renameTo(f2);
        System.out.println("把LOL.exe改名成了DOTA.exe");
         
        System.out.println("注意： 需要在D:\\LOLFolder确实存在一个LOL.exe,\r\n才可以看到对应的文件长度、修改时间等信息");
    }
}
```



 步骤 **3** : 

### 文件常用方法2

[**顶**](https://how2j.cn/k/io/io-file/345.html#)[**折**](https://how2j.cn/k/io/io-file/345.html#nowhere)

代码比较复制代码

```java
package file;
  
import java.io.File;
import java.io.IOException;
  
public class TestFile {
  
    public static void main(String[] args) throws IOException {
  
        File f = new File("d:/LOLFolder/skin/garen.ski");
  
        // 以字符串数组的形式，返回当前文件夹下的所有文件（不包含子文件及子文件夹）
        f.list();
  
        // 以文件数组的形式，返回当前文件夹下的所有文件（不包含子文件及子文件夹）
        File[]fs= f.listFiles();
  
        // 以字符串形式返回获取所在文件夹
        f.getParent();
  
        // 以文件形式返回获取所在文件夹
        f.getParentFile();
        // 创建文件夹，如果父文件夹skin不存在，创建就无效
        f.mkdir();
  
        // 创建文件夹，如果父文件夹skin不存在，就会创建父文件夹
        f.mkdirs();
  
        // 创建一个空文件,如果父文件夹skin不存在，就会抛出异常
        f.createNewFile();
        // 所以创建一个空文件之前，通常都会创建父目录
        f.getParentFile().mkdirs();
  
        // 列出所有的盘符c: d: e: 等等
        f.listRoots();
  
        // 刪除文件
        f.delete();
  
        // JVM结束的时候，刪除文件，常用于临时文件的删除
        f.deleteOnExit();
  
    }
}
```



 步骤 **4** : 

### 练习-遍历文件夹 

  [**顶**](https://how2j.cn/k/io/io-file/345.html#)[**折**](https://how2j.cn/k/io/io-file/345.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/io/io-file/345.html#nowhere)

一般说来操作系统都会安装在C盘，所以会有一个 C:\WINDOWS目录。

遍历这个目录下所有的文件(不用遍历子目录)

找出这些文件里，最大的和最小(非0)的那个文件，打印出他们的文件名

**注:** 最小的文件不能是0长度

![练习-遍历文件夹](https://stepimagewm.how2j.cn/2393.png)



 步骤 **5** : 

### 答案-遍历文件夹 

[**顶**](https://how2j.cn/k/io/io-file/345.html#)[**折**](https://how2j.cn/k/io/io-file/345.html#nowhere)

查看答案 在查看答案前，尽量先自己完成，碰到问题再来查看答案，收获会更多

 步骤 **6** : 

### 练习-遍历子文件夹 

  [**顶**](https://how2j.cn/k/io/io-file/345.html#)[**折**](https://how2j.cn/k/io/io-file/345.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/io/io-file/345.html#nowhere)

同上的练习，要求遍历子文件夹

## I/O 什么是流

什么是流(Stream)，流就是一系列的数据

 步骤 **1** : 

### 什么是流

[**顶**](https://how2j.cn/k/io/io-stream/339.html#)[**折**](https://how2j.cn/k/io/io-stream/339.html#nowhere)

当不同的介质之间有数据交互的时候，JAVA就使用流来实现。
数据源可以	是文件，还可以是数据库，网络甚至是其他的程序


比如读取文件的数据到程序中，站在程序的角度来看，就叫做输入流
输入流： InputStream
输出流：OutputStream

![什么是流](https://stepimagewm.how2j.cn/759.png)



 步骤 **2** : 

### 文件输入流

[**顶**](https://how2j.cn/k/io/io-stream/339.html#)[**折**](https://how2j.cn/k/io/io-stream/339.html#nowhere)

如下代码，就建立了一个文件输入流，这个流可以用来把数据从硬盘的文件，读取到JVM(内存)。

目前代码只是建立了流，还没有开始读取，真正的读取在下个章节讲解。

代码比较复制代码

```java
package stream;
 
import java.io.File;
import java.io.FileInputStream;
import java.io.IOException;
 
public class TestStream {
 
    public static void main(String[] args) {
        try {
            File f = new File("d:/lol.txt");
            // 创建基于文件的输入流
            FileInputStream fis = new FileInputStream(f);
            // 通过这个输入流，就可以把数据从硬盘，读取到Java的虚拟机中来，也就是读取到内存中
 
        } catch (IOException e) {
            // TODO Auto-generated catch block
            e.printStackTrace();
        }
 
    }
}
```



 步骤 **3** : 

### 练习-流 

参考文件输入流的建立，建立一个文件输出流

---



## I/O 字节流

InputStream字节输入流
OutputStream字节输出流
用于以字节的形式读取和写入数据

 步骤 **1** : 

### ASCII码 概念

```tex
字符	十进制数字	十六进制数字
!	33	21
"	34	22
#	35	23
$	36	24
%	37	25
&	38	26
'	39	27
(	40	28
)	41	29
*	42	2A
+	43	2B
,	44	2C
-	45	2D
.	46	2E
/	47	2F
0	48	30
1	49	31
2	50	32
3	51	33
4	52	34
5	53	35
6	54	36
7	55	37
8	56	38
9	57	39
:	58	3A
;	59	3B
<	60	3C
=	61	3D
>	62	3E
@	64	40
A	65	41
B	66	42
C	67	43
D	68	44
E	69	45
F	70	46
G	71	47
H	72	48
I	73	49
J	74	4A
K	75	4B
L	76	4C
M	77	4D
N	78	4E
O	79	4F
P	80	50
Q	81	51
R	82	52
S	83	53
T	84	54
U	85	55
V	86	56
W	87	57
X	88	58
Y	89	59
Z	90	5A
[	91	5B
\	92	5C
]	93	5D
^	94	5E
_	95	5F
`	96	60
a	97	61
b	98	62
c	99	63
d	100	64
e	101	65
f	102	66
g	103	67
h	104	68
i	105	69
j	106	6A
k	107	6B
l	108	6C
m	109	6D
n	110	6E
o	111	6F
p	112	70
q	113	71
r	114	72
s	115	73
t	116	74
u	117	75
v	118	76
w	119	77
x	120	78
y	121	79
z	122	7A
{	123	7B
|	124	7C
}	125	7D
~	126	7E
```



所有的数据存放在计算机中都是以数字的形式存放的。 所以**字母就需要转换为数字才能够存放**。
比如A就对应的数字65，a对应的数字97. 不同的字母和符号对应不同的数字，就是一张码表。
ASCII是这样的一种码表。 只**包含简单的英文字母**，符号，数字等等。 **不包含中文，德文，俄语等复杂**的。

示例中列出了可见的ASCII码以及对应的十进制和十六进制数字，不可见的暂未列出



 步骤 **2** : 

### 以字节流的形式读取文件内容

[**顶**](https://how2j.cn/k/io/io-bytestream/340.html#)[**折**](https://how2j.cn/k/io/io-bytestream/340.html#nowhere)

InputStream是字节输入流，同时也是抽象类，只提供方法声明，不提供方法的具体实现。
FileInputStream 是InputStream子类，以FileInputStream 为例进行文件读取

代码比较复制代码

```java
package stream;
  
import java.io.File;
import java.io.FileInputStream;
import java.io.IOException;
  
public class TestStream {
  
    public static void main(String[] args) {
        try {
            //准备文件lol.txt其中的内容是AB，对应的ASCII分别是65 66
            File f =new File("d:/lol.txt");
            //创建基于文件的输入流
            FileInputStream fis =new FileInputStream(f);
            //创建字节数组，其长度就是文件的长度
            byte[] all =new byte[(int) f.length()];
            //以字节流的形式读取文件所有内容
            fis.read(all);
            for (byte b : all) {
                //打印出来是65 66
                System.out.println(b);
            }
             
            //每次使用完流，都应该进行关闭
            fis.close();
              
        } catch (IOException e) {
            // TODO Auto-generated catch block
            e.printStackTrace();
        }
          
    }
}
```





 步骤 **3** : 

### 以字节流的形式向文件写入数据

[**顶**](https://how2j.cn/k/io/io-bytestream/340.html#)[**折**](https://how2j.cn/k/io/io-bytestream/340.html#nowhere)

OutputStream是字节输出流，同时也是抽象类，只提供方法声明，不提供方法的具体实现。
FileOutputStream 是OutputStream子类，以FileOutputStream 为例向文件写出数据

注: 如果文件d:/lol2.txt不存在，写出操作会自动创建该文件。
但是如果是文件 d:/xyz/lol2.txt，而目录xyz又不存在，会抛出异常

![以字节流的形式向文件写入数据](https://stepimagewm.how2j.cn/2414.png)

代码比较复制代码

```java
package stream;
 
import java.io.File;
import java.io.FileOutputStream;
import java.io.IOException;
 
public class TestStream {
 
    public static void main(String[] args) {
        try {
            // 准备文件lol2.txt其中的内容是空的
            File f = new File("d:/lol2.txt");
            // 准备长度是2的字节数组，用88,89初始化，其对应的字符分别是X,Y
            byte data[] = { 88, 89 };
 
            // 创建基于文件的输出流
            FileOutputStream fos = new FileOutputStream(f);
            // 把数据写入到输出流
            fos.write(data);
            // 关闭输出流
            fos.close();
             
        } catch (IOException e) {
            // TODO Auto-generated catch block
            e.printStackTrace();
        }
 
    }
}
```

 步骤 **4** : 

### 练习-写入数据到文件 

  [**顶**](https://how2j.cn/k/io/io-bytestream/340.html#)[**折**](https://how2j.cn/k/io/io-bytestream/340.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/io/io-bytestream/340.html#nowhere)

[以字节流的形式向文件写入数据](https://how2j.cn/k/io/io-bytestream/340.html#step2414) 中的例子，当lol2.txt不存在的时候，是会自动创建lol2.txt文件的。
但是，如果是写入数据到d:/xyz/lol2.txt，而目录xyz又不存在的话，就会抛出异常。
那么怎么自动创建xyz目录？
如果是多层目录 d:/xyz/abc/def/lol2.txt 呢？

![练习-写入数据到文件](https://stepimagewm.how2j.cn/2415.png)



 步骤 **5** : 

答案-写入数据到文件 

[**顶**](https://how2j.cn/k/io/io-bytestream/340.html#)[**折**](https://how2j.cn/k/io/io-bytestream/340.html#nowhere)

查看答案 在查看答案前，尽量先自己完成，碰到问题再来查看答案，收获会更多

 步骤 **6** : 

### 练习-拆分文件 

  [**顶**](https://how2j.cn/k/io/io-bytestream/340.html#)[**折**](https://how2j.cn/k/io/io-bytestream/340.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/io/io-bytestream/340.html#nowhere)

找到一个大于100k的文件，按照100k为单位，拆分成多个子文件，并且以编号作为文件名结束。
比如文件 eclipse.exe，大小是309k。
拆分之后，成为
eclipse.exe-0
eclipse.exe-1
eclipse.exe-2
eclipse.exe-3

![练习-拆分文件](https://stepimagewm.how2j.cn/2417.png)



 步骤 **8** : 

### 练习-合并文件 

把上述拆分出来的文件，合并成一个原文件。

以是否能正常运行，验证合并是否正确

---

## I/O 关闭流的方式

所有的流，无论是输入流还是输出流，使用完毕之后，都应该关闭。 如果不关闭，会产生对资源占用的浪费。 当量比较大的时候，会影响到业务的正常开展。

### 在try中关闭

[**顶**](https://how2j.cn/k/io/io-closestream/682.html#)[**折**](https://how2j.cn/k/io/io-closestream/682.html#nowhere)

在try的作用域里关闭文件输入流，在前面的示例中都是使用这种方式，这样做有一个弊端；
如果文件不存在，或者读取的时候出现问题而抛出异常，那么就不会执行这一行关闭流的代码，存在巨大的资源占用隐患。 **不推荐**使用

代码比较复制代码

```JAVA
package stream;
 
import java.io.File;
import java.io.FileInputStream;
import java.io.IOException;
 
public class TestStream {
 
    public static void main(String[] args) {
        try {
            File f = new File("d:/lol.txt");
            FileInputStream fis = new FileInputStream(f);
            byte[] all = new byte[(int) f.length()];
            fis.read(all);
            for (byte b : all) {
                System.out.println(b);
            }
            // 在try 里关闭流
            fis.close();
        } catch (IOException e) {
            e.printStackTrace();
        }
 
    }
}
```





 步骤 **2** : 

### 在finally中关闭

[**顶**](https://how2j.cn/k/io/io-closestream/682.html#)[**折**](https://how2j.cn/k/io/io-closestream/682.html#nowhere)

这是标准的关闭流的方式
\1. 首先把流的引用声明在try的外面，如果声明在try里面，其作用域无法抵达finally.
\2. 在finally关闭之前，要先判断该引用是否为空
\3. 关闭的时候，需要再一次进行try catch处理

这是标准的严谨的关闭流的方式，但是看上去很繁琐，所以写不重要的或者测试代码的时候，都会采用上面的**有隐患**try的方式，因为不麻烦~

代码比较复制代码

```JAVA
package stream;
 
import java.io.File;
import java.io.FileInputStream;
import java.io.IOException;
 
public class TestStream {
 
    public static void main(String[] args) {
        File f = new File("d:/lol.txt");
        FileInputStream fis = null;
        try {
            fis = new FileInputStream(f);
            byte[] all = new byte[(int) f.length()];
            fis.read(all);
            for (byte b : all) {
                System.out.println(b);
            }
 
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            // 在finally 里关闭流
            if (null != fis)
                try {
 
                    fis.close();
                } catch (IOException e) {
                    // TODO Auto-generated catch block
                    e.printStackTrace();
                }
        }
 
    }
}
```





 步骤 **3** : 

### 使用try()的方式

[**顶**](https://how2j.cn/k/io/io-closestream/682.html#)[**折**](https://how2j.cn/k/io/io-closestream/682.html#nowhere)

把流定义在try()里,try,catch或者finally结束的时候，会自动关闭
这种编写代码的方式叫做 **try-with-resources**， 这是从JDK7开始支持的技术

所有的流，都实现了一个接口叫做 **AutoCloseable**，任何类实现了这个接口，都可以在try()中进行实例化。 并且在try, catch, finally结束的时候自动关闭，回收相关资源。

```JAVA
package stream;
  
import java.io.File;
import java.io.FileInputStream;
import java.io.IOException;
  
public class TestStream {
  
    public static void main(String[] args) {
        File f = new File("d:/lol.txt");
  
        //把流定义在try()里,try,catch或者finally结束的时候，会自动关闭
        try (FileInputStream fis = new FileInputStream(f)) {
            byte[] all = new byte[(int) f.length()];
            fis.read(all);
            for (byte b : all) {
                System.out.println(b);
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
  
    }
}
```



### I/O 字符流

Reader字符输入流
Writer字符输出流
专门用于字符的形式读取和写入数据

### I/O 中文问题

 步骤 **1** : 

### 使用字符流读取文件

[**顶**](https://how2j.cn/k/io/io-characterstream/341.html#)[**折**](https://how2j.cn/k/io/io-characterstream/341.html#nowhere)

FileReader 是Reader子类，以FileReader 为例进行文件读取

代码比较复制代码

```java
package stream;
 
import java.io.File;
import java.io.FileReader;
import java.io.IOException;
 
public class TestStream {
 
    public static void main(String[] args) {
        // 准备文件lol.txt其中的内容是AB
        File f = new File("d:/lol.txt");
        // 创建基于文件的Reader
        try (FileReader fr = new FileReader(f)) {
            // 创建字符数组，其长度就是文件的长度
            char[] all = new char[(int) f.length()];
            // 以字符流的形式读取文件所有内容
            fr.read(all);
            for (char b : all) {
                // 打印出来是A B
                System.out.println(b);
            }
        } catch (IOException e) {
            // TODO Auto-generated catch block
            e.printStackTrace();
        }
 
    }
}
```



 步骤 **2** : 

### 使用字符流把字符串写入到文件

[**顶**](https://how2j.cn/k/io/io-characterstream/341.html#)[**折**](https://how2j.cn/k/io/io-characterstream/341.html#nowhere)

FileWriter 是Writer的子类，以FileWriter 为例把字符串写入到文件

![使用字符流把字符串写入到文件](https://stepimagewm.how2j.cn/2432.png)

```java
package stream;
  
import java.io.File;
import java.io.FileWriter;
import java.io.IOException;
  
public class TestStream {
  
    public static void main(String[] args) {
        // 准备文件lol2.txt
        File f = new File("d:/lol2.txt");
        // 创建基于文件的Writer
        try (FileWriter fr = new FileWriter(f)) {
            // 以字符流的形式把数据写入到文件中
            String data="abcdefg1234567890";
            char[] cs = data.toCharArray();
            fr.write(cs);
  
        } catch (IOException e) {
            // TODO Auto-generated catch block
            e.printStackTrace();
        }
  
    }
}
```





 步骤 **3** : 

### 练习-文件加密 

  [**顶**](https://how2j.cn/k/io/io-characterstream/341.html#)[**折**](https://how2j.cn/k/io/io-characterstream/341.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/io/io-characterstream/341.html#nowhere)

准备一个**文本文件**(非二进制)，其中包含[ASCII码](https://how2j.cn/k/io/io-bytestream/340.html#step766)的字符和中文字符。
设计一个方法

 

public static void encodeFile(File encodingFile, File encodedFile);

 


在这个方法中把encodingFile的内容进行加密，然后保存到encodedFile文件中。
加密算法：
数字：
如果不是9的数字，在原来的基础上加1，比如5变成6, 3变成4
如果是9的数字，变成0
字母字符：
如果是非z字符，向右移动一个，比如d变成e, G变成H
如果是z，z->a, Z-A。
字符需要保留大小写
非字母字符
比如',&^ 保留不变，中文也保留不变
**建议：** 使用以前学习的练习题中的某个Java文件，比如循环练习，就有很多的字符和数字

![练习-文件加密](https://stepimagewm.how2j.cn/2434.png)



### 练习-文件解密 

  [**顶**](https://how2j.cn/k/io/io-characterstream/341.html#)[**折**](https://how2j.cn/k/io/io-characterstream/341.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/io/io-characterstream/341.html#nowhere)

解密在[文件加密](https://how2j.cn/k/io/io-characterstream/341.html#step2434)中生成的文件。
设计一个方法

 

public static void decodeFile(File decodingFile, File decodedFile);

 


在这个方法中把decodingFile的内容进行解密，然后保存到decodedFile文件中。
解密算法：
数字：
如果不是0的数字，在原来的基础上减1，比如6变成5, 4变成3
如果是0的数字，变成9
字母字符：
如果是非a字符，向左移动一个，比如e变成d, H变成G
如果是a，a->z, A-Z。
字符需要保留大小写
非字母字符：
比如',&^ 保留不变，中文也保留不变

## I/O 缓存流

 示例 **1** : 

### 使用缓存流读取数据

[**顶**](https://how2j.cn/k/io/io-bufferedstream/342.html#)[**折**](https://how2j.cn/k/io/io-bufferedstream/342.html#nowhere)

缓存字符输入流 BufferedReader 可以一次读取一行数据

代码比较复制代码

```java
package stream;
  
import java.io.BufferedReader;
import java.io.File;
import java.io.FileReader;
import java.io.IOException;
  
public class TestStream {
  
    public static void main(String[] args) {
        // 准备文件lol.txt其中的内容是
        // garen kill teemo
        // teemo revive after 1 minutes
        // teemo try to garen, but killed again
        File f = new File("d:/lol.txt");
        // 创建文件字符流
        // 缓存流必须建立在一个存在的流的基础上
        try (
                FileReader fr = new FileReader(f);
                BufferedReader br = new BufferedReader(fr);
            )
        {
            while (true) {
                // 一次读一行
                String line = br.readLine();
                if (null == line)
                    break;
                System.out.println(line);
            }
        } catch (IOException e) {
            // TODO Auto-generated catch block
            e.printStackTrace();
        }
  
    }
}
```



 示例 **2** : 

### 使用缓存流写出数据

[**顶**](https://how2j.cn/k/io/io-bufferedstream/342.html#)[**折**](https://how2j.cn/k/io/io-bufferedstream/342.html#nowhere)

PrintWriter 缓存字符输出流， 可以一次写出一行数据

代码比较复制代码

```java
package stream;
   
import java.io.File;
import java.io.FileWriter;
import java.io.IOException;
import java.io.PrintWriter;
   
public class TestStream {
   
    public static void main(String[] args) {
        // 向文件lol2.txt中写入三行语句
        File f = new File("d:/lol2.txt");
          
        try (
                // 创建文件字符流
                FileWriter fw = new FileWriter(f);
                // 缓存流必须建立在一个存在的流的基础上              
                PrintWriter pw = new PrintWriter(fw);              
        ) {
            pw.println("garen kill teemo");
            pw.println("teemo revive after 1 minutes");
            pw.println("teemo try to garen, but killed again");
        } catch (IOException e) {
            // TODO Auto-generated catch block
            e.printStackTrace();
        }
   
    }
}
```



 示例 **3** : 

### flush

[**顶**](https://how2j.cn/k/io/io-bufferedstream/342.html#)[**折**](https://how2j.cn/k/io/io-bufferedstream/342.html#nowhere)

有的时候，需要**立即把数据写入到硬盘**，而不是等缓存满了才写出去。 这时候就需要用到flush

代码比较复制代码

```java
package stream;
    
import java.io.File;
import java.io.FileWriter;
import java.io.IOException;
import java.io.PrintWriter;
public class TestStream {
    public static void main(String[] args) {
        //向文件lol2.txt中写入三行语句
        File f =new File("d:/lol2.txt");
        //创建文件字符流
        //缓存流必须建立在一个存在的流的基础上
        try(FileWriter fr = new FileWriter(f);PrintWriter pw = new PrintWriter(fr);) {
            pw.println("garen kill teemo");
            //强制把缓存中的数据写入硬盘，无论缓存是否已满
                pw.flush();           
            pw.println("teemo revive after 1 minutes");
                pw.flush();
            pw.println("teemo try to garen, but killed again");
                pw.flush();
        } catch (IOException e) {
            // TODO Auto-generated catch block
            e.printStackTrace();
        }
    }
}
```



 示例 **4** : 

### 练习-移除注释 

  [**顶**](https://how2j.cn/k/io/io-bufferedstream/342.html#)[**折**](https://how2j.cn/k/io/io-bufferedstream/342.html#nowhere) 姿势不对,事倍功半! [点击查看做练习的正确姿势](https://how2j.cn/k/io/io-bufferedstream/342.html#nowhere)

设计一个方法，用于移除Java文件中的注释

 

public void removeComments(File javaFile)

 


比如，移出以//开头的注释行

 

File f = new File("d:/LOLFolder/LOL.exe");

System.out.println("当前文件是：" +f);

//文件是否存在

System.out.println("判断是否存在："+f.exists());

//是否是文件夹

System.out.println("判断是否是文件夹："+f.isDirectory());

 

## I/O 数据流

DataInputStream 数据输入流
DataOutputStream 数据输出流



 步骤 **1** : 

### 直接进行字符串的读写

[**顶**](https://how2j.cn/k/io/io-datastream/350.html#)[**折**](https://how2j.cn/k/io/io-datastream/350.html#nowhere)

使用数据流的writeUTF()和readUTF() 可以进行数据的**格式化顺序读写**
如本例，通过DataOutputStream 向文件顺序写出 布尔值，整数和字符串。 然后再通过DataInputStream 顺序读入这些数据。

**注：** 要用DataInputStream 读取一个文件，这个文件必须是由DataOutputStream 写出的，否则会出现EOFException，因为DataOutputStream 在写出的时候会做一些特殊标记，只有DataInputStream 才能成功的读取。

![直接进行字符串的读写](https://stepimagewm.how2j.cn/771.png)

代码比较复制代码

```java
package stream;
      
import java.io.DataInputStream;
import java.io.DataOutputStream;
import java.io.File;
import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.IOException;
      
public class TestStream {
      
    public static void main(String[] args) {
        write();
        read();
    }
 
    private static void read() {
        File f =new File("d:/lol.txt");
        try (
                FileInputStream fis  = new FileInputStream(f);
                DataInputStream dis =new DataInputStream(fis);
        ){
            boolean b= dis.readBoolean();
            int i = dis.readInt();
            String str = dis.readUTF();
             
            System.out.println("读取到布尔值:"+b);
            System.out.println("读取到整数:"+i);
            System.out.println("读取到字符串:"+str);
 
        } catch (IOException e) {
            e.printStackTrace();
        }
         
    }
 
    private static void write() {
        File f =new File("d:/lol.txt");
        try (
                FileOutputStream fos  = new FileOutputStream(f);
                DataOutputStream dos =new DataOutputStream(fos);
        ){
            dos.writeBoolean(true);
            dos.writeInt(300);
            dos.writeUTF("123 this is gareen");
        } catch (IOException e) {
            e.printStackTrace();
        }
         
    }
}
```



 步骤 **2** : 

练习-向文件中写入两个数字，然后把这两个数字分别读取出来 

要求
第一种方式： 使用[缓存流](https://how2j.cn/k/io/io-bufferedstream/342.html)把两个数字以字符串的形式写到文件里，再用[缓存流](https://how2j.cn/k/io/io-bufferedstream/342.html)以字符串的形式读取出来，然后转换为两个数字。
**注：** 两个数字之间要有分隔符用于区分这两个数字。 比如数字是31和15，如果不使用分隔符，那么就是3115，读取出来就无法识别到底是哪两个数字。 使用分隔符31@15能解决这个问题。

第二种方式： 使用数据流DataOutputStream向文件连续写入两个数字，然后用DataInpuStream连续读取两个数字

---



## I/O 对象流

对象流指的是可以直接**把一个对象以流的形式**传输给其他的介质，比如硬盘

一个对象以流的形式进行传输，叫做序列化。 该对象所对应的类，必须是实现Serializable接口



 步骤 **1** : 

### 序列化一个对象

[**顶**](https://how2j.cn/k/io/io-objectstream/351.html#)[**折**](https://how2j.cn/k/io/io-objectstream/351.html#nowhere)

创建一个Hero对象，设置其名称为garen。
把该对象序列化到一个文件garen.lol。
然后再通过序列化把该文件转换为一个Hero对象

**注：**把一个对象序列化有一个前提是：这个对象的类，必须实现了Serializable接口

- [TestStream.java](https://how2j.cn/k/io/io-objectstream/351.html#nowhere)

- ```java
  package stream;
      
  import java.io.File;
  import java.io.FileInputStream;
  import java.io.FileOutputStream;
  import java.io.IOException;
  import java.io.ObjectInputStream;
  import java.io.ObjectOutputStream;
    
  import charactor.Hero;
      
  public class TestStream {
      
      public static void main(String[] args) {
          //创建一个Hero garen
          //要把Hero对象直接保存在文件上，务必让Hero类实现Serializable接口
          Hero h = new Hero();
          h.name = "garen";
          h.hp = 616;
            
          //准备一个文件用于保存该对象
          File f =new File("d:/garen.lol");
   
          try(
              //创建对象输出流
              FileOutputStream fos = new FileOutputStream(f);
              ObjectOutputStream oos =new ObjectOutputStream(fos);
              //创建对象输入流              
              FileInputStream fis = new FileInputStream(f);
              ObjectInputStream ois =new ObjectInputStream(fis);
          ) {
              oos.writeObject(h);
              Hero h2 = (Hero) ois.readObject();
              System.out.println(h2.name);
              System.out.println(h2.hp);
                 
          } catch (IOException e) {
              // TODO Auto-generated catch block
              e.printStackTrace();
          } catch (ClassNotFoundException e) {
              // TODO Auto-generated catch block
              e.printStackTrace();
          }
              
      }
  }
  ```

- [Hero.java](https://how2j.cn/k/io/io-objectstream/351.html#nowhere)

- ```java
  	 
  import java.io.Serializable;
   
  public class Hero implements Serializable {
      //表示这个类当前的版本，如果有了变化，比如新设计了属性，就应该修改这个版本号
      private static final long serialVersionUID = 1L;
      public String name;
      public float hp;
   
  }
  ```





 步骤 **2** : 

### 练习-序列化数组   



准备一个长度是10，类型是Hero的数组，使用10个Hero对象初始化该数组

然后把该数组序列化到一个文件heros.lol

接着使用ObjectInputStream 读取该文件，并转换为Hero数组，验证该数组中的内容，是否和序列化之前一样

![练习-序列化数组](https://stepimagewm.how2j.cn/2442.png)

### I/O System.in

System.out 是常用的在控制台输出数据的
System.in 可以从控制台输入数据

 步骤 **1** : 

## System.in	

```java
package stream;
 
import java.io.IOException;
import java.io.InputStream;
 
public class TestStream {
 
    public static void main(String[] args) {
        // 控制台输入
        try (InputStream is = System.in;) {
            while (true) {
                // 敲入a,然后敲回车可以看到
                // 97 13 10
                // 97是a的ASCII码
                // 13 10分别对应回车换行
                int i = is.read();
                System.out.println(i);
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```
}

 步骤 **2** : 

### Scanner读取字符串

[**顶**](https://how2j.cn/k/io/io-system-in/352.html#)[**折**](https://how2j.cn/k/io/io-system-in/352.html#nowhere)

使用System.in.read虽然可以读取数据，但是很不方便
使用Scanner就可以逐行读取了

代码比较复制代码

```java
package stream;
    
import java.util.Scanner;
    
public class TestStream {
    
    public static void main(String[] args) {
         
            Scanner s = new Scanner(System.in);
             
            while(true){
                String line = s.nextLine();
                System.out.println(line);
            }
         
    }
}
```



 步骤 **3** : 

### Scanner从控制台读取整数

[**顶**](https://how2j.cn/k/io/io-system-in/352.html#)[**折**](https://how2j.cn/k/io/io-system-in/352.html#nowhere)

使用Scanner从控制台读取整数

![Scanner从控制台读取整数](https://stepimagewm.how2j.cn/2142.png)

代码比较复制代码

```java
package stream;
 
import java.util.Scanner;
 
public class TestStream {
    public static void main(String[] args) {
        Scanner s = new Scanner(System.in);
        int a = s.nextInt();
        System.out.println("第一个整数："+a);
        int b = s.nextInt();
        System.out.println("第二个整数："+b);
    }
}
```



 步骤 **4** : 

### 练习-自动创建类 

自动创建有一个属性的类文件。
通过控制台，获取类名，属性名称，属性类型，根据一个模板文件，自动创建这个类文件，并且为属性提供setter和getter

![练习-自动创建类](https://stepimagewm.how2j.cn/2444.png)

```java
public class @class@ {
    public @type@ @property@;
    public @class@() {
    }
    public void set@Uproperty@(@type@  @property@){
        this.@property@ = @property@;
    }
      
    public @type@  get@Uproperty@(){
        return this.@property@;
    }
}
```





