# XSS-labs level 10
#### 漏洞原理

攻击者（我）将含恶意脚本的payload写入URL参数中，并修改input标签的type属性值，使输入框暴露出来，实现点击完成攻击。点击时，服务器接收这段payload并拼接到响应页面，返回含有恶意脚本的html代码给浏览器，浏览器解析并执行，实现攻击


#### 漏洞复现

1.页面没有输入框了

![10-1](D:\Geek考核\Phase6\phase6-png\10-1.png)

看看源码

![10-2](D:\Geek考核\Phase6\phase6-png\10-2.png)

发现`input`标签里`type`属性的值是`hidden`，输入框被隐藏了

2.从url栏里输入参数

![10-3](D:\Geek考核\Phase6\phase6-png\10-3.png)

js代码没有执行

3.在url给input传参

![10-4](D:\Geek考核\Phase6\phase6-png\10-4.png)

![10-5](D:\Geek考核\Phase6\phase6-png\10-5.png)

发现只有t_sort的参数被传入了，所以可以利用t_sort来构造payload

4.沿用上一关方法，把hidden注释掉

![10-6](D:\Geek考核\Phase6\phase6-png\10-6.png)

![10-7](D:\Geek考核\Phase6\phase6-png\10-7.png)

发现`>`被过滤了

5.换个思路，直接在开发者工具将type的值改为button

![10-8](D:\Geek考核\Phase6\phase6-png\10-8.png)

点击页面上出现的写有4的按钮

![10-9](D:\Geek考核\Phase6\phase6-png\10-9.png)

level 10通关