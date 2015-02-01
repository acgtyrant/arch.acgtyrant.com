title: 虛擬終端
date: 2015-01-06 16:02:25
tags:
- Utilities
---

[我是 urxvt 重度用戶，但我越來越對 urxvt 的字體渲染不滿意，感到有必要物色更上一層的虛擬終端。](http://arch.acgtyrant.com/2015/01/05/I-do-not-recommend-urxvt-again-now/)

想了下，我期望的虛擬終端應該能：

1. 能用鼠標打開 URL.
2. 支持 Powerline.
3. 支持 Tmux.
4. 半透明。
5. 字體渲染好。
6. 顏色賞心悅目。
7. 不基于 Qt.
8. 配置封裝成一個與 INI 類似的文本文件，方便版本管理及備份。
9. 能關掉響鈴！有 Visible 響鈴就更好。

於是測評並翻譯了[虛擬終端][1]，直接查閱即可。

aterm, Mrxvt, rxvt, Terminal, st, xterm, evilvte, termit 不美觀，棄。

Eterm, KMSCON 啓動不起來，棄。

Konsole, QTerminal 用 Qt, 棄。

Tilda, Yakuake, Guake, Stjerm 都是下拉式的，在 Tiling Windows Manager 上表現一定不佳，棄。

![不過 Yakuake 在 KDE 下確實很出色，這是某朋友的](https://lh5.googleusercontent.com/-vV0JxDB0LRs/VKYU4KpWKsI/AAAAAAAAJwI/9Uma_C5vp-A/s0/01886aef115cc691fc34d06cd82e55c38a22b0.png)

Terminology 有點意思，但如果不是在 Enlightenment 就不能發揮最佳效果了，棄。

我很喜歡 GNOME, 坑爹的是 GNOME-Terminal 官方在 3.8 之後就砍掉半透明了，據說原因沒有公開，是他們內部的一致決定。再次，GNOME 同樣在 VTE 砍掉了半透明，害得有些基於 VTE 的虛擬終端也不支持了。

[FinalTerm](http://finalterm.org/) 將來可能會是**終結戰國時代，傲視天下一切的最強虛擬終端**。可惜不光尚在 Heavy Development 中，又莫名地已經停滯兩個月了，目前只支持 bash 而且還很不完善。**我很期待它的到來！**

![urxvt, gnome-terminal, finalterm, terminology](https://lh5.googleusercontent.com/-ROf7cqRJMEM/VKYXbaoNxtI/AAAAAAAAJwg/TKxevW1J0is/s0/DeepinScreenshot20150102115815.png)

MATE-Terminal 是最和 GNOME Terminal 相似的終端！但是它並沒有獨立的 Configuration File, 空歡喜一場，棄。

LXDE Terminal 字體渲染不錯，但顏色機制就不行，棄。

Roxterm 算滿足了我的期望，但菜單設計有點怪，棄。

Sakura 功能簡陋，棄。

最後只剩下 Lilyterm vs Xfce Terminal 了，幾乎都能滿足我的期望，我左右爲難了很久。但前者運行 tmux 後，每次退出就彈出的警告挺惱人，棄。

從此，御用終端是 Xfce Terminal 了！

<blockquote class="twitter-tweet" lang="en"><p>晴空一声霹雳响，终端脱胎换骨！ <a href="http://t.co/13cGQ4VaM3">pic.twitter.com/13cGQ4VaM3</a></p>&mdash; 御宅暴君 (@acgtyrant) <a href="https://twitter.com/acgtyrant/status/552128612258684928">January 5, 2015</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

#### 事情還沒完。

<blockquote class="twitter-tweet" lang="en"><p><a href="https://twitter.com/acgtyrant">@acgtyrant</a> 按 F1 會彈幫助還得自己手動改有些麻煩，我覺得用 tilda 不錯。</p>&mdash; 寫不出並集函數 (@codeotakuchiyan) <a href="https://twitter.com/codeotakuchiyan/status/552130116919508992">January 5, 2015</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

確實如此誒，比如在 htop 像按 F1 會彈 Xfce4 Terminal 的幫助，而不是 htop 內置幫助；此外 Xfce4 Terminal 用 Tmux 後，窗口分割線難看。

再次，我以爲作爲下拉式 Tilda 的在 i3 下會表現得一團亂糟，但實際上可以取消它的下拉動畫效果，以及自動隱藏機制；而且不像 Xfce4 Terminal 帶多少點依賴，更輕量！最後還可以在配置裏給快捷鍵賦空值，免了與 i3, tmux, vim 等的快捷鍵衝突。

**從此，新・御用終端是 Tilda 了！** 

[1]: https://wiki.archlinux.org/index.php/List_of_Applications/Utilities_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)#.E8.99.9A.E6.8B.9F.E7.BB.88.E7.AB.AF


> Written with [StackEdit](https://stackedit.io/).
