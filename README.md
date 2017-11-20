### docker 详解

### docker 存在的意义

* 使用dokcer加速本地开发和构建，开发人员可以构建、运行并分享Docker容器，容器可以在开发环境中构建，然后轻松地提交到测试环境中，并最终进入生产环境
* 能够让独立服务或应用程序在不同环境中，得到相同的运行结果。
* 用docker 创建隔离环境进行测试
* docker 可以让开发者先在本机上构建一个复杂的程序测试，而不是一开始就在生产环境进行测试

### docker概念

* Docker 的常用文档:https://docs.docker.com/
* Docker 镜像: 用户基于镜像来运行自己的容器，可以把镜像当做容器的『源代码』，镜像体积很小，易于分享、存储和更新
* Registry: Docker 用 Registry 保存用户构建的镜像，Registry 分为公共和私有两种:
  * Docker 公司运营的公共 Registry 叫做 Docker Hub，我们可以在上面注册账号，分享并保存自己的镜像。
  * 可以在 Docker Hub 保存自己的私有镜像或者架设自己私有的 Registry
* Docker 容器: 把应用程序或服务打包放进去，容器是基于镜像启动的，容器中可以运行一个或多个进程。
  * 镜像是 Docker 生命周期中的构建或打包阶段
  * 容器则是启动或执行阶段

### docker的使用命令

1 docker 命令介绍

```
docker --help

管理命令:
  container   管理容器
  image       管理镜像
  network     管理网络
命令：
  attach      介入到一个正在运行的容器
  build       根据 Dockerfile 构建一个镜像
  commit      根据容器的更改创建一个新的镜像
  cp          在本地文件系统与容器中复制 文件/文件夹
  create      创建一个新容器
  exec        在容器中执行一条命令
  images      列出镜像
  kill        杀死一个或多个正在运行的容器    
  logs        取得容器的日志
  pause       暂停一个或多个容器的所有进程
  ps          列出所有容器
  pull        拉取一个镜像或仓库到 registry
  push        推送一个镜像或仓库到 registry
  rename      重命名一个容器
  restart     重新启动一个或多个容器
  rm          删除一个或多个容器
  rmi         删除一个或多个镜像
  run         在一个新的容器中执行一条命令
  search      在 Docker Hub 中搜索镜像
  start       启动一个或多个已经停止运行的容器
  stats       显示一个容器的实时资源占用
  stop        停止一个或多个正在运行的容器
  tag         为镜像创建一个新的标签
  top         显示一个容器内的所有进程
  unpause     恢复一个或多个容器内所有被暂停的进程

```



### 查看docker信息（version、info）

1. 查看系统内核 
 
```
 uname -r
```
 
2. 启动docker 境像

```
systemctl start docker 
```

3.查看docker版本  

```
docker verison
```

4.显示docker系统的信息 

```
docker info
```

### 操作docker镜像

1.检索image 

```
docker search image-name
```

2.下载image

```
docker pull image-name
```

3.列出镜像列表

```
docker images 
```
4.删除一个或者多个镜像

```
docker rmi image-name
```

5.显示一个镜像的历史

```
docker history image-name  
```

6.

 