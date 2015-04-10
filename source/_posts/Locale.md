title: Locale
date: 2015-02-10 13:52:00
tags:
- ArchWiki
---

Arch Linux 安装过程重要的环节之一便是设置 [Locale](https://wiki.archlinux.org/index.php/Locale) 了，不翻译。现在恕我直接假设您了解 Locale 机制的原理。

按[曝光效应](http://www.douban.com/group/topic/39675260/)，用母语即中文肯定始终要比英文舒服多，所以我便在 `~/.locale.conf` 设置了 `LANG=zh_CN.UTF-8`, 它比 `/etc/locale.conf` 优先。[其实随时也可以调节 Locale](http://arch.acgtyrant.com/2014/11/30/Enviroment-variables/).

但 root 往往涉及到系统管理，为了安全与调试，还设置为「足够国际的 Locale 变量」好，为此我研究了下以前不甚留意过的两个 Locale 变量：`C` 和 `POSIX`. [现在了解到原来它们就是同一回事](http://unix.stackexchange.com/a/87747)。

那么 `C` 和 `en_US.UTF-8 UTF-8` 哪个更好呢？我一度曾以为，既然 GNU/Linux 本身就几乎是用 C 编写而成，`C` 应该更为适合。但实际上它在编码上就完败给后者，即只支持 ASCII 字符，而且国际上所有程序又不一定全用英语。于是决定在 `/etc/locale.conf` 用 `LANG=en_US.UTF-8 UTF-8` 了.

PS: felixonmars 指出原来还有个 `C.UTF-8` 这奇特的 Locale 变量，[虽然还没广泛普及是了](https://sourceware.org/bugzilla/show_bug.cgi?id=17318)。
