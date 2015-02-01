title: Arch Linux 上突破代理悖論困境
date: 2014-11-03 12:08:17
tags:
- Internet
---
代理悖論困境，其實它還有個更通俗易懂的稱呼，不過我故意貫徹了措辭上的政治正確，以免招來不必要的麻煩。解釋也好望文生義：爲了實現代理訪問，您需要得到一個代理軟件；爲了得到一個代理軟件，您需要實現代理訪問。

其實解決不難，用 VPN 全局代理得到一個代理軟件即可，網上滿是免費的 VPN, 也可以找朋友要。隨便用下就扔掉，畢竟安全上不可靠。

但是 Arch Linux 特殊就特殊在它不會自帶 VPN 客戶端，據我所知 Linux 界真正流行的 VPN GUI 客戶端就只有 Network Manager. 但 GNOME 和 Network Manager 在我 Arch Linux 下就從來沒穩定工作過，我猜有不少 Arch Linux 用戶也爲此而煩惱。

且有不少關鍵工具就陷入了代理悖論困境：

* [GoAgent][1] 就無法正常上傳到 GAE, 因爲 GAE 的 IP 幾乎被封鎖。
* AUR 上的 Google Chrome 和 chromium-pepper-flash 就託管在 Google 網站上，自然沒法下載來並編譯安裝。
* 您無法在 Google Chrome/Chromium 上同步賬戶，包括 Extension.
* 您無妨訪問 Chrome App Store 並安裝任意一個代理 Extension.

於是我每次重裝 Arch Linux 時就相當痛不欲生，好在總算摸索出了門道。

消費／索取到一個 [Shadowsocks][2] 服務，安裝 [cow](https://aur.archlinux.org/packages/cow-proxy/) 並用它[把 Shadowsokcs 包裝成 HTTP/HTTPS 代理](https://github.com/cyfdecyf/cow)，接着[用環境變量實現亞全局代理](https://wiki.archlinux.org/index.php/Proxy#Environment_variables)。當然您能弄到現成的 HTTP/HTTPS 代理就更好，不過現如今恐怕只有私人服務器的地址才有效了吧。至此，上面所提到的前兩個困境解決。

Chromium 已經打包在官方軟件源，所以可以直接用 pacman 下載安裝。理論上它會自動調用 HTTP/HTTPS 環境變量，不過不知爲啥它在我這裏不生效，於是可以通過 `chromium --proxy-server="http://127.0.0.1:7777;https://127.0.0.1:7777"` 命令行強制指定爲地上的 cow 代理服務器，也可以直接用 shadowsocks 上的 Socks5 代理地址，詳情參見 `man chromium`. 至此，上面提到的後兩個困境解決。

不過用命令行啓動 Chromium 代理終究不太方便，您可以在解決代理悖論困境後改用代理 Extension [Proxy SwitchyOmega](https://chrome.google.com/webstore/detail/proxy-switchyomega/padekgcemlokbadohgkifijomclgjgif?hl=en).

如果您有不錯的解決方案，歡迎留言。

 [1]: https://wiki.archlinux.org/index.php/GoAgent_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87) 
 [2]: https://wiki.archlinux.org/index.php/Shadowsocks_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)