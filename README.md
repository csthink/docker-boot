# docker-boot 项目使用说明

## 使用前提
系统中已安装 git、docker、docker-compose

## 快速使用
1. 检查系统是否已安装必要的软件
```
git --version # 检查 git 是否安装
docker version # 检查 docker 是否安装
docker-compose version # 检查 docker-compose 是否安装
```
2. git 克隆代码到本地
```
git clone https://github.com/csthink/docker-boot.git
```

3. 创建配置文件
拷贝 env.example 并重命名.env 文件

4. 启动容器
```
# 第一次会去 Docker Registry 下载相关镜像，推荐配置 Docker 的国内镜像源，推荐阿里云，DaoCloud或网易
docker-compose up -d
```

5. 验证服务是否正常启动
浏览器直接访问 [localhost](http://localhost/),看到 Hello,docker-boot! 即表明环境搭建成功！

## 目录结构


## 相关命令
### 关闭容器并删除服务
```
docker-compose down
```

### 容器操作
```
# 进入容器(比如进入nginx容器)
docker exec -it docker—boot_nginx_1 sh
# 退出容器
exit
```

### nginx 相关操作
```
# 以下操作是在宿主机中直接执行，不需要进入容器，也可以通过进入容器后只执行相关 linux 部分的命令，不需要输入 ``docker exec -it docker-boot_nginx_1``

# 检查nginx服务是否启动
docker exec -it docker-boot_nginx_1 ps aux | grep nginx
# 检查nginx服务是否正常监听相关端口
docker exec -it docker-boot_nginx_1 netstat -antup | grep 80
# 检查 nginx 配置文件是否合法
docker exec -it docker-boot_nginx_1 nginx -t
# 重启 nginx 服务
docker exec -it docker-boot_nginx_1 nginx -s reload
```

### MySQL 相关操作
*** 注意 ./docker/data/mysql 必须是一个空目录，否则可能会导致容器一直在重启 ***


### 日志操作
```
docker logs --tail 5 --follow --timestamps docker-boot_nginx_1
```