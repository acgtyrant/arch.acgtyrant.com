title: 一次 IRC 搜索引發的調研
date: 2014-08-11 19:57:33
tags:
---

[Stark-Ceru 下的 Pidgin 好看是好看][1]，但畢竟常年只登錄 IRC, 用不到其它即時聊天協議和軟件，所以在下便決定改用某家專於 IRC 協議的應用軟件，以進一步提升用戶體驗，再順便溫習溫習下 IRC 使用方法，畢竟我不知如何設置 Away 消息，如何管理 Channel, 如何使用 `/me` 命令等等。

[Arch Linux 首頁][2]的導引很簡單，就 Home, Packages, Forums, Wiki, Bugs, AUR, Download 這七塊而已，所謂的「資料指南手冊」自然全集中在 Wiki 板塊里了。但是，ArchWiki 全無 IRC 的使用教程！在下只發現 [IRC channels 列表][3]以及 [List of applications 的 IRC clients 章節][4]，也就是說 **Arch Linux 用戶並不需要官方來教他怎麼用 IRC!**  所以在下便直接開始一一試用後者所列出的所有 IRC 客戶端，只不過 IRC 使用教程還得自行尋找，於是在下也就順便調研下其它 Linux 發行版了，看看它們會怎麼讓用戶使用乃至掌握 IRC. 下面會開始談談個人體會，如有誤解，恕請指正。

[openSUSE:IRC for newbies][5] 直接讓新用戶去 webchat.freenode.net 註冊，在告知最爲權威的 irchelp.org 網站後，後文就直接指定 Xchat 並展開使用教程了，完全忽略了其它 IRC Client 的存在；其界面有中文語言，還可以進一步指定「大陸簡體／臺灣正體」；openSUSE wiki 界面與 ArchWiki 有點像，我猜前者也基於 MediaWiki; #openSUSE-cn 頻道基本不活躍，從來沒見到瑪格麗特的身影；去 #openSUSE-tw 瞄了一眼，貌似只有兩個活人和兩個機器人和我。

fedora 的 [How to use IRC 頁面][6]同樣直接指定 X-chat;  不過好歹也[提及了其它 IRC Client 的存在][7]；有[視頻][8]噢；沒有中文翻譯；#fedora-zh 頻道里我認出了用 Arch Linux 的五個老面孔（咦？

其實最讓我驚歎的要數 Ubuntu 了，**它的社區好龐大且完善**！且聽我道來。

從 http://community.ubuntu.com/contribute/support/irc/ 頁面就可以看出，官方首頁第二板塊就是 Comminity, Support 板塊又進一步細分爲 Mailing lists, Ask Ubuntu, Ubuntu Forums, IRC, Launchpad Answers.

官方對 IRC Supporter 的規定在我看來相當嚴苛，比如

> Don't use LMGTFY, or tell users to RTFM
>
> Do point out/remind about the existance of the 'man' command
>
> Don't read out google results to people

習慣了 The Arch Way 的用戶肯定會對此嘖嘖稱奇，Ubuntu 不愧是 User-Friendly 發行版！

我又進一步研究了下 Ubuntu 官方及社區：

https://help.ubuntu.com/ 旗下有三個板塊：

1. Official Documentation
2. Community Help Wiki
3. Contribute

其中 [Official Documentation][9] 便是首頁，又以版本爲依據，分爲：

1. Ubuntu 14.04 LTS
2. Ubuntu 12.04 LTS
3. Ubuntu 10.04 LTS
4. The current Stable release
5. The current Long Term Support (LTS) release

再次，[Documentation for Ubuntu 14.04 LTS][10] 又進一步細分爲：

1. Ubuntu Desktop Help
2. Ubuntu Server Guide (PDF version)
3. Installing Ubuntu (Only published in U.S. English)

點開前兩者，很意外地發現它們大概依據當前 IP, 自動顯示成中文了，且基本做到了空格緩衝，雖然 Server Guide 還是有些章節並沒翻譯好。**不過 Ubuntu 官方文檔质量之上乘，想必大家有目共睹了吧。**

再看看 Community Help Wiki, 自然便是由來自 Community 民間的大家共同維護了；索引挺棒；但奇怪的是似乎並沒有多語言版本**；Fcitx, WPS, WizNote 等優秀軟件並沒有進入 Community Help Wiki, 遺憾。

其實 [Other Resources][11] 還有兩個重要的資源：[Ubuntu Manual][12] 和 [Ubuntu Wiki][13]. 前者具備多達五十二種翻譯，自然也包括簡體中文，不過版本卻是 13.10, 我猜它大概是由民間自發編輯而成。**後者並不與 Community Help Wiki 重合，而是提供了 Teams, LoCoTeams, Community Links 等等政治資訊。**這下可好了，**Ubuntu 的確主要以 [Country][14] 爲單位，讓地區民間組織自發打造 Community Help Wiki.**

