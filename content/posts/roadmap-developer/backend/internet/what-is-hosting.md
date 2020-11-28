---
title: "What Is Hosting"
menuTitle: "網站代管"
date: 2020-10-19T00:13:27+08:00
publishDate: 2020-11-22T00:00:00+08:00
draft: false
tags: ["roadmap-developer","internet","hosting","web host"]
pre : '<i class="fas fa-globe" style="margin: 3px;"></i>'
---
# Hosting 是什麼 ?

網頁代管(Web Hosting)，將網頁程式碼放到外部可連結的伺服器上，讓他人可以透過網際網路訪問網站內容。

# 案外案： 那 Hostname 又是什麼？

在還沒有網際網路的時代，主機之間互相聯絡的方式就是自己製作一份主機的通訊錄(也就是常見的 /etc/hosts 那份檔案)，讓自己記得聯絡對象的 ip ，並且為該 ip 賦予一個我的主機認得的名字。
這個名字就稱為「Hostname」。

當自己主機要向外聯絡時，會優先去查看通訊錄裡是不是已經認得這個 Hostname ， 不認得時才會向外去 DNS 詢問是否有對應 Domain Name 。

因此可以做個實驗，在自己的 /etc/hosts 設定某個別的 ip 對應名稱為「www.google.com.tw」，設定完之後自己 ping 一下 www.google.com.tw 。
會發現回應的 ip 不再是 google 的主機 ip ，而是新設定的 ip ，對我自己的主機來說， www.google.com.tw 這個名字已經被別人取代，再也不會連到跟大家一樣的 google 首頁了。
> 畢竟 DNS 系統是晚於通訊錄方式出現，算是在當時既有的模式之上進行擴充，所以通訊錄查詢會被優先使用也是合理現象。

## 參考資料
- [wiki-網頁代管服務](https://zh.wikipedia.org/wiki/%E7%B6%B2%E9%A0%81%E5%AF%84%E5%AD%98%E6%9C%8D%E5%8B%99)
- [什麼是網頁寄存 (What is Web Hosting)](http://learn-web-hosting-domain-name.mygreatname.com/what-is-web-hosting.html)
### 關於 Hostname 的資料來源待補充
- []