# XSS-labs level 3

#### 漏洞原理

类型：反射型xss

原理：攻击者（我）在搜索框内输入恶意脚本，企图通过闭合input标签来实现攻击，但是当服务器获取我输入的恶意脚本时，对“、<、>这些特殊符号进行HTML实体编码，导致我的恶意脚本失效，被转成普通文本，无法闭合标签，这是服务器的一种防御手段。但是服务器未对单引号进行转义，所以可以利用单引号闭合input标签，添加一个onclick点击事件来执行攻击。服务器返回含有恶意脚本的HTML页面，浏览器解析并执行

1.先打开开发者工具

![3-1](D:\Geek考核\Phase6\phase6-png\3-1.png)

![3-2](D:\Geek考核\Phase6\phase6-png\3-2.png)

找level4.php，通关的原理仍是要触发弹窗

2.去看看form表单那块的代码

![3-3](D:\Geek考核\Phase6\phase6-png\3-3.png)

页面能输入的内容到了html文件里仍是单标签的value属性值，所以尝试闭合标签的方法

![3-4](D:\Geek考核\Phase6\phase6-png\3-4.png)

失败了

![3-5](D:\Geek考核\Phase6\phase6-png\3-5.png)

3.查看源代码

![3-6](D:\Geek考核\Phase6\phase6-png\3-6.png)

发现源代码里我输入的js代码被实体编码了

4.试试input的onclick属性绕过html实体转义

![](D:\Geek考核\Phase6\phase6-png\3-7.png)



又失败了，打开源代码

![3-8](D:\Geek考核\Phase6\phase6-png\3-8.png)

双引号被实体转义了，用单引号

5.单引号

![3-9](D:\Geek考核\Phase6\phase6-png\3-9.png)

又失败了，打开原码观察，可能是input标签最后` ''`使语法不对导致的



![3-10](D:\Geek考核\Phase6\phase6-png\3-10.png)

6.补充payload使语法正确

![3-11](D:\Geek考核\Phase6\phase6-png\3-11.png)

点击输入框，完成onclick点击事件

![3-12](D:\Geek考核\Phase6\phase6-png\3-12.png)

level3通关

#### XSS防御手段

###### 1.对输入和URL参数进行过滤

检查用户输入的数据中是否包含一些特殊字符，如<、>、'、"等，发现存在这些特殊字符过滤或者编码

|特殊字符|实体编码|
|:------------:|:-----------:|
|&|`&amp;`|
|<|`&lt`|
|>|`&gt`|
|''|`&quot`|
| '    | `&#x27` |
| /    | `&#x2F` |

###### 2.HTML实体转义

字符串js编码转换成实体html编码的方法

###### 3.对输出内容进行编码

在变量输出到HTML页面时，可以使用编码或转义的方式来防御XSS攻击

#### HTML实体转义如何绕过

[XSS 常用语句以及绕过思路]([XSS | XSS 常用语句以及绕过思路_xss语句-CSDN博客](https://blog.csdn.net/m0_73360524/article/details/142644247))
