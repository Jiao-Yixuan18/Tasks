# JS学习笔记

> ——焦怡煖

## 学习背景

已学习HTML CSS基础

## 学习内容的目录

- 这是内容[A](#A)
- 这是内容[B](#B)

## 学习内容

### JavaScript是什么

+ JavaScript是什么

JavaScript 是一种轻量级的编程语言。

JavaScript 是可插入 HTML 页面的编程代码。

JavaScript 插入 HTML 页面后，可由所有的现代浏览器执行。

+ JavaScript可以用来做什么
1. Web/移动端 APP
2. 实时联网 APP
3. 命令行工具
4. 游戏
+ JavaScript 在哪里运行？
在浏览器，有JavaScript引擎
FireFox:SpiderMonkey
Chorme:V8
Node是一个包含谷歌浏览器V8引擎的C++程序，实现了在谷歌浏览器外跑C++
### 第一个JavaScript程序

打开浏览器，按F12，打开开发者工具，点击Console按钮，这是JavaScript控制台，在其中可以写JavaScript代码
1. ```JavaScript
console.log('Hello World');
回车执行可得到Hello World
2. 数学运算
2+2
回车得到4
3. 输入alert函数
例：输入alert('yo');
回车浏览器蹦出一个带yo的窗口
### 搭建开发环境
VS code(推荐)
Sublime Text
Atom	

node

[node安装教程](https://blog.csdn.net/python_0011/article/details/132109189?ops_request_misc=elastic_search_misc&request_id=ef5729efc2995b8e48a00a6294b7e419&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-132109189-null-null.142^v102^pc_search_result_base5&utm_term=%E4%B8%8B%E8%BD%BDnode&spm=1018.2226.3001.4187)

在VScode新建html（作为JS容器）

### 在浏览器里使用JS文件

可以在head和body标签里添加script标签（一般放在body最后，浏览器先渲染内容，效率高）

### 编程原则之关注点分离

将js文件（页面上的行为）与html（页面内容）分离出来，将关注点分离，实现每个代码的职责单一

1. 在VScode里新建一个js文件
2. 将html里script标签里的内容剪切放进js文件
3. 在html里script标签里添加属性src=“js文件名”，这会告诉浏览器Javascript代码在该文件中

### 变量与常量

用var（用得少）,let（声明变量）,const（声明常量）
let值可以被修改，const不能
当const声明数组或者对象时，其内部元素可以被改变，只是不能将整个数组完全更改
使用const时，在声明时就初始化数值

### 数据类型

值类型(基本类型)：字符串（String）、数字(Number)、布尔(Boolean)、空（Null）、未定义（Undefined）、Symbol。

引用数据类型（对象类型）：对象(Object)、数组(Array)、函数(Function)，还有两个特殊的对象：正则（RegExp）和日期（Date）。

### 模版字符串




## 参考资料

1. [JavaScript]()
2. [bilibili]