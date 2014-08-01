title: 系統監視器大全
date: 2013-12-27 17:32:32
tags:
- Others
- Linux
---
在下完善了[系統監視器軟件列表][1]，直接查閱即可。

左上、中上、右下、右中、右下依次為 LXTask、GNOME-System-Minotor、Procexp、Proxcexp 的 System Informantion、Procexp 的 Network Information：

![System Monitor 一覽][2]

竊以為，Procexp 比較復古，LXTask 輕量且簡潔、GNOME-System-Monitor 則功能豐富、信息詳細、圖表漂亮。諸位各取所需即可，酷愛 CLI 風格的用戶自然首選經典的 htop 了。

至於在下，htop 看上去夠 hacker 的樣子，但是 kill 程序時終究不夠方便，便改用 lxtask 來執行 kill 了，此外偶爾用 GNOME-System-Monitor 來看圖表也不錯。

PS：很奇怪官方 Repo 為什麼會沒有 KSysGuard 包...

Updated: 感謝 [twitter|xosdy] 補充上相應的 KSysGaurd 包！

  [1]: https://wiki.archlinux.org/index.php/List_of_Applications/Other_%28%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87%29#System_Monitoring
  [2]: https://lh3.googleusercontent.com/-WPE5Qd_ApfA/Ur1CHlKPDqI/AAAAAAAAEn4/DmwLhkqgT9s/s0/2013-12-27-165845_1919x1079_scrot.png
