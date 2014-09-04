title: 電子商務在 Arch Linux 下的簡易解決方案
date: 2014-02-20 23:01:32
tags:
- 中國特色解決方案
- Linux
---
掐指一算，在下已經寫了五篇[中國特色解決方案][1]了呢：

1. 辦公軟件：[WPS Office for Linux：Linux Office 的希望之星！][2]
2. 科學上網：[Arch Linux 科學上網方案其一：GoAgent][3]
3. QQ: [QQ 在 Arch Linux 下的解決方案][4]
4. 網上銀行：[浦發銀行網上銀行 在 Linux + Chrome 下的初體驗][5]
5. 科學上網：[Arch Linux 科學上網方案其二：Shadowsocks][6]

原本還打算乘勝追擊，再寫個『**電子商務**』條目，旨在為廣大中文 Arch Linux 用戶提供網上銀行、支付寶等等的一系列解決方案。不過後來發現其實寫不了多少，且[就爲什麼支付寶使用用戶體驗欠佳的安全控件，而國外 Paypal 沒有這種的問題？][7]的一系列答案來看，想必將來信用卡支付取代障礙重重的傳統網上支付手段是一大趨勢。

就不再試圖在 ArchWiki 新建立該條目了，姑且改成獨家博客發佈吧w

## 支付寶

### 安全控件 for Linux

在下早先試過來自官方渠道的安全控件，但壓根不奏效；[AUR|aliedit] 卻倒有效，一命安裝即可。

此外，知乎上有人對支付寶安全控件提出了質疑：[網上流傳的所謂「支付寶偷偷添加根證書，將造成安全隱患」的說法是否正確？][8]在下檢查了 Chromium 及 update-ca-certificate 追蹤路徑，倒沒有發現任何發自 Alipay 的任何證書。

### 短信驗證

但據傳說中的聖三十三大 Arch Linux Developer [twitter|felixonmars] 所說，其實如今安全控件 for Linux 已經不再是必須的了，官方已一律改用短信驗證。這說法有待考證，不過在下以前在支付時，的確要通過短信驗證。

### 手機寶令

在寫《信息安全的一次深入淺出》的過程中，在下特地重新檢查、進一步強化了支付寶的安全措施，這次就試試了『[手機寶令][9]』。

發現它更可以代替短信驗證，如今支付時，只要輸入『支付密碼』和『手機寶令』就可以了，不光消除了短信被竊聽的可能性，而且應該遵循了[一次一密碼][10]的原理，安全更加無懈可擊。就目前來看，這對擁有智能手機的 Linux 用户应该是最佳支付寶支付解決方案了。

## 網上銀行

<blockquote class="twitter-tweet" lang="zh-cn"><p>别tmd抱怨网银不支持linux。建行、招行、浦发行，这三个行是我知道在Linux下能完全正常使用网银的银行。你自己做的选择，别抱怨。</p>&mdash; 一阁 (@yegle) <a href="https://twitter.com/yegle/statuses/29580740845">11月 3, 2010</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

**直接去找一家對 Linux 用戶友好的銀行，是足夠一勞永逸的網上銀行解決方案。**更多信息，可以直接訪問[网上银行兼容性列表][11]即可，在此對张韡武先生，哲思社區，及廣大作出貢獻的用戶深表感謝。不過說實話，在下覺得那家用戶界面有待進一步優化，以後時機成熟時會大刀闊斧地助其改版的。

[於是在下雷厲風行地行動，以表支持對 Linux 用戶友好的浦發銀行。][12]

如果您仍舊試圖想辦法讓那些不作為的網上銀行能在 Linux 下使用，只能說**大多中文 Linux 用戶真的太沒骨氣了**。

話雖如此，傳說中的聖三十三大 Arch Linux Developer [twitter|felixonmars] 剛好出臺了《[Pipelight – 让 Linux 原生 Chromium/Chrome 无缝支持 ActiveX 控件 (看! 网银!)》][13]，有需求的可以看看，但恕在下不對此解決方案作出任何承諾。

> Written with [StackEdit](https://stackedit.io/).


  [1]: http://arch.acgtyrant.com/tags/%E4%B8%AD%E5%9C%8B%E7%89%B9%E8%89%B2%E8%A7%A3%E6%B1%BA%E6%96%B9%E6%A1%88/
  [2]: http://arch.acgtyrant.com/2013/11/09/wps-office-for-linux/
  [3]: http://arch.acgtyrant.com/2013/11/16/goagent/
  [4]: http://arch.acgtyrant.com/2013/11/20/qq-for-arch-linux/
  [5]: http://arch.acgtyrant.com/2014/01/08/spdb-in-chrome-for-linux/
  [6]: http://arch.acgtyrant.com/2014/01/22/shadowsocks/
  [7]: http://www.zhihu.com/question/19559480?rf=20529925
  [8]: http://www.zhihu.com/question/22306245
  [9]: http://home.alipay.com/security/securityMobileOtp.htm
  [10]: http://blog.yegle.net/2010/08/29/yubikey-the-cheap-otp-solution/
  [11]: http://openbanks.info/
  [12]: http://arch.acgtyrant.com/2014/01/08/spdb-in-chrome-for-linux/
  [13]: http://blog.felixc.at/2014/02/pipelight-let-linux-native-chromium-chrome-support-activex-seamlessly/
