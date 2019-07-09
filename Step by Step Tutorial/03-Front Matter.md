# 3. Front Matter

Front matter是YAML(一种语言)的片段, 在两条虚线之间. front matter用来给页面设置变量, 例如:
```
---
my_number: 5
---
```
front matter变量要在`page`变量下面使用. 例如输出上面的变量:
```
{{ page.my_number }}
```

## 使用front matter

用front matter填充`<title>`元素:
```
---
title: Home
---
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>{{ page.title }}</title>
  </head>
  <body>
    <h1>{{ "Hello World!" | downcase }}</h1>
  </body>
</html>
```
Liquid filter和front matter起作用了!你可能感觉这比使用HTML代码要复杂. 下个教程你就知道为什么要这样做了