title: 信息安全的一次深入淺出
date: 2014-03-23 18:12:56
tags:
- 信息安全
---
繼 [深析 CLI vs GUI][1] 之後，接著就是信息安全上的一次深入淺出了。不過在下並不打算全憑一人之力講全，而是**給大家按圖索驥的一張好圖**。此外在下並非信息安全專業人士，難免疏漏，敬請讀者斧正。

通過本圖，您可以索到信息安全觀、數論上的眾多概念及原理、RSA 算法原理、Hash 入門知識、數字證書原理、SSL, SSH, PGP, Hash checker, CA Mannage Tools 等應用和物理安全概念知識。不過若您能會閱讀英語文獻就更好。

## 您相信什麼？

在下見過一道很有趣的形而上學疑問：**三角形內角之和為什麼是 180 度？**

但關鍵不在於答案，**畢竟這是一個本質主義問題，當然也沒有終極答案。**但是，我們可以從另一方面來認識其疑問的本質：**三角形內角之和是否穩定的？**

且從在下對世界的觀察來看，世界依然貫徹歐幾里得幾何原理，從而三角形內角之和自然依舊穩定，即還是 180 度的那老樣子，於是我們便心安理得地生活。

但真的就一定那麼一成不變嗎？科學界向來流傳著令人不安的假說：

> 一个农场里有一一群火鸡，农场主每天中午十一点来给它们喂食。火鸡中的一名科学家观察这个现象，一直观察了近一年都没有例外，于是它也发现了自己宇宙中的伟大定律：“每天上午十一点，就有食物降临。”它在感恩节早晨向火鸡们公布了这个定律，但这天上午十一点食物没有降临，农场主进来把它们都捉去杀了。

也許我們所依靠的科學隨時會在『神』隨意的捉弄下，從而崩潰。

Do not panic!

其實我們本來就對此無能為力，還不如好好地**繼續信賴以往所依靠的信仰，好好快活一輩子**。對在下來說，科學是信賴的首選，不過**科學可不是萬能的，它就安慰不了非理性的人**，所以若要信從宗教也無妨。

不過，說穿了，是否相信科學，其實也意味著**是否相信他人**。畢竟大家所學習到的大多『科學』知識，**就是通過『他人』所傳授的**，雖說有些所學習到的知識也可以通過『實驗』來證偽。但生活本來又不是科學範疇的全部，**很多信息就只能通過所信任的他人來汲取了**，就像『人文』一樣。

但是，畢竟純粹由他人所提供的信息並不如科學可靠，或被實驗是否具備可證偽性。**他人向您提供了虛假的信息，從而『欺詐』，從來也不是不可能的**，其實這就屬於**『社會工程學』**的範疇。作為信息安全的重要議題之一，在下由衷地大家好好暸解下它，業界佳作為 [The Art of Deception][2]. 不過它畢竟是『人文』範疇，且在下本文只打算專注於『科學』上的探討，所以就不展開了。**其實若您在閱讀本文時同時抱著懷疑態度，那您在社會工程學上的造詣已算是登堂入室了。**

說了這麼多，其實是為了讓您好好思索下兩道問題：

1. 您願意相信**在下**嗎？
2. 您願意追求**科學**嗎？

若充分思索過並答覆均是，那就可以繼續了。

## 三大原理

### RSA 算法原理

既然要講究科學，首當其衝的自然是數論了，即密碼學中的基礎。

直接學習 [Discrete Mathematics and Its Applications][3] 以下四章即可，別忘多做對應的大量習題：

* 3.4 The Integers and Division
* 3.5 Primes and Greatest Common Divisors
* 3.6 Integers and Algorithms
* 3.7 Applications of Number Theory

啃起來的確很苦逼，但能一勞永逸地打好密碼學所需的堅實數論基礎，過了這坎後面就輕鬆了。

其實有兩篇文章比較好快速上手：

* [RSA算法原理（一）][4]
* [RSA算法原理（二）][5]

但非常不推薦，因為有跳過若干理論，且因節奏太快，導致記憶容易不牢。不徹底貫通好 RSA 算法原理的話，後續的學習會棘手無比。不過倒是學習 Discrete Mathematics and Its Applications 之後很理想的總結材料。

為準確需要，定義**那一把不公開的密鑰為私鑰，另一把公開的密鑰則為公鑰**。那麼在這節您至少需要搞清：

