# Git 常见问题以及解决方案

[toc]

## git 链接GitHub仓库详解



## git 上传代码

### 官方方法：新建一个仓库之后

…or create a new repository on the command line



```
echo "# MindMasterNoteBook" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:wihang/MindMasterNoteBook.git
git push -u origin main
```

…or push an existing repository from the command line



```
git remote add origin git@github.com:wihang/MindMasterNoteBook.git
git branch -M main
git push -u origin main
```

…or import code from another repository

You can initialize this repository with code from a Subversion, Mercurial, or TFS project.

[Import code](https://github.com/wihang/MindMasterNoteBook/import)



## git 上传代码以及更新

### 问题：

#### 在提交代码以及clone出现 fatal: unable to access 'https://github.com/ 如何解决？

- 解决方案一
  1、看看你的git配置
  git config --global -l

  如果你没有任何与https代理相关的内容，例如https_proxy = …问题不在这里。

  如果您有与https代理相关的内容，请将其从〜/ .gitconfig文件中删除，然后重试。

  2、如果仍然不起作用，请取消设置环境变量
  env|grep -i proxy

  你应该有一行或几行https_proxy = …

  使用以下内容逐个取消设置：取消设置https_proxy（或HTTPS_PROXY，具体取决于变量的名称）

  3、再次检查环境变量
  env|grep -i proxy

  如果它没有显示任何你应该是好的。

  注意：此解决方案可以应用于http和https代理问题。只是变量名称从https更改为http。

- 解决方案二
  在开启shadowsocks的前提下，手动配置git的代理。git客户端输入如下两个命令就可以了。

  git config --global http.proxy http://127.0.0.1:1080

  git config --global https.proxy http://127.0.0.1:1080

  http://也可以改成sockets5://,但是区别在于：socks5不支持通过pubkey免密登录github，每次提交代码只能输入用户名和密码。http可以支持免密登录。

  取消代理：

  git config --global --unset http.proxy

  git config --global --unset https.proxy

  其实方案一和方案二是同一种方法，不过方案二更加具体一点罢了，大部分问题都可以用方案二解决，当方案二无效时，考虑使用方案一。

---

#### [关于git报 warning: LF will be replaced by CRLF in README.md.的警告的解决办法](https://www.cnblogs.com/h-flower/p/11212502.html)

​	在使用git把代码上传至仓库时，会有下面这种警告：

![img](https://img2018.cnblogs.com/blog/1551991/201907/1551991-20190719120746350-1369403204.png)

​	虽然说是警告，但是看着真的很碍眼啊，特别是有强迫症的人就更难受了。

​	输入这一行命令就可以完美解决了

​	git config core.autocrlf false
