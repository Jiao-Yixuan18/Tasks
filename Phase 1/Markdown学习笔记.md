# Markdown是什么

Markdown是什么Markdown 是一种轻量级标记语言，创始人为约翰·格鲁伯（John Gruber）。它允许人们使用易读易写的纯文本格式编写文档，然后转换成有效的 XHTML（或者HTML）文档。这种语言吸收了很多在电子邮件中已有的纯文本标记的特性。
由于 Markdown 的轻量化、易读易写特性，并且对于图片，图表、数学式都有支持，许多网站都广泛使用 Markdown 来撰写帮助文档或是用于论坛上发表消息。讨论如 GitHub、Reddit、Diaspora、Stack Exchange、OpenStreetMap、SourceForge、简书等，甚至还能被使用来撰写电子书。

Markdown 编写的文档可以导出 HTML 、Word、图像、PDF、Epub 等多种格式的文档。

Markdown 编写的文档后缀为 .md, .markdown

---
# Markdown的优势

1.纯文本编辑，只要是支持Markdown编辑的都能获得同样的结果，摆脱排版苦恼

2.学习成本低，常用的语法很少，简单易学快速上手

3.支持跨平台同步数据

4.支持插入图片、视频等

5.随时修改，不必担心word等工具出现排版错误

---
# Markdown语法

### 一、标题

使用#号标记，可以表示1-6级标题， 随#的个数递增，一级标题字号最大，六级标题字号最小。

#一级标题

##二级标题

###三级标题

####四级标题

#####五级标题

######六级标题

### 二、字体

<img width="578" height="311" alt="字体" src="https://github.com/user-attachments/assets/edc680d2-f886-4bd8-b795-5b7c2b8a76e3" />

### 三、换行

Markdown换行的方式有很多种:

直接在一句话后敲两个空格

两句话之间加一个空行

如果你在编辑的时候，想让一行文字在显示的时候换行，就在中间加<br/>

### 四、引用

Markdown 中引用通过符号 > 来实现。> 符号后的空格，可有可无。

在引用的区块内，允许换行存在，换行并不会终止引用的区块。如果要结束引用，需要一行空白行，来结束引用的区块。

引用的嵌套使用：

<img width="301" height="80" alt="引用" src="https://github.com/user-attachments/assets/2758f9e4-27a0-430b-9200-8dfd9fee3b14" />


>这是一个引用

>>这是一个引用的引用

>>>这是一个引用的引用的引用

### 五、链接


[链接名称] (链接地址)

<链接地址>

即是：

[这是Jiao-Yixuan18的主页](https://github.com/Jiao-Yixuan18/Jiao-Yixuan18.git)

或者

<https://blog.csdn.net/qq_40818172?type=lately>

### 六、图片

Ctrl+v粘贴图片

### 七、列表

列表分为有序列表和无序列表

无序列表，使用*、+、-，再加一个空格作为列表的标记

有序列表，使用数字并加上.号，再加一个空格作为列表的标记

<img width="577" height="391" alt="列表一" src="https://github.com/user-attachments/assets/dc62a7ee-a32e-48bb-a2a8-94de1ae95d8c" />


如果想要控制列表的层级，则需要在列表符号前使用Tab

<img width="592" height="488" alt="列表二" src="https://github.com/user-attachments/assets/b00d706a-e952-46d9-ab1d-9c29e844832e" />

### 八、分割线

分割线的使用，可以在一行中用三个-or*来建立一个分割线，但是注意：在分割线的上面空一行！！！

### 九、删除线

在要添加删除线的文字**前后**添加**两个~**

### 十、下划线

在需要添加下划线的文字**首尾**添加<u>文本</u>

### 十一、代码块

Markdown中代码块有两种：

* 如果在一行内需要引用代码，只需要用反引号`引起来

<img width="590" height="173" alt="代码块1" src="https://github.com/user-attachments/assets/7a95c069-faff-4035-9462-c7bdd3b95221" />


* 如果是在一个块内需要引用代码，则在需要引用的代码块的前一行和后一行使用三个反引号，同时在前一个反引号后写入代码的语言。

<img width="596" height="283" alt="代码块2" src="https://github.com/user-attachments/assets/ca38b369-460d-4f52-999c-5bde9e2f7046" />

### 十二、表格

表格使用|来分割不同的单元格，使用-来分隔表头和其他行

* :-：将表头及单元格内容左对齐

* -:：将表头及单元格内容右对齐

* :-:：将表头及单元格内容居中

<img width="191" height="82" alt="表格" src="https://github.com/user-attachments/assets/e269af75-e84d-46fc-be70-2f086200bc8d" />

| 项目   |   价格 | 数量 |
| ------ | -----: | :--: |
| 计算机 | \$1600 |  5   |
| 手机   |   \$12 |  12  |
| 管线   |    \$1 | 234  |

### 十三、脚注

<img width="586" height="127" alt="脚注" src="https://github.com/user-attachments/assets/852cf4cf-5efd-475f-b6db-c571171a8ca3" />

使用 Markdown[^1]可以效率的书写文档, 直接转换成 HTML[^2], 你可以使用 Typora[^T] 编辑器进行书写。
[^1]:Markdown是一种纯文本标记语言
[^2]:HyperText Markup Language 超文本标记语言
[^T]:NEW WAY TO READ & WRITE MARKDOWN.

### 十四、特殊符号

<img width="590" height="164" alt="特殊符号" src="https://github.com/user-attachments/assets/b1c328bd-bdab-4c41-a27d-992c34c146d3" />

效果
\\
\*
\_
\+
\.

---

# Markdown的高级用法

### 一、制作待办事项

制作一个待办事项，格式为、-[] 表示未完成；-[x]表示已完成

<img width="565" height="106" alt="待办" src="https://github.com/user-attachments/assets/c52284aa-9a18-457c-b272-1d447440585d" />

- [ ] 支持以 PDF 格式导出文稿
- [ ] 改进 Cmd 渲染算法，使用局部渲染技术提高渲染效率
- [x] 新增 Todo 列表功能
- [x] 修复 LaTex 公式渲染问题
- [x] 新增 LaTex 公式编号功能

### 二、书写公式

$$表示整行公式

在公式前写$$

### 三、绘制流程图

<img width="352" height="286" alt="image" src="https://github.com/user-attachments/assets/5bdc4748-6aaf-4e23-9214-0e7e2bc1ca45" />

<img width="581" height="346" alt="流程图2" src="https://github.com/user-attachments/assets/a0d4208f-cee7-4bd2-ac99-b24a17d7698a" />

### 四、绘制序列图

<img width="545" height="476" alt="image" src="https://github.com/user-attachments/assets/74537060-aca9-45cb-9e42-b5aa0639e9fa" />

### 五、绘制甘特图

<img width="406" height="343" alt="甘特图1" src="https://github.com/user-attachments/assets/3a1d82bb-f7ec-4d7b-943e-189d8293bd3e" />

<img width="591" height="285" alt="甘特图2" src="https://github.com/user-attachments/assets/b961eda6-a30b-40e8-8cb6-cde48b1d4719" />

### 六、Html

* Markdown支持原生HTML语法

例：

效果：

<table>
    <tr>
        <th rowspan="2">值班人员</th>
        <th>星期一</th>
        <th>星期二</th>
        <th>星期三</th>
    </tr>
    <tr>
        <td>李强</td>
        <td>张明</td>
        <td>王平</td>
    </tr>
</table>

* 可以实现对字体格式的改变