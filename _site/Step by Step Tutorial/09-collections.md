# 9. collections
让我们看看如何做作者页面，以便每位作者都有自己的页面，其中包含一个简介和他们发布的post。

要完成这项任务要使用collection. collection类似于`_posts`.

## 配置

配置collection, 需要在根目录用以下代码创建一个`_config.yml`文件:

```
collections:
  authors:
```

为了加载这个配置, 需要重启jekyll server. 在终端按`Ctrl`+`c`停止server, 然后使用`jekyll serve`启动Jekyll server

## 添加作者

在根目录创建一个`_authors`目录. 这是一个collection目录

为每个作者创建一个文档:
`_authors/jill.md`:

```
---
short_name: jill
name: Jill Smith
position: Chief Editor
---
Jill is an avid fruit grower based in the south of France.
```

`_authors/ted.md`:

```
---
short_name: ted
name: Ted Doe
position: Writer
---
Ted has been eating fruit since he was baby.
```

## staff page

创建一个包含所有作者的页面. jekyll提供了`site.authors`

在根目录创建`staff.html`, 然后迭代`site.authors`输出作者列表:

```
---
layout: default
title: Staff
---
<h1>Staff</h1>

<ul>
  {% for author in site.authors %}
    <li>
      <h2>{{ author.name }}</h2>
      <h3>{{ author.position }}</h3>
      <p>{{ author.content | markdownify }}</p>
    </li>
  {% endfor %}
</ul>
```

因为内容是markdown, 你需要使用`markdownify`filter.

你需要导航到这个页面, 打开`_data/navigation.yml`. 添加以下条目:

```
- name: Home
  link: /
- name: About
  link: /about.html
- name: Blog
  link: /blog.html
- name: Staff
  link: /staff.html
```

## 输出collection中页面


一般, collections中的页面不可以输出. 现在, 我们想每个作者有他们自己的页面. 所以要调整一下collection配置:

打开`_config.yml`添加`output: true`配置:

```
collections:
  authors:
    output: true
```

你能使用`autuor.url`链接到输出页面:

调整一下`staff.html`:

```
---
layout: default
---
<h1>Staff</h1>

<ul>
  {% for author in site.authors %}
    <li>
      <h2><a href="{{ author.url }}">{{ author.name }}</a></h2>
      <h3>{{ author.position }}</h3>
      <p>{{ author.content | markdownify }}</p>
    </li>
  {% endfor %}
</ul>
```

就像`_posts`一样, 你需要给作者的layout

用一下代码创建`_layouts/author.html`:

```
---
layout: default
---
<h1>{{ page.name }}</h1>
<h2>{{ page.position }}</h2>

{{ content }}
```

## Front matter defaults

之前给每个页面加layout有点重复.所以可以实现自动在front matter添加layout

实现这功能, 需要在`_config.yml`使用**front matter defaults**:

```
collections:
  authors:
    output: true

defaults:
  - scope:
      path: ""
      type: "authors"
    values:
      layout: "author"
  - scope:
      path: ""
      type: "posts"
    values:
      layout: "post"
  - scope:
      path: ""
    values:
      layout: "default"
```

现在你能去掉所有页面front matter中的layout了. 注意每次修改`_config.yml`文件你都需要重启jekyll server

## 在作者个人页面列出posts

列出一个作者发布的post. 你需要将`_authors`的`short_name`与`_post`的author匹配. 用此来过滤按作者过滤`_posts`


在`_layouts/author.html`迭代这个过滤的列表:

```
---
layout: default
---
<h1>{{ page.name }}</h1>
<h2>{{ page.position }}</h2>

{{ content }}

<h2>Posts</h2>
<ul>
  {% assign filtered_posts = site.posts | where: 'author', page.short_name %}
  {% for post in filtered_posts %}
    <li><a href="{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
```

## 在post链接到作者页面

在`_layouts/post.html`使用相似的过滤技巧:

```
---
layout: default
---
<h1>{{ page.title }}</h1>

<p>
  {{ page.date | date_to_string }}
  {% assign author = site.authors | where: 'short_name', page.author | first %}
  {% if author %}
    - <a href="{{ author.url }}">{{ author.name }}</a>
  {% endif %}
</p>

{{ content }}
```







