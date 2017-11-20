##docker的指令

### Docker 存在的意义

 * 使用dokcer加速本地开发和构建，开发人员可以构建、运行并分享Docker容器，容器可以在开发环境中构建，然后轻松地提交到测试环境中，并最终进入生产环境
 * 能够让独立服务或应用程序在不同环境中，得到相同的运行结果。
 * 用docker 创建隔离环境进行测试
 * docker 可以让开发者先在本机上构建一个复杂的程序测试，而不是一开始就在生产环境进行测试

### Docker概念

 * Docker 的常用文档:https://docs.docker.com/
 * Docker 镜像: 用户基于镜像来运行自己的容器，可以把镜像当做容器的『源代码』，镜像体积很小，易于分享、存储和更新
 * Registry: Docker 用 Registry 保存用户构建的镜像，Registry 分为公共和私有两种:
   * Docker 公司运营的公共 Registry 叫做 Docker Hub，我们可以在上面注册账号，分享并保存自己的镜像。
   * 可以在 Docker Hub 保存自己的私有镜像或者架设自己私有的 Registry
 * Docker 容器: 把应用程序或服务打包放进去，容器是基于镜像启动的，容器中可以运行一个或多个进程。
   * 镜像是 Docker 生命周期中的构建或打包阶段
   * 容器则是启动或执行阶段

### 查看docker信息（version、info）
 1. 查看系统内核 
 
 `
    uname -r
 `
 
 2. 启动docker 境像
 
 `
    systemctl start docker 
 `
 
 3.查看docker版本  
 
 `
    docker verison
 `
 
 4.显示docker系统的信息 
 
 `
    docker info
 `

### 操作docker镜像

 1.检索image 
 
 `
    docker search image-name
 `
 
 2.下载image
 
 `
    docker pull image-name
 `
 
 3.列出镜像列表
 
 `
    docker images 
 `
 4.删除一个或者多个镜像
 
 `
    docker rmi image-name
 `
 
 5.显示一个镜像的历史
 
 `
   docker history image-name  
 `
 
 6.
 
 