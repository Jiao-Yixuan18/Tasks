# python爬虫

### 爬虫的流程

* 1.获取网页内容

  ![16](D:\Geek考核\Phase7\Phase7-png\16.png)

  基础知识：HTTP请求、Python Requests库

* 2.解析网页内容

  ![17](D:\Geek考核\Phase7\Phase7-png\17.png)

  基础知识：HTML、Python的Beautiful Soup、XPath库、正则表达式

* 3.储存数据或分析数据

  ![image-20260210231800471](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20260210231800471.png)

  基础知识：CSV、JSON等纯文本数据格式、MySQL数据库

储存方式可以是CSV、JSON之类的纯文本

如果数据量很大，可以把数据储存进MySQL之类的数据库

* 合理爬虫
  * 1.请求数量和频率不能太高，否则可能无异于DoS攻击（DoS攻击就是通过给服务器发送海量高频请求，让网站资源被耗尽，无法服务其他正常用户）
  * 2.可以通过查看网站的robot.txt文件，了解可爬取的网页路径范围，robot.txt会指明哪些网页允许被爬取，哪些不允许，有些还会专门列出针对搜索引擎爬虫的许可范围

### 基础知识

#### HTTP请求

超文本传输协议（Hypertext Transfer Protocol）是一种客户端和服务器之间的请求-响应协议

比如，浏览器就可以看做客户端，当我们在浏览器地址栏输入想访问的网址，按下回车后，浏览器就会向运行该网站的服务器发送一个请求 ，然后等待服务器返回给浏览器响应

![18](D:\Geek考核\Phase7\Phase7-png\18.png)

###### 请求方法

  * GET（获得数据）

    当我们进入一个网页，浏览器会发送GET请求，得到网页内容

  * POST（创建数据）

    当我们提交账号注册表单时，浏览器会发送POST请求，把用户名、密码等信息放到请求主体里，给到服务器

    爬虫程序基本上是在获取数据，因此爬虫时发送的请求大多数用GET方法

###### HTTP请求结构

  ![19](D:\Geek考核\Phase7\Phase7-png\19.png)

  * 请求行：

    * 方法类型：`POST`

    * 资源路径：`/user/info`

      指明了你要访问服务器的哪个资源

      ![20](D:\Geek考核\Phase7\Phase7-png\20.png)

      `?`后面是查询参数，可以传递给服务器额外的信息，不同信息之间用`&`分隔

      这里`start=75`,豆瓣的服务器就知道 ，返回给用户的页面内容，从排在第75的电影开始往后展示

    * 协议版本：`HTTP/1.1`

      有`HTTP/0.9`、`HTTP/1.0`、`HTTP/1.1`、`HTTP/2.0`等

  * 请求头：

    包含给服务器的信息

    * `Host`  主机域名，主机域名结合请求行里的资源路径，可以得到一个完整的网址

      ![21](D:\Geek考核\Phase7\Phase7-png\21.png)

    * `User-Agent`  用来告知服务器客户端的相关信息

      ![22](D:\Geek考核\Phase7\Phase7-png\22.png)

    * `Accept` 告诉服务器，客户端想接收的响应数据是什么类型

      ![23](D:\Geek考核\Phase7\Phase7-png\23.png)

			> `*/*`表示啥类型都行
		
	* 请求体：
	
	  放客户端传给服务器的其他任意数据，GET方法的请求体一般是空的

###### HTTP响应

![24](D:\Geek考核\Phase7\Phase7-png\24.png)

* 状态行

  * 协议版本  `HTTP/1.1`
  * 状态码  `200`

  ![25](D:\Geek考核\Phase7\Phase7-png\25.png)

  * 状态消息  `OK`

* 响应头

	包含一些告知客户端的信息

	* `Date`  生成响应的日期和时间
	* `Content-Type`  返回内容的类型及编码格式
	  * `text/html;charset=utf-8`  响应类型是HTML，编码是UTF-8
	  * `appplication/json;charset=utf-8`  响应类型是JSON，编码是UTF-8

* 响应体

  服务器想给客户端的数据内容

### 如何利用Python Requests发送请求

```python
#引用
import requests
#发送GET请求
#要输入完整的URL，包含http://
response = requests.get("https://www.baidu.com")
print(response)
#返回服务器给我们的响应
#响应实例包含的属性有 status_code 即HTTP状态码
print(response.status_code)
#请求成功时，响应体里才是我们想要的信息，所以需要根据状态码判断到底成没成功
#可以用Response类的OK属性，为True说明请求成功， 否则失败
if response.ok:
    print(response.text)
else:
    print("请求失败")

```

