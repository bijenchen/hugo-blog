---
title: "How Does the Internet Work"
menuTitle: "網路運作原理"
date: 2020-10-19T00:07:56+08:00
publishDate: 2020-10-19T00:07:56+08:00
draft: true
tags: ["roadmap-developer","internet"]
pre : '<i class="fas fa-globe" style="margin: 3px;"></i>'
---
# 網路如何運作 ?

## 網際網路設計的初衷
讓機器(電腦)彼此之間可以連線，互通資訊。

## 達成方式

### 設計出彼此溝通的規範: 網際網路協定 Internet Protocol (IP)
每臺機器都有一組自己獨有的 IP，作為表示自身位址的資訊，讓機器之間可以找到對方。
由四組數字組成，每組數字的區間都是 0~255。 *日後被稱為 IPv4*
> 由於 IPv4 上限僅為 $2^8$ x $2^8$ x $2^8$ x $2^8$ = $2^32$ 個，無法應日漸蓬勃的網路運用需求，所以 IPv6 應運而生，將 IP 範圍擴充為 $16^32$ = $2^128$ 個。

### 建構連線網路
早期是借用遍布率廣泛的電話系統線路作為機器之間的連線途徑，個體用戶往中繼點連線、中繼點往更大的上層中繼點連線，以此類推直到將每臺機器都串在一起。
隨著網際網路的需求增高，現代已經不再佔用電話線路，改由專屬的網路線路提供連線途徑，架構的大致概念仍然維持。



## 參考資料
- [MDN web docs](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/How_does_the_Internet_work)
- [stanford](https://web.stanford.edu/class/msande91si/www-spr04/readings/week1/InternetWhitepaper.htm)
- IP
    - [IPv6](https://zh.wikipedia.org/wiki/IPv6)
    - [IPv4](https://zh.wikipedia.org/wiki/IPv4)
    - [認識IPv4與IPv6的差異](https://www.ithome.com.tw/tech/92046)