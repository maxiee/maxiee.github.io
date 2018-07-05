---
title: 使用 Emacs 的 rjsx-mode 进行 React 开发
subTitle: 对 JSX 高亮和补全的支持
---

A JSX major mode for Emacs，[项目主页](https://github.com/felipeochoa/rjsx-mode)。

通过 melpa 安装，包名为 `rjsx-mode`。

`rjsx-mode` 插件会自动与 `.jsx` 后缀的文件相关联。通过一下配置进行更大范围的文件关联：

```
(add-to-list 'auto-mode-alist '("components\\/.*\\.js\\'" . rjsx-mode))
```

如何手动启动？

```
M-x rjsx-mode
```

如何判断 `rjsx-mode` 是否启动?

这个插件的 Feature 都能用了（高亮、补全），就说明启用成功了，哈哈。