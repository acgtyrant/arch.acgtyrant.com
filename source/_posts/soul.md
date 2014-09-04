title: Arch Linux 的靈魂：PKGBUILD、AUR 和 ABS
date: 2013-12-26 22:32:29
tags:
- Arch 真諦
---
在下先前在 [LinuxTOY][1] 上看到了該文，覺得是非常很好的 Arch Linux 傳道文，特此重新大幅度優化排版並更新了部分過時內容，以饗讀者。此外難免會有疏漏之處，歡迎斧正。

**版權特定聲明：**

 1. 原載：https://linuxtoy.org
 2. 作者：Ning Bao
 3. 原文網址：https://linuxtoy.org/archives/archlinux-pkgbuild-aur-and-abs.html

Updated 1: 感謝 [twitter|lilydjwg] 進一步大力斧正過時內容！
Updated 2: 感谢 [twitter|felixonmars] 提供了种种宝贵的意见！

注意：在嘗試本文提供的種種練習前，確保已經安裝了 `base-devel`

## PKGBUILD 和 makepkg

其实，我使用 Arch Linux 的时间并不是很长。可是，就是在这半年的时间内，我感觉我学到了很多的东西，对 GNU/Linux 有了更多的了解，也在这个过程中深深地爱上了 Arch Linux 这个发行版。

首先声明一下，我不是一个程序员，从来没有写过真正的 Code，顶多是写一点 scripts，或者做一些简单的网页什么的。和很多人一样，我对计算机的接触是从 DOS/Windows 开始的。Windows 的图形界面很容易学。可是时间长了，**Windows 就会运行的越来越慢，我的硬盘上也就会有很多我根本不知道是什么的东西。**而且，**在 Windows 上很多东西都是设定好的，改变起来非常不容易。**不要跟我提注册表，那个东西实在是让我一头雾水。还有，大部分 Windows 上的软件都不是自由软件。**这意味着人们很难了解这些软件内部的情況，你可能在毫无察觉的情况下就中了病毒或木马。**

所以，为了能够完全了解和控制我每天工作生活要用的计算机，我开始学着使用 GNU/Linux。我一开始是用 Mandriva（那个时候还叫 Mandrake Linux）。后来是 Ubuntu（也包括其他一些 Debian 为基础的发行版）。Wow！我一用上 Ubuntu 就有了完全不同的感觉。特别是非常好用的 apt-get，加上庞大的自由软件库，让我大开眼界。可是在使用 Ubuntu 一段时间以后，我发现这个平台实在和 Windows 非常相似。Gnome 和 KDE 的界面都是在模仿 Windows。更糟糕的是，Ubuntu 会在一开始安装一些乱七八糟的东西，大大影响了我的电脑的运行速度。我需要一点一点把我不用的东西去掉，这个过程真的很不爽。我开始问自己为什么要放弃 Windows 呢？

Ubuntu 有一个很大很好的用户社区，很多问题都可以在讨论区得到解决。然而，**Ubuntu 的用户完全要依赖 Maintainer**。我就有过这样的经历，在发现一个 Bug 后得到很多其他人的确定，可是 Maintainer 迟迟不作修改。还有，也许有很多人都很想用一个比较新的软件，但是大家都要等到有人能够而且愿意作 Maintainer 之后，这个软件才会在 Repository 里出现。**我或许能够在调试后自己从源代码编译，可是我要如何和别人分享我的成果呢？**

其实，各种 Linux 发行版在本质上没有什么不一样。大家使用的软件都是要从源代码编译生成可以运行的二进制码。如果没有 rpm、apt-get 或者 pacman，我们也是可以快乐生活的。只不过，我们的生活会变得麻烦一些。如果要从源码安装一个软件，我们通常是要做如下的步骤：

``` shell
wget http://somewhere.org/source/package.tar.gz # 下载源代码
tar xvzf package.tar.gz # 解压缩
cd package # 进入源代码目录
./configure # 设定
make # 编译
make install # 安装
```

