title: 深析 CLI vs GUI
date: 2014-02-01 22:51:19
tags:
- 其它
- Linux
---

注意：該文假設**您具備高等數學知識，能熟練操作 Linux 以能夠日常使用，暸解 TeX, i3 等工具，有一定的計算機科學知識，且擁有良好的正版消費觀。**此外在下從未接觸過 Mac OS X 系統，所以對 GUI 的評估可能會有認識上的不足。

## CLI 與 GUI 的可操作性定義

宛如 Linux vs Windows, GTK+ vs Qt, Vim vs EMacs 一樣，CLI vs GUI 也算是很有來頭的爭議之一了，想必大多 Linux 用戶偏好 CLI 哲學，從而對 GUI 嗤之以鼻吧，不過大家其實不光沒有下過 CLI & GUI 的嚴謹定義，且若只鍾情 CLI 而拒絕一切 GUI 的話，那就過猶不及了。

首先均對 CLI 和 GUI 下一種概念性定義：**操作**。是的您沒看錯，所以您需要**摒棄以往對該兩術語在 UI 方面的印象。**接著分別下 CLI 和 GUI 的可操作性定義：**通過字符串的輸入，以實現所期望的操作**；**在一切操作中，CLI 操作的補集**。 

為方便，下面直接改用『**CLI 操作**』，『**GUI 操作**』來稱呼它們，並且再定義兩道派生義：

1. **CLI 程序：總體上，可認為 CLI 操作佔了一切操作的絕大部分，乃至全體的程序。**
2. **GUI 程序：一切程序中，CLI 程序的補集。**

其實 CLI 和 GUI 本来不衝突，畢竟說了都是操作，**而一個程序可以同時具備這兩種操作方式，於是它到底算哪一種程序，其實是不重要的。**

## 重新認識 CLI 操作

現在諸位想一想，為了在終端上執行一道命令，比如 `ls`，需要怎麼做呢？

簡單，在當前輸入光標已處於終端的前提下，直接在鍵盤上依次按印有 'l', 's', 'Enter' 這三塊鍵即可，這麼一做就會實現以下字符的輸入：`l`, `s`, `\n` 。這當然是典型的 CLI 操作了。

![ls][1]

但是，在 Android 上用 IME 輸入這道命令，這行為還算是嗎？

![這算 CLI 操作嗎？][2]

特別提醒下，對 **CLI 操作**的理解關鍵在於：**不論輸入方式如何，只要是以輸入的字符串為媒介，來實現所理想的操作，那麼這就算是 CLI 操作。**於是這當然也算了。

此外，仔細想一想，以往所謂的『**快捷鍵**』說穿了也是一串字符串輸入而已，於是**甚至連 MPlayer 都稱得上 CLI 程序了**，畢竟它的操作方式就只有這些快捷鍵了：

    Key	 Description
    p	 Toggle pause/play.
    Space	 Toggle pause/play.
    Backspace	 Return to menu when using dvdnav.
    ←	 Seek backward ten seconds.
    →	 Seek forward ten seconds.
    ↓	 Seek backward one minute.
    ↑	 Seek forward one minute.
    <	 Go back in the playlist.
    >	 Go forward in the playlist.
    m	 Mute the sound.
    0	 Volume up.
    9	 Volume down.
    f	 Toggle fullscreen mode.
    o	 Toggle OSD state.
    v	 Toggle subtitle visibility.
    I	 Show filename.
    1, 2	 Adjust contrast.
    3, 4	 Adjust brightness.
    j	 Cycle through the available subtitles.
    #	 Cycle through the available audio tracks.
    
![→	 Seek forward ten seconds.][3]

CLI 操作的定義如此廣泛，其實不光 Shell 命令，而且連由此拓展出的**命令交互式環境操作**，如 Zsh, IPython 等，以及**用程序語言編程**，如寫 Shell, Python 腳本，C 程序等，都稱得上 CLI 操作：

![Interactive shells and programming][4]

好了，現在終於要涉及到 CLI 操作的本質了，請從數學上理解：**輸入的文字是一種變量，其所实现的操作为一种函数值，且所有**合法的**文字串為定义域，所有**期望的**操作结果为函数值，且彼此有一定的映射关系，即函数。**于是 CLI 操作说白了是**在明白函数關係的前提下，为了得到所期望的操作结果，从而输入特定的一段字符串的行为而已。**

