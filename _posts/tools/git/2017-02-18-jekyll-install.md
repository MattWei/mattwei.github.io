---
layout: post
title: "Jekyll 使用"
description: "."
tags: [GitHub, Jekyll]
category: 工具
---

# 新建Jekyll site

使用默认的gem-based  theme新建一个site:
```
# Install Jekyll and Bundler gems through RubyGems
~ $ gem install jekyll bundler

# Create a new Jekyll site at ./myblog
~ $ jekyll new myblog

# Change into your new directory
~ $ cd myblog

# Build the site on the preview server
~/myblog $ bundle exec jekyll serve

# Now browse to http://localhost:4000

```

# GitHub pages 本地化
[GitHub pages文档](https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll/)

1. 将GitHub上的文档clone下来
    ```
    $ git clone URL directory
    ```

2. 新建Gemfile,加入
    ```
    source 'https://rubygems.org'
    gem 'github-pages', group: :jekyll_plugins
    ```
3. 安装jekyll和其他依赖
    ```
    $ bundle install

    Fetching gem metadata from https://rubygems.org/............
    Fetching version metadata from https://rubygems.org/...
    Fetching dependency metadata from https://rubygems.org/..
    Resolving dependencies...
    ```
4. 本地运行,并在浏览器上输入 http://localhost:4000 查看
    ```
    $ bundle exec jekyll serve
    ```

# 安装theme
[GitHub pages文档](https://help.github.com/articles/adding-a-jekyll-theme-to-your-github-pages-site/)
1. 将theme代码clone下来
2. 安装jekyll 和其他依赖
    ```
    $ bundle install
    ```
3. 上传github-pages
    ```
    $ git push origin master
    ```
