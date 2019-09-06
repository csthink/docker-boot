# docker-boot 项目使用说明

## 使用前提
系统中已安装 ``git``、``docker``、``docker-compose``

## 快速使用
1. 检查系统是否已安装必要的软件
```bash
git --version # 检查 git 是否安装
docker version # 检查 docker 是否安装
docker-compose version # 检查 docker-compose 是否安装
```
2. git 克隆代码到本地
```bash
git clone https://github.com/csthink/docker-boot.git
```

3. 创建配置文件
拷贝 env.example 并重命名.env 文件

4. 启动容器
*** docker 第一次会去 Docker Registry 下载相关镜像,国内网络环境拉取镜像比较耗时，可以修改 Docker 的镜像源，推荐使用阿里云，DaoCloud或网易 ***
```bash
docker-compose up -d
```

5. 验证服务是否正常启动
浏览器直接访问 [localhost](http://localhost/),看到 Hello,docker-boot! 即表明环境搭建成功！


## 有用的提示

### 关闭容器并删除服务
```bash
docker-compose down
```

### 容器操作
```
# 进入容器(比如进入nginx容器)
docker exec -it docker—boot_nginx_1 sh
# 退出容器
exit
```

### nginx
- nginx 的访问日志文件: ***/docker/log/nginx/access.log***
- nginx 的错误日志文件: ***/docker/log/nginx/error.log***
- nginx 的主配置文件: ***/docker/config/nginx/nginx.conf***
- nginx 的虚拟主机配置文件目录: ***/docker/config/nginx/conf.d***
- nginx 的HTTPS 证书目录: ***/docker/config/nginx/certs***
- 相关配置请修改 .env 文件和 nginx 的配置文件
  
```bash
# 以下操作是在宿主机中直接执行，不需要进入容器，也可以进入容器后只执行相关 linux 部分的命令，不需要输入 docker exec -it nginx

# 检查nginx服务是否启动
docker exec -it nginx ps aux | grep nginx
# 检查nginx服务是否正常监听相关端口
docker exec -it nginx_1 netstat -antup | grep 80
# 检查 nginx 配置文件是否合法
docker exec -it nginx_1 nginx -t
# 重启 nginx 服务
docker exec -it nginx nginx -s reload
```

### Mysql 
- mysql 的数据目录: ***/docker/data/mysql***
- mysql 的慢查询日志: ***/docker/log/mysql/mysql.slow.log***
- mysql 的配置文件: ***/docker/config/mysql/my.cnf***
- mysql 初始连接信息(相关配置请修改 .env 文件和 mysql 的配置文件)

```bash
HOST: 127.0.0.1
PORT: 3306
USER: root
PWD: 111111
```

### redis
- redis 的数据目录: ***/docker/data/redis***
- redis 的日志文件: ***/docker/data/redis/redis.log***
- redis 的配置文件: ***/docker/config/redis/redis.conf***
- redis 初始连接信息(相关配置请修改 .env 文件和 redis 的配置文件)

```
HOST: 127.0.0.1
PORT: 6379
PWD: 111111
```

### docker 日志操作
```bash
docker logs --tail 5 --follow --timestamps redis
```

## 相关资源
- [redis 配置文件](http://download.redis.io/redis-stable/redis.conf) 
