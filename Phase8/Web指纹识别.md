# Web指纹识别

### Web指纹基本识别方法

###### 在线网站识别

[云悉指纹识别](https://www.yunsee.cn/)

[Whatweb](https://whatweb.net/)

###### 工具识别

[Ehole](https://github.com/EdgeSecurityTeam/EHole)

[TiderFinger](https://github.com/TideSec/TideFinger)

[WhatWeb](https://github.com/urbanadventurer/WhatWeb)(kali集成该工具)

[Finger](https://github.com/EASY233/Finger)

###### 手动识别

![25](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase8/Phase8-png/25.png)

###### Wappalyzer插件识别

[Wappalyzer](https://www.wappalyzer.com/)

### Web指纹识别工具

###### whatweb

* 常规扫描

![7](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase8/Phase8-png/7.png)

扫描后可得到指纹：

`200 OK`:HTTP状态码，表示服务器成功响应了请求

`Cookies`

`Country`:服务器IP属地

`HTML5`:HTML5标准

`HTTPServer`:服务器

`IP`:百度首页解析到的其中一个公网 IP 地址(当`whatweb` 扫描 `https://www.baidu.com` 时，工具会先把域名 `www.baidu.com` 解析成对应的 IP 地址，这里解析到的是 153.3.238.127；百度这样的大型网站会有多个IP地址，所以每次解析可能会得到不同的IP地址)

`OpenSearch`:一个分布式搜索与分析引擎

`Script`:页面包含JavaScript脚本

`Title`:首页标题

`UncommonHeaders`:不常见的HTTP头

`X-UA-Compatible`:兼容老旧的IE浏览器

`X-XSS-Protection`:XSS防护功能，1表示启用，0表示关闭，`mode=block`表示如果浏览器检测到XSS攻击，就直接阻止整个页面的加载

* 批量扫描

![8](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase8/Phase8-png/8.png)

![9](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase8/Phase8-png/9.png)

`Django`:

![33](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase8/Phase8-png/33.png)

`Email`:各种邮箱地址

`JQuery`:![34](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase8/Phase8-png/34.png)

`Shopify`

`Struct-Transport-Security`:是HSTS的标头.HTST是HTTP严格传输安全

[HSTS](https://www.freebuf.com/articles/network/413334.html)

* 详细回显扫描

![10](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase8/Phase8-png/10.png)

`whatweb report for http://www.csdn.net`：扫描的目标地址是http://www.csdn.net

`Status:301 Moved Permanently`:HTTP状态码“永久重定向”

`Ttile:301 Moved Permanently`:重定向页面的标题

`IP:123.129.227.51`:www.csdn.net这个域名解析到服务网公网ip地址

`Country:CHINA,CN`:服务器属于中国

![11](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase8/Phase8-png/11.png)

![12](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase8/Phase8-png/12.png)

![13](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase8/Phase8-png/13.png)





* 强度扫描等级控制

![14](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase8/Phase8-png/14.png)

![15](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase8/Phase8-png/15.png)

* 扫描内网主机

在此之前，需要先知道内网网段

如何得知内网网段？

![16](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase8/Phase8-png/16.png)

命令：whatweb --no-errors -t 255 内网网段

![17](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase8/Phase8-png/17.png)

* 查看whatweb插件信息

![32](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase8/Phase8-png/32.png)



###### Wappalyzer

在google浏览器安装wappalyzer扩展

* 访问目标网站，打开wappalyzer扩展，扫描完成后会显示网站的技术指纹

这里以百度为例

![26](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase8/Phase8-png/26.png)

* 点击任意一个技术名，可以跳转到技术介绍页面

![27](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase8/Phase8-png/27.png)

![28](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase8/Phase8-png/28.png)

![29](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase8/Phase8-png/29.png)


![30](https://github.com/Jiao-Yixuan18/Tasks/blob/main/Phase8/Phase8-png/30.png)
