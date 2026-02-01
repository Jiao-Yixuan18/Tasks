# XSS-labs level 9
#### 漏洞原理

攻击者（我）将含有恶意脚本的payload输入“添加友情链接”的输入框里，服务器进行html实体转义、双写过滤、大小写混淆过滤，于是对被过滤的部分进行编码来绕过，服务器接收并将payload拼接到html中，返回含恶意脚本的HTML页面给浏览器，浏览器解析并执行


#### 漏洞复现

1.试试javascript伪代码

![9-1](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase6/phase6-png/9-1.png)

![9-2](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase6/phase6-png/9-2.png)

提示：您的链接不合法？有没有！

2.查看源码

![9-6](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase6/phase6-png/9-6.png)

发现输入的值不能再和上关一样，能写入a标签的href属性值里

在博客学习level9复现过程，发现需要检查后台源代码

3.用vscode打开level9.php查看![9-4](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase6/phase6-png/9-4.png)

`strpos()`函数的作用是在字符串$str7中查找子串‘http://'第一次出现的位置：

* 找到了：返回子串在$str中的起始引索位置（从0开始计数）

* 没找到：返回布尔值false

  所以这串代码的意思是，在我输入的字符串中，如果'http://'存在，则这个函数返回'http://'的起始引索位置，而这个返回值是一个数，显然与布尔值`false`不能严格相等，进入else分支，href的值是我输入的字符串；

  如果’http://‘不存在，则这个函数返回false，if语句的条件成立，进入if分支，href的值是“您的链接不合法？有没有！”

所以得在payload里构造一个http://的结构，加上可执行的js代码，才能通关

4.构造payload



![9-5](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase6/phase6-png/9-5.png)

被转义了

再试试大小写混淆，依旧被过滤

试试双写绕过，依旧被过滤

5.试试javascript伪代码，把http://注释掉

![9-15](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase6/phase6-png/9-15.png)



![9-16](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase6/phase6-png/9-16.png)依旧被过滤，试试编码

![9-10](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase6/phase6-png/9-10.png)

![9-13](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase6/phase6-png/9-13.png)

![9-14](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase6/phase6-png/9-14.png)

通关了

#### 总结一下现在遇到了绕过方式

* 大小写混淆
* 双写
* 编码
* js伪协议

