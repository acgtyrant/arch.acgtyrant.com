title: 如何让 Dota 2 for Linux 正常显示中文
date: 2015-02-05 19:12:29
tags:
- Game
---

很久以前，我 Arch Linux 上的 Dota 2 能正常显示中文过，不过后来又莫名失效。且长期观察下来，我猜 Dota 2 for Linux 会自动按一定规则调用某字体。若该字体不支持中文，则 Dota 2 部分文字会变成方块，比如比赛中的玩家 ID, Loading 提示等。

既然规则尚不明朗，就只能把 Arch Linux 已安装字体控制到最少程度了，好让 Dota 2 调用上支持中文的字体。前天一次重装中，Chromium 的 ttf-fonts 依赖有很多字体可选，包括：

1. ttf-dejavu
2. ttf-freefont
3. ttf-liberation
4. ttf-bitstream-vera
5. ttf-linux-libertine
6. ttf-droid
7. ttf-ubuntu-font-family
8. ttf-oxygen

这次，我心血来潮地选 `ttf-ubuntu-font-family`, 其后又主动安装了 `otf-hermit`, `wqy-zenhei`, `wqy-microhei`. 这应该就是我 Arch Linux 上仅有的所有字体，于是 Dota 2 终于又能正常显示所有中文了。

![多谢字体专家 \[Twitter|shota_nuke\] 指出这是文泉驿正黑。](https://lh4.googleusercontent.com/-qN9wYXlT5tE/VNNcTWknjhI/AAAAAAAAJ90/JCHzAt9xhTI/s0/ScreenShot.png)

当然不排除将来安装其他软件包时，夹带性地安装进新字体。您只能小心翼翼地检查所安装软件包有什么字体依赖，其字体又是否会影响 Dota 2. 据我所知，`ttf-dejavu` 就会害得字体变方框，直接在 `pacman.conf` 里的 `IgnorePkg` 加上它即可。