到底该怎么理解**函数**，又怎樣規定其呢？都不重要！关键是，只要有了准确的函数、定义域和值域，我们就拥有了真正意義上的**邏輯到邏輯的映射**，而且**其映射本身又是嚴謹的邏輯**。

## 邏輯觀點下的 CLI 優勢及缺陷

TeX 算是 CLI 操作的登峰造極之成了：通過一大段『命令』的輸入，即可謂字符串，再遵循必要的結構，我們就可以得到邏輯分明，清晰漂亮的文檔來。王垠先生更是在 [TeX — Beauty and Fun][5] 中一針見血地指出：

> 不适合直接用 TeX 编辑的是没有逻辑结构的东西，比如报纸，画 报，广告等。像彩色杂志，图片很多，还有各种变化多端的分栏方 式，就不适合用 TeX 来排版。
>
> TeX 似乎不大适合艺术创作，它体现着理性的思维方式。所以， 作家可能不会用 TeX。

**TeX 天生就具備了邏輯特性，於是只要所期望創造的對象具備邏輯，它都能創造出來。**即**只要先定義具備邏輯的一堆『命令』，再發掘出作品相應的邏輯，最後定義必要的映射就可以了。**最典型的函数大概就要算 TeX 獨有的数学公式命令了。

不過，這也就註定了 CLI 重大缺陷之一：**當所期望的操作結果不具備邏輯性時，那麼就很難設計實現它的理想 CLI 操作出來。**

請看兩張圖：

![大小不規則的窗口][6]

![那麼要移動窗框，並形成看上去比較有規則的大小，該怎麼操作呢？][7]

i3 並沒有提供能直接達成該變化的一次性 CLI 操作，畢竟所要實現的目標邏輯有點複雜，不過還是有些 CLI 操作能實現的，在本人的配置下，是：

    # resize window (you can also use the mouse for that)

    mode "resize" { 
    
    bindsym h resize shrink left 10 px or 10 ppt
    bindsym Shift+H resize grow left 10 px or 10 ppt
    bindsym j resize shrink down 10 px or 10 ppt
    bindsym Shift+J resize grow down 10 px or 10 ppt
    bindsym k resize shrink up 10 px or 10 ppt
    bindsym Shift+K resize grow up 10 px or 10 ppt
    bindsym l resize shrink right 10 px or 10 ppt
    bindsym Shift+L resize grow right 10 px or 10 ppt
    
    bindsym Left resize shrink left 10 px or 10 ppt
    bindsym Shift+Left resize grow left 10 px or 10 ppt
    bindsym Down resize shrink down 10 px or 10 ppt
    bindsym Shift+Down resize grow down 10 px or 10 ppt
    bindsym Up resize shrink up 10 px or 10 ppt
    bindsym Shift+Up resize grow up 10 px or 10 ppt
    bindsym Right resize shrink right 10 px or 10 ppt 
    bindsym Shift+Right resize grow right 10 px or 10 ppt
    
    bindsym Return mode "default"
    bindsym Escape mode "default"
    
    }
    
    bindsym $mod+r mode "resize"

但是仍有若干難處：其一，該快捷鍵只能進行**等距移動**；其二，要形成不規則大小到規則大小的變換，所需要的移動量為多大？且期望結果又如何？**用戶很難事先在腦海中估算出清晰的印象**；其三，實踐證明，除了最開始的觸發輸入 `mod+r` 字符串，接著還要按約四十次 `Shift+j`, 約 八十次 `Shift+l`，雖說可以直接按住鍵不放可以加快窗框移動的速度，但**時間開銷仍可觀**；其四，其實有時會移過頭，於是就不得不再按 `j` 和 `l` 反向移動，**加以重新調整**。

但是真的只能這樣了嗎？

![只要用鼠標拖一下就可以了！即 GUI 操作][8]

鼠標拖住窗框時，**其移動軌跡就代替了以上 CLI 操作所需要的大量字符串輸入，並直接與其窗框在平面幾何上的變動形成同構關係。**

![假設有四個窗口，且不光要調整大小如下，且要讓彼此的位置如此更毫無邏輯呢？][9]

