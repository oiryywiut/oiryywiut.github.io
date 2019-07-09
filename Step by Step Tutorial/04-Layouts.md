# 4. Layouts

网站一般有多个页面, jekyll站点也不例外. layout就是把一些重复的代码放在一起, 生成页面的时候调用.

Jekyll支持Markdown以及HTML. markdown适用于内容结构简单的页面. 因为它比HTML更简洁. 让我们试一试.

在根目录创建`about.md`.

## 创建layout

layout存放在`_layouts`目录. 在`_layouts/default.html`用下面代码创建你的第一个layout:
```
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>{{ page.title }}</title>
  </head>
  <body>
    {{ content }}
  </body>
</html>
```
这几乎与`index.html`相同! 除了没有front matter, 页面的内容被替换为`content`变量.

为了让`index.html`使用这个layout, 你需要在`index.html`的front matter设置`layout`变量, 这时, 你的`index.html`文件应该像下面一样:
```
---
layout: default
title: Home
---
<h1>{{ "Hello World!" | downcase }}</h1>
```
这样做之后,你会发现, 输出的页面与之前的完全一样

## about页面
之前的about页面, 你也能使用layout.
把以下代码添加到`about.md`:
```
---
layout: default
title: About
---
# About page

This page tells you a little bit about me.
```
在浏览器地址栏输入`http://localhost:4000/about.html `查看about页面

祝贺你, 你的网站已经有两个页面了! 但是如何从一个页面导航到另一个页面? 下一教程为你解答