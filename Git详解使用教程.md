# [Git详解使用教程](https://www.cnblogs.com/duanming/p/11830252.html)

[toc]

### 一. 什么是Git

`Git`(读音为/gɪt/)。是一个`开源的` `分布式版本控制系统`，可以有效、高速地处理从很小到非常大的项目版本管理。
Git 是 Linus Torvalds 为了帮助管理 Linux 内核开发而开发的一个开放源码的版本控制软件。

---

### 二.安装Git

1.由于官网下载速度很慢，我这里直接贴出来[百度网盘下载地址](https://pan.baidu.com/s/1IJwH-4QqeAPJTYrylU-0Bw)，下载后得到需要的Git安装文件。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029115050422.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
2.`双击安装程序`，现在我们对Git还没有深入了解，所以直接一路点击下一步，全部按照默认配置安装。
3.安装完成后`开始菜单`中找到`Git Bash`点开。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029120003733.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)

---

### 三、使用Git — 设置使用者的信息

4.出现`Git Bash窗口`即代表我们安装成功了。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029120210358.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
5.因为Git是分布式版本控制系统，所以需要绑定一个用户名和邮箱；以后我们每次提交代码都是用自己的用户提交的，这样就达到了在公司中，分辨多个开发人员提交的代码。
输入运行两条命令设置用户名和邮箱，设置一次就可以了：① `git config --global user.name "自定义的用户名"`, ② `git config --global user.email "12345678@qq.com"` ， 如下：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029124622642.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
6.没报错就说明成功了，如果想要查询当前的用户名和邮箱，可以使用`git config user.name`, `git config user.email`两条命令。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029125037565.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
7.如果想要取消掉当前的用户重新设置新的用户名和邮箱可以使用`git config --global --unset user.name "想要取消的用户名"`，`git config --global --unset user.email "想要取消的邮箱"`这两条命令进行取消，然后再通过`步骤5`重新设置用户名和邮箱。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029125617242.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)

---

### 四、使用Git — 创建本地库

`补充知识：`版本库又名仓库，英文名`repository`,你可以简单的理解为一个目录，这个目录里面的所有文件都可以被`Git`管理起来，每个文件的修改，删除，Git都能跟踪，以便任何时刻都可以追踪历史，或者在将来某个时刻还可以将文件”还原”；这也是Git的强大之处。
8.创建一个目录， 进入该目录
在Linux下能用的文件操作命令，这里基本也都可以使用；`cd d:`移动到`d:`盘下，创建一个目录，我这里叫做`firstRepo`，通过`mkdir firstRepo`命令。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029130738337.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
9.通过`git init`命令将这个文件夹变成一个本地的仓库，以后就可以通过Git管理这个本地仓库了。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029131104646.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
这时候我们发现当前目录下会多了一个`.git`的目录，这个目录是Git来跟踪管理版本的，除非你明确知道自己在干什么，否则最好不要动这个目录里面的文件。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029132028391.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
`补充知识：`所有的版本控制系统，都能跟踪文本文件的改动，比如txt文件，网页，所有程序的代码等，Git也不列外，版本控制系统可以告诉你每次的改动，但是图片，视频这些二进制文件，虽能也能由版本控制系统管理，但没法跟踪文件的变化，只能把二进制文件每次改动记录下来，也就是知道图片从1kb变成2kb，但是到底改了什么，版本控制也不知道。

---

### 五、使用Git — 文件入库

10.把文件添加到版本库
**第一步：** 在当前目录下创建一个文件，我这里创建一个`readme.txt`文件，并写入一行内容，我写入的是`aaaaa这是第一行`。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029132436873.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
**第二步：** 通过命令`git status`查看当前仓库文件的状态。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029133241323.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
我们可以看到，在`master`分支上有一个没有跟踪的文件`readme.txt`，这就是因为我们创建之后写了第一行之后没有添加到`暂存区`。
`补充知识：`工作区，就是在电脑里能看到的目录，暂存区，英文名叫stage，或者index，一般存放在`.git/index`中，所以我们把暂存区也叫做索引；版本库，工作区有一个隐藏目录`.git`这个不算工作区，是Git的版本库。

