---
title: "代理與反向代理"
menuTitle: "Proxy & Reverse proxy"
date: 2021-05-12T10:33:34+08:00
publishDate: 2021-05-12T10:33:34+08:00
draft: true
tags: ["network","experience","proxy","reverse proxy"]
pre : "<b>[工作筆記] </b>"
---

## 緣起

再度看到反向代理這個名詞，發現自己好像對代理的概念模模糊糊，所以來查一下！

## 網路連線的基本架構

      Request ------->
Client -- Internet -- Server
      <------ Response

## 代理相關機制的目標

因為與網際網路連線都會有被攻擊的風險，所以試圖降低網際網路連線的風險。

## 代理( Proxy )
  - 作用方式:
    在 Client 端往 Internet 連線的途中架設一個中繼站，對 Client 發送的連線請求( Request )進行加工，達到隱蔽 Client 資訊的結果。
  - 實例:
    VPN
  - 位置:
    Client -- Internet 這個過程中
  - 手法:
    以 Proxy 的 IP 向網際網路( Internet )連線，使 Internet 到 Server 的這一段無法知道 Client 的 IP ，只能知道 Proxy 的 IP 。
  - 可用功能:
    + 突破防火牆
        * 好處:
            實現資訊自由 XD
    + 隱蔽 Client 端資訊
        * 好處:
            想要偷看連線的人，無法輕易取得 Client 的真實資訊，降低 Client 端受攻擊的風險。

## 反向代理( Reverse Proxy )
  - 作用方式:
    在連線請求( Request )從 Internet 進入 Server 端的途中架設一個中繼站，處理送進來的連線請求，避免惡意連線進入。
  - 實例:
    Nginx
  - 位置:
    Internet -- Server 這個過程中
  - 手法:
    接收到網際網路傳入的連線請求後，判斷「是否允許連線請求接觸 Server 」，此機制也能達到「分配連線給伺服器( Server )」的作用，讓擁有多個伺服器支援同一服務的廠商可以平衡伺服器之間的負荷(畢竟伺服器還不便宜，讓大家都平均忙好過有一個人累到壞掉，就算真的壞了還有別人可以及時補上)。
  - 可用功能:
    + 過濾黑名單 IP
        * 好處:
            對於已知的惡意 IP ，可建立黑名單，在收到連線請求時就不轉送，避免惡意 IP 接觸提供服務的 Server。
    + 隱蔽 Server 端資訊
        * 好處:
            傳入的連線不會知道要連向哪個 Server ，都是透過反向代理轉介，所以不必將 Server IP 暴露給網際網路，若是遭受攻擊是反向代理被攻擊， Server 會處在安全地帶。
        * 附註:
            反向代理被攻擊雖然也不好，但負責反向代理的機器與提供服務的伺服器分開的話，負荷較輕的反向代理所在伺服器就算掛掉，提供主服務的伺服器也能繼續運作，只要把新的反向代理建起來即可，影響範圍會少很多。
    + 分配接收不同連線請求的 Server
        * 好處: 達到 Server 之間的負載平衡。避免單一伺服器負荷過重，也能對不同連線提供相應的客製化服務。

## 情境模擬

當一個所在地為中國的 IP 想要突破網路長城連線到 google 時：
1. 此 IP 會連線到 代理伺服器 ( Proxy Server ) ，將連線請求進行偽裝，藉此通過網路長城。
2. 出了網路長城後，連線至網際網路，走向 google 的服務。
3. google 的反向代理伺服器( Reverse Proxy Server )接收到連線請求後，將連線請求轉送給提供 google 服務的眾多 server 中，比較不忙的那個(或者專門服務中國區連線的 Server )

## 參考資料
- [Day02-何謂網路釣魚，Reverse Proxy 又是什麼](https://ithelp.ithome.com.tw/articles/10202316)
    + 簡單解釋 Reverse Proxy 運作原理，包含負載均衡等名詞解釋
- [What Is A Reverse Proxy? | Proxy Servers Explained](https://www.cloudflare.com/zh-tw/learning/cdn/glossary/reverse-proxy/)
    + 有兩張圖示解釋 Proxy & Reverse Proxy 各自與 Client, Internet & Server 的關係
- [What is a Reverse Proxy vs. Load Balancer?](https://www.nginx.com/resources/glossary/reverse-proxy-vs-load-balancer/)
    + 關於反向代理如何實現負載平衡的說明
- [用 Nginx 伺服器建立反向代理](https://ithelp.ithome.com.tw/articles/10221704)
    + 示範反向代理大概會如何撰寫設定檔
- [WEB的正向代理與反向代理](https://jackterrylau.pixnet.net/blog/post/229520831-web%E7%9A%84%E6%AD%A3%E5%90%91%E4%BB%A3%E7%90%86%E8%88%87%E5%8F%8D%E5%90%91%E4%BB%A3%E7%90%86)
    + 以較生活化的例子解釋代理與反向代理
- [系統設計 - 正向代理跟反向代理](https://www.jyt0532.com/2019/11/18/proxy-reverse-proxy/)
    + 兩種代理設計的比較
- [Wiki一下: Proxy server](https://en.wikipedia.org/wiki/Proxy_server)
- [Wiki一下: Reverse proxy](https://en.wikipedia.org/wiki/Reverse_proxy)
