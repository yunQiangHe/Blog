---
title: vuex
date: 2019-03-28 22:34:06
categories: Vue
tags:
description: Vuex 是一个专为 Vue.js 应用程序开发的状态管理模式。它采用集中式存储管理应用的所有组件的状态，并以相应的规则保证状态以一种可预测的方式发生变化。Vuex 也集成到 Vue 的官方调试工具 devtools extension，提供了诸如零配置的 time-travel 调试、状态快照导入导出等高级调试功能。
---
[Vuex](https://vuex.vuejs.org/zh/)
## vuex

* 一个 Vuex 应用的核心是 store（仓库，一个容器），store包含着你的应用中大部分的**状态 (state)**。

* 每一个 Vuex 应用的核心就是 **store（仓库）**。“store”基本上就是一个容器，它包含着你的应用中大部分的状态 (state)。Vuex 和单纯的全局对象有以下两点不同：

1. **Vuex 的状态存储是响应式的**。当 Vue 组件从 store 中读取状态的时候，若 store 中的状态发生变化，那么相应的组件也会相应地得到高效更新。

2. 你不能直接改变 store 中的状态。**改变 store 中的状态的唯一途径就是显式地提交 (commit) mutation**。这样使得我们可以方便地跟踪每一个状态的变化，从而让我们能够实现一些工具帮助我们更好地了解我们的应用。

## 核心概念
1. State
* Vuex 使用单一状态树——是的，用一个对象就包含了全部的应用层级状态。

* mapState辅助函数 当一个组件需要获取多个状态时候，将这些状态都声明为计算属性会有些重复和冗余。为了解决这个问题，我们可以使用 mapState 辅助函数帮助我们生成计算属性
* **对象展开运算符**
```bash
mapState 函数返回的是一个对象。我们如何将它与局部计算属性混合使用呢？
通常，我们需要使用一个工具函数将多个对象合并为一个，
以使我们可以将最终对象传给 computed 属性。
computed: {
  localComputed () { /* ... */ },
  // 使用对象展开运算符将此对象混入到外部对象中
  ...mapState({
    // ...
  })
}
```
2. Getter
* 有时候我们需要从 store 中的 state 中派生出一些状态 
* 通过属性访问
* 通过方法访问
* mapGetters 辅助函数

3. Mutations
> 更改 Vuex 的 store 中的状态的唯一方法是提交 mutation。Vuex 中的 mutation 非常类似于事件：每个 mutation 都有一个字符串的 **事件类型 (type)** 和 一个 **回调函数 (handler)**。这个回调函数就是我们实际进行状态更改的地方，并且它会接受 state 作为第一个参数
```bash
const store = new Vuex.Store({
  state: {
    count: 1
  },
  mutations: {
    increment (state) {
      // 变更状态
      state.count++
    }
  }
})
“当触发一个类型为 increment 的 mutation 时，调用此函数。
”要唤醒一个 mutation handler，
你需要以相应的 type 调用 store.commit 方法：
store.commit('increment')
```
* **提交载荷（Payload）**你可以向 store.commit **传入额外的参数**，即 mutation 的 载荷（payload）
```
mutations: {
  increment (state, payload) {
    state.count += payload.amount
  }
}
在大多数情况下，载荷应该是一个对象
store.commit('increment', {
  amount: 10
})
```
* 对象风格的提交方式
* 使用常量替代 mutation 事件类型在各种 Flux 实现中是很常见的模式.
* Mutation 必须是同步函数

4. Action
* Action 类似于 mutation，不同在于：
  1. Action 提交的是 mutation，而不是直接变更状态。
  2. Action 可以包含任意异步操作。
```
const store = new Vuex.Store({
  state: {
    count: 0
  },
  mutations: {
    increment (state) {
      state.count++
    }
  },
  actions: {
    increment (context) {
      context.commit('increment')
    }
  }
})
```
Action 函数接受一个与 store 实例具有相同方法和属性的 context 对象，因此你可以调用 context.commit 提交一个 mutation，或者通过 context.state 和 context.getters 来获取 state 和 getters。当我们在之后介绍到 Modules 时，你就知道 context 对象为什么不是 store 实例本身了。

* 分发 Action
Action 通过 store.dispatch 方法触发：store.dispatch('increment')
来看一个更加实际的购物车示例，涉及到调用异步 API 和分发多重 mutation
**Action 通常是异步的，那么如何知道 action 什么时候结束呢？**
**更重要的是，我们如何才能组合多个 action，以处理更加复杂的异步流程？**

5. Module
* Vuex 允许我们将 store 分割成模块（module）。每个模块拥有自己的 state、mutation、action、getter、甚至是嵌套子模块

## 项目结构
```
├── index.html
├── main.js
├── api
│   └── ... # 抽取出API请求
├── components
│   ├── App.vue
│   └── ...
└── store
    ├── index.js          # 我们组装模块并导出 store 的地方
    ├── actions.js        # 根级别的 action
    ├── mutations.js      # 根级别的 mutation
    └── modules
        ├── cart.js       # 购物车模块
        └── products.js   # 产品模块
```

* Vuex 并不限制你的代码结构。但是，它规定了一些需要遵守的规则：

1. 应用层级的状态应该集中到单个 store 对象中。
2. 提交 mutation 是更改状态的唯一方法，并且这个过程是同步的。
3. 异步逻辑都应该封装到 action 里面。

## 插件
Vuex 的 store 接受 plugins 选项，这个选项暴露出每次 mutation 的钩子。Vuex 插件就是一个函数，它接收 store 作为唯一参数

## 严格模式
在严格模式下，无论何时发生了状态变更且不是由 mutation 函数引起的，将会抛出错误。这能保证所有的状态变更都能被调试工具跟踪到。

## 表单处理
当在严格模式中使用 Vuex 时，在属于 Vuex 的 state 上使用 v-model 会比较棘手