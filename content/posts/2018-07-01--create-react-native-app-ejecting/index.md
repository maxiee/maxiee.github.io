---
title: Ejecting of Create React Native App
subTitle: 将 Expo 项目恢复为普通项目
---

CRNA 默认跟 Expo 绑定在一起的, 这个东西练习的时候好用, 发布的时候还是想用自己的.

CRNA 支持去除内置的 Expo, 这个过程叫 Eject. 去除过程是不可逆的, 就算用 git 托管, 这个过程也是不可逆的.

*有没有办法在创建项目时就创建 Eject 的?*

首先执行 eject 指令:

```
npm run eject
```

`npm run eject` will start the process of ejecting from Create React Native App's build scripts. You'll be asked a couple of questions about how you'd like to build your project. Once this command has successfully run, you should also follow any steps below that are applicable to your environment.

问了我三个问题:

- 向改用哪种方式? 我选择了 React Native 传统的
- 在屏幕上叫什么? 输入一个名字
- iOS 和 Android 的工程叫什么? 输入一个名字

然后就开始重新安装依赖了.

之后就能看到 Android 和 iOS 工程都被创建出来了.