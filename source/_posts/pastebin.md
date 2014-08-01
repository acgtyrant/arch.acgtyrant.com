title: 『網絡剪貼板』-往网上扔文本和图片啦！
date: 2014-01-04 15:28:15
tags:
- Internet
- Linux
---
『網路剪貼板』經常被用來上傳必要的資訊，以方便使用者在 IRC 頻道向他人求助。目前『網路剪貼簿』服務均支援文字 (e.g. sprunge.org, pastie.org, codepad.org) 和圖片 (e.g. imgur.com, picpaste.com)『網路剪貼簿』客戶端大多允許您直接通過 CLI 上傳，無需依靠網路瀏覽器。

而 **IRC 場所鼓勵用戶使用『網絡剪貼板』來傳達大段文本**，比如源代碼、錯誤信息等，而不是粘貼多行影響到大家。此外網絡剪貼板畢竟也是傳圖的極少數有效途徑之一。

至於具體的客戶端及用法，直接誒查詢 ArchWiki 上的[『網絡剪貼板』][1]條目即可。

個人推薦用 [Pkg|wgetpaste]、[Pkg|imgur] 來分別上傳文本和圖片。其實竊以爲，若要上傳圖片，最好還是**通過 GUI 來操作**，畢竟圖片名比較難以識別，需要直接預覽圖片以方便快速篩選。可惜就目前來看只有一家不怎麼快捷的 [zscreen][2]。

[Pkg|gist] 也挺不賴，**畢竟可隨時再編輯，設置 Private，表明 Gist 創建者的身份，甚至提供了可評論機制等等。**如果您是職業程序員的話，那麼它應當是首選。

此外，[twitter|lilydjwg] 也提供了供 Vim-cn & ArchLinux-cn 全體用戶享用的網絡剪貼板服務，均支持[文本][3]和[圖片][4] ，感謝他的分享！就是 curl 命令麻煩了點，[twitter|m13253] 提供了改良的[腳本命令][5]。


  [1]: https://wiki.archlinux.org/index.php/List_of_Applications/Internet_%28%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87%29#.E7.B2.98.E8.B4.B4.E5.91.BD.E4.BB.A4.E5.AE.A2.E6.88.B7.E7.AB.AF
  [2]: https://aur.archlinux.org/packages/zscreen/
  [3]: http://p.vim-cn.com/
  [4]: http://img.vim-cn.com/
  [5]: http://p.vim-cn.com/cbnf/bash
