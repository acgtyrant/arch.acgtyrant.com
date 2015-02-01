title: 文件管理
date: 2015-01-20 14:15:45
tags:
- Documents
---
在海外的 Web 产品上，经常看到「Archieves」一词。博客，邮件客户端，时间管理客户端都有。

我一直觉得它没用，直到 NovaDNG 偶然提起他习惯定期归档邮件。我试了下，发现**它原来还真如同字面上的意思**，把邮件归档起来，在邮箱就看不到它了，的确对整理很有用。于是我便也习惯定期归档邮件了。

久而久之，我也开始试图把文件管理得井井有条。事实上，**Windows 本身就把个人用户的文件夹分类得很科学**，我记得有 `Pictures`, `Videos`, `Documents`, `Games`, `Downloads` 等等。您用 Chrome, Firefox 下载文件时，也是会默认保存到个人文件夹下的 `Downloads` 文件夹的。同理，大多 Linux 发行版也沿袭了这分类。

可惜，**中国软件产品的市场秩序一直相当混乱**，大概很多国产软件并不充分利用这些文件夹，而是自立门户地创建文件夹，尤其是「迅雷下载」。而且不安全、稳定性差的的盗版 Windows 一直大行其道，病毒和流氓软件又猖狂无比。以致「重装系统大法」竟然成了中国 Windows 用户悠久的传统。在这种情境下，把文件整理了也没用，毕竟一旦施展重装系统大法就全没了。也难怪绝大多 Windows 用户一直不会管理文件；也难怪竟有不少中国用户会指责 Chrome 默认安装到 C 盘里，不给自定义安装路径的选项。您要知道，在发达国家高度正版化、秩序规范化的市场里，销售的个人计算机一开始就只有一个 C 盘的，毕竟他们一直用正版 Windows, 也能有力地制裁流氓软件、病毒的开发者等，用不着天天施展醉生梦死的重装系统大法。

我之所以感慨这些。因为我前几天处于开题报告创作需要，向一些人索取毕业设计材料，便吃惊地发现有些人早就弄丢了，有的因为重装系统，有的因为没归档好。我说，就算再不怎么管理文件，毕业设计这个凝聚心血的创作成果也至少会保留吧。

但我并不想挖苦这些 Windows 用户。毕竟我本来也是托「比 Windows 稳定，不受病毒、流氓软件之扰」的 Linux 之福，才养成了文件管理的习惯。接下来我会解说**如何靠 Linux 实现理想的文件管理**。

首先，大部分发行版应该已经在用户目录下创建了一些文件夹：

1. Documents
2. Downloads
3. Music
4. Pircutres
5. Videos

分类对普通用户已经相当完善了，下载资源时一般会自动默认下载到 `Downloads`, 您可以按文件格式，改变下载位置到相应的文件夹里。此外，**这些文件名最好用英文**，毕竟有太多应用程序没对路径做本地化处理。

在此我要推荐一个 online backup services, 即坚果云，已在 AUR 里被打包成 `nutstore`. 它有一个我梦寐以求的、最强大、最终极的特性：**Multiple file folders sync!** 就是字面上的意思，除了 `Nutstore` 主文件夹，**您还可以指定若干其它文件夹并同步它们**。