這次 i3 就幾乎沒可行的 CLI 操作來實現了，在 Windows 下可以直接用鼠標拖動窗框，拖動標題欄以實現移動的 GUI 操作，其實 i3 當然也能做到，除了上面提到的拖動窗框的 GUI 操作，可以一邊按住 mod 鍵，一邊用鼠標直接點擊窗口上任意處並按住不放，開始拖動窗口即可。

![由於可以直接移動鼠標指針到窗口上的任意處，並實現拖動操作，這已經完全超越了 Windows 下那類似的操作][10]

鼠標的移動軌跡本來可以毫無邏輯，自然方便被映射成窗口大小及位置隨心所欲的變化。同理，小紅點、軌跡球、觸摸板和操縱桿等一樣也能做得到，且傳說中的 Apple Trackpad 應該更勝一籌。**這些都可謂 GUI 操作，並能方便實現非邏輯的操作結果，CLI 操作就只能有心無力了。**

## 邏輯觀點下的『量』

其實嚴格說來，**任何對象都有一定的邏輯，區別只在於『量』而已**

就拿上面提到的四個窗口移動難題來說，用原本的 "resize" 操作還是能勉強做到的，所需要的只是充滿耐心地、不停地調整某窗大小，再激活另一窗口調整、校對，如此反覆而已...只不過操作量自然大得驚人。畢竟那種四種窗的大小與位置還是有一定的邏輯，即無非是『十六個點的 X-Y 幾何位置』和『2^4 個激活順序中的其中一種』罷了，我們只要使用 resize 操作讓初始的四個窗口對齊到這十六點，並接著按一定順序激活窗口，以實現正確的覆蓋效果，就行了：

![由於部分窗口的邊界已超出屏幕，所以不好一一圈出『十六個點』了...][11]

再次，您有見過某人用鍵盤畫畫嗎？當然這活終究只能靠鼠標來幹，且數位板更為合適，由此看來，靠 PC 來畫畫，似乎就只能是 GUI 操作了嗎？

非也，任何 PC 上畫畫出來的圖像，說到底均是以二進制數字形式儲存的，所以在理論上且理想的話，即**您知道某圖在某有效格式下的二進制表示，那麼只要創建該格式的空文件，並編輯其、開始充滿耐心地不停地敲擊 0 和 1 進去，敲擊完畢便保存，這樣也可以『畫』出同樣的圖像來，**就是要畫到天荒地老。雖說實在夠低級且粗暴，但這的確算得上**可行且有效的邏輯了**，於是我們可以通過 CLI 操作來畫畫。

事實上，現實中早有人這麼做了，只不過當然還沒誇張到用二進制數字畫畫。據在下所知，能實現畫畫結果的 CLI 操作有：

其一，[用 SVG 編程][12]，用以實現幾何圖形的矢量表示。

其二，CLI 流派的繪圖工具：TeX 的 MetaPost, Python 的 matplotlib， Matlab 的繪圖函數等等。

其三，[ASCII 藝術][13]，即用 ASCII 字符來逼近所需要的畫畫，似乎在日本 BBS 蠻流行；此外也多為直接用程序語言編寫而成，比如[动画演示10个有趣但毫无用处的Linux命令][14]；且有時還能模擬，以下為在終端調用 img2txt 來顯示圖片的效果：

![img2txt in ranger][15]

但是，想必聰明人看出 CLI 操作的侷限來了：**幾乎只能實現本身具備可靠邏輯的畫畫，對於高度複雜的圖像，就只勉強能用遠遠不夠的邏輯量來畫畫了。**

## GUI 操作对庞大逻辑的『封装』

說到底，試圖用如此低級繁雜的大量邏輯來實現高層邏輯，終究吃力不討好。**但 GUI 操作就不一樣了，它能夠封裝大量低級邏輯，即 CLI 操作，一勞永逸地提升操作效率。**

這回就拿『文本配置』來來談吧。[ArchWiki][16] 指出，GTK+ 2.x Style 的配置主要有兩種方法。其一是通過文本文件來配置：

    $XDG_CONFIG_HOME/gtk-3.0/settings.ini
    [Settings]
    gtk-application-prefer-dark-theme = false
    gtk-theme-name = Zukitwo
    gtk-fallback-icon-theme = gnome
    gtk-icon-theme-name = [icon theme name]
    gtk-font-name = [font name] [font size]

配置示範：

    ~/.gtkrc-2.0
    gtk-icon-theme-name = "Tango"
    gtk-theme-name = "Murrine-Gray"
    gtk-font-name = "DejaVu Sans 8"

