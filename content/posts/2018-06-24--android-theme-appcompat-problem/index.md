---
title: You need to use a Theme.AppCompat theme (or descendant) with this activity.
subTitle: 一个 Android Support 版本不一致导致的编译错误
category: "Android"
---

今天重新编译一下心动，就爆出了这个问题，还是第一次遇到。

字面意思是我的 MainActivity 设置的主题不对。

上一次编译是没有这个问题的，这一次出现了问题。

看看有哪些改动点，改动地方并不多，比较明显的是导入了 Admob 的 SDK。又联想到工程里面的 Support 库好久没升级了，可能是导入 Admob 时发生了不兼容问题。

将 Support 升级到最新版本后这个问题解决了，确实是版本不兼容导致的。