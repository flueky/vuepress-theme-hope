---
title: Markdown 语法
toc: true
order: 3
category:
 - Guide
---

详细展示了 `Markdown` 的一些基本语法，以及 `vuepress theme hope` 支持的高级语法。

<!-- more -->

## 示例

::: md-demo 示例

此为预览，点击后展开，查看 markdown 文本。

:::

## 标题

::: md-demo 标题
# H1
## H2
### H3
#### H4
##### H5
###### H6
:::

## 文本

::: md-demo 文本
正常文本
**粗体文本**
*斜体文本*
~~删除文本~~
==标记文本==
<u>下划线文本</u>
<kbd>ctl/cmd</kbd> + <kbd>c</kbd>
换行<br>内容
:::

## 列表

::: md-demo 列表
1. 数据1
    a. 数据数据1
    b. 数据数据2
1. 数据2
3. 数据3

- 一级列表
    * 二级列表
    - 二级列表
        - 三级列表
        + 三级列表
    - 二级列表
- 一级列表
<br>
- [ ] 待办任务
- [x] 已办任务
:::

## 引用

::: md-demo 引用
> 引用1
>> 引用11
>> 引用12
>
> 引用2
> 引用3
:::

## 代码块

::: md-demo 代码块
- 内嵌代码块
执行代码 `printf("hello world")`。

- 短代码块
```
int main(){
    printf("hello world");
}
```

- 长代码块 (支持高亮)
```c
#include <stdio.h>

int main(){
    printf("hello world");
}
```
:::

## 链接

::: md-demo 链接
- 点击打开 [百度](https://www.baidu.com) 。
- 跳转到 [示例](#示例) 。
- 定义引用[链接][1] 。
- 定义[隐式引用链接][] 。
- https://www.baidu.com .
- <flueky.zuo@gmail.com> .

[1]: https://www.baidu.com "百度"
[隐式引用链接]: https://www.baidu.com 
:::

## 图像

::: md-demo 图像
![图像描述](https://support-assets.githubassets.com/packs/static/components/v2/components/assets/images/product-cards/get-started-f69cbc8bacc67cbe4240.webp =500x500)

<img src="https://support-assets.githubassets.com/packs/static/components/v2/components/assets/images/product-cards/feedback-957018385da3380db6c1.webp" width=600></img>
:::

## 注脚

::: md-demo 注脚
这里有一个注脚。[^1]
这里有另一个注脚。[^2]

[^1]: 注脚解释1。
[^2]: 注脚解释2。
:::

## 上标下标

::: md-demo 上标下标
- 标签
x<sup>y</sup>
a<sub>1</sub>
- markdown
19^th^
H~2~O
:::

## 表格

::: md-demo 表格
|列1|列2|列3|
|:-----|:-----:|-----:|
|文本居左|文本居中|文本居右|
:::

## 分割线

::: md-demo 分割线
---
***
___
:::

## 数学公式

::: md-demo 数学公式
Euler's identity $e^{i\pi}+1=0$ is a beautiful formula in $\mathbb{R}^2$.

$$
\frac {\partial^r} {\partial \omega^r} \left(\frac {y^{\omega}} {\omega}\right)
= \left(\frac {y^{\omega}} {\omega}\right) \left\{(\log y)^r + \sum_{i=1}^r \frac {(-1)^i r \cdots (r-i+1) (\log y)^{r-i}} {\omega^i} \right\}
$$
:::

## 警告

::: md-demo 警告
> [!important]
> This is important text

> [!info]
> This is information text

> [!tip]
> This is tip text

> [!warning]
> This is warning text

> [!caution]
> This is caution text

> [!note]
> This is note text
:::

## 提示

:::: md-demo 提示
::: important Custom Title

A custom important container with `code`, [link](#demo).

```js
const a = 1;
```

:::

::: info Custom Title

A custom information container with `code`, [link](#demo).

```js
const a = 1;
```

:::

::: note Custom Title

A custom note container with `code`, [link](#demo).

```js
const a = 1;
```

:::

::: tip Custom Title

A custom tip container with `code`, [link](#demo).

```js
const a = 1;
```

:::

::: warning Custom Title

A custom warning container with `code`, [link](#demo).

```js
const a = 1;
```

:::

::: caution Custom Title

A custom caution container with `code`, [link](#demo).

```js
const a = 1;
```

:::

::: details Custom Title

A custom details container with `code`, [link](#demo).

```js
const a = 1;
```
:::

::::

## 标签

:::: md-demo 标签

A tab of fruit:

::: tabs#fruit

@tab apple#apple

Apple

@tab banana#banana

Banana

:::

Another tab of fruit:

::: tabs#fruit

@tab apple

Apple

@tab banana

Banana

@tab orange

Orange

:::

A tab of fruit without id:

::: tabs

@tab apple

Apple

@tab banana

Banana

@tab orange

Orange

:::
::::

## 自定义对齐

:::: md-demo 对齐

::: left
左对齐的内容
:::

::: center
居中的内容
:::

::: right
右对齐的内容
:::

::: justify
两端对齐的内容
:::

::::

## 思维导图

````markmap
---
markmap:
  colorFreezeLevel: 2
---

# markmap

## Links

- <https://markmap.js.org/>
- [GitHub](https://github.com/markmap/markmap)

## Features

- links
- **strong** ~~del~~ *italic* ==highlight==
- multiline
  text
- `inline code`
-
    ```js
    console.log('code block');
    ```
- Katex
  - $x = {-b \pm \sqrt{b^2-4ac} \over 2a}$
- Now we can wrap very very very very long text based on `maxWidth` option
````

## 流程图

```flow
st=>start: Start|past:>http://www.google.com[blank]
e=>end: End|future:>http://www.google.com
op1=>operation: My Operation|past
op2=>operation: Stuff|current
sub1=>subroutine: My Subroutine|invalid
cond=>condition: Yes
or No?|approved:>http://www.google.com
c2=>condition: Good idea|rejected
io=>inputoutput: catch something...|future

st->op1(right)->cond
cond(yes, right)->c2
cond(no)->sub1(left)->op1
c2(yes)->io->e
c2(no)->op2->e
```