## docker部署flask项目

```
常用的docker daemon镜像守护进程
常用镜像源
https://docker.1panel.live
https://docker.1ms.run
```
```bash
docker images
docker ps
```

### 使用Dockerfile和docker compose来进行docker的部署

**编写dockerfile以及compose.yml**

```python
# 项目框架
# backend 
# frontend
# compose.yml
```

### 整体项目工程构建

```bash
1.独立build
docker build -t "container_name" .
2.使用docker compose 进行build
docker-compose build
```

**前端使用npm或者yarn工具构建前端项目**

```python
npm run build
# 或者使用 yarn build 
```

```bash
# use
# before push ,login first
# so run > docker login
docker login # 这一步总是打开docker desktop，其他的认证方法我都没有测试 
# 
#login sucessed
docker push image_name
```



### 部署远端服务器

```bash
docker pull image_name:tag
```

或者使用docker-compose pull

```bash
sudo docker stop $(docker ps -q) #关闭所有正在运行中的容器
sudo docker-compose pull
docker compose up -d # 运行docker compose 并在后台运行
```

### 单独或者统一配置数据库

```bash
docker pull mysql
```

连接mysql数据库
run.sql进行数据库的构建，使用10.16.13.212进行与服务器的连接，注意默认端口号是:3306

```bash
10.16.13.212:3306     # 可以使用navicat工具 run.sql
```

```bash
docker volume ls

```

### docker运行意外退出

```bash
docker ps -a # 查看包括退出的docker container
ubuntu@VM-0-11-ubuntu:~$ docker run -it iocion/test:v1.0 bash
ubuntu@VM-0-11-ubuntu:~$ docker exec -it iocion/test:v1.0 bash # 进入容器内部进行操作
```

<span id="busuanzi_container_page_pv">文章总观看量<span id="busuanzi_value_page_pv"></span>次</span>

