title: 字體及其渲染
date: 2015-01-03 12:21:40
tags:
- ArchWiki
---
我一直覺得我 Arch Linux 上的字體渲染有待進一步優化，爲此收集了一大堆資料，什麼微調啊，渲染啊，點陣啊，infinality 啊，讀起來挺扶額的。

但我決定直接向一直被讚許有加的 Ubuntu 和 OS X 看齊，如果差距並不大，那麼就沒必要仔細研究字體渲染原理及優化方案了。

![我的 Arch Linux 字體渲染效果圖](https://lh4.googleusercontent.com/-ZfDRusnR8mY/VKdpmkGiG1I/AAAAAAAAJxk/pa2KHpbPIoM/s0/DeepinScreenshot20150103120112.png)

![李先生發來的 Ubuntu 字體渲染效果圖，當時沒交代清楚，他截了臺式機上的……](https://lh5.googleusercontent.com/-yyLEup7ybps/VKdpYOSpaEI/AAAAAAAAJxQ/JeC2SQmaV44/s0/%25E9%2580%2589%25E5%258C%25BA_355.png)

但是 OS X Retina 下的字體渲染效果在低分屏下果然是看不出來的。也罷。

對比了下，Ubuntu 字體渲染略朦朧，但並不足夠吸引我。於是我就不再折騰字體了，也不翻譯相關 ArchWiki 條目。如果您仍對字體渲染機制與優化方案頗感興趣，按以下繼續展開研究即可，若能發表總結文／翻譯 ArchWiki 條目就更好。

首先是至高無上的 ArchWiki!

* [Fonts - ArchWiki](https://wiki.archlinux.org/index.php/Font)
* [Font configuration - ArchWiki](https://wiki.archlinux.org/index.php/Font_configuration)
* [Infinality - ArchWiki](https://wiki.archlinux.org/index.php/Infinality)

其它資料：

* [微軟爲什麼不改善 Windows 的字體渲染？ - 知乎](http://www.zhihu.com/question/21829301)
* [OS X 和 Windows 的字体渲染有什么区别？ - 知乎](http://www.zhihu.com/question/19573048)
* [Windows Vista 之后的中文字体渲染效果不佳，为什么微软不改变？ - 知乎](http://www.zhihu.com/question/20212295)
* [阅读字体：衬线与渲染 – techo](http://cinvro.com/post/read-typography/)
* [arch的LCD字体渲染优化 - 查看主题 • Ubuntu中文论坛](http://forum.ubuntu.org.cn/viewtopic.php?f=155&t=262405)
* [对比了一下文泉驿微米黑、文泉驿正黑、微软雅黑和冬青黑体(苹果丽黑)。 - 查看主题 • Ubuntu中文论坛](http://forum.ubuntu.org.cn/viewtopic.php?f=8&t=394169)
* [怎么把字体变得跟ubuntu一样圆滑？最近转到arch了 - 查看主题 • Ubuntu中文论坛](http://forum.ubuntu.org.cn/viewtopic.php?f=8&t=368351)
* [字型粗細問題？ (第 1 頁) / 初學者園地 / Arch Linux 中文社區](http://archlinux.alone.tw/bbs/viewtopic.php?pid=2012)
* [ArchLinux下的字体基本配置方法 (针对液晶显示器) at im rem1x.](http://imxie.net/2010/06/basic-lcd-font-config-on-archlinux.htm)
* [求助, Arch 字体渲染问题 - Google Groups](https://groups.google.com/forum/#!msg/archlinux-cn/-6KGX4VQAmQ/NUFM1EmOOugJ)
* [[原创]史上最强（伪）的合成字体DejaVuSansYuanTi - 查看主题 • Ubuntu中文论坛](http://forum.ubuntu.org.cn/viewtopic.php?f=8&t=110509&sid=52e087184a04d097119d2c9ab4c3a706)
* [Linux字体美化实战(Fontconfig配置) [金步国]](http://www.jinbuguo.com/gui/linux_fontconfig.html)
* [Perfect Font Rendering! | I'm TualatriX](http://imtx.me/archives/1315.html)
* [WebKit一定要啟用Pango字體渲染 | I'm TualatriX](http://imtx.me/archives/1332.html)
* [openSUSE 上的 infinality – 陈三](http://www.zfanw.com/blog/opensuse-infinality.html)
* [字体](http://i.linuxtoy.org/docs/guide/ch19s07.html)
* [Ubuntu 字体设置与 infinality – 陈三](http://www.zfanw.com/blog/ubuntu-font-render-with-infinality.html)
* [点阵字体，次像素渲染，再见 | FREDERICKJOE'S BLOG](http://blog.hfq.me/adios-low-resol.html)
* [有关字体（2）——渲染 | FREDERICKJOE'S BLOG](http://blog.hfq.me/about-fonts-rendering.html)
* [QML Scene Graph 的文本渲染 | I, KDE](http://www.ikde.org/program/qml-scene-graph-text-render/)

最後，御用字體是：

1. Droid Sans Mono for Powerline
2. 文泉驛微米黑
3. 文泉驛等寬微米黑
4. 方正蘭亭黑
5. 思源黑體

可能有不少更好的英文字體，但 Droid Sans Mono 已經夠滿足我，無意再物色；其它四種中文字體大同小異，就不排名了。