但是這麼一來就有不少問題了：

1. 怎樣知道已安裝/可使用的 `icon-theme-name`, `gtk-theme-name`, `gtk-font-name` 有哪些？
2. 該配置文件的編碼是什麼，支持中文嗎？特別是 `方正兰亭黑_GBK` 这样的字体名稱。
3. 用双引号括起来的字符串内，有哪些字符需要转义？特别是 `_` 这种。
4. 除了示范中的参数，还有其它哪些参数？
5. 又怎样知道其它参数所已安裝/可使用的對象有什麼？
6. 在各种参数中，所制定的对象均要用双引号括起来吗？
7. 如果對象名稱含有空格，又該怎麼辦呢？要用 `\` 轉義嗎？
8. 有能使用的註釋符嗎？若有，它是什麼？
9. 此外，參數會有特定的順序嗎？比如 `gtk-icon-theme-name` 是否一定要排在 `gtk-theme-name` 前面？
10. 該配置規則是否適用於 GTK+ 3.x 呢？若否，又有什麼變動？
11. 文本配置總算配置好了，不過它真是理想的嗎？又有什麼途徑lai觀察配置效果呢？
12. blablablabla...

您瞧，光進行這樣的手動配置，就要考慮眾多複雜的細節。在下過去曾手動配置 GTK+ 3.x 十幾次，但 GTK+ 3.x 調用其卻總失敗，且語焉不詳的 `syntax error` 又不能指出到底是哪裡的格式不對、正確格式規範又是如何等等，實在苦惱了很久。

不過，在下姑且試了試當時瞧不上的 GUI 配置方法：gtk2_prefs 程序。

![配置如此簡單][17]

經過簡單的幾步『點擊』挑選並『OK』，結果 GTK+ 2.x 立馬配置成功。這麼一看，**此 GUI 操作完全不用顧及 CLI 配置下那堆複雜瑣碎的一堆細節了，我們只要點擊點擊就好**。更關鍵的是，**我們還能夠直接 Preview 效果**。

此 GUI 操作為什麼這麼輕鬆呢？**因為它把龐大且複雜的邏輯細節封裝到 GUI 菜單中了。**這便是 GUI 的優勢所在之一。再拿上面所提到的畫畫例子，要畫出足夠複雜的圖像，自然也要依靠相應的 GUI 操作及程序：

![Toolbox 中各種各樣的 GUI 操作][18]

## 再解构及自動化

由此看來，不是每種操作都能通過 CLI 方式高效地實現，畢竟很多操作的邏輯是實在的太複雜，我們只能用 GUI 操作來封裝其複雜的邏輯，大大降低操作成本。

但是，**封裝自然也意味著對底層細節的隱藏**，且 GUI 程序提供的 GUI 操作終究有限，當我們想進行一種特殊且程序本身卻沒有的操作，就只能乾瞪眼、有心無力了。這便是 GUI 程序的弊端之一，也是 IDE 一直為人詬病的地方。《[GUI和CLI的使用比较][19]》就對此总结地好：

> 对于在GUI界面和集成开发环境(IDE)上成长起来的程序员,这似乎显得很极端.毕竟,用鼠标指指点点,你不是也同样能把这些事情做好吗?

> 简单的回答:"不能".GUI界面很奇妙,对于某些简单操作,它们可能更快、更方便.移动文件、阅读MIME编码的电子邮件以及写信,这些都是你可能想要 在图形环境中完成的事情.但如果你使用GUI完成所有的工作,你就会错过你的环境的某些能力.你将无法使常见任务自动化,或是利用各种可用工具的全部 力量.同时,你也将无法组合你的各种工具,创建定制的宏工具.GUI的好处是WYSIWYG--所见即所得(what you see is what you get).缺点是WYSIAYG-- 所见即全部所得(what you see is all you get).

> GUI环境通常受限于它们的设计者想要提供的能力.如果你需要超越设计者提供的模型,你大概不会那么走运--而且很多时候,你确实需要超越这些模型.注重实效的程序员 并非只是剪切代码、或是开发对象模型、或是撰写文档、或是构建过程自动化--所有这些事情我们全都要做.通常,任何一样工具的适用范围都局限于该工具预期要完成的任务. 例如,假定你需要把代码预处理器集成进你的IDE中(为了实现按合约设计、多处理编译指示,等等).除非IDE的设计者明确地为这种能力提供了挂钩,否则,你无法做到这一点.

**若拋開方便且固定的 GUI 操作，勇於面對底層邏輯上的細節，且當我們終於掌握了足夠的邏輯細節，拿我們就可以自行地把對應的 CLI 操作封裝起來成全新的操作，甚至實現自動化。**[王垠先生也英雄所見略同][20]：

> 有一次某杂志采访一些出名的 Linux 内核程序员，包括 Linus 在内，没有一个人用 IDE，有的人用 VIM，有的用 Emacs，只有 Linus 说 “GNU Emacs is evil”，但是其实他用的是一种跟 Emacs 有同样键绑定功能的 MicroEmacs。大家都是用编辑器编辑了程序文件，然后用 make 这样的自动工具调用 gcc 编译器完成编译工作的。甚至高级的 Windows 程序员也不用 IDE，他们可以从命令行调用 cl，nmake 来编译自己的程序。虽然这样的 Windows 程序员很少，但是他们却是最了解 Windows，最高明的 Windows 程序员。

> 为什么 UNIX 程序员不用 IDE？明白了这个道理你就能体会到 UNIX 的设计思想了。首先，一个 IDE 集成了编辑器，编译器，汇编器，调试器，跟踪器…… 这个编辑器功能肯定比不上 VIM 或 Emacs，编译器比不上 GCC，汇编器比不上 as，调试器比不上 gdb, ddd, 跟踪器比不上 strace, ltrace, truss。你得到的是一套整合的低能的程序。如果你对调试器的功能不满意，你只好换用另外一套 IDE，但是这套 IDE 的热键，菜单，编辑器功能，按钮…… 跟原来那个有很大不同。你不得不花很多时间来熟悉新的环境，而不能保持原来的某些东西。

> 而在 UNIX 下就不一样了。你可以用你最喜欢的 VIM 编辑程序，你在 VIM 里可以调用 GNU make，make 可以调用 gcc, ld, ... make 的出错信息可以被 VIM 捕获，VIM 能帮你在源程序里定位。你如果喜欢 icc, 你可以让 make 用 icc 而不是 gcc。你如果觉得 gdb 跟踪变量时比较麻烦，你可以用 ddd 来显示各种数据结构之间的关系。你还可以在 Emacs 里调用 gdb，那样就可以同步显示源代码了。而且 VIM 和 Emacs 还可以编辑很多其它东西，比如信件，LaTeX 文档，HTML，配置文件…… 你不用另外找一个什么编辑器来干这些杂活了。很多程序比如 Mutt, tin 都可以在内部使用 VIM，这样就更方便了。实际上 make 在其它方面还能帮你很多忙，我的每一个比较大型的 LaTeX 文档都是用 make 维护的。

歸根結底，**GUI 在封裝大量低級操作的同時，也伴隨著 WYSIAYG(what you see is all you get), 即所见即全部所得的弊端。**對 GUI 操作再重新解構成底層 CLI 操作，則不光打破 WYSIAYG 困境，且還能按我們所需要的隨心所欲設計，並實現自動化。

## GUI 程序開發的可觀成本

此外，GUI 操作還有另一個代價，**它終究是要靠一大堆底層邏輯支撐的。**若要開發一種 GUI 程序，開發人員必須研究種種 GUI 操作下的複雜邏輯，並考慮如何分割成眾多獨立且較簡單的邏輯，再慢慢地開發对应的函數和小程序，并最终封裝成種種 CLI 操作來。造就了 GUI 程序开发成本相当可观：

![Adobe 出臺了不少強悍無比的 GUI 程序，但個個的原價也奇貴無比；Microsoft Office 系列也是如此][21]

Mac OS X 應該算是把 GUI 操作发挥到登峰造極的操作系統了，但它毕竟是商业化的操作系统，就算您想买最便宜的 Mac PC，比如 Mac mini，也要花 RMB 4488 多，Windows 操作系統也是一樣的道理（雖說如今 Windows 8 在中國市場的價格已經不是很貴了……

但 Linux 在 GUI 程序開發上，所能夠挖掘的商業利益就少得可憐，也難怪它在 GUI 方面，與 Windows 及 Mac OS X 一直有所差距。但您見過依賴 GUI 操作的服務器嗎？Linux 天生就靠底層邏輯起家，且對應的 CLI 操作及程序的開發成本、運行開銷自然也小，於是也難怪它會在服務器、嵌入式機器領域如此流行了。

不過在下挺看好 Linux, 畢竟 Linux 不光在 CLI 上完暴 Windows, 且如今其 GUI 程序對普通用戶來說已經足夠好用，用心閱讀過敝博的讀者應該深有體會吧。

## Linux 特有 CLI 操作之鑑賞

這裡只粗略點評在下與 Linux 上所發現的特有 CLI 操作，當您已暸解這些操作之時，便算是真正洞悉到 Linux 的特色之一了：

1. 命令行交互式环境，即 Shell. 全體 Linux 用戶最經常接觸的玩意恐怕就要數這個了，典型的有 bash, zsh, iPython, 甚至 Matlab.
2. 命令参数，即 Command Arguments. 這算是極其普遍的 CLI 操作了，即在命令中追加若干特定參數，以實現對應的 CLI 操作結果。Git 就把這機制發揮得挺好，在補全時就會列出非常詳細的參數及作用。
3. Tab 补全，即 Tab Completing. 該機制自然大大提升了 CLI 操作的效率，尤其是 Zsh. 此外它有個逆天的『[漸進補全][22]』插件，不過很容易變得很卡，尤其是遠程登錄時，個人還是不推薦。
4. 别名，即 Alias. 它可以對一段構成複雜 CLI 操作的字符串賦予別名，執行它時直接用該 alias 即可，可謂又一大提升 CLI 操作的利器。這裡再對 Arch Linux 用戶推薦下非常好用的 alias: [Oh my Zshell 及兩道 Arch Linux 專用插件。][23]
5. 环境变量，即 Enviroment Variables. 直接給全局規定了特定的變量，在下就用它[一勞永逸實現亞全系統代理][24]。
6. 命令路径，即 \$PATH. 可以規定 Shell 所能執行的命令所在目錄有哪些，在下添加上了 `$HOME/bin`, [用來放一些有用的命令與腳本][25]。
7. 管道机制，即 Pipe. 這機制挺神奇，它讓用戶能夠把 CLI 操作結果在作為新一輪的字符串，輸入到下一個 CLI 操作中，幾乎固定不變的 GUI 操作就只能望洋興嘆了；xl2tpd 就可以通過`/var/run/xl2tpd/l2tp-control`來控制。
8. 输入输出重定向，即 I/O rediction. Linux 的 CLI 操作神奇之處真是沒完沒了呀！比如 `> file` 就可以清空該文件，或當其文件不存在時就創建以 `file` 為名的空文件；`ls > /dev/null` 就可以把 `ls` 的操作結果餵給黑洞君。kodango 先生所翻譯的 [Bash One-Liners Explained 译文（三）][26] 對此科普得好。
9. 程序语言，即 Program Language. 在 Linux 上能很輕鬆地寫 Shell Script, Python Script 等，實現 CLI 操作自動化。 
10. 鍵綁定，即 Key-binding. 最有名的就有 Vim 及 Emacs 兩大流派了，充分利用該機制，就又可以通過 CLI 操作來操作所要輸入的字符串。由於在下是 Vim 用戶，所以曾試圖把 Linux 下任何地方統統設為該 binding, 包括 Zsh, 不過用了一段時間，發現並不是每個地方都適合使用該 binding，尤其在 Shell 下就相當過猶不及，Shell 所能進行的大多 CLI 操作終究之時一行簡單的字符串而已，[Emacs binding][27] 就要比它好用。不過自帶 Vim binding 的文件管理器 ranger 也挺好用。
11. 文本配置，即 dotfiles. 不少 CLI 程序都支持調用文本文件中的配置，所以實際上 Linux 普通用戶從來不需要備份眾多軟件甚至整個操作系統系統，只要備份這些文本配置就行了，且隨便搬到哪一種 Linux 都能用得上。[在下用 stow 管理 dotfiles.][28]
12. 正则表达式，即 REGEX. 又是強悍無比的 CLI 操作機制，所可用的工具則可有 Perl, [awk][29], [sed][30], grep 等等，[有個 Joke 把它描繪得挺好玩。][31]
13. 顏色高亮，即 Color highlight。在下於 `.Xresource` 及 `.config/i3/config` 中定義了一些顏色，打造出了如此漂亮的終端及桌面 UI, 此外不少 CLI 程序也支持調用語法高亮，比如 `ls --color=auto`, `grep --color`， vim 的 `syntax on`, git 的 `ui = on` 等等。
14. Powerline. Linux 界剛出現的新興之物，大概是由 [Lokaltog][32] 所開創，其特色為用 `⮀` 為分隔符，不同的區間用不同的顏色背景，極其相當養眼，竊以為算是極其漂亮的 CLI UI 了。如今在下同時使用 Tmux 的 [Tmux-powerline][33], Zsh 的 [powerline-modified theme][34], Vim 的 [vim-airline plugin][35].（若再有 Powerline 的 i3 status bar 就完滿了...

## 集 CLI 和 GUI 之大成

固然拜 Linux 所賜，在下如今算是十分熟悉種種 CLI 操作了，但鑑於同時尚未接觸 Mac, 自然也對 GUI 操作沒什麼發言權。不過，若要舉一舉同時出色地對 CLI 及 GUI 取其精华，去其糟粕了的程序，在下倒有幸接觸過一二，其中之一便是 TeXmacs.

TeX 算是 CLI 操作中的典範了，但說實話，TeX 同時也是很糟糕的語言，[Knuth 都不予否定][36]，但是，這並不妨礙大家用它作出了众多好作品。不過学习难度，使用成本太高終究是很明显的另一碼事。要學習它，您必須掌握好多知識：**众多命令、宏包、环境、引擎、Linux 发行版、编辑器、排版方法甚至英语。**您瞧，為了單純的作品寫作，就要掌握那麼多底層邏輯。[王垠先生猛啃 TeXbook 兩月了然後立馬忘光][37]，在下也曾系統性地學習 LaTeX 了兩次，卻也一直用得力不從心。

直到在下發現了 TeXmacs 的存在。它就完全重新設計了底層的排版語言，並封裝成 GUI 操作，但同時也提供了大量的 CLI 操作，即快捷鍵。於是 TeX 寫作就成了一件舒心的事情，實現了 WYSIWYG 的真諦：

{% vimeo 85433206 %}

但同時還不忘提供敲數學公式的 CLI 操作流：

{% vimeo 85433207 %}

如此出色地集 CLI 和 GUI 之大成與一身！想必對大家的程序設計觀念頗為啟發吧。

## 後記

> 从Linux到Android再到其他种种，都有一群爱好折腾的人照着别人的教程改这改那，然后觉得自己特极客特专业特牛X。

> Linux内核代码超千万行，还有下面的各种桌面、平台、编译器、库、软件，你给他们贡献过一行代码没？

在[一心只玩 linux 的学生毕业后适合什么工作？][38]提問中，有如此[譏諷][39]道。

說來在下也挺無地自容，畢竟玩 Linux 都那麼久了，然而如今它對我而言，**說到底還只停留在『玩具』的層次上，離『謀生工具』層次還遠得很。**

不過也不曾後悔選 Arch Linux 過，畢竟 Arch 真諦之一是純粹的『用戶中心』，它直接暴露操作系統的種種細節給用戶自行操作、排錯和使用，對我而言是再好不過的實驗平臺了。

話說回來，本博至今已算是積累了六萬多文字，二十篇文章等，可是訪問量一直低迷到想嘆息。也許**是時候該少貪玩了**。自然首當其衝地，該文是轉型的一次嘗試，為此釋放在下對 Linux 所長期積累的思考。

> Written with [StackEdit](https://stackedit.io/).


  [1]: https://lh4.googleusercontent.com/-HwrlshcPNTI/Utzg6ik9_II/AAAAAAAAEzs/x0BSeD3H0sU/s0/2014-01-20-164015_681x160_scrot.png
  [2]: https://lh6.googleusercontent.com/udOKpgbK2cZjieKMQpj9vNXDkvHx-_xlFi4jPSXdkrs=s0 "這算 CLI 操作嗎？"
  [3]: https://lh3.googleusercontent.com/-413FuoQkmJo/Utzh_iaIq_I/AAAAAAAAE0A/Qsgr5eF3_gQ/s0/ScreenShot.png "由 → 触发的快进操作"
  [4]: https://lh4.googleusercontent.com/-6Pu46QjEW4I/Ut0bW-Hfa4I/AAAAAAAAE2c/MRMosAAFzrA/s0/2014-01-20-204921_975x449_scrot.png
  [5]: http://docs.huihoo.com/homepage/shredderyin/tex_frame.html
  [6]: https://lh4.googleusercontent.com/-nxGg26dVtME/UtzmsjpJ5LI/AAAAAAAAE0Y/geiI84ATODs/s0/ScreenShot.png
  [7]: https://lh4.googleusercontent.com/-EPbtvT8JwKo/Utzn0STGJvI/AAAAAAAAE0s/EYLOtzWYl70/s0/ScreenShot.png
  [8]: https://lh5.googleusercontent.com/-KxJA0MkEvUM/Utzulf9D0mI/AAAAAAAAE1E/_M_cOoxy6HU/s0/Screenshot+-+01192014+-+11%253A26%253A18+PM.png
  [9]: https://lh6.googleusercontent.com/-_HEZh3eB0z4/UtzvE2r2IuI/AAAAAAAAE1Y/BMKDyEVcxx0/s0/ScreenShot.png
  [10]: https://lh5.googleusercontent.com/--o1R74Qqj0Y/UtzwqlhC-DI/AAAAAAAAE1w/yldMsAd2QyU/s0/Screenshot+-+01202014+-+05%253A47%253A15+PM.png
  [11]: https://lh3.googleusercontent.com/-s-SYL6KBJWY/UuIeEED0-lI/AAAAAAAAE4s/UQdeOgkKKqM/w1010-h568-no/Screenshot+-+01202014+-+05%253A47%253A16+PM.png
  [12]: http://www.ibm.com/developerworks/cn/xml/x-matters40/
  [13]: http://en.wikipedia.org/wiki/ASCII_art
  [14]: http://www.aqee.net/10-funny-liunx-command/
  [15]: https://lh5.googleusercontent.com/-njQmmbki9UA/Ut0k3_kI9XI/AAAAAAAAE20/35s9lXjIELs/s0/2014-01-20-212957_1367x769_scrot.png
  [16]: https://wiki.archlinux.org/index.php/GTK+#GTK.2B_2.x
  [17]: https://lh6.googleusercontent.com/-w74jaaFtC6I/UuINi4hoRYI/AAAAAAAAE4A/z5zA7jf9G18/s0/2014-01-24-145156_739x411_scrot.png
  [18]: https://lh5.googleusercontent.com/-WI2yRG0YrpU/UuIFV44X6LI/AAAAAAAAE3o/xAzN1hcqy60/s0/ScreenShot.png
  [19]: http://blog.icehoney.me/posts/2014-01-18-GUI-VS-CLI
  [20]: http://yinwang0.lofter.com/post/183ec2_479b6a
  [21]: https://lh4.googleusercontent.com/-f7qUmwExT0Y/UuIYb-bqrlI/AAAAAAAAE4Y/4wGOT0nhoes/s0/2014-01-24-153030_1018x767_scrot.png
  [22]: https://linuxtoy.org/archives/incr-zsh.html
  [23]: http://arch.acgtyrant.com/2014/01/15/oh-my-zshell-and-two-plugins-for-arch-linux/
  [24]: https://wiki.archlinux.org/index.php/GoAgent_%28%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87%29#.E4.BA.9A.E5.85.A8.E5.B1.80
  [25]: https://github.com/acgtyrant/bin
  [26]: http://kodango.com/bash-one-liners-explained-part-three
  [27]: http://kodango.com/bash-one-liners-explained-part-five
  [28]: https://github.com/acgtyrant/dotfiles/
  [29]: http://coolshell.cn/articles/9070.html
  [30]: http://coolshell.cn/articles/9104.html
  [31]: https://xkcd.com/208/
  [32]: https://github.com/Lokaltog/powerline
  [33]: https://github.com/erikw/tmux-powerline
  [34]: https://github.com/acgtyrant/dotfiles/blob/master/Shell/.oh-my-zsh/themes/powerline-modified.zsh-theme
  [35]: https://github.com/bling/vim-airline
  [36]: http://bbs.ctex.org/forum.php?mod=redirect&goto=findpost&ptid=74859&pid=446669
  [37]: http://yinwang0.lofter.com/post/183ec2_4cbdca
  [38]: http://www.zhihu.com/question/20638258
  [39]: http://www.zhihu.com/question/20638258/answer/18318792
