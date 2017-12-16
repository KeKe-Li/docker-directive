<p align="center">
<img width="130" align="center" src="assets/images/docker.png" />
</p>
<h1 align="center">docker命令详解</h1>


### 此次操作都是在unbantu17.01下进行,docker版本是17.10.0-ce,docker-compose是1.17.1.

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

```shell
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

2.更详细的功能参数配置


| 参数 | 解释 |
| --------- | --------- |
|--api-enable-cors=false|开放远程API调用的 CORS 头信息。这个接口开关对想进行二次开发的上层应用提供了支持.|
|-b, --bridge=""|挂载已经存在的网桥设备到 Docker 容器里。注意，使用 none 可以停用容器里的网络.|
|--bip=""|使用 CIDR 地址来设定网络桥的 IP。注意，此参数和 -b 不能一起使用.|
|-D, --debug=false|开启Debug模式。例如：docker -d -D|
|-d, --daemon=false|开启Daemon模式.|
|--dns=[]|强制容器使用DNS服务器.例如： docker -d --dns 8.8.8.8|
|--dns-search=[]|强制容器使用指定的DNS搜索域名.例如： docker -d --dns-search example.com|
|-e, --exec-driver="native"|强制容器使用指定的运行时驱动.例如：docker -d -e lxc|
|-G, --group="docker"|在后台运行模式下，赋予指定的Group到相应的unix socket上。注意，当此参数 --group 赋予空字符串时，将去除组信息。|
|-g, --graph="/var/lib/docker"|配置Docker运行时根目录|
|-H, --host=[]|在后台模式下指定socket绑定，可以绑定一个或多个 tcp://host:port, unix:///path/to/socket, fd://* 或 fd://socketfd。例如：$ docker -H tcp://0.0.0.0:2375 ps 或者 $ export DOCKER_HOST="tcp://0.0.0.0:2375" $ docker ps|
|--icc=true |启用内联容器的通信.|
|--ip="0.0.0.0"|容器绑定IP时使用的默认IP地址.|
|--ip-forward=true|启动容器的 net.ipv4.ip_forward.|
|--iptables=true|启动Docker容器自定义的iptable规则.|
|--mtu=0|设置容器网络的MTU值，如果没有这个参数，选用默认 route MTU，如果没有默认route，就设置成常量值 1500.|
|-p, --pidfile="/var/run/docker.pid"|后台进程PID文件路径.|
|-r, --restart=true|重启之前运行中的容器.|
|-s, --storage-driver=""|强制容器运行时使用指定的存储驱动，例如,指定使用devicemapper, 可以这样：docker -d -s devicemapper|
|--selinux-enabled=false|启用selinux支持|
|--storage-opt=[]|配置存储驱动的参数|
|--tls=false|启动TLS认证开关|
|--tlscacert="/Users/dxiao/.docker/ca.pem"|通过CA认证过的的certificate文件路径|
|--tlscert="/Users/dxiao/.docker/cert.pem"|TLS的certificate文件路径|
|--tlskey="/Users/dxiao/.docker/key.pem"|TLS的key文件路径|
|--tlsverify=false|使用TLS并做后台进程与客户端通讯的验证|
|-v, --version=false|显示版本信息|

*注意：其中带有[] 的启动参数可以指定多次，例如
```shell
docker run -a stdin -a stdout -a stderr -i -t ubuntu /bin/bash

```


### docker基本


1. 查看系统内核 
 
```shell
 uname -r
```
 
2. 启动docker 境像

```shell
systemctl start docker 
```

3.查看docker版本  

```shell
docker verison
```

4.显示docker系统的信息 

```shell
docker info
```

### 操作docker镜像

1.检索image 

```shell
docker search image-name
```

2.下载image

```shell
docker pull image-name
```

3.列出镜像列表

```shell
docker images 
```
4.删除一个或者多个镜像

```shell
docker rmi image-name
```

5.显示一个镜像的历史

```shell
docker history image-name  
```

6.通过容器创建镜像

*从已经创建的容器中更新镜像，并且提交这个镜像
*使用 Dockerfile 指令来创建一个新的镜像
下面通过已存在的容器创建一个新的镜像。

```shell
docker commit -m="First Image" -a="keke" 7a15f99695c0 keke/unbantu:17.10.0

