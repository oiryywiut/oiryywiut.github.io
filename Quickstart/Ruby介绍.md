# Ruby 101
jekyll是用Ruby写的. 如果你没听说过Ruby, 这个页面能帮你快速掌握一些术语.

## Gems
gem是被打包的代码, 能包含在Ruby项目中, 并能够共享给其它项目或其他人. gem能执行功能, 例如:
- 将Ruby对象转换为JSON
- 分页
- 与API交互, 例如Github
- jekyll本身是一个gem. 以及许多Jekyll插件也是gem, 包括jekyll-feed, jekyll-seo-tag和jekyll-archives.

## Gemfile
Gemfile是一个装着gem的文件. 对于一个简单的jekyll站点, 它可能像这样:
```
source 'https://rubygems.org'

gem 'jekyll'

group :jekyll_plugins do
  gem 'jekyll-feed'
  gem 'jekyll-seo-tag'
end
```

## Bundler
bundler可以安装Gemfile中的gem. 安装bundler(只需安装一次):
```
gem install bundler
```
安装Gemfile中的相应版本的gem:
```
bundle install
```