如果我们要像这样安装一个两个软件是没有什么问题的。但是如果我们要对付成百上千的软件／类库的话，这样的土办法是行不通的。于是出现了不同的 Linux 发行版，**他们之间的区别只是在于如何管理成百上千的软件，特别是不同软件／类库之间互相依存的关系，也就是 dependency 的问题。**

大多数 Linux 发行版都是以二进制包为基础的，这其中又分 Redhat（还有 SUSE、Fedora 等）、Debian（还有 Ubuntu、PCLinux 等）和 Slackware 阵营。为了解决管理大量软件包的问题，这些发行版采取了这样一个办法。**他们找了一群大牛程序员来作 Maintainer，这些 Maintainer 负责把源代码编译成二进制码，加上一些控制信息（比如如何安装、dependency 等），然后一起打包放在服务器上。所以，最终用户根本不用接触源代码。**如果你有兴趣的话，你可以抓一个 Debian 的 DEB 文件下来研究一下： 

``` shell
wget http://somewhare.org/package.deb
tar vx package.deb
```
    
你会发现你多了三个文件： `debian-binary`，`control.tar.gz`，`data.tar.gz`。

然后再用 `tar tzvf` 命令看一看 `control.tar.gz` 和 `data.tar.gz` 里面有什么东东，你就明白神奇的 dpkg/apt-get 是怎么一回事情了。

二进制包固然是很方便，但是这种办法有一个很大的问题。**那就是最终用户受到 Maintainer 很大的控制**。比如说，我们并不知道 Maintainer 在编译的过程中是如何设定的（./configure）。如果我们要用不同的设定，就要自己从源代码从头开始。另外，如果某一个 Maintainer 心术不正，在二进制包里面加了木马程序，我们这些最终用户是很难察觉的。还有，设想一下如果某一个 Maintainer 外出休假了，那么你的软件也就不能及时更新了。

所以，**也有一些发行版采取了完全不同的办法，这些发行版是以源代码为基础的。Gentoo 就是其中的代表。**如果你用过 Gentoo 你就会知道 ebuild 文件。你如果有兴趣，可以从 http://packages.gentoo.org/ 抓一个 ebuild 文件研究一下。你会明白 **Gentoo 的用户其实从 Gentoo 得到的只有这些 ebuild 文件，在每一个 ebuild 文件里包含了安装使用一个软件需要的所有信息（从哪里下载源代码、如何编译、如何安装还有 dependency 的问题等）。之后，Gentoo 的用户用 emerge 命令按照 ebuild 文件的指示编译、安装一个软件。Gentoo 用户可以使用 USE 等变量来选择启用或者禁用软件的一些功能。**这样做的好处是，Gentoo 的用户可以一目了然地了解每一个软件的编译、安装的过程。如果需要的话，Gentoo 的用户可以修改 ebuild，按照自己的需要编译一个软件。

我也用过 Gentoo。不过对于我这样的初学者，Gentoo 实在是太复杂了，有太多的参数要设定，ebuild 的编写也不是那么简单。还有，**Gentoo 几乎不提供任何二进制包，所以绝大部分的软件都要从源代码编译，这是一个非常慢的过程。**其实在大部分情况下，用户对一些软件的设定都是差不多的，没有必要让每一个 Gentoo 的用户都从头编译。所以，我需要找到一个发行版，既有 Debian 的易用性，又有 Gentoo 的灵活性。

我因此找到了 Arch Linux。那么 Arch Linux 又是如何解决从源代码到二进制码的问题呢？Arch Linux 使用了 **makepkg** 这样一个工具。**makepkg 会按照 PKGBUILD 文件生成一个二进制包**。有些时候，**makepkg 还需要 install 文件（主要用来显示提示信息、备份用户设置等）和其他的配置文件以及补丁等**。那么 PKGBUILD 是什么呢？PKGBUILD 和 Gentoo 的 ebuild 一样，**包含了安装使用一个软件需要的所有信息**。下面是 dwm（一个非常非常简捷、高效的窗口管理器）的 PKGBUILD 文件：

