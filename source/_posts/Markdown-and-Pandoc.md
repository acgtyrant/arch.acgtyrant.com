title: 用 Markdown + Pandoc 學術創作
date: 2015-01-19 22:53:47
tags:
- Documents
---
我校堂堂理學院，旗下專業就包括數學系，但不可思議的是校方依然強制指定畢業設計採用 doc 格式。

得了，我先用 [Markdown Pandoc](http://pages.tzengyuxio.me/pandoc/) 排版，後者有不錯的論文用擴展「腳註」，用來生成參考文獻。

![用 Gedit 和 Fcitx-rime 寫 Markdown 太舒服了！](https://lh3.googleusercontent.com/-XLTUdeYt0OI/VL0WrcMgiMI/AAAAAAAAJ7U/Sic_QMl2sJY/s0/DeepinScreenshot20150115214202.png)

之後用 Pandoc 轉換，很好地在 docx 裏實現了代碼高亮。

![](https://lh4.googleusercontent.com/-fEyYNgbofGs/VL0kclKcDnI/AAAAAAAAJ8A/FF9wyai3HDA/s0/DeepinScreenshot20150116162904.png)

不過 Pandoc 本身並不是很完美，也許有時候您需要先轉換成 HTML, 再轉成 docx. 

至於具體到底怎麼轉換，直接看[官方文檔](http://johnmacfarlane.net/pandoc/README.html)即可。在 `-c` 參數裏推薦用 [github.css](https://github.com/sindresorhus/github-markdown-css).

另外，AUR 分別有兩個包 `haskell-pandoc` 和 `pandoc-static`, 安裝前者您就不得不下載並編譯 AUR 裏的一大堆 Haskell 庫，後者則是由 parabolagnulinux.org 官方打包好的二進制包，自然優先安裝後者。


> Written with [StackEdit](https://stackedit.io/).
