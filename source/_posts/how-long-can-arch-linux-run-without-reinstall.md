title: How long can Arch Linux run without reinstall
date: 2013-11-03 16:04:23
tags:
- 其它
---

原諒在下用英文標題，事實上還真想不出能更直截了當的中文標題。

Twitter 上 @mariotaku & @bigeagle_xd & @upsuperx 等人展開了[友好而熱烈的討論][1]。於是“我突然感到有必要统计 Arch Linux 生存时间了。”

首先下 **Arch Linux 無重裝運行時間**的操作性定義：<s>**運行`less /var/log/pacman.log`</s>，**运行`head /var/log/pacman.log`**，第一行所表明的時間為起始時間，再對當前時間`date`作出相減即可。**

![看來實際上有快四月多了，比我想象的還要短...][2]

（其實這實驗方法不怎麼好，畢竟理論上應該有更複雜的命令來直接計算精確的運行時間，希望能有資深用戶給出更棒的命令

此外，Arch Linux Forum 上也有相關的討論：[How long have you been without a reinstall？][3]雖然已經是 2008 年的老帖了，不過參考下也無妨，特別翻譯若干 Post 如下：

> In my home I have Arch running on three boxes, while I performed only
> one install procedure almost 4 years ago. During that time I changed
> disks and other hardware number of times, did a lot of experimenting
> and risky stuff too.
> 
> （我老家有三臺跑 Arch Linux 的主機，而且自四年前起，總共就只裝了一次。不過我還是有試過換硬盤、還修改硬件參數呢。

> Reinstall ??  What is that ?
> 
> （重裝是啥？能吃嗎？
> 
> I maintain several Arch workstations which are at least a year old
> installations, these are updated most of the time, and never had
> problems with that.
> 
> My Desktop on the other hand... I Installed Arch on in at least 4
> times in the past year but only because I had to... added/removed
> RAID, changed RAID configurations.. etc.
> 
> I had a very unpleasant one with my fit-pc appliance though, after an
> update kernel panic.. and it totally sucks on an appliance - I had to
> reinstall then, but I guess if I was stubborn enough I could have
> saved it.
> 
> So I think the bottom line from my perspective is, that Arch is an
> adventure, but if you got skills you will get out of any tough
> situation smile
> 
> （我有在維護N臺 Arch
> 工作站，且自安裝時間起至少也有一年多了，並且常保持更新，從未出問題過。不過桌面計算機就可難說了，過去一年至少有施展四次必殺：重裝大法！雖然全是為了調整
> RAID 而已。不過還有一次不愉快的精力，一套應用軟件在一次 Kernel Panic
> 後就完全沒法用了，不得不重裝，雖然理論上來說應該也可以不用重裝的。
> 
> I never reinstall my ArchLinux distro since July 2005 ... but, a clone
> my hd (with archlinux of course ;-)) when i upgrade my pc...
> 
> （2005年7月以來我就沒再重裝過了，不過倒是在換機器的時候有進行一次乾坤大挪移過XD
> 
> My first and only installation on this machine: 17 April 2006  I've
> installed Arch on my laptop, my girlfriend pc, some PCs and other
> three PCs in the company where I work without a single reinstall.
> 
> When I was in Paris I haven't updated some machines for 7-8 months
> (during the modular xorg transition), as soon as I went back and after
> about 700-800 MB of download everything was up to date without much
> fuss.
> 
> （我有史以來在這些機器上就裝了一次
> Arch：2006年4月17日起，本家筆記本，女朋友專用臺機，大大小小的其他主機，包括公司的三臺工作機在內，且更是從來沒掛過。
> 
> 在巴黎的時候，一些主機已經有七八月沒更新過了，那時候還正值 xorg 更新換代。當我到家時，就轉身嘩嘩麗麗地衝向主機並一命令更新，一共下載了
> 700-800 MB 多，總算又煥然一新，得來全不費工夫，嘖嘖。

此外，有必要搞明白一點：**如此長的無重裝運行時間並不意味著全程無麻煩**，畢竟可能還是會遇到眾多大大小小的麻煩，又是繁瑣更新又是看公告的，雖然問題也幾乎從來不會嚴重倒需要重裝的程度。所以以上實例，最多也就證明了：**在定在期更新，高度關注公告並服從更新說明的前提下，Arch Linux 可以非常穩定地滾動更新長達N年。**

諸位，**乃們的無重裝運行時間究竟有多久了呢？**歡迎在 Disqus 貼圖，期待能有打破4年記錄的高人出現，以證明 Arch Linux 也能很穩定。

Mon Nov  4 21:14:02 CST 2013 Updated:
目前 Arch Linux 中文用戶保持的無重裝運行時間最高記錄為依雲：[2010-09-18 03:37]
installed filesystem (2010.02-4)！（啪啪啪（鼓掌


  [1]: https://twitter.com/upsuperx/status/396846989599444992
  [2]: https://lh3.googleusercontent.com/-CpkM1e217ak/UnX0lCxRu_I/AAAAAAAAERs/TohKrcnc4H4/w1044-h358-no/2013-11-03-145924_1365x468_scrot.png
  [3]: https://bbs.archlinux.org/viewtopic.php?id=51154