上面命令参数说明：
* -m 提交的描述信息
* -a 指定镜像作者
* 7a15f99695c0 记住这个是容器id，不是镜像id
* keke/unbantu:17.10.0 创建的目标镜像名

```
1. 在[Docker](https://www.docker.com/) 注册账户，发布的镜像都在[这个页面里](https://cloud.docker.com/repository/list)展示
2. 将上面做的镜像`unbantu`，起个新的名字`unbantu-test`

```shell
docker tag keke/unbantu:17.10.0 keke/unbantu-test:lastest
```
3. 登录docker

```shell
docker login
```
4.上传unbantu镜像
```shell
docker push keke/unbantu-test:lastest
```

### 启动容器
docker容器可以理解为在沙盒中运行的进程。这个沙盒包含了该进程运行所必须的资源，包括文件系统、系统类库、shell 环境等等。但这个沙盒默认是不会运行任何程序的。你需要在沙盒中运行一个进程来启动某一个容器。这个进程是该容器的唯一进程，所以当该进程结束的时候，容器也会完全的停止。

1.在容器中安装新的程序  
```shell
docker run image-name apt-get install -y -name
``` 
2.在容器中运行"echo"命令，输出"hello word"
```shell
docker run image-name echo "hello word" 
```
3.交互式进入容器中 
```shell
docker run -i -t image_name /bin/bash  
```
注意:在执行apt-get 命令的时候，要带上-y参数。如果不指定-y参数的话，apt-get命令会进入交互模式，需要用户输入命令来进行确认，但在docker环境中是无法响应这种交互的。apt-get 命令执行完毕之后，容器就会停止，但对容器的改动不会丢失.


### 查看容器

1.列出当前所有正在运行的container
```shell
docker ps
```

2.列出所有的container
```shell
docker ps -a  
```

3.列出最近一次启动的container 
```shell
docker ps -l  
```

4.保存对容器的修改
当你对某一个容器做了修改之后（通过在容器中运行某一个命令），可以把对容器的修改保存下来，这样下次可以从保存后的最新状态运行该容器。

1.保存对容器的修改; -a, --author="" Author; -m, --message="" Commit message  
```shell
docker commit ID new-image-name 
```

5.操作容器

1.删除所有容器 
```shell
docker rm `docker ps -a -q`
```

2.删除单个容器; -f, --force=false; -l, --link=false Remove the specified link and not the underlying container; -v, --volumes=false Remove the volumes associated to the container  
```shell
docker rm Name/ID 
```

3.停止、启动、杀死一个容器
```shell
docker stop Name/ID  
docker start Name/ID  
docker kill Name/ID 
```

4.从一个容器中取日志; -f, --follow=false Follow log output; -t, --timestamps=false Show timestamps 
```shell
docker logs Name/ID  
```

5.列出一个容器里面被改变的文件或者目录，list列表会显示出三种事件，A 增加的，D 删除的，C 被改变的
```shell
docker diff Name/ID
```

6.显示一个运行的容器里面的进程信息 
```shell
docker top Name/ID  
```

7.从容器里面拷贝文件/目录到本地一个路径 

```shell
docker cp Name:/container-path to-path  
docker cp ID:/container-path to-path 
```

8.重启一个正在运行的容器; -t, --time=10 Number of seconds to try to stop for before killing the container, Default=10
```shell
docker restart Name/ID
```

9.附加到一个运行的容器上面; --no-stdin=false Do not attach stdin; --sig-proxy=true Proxify all received signal to the process  
```shell
docker attach ID #重新启动并运行一个交互式会话shell
```
注意：使用这个命令可以挂载正在后台运行的容器，在开发应用的过程中运用这个命令可以随时观察容器內进程的运行状况.

### 保存和加载镜像
当需要把一台机器上的镜像迁移到另一台机器的时候，需要保存镜像与加载镜像。

1.保存镜像到一个tar包; -o, --output="" Write to an file  
```shell
docker save image-name -o file-path 
```

2.加载一个tar包格式的镜像; -i, --input="" Read from a tar archive file
```shell
docker load -i file-path 
```

3.从机器A拷贝到机器B
```shell
docker save image-name > /home/keke/main.tar

