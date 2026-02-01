# XSS-labs level 4

#### 漏洞原理

类型：反射型xss

原理：这一关的漏洞原理与上一关类似，只是这里双引号没有没HTML实体编码，且源代码中用“闭合，所以构造一个payload：” onclick=alert(4) type="

攻击者（我）将上面这个含有恶意脚本的payload输入进搜索框，服务器接收到这个含有恶意脚本的payload，不进行过滤和转义，就将payload拼接到HTML里，向浏览器返回含有恶意脚本的HTML,浏览器解析执行

#### 漏洞复现

1.打开开发者工具，依旧是触发弹窗跳转到下一关

![4-2](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase6/phase6-png/4-2.png)

2.尝试level3的方法

![4-3](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase6/phase6-png/4-3.png)

![4-4](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase6/phase6-png/4-4.png)

失败

3.查看源代码是否有实体转义

![4-5](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase6/phase6-png/4-5.png)

发现源代码没有实体转义，只是闭合不能再用单引号

4.用双引号闭合属性值

![4-6](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase6/phase6-png/4-6.png)

![4-7](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase6/phase6-png/4-7.png)


level4通关
