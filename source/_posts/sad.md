title: 鬱悶
date: 2013-11-12 22:17:17
tags:
- 其它
---
對 Arch Linux Chinese User 失望透頂，其實在下從來不看好國內任何中文 Web 2.0 社區。由於 Arch Linux Chinese Community 應該多多少少有貫徹 FOSS 精神，但把信賴寄託與前者的在下，到頭來還只不過在一廂情願罷了。

很早曾在 Arch Linux Chinese Community Mailing List 活躍過。

先是 [诸位不妨来试试导入CA.crt进系统看看？][1]。第一回覆者 GSC 馬上就犯中國用戶常見的毛病：歪題 ；第二回覆者 Felix Yan 只給出了一段高深莫測的代碼，就不再回應，但當時那代碼大概仍不奏效；再也沒有其他回覆了。後來，在下只好重裝了系統並再導入證書，實驗總算才順利結束。並親自創建完成了 wiki 上的[『GoAgent』][2]條目。

但還有棘手的『銳捷』撥號機制，後者是中國各大高校普遍採用的學生寢室網絡解決方案，但對 Linux 用戶非常不友好，且我校採用了更刁難的額外『二次撥號』方案，即銳捷撥號只會撥號到校園內網，要訪問互聯網，還得鏈接 L2TP 到運營商，才能訪問外網。當初在下9月開學以來折騰了大半月，才得以解決掉令人頭痛的銳捷+二次撥號機制。並完善了[『MentoHUST』條目][3]，但是有個別細節沒法獨立解決，特地發[郵件][4]求助。

No help.算了，在下無能為力完善『MentoHUST』的『二次撥號』章節了。

大概在其間，由於 Arch Linux Chinese Mailing List 管理情況如此糟糕，在下感到有必要挺身而出，找 Phoenixlzx 商量了下，結果算是領略到他的臭脾氣了：

![硬把疑問句當成肯定句，這不叫情緒化叫什麼？][5]

事後，在下感到申請管理員的時機仍尚未成熟，所以並沒有採取行動。但久而久之，愈發真覺得這郵件列表荒廢到真無藥可救了，便撒手不管。

接著投靠到 Arch Linux Chinese IRC 來。

不久，與 Phoenix 發起了一次衝突。其實在下早隱隱約約感覺到他品格有問題，經過這事件，算是正式決裂了，並決定不再接觸與 Phoenix 有關的一切事物，包括他所管理的 Arch Linux Chinese BSS。好在 IRC 並非由他所支配，否則在下只能又離開了。

近期，GoAgent 開始了一些列高強度升級，改得亂七八糟，各種失靈，害得在下只好不停地按自己所親自撰寫的『GoAgent』條目，重裝，再配置起來。不過 systemctl 莫名失效了，只好手動運行起來，但在下驚奇地發現，所用的 Python 版本不再支持 3，而是 2！據依雲醬說，GoAgent 作者的確當時支持 Python 3，但是改壞了，於是很快又改回 Python2.

在下感到很奇怪，條目上這麼明確的錯誤，為什麼一直沒被糾正？有一種可能：沒人看（悲從中來

世態炎涼，人情冷暖，算是充分體會到[瑪麗格蘇的鬱悶之情][6]了。現在考慮嘗試 OpenSUSE 發行版，畢竟在下有約定要分擔瑪麗格蘇的辛苦。當然，敝博在下還是會繼續維護的，畢竟好歹也能給自己一人以及僅有的好夥伴們看看。


  [1]: https://groups.google.com/forum/#!topic/archlinux-cn/_PPW2dZHltE
  [2]: https://wiki.archlinux.org/index.php/Goagent_%28%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87%29
  [3]: https://wiki.archlinux.org/index.php/MentoHUST_%28%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87%29
  [4]: https://groups.google.com/forum/#!topic/archlinux-cn/C6m6B7HU-d8
  [5]: https://lh5.googleusercontent.com/-rJHPRcdET3I/Uhb4Xbq9-0I/AAAAAAAADZY/pKWKdMXPjG8/s0/Phoenix+Nemo+-+Google%252B+-+%255Barchlinux-cn%255D+%25E5%2588%2597%25E8%25A1%25A8%25E9%2587%258C%25E6%259C%2589%25E5%2587%25A0%25E4%25B8%25AA%25E5%25AE%25B6%25E4%25BC%2599%25E5%2590%25B5%25E6%25AD%25BB%25E4%25BA%2586....png
  [6]: https://forum.suse.org.cn/viewtopic.php?p=8735#p8735