1. 『對稱』與『非對稱』的區別
2. RSA 算法中 Key Pair 是否相對的，即能否把原公鑰用來加密，原私鑰用來解密？
2. 如果使用私鑰加密，公鑰解密的話，那能否使用其它公鑰解密？

RSA 算法的精髓在於『非對稱』，即：**生成兩把獨立的密鑰，且經過其中任意一把加密所得到的數據，就幾乎只能使用另一把來解密；幾乎無法通過所擁有的一把密鑰來推導出另一把密鑰。**如果您深得其意，便可放心繼續下一節了。

### Hash 校驗原理

[什么是哈希算法？][6]

[理论计算机初步：从hash函数到王小云的MD5破解][7] 科普了王小云教授的科研成果，其實張志強先生對 Hash 函數的點明也挺到位：

1. 任意y，找x，使得f(x)=y，非常困难。
2. 给定x1，找x2，使得f(x1)=f(x2)，非常困难。
3. 找x1，x2，使得f(x1)=f(x2)，非常困难

於是 Hash 函數的本質**在於對不同數據的高強度壓縮成同樣不同的字符串來，且幾乎無法針對已知的字符串結果逆向推導出原數據，從而無法通過構造特定數據來生成該字符串。**

於是它成了『文件校驗』極其可靠的途徑：**在優秀 Hash 算法下，只要文件本身有微小的數據變化，就立馬得到截然不同的字符串，從而表明文件已變動/損壞。**此外在『數字證書』也發揮著關鍵的作用，下文會分析。

常見的 Hash 算法則有：MD5, 下載工具經常用它來校驗文件完整性，[Arch Linux 的 PKGBUILD 文件][8]就有`md5sums`一項；SHA-1, Git 就用它來標記 Commit.

### 數字證書

阮一峰先生又科普了一篇好文：[数字签名是什么？][9]

不過講得還不夠清楚，以下是若干要點：

1. 生成 Digest 的意義何在？當然是文件校驗了，這便是 Hash 函數發揮關鍵作用的地方。
2. 為何可以私鑰加密公鑰解密？因為 RSA 算法具備『非對稱』的特徵。
3. 既然用私鑰加密，但公鑰不就本來公開的嗎？豈不是人人都可以解密了？[在下已經在評論區撥亂反正。][10]

然後就可以研究 Real Life 的 CA 了，首當其衝的便是中國大陸發行的 CA, 也順便再溫習溫習 CA, 畢竟有不少 Post 也很好地科普了 CA 體系:

1. [数字证书及CA的扫盲介绍][11]
2. [CNNIC证书的危害及各种清除方法][12]
3. [为什么不能信任 CNNIC 证书？][13]
4. [网上流传的所谓「支付宝偷偷添加根证书，将造成安全隐患」的说法是否正确？][14]
5. [12306.cn 购票为什么要安装根证书？？][15]
6. [为什么在12306买火车票要装根证书？][16]
7. [天朝颁发的证书一览表][17]

在下的做法是驅逐 CNNIC 證書，**這不是懷疑而是抵制**，畢竟就編程隨想所列舉的種種罪證，CNNIC 確實差勁到令人髮指。至於 Alipay 根證書，由於沒條件在 Windows 下實驗研究，且在已安裝 [AUR|aliedit] 的前提下，未在 Chromium 及 `update-ca-certificate` 追蹤路徑中發現任何簽發自 Alipay 的任何 CA, 於是就不再進一步評論了，但歡迎其它用戶補充。

此外在下同時對各大 Linux 發行版如何選擇 Built-In CA 產生了[好奇][18]，且發現 [Arch Linux][19] 使用 [Debian 的 ca-certificate][20], 後者由 [mozilla][21], [spi][22] 和 [cacert][23] 組合而成。[且在 testing 分支中已經加入了 CNNIC 根證書][24]，這下足夠牽一髮而動全身了。

## 應用

至此，三大原理已科普完畢，接著便是各種應用了：SSL, SSH, PGP, Hash checker, CA Mannage Tools.

### HTTP 與 SSL 的合體：HTTPS

在這裡，您最好具備一定的計算機網絡知識。

[https、SSL与数字证书介绍][25]

巧合的是，在碼本文的過程中，阮一峰先生又出臺了《[SSL/TLS协议运行机制的概述][26]》。

此外，GoAgent 之所以要導入證書，正因為它也要代理 HTTPS 協議，從而不得不提供它在 127.0.0.1 上的證書以『欺騙』瀏覽器及操作系統。此外，GoAgent 在 Arch Linux 上還被聖三十三大 TU 之一 [twitter|felixonmars] 添加了特性：`CA.crt` **隨機生成！**碉堡了。

