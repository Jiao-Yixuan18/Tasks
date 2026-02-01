# XSS-labs level 6
#### 漏洞原理

攻击者（我）将含有恶意脚本的payload输入搜索框中，但是服务器出于防护，对href、onclick、script等进行了过滤（这里写等是因为我试的这几个方法确实都被过滤了，或许还有其他情况），于是用大小写混淆来绕过，服务器对大小写混淆没有过滤，将payload拼接进html代码里，返回给浏览器，浏览器解析HTML代码，渲染，最后执行js代码，实现攻击

#### 漏洞复现

1.试试javascript伪协议

![6-1](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase6/phase6-png/6-1.png)

不行，打开开发者工具看看是什么原因

![6-2](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase6/phase6-png/6-2.png)

href被过滤了

2.试试onclick

![6-3](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase6/phase6-png/6-3.png)

![6-4](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase6/phase6-png/6-4.png)

onclick被过滤了

3.试试js代码

![6-5](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase6/phase6-png/6-5.png)

![6-6](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase6/phase6-png/6-6.png)

前面的script被过滤了

4.试试大小写混淆，把script中被过滤的改成大写

![6-7](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase6/phase6-png/6-7.png)

![6-8](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase6/phase6-png/6-8.png)


level6通关
