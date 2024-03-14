## Docker

### 拉取镜像

```bash
$ docker pull ubuntu:latest
```

### 运行镜像

```bash
docker run <image_name>
```

### 查看容器

```bash
#运行中的容器
docker ps
docker container ls

#存在的所有容器
docker ps -a
```

### 映射主机端口

```bash
docker run -p 8080:80 nginx
```

### 挂载volume

```bash
docker run -v /local/path:/mounted/volume/path -it ubuntu /bin/bash
```

### 交互容器

```bash
docker run -it ubuntu /bin/bash
```

### 本地文件上传到容器内

```bash
docker cp /dir/a.txt d3a46083eadf:/usr/src/a.txt
```

