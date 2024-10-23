---
title: 使用 Docker
order: 4
category:
 - Guide
---

使用 Docker 可以简化 vuepress theme hope 的运行和部署步骤。要求大家事先在在电脑上安装好 Docker ，见 [官方文档](https://docs.docker.com/get-started/get-docker/) 。

<!-- more -->

## 编译 Docker Image

在源码中[ci](https://github.com/flueky/vuepress-theme-hope/tree/main/ci) 目录下，提供了编写好的 `dockerfile` 文件。 

### nginx-ubuntu

`nginx-ubuntu` 是楼主自行构建的的 docker image。 可以通过直接修改 dockerfile 中的下载链接，更新新的版本。 

```shell
docker build -t nginx-ubuntu  -f ci/nginx/dockerfile . # 构建 image
```

也可以直接从官方提供的 [站点](https://nodejs.org/en/download/package-manager) 下载自己需要的镜像 。

```shell
# pulls the Node.js Docker image
docker pull node:22-alpine
# verifies the right Node.js version is in the environment
docker run node:22-alpine node -v # should print `v22.10.0`
# verifies the right npm version is in the environment
docker run node:22-alpine npm -v # should print `10.9.0`
```

### vuepress-theme-hope-server

```docker
# 如果用 nginx 官方的镜像，替换成 node:22-alpine
FROM nginx-ubuntu
# 定义工作目录，即 CMD 参数执行的位置
WORKDIR /root/vuepress-theme-hope
# 端口给物理机器映射。 8080 是 nodejs 默认端口
EXPOSE 8080
# 设置容器运行时执行的命令
CMD pnpm install && pnpm docs:dev
``` 

以上是 `ci/dev/dockerfile` 内容，需要执行 `docker build` 命令生成镜像文件才能使用。

```shell
docker build -t vuepress-theme-hope-server -f ci/dev/dockerfile . # -t vuepress-theme-hope-server 指定镜像文件名称。
docker run -d --privileged=true -v ~/workspace/blog/vuepress-theme-hope:/root/vuepress-theme-hope -p 8081:8080 --name vue-docs vuepress-theme-hope-server
```

参数解释：

- -d: 在后台运行
- --privileged=true：给容器赋予读写外部磁盘的权限
- -v xxxx:xxx 映射外部存储路径到容器内
- -p: 映射端口
- --name: 设定容器名称
- vuepress-theme-hope-server：使用的镜像名称

> [!important]
> 如果修改一些配置文件导致服务自动重启失败，建议先删除 `node_modules` 目录并执行 `docker restart vue-docs`， 重启容器。

### vuepress-theme-hope-build

```docker
FROM nginx-ubuntu
# 安装需要程序
RUN set -eux; \
	apt install -y \
		zip \
    ; \
	apt clean all

WORKDIR /root/vuepress-theme-hope
# 设置容器运行时，执行的命令
CMD pnpm install && pnpm docs:build \
	&& cd src/.vuepress && zip -r dist.zip dist \
	&& mkdir ../../out && mv dist.zip ../../out \
	&& rm -r dist
```

```shell
docker build -t vuepress-theme-hope-build  -f ci/build/dockerfile .
docker run -i --privileged=true -v ~/workspace/blog/vuepress-theme-hope:/root/vuepress-theme-hope vuepress-theme-hope-build 
```

参数解释:
- -i：交互的方式运行，用于输出命令日志输出
- vuepress-theme-hope-build：使用的镜像名称

:::: important 重要提醒

在使用 docker 时，如下命令可能对你有用。
```shell
docker image list # 查看本机已编译/下载的镜像
docker ps -a # 查看全部（运行/停止）的容器
docker system prune #  清理没有名字的镜像以及停止运行的容器，释放物理空间
```

> [!tip]
> 当 dockerfile 被修改后，反复构建多次镜像，只有最后一次生成的镜像会拥有名字。之前其余的镜像只剩 id 信息。可使用 `docker image list` 检查。

::::