![](https://lh6.googleusercontent.com/-ylaCVei55qg/VL3sHztpZEI/AAAAAAAAJ8Y/evtRshlLIPI/s0/DeepinScreenshot20150120134640.png)

我就同步了 `Pictures`, 这下我妈妈要担心我到处云同步糟糕图了。此外，御用截图工具 `Deepin-Screenshot` 也会自动保存截图到这文件夹里，这下也不用怕截图丢失了。

![](https://lh5.googleusercontent.com/-jf_WcNVF7Fs/VL3tATQerLI/AAAAAAAAJ8s/MnAc2JIEOOE/s0/DeepinScreenshot20150120135145.png)

其实我个人不怎么常用 `Documents`, 而且出于本身作为学生、开发者的需要，我另行创建了两个御用文件夹 `Projests`, `Courses`. 前者放一些项目，并不用坚果云同步，而是各自用 Git 管理并 Push 到 GitHub 上去；后者则同步，至于内部分类。有如下，其中部分文件夹已做打码处理：
	
	// tree 命令可格式化输出目录一览，`-d` 表明只输出目录，`-L 2` 表明只递归输出目录两次。
	$ tree -d -L 2 
	.
	├── Unix Linux 编程实践教程
	│   ├── acrobat_reader
	│   ├── chapters
	│   ├── docs
	│   ├── exams
	│   ├── html
	│   ├── images
	│   ├── pptviewer
	│   └── projects
	├── 毕业设计
	│   ├── 归档
	│   ├── 行政
	│   ├── 开题报告
	│   ├── 李ＸＸ
	│   ├── 潘ＸＸ
	│   └── 徐ＸＸ
	├── 结业｜归档
	│   ├── Computer Network
	│   ├── MITx 6.00.1x Introduction to Computer Science and Programming
	│   ├── MITx 6.00.2x Introduction to Computational Thinking and Data Science
	│   ├── Numerical Analysis
	│   ├── 泛函分析
	│   ├── 计算机组成
	│   ├── 近世代数
	│   ├── 趣味语言学
	│   ├── 数据结构与算法
	│   ├── 数据库原理与应用
	│   ├── 数学建模
	│   ├── 拓扑学
	│   ├── 体育保健
	│   └── 运筹学课程设计
	├── 坑｜归档
	│   ├── Algorithm, Part 1
	│   ├── Algorithms Design and Analysis, Part 1
	│   ├── Cryptography I
	│   ├── High Performance Scientific Computing
	│   ├── Linear and Discrete Optimization
	│   ├── SICP
	│   ├── The Hardware Software Interface
	│   ├── 关爱生命——实用急救与自救技能
	│   ├── 计算机辅助翻译原理与实践
	│   └── 英语口语
	└── 专业资料

	43 directories

我把所学习的学校课程和公开课都分成三大类：

1. 进行中，就直接放在 `Courses` 目录下，比如我正在看的《Unix/Linux 编程实践教程》，以及毕业设计。
2. 已完成的课程则归档到 `结业｜归档`，现在其子目录比较少，毕竟因为我在大三才养成这习惯，如果您刚上大学，趁早学会文件管理吧！一旦到毕业时用 `tree` 命令打印，输出一定看起来挺有成就感。
3. 剩下的课程自然都是坑了的，但要 Push 进`坑｜归档`，而不是直接删除。其实这归档也大有用处，因为将来若您要重拾某课时，特别是以每学期循环的公开课，则直接把它 Pop 到父目录即 `Courses` 就好。顺便一提，`｜` 和 `Ｘ` 都是用 [Fcitx-rime](http://arch.acgtyrant.com/2014/11/11/Fcitx-rime/) 打出的全角字符，[善用全角／半角字符，可以排版得很好看。](http://blog.acgtyrant.com/chinese-western-mixed-typesetting.html)

剩下的`专业资料`则用来存放我所学专业的行政资料，比如校历图、选课表、培养计划什么的。

最后，善用文件管理器的导航栏，我就在 Nautilus 设定了常用目录，包括  [Arch Build System](https://wiki.archlinux.org/index.php/Arch_Build_System) 用的 `abs`, 博文目录 `_posts`, 以及上文提到的文件夹等。

其实还有个关键即 dotfiles 管理没讲到，将来会另起一文并解说。

综上所述，我用 `tree` 命令格式化打印目录一览，坚果云云同步文件，科学的文件夹分类，优秀的文件管理器 Nautilus, 这就是我的文件管理法了。Linux 真好用啊，不过有钱人大概可以直接上 OS X, 其文件管理大概连学习曲线都没有。

> Written with [StackEdit](https://stackedit.io/).