### SSH

還是繼續由阮一峰先生兩文打頭陣...

1. [SSH原理与运用（一）：远程登录][27]
2. [SSH原理与运用（二）：远程操作与端口转发][28]

不過 V2EX 上有人對此提出質疑：[阮一峰blog里关于公钥登录的描述是不是有问题][29]。自己看看吧，在下就不評論了。

此外還有兩篇值得一提：

1. [GitHub Help 中的 SSH 章節][30]：Git 協議可以使用 SSH 協議加密。
2. [wik|SSH]: 對 Arch Linux 用戶來說真是最佳手冊。

### PGP

既然已暸解 RSA 算法，則可以挑一個好用的加密／解密工具了。

1. [GPG入门教程][31]：看阮一峰先生寫了這麼多，大夥兒不妨考慮 Donate 下吧，在下捐了 RMB 25. 此外在評論區中又發現了兩篇好文，其作者也是 Arch Linux 用戶哦，從ta博客上看得出挺有信息安全的造詣：[使用 GnuPG 实现电子邮件加密和数字签名——PGP 30分钟简明教程(1)][32] 及 [使用 GnuPG 实现文件加密和数字签名——PGP 30分钟简明教程(2)][33]
2. [wiki|GnuPG]: 狀哉我大 ArchWiki

GPG 在 Pacman 的 Signing 似乎也佔著重要地位：[wiki|pacman-key], 若琢磨透，那 Arch Linux 的安全就更加無懈可擊。此外值得一提的是 [haveged][34], 可供大量『熵』來初始化密鑰。

### Hash Checker

既然明白了 Hash 的原理，於是我們可以用 Hash checker 來專門校驗文件真實性和完整性。在下完善了 [Hash checkers][35] 條目，直接挑中意的工具即可。個人比較偏好 gtkhash, 不過 hashdeep 或許更合 CLI 狂的口味，其實大多 Linux 發行版內置的 [md5sum 用法][36]也很簡單易懂的。

### CA Manager

在下以為既然操作系統內置了那麼多證書，那麼邏輯會很複雜，所以就孜孜不倦不倦地尋找 GUI 工具——直到發現管理內置 CA 其實比想象中的還要容易得許多。

事實上，Arch Linux 只用一個來自 Debian 的`ca-certificate`包來內置 CA, 且這些證書全在`/usr/share/ca-certificate`內。

所以想刪除 CNNIC 證書時：

