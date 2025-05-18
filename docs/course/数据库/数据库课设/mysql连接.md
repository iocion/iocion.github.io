### 1.mysql 80版本忘记密码

```bash
mysqld --initialize-insecure //初始化数据库生成data文件
net stop mysql80 //关闭mysql服务器
mysqld --console --skip-grant-tables --shared-memory //跳过权限
mysql -u root -p //登录，输入密码直接回车,记得cmd必须使用管理员权限打开
```

​	本地localhost连接失败，使用上面这种方法，虽然能够重新连接sql，但是关闭 跳过权限的那一步之后，还是会有1045的报错，解决后还是出现2003的报错，最后放弃，选择重新安装mysql

发现应该是由于没有完全配置好，mysql内容就直接进行了连接，所以连接失败，通过这个视频完成了重装

<[手把手教你安装MySQL(最新版本安装)_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1jcabemEr7/?spm_id_from=333.1007.top_right_bar_window_history.content.click)>

### 2.docker启动连接mysql

```bash
在远端server端：
docker pull mysql:lastest # 拉取最新的mysql镜像
---------------------------------------------------
在本地local端： 
# 打开dockerhub
docker login
docker build -t iocion/my_mysql_project .
docker push iocion/my_mysql_project
---------------------------------------------------
server端：
docker volume create medicine_mysql # 创建一个volume体积卷
docker run -d --name=mysql-server -p 3310:3306 -v medicine_mysql:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=123456 mysql # 运行docker mysql
# 连接名host=mysql-server
# -p port 端口映射
# -v 体积卷位置
# -e 密码以及数据库类型
********************************
docker run -d --name=mysql-server -p 3310:3306 -v medicine_mysql:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=123456 -e TZ=Asia/Shanghai mysql 
#指定时区为上海,经过尝试发现时区无法更改，在数据库执行
SELECT @@global.time_zone;
SELECT NOW();
# 返回system，于是选择直接在ubuntu内部进行系统更改时区
sudo timedatectl set-timezone Asia/Shanghai
```

```bash
ubuntu@VM-0-11-ubuntu:~$ timedatectl status
               Local time: Sat 2025-05-17 12:59:22 CST
           Universal time: Sat 2025-05-17 04:59:22 UTC
                 RTC time: Sat 2025-05-17 04:59:22
                Time zone: Asia/Shanghai (CST, +0800)
System clock synchronized: yes
              NTP service: active
          RTC in local TZ: no
通过检查 timedatectl status 发现系统时区更新成功，于是解决问题
```

### 3.使用python的sqlalchemy连接local或者远端mysql

```python
app = Flask(__name__)
app.config['SQLALCHEMY_DATABASE_URI'] = 'mysql+pymysql://root:123456@119.45.43.103:3310/test1'  # 替换为你的 MySQL 连接信息
app.config['SQLALCHEMY_TRACK_MODIFICATIONS'] = False
# app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///market.db'
app.config['SECRET_KEY'] ='db92354e927ef71db526f676'
db = SQLAlchemy(app)
```

关键部分：四部分都缺一不可，都可能造成无法连接数据库

```python
app.config['SQLALCHEMY_DATABASE_URI'] = 'mysql+pymysql://root:123456@119.45.43.103:3310/test1'  # 替换为你的 MySQL 连接信息
mysql+pymysql->数据库类型
username->用户名称
@port ->端口
db_name->数据库名称
```

### 4.使用sqlalchemy的一些错误和学习过程

```python
item_count = Item.query.count()
filter_by # 不支持多参数<= > 的比较
filter # 支持直接比较，使用 类 + 属性名称 进行查询 可用like,not like等方式
item = Item.query.filter_by(id=item_id).first()
item = Item.query.filter(Item.name.like(f%'{item_name}'%)).first()
```







