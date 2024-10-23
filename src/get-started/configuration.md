---
title: 基本配置
order: 1
category:
 - Guide
---

<!-- more -->
 
## Base URL

运行服务后，默认地址是 http://localhost:8080，如需要，可替换成任意你想要的地址。

如：http://localhost:8080/demo/。

修改 `.vuepress/config.js`

```js
export default defineUserConfig({
  base: "/",
})
```

## 多语言

此项目支持多语言切换，可通过工具栏切换。

```js
export default defineUserConfig({
  locales: {
    "/": { // 默认语言
      lang: "zh-CN",
      title: "文档演示",
      description: "vuepress-theme-hope 的文档演示",
    },
    "/en/": {
      lang: "en-US",
      title: "Docs Demo",
      description: "A docs demo for vuepress-theme-hope",
    },
  },
})
```

## 个人信息

修改 `.vuepress/theme.js`

```js
export default hopeTheme({
  author: {
    name: "Flueky Zuo",
    // 个人主页地址
    url: "https://flueky.github.io",
  },
}）
```