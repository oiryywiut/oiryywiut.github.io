# 8. 写博客
你可能想知道如何在没有数据库的情况下拥有博客。在Jekyll中，博客由文本文件提供支持.

## Posts
一篇博客被称为一个post, post要位于根目录一个`_posts`的文件夹. post的文件名有一个特殊的格式: 一个发布日期, 一个标题, 后跟拓展名

用下列内容首次创建`_posts/2018-08-20-bananas.md`post:

```
---
layout: post
author: jill
---
A banana is an edible fruit – botanically a berry – produced by several kinds
of large herbaceous flowering plants in the genus Musa.

In some countries, bananas used for cooking may be called "plantains",
distinguishing them from dessert bananas. The fruit is variable in size, color,
and firmness, but is usually elongated and curved, with soft flesh rich in
starch covered with a rind, which may be green, yellow, red, purple, or brown
when ripe.
```

这就像之前创建的`about.md`, 除了它有一个author和不同的layout. author是自定义变量, 它不是必须的.

## layout   
`post`layout不存在, 所以需要在`_layouts/post.html`创建一个. 使用以下代码:

```
---
layout: default
---
<h1>{{ page.title }}</h1>
<p>{{ page.date | date_to_string }} - {{ page.author }}</p>

{{ content }}
```

这是layout继承的实例. post layout输出标题, 日期, 作者和内容主体. 这些都是基于default layout.

还有`date_to_string`filter, 这能让日期更好的显示.

## 链接到posts
现在没有办法导航到post. 一般post有一个页面列出所有的post.

jekyll使你能够通过`site.posts`遍历post.

在根目录创建`blog.html`并敲入以下代码:

```
---
layout: default
title: Blog
---
<h1>Latest Posts</h1>

<ul>
  {% for post in site.posts %}
    <li>
      <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
      <p>{{ post.excerpt }}</p>
    </li>
  {% endfor %}
</ul>
```

- `post.url`是jekyll自动设置post输出的路径
- `post.title`是从帖子文件名中提取的，可以通过设置在title来覆盖
- `post.excerpt`默认情况下是post内容的第一段

你还需要从主页链接到此页. 打开`_data/navigation.yml`, 给`blog.html`添加条目:

```
- name: Home
  link: /
- name: About
  link: /about.html
- name: Blog
  link: /blog.html
```

## More posts
还可以加入更多的post:
`_posts/2018-08-21-apples.md`:

```
---
layout: post
author: jill
---
An apple is a sweet, edible fruit produced by an apple tree.

Apple trees are cultivated worldwide, and are the most widely grown species in
the genus Malus. The tree originated in Central Asia, where its wild ancestor,
Malus sieversii, is still found today. Apples have been grown for thousands of
years in Asia and Europe, and were brought to North America by European
colonists.
```

`_posts/2018-08-22-kiwifruit.md`:

```
---
layout: post
author: ted
---
Kiwifruit (often abbreviated as kiwi), or Chinese gooseberry is the edible
berry of several species of woody vines in the genus Actinidia.

The most common cultivar group of kiwifruit is oval, about the size of a large
hen's egg (5–8 cm (2.0–3.1 in) in length and 4.5–5.5 cm (1.8–2.2 in) in
diameter). It has a fibrous, dull greenish-brown skin and bright green or
golden flesh with rows of tiny, black, edible seeds. The fruit has a soft
texture, with a sweet and unique flavor.
```

现在, 可在`http://localhost:4000`看看效果.





