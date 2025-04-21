
## Docker是什么
**Docker 属于 Linux 容器的一种封装，提供简单易用的容器使用接口。** 它是目前最流行的 Linux 容器解决方案。

## 安装
去官网下载安装包，安装完成后，运行下面的命令，验证是否安装成功。
```shell
docker version
# or 
docker info
```

## Image
Image叫做Docker镜像，是一个二进制文件。docker把应用程序机器依赖打包在Image文件中。通过Image文件，可以生成Docker容器。

Docker 根据 Image 文件生成容器的实例。同一个 Image 文件，可以生成多个同时运行的容器实例。


```shell
# 列出本机上的所有docker image文件
docker image ls

# 删除指定的docker image文件
docker image rm [imageName]
```


#### Docker Hub
Docker Hub是Docker的官方仓库，是最常用最重要的Image仓库。大家制作的Image文件都可以上传到这个仓库供他人使用

#### 从Docker仓库拉取Image镜像文件

```shell
docker image pull [imageName]

# 比如从docker hub拉取hello-world镜像文件
docker image pull libaray/hello-world
```

其中`library`是 image 文件所在的组，`hello-world`是 image 文件的名字。
由于 Docker 官方提供的 image 文件，都放在[`library`](https://hub.docker.com/r/library/)组里面，所以它的是默认组，可以省略。因此，上面的命令可以写成下面这样。
```shell
docker image pull hello-world
```

#### 运行docker image
使用`docker container run`命令来运行一个image文件，并生成对应的container实例，多次运行会产生多个container实例。
```shell
docker container run [imageName]
# for example
docker container run hello-world
```
`docker container run` 命令也可以简写为`docker run [iamgeName]`

此外 `docker container run`命令还有自动拉取image文件的功能，当运行该命令时，如果指定的image文件在本机不存在，docker会自动从仓库拉取，因此`docker image pull [imageName]`命令不是必须的。

## Container
**image 文件生成的容器实例，本身也是一个文件，称为容器文件。** 也就是说，一旦容器生成，就会同时存在两个文件： image 文件和容器文件。而且关闭容器并不会删除容器文件，只是容器停止运行而已。

```shell
# 列出本机正在运行的容器
docker container ls

# 列出本机所有容器，包括终止运行的容器
docker container ls --all

# 删除容器文件
docker container rm [containerID]
```

