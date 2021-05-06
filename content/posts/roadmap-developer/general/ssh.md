---
title: "SSH"
menuTitle: "SSH"
date: 2020-12-26T10:57:19+08:00
publishDate: 2020-12-26T10:57:19+08:00
draft: false
tags: ["roadmap-developer","general","ssh"]
pre : '<i class="fas fa-key" style="margin: 3px;"></i>'
---

# SSH(Secure Shell)

## 作用
與遠端伺服器進行較為安全的連線

## 實現方式
以一組鑰匙(私鑰private key - 公鑰public key)分別存放在自己和遠端伺服器手上，透過配對鑰匙來進行訊息正確解密，達到隱蔽交換資料的目的。

### 過程
我們跟遠端伺服器會各自把自己的私鑰留在手上，互相交換公鑰給對方
(也就是交換後，手上持有的是自己的私鑰與對方的公鑰)。

當進行連線時，會先用對方的公鑰加密我們自己發出的訊息，把加密過的訊息傳給對方。

遠端伺服器收到加密過的訊息之後，會用手上的自己的私鑰解密進行解密，讀取正確的訊息內容。


所以，假設現在情境是要登入遠端伺服器，我們就會用手上持有的「遠端伺服器公鑰」把登入資訊加密，接著傳送給遠端伺服器。

伺服器因此會收到「以伺服器公鑰加密過的資料」，這時候因為伺服器手上握有跟這個伺服器公鑰成對的伺服器私鑰，所以可以用伺服器私鑰正確解密。

解密完後伺服器就會看到我們的登入資訊，因而放行讓我們登入。

## 如何增加 ssh key 到 bitbucket 中，並且使用自訂的 hostname

### 連線資訊
![](https://i.imgur.com/AqxzkWO.png)

## 參考資料
- [你該知道所有關於 SSH 的那些事](https://jennycodes.me/posts/security-ssh)
- [第十一章、遠端連線伺服器SSH / XDMCP / VNC / RDP](http://linux.vbird.org/linux_server/0310telnetssh.php)

## 延伸閱讀
- [How to Create SSH Tunneling or Port Forwarding in Linux](https://www.tecmint.com/create-ssh-tunneling-port-forwarding-in-linux/)
- [SSH Config File](https://www.ssh.com/ssh/config/)
- [[教學] 產生SSH Key並且透過KEY進行免密碼登入](https://xenby.com/b/220-%E6%95%99%E5%AD%B8-%E7%94%A2%E7%94%9Fssh-key%E4%B8%A6%E4%B8%94%E9%80%8F%E9%81%8Ekey%E9%80%B2%E8%A1%8C%E5%85%8D%E5%AF%86%E7%A2%BC%E7%99%BB%E5%85%A5)
