title: MentoHUST 及『二次撥號』的臨時解決方案
date: 2014-02-23 12:34:33
tags:
- 中國特色解決方案
- Linux
---

> Warning! [在下不再維護二次撥號的臨時解決方案！][1]

在下很早完善了 [wiki|MentoHUST (简体中文)]，普通用户直接查阅即可。

但有些個別大學的網絡拓撲結構比較特殊：**銳捷撥號後只能訪問校內的局域網，需要進行二次撥號，即 L2TP 連接到運營商，才能訪問外網。**如浙江理工大學，集美大學等等。于是本文旨在指導 Arch Linux 用户如何進行二次撥號，對其它 Linux 發行版用户应该也有一定的参考价值。

在此之前，請先按 [wiki|MentoHUST (简体中文)] 調試 MentoHUST 直到撥號成功。該步驟很重要，一定要完成。

然後準備好 L2TP 用戶名、密碼、服務器地址，可自行向運營商或校方相關部門索取，再安裝  [Pkg|xl2tpd]。

爲方便示範，不妨假設 L2TP 用戶名、密碼、服務器地址分別爲`hzxic10660211`，`123456`，`192.168.193.10`，且您連接用的 Interface 為`enp3s0`，網管為`10.10.173.1`

編輯`/etc/ppp/chap-secrets`如下：

     # Secrets for authentication using CHAP
     # client        server  secret                  IP addresses
     hzxic10660211   *   123456   *

編輯`/etc/ppp/pap-secrets`如下：

    # Secrets for authentication using PAP
    # client        server  secret                  IP addresses
    hzxic10660211   *   123456   *

注意，**確保格式正確**，即第一個星號左右各有三個空格，第二個星號左邊有三個空格。

編輯`/etc/ppp/options.l2tpd.client`如下：

    noauth
    proxyarp
    defaultroute

編輯`/etc/xl2tpd/xl2tpd.conf`如下：

    [lac bras]
    lns = 192.168.193.10 #服務器地址
    redial = yes
    redial timeout = 15
    max redials = 5
    require pap = yes
    require chap =yes
    require authentication = yes
    name = hzxic10660211 #用戶名
    ppp debug = yes
    pppoptfile = /etc/ppp/options.l2tpd.client

按 MentoHUST 的**配置與運行**章節配置好，啓動 MentoHUST 並撥號成功後，執行以下：

    # systemctl start xl2tpd.service
    # sh -c "echo 'c bras' > \$L2TPD_PIPE"

注意：`sudo echo "c bras" > /var/run/xl2tpd/l2tp-control`[不可行][2]。

執行`ifconfig ppp0`，記下第二道行中的`inet`後面的一段 IP, 不妨假定是`39.187.138.79`，則再執行以下：

    # route add -host 192.168.193.10 gw 10.10.173.1 metric 1 dev enp3s0
    # route add -net 0.0.0.0 netmask 0.0.0.0 gw 39.187.138.79 metric 1 dev ppp0
    
大功告成。

## 自動化腳本

https://github.com/acgtyrant/bin/blob/master/l2tp

按實際情況配置開頭的一系列變量，並以 root 用戶執行即可，不出意外的話，應該會一次性成功。

## TODO

該解決方案只所以發佈在敝博，正因為是臨時的：

1. 在集美大學等的可行性有待驗證，特別是校內網路由方面的配置。
2. 在自動化腳本中，用`iproute2`命令全面代替`net-tools`命令，不過也許還會 Fork 出只使用`net-tools`命令的版本。
4. 原[wiki|MentoHUST (简体中文)]文檔其實還不夠友好，有待進一步優化措辭及排版。
5. 如果能有 Shell 高手親自出手相助，及在自動化腳本加入專門初始化`/etc/ppp/chap-secrets`,`/etc/ppp/pap-secrets`,`/etc/ppp/options.l2tpd.client`,`/etc/xl2tpd/xl2tpd.conf`等等文件的 Feature 就再好不過了。
6. 時機成熟時，會在[wiki|MentoHUST (简体中文)]創建對應的『二次撥號』章節並加以維護，本文章到時自動失效。

> Written with [StackEdit](https://stackedit.io/).


> Written with [StackEdit](https://stackedit.io/).


  [1]: http://arch.acgtyrant.com/2014/03/06/mentohust/
  [2]: http://stackoverflow.com/questions/84882/sudo-echo-something-etc-privilegedfile-doesnt-work-is-there-an-alterna
