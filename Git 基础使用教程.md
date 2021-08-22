# Git 基础使用教程

[toc]



GitHub 作为全球最大的程序员交友网站(开源及私有软件项目的托管平台)，身为程序员怎么能不熟悉为之添砖加瓦的操作。

## Git

Git 是一个开源的分布式版本控制系统，我们可以使用 Git 将代码上传至 GitHub。同时，GitHub 只支持 Git 作为唯一的版本库格式进行托管。

## 本地生成 ssh key

你的本地 Git 仓库和 GitHub 仓库之间的传输是通过SSH加密的，所以我们需要配置验证信息，使用以下命令生成 SSH Key：

```tex
$ ssh-keygen -t rsa -C "你自己的邮箱" 
```

之后会要求确认路径和输入密码，我们这使用默认的一路回车就行。成功的话会在 用户根目录下生成 .ssh 文件夹，点进去进去，打开 id_rsa.pub，复制里面的 key。

## GitHub 中添加 ssh key

打开 Github，进入 Account => Settings（账户配置）。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191201205809965.png)

左边选择 SSH and GPG keys，然后点击 New SSH key 按钮,title 设置标题，可以随便填，粘贴在你电脑上生成的 key。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191201210506862.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MTMwODU3Mw==,size_16,color_FFFFFF,t_70)

## GitHub 上创建仓库

点击" New repository " 如下图所示：
![在这里插入图片描述](https://img-blog.csdnimg.cn/2019120121125858.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MTMwODU3Mw==,size_16,color_FFFFFF,t_70)

之后在在Repository name 填入 test(远程仓库名) ，其他保持默认设置，点击"Create repository"按钮，就成功地创建了一个新的Git仓库：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191201211536323.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MTMwODU3Mw==,size_16,color_FFFFFF,t_70)创建成功后，显示如下信息：![在这里插入图片描述](https://img-blog.csdnimg.cn/2019120121174521.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MTMwODU3Mw==,size_16,color_FFFFFF,t_70)
我们已经在 GitHub 上成功创建仓库。

## 本地上传

在上传之前我们使用 Git 配置用户信息，运行以下命令：

```tex
$ git config --global user.name "名字"
$ git config --global user.email "你的邮箱"
```


之后我们进入到保存我们想要上传代码的文件中，执行初始化本地仓库命令：

```tex
$ git init
```


之后将本地代码全部添加到暂存区：

```tex
$ git add .
```


添加备注信息：

```tex
$ git commit -m "第一次提交"
```


绑定远程仓库（仅第一次需要）

```tex
$ git remote add origin https://github.com/Lian-Zekun/test.git
```


选择 main 分支

```tex
$ git branch -M main
```


提交代码到远程仓库

```tex
$ git push -u origin main
```

---

## 其他PC端获取代码

首先在该 PC 端生成 ssh key 并添加到自己的 GitHub 中。
拉取代码：

```tex
$ git clone https://github.com/Lian-Zekun/test.git
```

## 更新代码

首先需要保证本地代码和远程代码文件是匹配的，如何双方文件存在差异可能会报错：error: failed to push some refs to …
如果不同步，执行以下命令：

```tex
$ git pull
```

添加代码到暂存区：

```tex
$ git add -u
```

或

```tex
$ git add -A
```

-u 表示将所有已跟踪的文件的修改和删除信息添加到暂存区。
-A 表示将所有已跟踪的文件的修改、删除信息以及新增文件的信息添加到暂存区。

添加备注信息：

```tex
$ git commit -m "第二次提交"
```

提交代码到远程仓库

```tex
$ git push origin main
```