**第三步：** 使用`git add readme.txt`命令把readme.txt文件加入到暂存区。再使用`git commit -m "第一次提交readme.txt"`把readme.txt从暂存区提交到版本库。
![在这里插入图片描述](https://img-blog.csdnimg.cn/2019102913423983.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
从红色框中我们可以看到一个文件更改了，就是readme.txt。

**第四步：** 我们再通过`git status`看一下当前工作区的状态
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029134512981.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
我们可以看到，没什么可以做的了。

继续更改readme.txt内容，在之前的基础之上增加一行22222222内容，继续使用`git status`查看。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029140550509.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
从图中可以看到新修改了但是没有staged就是没有存入暂存区。

11.我们想看一下readme.txt到底改了什么内容，可以使用`git diff readme.txt`![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029143128802.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
从这里我们可以详细看到有哪些内容变动了。
清楚了被改动的地方，我们可以放心的提交到版本库了，使用`git add readme.txt`和`git commit -m " 增加了一行2222"`两条命令。

---

### 六、使用Git — 版本回退

通过上面，我们清楚了怎么修改文件并且再保存了，现在对readme.txt再继续进行修改，再增加一行内容为33333，继续执行上面的命令添加到版本库。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029145514970.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
现在我们对readme.txt总共已经进行了几次次修改，想要查看一下历史记录该怎么查？

12.使用命令`git log`查看历史版本记录
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029145926205.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
13.还可以按照每一次版本变更为一行内容进行显示，使用命令`git log --pretty=oneline`
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029150314428.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)

现在我需要版本回退，想把当前的版本回退到上一个版本，可以使用如下两种命令：
① `git reset --hard HEAD^`回到上一个版本，`git reset --hard HEAD^^`回退到上上一个版本，以此类推；
② 如果回退到前50个版本的话，使用方法①就显得不太明智了，我们可以使用简便命令操作：`git reset --hard HEAD~50`就可以了。
当前readme.txt文件内容如下：（使用Linux中的cat方法可以查看）
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029150945599.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
执行`git reset --hard HEAD^`命令回到上一版本，然后再通过cat查看：![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029151144945.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
我这里已经成功回到了上一版本了，我这里上一版本是最开始的空文件，是因为中间的几次更改我一边写帖子一边操作忘记添加到版本库了。

14.我们现在又想回到刚才回退之前的最新版本了，但是使用`git log --pretty=oneline`查看的是比当前老的版本，我们只能通过`git reflog`来查看比当前新的版本， 这时候我们看每一行都有一串黄色的字符，这个是每次的`版本号`。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029152021362.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
可以看到增加3333这一行对应的版本号，我们还可以通过`git reset --hard 版本号`到达指定版本号。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029152154960.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029152327600.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
按照版本号恢复之后，我们通过cat查看，可以看到是最新的版本了。

**小结一下：** `git add`把文件添加到暂存区 ； `git commit`提交更改到当前分支上；master是一个分支，前面的HEAD是master分支的名称。

------

我们现在再在readme.txt文件中添加一行内容为444444444，同时再新建一个文件test.txt内容testing, 先用命令`git status`查看一下状态，如下：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029152842950.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
15.先使用git add命令把2个文件都添加到暂存区，再使用`git status`来查看状态：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029153123282.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
再使用`git commit`一次性提交到分支上，如下：
![在这里插入图片描述](https://img-blog.csdnimg.cn/201910291533357.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)

---

### 七、使用Git — 撤销修改和删除文件

16.撤销修改
先在readme.txt文件中增加一行55555555555，通过命令查看：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029153639890.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
这时候我发现我新增加的555555内容有问题，我必须马上恢复以前的版本，现在可以采取的操作有：
① 如果知道要删掉的内容，直接可以手动去改掉，然后重新add并commit即可。
② 也可以按照前面版本回退的方法直接恢复到上一个版本。`git reset --hard HEAD^`
这时候我们还有第三种方法，先看一下当前状态：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029154012605.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
这个时候我们发现红线内告诉我们了说使用`git checkout -- file`可以丢弃工作区的修改，如下：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029154219516.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
我们来解释一下`git checkout -- readme.txt`这个命令：
① readme.txt自从修改之后还没放到暂存区，使用撤销修改就回到了和版本库一模一样的状态了。
② 另一种就是readme.txt已经放入暂存区看，接着又作了修改，撤销修改之后就回到了添加暂存区后的状态。
上面撤销55555就是情况①
对于第②种情况，我们对readme.txt添加一行内容为66666666666,接着git add添加到暂存区后，再添加内容77777，想通过撤销命令让其回到暂存区后的状态。如下：![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029155209126.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
这里要**注意**了，命令`git checkout -- readme.txt`中的 `--`不能省略，不然变成创建分支的命令了。

17.删除文件
现在在暂存区中增加b.txt文件，然后提交，再执行`rm b.txt`删除工作区的b.txt如下：![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029155924523.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
我们可以打开文件夹看到，b.txt已经不在工作区了。![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029160706213.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)

现在我们只是把b.txt从工作区中删掉了，但是前面我们已经把当前状态同步到了版本库了，注意这句话的表达方式，我为什么没说是把b.txt提交到版本库了，而是讲当前状态同步；

选择① 执行commit（commit有`交托给`的意思，可以品味一下这个命令的真正意义）命令，把当前状态提交到版本库，这样当前状态就会同步至版本库，版本库内的b.txt就会被删掉。

选择② 在我们没有commit之前，从版本库中恢复此文件下来：
可以使用`git checkout -- b.txt`
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029160928781.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
这时候我们可以看一下工作区的b.txt又回来了，如下：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029161035822.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)

---

### 八：创建SSH Key

1.注册GitHub账号。
2.创建SSH Key。`windows + R`键同时按，打开运行命令窗口，输入`.`进入家目录。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029162641996.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
输入`.`
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029162721200.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
看看这个目录下有没有`id_rsa`和`id_rsa.pub`这两个文件，如果有（那就奇了怪了！），一般第一次使用是没有的，真有的话可以直接跳过下面的命令。

打开命令行，执行命令：`ssh-keygen -t rsa -C "dmneil7o@icloud.com"`邮箱是自己GitHub账号;它会让你选择路径，还会让你设置密码，这里最好全部都按照默认，一路回车下去，如下：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029163434970.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
这时候我们再次打开家目录，会发现有一个`.ssh`文件夹，如下：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029163716555.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
如果上面的命令没有问题的话，也看不到这个文件夹肯定就是`隐藏文件显示按钮`没有打开，点击`查看(View)`把`隐藏的项目（Hidden items）`选项勾上。
打开`.ssh`这个文件夹，可以看到两个文件：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029164005866.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
`id_rsa`是私钥，不能泄露， `id_rsa.pub`是公钥，可以放心传播。

3.登录GitHub，打开`settings`找到`SSH Key`页面，点击`New SSH Key`， 填上标题，同时在Key文本框中粘贴`id_rsa.pub`文件的公钥内容。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029164429903.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029164546321.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029164736208.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
点击`Add SSH key`之后会跳转到输入密码的界面，我们需要输入GitHub密码来继续：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029165109570.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
接下来我们就可以看到我们新加的SSH key了，如下：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029165245205.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)

---

### 九、添加远程库

需求是：我们有本地的Git仓库，又想在GitHub中创建一个Git仓库，并且希望这两个仓库进行远程同步，这样GitHub的仓库别人就可以来写作了。
1.在GitHub上创建一个仓库，在页面右上角`➕`号选择新的仓库（New repository）；
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029165705431.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
2.填入仓库名称就可以了，直接点创建，如下：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029165952715.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
这时候一个新的仓库就建立完成了，目前这个仓库还是空的![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029170541162.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
页面提示说，我们可以有多种方法初始化这个仓库，我们按照给出的提示在本地仓库中运行下面的命令：
`git remote add origin https://github.com/duanmingpy/helloworld.git`
`git push -u origin master`
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029171116939.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
把提示的东西都输入完成之后就可以推送成功了，如下：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029171326815.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
这里使用的几个命令,其中`git push`命令，实际上是把当前分支master推送到远程。

因为远程库是空的，第一次推送master增加一个`-u`参数，这样Git不仅仅会把本地的master分支的内容推送到远程GitHub仓库中新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送和拉取就可以简化命令了。
我们刷新GitHub仓库的页面，这样就可以看到GitHub上的仓库和本地一模一样了。如下：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029171833850.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
现在开始，只要本地有commit，就可以使用`git push origin master`把本地master分支的最新修改交托给GitHub上了，现在就真正意义上的拥有了分布式版本库了。

---

### 十、从GitHub上克隆

【标题九】讲述了先有本地库更新，后有远程库。
现在考虑如果远程库有更新，怎么克隆到本地呢？

1.先准备一个远程库，在GitHub上再新建一个仓库，但是要有文件在，如下：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029172637219.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
创建完成之后如下：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029172908308.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
现在我们在命令行中进入一个新的空的文件夹中，然后执行克隆语句：
克隆语句：`git clone https://github.com/duanmingpy/remote_repo.git`，后面的地址是自己的
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029174609492.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
打开我们拉下来的文件夹就可以看到：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029174829232.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)

---

### 十一、创建与合并分支

在[上篇文章](https://blog.csdn.net/qq_38727847/article/details/102796482)的版本回退上我们就知道了，每次提交，Git都把它们串成一条时间线，这条时间线是一个分支。
到现在为止，我们还只有一个master主分支，HEAD严格来说是指向master，所以HEAD指向的就是当前分支，就像python中模块的`__main__`特殊变量一样。
现在我们来创建新的分支：
1.查看所有分支命令`git branch`
2.`git checkout -b 分支名` 创建并切换到这个分支
![在这里插入图片描述](https://img-blog.csdnimg.cn/2019102917581940.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
`git checkout`命令加上参数`-b`就代表创建之后切换到，相当于两条命令：
`git branch dy` 和 `git checkout dy` 相当于这两条。
`git branch`查看分支，会列出所有分支，当前分支前面有一个星号，上面用到了。

**分支之间的工作**
现在我们在dy分支上，我们查看一下README.md的内容，接着添加一行7777777，再把它添加到版本库。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029185304971.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
我们在dy分支上完成了提交之后，切换到master分支上查看README.md，如下：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029185700369.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
现在我们想要把dy分支上增加的内容合并到分支master分支上，可以在master分支上使用如下命令：
`git merge dy`
![在这里插入图片描述](https://img-blog.csdnimg.cn/2019102919004163.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
我们可以在执行合并那里看到一句`Fast-forword`这是因为执行的模式是`快进模式`，就是直接把master执行了dy的当前提交，所有合并速度快。
我们现在把dy分支删除：
`git branch -d dy`
![在这里插入图片描述](https://img-blog.csdnimg.cn/2019102919042632.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)

暂时先总结一下创建与合并命令：
查看分支`git branch`
创建分支`git branch name`
切换分支`git checkout name`
创建+切换分支`git checkout -b name`
合并某分支到当前分支`git merge name`
删除分支`git branch -d name`

------

下面我们考虑：
如果在dy分支上我们修改提交了新内容，在master上也修改提交了新内容，那么我们在合并的时候取谁的呢？
还是一步一步来，
1先创建一个新分支叫做dy，因为刚才把它给删掉了
2查看一下README.md的内容
3添加一些新内容
4提交到版本库
如下：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029191320336.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
同样的操作，我们切换到master分支上也添加两行内容：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029191719872.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
提交到版本库之后，我们在master分支上进行合并dy，如下操作：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029192300881.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
我们可以从上面这一张图可以仔细的分析出，两个分支上都做了新的提交，在合并的时候会有冲突，并且分支名也从master变成了`master | MERGING`， 同时我们`cat README.md`发现文件内容也变了，在`git status`上给我们提供了解决方法：`git commit`；
Git使用了`<<<<<<<` ; `========`;`>>>>>>>` 分别标记出不同分支修改的内容，我们可以打开文件修改成和主分支一致，然后在`master | MERGING`这个临时分支上进行`git commit`。
使用vscode打开查看：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029192859751.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
vscode默认给我们几个选项，我点击了`采用当前更改`按钮，变成了master提交的内容了，如下：
![在这里插入图片描述](https://img-blog.csdnimg.cn/2019102919302787.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
然后回到Git客户端，在`master | MERGING`分支上查看内容并进行提交操作，如下：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029193601593.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
经过这一系列的操作之后，我们可以通过`git log`查看分支合并情况：
![在这里插入图片描述](https://img-blog.csdnimg.cn/2019102919372132.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)

------

分支管理策略：
通常我们合并分支的时候，Git一般是用Fast forward模式，这种模式下，删除分支之后，会丢掉分支信息，现在我们来使用`-no-ff`来禁用Fast forward模式。
1创建一个dev分支。
2修改README.md内容。
3添加到暂存区。
4切换回dy分支。
5合并dev分支，使用命令`git merge -no-ff -m "注释内容" dev`
6查看历史记录
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029195017803.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
删除dev之后我们发现在最后的log中还有dev的操作。
分支策略：master主分支应该是非常稳定的，也是用来发布的新版本，一般情况下干活都不在master分支上干，都是在新建的分支上，干完之后需要发布，或者说新建分支代码稳定之后可以合并到主分支master上。

---

### 十二、bug分支

在开发过程中，bug问题是不能避免的，那么有了bug就需要修复，在Git中，由于拥有强大的分支，每个bug我们都可以通过一个临时分支来修复，修复完成之后合并分支，然后将临时的分支删除掉。

例如我在开发中接到一个404bug的时候，可以临时创建一个404分支来修复。但是我目前在的分支dev的开发工作还没有完成，但是bug需要五个小时内完成，怎么办？这时候Git有一个stash功能，可以将当前工作现场`隐藏到后台`，等以后再恢复现场继续工作。如下：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029195959501.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
接下来我们要知道bug是哪个分支上的，比如bug是master分支上的，我就需要再master分支上重新建一个分支：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029200442159.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
修复好bug之后切换到master分支，并合并，最后删除这个临时分支：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029200814630.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
现在又可以回到当前的分支上继续干活了。
要把我们的现场恢复回来：
通过`git stash list`查看隐藏的工作现场，
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029201128122.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
恢复的方式有两种：
1`git stash apply`，这种恢复方式恢复后stash内容并不删除，需要使用`git stash drop`来删除。
2另一种方式是使用`git stash pop`，恢复的同时把stash内容也删除了。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029201450316.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)

---

### 十三、多人协作

当我们从远程库克隆的时候，实际上Git自动把本地的master分支和远程的master分支对应起来了，并且远程库的默认名称是origin。
1.查看远程信息`git remote`
2.查看远程库详细信息`git remote -v`
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029202156861.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
**推送分支**
推送一个分支就是把该分支上所有本地提交到远程库上，推送的时候要制定本地的分支，Git会把该分支推送到远程库对应的远程分支上：
使用命令`git push origin master`
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029202609574.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
本地的README.md:
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029202653147.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
执行推送命令：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029202855928.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
推送成功之后我们刷新一下GitHub页面：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029203005225.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
需要推送哪个分支我们就把参数换成分支名就可以了。
`知识补充：`一般情况下master分支是主分支，因此要时时刻刻与远程同步；一些修复的bug分支是不需要推送到远程的，只要先在本地合并到主分支上，然后把主分支master推送到远程去即可。

**抓取分支：**
在进行多人协作时，大家都会往master分支上推送各自的修改，现在我们假设有另外一个同事，通过添加SSH Key添加到GitHub上，或者是同一台电脑上另外一个目录克隆。
先把dy分支也push到GitHub上：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029203944336.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
我们新建一个目录名就叫做：clonedir2
在这个目录下模仿另外一个同事也进行克隆这个项目：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029204127334.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
这个同事需要在dy分支上做开发，在终端用命令创建一个dy分支，现在就可以在dy分支上进行开发，开发完成后，把dy分支推送到远程库中。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029204903701.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
同事已经推送到远程了，这里我也改了一下这个文件，也想要推到远程：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029205447655.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
推送失败的原因是同事最近也提交了，提交到有冲突，上面提示我们，先用git pull把最新的提交抓取下来，然后在本地合并，解决冲突之后再推送。
先要指定本地dy分支与远程origin/dy分支的连接，根据提示设置dy分支和origin/dy的链接，如下：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029210132293.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
我们又看到了熟悉的MERGING临时分支了；
解决方式和之前是一样的，我先看一下内容，然后修改，然后再继续推送到远程中：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191029210607130.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI3ODQ3,size_16,color_FFFFFF,t_70)
所以：多人协作的工作模式是：
1可以试图用`git push origin branch name`推送自己的修改
2如果推送失败，是因为远程分支比本地更新早，需要先用`git pull`试图合并。
3如果合并有冲突，需要解决冲突，并在本地提交，使用`git push origin branch name`

------

**总结：**
Git基本常用命令如下：
创建目录`mkdir`
显示当前目录的路径：`pwd`
把当前的目录变成可以管理的Git仓库：`git init`
把xx文件添加到暂存区：`git add xx`
提交文件：`git commit -m "注释"`
查看仓库状态`git status`
查看xx文件修改了哪些内容`git diff xx`
查看历史记录`git log`
回退版本`git reset --hard HEAD^`或者`git reset --hard HEAD~50`
查看文件`cat xx`
查看历史记录的版本号id`git reflog`
把xx文件在工作区的修改全部撤销`git checkout -- xx`
删除xx文件`rm xx`
关联一个远程库`git remote add origin 地址`
把当前master分支推送到远程库`git push -u(第一次要用-u 以后不需要) origin master`
从远程库中克隆`https://github.com/duanmingpy/remote_repo.git`
创建dy分支并切换到`git checkout –b dy`
查看当前所有分支`git branch`
切换回master分支`git checkout master`
在当前的分支上合并dy分支`git merge dy`
删除dy分支`git branch –d dy`
创建分支`git branch name`
把当前的工作隐藏起来，等以后恢复现场后继续工作`git stash`
查看所有被隐藏的文件列表`git stash list`
恢复被隐藏的文件，但是内容不删除`git stash apply`
删除文件`git stash drop`
恢复文件的同时删除文件`git stash drop`
查看远程库的信息`git remote`
查看远程库的详细信息`git remote -v`
把master分支推送到远程库对应的远程分支上`git push origin master`