*使用scp将main.tar拷到机器A上:

docker load < /home/keke/main.tar

```

### 登录

1.登陆registry server; -e, --email="" Email; -p, --password="" Password; -u, --username="" Username

```shell
docker login
```

### 发布docker镜像

```shell
docker push new-image-name 
```



### 构建镜像(Dockerfile + docker build)

1. Dockerfile文件使用

docker build命令会根据Dockerfile文件及上下文构建新Docker镜像。构建上下文是指Dockerfile所在的本地路径或一个URL（Git仓库地址）。构建上下文环境会被递归处理，所以，构建所指定的路径还包括了子目录，而URL还包括了其中指定的子模块。

* 构建镜像

将当前目录做为构建上下文时，可以像下面这样使用docker build命令构建镜像：

```shell
keke@keke:~/Downloads/hello-system$ sudo docker build .
Sending build context to Docker daemon  70.14kB

```

说明：构建会在Docker后台守护进程（daemon）中执行，而不是CLI中。构建前，构建进程会将全部内容（递归）发送到守护进程。大多情况下，应该将一个空目录作为构建上下文环境，并将Dockerfile文件放在该目录下。

在构建上下文中使用的Dockerfile文件，是一个构建指令文件。为了提高构建性能，可以通过.dockerignore文件排除上下文目录下，不需要的文件和目录。

Dockerfile一般位于构建上下文的根目录下，也可以通过-f指定该文件的位置：

```shell
keke@keke:~$ sudo docker build -f /home/keke/Downloads/hello-system/Dockerfile .

```
构建时,还可以通过-t参数指定构建成后,镜像的仓库,标签等：

* 镜像标签

```shell

```


```dockerfile
FROM ...

RUN ...

# 指定容器内的程序将会使用容器的指定端口
# 配合 docker run -p
EXPOSE ...

```

* RUN: 指定镜像被构建时要运行的命令
* CMD: 指定容器被启动时要运行的命令
* ENTRYPOINT: 同 CMD ，但不会被 docker run -t 覆盖
* WORKDIR: CMD/ENTRYPOINT 会在这个目录下执行
* VOLUME
* ADD
* COPY

```shell
docker history images-name
```

1.从新镜像启动容器
```shell
docker run -d -p 4000:80 --name [name] #可以在 Dokcer 宿主机上指定一个具体的端口映射到容器的80端口上
```

### 守护容器

```shell
docker run -d container-name #创建守护容器
docker top container-name #查看容器内进程
docker exec container-name touch a.txt #在容器内部运行进程
docker stop container-name #停止容器

```  

### 关于docker
觉得此文章不错可以给我star！
如果还有遇到问题可以加我微信Sen0676备注下来自github,进go实战群详细交流！ 

### 参考资料

### 官方英文资源

* Docker官网：http://www.docker.com
* Docker windows入门：https://docs.docker.com/windows/
* Docker Linux 入门：https://docs.docker.com/linux/
* Docker mac 入门：https://docs.docker.com/mac/
* Docker 用户指引：https://docs.docker.com/engine/userguide/
* Docker 官方博客：http://blog.docker.com/
* Docker Hub: https://hub.docker.com/
* Docker开源： https://www.docker.com/open-source

### 中文资源

* Docker中文网站：http://www.docker.org.cn
* Docker中文文档：http://www.dockerinfo.net/document
* Docker安装手册：http://www.docker.org.cn/book/install.html
* 一小时Docker教程 ：https://blog.csphere.cn/archives/22
* Docker中文指南：http://www.widuu.com/chinese_docker/index.html

### 其它资源

* [Docker 快速手册！](https://github.com/eon01/DockerCheatSheet)
* [Docker 教程](http://www.runoob.com/docker/docker-tutorial.html)
* [MySQL Docker 单一机器上如何配置自动备份](http://blog.csdn.net/zhangchao19890805/article/details/52756865)
* [Docker — 从入门到实践](https://yeasy.gitbooks.io/docker_practice/content/)
* [docker问答](https://segmentfault.com/t/docker)
* [moby](https://github.com/docker/docker)
* https://wiki.openstack.org/wiki/Docker
* https://wiki.archlinux.org/index.php/Docker

### License
  This is free software distributed under the terms of the MIT license
