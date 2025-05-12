### mysql 80版本忘记密码

```bash
mysqld --initialize-insecure //初始化数据库生成data文件
net stop mysql80 //关闭mysql服务器
mysqld --console --skip-grant-tables --shared-memory //跳过权限
mysql -u root -p //登录，输入密码直接回车,记得cmd必须使用管理员权限打开
```

​	本地localhost连接失败，使用上面这种方法，虽然能够重新连接sql，但是关闭 跳过权限的那一步之后，还是会有1045的报错，解决后还是出现2003的报错，最后放弃，选择重新安装mysql

发现应该是由于没有完全配置好，mysql内容就直接进行了连接，所以连接失败，通过这个视频完成了重装

<[手把手教你安装MySQL(最新版本安装)_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1jcabemEr7/?spm_id_from=333.1007.top_right_bar_window_history.content.click)>
