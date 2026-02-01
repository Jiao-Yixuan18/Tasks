# XSS-labs level 8
#### 漏洞原理

攻击者（我）将含有恶意脚本的payload输入“添加友情链接”的框里，这段字符串不仅是input标签中value的值，还是表单下面a标签href属性的值，但是服务器接收到这些代码后，会进行html实体转义、过滤js伪协议、双写、大小写混淆，于是对js伪协议进行Unicode编码来实现绕过，服务器正常接受这段字符串，并拼接到html里返回给浏览器，浏览器解析渲染执行，实现攻击


#### 漏洞复现

1.页面有一个链接

![8-1](D:\Geek考核\Phase6\phase6-png\8-1.png)

点一下试试

![8-2](D:\Geek考核\Phase6\phase6-png\8-2.png)

404 没有找到资源

2.试试闭合input标签

![8-3](D:\Geek考核\Phase6\phase6-png\8-3.png)

没变化，查看源代码

![8-4](D:\Geek考核\Phase6\phase6-png\8-4.png)

发现html中的一些特殊符号被实体转义了

而且，输入的内容变成了下边链接href属性的值

所以可以通过输入来控制href属性值

所以可以试试javascript伪协议

3.试试javascript伪协议

![8-5](D:\Geek考核\Phase6\phase6-png\8-5.png)

点击按钮和链接都没反应，查看源码

![8-6](D:\Geek考核\Phase6\phase6-png\8-6.png)

发现被过滤了

4.试试双写绕过

![8-7](D:\Geek考核\Phase6\phase6-png\8-7.png)



![8-8](D:\Geek考核\Phase6\phase6-png\8-8.png)

依旧被过滤

5.试试大小写混淆

![8-9](D:\Geek考核\Phase6\phase6-png\8-9.png)



![8-10](D:\Geek考核\Phase6\phase6-png\8-10.png)

依旧被过滤

6.浏览器在解析js属性值时,支持十进制和十六进制Unicode编码形式，所以可以把href的值改为javascript伪代码的Unicode形式

![8-11](D:\Geek考核\Phase6\phase6-png\8-11.png)

![8-12](D:\Geek考核\Phase6\phase6-png\8-12.png)

![8-13](D:\Geek考核\Phase6\phase6-png\8-13.png)