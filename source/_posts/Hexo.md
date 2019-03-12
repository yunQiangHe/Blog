---
title: Hexo
date: 2019-03-12 17:45:20
categories: 
tags: 
description: Hexo是一个快速、简洁且高效的博客框架。Hexo 使用 Markdown（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页。
---
[参考链接hexo.io](https://hexo.io/zh-cn/)
[主题maupassant](https://github.com/tufu9441/maupassant-hexo)

> **Hexo** 是一个快速、简洁且高效的博客框架。Hexo 使用 Markdown（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页。


```bash
$ hexo new [layout] "title" 新建一篇文章
$ hexo server 启动服务器。默认情况下，访问网址为 http://localhost:4000/
$ hexo clean 清除缓存文件 (db.json) 和已生成的静态文件 (public)。
$ hexo generate
$ hexo deploy
```

**tips**
1. 在文章的front-matter中添加toc: true即可让该篇文章显示目录;
2. 文章和页面的评论功能可以通过在front-matter中设置comments: true或comments: false来进行开启或关闭（默认开启）。
3. 在source目录下建立相应名称的文件夹，然后在文件夹中建立index.md文件，并在index.md的front-matter中设置layout为layout: page。若需要单栏页面，就将layout设置为 layout: single-column。