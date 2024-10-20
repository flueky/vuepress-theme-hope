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