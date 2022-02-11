# 人人都能学会的游戏外挂软件——Cheat Engine

## **1.简介**

**Cheat Engine是一款强大的内存修改工具**

1.官方网站：[https://www.cheatengine.org/](https://link.zhihu.com/?target=https%3A//www.cheatengine.org/)

2.支持多种变量的搜索和修改，被广泛用来进行外挂开发

3.支持内存反汇编和修改功能，能够查看指定区域汇编代码并进行修改和插入自己的代码

5.支持**Lua**脚本语言，可以进行自动化操作

6.一系列的辅助工具帮助定位关键代码和关键数据

7.支持D3D视频，支持库的反汇编和分析

8.提供了相对傻瓜化的内存修改操作



## **2.打开官方自带游戏进程**



**2.1.打开Cheat Engine Tutorial**

![img](https://pic4.zhimg.com/80/v2-85e8926f826d92351476e04b4944dfef_720w.jpg)



**2.2.点击next**

可看到血条为100



![img](https://pic1.zhimg.com/80/v2-df5f5908f6c4ca115d719555db1e2390_720w.jpg)



## **3.选择游戏进程**



Application、Processes、Windows分别对应应用、进程与窗口，一般选择窗口

![img](https://pic2.zhimg.com/80/v2-e22d155b019f9504272cb2ed6c852de1_720w.jpg)



**3.1.选择相应窗口**



![img](https://pic3.zhimg.com/80/v2-381a1e7b018e8d34004319600f8a66d6_720w.jpg)







##  

## **4.修改游戏中的参数（一）**



**这一关可以看到准确的生命值**

4.1.通过搜索100（输入100，点击First Scan）来寻找生命值

值为100的变量太多了，无法找到生命值



![img](https://pic4.zhimg.com/80/v2-1b7e9f4d2a5a4a74767168ca8f40b1eb_720w.jpg)



**4.2.点击Hit me，可以看到生命值变为95**



![img](https://pic1.zhimg.com/80/v2-0a8c228c42bcf36da29f7688748f95dc_720w.jpg)



**4.3.此时输入95再点击Next Scan**



只剩下一个变量，即我们要改变的生命值



![img](https://pic1.zhimg.com/80/v2-7f0763100a9e8f4b220d33ba045fdc30_720w.jpg)



**4.4.双击该变量，将其加入到下面的列表中**



![img](https://pic4.zhimg.com/80/v2-28cb138f9e7a325c474854183ac001c7_720w.jpg)



**4.5.双击Value值所在位置，即可修改生命值**



![img](https://pic3.zhimg.com/80/v2-256dd364b715117d99563d7dc1618cae_720w.jpg)



![img](https://pic1.zhimg.com/80/v2-2e6c6ce3e3ec979ec5a9a2be226b539c_720w.jpg)



**4.6.按空格或者点击Active所在位置将其激活**



![img](https://pic4.zhimg.com/80/v2-df15a894b89390bb22a4561076ca2543_720w.jpg)



**4.7.此时再点击hit me时，生命值将维持在1000左右**



![img](https://pic1.zhimg.com/80/v2-a332cae6d904d7d99321d35ac9ca83cc_720w.jpg)



**4.8.点击next进入下一关，删除原先的记录**



![img](https://pic2.zhimg.com/80/v2-1041d7e3f8911bf54a60a7cbcaefee99_720w.jpg)



## **5.修改游戏中的参数（二）**



只知道生命值的范围，不知道具体的生命值

![img](https://pic4.zhimg.com/80/v2-24ad4714b0bf1dd91adb679b45463bab_720w.jpg)



**5.1.扫描类型改为Value between**



![img](https://pic4.zhimg.com/80/v2-0f0f4be8daab244ee9cdc51481b33bef_720w.jpg)



**5.2.输入0到500，开始新的扫描**



![img](https://pic3.zhimg.com/80/v2-3d18d201ddfe01cc51a6800d211aeb36_720w.jpg)



**5.3.点击Hit me，此时生命值减少**



![img](https://pic1.zhimg.com/80/v2-a9fa442321557c176cc5cffaf0591770_720w.jpg)





**5.4.扫描类型选择Decreased value**



再点击Next Scan，此时变量减少很多



![img](https://pic1.zhimg.com/80/v2-e1537e1c72c4a686ba05f2bca2d2c3ac_720w.jpg)



**5.5.重复上述步骤，只剩下一个变量，即生命值**



![img](https://pic1.zhimg.com/80/v2-6c10f540ea1b21eb4a9b3a42b8cdf1f8_720w.jpg)



**5.6.修改该变量的值，方法同 “修改游戏中的参数（一）”**



![img](https://pic4.zhimg.com/80/v2-f4d64f70185163af48596ef00b57377b_720w.jpg)



**5.7.点击Next，进入下一关**



![img](https://pic1.zhimg.com/80/v2-0e6164d52268e595d35b781b743ef290_720w.jpg)



## **6.修改游戏中的参数（三**）



有时候生命值或其他变量也会出现小数

![img](https://pic4.zhimg.com/80/v2-613cff6c19fa2745c4d4df2d426bd28f_720w.jpg)



**6.1.在Value Type中选择Float或Double即可**



其他同前面两种修改参数的方式



![img](https://pic3.zhimg.com/80/v2-417ee557c8ab01ea8c252478e097f8fa_720w.jpg)



**6.2.点击Next进入下一关（记得删除这一关修改值得记录）**



![img](https://pic1.zhimg.com/80/v2-8a4a96eba7d3ed1fd1148e40d78f97e0_720w.jpg)



## **7.修改游戏中的参数（四）**



**7.1.扫描值为100的变量**

![img](https://pic2.zhimg.com/80/v2-804e34e8631fa9b252ec50cf07e9a93d_720w.jpg)



**7.2.点击Change value修改生命值**



![img](https://pic3.zhimg.com/80/v2-bb9b61555c2d0a7192a91c6bbb2520ea_720w.jpg)



**7.3.扫描值为136的变量**



![img](https://pic4.zhimg.com/80/v2-438230df6cc9b42aa3f2033a8a4911cf_720w.jpg)


**7.4.查看是什么往这个地址里写东西**

这样就能找到修改这部分值得代码在哪儿



**这只是一个教程**，

在实际的游戏中可能会有一些反调试的内容，

如果我们在实际游戏中将Cheat Engine贸然加入到游戏中，那么游戏就可能出现崩溃，甚至一些比较严格的游戏厂家会直接进行封号操作，

最好不要拿一些真实的网游做测试，可以拿一些单击小游戏做测试

![img](https://pic2.zhimg.com/80/v2-3ca325f43c7b94a0677c962dac064d95_720w.jpg)



## 7.5.点击Change value可以看到有一条指令对内存进行了修改



把edx中的值放入到了[eax]中



![img](https://pic2.zhimg.com/80/v2-7035c42a3e56d1e5b6fcc6e175944e81_720w.jpg)



**7.6.eax对应的地址就是前面所搜索到的地址**



![img](https://pic2.zhimg.com/80/v2-d8f3d5b56985194739e2d71d35ea0bc5_720w.jpg)



**7.7.将指令替换为nop（在汇编中就是什么都不执行的意思）**



![img](https://pic1.zhimg.com/80/v2-641b1fbe7c703aac58f3e24fe996c9e0_720w.jpg)



**7.7.1.此时点击Change value，值已经不会再发生改变了**



![img](https://pic4.zhimg.com/80/v2-d58ef7728a051693f8d107d27c114f47_720w.jpg)



**7.8.点击高级选项即可看到前面修改的汇编指令**



![img](https://pic4.zhimg.com/80/v2-cd86aa11f974268b1f77958b80bcd8eb_720w.jpg)



**7.9.右键可选择恢复原始代码**



此时再点击Change value就又可以修改生命值了



![img](https://pic3.zhimg.com/80/v2-fd8ebb9f8a1a4d7a208fd489e4b196f6_720w.jpg)



后续关卡可自行进行尝试