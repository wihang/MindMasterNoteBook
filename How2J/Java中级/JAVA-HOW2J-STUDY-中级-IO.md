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

## I/O 字符流

## I/O 中文问题

## I/O 缓存流

## I/O 数据流

## I/O 对象流

## I/O System.in





