---
title: ReactInstanceManager & CatalystInstance & ReactRootView
subTitle: React Native 中几个基本概念的学习
---

## ReactInstanceManager

这个类管理 CatalystInstance 实例。它对外暴露一种通过 ReactPackage 设置 catalyst 实例的方法，并维护 实例的生命周期。它也在实例与框架的开发者支持功能之间建立连接。

启动 ReactRootView 里面的 JS 应用的时候需要 ReactInstanceManager 的实例。

ReactInstanceManager 实例的生命周期应当绑定到拥有 ReactRootView 以展示 React 应用的 Activity 上面。需要将宿主的生命周期事件传递进 ReactInstanceManager 实例。

这个类使用 builder 构建。

## CatalystInstance

是建立在 asynchronous JSC bridge 之上的更高层 API。

提供了一种支持调用 JS 方法的环境，并且允许从 JS 调用 Java API。

## ReactRootView

ReactRootView 是 catalyst 应用的默认根视图。

提供的能力包括监听尺寸变化，这样 UI Manager 可以重新布局元素。

它代理了它自己和子视图的触摸事件，将这些事件通过事件的方式传进 JS，这个通过 JSTouchDispatcher 实现。

就算 ReactRootView 的子视图拦截了触摸事件， 这个事件仍然能进入 ReactRootView。

## catalyst

catalyst 的中文是**催化剂**的意思。