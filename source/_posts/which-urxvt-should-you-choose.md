title: 有好多好多 urxvt，怎麼選呢？
date: 2013-12-13 19:55:02
tags:
- Others
---
[wiki|rxvt-unicode] 是御用 Terminal Emulator，相當輕便快捷。

但若嘗試直接搜索 [Pkg|rxvt-unicode] or [AUR|rxvt-unicode] 的話，您會發現搜索結果還真不少，五花八門，眼花繚亂，豐富多樣，應有盡有。恐怕就不知從哪包安裝起。且慢！不妨聽在下娓娓道來：

[Pkg|rxvt-unicode]：ArchWiki 首推，但有兩點地方要注意：其一，其實**源代碼的編譯選項默認關閉 256-color flag**，即 256色支持，但 Arch Linux 打包者已貼心地自行開啓其 flag，所以安裝好時**就已經直接支持 256色了**；其二，但源程序有一種存在了好多年的 BUG：**字體過寬**。但據說開發者不承認並拒絕修正，於是**該包依然延續了這 BUG 傳統**。

![字體過寬][1]

[Pkg|rxvt-unicode-terminfo]：與 [Pkg|rxvt-unicode] 彼此獨立，**且爲後者增添了 terminfo**，比如，能夠在其終端下查詢到正確的 $TERM（大概？

[Pkg|urxvt-perls]：同樣與 [Pkg|rxvt-unicode] 不衝突，且讓後者支持 **selection & URL 跳轉**等功能。

[AUR|urxvt-tabbedex]：TAB 功能增強版 urxvt（大概？但竊以為用 [wiki|tmux] 來彌補已足夠矣。

[AUR|rxvt-unicode-better-wheel-scrolling]：**支持 [VTE-Like 式鼠標滾動瀏覽][2]的 urxvt**（雖然在下不太清楚 VTE-Like 是啥。256-color 支持情況不明。

[AUR|rxvt-unicode-chinese]：已修正字體過寬 BUG的 urxvt。特別地，打包者申明了該包**是針對中文字體而優化的**。256-color 支持情況不明。

[AUR|rxvt-unicode-256xresources]：**其 urxvt 不光修正字體 BUG，還開啓了  256-color flag。**所以若您在已安裝 [Pkg|rxvt-unicode] 且只想解決其字體 BUG 時，直接**改安裝其包**可。

[AUR|rxvt-unicode-patched]：同修正字體過寬 BUG 的 urxvt，且支持 256-color。

[AUR|rxvt-unicode-multi_display-256xresources]：在 [AUR|rxvt-unicode-256xresources] 的基礎上，**又追加了 [secondary scroll][3] 補丁，即支持在 `man`、`less` 等進行鼠標滾動瀏覽。**

PS：可惜由於不明原因，secondary scroll 補丁於我 tmux 尚未成功生效，而[據作者測試卻表現正常][4]，期望能有其它用戶反饋下。

其實 AUR 還有其他大大小小的改造版 urxvt 及補丁，不過就不再一一介紹了。個人建議直接用 [AUR|rxvt-unicode-multi_display-256xresources] 代替 [Pkg|rxvt-unicode] 即可（重點一開始就說不好了嗎喂！

![字體 BUG 修正效果圖][5]


  [1]: https://lh3.googleusercontent.com/-tezlCku1MWg/UnjCeTIJ4tI/AAAAAAAAESk/LRYi3-gM-2A/s0/2013-11-05-180251_881x312_scrot.png "字體過寬"
  [2]: http://lists.schmorp.de/pipermail/rxvt-unicode/2011q4/001491.html
  [3]: http://lists.schmorp.de/pipermail/rxvt-unicode/2011q4/001491.html
  [4]: https://aur.archlinux.org/packages/rxvt-unicode-multi_display-256xresources/?comments=all
  [5]: https://lh6.googleusercontent.com/-gsswNVsykik/UnjUYtlry_I/AAAAAAAAETQ/87gmCwMP_4w/s0/2013-11-05-191849_671x253_scrot.png "字體 BUG 修正效果圖"