1. 編輯`/etc/ca-certificate.conf`，反註釋掉`mozilla/CNNIC_ROOT.crt` 一行
2. 執行`rm /usr/share/ca-certificate/mozilla/CNNIC_ROOT.crt`
3. 執行`update-ca-certificate

不過這個解決方案只臨時有效，下次更新時又會滿狀態原地復活。[twitter|felixonmars] 提供了專門人道清除 CNNIC 證書的自動化 patch, 雖然在下不太清楚其原理：

<blockquote class="twitter-tweet" lang="zh-cn"><p>我又捡起了以前弄的那个去掉 CNNIC 的 nss 补丁. patch本身放在 <a href="https://t.co/CzG9XNTY">https://t.co/CzG9XNTY</a> aur上放了俩包 <a href="https://t.co/dOTJaMc9">https://t.co/dOTJaMc9</a> 和 <a href="https://t.co/O3EfK27p">https://t.co/O3EfK27p</a></p>&mdash; Felix Yan (@felixonmars) <a href="https://twitter.com/felixonmars/statuses/297145331311841280">2013年2月1日</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

此外，當想在本地添加外來的證書時，以 GoAgent 為例：

    # mkdir /usr/local/share/ca-certificates/GoAgent
    # cp /usr/share/goagent/local/CA.crt /usr/local/share/ca-certificates/GoAgent
    # update-ca-certificates
    
神奇的`update-ca-certificates`啊！Unix 的『**一切皆文件**』哲學大大地優化了管理 CA 的效率。

## 物理安全

在下又不免想到：**既然證書那麼關鍵，那麼會不會有專門纂改證書的計算機病毒呢？**[果不出所料][37]，於是這就算是操作系統負責的安全範疇了。但是在下卻發現，若只要用戶已取得計算機控制權，則修改證書易如反掌。於是軟件安保措施無論做得再怎麼嚴密，仍無法阻止 Cracker 在物理上奪取控制權從而危及計算機的信息安全。從這點上來說，手機支付寶其實就就屬於物理安全的範疇：[物理安全是所有安全要素的根本][38]。

又想起很久以前讓在下印象深刻的一文 [Google 大秀他们数据中心的安保措施][39]，這算得上物理安全保護措施的典範了吧。

至於安全保障方案，日後待擬。

## 作業

到此圖已繪畢，在下姑且再給出最後一道有趣的作業：**如何通過在本文索到的知識，來更快、更高、更强地科學上網？**以下為若干提示：

1. GoAgent 亞全局代理
2. SSH 加密代理, 比如 IRC 協議
3. 全程使用 HTTPS 協議
4. 管理 CA, 比如人道大清洗某些證書
5. 人肉翻牆（畢竟它可謂屬於物理安全的範疇……同時，也是最終解決方案！

> Written with [StackEdit](https://stackedit.io/).


  [1]: http://arch.acgtyrant.com/2014/02/01/cli-vs-gui/
  [2]: http://book.douban.com/subject/1498757/
  [3]: http://book.douban.com/subject/3125432/
  [4]: http://www.ruanyifeng.com/blog/2013/06/rsa_algorithm_part_one.html
  [5]: http://www.ruanyifeng.com/blog/2013/07/rsa_algorithm_part_two.html
  [6]: http://www.zhihu.com/question/20820286
  [7]: http://zhiqiang.org/blog/science/computer-science/preliminary-computer-theory-xiao-yun-wang-from-the-hash-function-to-crack-md5.html
  [8]: http://arch.acgtyrant.com/2013/12/26/arch-linux%27-soal-pkgbuild,-aur-and-abs/
  [9]: http://www.ruanyifeng.com/blog/2011/08/what_is_a_digital_signature.html
  [10]: http://www.ruanyifeng.com/blog/20120111/08/what_is_a_digital_signature.html#comment-299452
  [11]: http://program-think.blogspot.com/2010/02/introduce-digital-certificate-and-ca.html
  [12]: http://program-think.blogspot.com/2010/02/remove-cnnic-cert.html
  [13]: http://www.zhihu.com/question/20746900
  [14]: http://www.zhihu.com/question/22306245
  [15]: http://www.zhihu.com/question/19974739
  [16]: http://www.williamlong.info/archives/3461.html
  [17]: http://www.v2ex.com/t/58891
  [18]: http://unix.stackexchange.com/questions/113639/how-it-is-decided-which-certificate-of-a-certificate-authority-will-be-used-in-a/113777#113777
  [19]: https://projects.archlinux.org/svntogit/packages.git/tree/trunk/PKGBUILD?h=packages/ca-certificates
  [20]: http://packages.qa.debian.org/c/ca-certificates.html
  [21]: http://www.mozilla.org/en-US/about/governance/policies/security-group/certs/
  [22]: http://www.spi-inc.org/
  [23]: http://www.cacert.org/
  [24]: http://sources.debian.net/src/ca-certificates/20130906/debian/changelog?hl=294#L294
  [25]: http://blog.sae.sina.com.cn/archives/2101
  [26]: http://www.ruanyifeng.com/blog/2014/02/ssl_tls.html
  [27]: http://www.ruanyifeng.com/blog/2011/12/ssh_remote_login.html
  [28]: http://www.ruanyifeng.com/blog/2011/12/ssh_port_forwarding.html
  [29]: http://www.v2ex.com/t/89578
  [30]: https://help.github.com/categories/56/articles
  [31]: http://www.ruanyifeng.com/blog/2013/07/gpg.html
  [32]: http://archboy.org/2013/04/18/gnupg-pgp-encrypt-decrypt-message-and-email-and-digital-signing-easy-tutorial/
  [33]: http://archboy.org/2013/05/15/gnupg-pgp-encrypt-decrypt-file-and-digital-signing-easy-tutorial/
  [34]: https://wiki.archlinux.org/index.php/Pacman-key#Initializing_the_keyring
  [35]: https://wiki.archlinux.org/index.php/List_of_applications/Security#Hash_checkers
  [36]: https://help.ubuntu.com/community/HowToMD5SUM
  [37]: https://twitter.com/m13253/status/431043473702010880
  [38]: http://leonax.net/p/5371/physical-security-is-the-fundamental-of-security/
  [39]: http://www.guao.hk/posts/security-and-data-protection-in-google-data-centers.html
