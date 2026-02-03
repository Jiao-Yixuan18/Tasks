# vulfocus-pikachu 1

#### 漏洞原理

攻击者（我）将含有恶意脚本的payioad输入提交框中，服务器接收到后，没有对其进行过滤和转义等防护操作，直接将其拼接到要返回给浏览器的html中，浏览器解析渲染并执行，实现`<script>alert('xss')</script>`的效果

#### 漏洞复现

1.打开靶场，输入个1试试

![p1-1](D:\Geek考核\Phase6\phase6-png\p1-1.png)

出现一小行字：who is 1,I don't care!

![p1-2](D:\Geek考核\Phase6\phase6-png\p1-2.png)

2.打开开发者工具，在源码里发现提示，输入kobe

![p1-3](D:\Geek考核\Phase6\phase6-png\p1-3.png)

出现了科比的图片，在输入`<script>aler('xss')</script>`试试能否弹出框

但是输入了一部分之后，输入不进去了，查看源码原来是`maxlength`属性做了限制，把20改为200

![p1-3](D:\Geek考核\Phase6\phase6-png\p1-3.png)

![p1-4](D:\Geek考核\Phase6\phase6-png\p1-4.png)

补完payload

![p1-5](D:\Geek考核\Phase6\phase6-png\p1-5.png)

点击提交

![p1-6](D:\Geek考核\Phase6\phase6-png\p1-6.png)