``` shell
# $Id$
# Maintainer: Sergej Pupykin <pupykin.s+arch@gmail.com>
# Contributor: Dag Odenhall <dag.odenhall@gmail.com>
# Contributor: Grigorios Bouzakis <grbzks@gmail.com>

pkgname=dwm
pkgver=6.0 # 软件版本
pkgrel=1 # 打包的版本
pkgdesc="A dynamic window manager for X" # 软件说明
url="http://dwm.suckless.org" # 官方网站
arch=('i686' 'x86_64') # 适用平台
license=('MIT') # 版权声明
options=(zipman) 
depends=('libx11' 'libxinerama') # 依赖
install=dwm.install
source=(http://dl.suckless.org/dwm/dwm-$pkgver.tar.gz
	config.h
	dwm.desktop) # 需要的源文件
md5sums=('8bb00d4142259beb11e13473b81c0857'
         '2453e037f46449774ec8afab49b4f1a2'
         '939f403a71b6e85261d09fc3412269ee') # MD5 校验码

build() {
  cd $srcdir/$pkgname-$pkgver
  cp $srcdir/config.h config.h
  sed -i 's/CPPFLAGS =/CPPFLAGS +=/g' config.mk
  sed -i 's/^CFLAGS = -g/#CFLAGS += -g/g' config.mk
  sed -i 's/^#CFLAGS = -std/CFLAGS += -std/g' config.mk
  sed -i 's/^LDFLAGS = -g/#LDFLAGS += -g/g' config.mk
  sed -i 's/^#LDFLAGS = -s/LDFLAGS += -s/g' config.mk
  make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11
} # 编译过程

package() {
  cd $srcdir/$pkgname-$pkgver
  make PREFIX=/usr DESTDIR=$pkgdir install
  install -m644 -D LICENSE $pkgdir/usr/share/licenses/$pkgname/LICENSE
  install -m644 -D README $pkgdir/usr/share/doc/$pkgname/README
  install -m644 -D $srcdir/dwm.desktop $pkgdir/usr/share/xsessions/dwm.desktop
}
```
    
我们可以注意到在“编译过程”这个部分，很多代码都和我们在 shell 里编译的命令一样。对！Arch Linux 不要求用户学习太多新的东西，PKGBUILD 很容易理解，因为里面都是基本的 shell 命令。

好，我们把 [PKGBUILD][2]，[dwm.install][3]，[dwm.desktop][4] 和 [config.h][5]（dwm 比较特殊，config.h 包含所有的配置信息，所以要在编译之前提供。其他的软件大多依靠外部的配置文件，像是 `.bashrc` 等）放在一个新的目录里之后。我们执行：

    makepkg

之后，你会发现这个目录里出现了一些新的东西，包括：`dwm-6.0-1-x86_64.pkg.tar.xz`，`dwm-6.0.tar.gz` 两个文件，还有两个目录：`src`，`pkg`.

通过比较这些文件、目录里的内容和 `PKGBUILD`，再留意下`makepkg`的输出，你就会明白 `makepkg` 到底做了些什么：

 1. 根据 `source` 里的内容下载了源代码文件 `dwm-6.0.tar.gz`
 2. 通过 md5 校验码确定下载的源代码文件和 `PKGBUILD` 的作者使用的一致
 3. 把源代码文件解压缩到 `./src`，并把本地提供的文件软链接到此处。`dwm-6.0` 正是压缩包中已有的路径
 4. 按照 `build()` 里的内容编译源代码，并把编译好的内容放在 `./pkg/$pkgname` 里（旧版本的 makepkg 不会创建 `$pkgname` 这个目录层级）
 5. 在 `./pkg/$pkgname` 里加上其它的一些信息，包括 `.PKGINFO`、`.MTREE` 和 `.INSTALL`，也就是 `dwm.install` 的拷贝；
 6. 把 `./pkg/$pkgname` 里面的内容打包形成 `dwm-6.0-1-x86_64.pkg.tar.xz`。

