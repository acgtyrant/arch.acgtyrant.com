title: 快速啓動
date: 2014-09-07 13:38:47
tags:
- Others
---

在下一直御用 i3 官方推薦的 dmenu, 輕快是輕快，但終究**不夠賞心悅目**，而且並不支持**智能排序**、**訪問 URL 或文件**、**Favicon 顯示**等。於是在下調研並翻譯了[「快速啓動」][1]章節，直接查閱即可。

我發現快速啓動大抵可以分類成兩種，一是 dmenu 類，二是 GUI, 由於 dmenu 類本身自然是 CLI, 並不會顯示 Favicon, 這就並不是我理想的快速啓動了. 所以測評重點只在 GUI 類。現在開始一如既往的個人簡評：

### dmenu 類：

ayr. 文檔太複雜，不做具體調研及測評。

Bashrun2. 依賴到 xterm, 看上去很奇怪……

dmenu-launch. 只是一個腳本，我沒興趣研究它強化了 dmenu 什麼。

dswitcher. 貌似只是讓您方便在 workshops 內不同窗口快速切換而已。

j4-dmenu-desktop. 旨在代替 i3 的 dmenu. 不光根據 .desktop 索引以提供了更精確的搜索結果，速度更是比 dmenu 快 25 倍之多，雖然照样局限于 CLI 形式，并不支持 Favicon 显示以及搜索文件。

xboomx & Yeganesh. 均是支持智能排序的 dmenu 而已，不同之處在於前者用 Python 編寫而後者則用 Haskell. 反正我現在已經完全對 dmenu 類快速啓動失去興趣了。

### GUI 類：

![ADeskBar. 與其說它是快速啓動，倒不如說是任務欄……而且不光缺失大量圖標，樣式也不好看，棄。](https://lh5.googleusercontent.com/-veBXLq1KWAM/VAwNA71dYJI/AAAAAAAAGF4/RDJSQqiix4I/s0/2014-09-07-143130_1366x768_scrot.png)

![Fehlstart. GTK+, 自稱比 Gnome-Do 或 Synapse 輕快。支持「啓動程序、智能排序、熱鍵綁定」。但其實樣子仍舊寒酸，又不支持打開文件或 URL, 棄。](https://lh5.googleusercontent.com/-SdEx68fxznc/VAwNKtw2gTI/AAAAAAAAGGM/rsO-A_RhyCM/s0/2014-09-07-142854_1366x768_scrot.png)

![Gmrun. 只相當於 GTK+ dmenu, 就是字面上的意思。和 Gnome Do, Kupfer, Synapse 等相比，太簡陋了，棄。](https://lh3.googleusercontent.com/-97NGrPErcrc/VAwiTv6IFgI/AAAAAAAAGJo/5icyXFenYtY/s0/2014-09-07-171316_1366x768_scrot.png)

![Gnome Do. 雖然基本只有搜索程序的簡單功能，但卻有大量豐富的擴展供您選用；官方主頁也很漂亮；但是我弄了半天也不知怎麼調出設置，棄。](https://lh3.googleusercontent.com/-BBMilP8DBlU/VAwSiVr19aI/AAAAAAAAGHI/TQSmHKvDCyQ/s0/2014-09-07-160603_1366x768_scrot.png)

![Kupfer. 不光長得幾乎和 Gnome Do 一模一樣，也基於插件以擴展。但是，在用戶體驗的細節上卻要比 Gnome-Do 出色得許多！比如右上角就有齒輪標誌，方便用戶直接點擊打開以設置，且設置中又列出了詳細的插件列表，可圈可點！](https://lh5.googleusercontent.com/-KiOhOFjxpdo/VAwStoMqSOI/AAAAAAAAGHc/4VDQE1uh3RU/s0/2014-09-07-160651_1366x768_scrot.png)

![Launchy. 其實我很吃驚我過去在 Windows 上的御用快速啓動原來也有 Linux 版。由於很久沒用過了，現在印象中要比我當初用過的 Windows 版改進了不少。不過 Launchy 在 Linux 上的表現依舊不佳，比如搜 WPS 就沒正確顯示 Favicon, 下拉的菜單也會留下殘影，棄。](https://lh6.googleusercontent.com/-7Cx0QTkGF5U/VAwVcg4j9LI/AAAAAAAAGH8/fQq4--hxtoM/s0/2014-09-07-161818_1366x768_scrot.png)

![Synapse. Felixonmars 御用快速啓動；也是採用了插件機制，不過會自帶對文檔和 URL 的搜索功能。從功能上來說的確算是滿足我的需求了，把主題改成 Virgilio, 我現在很……中意它！此外大家可能注意到了，本文大多快速啓動均爲淺綠色調，大概是因爲我現在用 [Stark-Verd 主題](http://arch.acgtyrant.com/2014/06/17/Moka-Project/)的緣故，不過縱觀下來其它一些 GUI 快速啓動都看上去怪怪的，就唯數這個最賞心悅目。](https://lh3.googleusercontent.com/-1qGBLtJEMxI/VAwZ9xynxxI/AAAAAAAAGIY/gDyK06fmRyk/s0/2014-09-07-163751_1366x768_scrot.png)

**以後……Synapse 就是暴君御用 Linux 快速啓動了！**

> Written with [StackEdit](https://stackedit.io/).

 [1]: https://wiki.archlinux.org/index.php/List_of_Applications/Other_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)#.E5.BF.AB.E9.80.9F.E5.90.AF.E5.8A.A8