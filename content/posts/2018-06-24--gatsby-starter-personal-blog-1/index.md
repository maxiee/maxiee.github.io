---
title: gatsby-starter-personal-blog 初体验
subTitle: 使用 gatsby 搭建了个人博客
cover: gatsby-cover.png 
---

## 介绍

[gatsby-starter-personal-blog](https://github.com/greglobinski/gatsby-starter-personal-blog) 是一个设计精良的 Gatsby 博客主题。

我在给 maxiee.github.io 挑选 Gatsby 博客主题时发现了它，并打算采用它。在本文中我记录了这个对主题的一些使用经验。

## gatsby-plugin-algolia

这个主题通过这个插件接入了一个外部的搜索服务。我不想要这个服务，因此干掉他。

这样做的结果就是搜索功能不可用了。

## 上传到 GitHub

按照官网教程，通过 `gatsby new` 在本地创建了工程，下一步是将它关联到 GitHub 上。

这一步参考文档 [How Gatsby Works with GitHub Pages](https://www.gatsbyjs.org/docs/how-gatsby-works-with-github-pages/)

## Cannot find module '../build/Release/sharp.node'

还遇到一个崩溃问题。Sharp 库是一个 node 的图片处理库。

Github 上有一个 [issue](https://github.com/gatsbyjs/gatsby/issues/4693) 是专门说这个问题的。

解决问题的方式是：

> Had the same error. Deleting node_modules, .cache, public and reinstalling all dependencies fixed it for me.

还真的管用了。。。🕯

## UNHANDLED REJECTION

在 `gatsby-config.js` 第一行添加：

```
const autoprefixer = require('autoprefixer');
```

参考 [issue](https://github.com/gatsbyjs/gatsby-starter-blog/issues/30#issuecomment-372113311)。

对这些错误目前都是知其然不知其所以然的懵逼状态。

## gatsby-plugin-google-analytics

这个是 Google 统计的插件，文档在[这里](https://github.com/gatsbyjs/gatsby/tree/master/packages/gatsby-plugin-google-analytics)。

遇到了一个问题：跟踪没有生效，原因是浏览器有缓存，缓存住了老的代码，新页面代码没有生效。

## react-adsense

项目主页位于[这里](http://git.hust.cc/react-adsense/)。

遇到一点小问题：需要在网页中加入：

```html
<script async src="//pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
```

由于主页的模板是使用 JSX，导入方法为，在 gatsby-ssr.js 中添加：

```js
(function(d) {
    var wfAD = d.createElement('script'), sAD = d.scripts[0];
    wfAD.src = 'https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js';
    wfAD.async = true;
    sAD.parentNode.insertBefore(wfAD, sAD);
})(document);
```