那么，我们有了一个 `.pkg.tar.xz` 这样一个二进制包之后，我们要如何安装呢？我们要使用这样一个命令：

    pacman -U dwm-6.0-1-x86_64.pkg.tar.xz

这个命令又完成了那些事情呢？

 1. 首先，二进制包被解压缩
 2. 按照 `.INSTALL` 的内容执行安装（或者是升级）前的命令
 3. 二进制包里面的内容会被拷贝到相应的目录（你注意到二进制包内的目录结构了吗？）
 5. 在 `/var/lib/pacman/local` 这个目录中建立 `dwm-6.0-1` 这样一个目录
 6. 这个目录里包含了四个文件 `desc`、`files`、`install` 和 `mtree`
 7. `desc` 记录了该软件包的基本信息，大部分由 PKGBUILD 中提取，如描述和依赖关系等，`files` 记录了每一个安装到系统上的文件的路径，`install` 就是 `.INSTALL` 的拷贝，`mtree` 是 `.MTREE` 的拷贝，记录了各文件的权限、时间、类型和校验码等信息，使用 gzip 压缩过
 4. 按照 `.INSTALL` 的内容执行安装（或者是升级）后的命令
 
从这以后，`pacman` 正是通过检查 `/var/lib/pacman/local` 里的内容来管理软件包的。比如说，在执行 `pacman -R dwm` 的过程中，pacman 首先在 `/var/lib/pacman/local` 找到了 `dwm-6.0-1` 这个目录，然后根据 `files` 的内容删除已安装的内容。`Dependency` 也是通过 `desc` 计算的。

OK！我已经解释了 `PKGBUILD` 的基本结构和 `makepkg` 的过程。基本上是两步：从 `PKGBUILD` 到 `.pkg.tar.xz` 包，再从二进制包安装到系统。这样一种办法有很多好处。首先，`PKGBUILD` 非常方便用户交流。我的一个 `PKGBUILD` 如果编译成功了，就可以给别人用。`PKGBUILD` 的内容一目了然，不但有助于学习，也再不用担心木马的问题了。

另外，我通过一个小例子展现 Arch Linux 的灵活性在哪里。比如，我要对 dwm 有自己的设置，也就是自己的 `config.h`，那我应该怎么做呢？我会做如下的事情：

 1. 编辑 `config.h`，另存为 `myconfig.h`；
 2. 编辑 `PKGBUILD`，把所有的 `config.h` 替换为 `myconfig.h`；
 3. 把 `pkgname` 改成 `dwm-my`；
 4. 添加 `provides=(dwm=$pkgname)` 和 `conflicts=(dwm)` 告诉 pacman 这个包与 dwm 是冲突的，并且它可以用来代替 dwm。

之后通过 `makepkg`，我会得到一个文件 `dwm-my-6.0-1-x86_64.pkg.tar.xz`，这个和原来的  `dwm-6.0-1-x86_64.pkg.tar.xz` 可以区别开。我可以安装 `dwm-my-6.0-1-x86_64.pkg.tar.xz`，如果有问题我还可以通过 `pacman -U dwm-6.0-1-x86_64.pkg.tar.xz` 来安装原来的二进制包。pacman 会知道这两个包之间的关系，并提示用户需要先卸载其中之一才能安装另一个。我还可以用同样的办法生成一系列的 `.pkg.tar.xz` 包，这在软件的安装调试过程中非常有用。

## AUR 和 ABS

我非常高兴看到我关于 PKGBUILD 和 makepkg 的文章在 LinuxTOY 受到了欢迎。我想先针对一些读者的回复谈一点题外话。

