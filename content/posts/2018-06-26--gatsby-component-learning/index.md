---
title: Gatsby Component
subTitle: Gatsby Component 学习笔记
cover: gatsby-cover.png
---

## 前言

本文是对官方[Building with Components](https://www.gatsbyjs.org/docs/building-with-components/)的学习笔记。

Gatsby 是基于 React，本身也采用了 React Component 的概念，这也是我为什么选它作为博客框架的原因。

文档中有一句话说明 Gatsby 与 React 的关系：

> Everything in Gatsby is built using components.

## Page Component

位于 `src/pages` 目录下的组件会自动变成以文件名为路径的页面。

例如：

- `src/pages/index.jsx` 自动映射到 `yoursite.com`
- `src/pages/about.jsx` 自动映射到 `yoursite.com/about/`

其中，每个 js、jsx 文件都必须包含一个 React Component，否则会构建失败。

## Page template components

`src/templates/` 下存放模板页面。

模板页面会通过 GraphQL 检索 markdown 数据，并进行展示。

## Layout Component

`src/layouts/index.jsx` 封装 Page Component。通过它来共享 Headers 和 Footers。

通过 `location` props 来判断是不是首页。

## HTML Component

`src/html.jsx` 负责 `<body />` 以外的内容。