# XSS-labs level 2

#### 漏洞原理 

类型：反射型xss

原理：攻击者（我）通过闭合input标签，构造了一个包含恶意脚本的搜索表单，点击搜索时，服务器直接获取URL中`keyword`的参数值（`"><script>alert(2)</script>`）,没有对这些数据进行过滤和转义，直接拼接进`input`标签的`value`属性中，返回含有恶意脚本的HTML页面，浏览器解析并执行恶意脚本，从而使弹窗弹出

#### 漏洞复现

1.和level1思路一样，先查看源代码

![2-1](D:\Geek考核\Phase6\phase6-png\2-1.png)

![2-2](D:\Geek考核\Phase6\phase6-png\2-2.png)

出现了和level1类似的js代码，通关原理一致，都是要弹出这个“完成的不错”的弹框，实现跳转到level3

继续往下看源代码

2.页面中有一个form表单，可以输入

![2-3](D:\Geek考核\Phase6\phase6-png\2-3.png)

但是输入的内容是包含在value的值里，可以闭合input标签，实现执行js代码

3.在输入框里输入能闭合input标签的payload

![2-4](D:\Geek考核\Phase6\phase6-png\2-4.png)

![2-5](D:\Geek考核\Phase6\phase6-png\2-5.png)

level2通关