我先声明我一点也没有要诋毁 Debian 或 Gentoo 的意思，它们都是非常伟大的发行版，都有自己的特色。其实大多数的发行版都可以自己去定制，从而达到类似的目的。比如说，有的人提到 Gentoo 也有二进制包，比如像 Openoffice 这样的怪物。然而，我个人以为比较不同的发行版关键是要看它最核心的设计思想。比如说，Gentoo 根本就不是为了使用二进制包设计的。你要是都想用二进制包，就别费劲用 Gentoo 了。关于 Debian 阵营的发行版，我也想讲几句。正如一些朋友的回复所讲，DEB/apt-get 是非常好的管理工具，软件库也非常的大。我的笔记本现在还在用 elive，也是 Debian 的分支。我不喜欢 Debian 系列的发行版的原因不是它不能定制，而是他们非常依靠 Maintainer。我们可以自己做 DEB 包，然后呢？你的 DEB 包什么时候才能进入软件库呢？还有，只有你自己知道你的 DEB 是怎么做的，别人不能了解你编译打包的过程。Debian 本身打包的过程没有 Arch Linux 的 PKGBUILD 来的简单明了。只要比较 Debian 的 Maintainer 手册和 Arch Linux 的 Wiki 就可以看出这一点。

选择什么样的发行版完全是要看个人需要。我选择 Arch Linux，是因为它当初设计的时候就是要满足 “KISS Rule”，也就是 “Keep It Simple, Stupid”。或者说像爱因斯坦讲得：“Everything should be made as simple as possible, but no simpler”。**Arch Linux 的所有配置基本都是非常相似的脚本，加上简单灵活的 PKGBUILD 和 pacman，其实关于 Arch Linux 本身真的没有太多新的东西要学习。**大家有兴趣可以看看 “[Arch Compared To Other Distros (简体中文)][6]” 。Arch Linux 实际上是强迫用户从零开始自己定制自己的系统，在这个过程中也就真正了解了 Linux 本身。

好了，现在言归正传谈一谈 AUR 和 ABS。

AUR 是指 Arch Linux User Repository，也就是 Arch Linux 用户社区的软件库。我们现在回忆一下在 Arch Linux 中我们把源代码变成可以运行的二进制码需要哪些文件。我们需要：PKGBUILD，可能还有 `.install` 文件，加上一些补丁和必要的配置文件（像 dwm 的 `config.h`）。这样就足够了！当你成功使用 PKGBUILD 编译安装了一个新软件之后就可以通过 AUR 和其他的人分享你的成果了。具体的步骤是：

 1. 在 `package-dir` 中执行 `makepkg --source` 把 `package-dir` 中所有所需的文件打包（包括 `PKGBUILD`，`.install`，`patch` 和其他的 `config` 等）
 2. 前往 http://aur.archlinux.org 选择 “Submit”，并把你的 `package-1.0-1.tar.gz` 这样的文件上传。如果你希望从命令行上直接完成上传，可以试试[这个脚本][aurupload]

![AUR Submit][7]
 
AUR 会自动根据你的 PKGBUILD 内容把你的 Package 加到 AUR 里来。就是这么简单！那么有人会问：“别的用户要如何使用 AUR 呢？”

这个就更简单了，我们还是用一张截图来解释：

![AUR Yaourt][8]

 1. 首先下载“Tarball”（红色的圈圈），这个 Tarball 和你上传的内容是一样的，无非是 PKGBUILD 什么的 
 2. `tar xvzf package.tar.gz` 然后解压缩
 3. 然后的步骤你应该知道了，那就是 `makepkg` 还有 `pacman -U`

不过需要提醒的是，为了对自己负责，你应该在编译之前读一下 `PKGBUILD` 和 `.install` 的内容，确定里面没有恶意的代码。另外，我建议你一般不要以 root 的身份进行 makepkg。其实，makepkg 本身也做了这样的限制，你不加 `asroot` 的选项是不能 makepkg 的。这是因为，makepkg 会执行 PKGBUILD 里 `build()` 部分的代码。想一想，如果有人在 `build()` 这部分加了这么一句 `rm -r /home`，你就死定了！

