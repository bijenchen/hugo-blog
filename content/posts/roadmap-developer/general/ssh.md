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

## 如何使用不同的 ssh key 連線

### 在 .ssh 目錄下建立 config 檔案
```
/Users/bijen/.ssh
```
注意， config 檔案要跟 private & public key 放在相同層級中。

### config 內容寫法
```
Host [your-ssh-name / 未來使用ssh連線時的代稱，可自行取名]
    HostName [ip or domain / 連線的目的地 ip 或 domain name]
    User [connect-account / 用來連線的帳號]
    PreferredAuthentications [驗證方式]
    IdentitiesOnly [是否只接受 ssh key 登入]
    IdentityFile [absolute path/ 用來驗證的檔案絕對位置，例如 public key path]
    UseKeychain [?待查]
    AddKeysToAgent [將連線密鑰存到連線目的地?待查]
```

#### 示範
```
Host bijen-bitbucket
    HostName bitbucket.org
    User git
    PreferredAuthentications publickey
    IdentitiesOnly no
    IdentityFile /Users/bijen/.ssh/id_rsa_bijen_bitbucket
    UseKeychain yes
    AddKeysToAgent yes

Host bijen-gcp
    HostName [104.199.xxx.xx/ my-gcp-server-ip]
    User bijen.chen
    PreferredAuthentications publickey
    IdentitiesOnly no
    IdentityFile /Users/bijen/.ssh/id_rsa_bijen
    UseKeychain yes
    AddKeysToAgent yes

Host bijen-aws
    HostName [my-aws-server-ip]
    User bijen.chen
    PreferredAuthentications publickey
    IdentitiesOnly no
    IdentityFile /Users/bijen/.ssh/id_rsa_bijen
    UseKeychain yes
    AddKeysToAgent yes
```
#### 說明
##### 當我想連線至 bitbucket 時

1. terminal 輸入 `ssh bijen-bitbucket`
2. 此時會用以下資訊連線至 bitbucket.org
    *  使用者帳號: git
    *  密鑰: id_rsa_bijen_bitbucket

##### 當我想連線至 gcp / aws 時

1. terminal 輸入 `ssh bijen-gcp` / `ssh bijen-aws`
2. 此時會用以下資訊連線至 gcp / aws 的 ip
    *  使用者帳號: bijen.chen
    *  密鑰: id_rsa_bijen

==note: 可以用相同的密鑰連線至不同的 server，不見得都要用不一樣的登入名稱與密鑰==

## 如何使用 ssh tunnel 連線 port 轉發
```
ssh -L <本地端 port>:<遠端主機 ip / dns>:<遠端主機 port> <ssh 連線遠端主機 ip / dns>
```
可以設定由本地指定 port 與遠端指定 port 對接，同時指定對接的身份，所以也可以達到透過跳板連線到遠端主機的目的。
舉例如下:

本地 33066 port 想要連線至遠端伺服器的 3306 port，分兩種情況：
1. 本地有 ssh 至遠端伺服器的權限時
```
ssh -L 33066:<remote-ip/dns>:3306 -N <ssh-user>@<remote-ip/dns>
```
2. 本地無 ssh 至遠端伺服器的權限，但中介伺服器有權限時
```
ssh -L 33066:<A-remote-ip/dns>:3306 -N <ssh-user>@<B-remote-ip/dns>
```

說明:

示範中的「A-remote」是遠端 mysql 資料庫所在的伺服器，本地無權連線。

但是本地可連線至中介伺服器「B-remote」，「B-remote」的該登入使用者(ssh-user)是有權連線至「A-remote」的，

所以此時的 ssh tunnel 行為會是：

以 127.0.0.1 (=本地) 33066 port 接上 B-remote 的 33066 port ， B-remote 再以「 B-remote 本地」的身份，以「B-remote 本地 33066 port 」接上 A-remote 3306 port //TODO:????待確認

因此，專案裡的資料庫連線設定應該是以本地使用者連線， tunnel 才能成功打通。

像是 laravel 的 .env 設定檔就會長這樣:
```
DB_BIJEN_HOST=127.0.0.1           # 以本地身份連結(這邊的本地同時代表「真實的本地」以及「中介伺服器的本地」)
DB_BIJEN_PORT=33066               # 要用來連結的本地 port (這邊的本地意義同上)
DB_BIJEN_DATABASE=database_BIJEN  # 欲連線的資料庫名稱
DB_BIJEN_USERNAME=bijen           # 欲連線的資料庫登入資訊
DB_BIJEN_PASSWORD=*******         # 欲連線的資料庫登入資訊
```

## 參考資料
- [你該知道所有關於 SSH 的那些事](https://jennycodes.me/posts/security-ssh)
- [第十一章、遠端連線伺服器SSH / XDMCP / VNC / RDP](http://linux.vbird.org/linux_server/0310telnetssh.php)
- [利用 ssh 的用户配置文件 config 管理 ssh 会话](https://luohoufu.github.io/2016/07/21/deepin2/)
    + PreferredAuthentications
- [OpenBSD manual page server SSH_CONFIG(5)](https://man.openbsd.org/ssh_config.5)
    + 各種 config 可以設定的項目

**KJ的筆記**
- [Ubuntu 系統網路 ssh config 指令](https://ubuntu-for-newbie.kejyun.com/docs/network/ssh/config/)
- [ssh tunnel 連線 port 轉發](https://ubuntu-for-newbie.kejyun.com/docs/network/ssh/ssh-tunnel-port-forward/)

## 延伸閱讀
- [How to Create SSH Tunneling or Port Forwarding in Linux](https://www.tecmint.com/create-ssh-tunneling-port-forwarding-in-linux/)
- [SSH Config File](https://www.ssh.com/ssh/config/)
- [[教學] 產生SSH Key並且透過KEY進行免密碼登入](https://xenby.com/b/220-%E6%95%99%E5%AD%B8-%E7%94%A2%E7%94%9Fssh-key%E4%B8%A6%E4%B8%94%E9%80%8F%E9%81%8Ekey%E9%80%B2%E8%A1%8C%E5%85%8D%E5%AF%86%E7%A2%BC%E7%99%BB%E5%85%A5)
