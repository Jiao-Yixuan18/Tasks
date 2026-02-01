# XSS-labs level 1

#### 漏洞原理

原理：攻击者（我）将恶意脚本（`<script>alert(1)</script>`）作为UPL参数的一部分传递给服务器，服务器没有对这些参数进行过滤和验证，直接拼接进响应页面，返回含有恶意脚本的HTML页面，浏览器解析并执行恶意脚本，从而使弹窗弹出

#### 漏洞复现

1.打开开发者工具查看源代码

![](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase6/phase6-png/1-1.png)

2.在源代码里找到一段js代码

![1-1.5](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase6/phase6-png/1-1.5.png)

这段代码重写了alert函数，任何地方调用alert()时，都会执行这个自定义函数

`confirm()`是弹窗函数，弹出一个带有“确定”和“取消”的弹窗

`window.location.href`的值是页面跳转的地址栏

level1中`window.location.href`的值就是level2

所以通关的关键就是让这个弹窗弹出来，跳转到下一关

2.这个页面中只有地址栏能够输入，猜测这里存在xss漏洞

name的值test在浏览器被渲染出来，所以可以通过修改name的值实现把js代码写进html文本，实现攻击

把name的值修改为`<script>alert(1)</script>`

![1-2](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase6/phase6-png/1-2.png)

3.回车，浏览器渲染时，遇到html里的被我输入的js代码，执行它

![1-3](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase6/phase6-png/1-3.png)

跳出弹窗：完成的不错！

level1通关

#### 问题

* Q1：为什么服务器会将恶意脚本作为响应内容返回给浏览器，浏览器没有防御功能吗？

  A1：服务器防护机制存在缺陷或匹配不到位，给了攻击者可乘之机，可以绕过或利用这些漏洞

  例如，在level1中，攻击者（我）把恶意脚本`<script>alert(1)</script>`写进URL参数里，服务器没有对攻击者（我）的输入进行防护，把xss代码当作普通代码执行，从而触发攻击（跳出弹窗）

* Q2：服务器防护机制失效的因素

  A2：

	* 没有对用户输入的数据进行严格的过滤、转义或长度限制
	* 没有启用web应用防火墙等防护机制，或者防护机制的规则宽松，无法识别恶意脚本 
	
* Q3：为什么浏览器会配合执行恶意脚本

  A3：浏览器的安全模型是“信任服务器返回的内容”，它无法区分输入的脚本是合法的还是恶意的，只要服务器返回的html里包含恶意脚本js代码，它就会执行

  