为了防止在打包过程意外删掉外边的文件，可以使用 Gentoo 使用的 sandbox 程序进行一定程序的防范。它当然也[在 AUR 里][aur-sandbox]。

有些性急的朋友可能要问这个 AUR 和 pacman 取得的二进制包有什么联系？你应该记住，只要是 Arch Linux，所有的东西一定是从 PKGBUILD 开始的。你通过 pacman 得到的二进制包也是从 PKGBUILD 编译而成的。在你的 `/etc/pacman.conf` 有很多 Repository 的设置，其中的 `[core]` 和 `[extra]` 是由 Arch Linux 的核心成员维护的，这些软件库里的软件由于特别重要，每个人都要用，所以 Arch Linux 的开发人员把二进制包提前做好，你就可以通过 pacman 取得了。然而，和 Debian 的 Maintainer 机制不一样，最终的用户可以很容易的了解这些软件的编译过程。如果需要的话，最终用户可以改变设置，重新编译这些软件。最典型的情形就是自己编译 kernel 的时候。这要通过 ABS 来解释清楚。ABS，也就是 Arch Linux Build System。首先我们要安装 ABS：

 1. `pacman -S abs`
 2. `vi /etc/abs/abs.conf` # 编辑 ABS 的配置文件
 3. 你会看到这样一行 `SUPFILES=(core extra !unstable community !testing)`，把你需要的 Repo 之前的 `!` 去掉
 4. 然后以 root 身份执行 `abs`

之后又要如何使用 ABS 呢？ABS 所作的事情无非是把所有 Repo 里的软件的 PKGBUILD 下载到你本地的硬盘中。这些 PKGBUILD 都放在了 `/var/abs` 中。你能通过 pacman 直接安装的二进制包其实也都是按照 ABS 的内容编译的。下面我还是用 dwm 的例子解释 ABS 的使用：

 1. `su`
 2. `cd /var/abs` # 你可以看到这个目录里有 `core`，`extra`，`community` 三个子目录，正如 `abs.conf`  中的设定
 3. `mkdir local` # 建立一个 `local` 目录，用来放你自己需要的软件的 PKGBUILD
 4. `chown username:usergroup ./local makepkg` # 要以非 root 身份进行
 5. `exit` # 退出
 6. `cd local`
 7. `cp -r ../community/x11/dwm ./` # 从 ABS 中拷贝 dwm 的内容
 8. `cd dwm`

下面不用我说了，你在这个目录里可以看到三个文件 `PKGBUILD`、`dwm.install`、`config.h`。你于是可以用 makepkg 和 pacman -U 来按照自己喜欢的方式安装 dwm。

OK，你实际已经清楚了解了 ABS 和 pacman 的关系，那么 AUR 又和 ABS 还有 pacman 有什么联系呢？说的直白一点，你上传到 AUR 的 PKGBUILD 要足够“有品”才能直接通过 pacman 使用。对于“有品”，我是这样定义的。你的 PKGBUILD 要有很多人用（很多人投票），没有恶意代码，没有太多的 Bug……而判定你的 PKGBUILD 够不够“有品”的人是一些叫作 TU（Trusted User）的人。这些人的工作是检查 AUR，关注那些特别受欢迎的 PKGBUILD。之后，他会仔细检查，确定这些 PKGBUILD 是不是安全。然后，他们会给这些 PKGBUILD 打上安全的标签，并且把这些 PKGBUILD 从 unsupported（我们上传的 PKGBUILD 一开始都是在 unsupported 中）移到 `community` 的 Repo 中。

在 community repo 里面的 PKGBUILD 会提前编译好，如果你在 `/etc/pacman.conf` 中开了 `community` repo，你就可以直接使用这些软件的二进制包了。也许有一天，你当初上传的 PKGBUILD 变得特别重要，这个软件可能被移到 `testing`，`extra` 或者 `core` 的 repo 中。补充一点，`testing` repo 里面一般是需要测试，又准备放到 `core` 或者 `extra` 中的软件。

