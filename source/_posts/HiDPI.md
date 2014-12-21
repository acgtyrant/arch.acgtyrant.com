title: HiDPI
date: 2014-11-11 14:43:56
tags:
- ArchWiki
---

我買不起 Apple 產品，自然也就一直不怎麼關注 Apple 各種產品與技術，包括二〇一二年大熱的 Retina, 對它也就只停留在「哇噢，超高分辨率！」的印象上。

您或許需要先被科普下「[分辨率](http://zh.wikipedia.org/zh/%E5%88%86%E8%BE%A8%E7%8E%87)」、「[顯示分辨率列表](http://zh.wikipedia.org/wiki/%E6%98%BE%E7%A4%BA%E5%88%86%E8%BE%A8%E7%8E%87%E5%88%97%E8%A1%A8)」和「[像素](zh.wikipedia.org/wiki/像素)」等。

直到今天偶然閱讀了[到底什么是 Retina Display（视网膜显示屏）？](http://www.zhihu.com/question/20260215/answer/14521344)方才豁然開朗：所謂的 Retina 原來是 **OS X 和第三方應用程序配合 HiDPI 所帶來的最佳顯示體驗**啊！這裏的「最佳」定義之一爲**肉眼在一定視線距離下可分辨的最大分辨率**，也就是說[實現了 Retina 的不同 Apple 設備，其分辨率就會因爲使用視線距離不同而不同。](http://www.zhihu.com/question/24935579/answer/29504330)當然， Retina 體驗還與對比度、亮度等有關。

Retina 這麼好，Linux 也不是不能辦到。

首先要有一個 HiDPI Screen, 其中譯爲「高分屏」，的確如同字面上的意思，即擁有超高分辨率的一塊屏幕。不過一般來說，十三寸、十五寸 Laptop 應該分別以 MacBook Pro with Retina 本身的分辨率即 2560 ×  1600 或 2880 × 1800 爲準，畢竟已經達到肉眼所能分辨的最大極限了。其它寸也如法炮製。

Linux 內核能通吃天下幾乎一切硬件，硬件上應該沒有問題。於是關鍵還是應用程序方面對 HiDPI 的支持，包括桌面環境和圖形庫在內。

其實……呔！ArchWiki 已經有 [HiDPI](https://wiki.archlinux.org/index.php/HiDPI) 條目。據我所知，GNOME 對 HiDPI 的支持已經相當成熟，Hexcles Ma 對此有評測：[Windows 7/8.1、GNOME 3 对高分屏的支持](http://blog.robotshell.org/2014/hidpi-support-in-windows-7-and-8-1-and-gnome-3)；KDE 好像還要等到全面遷移到 Qt5 才行，後者正式支持 HiDPI; GTK+ 將來也有望支持；[御用窗口管理器 i3 也不負衆望](https://faq.i3wm.org/question/3623/hi-dpi-support/)，雖然官方表示它只能管好自己，對別的應用程序就愛能莫助了，於是我不太清楚字體在 i3 in HiDPI 上會表現得如何。