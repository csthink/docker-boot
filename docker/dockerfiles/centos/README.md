## 构建 CentOS 基础镜像

- 构建基础镜像
```
docker build --rm --compress -t csthink/centos7:base .
```

- 运行容器
```
docker run --name centos -d csthink/centos7:base
```

- 进入容器
```
docker exec -it centos bash
# 退出容器
exit
```

- 提交镜像
```
docker commit centos csthink/centos7:base
```

- 推送镜像到 registry
```
docker login
docker push csthink/centos7:base
```