**Arch Linux 就是这样，非常灵活。既有 pacman 这样好的二进制包管理工具，又有 ABS 和 AUR 这样方便的源代码服务。通过 ABS，你可以完全控制你自己的系统到底是如何建立的。如果在 `pacman -Ss` 的时候找不到一个软件，你可以到 AUR 去找，如果还是找不到，为什么不自己试着从源代码开始，写一个 PKGBUILD 然后放到 AUR 中和别人分享呢？**

说到这里，我希望我已经把 Arch Linux 最核心的东西讲明白了。有些人说我的文章写得比 wiki 里的文章清楚。其实，我写的东西只是在順序上不一样。**我是从 PKGBUILD 开始讲到 AUR 和 ABS，再到 pacman。这个順序和 Arch Linux 实际的开发过程是一致的，所以逻辑上容易理解很多。如果你从 pacman 入手反过来读，你可能就完全错过了理解 Arch Linux 核心概念的机会。**

## Yaourt

就一般情况而言，当 Arch Linux 用户需要使用 AUR 中的包时，往往会执行到 AUR 官方网站查找所需的包、下载该包的 Tarball 文件、在命令行下对 Tarball 文件解压、通过 makepkg 编译打包、最后使用 pacman 安装这样一个过程。仔细打量这个过程，你是否觉得稍微有些繁琐呢？有解决的方案吗？回答是肯定的。这就是我们今天将要介绍的主角──Yaourt。

### 简介

Yaourt 是一个由 Julien Mischkowitz 所编写的 Bash 脚本，它是将 Pacman 与 AUR 这两者相结合的绝佳工具。通过 Yaourt 安装 AUR 中的包十分方便，它不仅简化了上述繁琐的过程，而且把这一过程半自动化，使用者只需在它的交互模式中简单的回答几个问题即可。此外，Yaourt 支持将结果以鲜亮的颜色输出，非常抢眼。

### 安装 Yaourt

除了在 Arch Linux 的 AUR 中可以找到 Yaourt 外，中国和法国的 Arch Linux 社区源也包含 Yaourt。我们采用 Arch Linux 中文社区的源来安装 Yaourt。为了 customizepkg 包，我们把 archlinuxfr 源也加上，但是优先使用 archlinuxcn 的。首先，将下列内容添加到 `/etc/pacman.conf` 文件：

```
[archlinuxcn] 
SigLevel = Optional TrustedOnly
Server = http://repo.archlinuxcn.org/$arch

[archlinuxfr] 
SigLevel = Optional TrustedOnly
Server = http://repo.archlinux.fr/$arch
```

接着，我们可以执行下面的命令来安装 Yaourt：

    pacman -Sy yaourt

另外，我们将 aurvote 和 customizepkg 这两个包也装上，前者用于对喜欢的包投票，而后者是定制 PKGBUILD 所需的：

    pacman -S aurvote customizepkg

同时，你需要为 aurvote 建立一个配置文件 `.aurvote` (位于 ~/ 目录下)： 

    user=你的 AUR 帐号
    pass=该帐号的密码

如果你没有 AUR 帐号，可到 http://aur.archlinux.org/account.php 注册一个。

### Yaourt 实战

为了说明 Yaourt 的使用，我们以一个实例来进行。譬如，我对 Phatch 这个批量图片处理程序非常喜欢，我希望在 Arch Linux 中安装它。首先，我们来看一下，在 Arch Linux 中是否存在 Phatch：

    yaourt phatch

Yaourt 在搜索后返回如下结果： 

![Yaourt phatch][9]

从该结果我们可以断定，Phatch 在 Arch Linux 的 AUR 中。现在，我们只需按 1 并回车就可以安装它了。

