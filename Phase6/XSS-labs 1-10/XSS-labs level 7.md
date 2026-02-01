# XSS-labs level 7
#### 漏洞原理

攻击者（我）将含有恶意脚本的payload输入搜索框，但是服务器出于保护，将script整个过滤了，代码中只剩空白，于是用双写`“><scrscriptipt>alert(7)<scrscriptipt>`来绕过，绕过成功，服务器将这段payload拼接进html代码中并返回给浏览器，浏览器解析返回来的html代码，渲染执行，实现攻击


#### 漏洞复现

1.试试js代码

![7-1](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase6/phase6-png/7-1.png)

![7-2](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase6/phase6-png/7-2.png)

发现script整个被过滤了

2.试试双写绕过

![7-3](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase6/phase6-png/7-3.png)

![7-4](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase6/phase6-png/7-4.png)


level7通关
