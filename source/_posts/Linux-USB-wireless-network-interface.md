title: Linux 用外置 USB 網卡
date: 2014-10-22 23:49:24
tags:
---
我新買的 ThinkPad E540 的無線網卡在 Linux 下工作表現很差，連公共無線網老是掉；而且 [create_ap](https://github.com/oblique/create_ap) 調用內置無線網卡接口時，遇到了一旦設置密碼，Android 終端會連不上的[奇怪 bug,](https://github.com/oblique/create_ap/issues/23) 我只好一直開個不加密的無線網。

我聽說有 USB 無線網卡這麼一個存在，[V2EX 上也對此討論過](http://www.v2ex.com/t/16812)，於是我買了一張 USB 無線網卡，而且 `wifi-menu` 命令調用其它網卡接口也意外地方便：當有兩個無線網卡接口時，需要在命令後加上一個無線網卡接口名參數，就像我執行 `sudo wifi-menu wlp0s20u6` 一樣。於是問題解決了。


> Written with [StackEdit](https://stackedit.io/).