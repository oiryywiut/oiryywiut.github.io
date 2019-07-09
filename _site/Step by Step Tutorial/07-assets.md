# 7. Assets

Jekyll能够直接使用CSS, JS, 图片和其它的assets. 

Jekyll站点的assets结构通常是这样的:
```
.
├── assets
|   ├── css
|   ├── images
|   └── js
...
```

## Sass

使用在`_includes/navigation.html`中的行内样式不是最佳实践, 让我们用类给页面添加样式:

```
<nav>
  {% for item in site.data.navigation %}
    <a href="{{ item.link }}" {% if page.url == item.link %}class="current"{% endif %}>{{ item.name }}</a>
  {% endfor %}
</nav>
```
你能够使用标准的CSS文件添加样式. 我们将在此使用[Sass](https://www.sass.hk/).

首先, 在`/assets/css/styles.scss`创建一个Sass文件. 文件内包含以下代码:

```
---
---
@import "main";
```

顶部的虚线是front matter, 告诉jekyll处理这个文件.`@import "main"`告诉告诉Sass在sass目录寻找一个`main.scss`文件(`_sass/`默认要放在在网站的根文件夹).

在`/_sass/`创建一个`main.scss`文件, 并敲入以下代码:

```
.current {
  color: green;
}
```

你需要在layout中引用css

打开`_layouts/default.html`, 把在`<head>`中引用css:

```
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>{{ page.title }}</title>
    <link rel="stylesheet" href="/assets/css/styles.css">
  </head>
  <body>
    {% include navigation.html %}
    {{ content }}
  </body>
</html>
```

此时, 应该可以在` http://localhost:4000`看到绿色的链接了
