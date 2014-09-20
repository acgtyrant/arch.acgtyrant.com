title: 网络工具
date: 2014-09-10 19:44:34
tags:
- Internet
---

由於 netstat 的需要，溫習了下 netstat 的用法，之後就又心血來潮調研了下「net-tools」。

其實熟悉 Arch Linux 的用戶知道，[官方很早就用 iproute2 代替 net-tools 了](https://www.archlinux.org/news/deprecation-of-net-tools/)，可謂現代 CLI 網絡工具。我試着用前者自帶的 `ss` 了下，細節上的確要比後者 `netstat` 好點。問題是 iproute2 太新，不論中文還是英文，資料少之又少，ArchWiki 竟然也沒有相關條目。好在 [Gentoo Wiki 有相關條目](http://wiki.gentoo.org/wiki/Iproute2)並介紹了 net-tools 內置各種命令的 iproute2 對應版本；DigitalOcean 上也有不錯的文檔：[How To Use IPRoute2 Tools to Manage Network Configuration on a Linux VPS](https://www.digitalocean.com/community/tutorials/how-to-use-iproute2-tools-to-manage-network-configuration-on-a-linux-vps).

但是同類軟件卻很少，並不值得在 List of Applications 新建章節以介紹。於是我也就在這裏簡單介紹下：

![gnome-nettool. 應該是 netstat 的前端，但沒想象中的有亮點，按 Unix 哲學還是原來 CLI 的 net-tools 方便使用。](https://lh4.googleusercontent.com/-dJ_5KRJoCaM/VBBD9_WcqnI/AAAAAAAAGYU/ZfLqZQrBgBY/s0/DeepinScreenshot20140910202225.png)

nmap. 掃描並監測他人主機上的 Port, 於我無用。

Zenmap. Arch Linux 的 nmap 自帶 GUI 前端，用法可參考：[Zenmap Tutorial: Audit Your Networks using Nmap GUI](http://www.linux.com/learn/tutorials/381794-audit-your-network-with-zenmap). 看起來很高大上。

[Why Can't I Connect?](https://www.whycanticonnect.com/) 您沒看錯這真的是軟件名的全稱，看起來有點新鮮，但 Arch Linux 並沒有現成的包，改天玩玩。

iftop, iptraf & nethogs. 出自 [A little collection of cool unix terminal/console/curses tools](http://kkovacs.eu/cool-but-obscure-unix-tools), 瞧您流量跑去哪了。

> Written with [StackEdit](https://stackedit.io/).