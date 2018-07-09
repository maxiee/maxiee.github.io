---
title: 多台设备统一管理终端配置
subTitle: 平时我需要使用多台设备，每台设备都有各自的 terminal，因此我需要对它们的设置文件进行统一管理。
---

## 介绍

平时我需要使用多台设备，每台设备都有各自的 terminal，因此我需要对它们的设置文件进行统一管理。

## Git 仓库

首先需要建一个 Git 仓库。我使用 GitLab 建了一个私有仓库。

## 使用哪个配置文件

最终我选择使用 `.bash_profile`。

## 系统判断

不同的系统有一些特定的设置。如何进行判断呢？'

通过 [How to detect the OS from a Bash script?](https://stackoverflow.com/questions/394230/how-to-detect-the-os-from-a-bash-script)，得到以下代码：

```bash
if [[ "$OSTYPE" == "linux-gnu" ]]; then
        # ...
elif [[ "$OSTYPE" == "darwin"* ]]; then
        # Mac OSX
elif [[ "$OSTYPE" == "cygwin" ]]; then
        # POSIX compatibility layer and Linux environment emulation for Windows
elif [[ "$OSTYPE" == "msys" ]]; then
        # Lightweight shell and GNU utilities compiled for Windows (part of MinGW)
elif [[ "$OSTYPE" == "win32" ]]; then
        # I'm not sure this can happen.
elif [[ "$OSTYPE" == "freebsd"* ]]; then
        # ...
else
        # Unknown.
fi
```

这个能满足我的需要。我有三个主要的平台：

- Linux：linux-gnu
- Termux：linux-android
- macOS：darwin17.0

这样共性和特性的都解决了。

## 配置文件编写

`.bash_profile` 的具体编写根据自己需要来写。

## Emacs 配置

Emacs 是我在 terminal 下常用的编辑器，因此它的配置也需要同步。

Emacs 遇到一个问题，就是安装的包怎么做到多设备同步？不能说每次一个新设备，都要手动打开 Emacs 一个个把它们装回来，那就太累了。

我希望的是，第一次打开 Emacs 的时候，它能够自动上 Melpa 上面下载缺少的包。

通过 [What's the best way to sync emacs settings between machines?](https://www.reddit.com/r/emacs/comments/3nm0cf/whats_the_best_way_to_sync_emacs_settings_between/) 这一篇，我学习到 [use-package](https://github.com/jwiegley/use-package) 这个插件，能够满足我的要求。

## 链接脚本

Git 仓库中的配置脚本都写好后，下面要写链接脚本。

每次在新设备上，只要执行一次链接脚本，就能自动配置完成。

主要参考一下脚本：

```bash
#! /bin/sh

SCRIPT_DIR=`pwd`

declare -a FILES=(
    ".bash_profile"
    ".emacs"
)

echo "Goto home $HOME"
cd $HOME

for FILE in "${FILES[@]}"; do
    f="$SCRIPT_DIR/$FILE"
    echo "File = $f"
    ln -s $f
done

echo "Install Finish"
```

参考来源：[Managing user configuration files across multiple computers](https://stackoverflow.com/questions/1413049/managing-user-configuration-files-across-multiple-computers)


## 参考文献

[bash config multiple computers site:superuser.com](https://www.google.com/search?q=bash+config+multiple+computers+site:superuser.com&sa=X&ved=0ahUKEwizq4iukZHcAhWJM94KHURdDv0QrQIIMygDMAA&biw=1080&bih=761)

[bash config multiple computers site:stackoverflow.com](https://www.google.com/search?q=bash+config+multiple+computers+site:stackoverflow.com&sa=X&ved=0ahUKEwizq4iukZHcAhWJM94KHURdDv0QrQIIQygEMAE&biw=1080&bih=761)

[Managing user configuration files across multiple computers](https://stackoverflow.com/questions/1413049/managing-user-configuration-files-across-multiple-computers)

[Mac OS X 配置环境变量](https://www.cnblogs.com/caowei/p/mac-path_2013-08-26.html)

[Mac OS X 系统的环境变量配置](http://yifeng.studio/2016/11/08/mac-environment-variables-configration/)

[How to detect the OS from a Bash script?](https://stackoverflow.com/questions/394230/how-to-detect-the-os-from-a-bash-script)

[What's the best way to sync emacs settings between machines?](https://www.reddit.com/r/emacs/comments/3nm0cf/whats_the_best_way_to_sync_emacs_settings_between/)