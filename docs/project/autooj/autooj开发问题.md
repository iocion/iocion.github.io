## autooj开发问题

```bash
# docker in docker
when docker run in http://localhost:8080
10.16.13.212:8006
```

```bash
# 用whoami命令查看用户名
username:ubuntu
ip:119.45.43.103
```

#### 1.mysql端口冲突问题

解决方法：使用mysql部署的时候，由于mysql的固定端口为3306，所有如果查看端口运行情况
```bash
netstat -tulpn # 如果3306端口被占用，则需要对3306端口进行映射
ss -tulpn # 更现代的用法   du -aux
# wrong 3306->3308  3306:3308 
# 如果向上面👆这样执行的话，一般默认mysql运行在3306端口，那还要修改my.conf的端口，所以一般不会这样做
<本地端口>:<容器/远程服务端口>
正确的是
3308:3306     3308->3306
使用navicat的3308端口进行访问主机3306端口运行的mysql，从而解决端口的冲突问题
docker run -d -p <宿主机端口>:<容器端口> --name <容器名称> <镜像名称>:<标签>
```

查看3306以及运行内容方法

```bash
root@VM-0-11-ubuntu:/home/ubuntu/AutoOJ# netstat -apn | grep 3306
tcp6       0      0 :::3306                 :::*                    LISTEN      1322021/mysqld
```

在运行过程中在这里需要修改端口

```python
def get_oj_db_connection():
    try:
        connection = pymysql.connect(
            host='119.45.43.103',
            port=3308, # 这里需要修改端口3306为3308
            user='db_user_name',
            password='db_passwd',
            db='db_name'
        )
        return connection
    except OperationalError as e:
        print("Error: ", e)
        return None
```

#### 2.项目迁移问题

```txt
需要注意一下几个位置的文件问题
compose.yml
main.js # npm run build
后端接口部分
utils.py 部分的数据库配置部分
```

![image-20250423120423961](C:\Users\han\AppData\Roaming\Typora\typora-user-images\image-20250423120423961.png)


<span id="busuanzi_container_page_pv">文章总观看量<span id="busuanzi_value_page_pv"></span>次</span>