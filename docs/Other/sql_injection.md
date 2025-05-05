# sql injection(sql注入)

**原理：系统原本要进行的任务，由于更改sql语句的信息而更改内容，让原本进行的任务转移**

```bash
https://test-ipv6.com/ # 测试网络是否允许ipv6的网站
https://test-ipv4.com/
```

```
# For linux you can use some tools 
# 1.sqlmap -> sqlmapapi
# Use this tool try to use url to inject some SQL language words  
```

### 校园网连接

AUST_Faculty 教职工登录入口  (http://10.255.0.41)

教职工自动登录python脚本

```python
import requests
data = {"callback": "dr1003", "DDDDD": "2023302434@unicom", "upass": "852999##", "0MKKey": "123456"}
url = "http://10.255.0.41"
response = requests.post(url, data=data)
print(response.text)
```

AUST_Student 学生登录入口 (http://10.255.0.19)

<span id="busuanzi_container_page_pv">文章总观看量<span id="busuanzi_value_page_pv"></span>次</span>

