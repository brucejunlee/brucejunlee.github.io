---
layout: post
title: "构建一个简单的博客"
author: "李军"
categories: journal
tags: [Jekyll, Github, Blog]
image:
  feature: github.jpg
  teaser: github-teaser.jpg
  credit:
  creditlink: ""
---

有很多种方式来创建静态网站，如[Hugo](https://gohugo.io)、Jekyll等。这里我们仅使用`Jekyll`+`GitHub`，来快速搭建一个简易、免费的个人博客。

# Jekyll是什么？

Jekyll是一个简单的、静态的站点生成器。它可用于搭建个人博客，项目，或者机构网站。基本上来讲，Jekyll使用模板和自定义的页面内容，就可以生成一个完整的网站。更多信息，请访问[官网](https://jekyllrb.com/docs/home/)。

# 快速操作指南

### 安装Ruby

```shell
cd ~
brew install ruby
```

### 安装Jekyll和bundler

```shell
gem install jekyll bundler
```

### 新建文件夹

```shell
jekyll new myblog
```

### 登陆网站

```shell
cd myblog
jekyll serve
```

### 使用模板

* 从[网站](http://jekyllthemes.org)或github下载选择一个模板下载

* 把模板中的所有内容放置在myblog文件夹下

  ```shell
  bundle install
  bundle exec jekyll serve
  ```

* 访问网址 http://localhost:4000

### 将网站部署到GitHub

* 创建一个与用户名一致的仓库

  ```nothing
  https://github.com/username/username.github.io.git
  ```

* 建立本地与GitHub仓库的关联

  ```shell
  cd myblog
  git init
  git add .
  git commit -m "first commit"
  git remote add origin https://github.com/username/username.github.io.git
  git push -u origin master
  ```

* 浏览器输入`username.github.io`即可

### 添加文章/修改文章内容

```shell
git add _post/2017-10-01-test.markdown
git commit -m "add test.file"
git push origin master
```

### 删除文章

```shell
git status
git rm _post/2017-01-01-delete.markdown
git commit -m "remove delete.file"
git push -u origin master
```

### 恢复文章

```shell
git  checkout -- _post/2017-01-01-delete.markdown
```

### 域名绑定

* 获取IP地址

  ```shell
  ping brucejunlee.github.io
  ```

* 申请域名

  * 这里申请万网的`.site`域名，并添加解析

* 在博客根目录下添加`CNAME`文件

  * ```nothing
    echo "brucejunlee.site" > CNAME
    ```

