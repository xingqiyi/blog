##  容器

### docker run 命令来在容器内运行一个应用程序
```bash
docker run ubuntu:15.10 /bin/echo "Hello world"
```

### 通过docker的两个参数 -i -t，让docker运行的容器实现"对话"的能力
```bash
docker run -i -t ubuntu:15.10 /bin/bash

// -t:在新容器内指定一个伪终端或终端。
// -i:允许你对容器内的标准输入 (STDIN) 进行交互。
// exit 或者 Ctrl + D 退出

```


### 后台运行
```
docker run -d ubuntu:15.10 /bin/sh -c "while true; do echo hello world; sleep 1; done"


```

### 查看在运行的容器

docker ps

### 查看标准输出

docker logs containerID 或者containerName

### 停止容器

docker stop containerID 或者 containerName

### 移除不需要的容器

docker rm  containerID 或者 containerName



### 查看所有命令选项
docker

### 查看 某个命令帮助
docker command --help

### 运行一个 web 应用

docker run -d -p 5000:5000 training/webapp python app.py
//容器内部的 5000 端口映射到我们本地主机的 5000 端口上



## 镜像

### 列出镜像列表
docker images

### 获取一个新镜像
docker pull ubuntu:16.04