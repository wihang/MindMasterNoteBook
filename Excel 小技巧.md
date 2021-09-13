# Excel 小技巧

## 如何设置每行颜色

  在编写测试案例的时候，众多的excel行看的眼睛花花的，这里给出一个小技巧，设置Excel的每行显示的颜色不一样，最终的效果如下：

![image](https://images0.cnblogs.com/blog/350213/201412/301123417311055.png)

  具体操作：

  \1. Ctrl+A全选所有表格区域或者用鼠标选择指定设置的区域

  \2. 选择![image](https://images0.cnblogs.com/blog/350213/201412/301123430752312.png)

  \3. ![image](https://images0.cnblogs.com/blog/350213/201412/301123454663382.png)

菜单找到自定义格式
选择公式
输入=mod(row(),2)=1
设置颜色
添加公式
输入=mod(row(),2)=0
设置另一个颜色

---

## 如何添加下拉选项框

![image-20210913121342416](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210913121342416.png)

数据 —— 数据验证 —— 选择序列

![image-20210913121409503](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210913121409503.png)

![image-20210913121442469](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210913121442469.png)

来源可以选择范围，即你输入的范围