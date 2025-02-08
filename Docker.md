# 简单概念

镜像  
容器  
仓库  

# 安装 docker

同时安装 `docker` 和 ``

# 常用命令

`docker version` : 查看是否安装成功  
`docker search` : 在 Docker index 中搜索一个镜像  
`docker search nginx`  
`docker images` : 列出本地存储的所有镜像  
`docker images nginx` : 查看镜像 nginx  
`docker image ls` : 查看镜像  
`docker container ls`  
`docker stop` : 终止一个运行中的容器  
`docker ps` : 列出当前正在运行的容器  
`docker ps -a` : 列出所有容器（包括已停止的容器）  
`docker rm container_name` : 删除一个或多个容器  
`docker rmi my-image` : 删除一个或多个镜像  
`docker pull` : 从一个 Docker 的仓库服务器下拉一个镜像或仓库  
`docker pull geekhour/hello-docker`  
`docker inspect container_name` : 获取容器或镜像的详细信息  
`docker run hello-docker` : 运行  
`docker build -t hello-docker /root/helloDocker/` : 构建  
`docker search nginx` : 联网搜索 nginx 镜像  
`docker save` : 保存镜像为 tar 包  
`docker save nginx:latest -o docker.nginx.latest.tar.gz` : 打包到当前目录下的 `docker.nginx.latest.tar.gz` 文件  
`docker load`  
`docker load -i docker.nginx.latest.tar.gz`  

`docker run -d -p 80:80 nginx`  
`docker run -d -p 80:80 -p 443:443 nginx`  


# 部署 nginx

`docker search nginx`  
`docker pull nginx` : 获取Nginx 镜像  
`docker images nginx` : 查看 nginx 的信息  
`docker run --name nginx-test -p 80:80 -d nginx` : 启动 Nginx  

该命令的解释:  
`docker run` : 创建一个新容器并运行一个命令  
`--name` : 给容器起一个名字，这里为 `nginx-test`  
`-p` : 指定宿主机与容器内部端口的映射关系，`-p [宿主机端口]:[容器内部端口]`，我设置的是 `80:80`  
`-d` : 设置容器在在后台一直运行  
`nginx` : 最后面的 nginx 是镜像名称，也可以是镜像 ID，例如上面提到的 “0466”  

`docker ps`  

`docker exec -it b130a /bin/bash`  

解释:  
`docker exec` : 在运行的容器中执行命令  
`-it` : `-i` 和 `-t` 两个参数配合使用，开启一个交互模式的终端  
`b130a` : 名称为nginx-test容器ID  
`/bin/bash` : 指定了执行命令的shell  




## 参考
[使用Docker部署Nginx环境「这是我参与11月更文挑战的第12天，活动详情查看：2021最后一次更文挑战」 上一文 - 掘金](https://juejin.cn/post/7029348407609131015)  


# 参考

bilibili up主 [GeekHour](https://space.bilibili.com/102438649) 的 （[【【GeekHour】30分钟Docker入门教程】](https://www.bilibili.com/video/BV14s4y1i7Vf/?p=7&share_source=copy_web&vd_source=33653892d82fc9a3389865129a15ce62)）  
[Docker Hello World | 菜鸟教程](https://www.runoob.com/docker/docker-hello-world.html)  
