title: Mirrors
date: 2015-02-25 11:06:18
tags:
- ArchWiki
---

说实话我一直没彻底分清 Repository 和 Mirror 的区别，直到今天好好钻研 [Mirror](https://wiki.archlinux.org/index.php/Mirrors) 了一番，颇为豁然开朗，下文有时会用「镜像」代替 "Mirror", 其维基条目已有对应的中文翻译，哪天我心血来潮了就优化下。我在[非官方镜像](https://wiki.archlinux.org/index.php/Mirrors#China) 删除了已进官方镜像列表的和停止维护的，还补充上了 [【最新整理】中国大陆开源软件镜像服务站点列表](http://code.csdn.net/news/2823301) 的若干新镜像，将来我还会游说它们主动申请进 Official Mirrors.

哪家镜像强？这都成 Arch Linux 中文社区的周经问题了。光口头向他人求助多没劲，直接看 [Sorting Mirrors](https://wiki.archlinux.org/index.php/Mirrors#Sorting_mirrors)即可，用 [Reflecotr](https://wiki.archlinux.org/index.php/Reflector) 最一劳永逸：`sudo reflector --verbose --country 'China' -l 5 -p http --sort rate --save /etc/pacman.d/mirrorlist`, 不过要注意**它会自动忽略那些非最新镜像**。

此外 Felixonmars 讲到：[进 Official Mirrors 的门槛](https://wiki.archlinux.org/index.php/DeveloperWiki:NewMirrors)其实挺低，大陆绝大多家 Mirror 应该都能满足；Arch Linux 唯一的中央镜像级别为 Tier 0, 地址公开，但访问要密码； Tier 0 下级为 Tier 1, 后者向前者 pull 过来更新，Tier 2 同理；很遗憾，目前**大陆仍然没有一家 Arch Linux 镜像能够到达 Tier 1 水准**。

如果您看到有些镜像有好些 Repository 的时间相当久远，不用太吃惊，那只不过是目录变动时间，若要看镜像同步时间，看 `lastsync` 和 `lastupdate` 即可。

最后再表扬下一些镜像：

1. [浙江大学镜像官网](http://mirrors.zju.edu.cn/)排版十分上乘，拼写也非常正确！
2. [北京理工大学开源软件镜像服务](http://mirror.bit.edu.cn/web/) 不论在排版还是拼写上，也与浙江大学镜像不分伯仲。它不光额外包含了众多开源软件库，还提供了两部有趣的影视作品。
3. [中国科技与技术大学](https://mirrors.ustc.edu.cn/) 除了同样出色的排版与拼写之外，还提供了 HTTPS 协议镜像，它可能是大陆唯一这么办的。


> Written with [StackEdit](https://stackedit.io/).
