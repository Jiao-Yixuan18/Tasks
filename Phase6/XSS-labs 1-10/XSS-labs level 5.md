# XSS-labs level 5

#### 漏洞原理

原理：攻击者（我）在payload里构建恶意脚本，服务器接收到恶意脚本后，对它进行了过滤，如这一关中的`o_nclick`和`scr_ipt`，从而防御攻击，可以用javascript伪协议来绕过，服务器把我输入的payload拼接到html里返回给浏览器，浏览器解析执行，实现攻击（跳出弹窗）


#### 漏洞复现

1.打开开发者工具，原理依旧是触发弹窗跳转下一关

![5-1](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase6/phase6-png/5-1.png)

2.试试level5方法

![5-2](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase6/phase6-png/5-2.png)

![5-3](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase6/phase6-png/5-3.png)

失败了，查看源代码，是否有过滤或转义

![5-4](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase6/phase6-png/5-4.png)

发现onclick被过滤，尝试闭合input标签加上js代码

![5-5](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase6/phase6-png/5-5.png)

![5-6](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase6/phase6-png/5-6.png)

![5-7](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase6/phase6-png/5-7.png))

出现了过滤，试试别的xss绕过语句

3.尝试闭合后添加a标签，用javascript伪协议



![5-8](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase6/phase6-png/5-8.png)



![5-9](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase6/phase6-png/5-9.png)



level5通关




