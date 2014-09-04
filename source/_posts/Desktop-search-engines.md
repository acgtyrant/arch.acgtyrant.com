title: Desktop search engines
date: 2014-08-22 14:03:36
tags:
- Utilities
---

Linux 上有不少查找命令：find, locate, whereis, which, type. 後三者在某特定情境還挺有用，但若用前兩者來常規搜索，用是能用，但終究不如 GUI 方便，Windows 下著名的搜索工具 Everything 就有 CLI 所不具備的優勢：

1. 所見即所得，即即時搜索。find 卻輸出又長又臭的檢索歷史，如果搜索結果數量不少，您還得手動把它 pipe 進一個 pager, 比如 `find / -name "log" | less`.
2. 搜索結果列表又詳又細。
2. 可回車或點擊直接打開文件。在 CLI 下，您還大費周章地輸入路徑名，跳轉，再打開文件。
3. 簡單快捷，直接輸入檢索關鍵詞就行了，但用 find 命令，免不了一些繁瑣的參數。
4. 其實 Everything 搜索如此之快，原理於 locate 差不多一致，即建立索引數據庫，但前者能靜默更新，不像後者還要手動執行。

所以在下便找了一些 Everything Althernatives for Linux 並完善「[桌面搜索引擎][1]」章節，直接查閱即可。

一如既往的个人评测惯例：

![Recoll: Qt 界面，丑，棄。][2]

![gnome-search-tool: 大抵最漂亮，不支持擴展名篩選。][3]

![DocFetcher: 不知道怎麼建立索引，棄。][4]

![Catfile: 界面也相當美觀，推薦][5]

![Searchmonkey: 兩年沒更新，界面一般，棄。][6]

tracker: 異常地複雜，光相關命令就有九條多；它大概是給其它桌面搜索引擎提供接口;也不知怎麼更新 Index, 棄。

> Written with [StackEdit](https://stackedit.io/).


  [1]: https://wiki.archlinux.org/index.php/List_of_Applications/Utilities_%28%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87%29#.E6.A1.8C.E9.9D.A2.E6.90.9C.E7.B4.A2.E5.BC.95.E6.93.8E
  [2]: https://lh4.googleusercontent.com/-MbGzDkg6iZ0/U_1h3N5qC7I/AAAAAAAAGDA/iAKidvuq2rw/s0/2014-08-22-140807_1365x765_scrot.png
  [3]: https://lh4.googleusercontent.com/-efJ8ec92eyo/U_1iE307EeI/AAAAAAAAGDU/pMa-l5ULmvY/s0/2014-08-22-140740_1365x764_scrot.png
  [4]: https://lh5.googleusercontent.com/-tBNLl7OKUJE/U_1iU2QYW7I/AAAAAAAAGDo/xhV9ejdpk9I/s0/2014-08-22-140547_1365x766_scrot.png
  [5]: https://lh4.googleusercontent.com/-q854aReEN5c/U_1i6ongOnI/AAAAAAAAGD8/hVbLeqImngU/s0/2014-08-22-140453_1365x771_scrot.png
  [6]: https://lh6.googleusercontent.com/-DobB_U7fbYU/U_1jT0wlUJI/AAAAAAAAGEY/OWs8Ik_Ko4c/s0/2014-08-27-124715_1919x1078_scrot.png