# 1. 基本设置

欢迎来到此教程, 本系列教程的目标是从头构建jekyll网站 - 不依靠默认主题. 让我们开始吧!

## 安装Jekyll和bundler

安装好Ruby后, 在终端输入以下代码安装jekyll和bundler:
```
gem install jekyll bundler
```
在当前文件夹创建一个Gemfile:
```
bundle init
```
编辑Gemfile, 把jekyll作为依赖添加进去:
```
gem "jekyll"
```
最后使用`bundle`或`bundle install`命令为你的项目安装jekyll

现在你能在每次使用这个教程中jekyll命令的时候, 给它加个`bundle exec`前缀, 这能够确保你安装的jekyll是你在Gemfile中指定的版本

## 创建一个站点

是时候创建一个站点了!首先为你的网站创建一个新文件夹, 随便命名. 本教程余下的部分, 我们将这个新文件夹称为根文件夹.

如果你喜欢, 你也能在根文件夹初始化一个Git仓库. jekyll的一大优点是没有数据库. 所有内容都能够用Git进行版本控制. 

让我们添加第一个文件. 在根文件夹创建一个如下的`index.html`文件:
```
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Home</title>
  </head>
  <body>
    <h1>Hello World!</h1>
  </body>
</html>
```

## 构建

Jekyll是一个静态站点生成器, 所以在看到网页之前, 我们需要jekyll构建这个网站. 你能在根文件夹用以下任一一个命令进行构建:
- `jekyll build` - 构建站点并把站点输出在`_site`目录
- `jekyll serve` - 和`jekyll build`一样, 不过还在`http://localhost:4000`运行一个local web server, 并且源文件有任何改变它都会重新构建

使用`jekyll serve`命令, 在浏览器地址栏输入` http://localhost:4000`, 你应该能看到“Hello World!”.

看到这里, 你可能认为jekyll没啥用. 只不过是把一个HTML文件移动了一下位置. 耐心点, 年轻人, 还有很多要学的.