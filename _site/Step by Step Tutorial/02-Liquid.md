# 2. Liquid

Liquid是让Jekyll变得有趣的地方. Liquid是一个模板语言, 有三个主要部分: **objects**, **tags**和**filters**.

## Objects

Objects告诉Liquid把内容输出在什么地方. objects用大括号``{{``和``}}``. 例如:
```
{{ page. title }}
```
在页面输出一个`page.title`的变量

## Tags

Tags使模板有了逻辑和控制. 他们用大括号和百分号表示: `{%`和`%}`. 例如:
```
{% if page.show_sidebar %}
  <div class="sidebar">
    sidebar content
  </div>
{% endif %}
```
意思是如果`page.show_sidebar`为true, 那么就输出下面的div元素

## Filters

Filters改变一个Liquid object的输出. filters使用在输出中, 由`|`分开. 例如:
```
{{ "hi" | capitalize }}
```
意思是输出`Hi`(使首字母大写).

## 使用Liquid

现在, 试着把你页面上的Hellow World!转换为小写:
```
...
<h1>{{ "Hello World!" | downcase }}</h1>
...
```
要让jekyll处理我们的操作, 我们需要在页面的顶部添加**font matter**:
```
---
# 在此处添加front matter, 告诉jekyll处理Liquid
---
```


front matter详情见下一教程