在显示一些输出信息后，Yaourt 会让你作出第一个选择：是否编辑 PKGBUILD 文件?按 y 回答并输入你喜欢的文本编辑器后，你可以针对 PKGBUILD 的内容进行修改。

![Edit PKGBUILD?][10]

第二个选择：是否编辑 `phatch.install`？

![Edit phatch.install?][11]

然后，Yaourt 会询问是否继续编译。我们的回答当然是 y。

![Continue build phatch?][12]

要求输入密码：

![Enter password][13]

接着，Yaourt 询问是否安装已编译好的包，同样回答 y 即可。

![Continue installing phatch?][14]

输入密码后，再输入 y，大功告成：

![Proceed with installation?][15]

综观 Yaourt 的命令行选项，与 Pacman 非常相似。关于 Yaourt 的更加详细的用法，通过 `man yaourt` 可以获得参考。其实，除了从 AUR 安装包外，Yaourt 也可以从 Arch Linux 的源安装包，此不赘述。

> Written with [StackEdit](https://stackedit.io/).

  [aurupload]: https://github.com/lilydjwg/winterpy/blob/master/pyexe/aurupload
  [aur-sandbox]: https://aur.archlinux.org/packages/sandbox/


  [1]: http://linuxtoy.org/
  [2]: https://projects.archlinux.org/svntogit/community.git/plain/trunk/PKGBUILD?h=packages/dwm
  [3]: https://projects.archlinux.org/svntogit/community.git/plain/trunk/dwm.install?h=packages/dwm
  [4]: https://projects.archlinux.org/svntogit/community.git/plain/trunk/dwm.desktop?h=packages/dwm
  [5]: https://projects.archlinux.org/svntogit/community.git/plain/trunk/config.h?h=packages/dwm
  [6]: https://wiki.archlinux.org/index.php/Arch_Compared_to_Other_Distributions_%28%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87%2929
  [7]: https://lh6.googleusercontent.com/-faAXv_bDkZI/UpqmB3aggiI/AAAAAAAAEbA/Szc6tPdRRsQ/s0/AUR++en++++Submit.png
  [8]: https://lh6.googleusercontent.com/-RY9Q0flAu1E/UpqpjcHi0hI/AAAAAAAAEbY/IXmTScs9zZk/s0/AUR++en++++yaourt.png
  [9]: https://lh5.googleusercontent.com/-XQ1I-G9Ai-Y/UpqrhNmGDVI/AAAAAAAAEbw/esDRwOkBCOY/s0/2013-12-01-112227_960x134_scrot.png
  [10]: https://lh4.googleusercontent.com/-e4E354Ub4eA/Upqr-01u9RI/AAAAAAAAEcE/LihvvIAtMOw/s0/2013-12-01-112429_958x656_scrot.png
  [11]: https://lh6.googleusercontent.com/-qr0AJX6WfsQ/UpqswHlbTlI/AAAAAAAAEcY/xKknI3ztJKU/s0/2013-12-01-112746_961x187_scrot.png
  [12]: https://lh3.googleusercontent.com/-9i2EXAxtnKg/Upqs6xiB0OI/AAAAAAAAEcs/r4CTWvtms_g/s0/2013-12-01-112831_960x53_scrot.png
  [13]: https://lh4.googleusercontent.com/-lEb2KmIwZzg/UpqtY-L-TMI/AAAAAAAAEdA/5Vzt2oMr55w/s0/2013-12-01-113030_959x52_scrot.png
  [14]: https://lh3.googleusercontent.com/-afG3mN5YWpA/UpqvNc3z2hI/AAAAAAAAEdY/4OAuYGL8WLY/s0/2013-12-01-113709_958x366_scrot.png
  [15]: https://lh6.googleusercontent.com/-zIM6pJBX9Xs/Upqv_zigNII/AAAAAAAAEds/8rcEIpfmwSI/s0/2013-12-01-114138_961x199_scrot.png
