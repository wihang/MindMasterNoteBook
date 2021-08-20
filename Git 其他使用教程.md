# Git 其他使用教程

## [Github私有仓库使用设置](https://www.cnblogs.com/haojile/p/11616566.html)

1、创建一个私有仓库

![img](https://img2018.cnblogs.com/blog/381891/201910/381891-20191001234526816-719800287.png)

 2、在个人中心的有一个“Developer setting”选项： 

![img](https://img2018.cnblogs.com/blog/381891/201910/381891-20191002100511061-244579598.png)

 

 3、在“Developer settings”中有一个“Personal access tokens”选项，点击“Generate new token”

![img](https://img2018.cnblogs.com/blog/381891/201910/381891-20191002000000756-604727042.png)

 4、 输入名称，并选择需要的权限：

![img](https://img2018.cnblogs.com/blog/381891/201910/381891-20191002000255288-741459836.png)

 5、点击“Generate token”即可创建成功，创建成功之后会出现类似下面的token字符串，一定要复制粘贴出来；

这个token只显示一次，如果不复制出来的话，就不会再显示了；

如果实在是忘记了，也没有复制出来，那可以删除这个token，然后重新生成一个。

![img](https://img2018.cnblogs.com/blog/381891/201910/381891-20191002000626289-809400945.png)

 6、使用方法：

```tex
Clone命令：
git clone https://<token>@github.com/<用户名>/<仓库名>
```

　　所以本例子的命令是：<!---->

```
git clone https://11b82b0a18fde70bb92288cf0b0b79b76f302d1e@github.com/<用户名>/siyoucangku
```

7、使用如下：

![img](https://img2018.cnblogs.com/blog/381891/201910/381891-20191002001612375-697445239.png)

