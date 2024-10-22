# Vuepree theme hope

## 运行环境

见 [搭建个人知识库](https://flueky.github.io/build-blog.html)。

## 启动服务

在准保好运行环境以及 clone 代码后，进入代码目录执行如下命令

```shell
pnpm install
pnpm docs:dev
```

输出结果如下：
```
✔ Initializing and preparing data - done in 5.80s

  vite v5.4.9 dev server running at:

  ➜  Local:   http://localhost:8080/
```

文档首页地址：http://localhost:8080/ <br>
博客首页地址：http://localhost:8080/blog/

## 部署服务

### Github Page

```shell
pnpm docs:build # 执行构建命令
```

将在 `src/.vuepress/dist` 生成的文件推送到 [Github Page](https://pages.github.com/) 上。

## Docker

Docker 可以很好的提供一套虚拟的 Linux 运行环境。[ci](ci) 目录下提供了需要构建的 docker 镜像文件。

```shell
docker build -t nginx-ubuntu -f ci/nginx/dockerfile . 
docker build -t vuepress-theme-hope-server -f ci/dev/dockerfile . 
docker build -t vuepress-theme-hope-build -f ci/build/dockerfile .
```

依次执行完上面三个命令后，使用 `docker image list` 检查结果。

```
REPOSITORY                   TAG       IMAGE ID       CREATED          SIZE
vuepress-theme-hope-build    latest    f0294dfa2ebf   18 minutes ago   322MB
vuepress-theme-hope-server   latest    c7839e714800   43 minutes ago   320MB
nginx-ubuntu                 latest    1b687a705528   47 minutes ago   320MB
```

### 启动服务

```shell
docker run -d  --privileged=true -v ~/workspace/blog/vuepress-theme-hope:/root/vuepress-theme-hope -p 8080:8080 --restart --name vue-docs vuepress-theme-hope-server
```

`~/workspace/blog/vuepress-theme-hope` 是本地源码目录，下同。

### 打包部署

```shell
docker run -i --privileged=true -v ~/workspace/blog/vuepress-theme-hope:/root/vuepress-theme-hope vuepress-theme-hope-build
```