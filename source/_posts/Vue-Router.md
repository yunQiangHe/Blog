---
title: Vue Router
date: 2019-03-30 13:45:05
categories: Vue
tags:
description: Vue Router 是 Vue.js 官方的路由管理器。它和 Vue.js 的核心深度集成，让构建单页面应用变得易如反掌。 
---
* 嵌套的路由/视图表
* 模块化的、基于组件的路由配置
* 路由参数、查询、通配符
* 基于 Vue.js 过渡系统的视图过渡效果
* 细粒度的导航控制
* 带有自动激活的 CSS class 的链接
* HTML5 历史模式或 hash 模式，在 IE9 中自动降级
* 自定义的滚动条行为

## 基础

### 1.动态路由匹配
### 2.嵌套路由
在嵌套的出口中渲染组件，需要在 VueRouter 的参数中使用 children 配置

### 3.编程式的导航
```
router.push(location, onComplete?, onAbort?)

router.replace(location, onComplete?, onAbort?)

router.go(n)

```

### 4.命名路由
### 5.命名视图
### 6.重定向redirect和别名alias
### 7.路由组件传参

### 8.HTML5 History 模式
vue-router **默认 hash 模式** —— 使用 URL 的 hash 来模拟一个完整的 URL，于是当 URL 改变时，页面不会重新加载。如果不想要很丑的 hash，我们可以用路由的 **history 模式**，这种模式充分利用 history.pushState API 来完成 URL 跳转而无须重新加载页面.不过这种模式要玩好，还需要**后台配置支持**。

## 进阶
### 1.导航守卫
* “导航”表示路由正在发生改变。

```
const router = new VueRouter({ ... })

// 全局前置守卫
router.beforeEach((to, from, next) => {
  // to: Route: 即将要进入的目标 路由对象
  // from: Route: 当前导航正要离开的路由
  // next: Function
})
// 全局后置钩子
router.afterEach((to, from) => {
  // ...
})
```
### 2.路由元信息
* 定义路由的时候可以配置 meta 字段

### 3.过渡动效
```
<transition>
  <router-view></router-view>
</transition>
```
### 4.数据获取
* 导航完成之后获取：先完成导航，然后在接下来的组件生命周期钩子中获取数据。在数据获取期间显示“加载中”之类的指示。
* 导航完成之前获取：导航完成前，在路由进入的守卫中获取数据，在数据获取成功后执行导航。

### 5.滚动行为
使用前端路由，当切换到新路由时，想要页面滚到顶部，或者是保持原先的滚动位置，就像重新加载页面那样。 vue-router 能做到，而且更好，它让你可以自定义路由切换时页面如何滚动
**注意: 这个功能只在支持 history.pushState 的浏览器中可用。**
```
const router = new VueRouter({
  routes: [...],
  scrollBehavior (to, from, savedPosition) {
    // return 期望滚动到哪个的位置
  }
})
```
### 6.路由懒加载
结合 Vue 的异步组件和 Webpack 的代码分割功能，轻松实现路由组件的懒加载。