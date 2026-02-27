# Web指纹识别小工具

```python
import requests
import hashlib

#资产列表 = [name, urls, keyword, headers, headers_value, md5_value]
assets = [
    #FOFA语句：app="用友-NC-Cloud"
    ("用友-NC-Cloud",
     [
         "http://123.7.18.41:8686/nccloud/resources/uap/rbac/login/main/index.html",
         "http://58.58.247.134:2105/nccloud/resources/uap/rbac/login/main/index.html",
         "http://159.138.83.66:8081/nccloud/resources/uap/rbac/login/main/index.html",
         "http://61.178.89.163:9003/nccloud/resources/uap/rbac/login/main/index.html",
         "http://183.6.55.151:8088/nccloud/resources/uap/rbac/login/main/index.html"
     ],
     "uap", "Server", "server", "10740C05D133C5508488F6CC90681BF9"),
    #FOFA语句：app="GitLab" && country="CN"
    ("GitLab",
    [
        "http://47.237.0.83",
        "http://112.86.12.16:8090",
        "http://47.104.250.248:8084",
        "http://106.15.238.70",
        "http://106.13.230.232:8099"
    ],
     "GitLab", "Server", "nginx", ""),
    #FOFA语句：app="爱快流控路由" && country="CN"
    ("爱快流控路由",
     [
         "http://121.28.73.254:8081",
         "http://221.205.207.116:8082",
         "http://116.21.246.121:8081",
         "http://175.0.106.112:8889",
         "http://120.224.121.7:8989"
     ],
     "爱快流控路由", "Server", "FastCGI", "c1af9e622eae1dcb95ef44f996bf6228"),
]

for name, urls, keyword, headers, headers_value, md5_value in assets:
    print(f"\n识别资产：{name}")
    # 遍历所有网站
    for url in urls:
        print(f"\n检测网址：{url}")
        #使用异常处理语句
        try:
            #发送请求
            res = requests.get(url, timeout=5, verify=False)
            #识别关键词
            if keyword in res.text:
                print("string识别成功")
            else:
                print("string识别失败")
            #识别响应头
            if res.headers.get(headers) == headers_value:
                print("headers识别成功")
            else:
                print("headers识别失败")
            #识别网站ico的md5
            icon_res = requests.get(f"{url}/favicon.ico", timeout=5, verify=False)
            calc_md5 = hashlib.md5(icon_res.content).hexdigest()
            if calc_md5 == md5_value:
                print("MD5识别成功")
            else:
                print("MD5识别失败")
        except:
            print("请求异常")
```
运行

```
D:\Scripts\python.exe D:\Tools\PyCharm\PyCharmProject\py_project01\第六章-实践\指纹小工具.py 

识别资产：用友-NC-Cloud

检测网址：http://123.7.18.41:8686/nccloud/resources/uap/rbac/login/main/index.html
string识别成功
headers识别成功
MD5识别失败

检测网址：http://58.58.247.134:2105/nccloud/resources/uap/rbac/login/main/index.html
string识别成功
headers识别成功
MD5识别失败

检测网址：http://159.138.83.66:8081/nccloud/resources/uap/rbac/login/main/index.html
string识别成功
headers识别成功
MD5识别失败

检测网址：http://61.178.89.163:9003/nccloud/resources/uap/rbac/login/main/index.html
string识别成功
headers识别成功
MD5识别失败

检测网址：http://183.6.55.151:8088/nccloud/resources/uap/rbac/login/main/index.html
string识别成功
headers识别成功
MD5识别失败

识别资产：GitLab

检测网址：http://47.237.0.83
string识别成功
headers识别成功
MD5识别失败

检测网址：http://112.86.12.16:8090
string识别失败
headers识别失败
MD5识别失败

检测网址：http://47.104.250.248:8084
string识别成功
headers识别成功
MD5识别失败

检测网址：http://106.15.238.70
string识别成功
headers识别成功
MD5识别失败

检测网址：http://106.13.230.232:8099
string识别成功
headers识别成功
MD5识别失败

识别资产：爱快流控路由

检测网址：http://121.28.73.254:8081
string识别成功
headers识别成功
MD5识别成功

检测网址：http://221.205.207.116:8082
string识别成功
headers识别成功
MD5识别成功

检测网址：http://116.21.246.121:8081
string识别成功
headers识别成功
MD5识别成功

检测网址：http://175.0.106.112:8889
string识别成功
headers识别成功
MD5识别成功

检测网址：http://120.224.121.7:8989
string识别成功
headers识别成功
MD5识别成功

进程已结束，退出代码为 0

```
