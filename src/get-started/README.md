---
title: 快速上手
category:
 - Guide
---

这不仅是一篇使用 [Vuepress Theme Hope](https://theme-hope.vuejs.press/) 的教程，也记录着小编对原项目的整理和优化。多数内容均来自 [官方文档](https://theme-hope.vuejs.press/get-started/) 。

<!-- more -->

```shell
# 获取源码
git clone https://github.com/flueky/vuepress-theme-hope.git
# 安装 nodejs 后执行下面命令
npm install -g pnpm 
# 安装依赖
pnpm install
# 运行服务
pnpm docs:dev
```

## 工程结构

```
├─ ci # dockerfile 
└─ src
   ├─ .vuepress
   │  ├─ ...
   │  ├─ navbar # 导航栏配置
   │  ├─ sidebar # 侧边栏配置
   │  ├─ config.ts # vuepress 项目配置
   │  └─ theme.ts # 主题配置
   ├─ blog
   |  └─ README.md # 博客首页
   ├─ get-started
   │  ├─ ...
   │  └─ markdown.md
   │  └─ README.md
   ├─ ...
   └─ README.md # 文档首页
```

1. [基本配置](configuration.md)
2. [高级优化](advanced.md)
3. [Markdown 语法](markdown.md)
4. [使用 Docker](doker.md)