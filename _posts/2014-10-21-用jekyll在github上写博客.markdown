---
layout: post
title: "用jekyll在github上写博客"
author: "Moose W. Oler"
abstract: "本文介绍了如何在github上写博客。涉及到用jekyll本地调试的一些内容。"
categories: 
 - 博客建设
tags: 
 - github
 - jekyll
 - markdown
---

###0 引言

GitHub Pages是为了满足github的用户建立项目主页的需求而提供的功能。它除了支持纯HTML
之外，还支持Jekyll。由于Jekyll自己宣传是“blog-aware”，所以github也鼓励自己的用户
用github.io写博客（）。

我最早看到的用Jekyll在github上建博的文章是这一篇：[搭建一个免费的，无限流量的Blog----github Pages和Jekyll入门](http://www.ruanyifeng.com/blog/2012/08/blogging_with_jekyll.html)。几年之后，有些用法发生了变化，包括github自己也给了适用[新手](https://pages.github.com/)和[老手](https://help.github.com/articles/using-jekyll-with-pages/)的jekyll攻略。这也就是为什么本文会出现在这里。

我的系统是debian 7.6。

###1 安装jekyll

**先安装ruby**

用下边的语句安装ruby。另外，还要安装dev包，需要根据实际版本号修改。 

    apt-get install ruby ruby1.9.1-dev 
    
**再安装bundler**

bundler是ruby的软件包管理器，由它来负责维护jekyll会方便很多。

    gem install bundler

**安装jekyll**

推荐在本机上装jekyll，这样就可以在提交前方便的修改。

先在站点的根目录下建立一个Gemfile，内容如下：

    source 'http://rubygems.org'
    gem 'github-pages'
    gem 'execjs'  
    gem 'therubyracer'

然后，用

    bundle install

bundle会自动解决依赖和版本号的问题，可能会#需要root权限#。

###2 本地运行

    bundle exec jekyll serve

然后打开浏览器，http://localhost:4000，即可预览博客。

