---
title: webpack
date: 2019-08-17 23:48:32
categories:
tags:
description: webpack是现代前端开发中最火的模块打包工具，只需要通过简单的配置，便可以完成模块的加载和打包。那它是怎么做到通过对一些插件的配置，便可以轻松实现对代码的构建呢？
---

[webpack详解](https://juejin.im/post/5aa3d2056fb9a028c36868aa)
[【Cute-Webpack】Webpack4 入门手册（共 18 章](https://juejin.im/post/5d518b4de51d4561cc25f013)
[《2019最新Webpack4.0教程4.x 成仙之路》](https://www.bilibili.com/video/av41546218/?p=1)

[node中path.resolve()](http://nodejs.cn/api/path.html#path_path_resolve_paths)

## 核心概念
1. 入口 entry
2. 出口 output
3. loader
4. 插件 plugins
5. 模式 mode
6. 浏览器兼容性(browser compatibility)

## 补充概念
1. 模块(module): 这些选项决定了如何处理项目中的不同类型的模块。
webpack 模块可以支持如下:

- ES2015 import 语句
- CommonJS require() 语句
- AMD define 和 require 语句
- css/sass/less 文件中的 @import 语句。
- 样式(url(...))或 HTML 文件(<img src=...>)中的图片链接(image url)
