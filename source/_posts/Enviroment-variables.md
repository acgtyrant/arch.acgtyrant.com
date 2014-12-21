title: 環境變量
date: 2014-11-30 01:16:21
tags:
- ArchWiki
---

我以前一直以爲環境變量是由 Shell 管理的，要不就是由別的獨立應用程序管理，就像 passwd 管理帳號一樣。可是看了[維基百科相關條](http://zh.wikipedia.org/wiki/%E7%8E%AF%E5%A2%83%E5%8F%98%E9%87%8F)目才吃驚地發現：**原來一開始就由操作系統管理的！即每個進程都有它自己的環境變量，且子進程一般會繼承或改變來自父進程的所有環境變量。**也就是說，當 PID 爲 1 的 init 程序，比如 systemd, 啓動時，就已經有環境變量機制了。

ArchWiki 又有一條[啓蒙級條目](https://wiki.archlinux.org/index.php/Environment_variables)。不翻譯，只簡要概括若干竅門：

其一，`/proc/${PID}/environ` 裏面就有對應 `$PID` 的環境變量內容。我發現，PID 爲一的程序其環境變量居然只有 `TERM=linux`! 而且我又再 urxvt 下的 Zsh 執行 `env | grep TERM` 它返回：

```
COLORTERM=rxvt-xpm
LESS_TERMCAP_mb=
LESS_TERMCAP_md=
LESS_TERMCAP_me=
LESS_TERMCAP_se=
LESS_TERMCAP_so=
LESS_TERMCAP_ue=
LESS_TERMCAP_us=
TERM=screen-256color
TERMINFO=/usr/share/terminfo
```

這很好地證明了維基百科的說法。

其二，env 命令可以一邊改變當前環境變量並執行新程序，比如 `env LANG=en_US.UTF-8` 前綴就可以幫助你運行某調試程序並輸出英文。

其三，留心[很有用的環境變量](https://wiki.archlinux.org/index.php/Environment_variables#Examples)。比如 `http_proxy`!

其四，[注意在什麼場合該定義合適的什麼變量](https://wiki.archlinux.org/index.php/Environment_variables#Defining_variables)。比如最全局的則在 systemd 層次定義，Shell 用戶層次在 `~/.bashrc` 或 `~/.zshenv` 定義，圖形環境相關環境變量則在 `.xinitrc` 定義等到，ArchWiki 條目已經對此很好地說明。

其五，Shell, Shell Script, 進程，環境變量彼此又有什麼關係呢？

網上相關資料多得是。我只給結論：Shell 只是一個被操作系統用來與用戶交互的應用程序，其自然也是 init 程序的子進程；Shell Script 在 Shell 有執行權限且被直接執行時，比如 `./shellscript` 或 `sh ./shellscript`, Shell 會創建 Sub-Shell 環境，也就是子進程，來運行這個 Shell Script; Shell Script 被執行時，它所對應的進程當然也有環境變量；只不過 Shell Script 裏面所定義的變量獨立與其進程環境變量，除非其被 `export`; Shell Script 被 `source` 時，即執行 `source ./shellscript` 或 `. ./shellscript`, 那麼 Shell 不會爲它創建子進程，而是直接在它的環境執行，也就是說，其 Shell Script 所 export 的變量可以變成其 Shell 的環境變量，此外 source 可以不管其 Shell Script 到底有沒有可執行權限。

不得不說，Unix 哲學太厲害了！