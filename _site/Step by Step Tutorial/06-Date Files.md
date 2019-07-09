# 6. 数据文件

Jekyll支持加载`_data`目录中的YAML, JSON和CSV文件. 数据文件将内容与源代码分开, 使网站更容易维护.

## 使用数据文件
YAML是Ruby生态系统中常见的格式. 你能够使用它存储一系列的链接数据. 每个数据有一个链接名和链接地址.

在`_data`目录用下列代码创建一个`navigation.yml`的数据文件:
```
- name: Home
  link: /
- name: About
  link: /about.html
```
Jekyll使你能够用`site.data.navigation`调用`navigation.yml`的数据文件.

现在你能够迭代数据文件, 而不是在`_includes/navigation.html`手动敲入链接:
```
<nav>
  {% for item in site.data.navigation %}
    <a href="{{ item.link }}" {% if page.url == item.link %}style="color: red;"{% endif %}>
      {{ item.name }}
    </a>
  {% endfor %}
</nav>
```
输出结果完全一样. 不同的是你增加新链接更容易了.

没有CSS，JS和图像的网站有什么用？下一教程学习如何处理jekyll中的**assets**