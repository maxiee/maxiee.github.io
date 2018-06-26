---
title: NSURLProtocol & WKURLSchemeHandler 初识
subTitle: 想在 WKWebView 里拦截请求该怎么做呢？
---

## 介绍

NSURLProtocol 对象处理特定协议 URL 数据的加载。

NSURLProtocol 类自己是一个抽象类，提供了处理带有特定 Scheme 的 URL 的基础方法。

开发者为 App 所需要支持的自定义协议或者 URL Scheme 创建子类。

## NSURLProtocol 的抽象方法

canInitWithRequest：

- 这个方法判断 protocol 是否能处理给出的请求

canonicalRequestForRequest：

- 返回给出请求的 canonical version

requestIsCacheEquivalent:toRequest：

- 考虑 Cache 的情况下判断两个请求是否等同

startLoading：

- 请求的正式加载

stopLoading：

- 请求停止加载

## NSURLProtocol 与 WKWebView 结合

通过网上的文档了解到，在之前（iOS 10 之前），WKWebView 想要使用 NSURLProtocol 做拦截是不容易的，需要通过反射访问私有 API。

iOS 提供了 WKURLSchemeHandler，这个问题迎刃而解。

具体使用可以参考[Intercepting UIWebView & WKWebView — Custom URL Scheme handling](https://medium.com/@kumarreddy_b/custom-scheme-handling-in-uiwebview-wkwebview-bbeb2f3f6cc1)。

我想做的事也能够实现了。