# HTML学习笔记

> ——焦怡煖

## 学习背景

学会使用 Git 推送项目

学习如何与他人在Github 上协作完成项目

## 学习内容的目录

HTML笔记补充

## 学习内容

### HTML笔记补充

> 这里是对菜鸟教程中没有提及的内容的补充

#### 如何查看网页源代码

在空白处右击点检查

点击左上角小箭头

源代码——页面内容 可以相互锁定

#### VScode自动生成html代码

在VScode新建HTML文件，输入！，再点Tab，自动生成一个html代码

#### 水平线

<hr color="" with="" size="" align="/">

属性：

1.color:设置水平线的颜色

2.width：设置水平线的长度（单位px 像素）

3.size：设置水平线的高度（单位px 像素）

4.align：设置水平线的对齐方式

#### 标题

1.生成标题快捷键 h$*6

2.如何在VScode源代码处打开网页预览？

右击，选择open in brower

3.标题标签位置

在标签中添加属性：align="left/center/right"

#### 段落

自动生成段落标签：输入p，再点tab

#### 图像

<img src="" alt="" title="" width="">

<img>是单标签，不需要进行闭合操作

属性：

1.src：路径（图片地址与名字）

2.alt:规定图像的替代文本

3.width：规定图像的宽度

4.height:规定图像的高度

5.title：鼠标悬停在图片上给予提示

6.图片路径详解

（1）绝对路径：电脑的盘符储存与访问的具体地址

<img src="E:\略">

（2）相对路径：两者相对关系，两者在同一路径下可以直接访问

* 子级关系  /

  ![同级子级](C:\Users\lenovo\Desktop\同级子级.jpg)

* 父级关系  ../

  ![父级](C:\Users\lenovo\Desktop\父级.jpg)

* 同级关系  ./  (可省略)

  

（3）网络路径：具体的网络地址

<img src="http://略" alt="">

#### 链接

1.<a>里要写完整的URL，从http开始

2.点击图片跳转到其他位置

![图片链接](C:\Users\lenovo\Desktop\图片链接.jpg)

3.超链接表现

当把鼠标指针移动到网页中的某个链接上时，箭头会变为一只小手

#### 文本

1.<span> 无含义，为加CSS方便

2.标签可以嵌套使用

#### 列表

* 常见的应用场景

1.无序列表的列表效果

2.导航效果（可通过CSS调整位置）

* 快捷键

快速生成ul+li的布局：ul>li*3（数字需要根据自己需要的li数量修改）

#### 表格

* 快捷键

  table>tr*2>td

* 表格属性

1.border:设置表格的边框

2.width:设置表格的宽度

3.height:设置表格的高度

* 单元格合并

  水平合并 colspan

  垂直合并 rowspan

  ![合并单元格1](C:\Users\lenovo\Desktop\合并单元格1.jpg)
  
  ![合并单元格2](C:\Users\lenovo\Desktop\合并单元格2.jpg)
  
  ![合并单元格4](C:\Users\lenovo\Desktop\合并单元格4.jpg)
  
  ![合并单元格3](C:\Users\lenovo\Desktop\合并单元格3.jpg)
  
  
  
  #### 表单
  
  表单是由容器和控件组成的，一个表单一般应该包含用户填写信息的输入框、按钮等，这些输入框、按钮叫做控件，表单就是容器，它能够容纳各种各样的控件
  
  <form action="url" method="get/post" name="myform"></form>
  
* 属性说明
action 服务器地址
name 表单名称
* method中post和get的区别
1.数据提交方式，get把提交的数据url可以看到，post看不到

2.get一般用于提交少量数据，post一般用于提交大量数据

* 表单元素
  1.表单标签
  2.表单域
  3.表单按钮

  
  #### 区块
 * 内联元素和块级元素的区别 
 |   块级元素 | 内联元素 |
 | :-----: | :--: |
 | 块元素会在页面中独占一行 （自上而下垂直排列）|  行内元素不会独占页面中的一行，只占自身的大小   |
 |   可以设置width,height属性 |  行内元素设置width,height属性无效  |
 |    一般块级元素可以包含行内元素和其他块级元素 | 一般内联元素包含内联元素 不包含块级元素  |

* 常见块级元素

  > div、form、h1~h6、hr、p、table、ul等

* 常见内联元素

  > a、b、em、i、span、strong等

* 行内块级元素（特点：不换行，能够识别宽高）

  > button、img、input等


## 参考资料

1. [HTML 简介 | 菜鸟教程](https://www.runoob.com/html/html-intro.html)
2. 2.[bilibili学习视频](https://www.bilibili.com/video/BV1oz421q7BB/?spm_id_from=333.337.search-card.all.click&vd_source=6aba70bfaeecdb8314d86a42c169cfd0)