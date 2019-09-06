## 构建 Alpine Linux 基础镜像

- 构建基础镜像
```
docker build --rm --compress -t csthink/alpine:base .
```

- 运行容器
```
docker run -it --name alpine -d csthink/alpine:base sh
```

- 进入容器
```
docker exec -it alpine sh
# 退出容器
exit
```

- 提交镜像
```
docker commit alpine csthink/alpine:base
```

- 推送镜像到 registry
```
docker login
docker push csthink/alpine:base
```