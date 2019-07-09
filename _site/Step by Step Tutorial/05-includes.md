# 5. Includes

链接应该被添加到各个页面, 所以把链接添加到layout是不错的. 但还有一个方法, 那就是includes.

## Include tag

`include`tag能够引用存在`_includes`文件夹的内容, 就像layout能够被引用一样.

## Include使用

在`_includes/`创建一个`navigation.html`文件. 把下列的代码添加进去:
```
<nav>
  <a href="/">Home</a>
  <a href="/about.html">About</a>
</nav>
```
使用include tag把`navigation.html`添加到`_layouts/default.html`:
```
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>{{ page.title }}</title>
  </head>
  <body>
    {% include navigation.html %}
    {{ content }}
  </body>
</html>
```
可以看到, 现在在浏览器的` http://localhost:4000`页面有了两个链接

## 高亮链接

`_includes/navigation.html`需要知道页面的URL, 以便能添加样式. Jekyll有个`page.url`变量.

`page.url`可以检查页面的URL. 它可以用来高亮你现在所处位置的链接(类似于面包屑导航). 用一下代码替换`navigation.html`的代码:
```
<nav>
  <a href="/" {% if page.url == "/" %}style="color: red;"{% endif %}>
    Home
  </a>
  <a href="/about.html" {% if page.url == "/about.html" %}style="color: red;"{% endif %}>
    About
  </a>
</nav>
```
现在, 再上` http://localhost:4000`看看.

如果要添加新链接, 或者改变链接颜色, 仍然要敲很多重复的代码. 下一教程将会解决这个问题