```
D:\Scripts\python.exe "D:\Tools\PyCharm\PyCharmProject\py_project01\第五章 - 爬虫\1..py" 
<Response [200]>
200
<!DOCTYPE html>
<!--STATUS OK--><html> <head><meta http-equiv=content-type content=text/html;charset=utf-8><meta http-equiv=X-UA-Compatible content=IE=Edge><meta content=always name=referrer><link rel=stylesheet type=text/css href=https://ss1.bdstatic.com/5eN1bjq8AAUYm2zgoY3K/r/www/cache/bdorz/baidu.min.css><title>ç¾åº¦ä¸ä¸ï¼ä½ å°±ç¥é</title></head> <body link=#0000cc> <div id=wrapper> <div id=head> <div class=head_wrapper> <div class=s_form> <div class=s_form_wrapper> <div id=lg> <img hidefocus=true src=//www.baidu.com/img/bd_logo1.png width=270 height=129> </div> <form id=form name=f action=//www.baidu.com/s class=fm> <input type=hidden name=bdorz_come value=1> <input type=hidden name=ie value=utf-8> <input type=hidden name=f value=8> <input type=hidden name=rsv_bp value=1> <input type=hidden name=rsv_idx value=1> <input type=hidden name=tn value=baidu><span class="bg s_ipt_wr"><input id=kw name=wd class=s_ipt value maxlength=255 autocomplete=off autofocus=autofocus></span><span class="bg s_btn_wr"><input type=submit id=su value=ç¾åº¦ä¸ä¸ class="bg s_btn" autofocus></span> </form> </div> </div> <div id=u1> <a href=http://news.baidu.com name=tj_trnews class=mnav>æ°é»</a> <a href=https://www.hao123.com name=tj_trhao123 class=mnav>hao123</a> <a href=http://map.baidu.com name=tj_trmap class=mnav>å°å¾</a> <a href=http://v.baidu.com name=tj_trvideo class=mnav>è§é¢</a> <a href=http://tieba.baidu.com name=tj_trtieba class=mnav>è´´å§</a> <noscript> <a href=http://www.baidu.com/bdorz/login.gif?login&amp;tpl=mn&amp;u=http%3A%2F%2Fwww.baidu.com%2f%3fbdorz_come%3d1 name=tj_login class=lb>ç»å½</a> </noscript> <script>document.write('<a href="http://www.baidu.com/bdorz/login.gif?login&tpl=mn&u='+ encodeURIComponent(window.location.href+ (window.location.search === "" ? "?" : "&")+ "bdorz_come=1")+ '" name="tj_login" class="lb">ç»å½</a>');
                </script> <a href=//www.baidu.com/more/ name=tj_briicon class=bri style="display: block;">æ´å¤äº§å</a> </div> </div> </div> <div id=ftCon> <div id=ftConw> <p id=lh> <a href=http://home.baidu.com>å³äºç¾åº¦</a> <a href=http://ir.baidu.com>About Baidu</a> </p> <p id=cp>&copy;2017&nbsp;Baidu&nbsp;<a href=http://www.baidu.com/duty/>ä½¿ç¨ç¾åº¦åå¿è¯»</a>&nbsp; <a href=http://jianyi.baidu.com/ class=cp-feedback>æè§åé¦</a>&nbsp;äº¬ICPè¯030173å·&nbsp; <img src=//www.baidu.com/img/gs.gif> </p> </div> </div> </div> </body> </html>


进程已结束，退出代码为 0
```

当用requests库的函数发送请求时，请求头里的信息会自动被生成，不需要手动传入。但如果想指定某些信息进行修改的话，可以额外传入一个叫headers的参数，它的数据类型是字典

例子：帮我们把爬虫程序伪装成正常浏览器

当我们正常使用浏览器时，浏览器会发送GET请求，并且请求头的User-Agent会自动带有浏览器类型及版本，还有电脑操作系统

![26](D:\Geek考核\Phase7\Phase7-png\26.png)

用代码发送请求，不会带有这些浏览器相关信息

![27](D:\Geek考核\Phase7\Phase7-png\27.png)

服务器可以通过这点判断进来的请求是来自浏览器还是程序

有些网站只想服务于真正的用户，就会根据User-Agent拒绝来自程序的请求，这时可以篡改User-Agent的属性，把代码发送的请求，伪装成浏览器请求

### 如何用Beautiful Soup解析HTML内容

Beautiful Soup把HTML内容解析为下图这样的树状结构

![28](D:\Geek考核\Phase7\Phase7-png\28.png)

```python
#导入依赖库
from bs4 import BeautifulSoup
import requests

# 1. 发送请求
response = requests.get("https://books.toscrape.com")

# 2. 从 response 对象中提取网页文本内容
html_content = response.text

# 3. 传给 BeautifulSoup 进行解析
#创建对象
soup = BeautifulSoup(html_content, features="html.parser")

# 打印测试
print(soup.p)
print(soup.img)

# 查找所有价格
#find_all方法，能根据标签、属性等，找出所有符合要求的元素
all_prices = soup.find_all(name="p", attrs={"class": "price_color"})
#遍历并打印价格
for price in all_prices:
    print(price.string)

#查找所有标题
#先找所有h3标签
all_titles = soup.find_all("h3")
#遍历h3标签里的a标签
for title in all_titles:
    all_links = title.find_all("a")
    #遍历h3标签里的a标签的内容
    for link in all_links:
        print(link.string)
```

```
D:\Scripts\python.exe "D:\Tools\PyCharm\PyCharmProject\py_project01\第五章 - 爬虫\3.Beautiful Soup解析HTML内容.py" 
<p class="star-rating Three">
<i class="icon-star"></i>
<i class="icon-star"></i>
<i class="icon-star"></i>
<i class="icon-star"></i>
<i class="icon-star"></i>
</p>
<img alt="A Light in the Attic" class="thumbnail" src="media/cache/2c/da/2cdad67c44b002e7ead0cc35693c0e8b.jpg"/>
Â£51.77
Â£53.74
Â£50.10
Â£47.82
Â£54.23
Â£22.65
Â£33.34
Â£17.93
Â£22.60
Â£52.15
Â£13.99
Â£20.66
Â£17.46
Â£52.29
Â£35.02
Â£57.25
Â£23.88
Â£37.59
Â£51.33
Â£45.17
A Light in the ...
Tipping the Velvet
Soumission
Sharp Objects
Sapiens: A Brief History ...
The Requiem Red
The Dirty Little Secrets ...
The Coming Woman: A ...
The Boys in the ...
The Black Maria
Starving Hearts (Triangular Trade ...
Shakespeare's Sonnets
Set Me Free
Scott Pilgrim's Precious Little ...
Rip it Up and ...
Our Band Could Be ...
Olio
Mesaerion: The Best Science ...
Libertarianism for Beginners
It's Only the Himalayas

进程已结束，退出代码为 0
```