[Ubuntu China LoCo Team][15] 槽點滿賽：**官網赫然顯示着 Ubuntu Kylin LOGO!** 我懷疑它並非由中國大陸社區自發，而是 Canonical 和中國政府聯手推出的發行版，雖然我並不清楚社區的反應，我個人就不看好這分裂；[Forum][16], [Wiki][17], IRC 倒沒變，但 UI 一如既往地老土，真搞不明白它們爲何沒有升級成與官方一致的 UI; #ubuntu-cn 頻道之水在中文 Linux 界是出了名的，的確如此，在此調研中，我發起的若干討論有時很難得到響應。

[IRC in Community Help Wiki][18] vs [IRC in Ubuntu 中文 Wiki][19], 自己比較下吧。

最後，我去了趟傳說中的 [Ubuntu 中國官方網站][20]。

早先從 Office Documents 就可以看得出，文案人員有貫徹空格緩衝的原則。但是 Ubuntu Kylin 官方就沒做好這一點，**非常參差不齊**，有的地方插了空格有的地方就沒有。

其實不光沒做到全面空格緩衝，仔細一瞧「[进一步了解 Ubuntu Kylin][21]」：

![莫名的斷句][22]

![你不是您][23]

![那個「点击进入官网」鏈接實則是「http://www.ubuntu-china.cn/www.ubuntukylin.com」，Ubuntu Kylin 你這麼拒人於千里之外你爸爸之一 Caninocal 知道嗎？][24]

那個所謂的蓮花即時通信一點動靜都沒有。

其實這還不是真正的官網，在「[下載 Ubuntu Kylin][25]」頁面點開援助之手下面的「Ubuntu 問答」「Ubuntu 論壇」和「Ubuntu 閒談」。您會發現前兩者還是 Ubuntu 國際官網的，後一者貌似指向並不存在的 HTTPS 超鏈接，導致打不開。

真正的官網是 http://www.ubuntukylin.com. [wiki 有是有][25]；唯一的 IRC 頻道只面向開發者，因爲它就叫 #ubuntukylin-devel；沒有 Community Help Wiki, 只有[知識庫][26]，不出所料地也沒有關於 IRC 的教程；Ubuntu Kylin 的 [Community][27] 和 [Forum][28] 徹底分裂出去，社區文化又難看，全無 Ubuntu 的優雅風采了。

> Written with [StackEdit](https://stackedit.io/).


  [1]: arch.acgtyrant.com/2014/06/18/Moka-Project
  [2]: https://www.archlinux.org
  [3]: https://wiki.archlinux.org/index.php/IRC_Channels
  [4]: https://wiki.archlinux.org/index.php/List_of_Applications#IRC_clients
  [5]: http://en.opensuse.org/openSUSE:IRC_for_newbies
  [6]: https://fedoraproject.org/wiki/How_to_use_IRC
  [7]: http://www.ircreviews.org/clients/platforms-unix.html
  [8]: https://kushal.fedorapeople.org/xchat1.ogg
  [9]: https://help.ubuntu.com/
  [10]: https://help.ubuntu.com/14.04/index.html
  [11]: https://help.ubuntu.com/community/OtherResources
  [12]: http://ubuntu-manual.org/
  [13]: https://wiki.ubuntu.com/
  [14]: http://loco.ubuntu.com/teams/
  [15]: http://loco.ubuntu.com/teams/ubuntu-china/
  [16]: http://forum.ubuntu.org.cn/
  [17]: http://wiki.ubuntu.org.cn/%E9%A6%96%E9%A1%B5
  [18]: https://help.ubuntu.com/community/InternetRelayChat
  [19]: http://wiki.ubuntu.org.cn/IRC%E5%9F%BA%E6%9C%AC%E6%A6%82%E5%BF%B5
  [20]: http://www.ubuntu-china.cn/
  [21]: http://www.ubuntu-china.cn/desktop
  [22]: https://lh6.googleusercontent.com/-38q4MsvjSCQ/U-jU7Suc3hI/AAAAAAAAF-I/TnImWf9ObNw/s0/2014-08-11-223449_1093x333_scrot.png
  [23]: https://lh5.googleusercontent.com/-2LkKXJeWVek/U-jVL3LN5kI/AAAAAAAAF-c/ykcXQmBhHL4/s0/2014-08-11-223610_996x294_scrot.png
  [24]: https://lh4.googleusercontent.com/-e1kYBK4wols/U-jVl5t0wSI/AAAAAAAAF-w/nt_Qvw_QwMg/s0/2014-08-11-223753_734x250_scrot.png
  [25]: https://wiki.ubuntu.com/Ubuntu%20Kylin%20Chinese
  [26]: http://www.ubuntukylin.com/ask/
  [27]: http://www.ubuntukylin.com/Community/
  [28]: http://www.ubuntukylin.com/ukylin/portal.php