---
title: "Dns and How It Works"
menuTitle: "DNS"
date: 2020-10-19T00:13:02+08:00
publishDate: 2020-10-19T00:13:02+08:00
draft: false
tags: ["roadmap-developer","internet","DNS","Domamin Name System"]
pre : '<i class="fas fa-globe" style="margin: 3px;"></i>'
---
# DNS 是什麼 ? 他們是如何運作 ?

## DNS 是什麼
Domain Name System ，紀錄數字IP與文字網址對應關係的地方。
概念上像是把我家的經緯度座標變成中文地址的地政系統一樣的東西。

## 如何運作
就是把「 IP 」與「對應的網址」的對應關係存起來，讓人類可以雙向查詢對應內容。

## domain name 與 hostname 的不同

- domain name: 網域名稱
- hostname: 主機名稱

舉例: www.abcabc.com.tw
- 有一台提供 .tw 網域的主機 (hostname 叫做: tw)
- 隸屬於 .tw 網域底下，有一台提供 com.tw 網域的主機 (hostname 叫做: com)
- 隸屬於 com.tw 網域底下，有一台提供 abcabc.com.tw 網域的主機 (hostname 叫做: abcabc)
- 隸屬於 abcabc.com.tw 網域底下，有一台提供 www 服務的主機 (hostname 叫做: www)

## 參考資料
- [wiki](https://zh.wikipedia.org/wiki/%E5%9F%9F%E5%90%8D%E7%B3%BB%E7%BB%9F)
- [aws](https://aws.amazon.com/tw/route53/what-is-dns/)
- [第十九章、主機名稱控制者： DNS 伺服器](http://linux.vbird.org/linux_server/0350dns.php)
    + domain name 與 hostname 的不同