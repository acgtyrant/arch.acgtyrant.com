title: Compton
date: 2015-03-05 20:24:46
tags:
- ArchWiki
- Linux
---
我曾经一度很困惑：明明是同一个 GTK+ 主题，GNOME 下那些程序的边角为啥就那么圆润？直到有一天得知，那些华丽的「桌面效果」原来就是靠 Composite Windows Manager 实现的。而且虽说是个 "Windows Manager", 但可以与 i3 彼此同时且独立地运行，毕竟前者只负责渲染部分图形效果，其他自然继续全由 i3 处理。

最大名鼎鼎的 Composite Windows Manager 大概要就数 Compiz 了，遥想当年入 Ubuntu 门时，所阅读教程的章节之一便是用它来美化桌面。酷归酷，当时怕连同系统也玩坏，便没再仔细研究过了。

如今 Compiz 似乎已经停止维护了，万分可惜。好在我们有 [Compton](https://wiki.archlinux.org/index.php/Compton), 而且它是 xcompmgr-dana 的 fork, 更也是 xcompmgr 的 fork 的 fork, 按奥卡姆剃刀法则，应该优先用最「新」的 Compton.

于是我只要在 i3 的 config 加上一句 `exec --no-startup-id compton -b -c`, 就可以让所有 GTK+ 程序如此赏心悦目了：

![Fcitx-rime](https://lh5.googleusercontent.com/-DjQKHAcrOrY/VPhJ167ZYHI/AAAAAAAAKAQ/xAu6wyVrOxo/s0/2015-03-05-201838_1360x766_scrot.png)

![窗口式 Dota 2, 估计 Windows 就没法做到](https://lh3.googleusercontent.com/-1wfTxV5rMqo/VPhJ9pTc7kI/AAAAAAAAKAk/cnjeEK3WGYk/s0/2015-03-05-123114_1916x1079_scrot.png)

![Gedit](https://lh5.googleusercontent.com/-j_iOl3jvNT4/VPhKKsDGHoI/AAAAAAAAKA4/hKZkAeNPCak/s0/2015-03-05-170636_1135x937_scrot.png)

此外，[据说 Composite Windows Manager 会影响游戏的流畅度][1]，但我实际测试了下，发现无论开不开 Compton, 对 Dota 2 的 FPS 影响都几乎微乎其微。据说还是因为 Compton 对 OpenGL 优化好的缘故。

[1]: http://en.wikipedia.org/wiki/Mutter_(software)#Performance


> Written with [StackEdit](https://stackedit.io/).
