---
title: "部署專案相關筆記"
menuTitle: "Deploy a project"
date: 2021-05-18T17:20:03+08:00
publishDate: 2021-05-18T17:20:03+08:00
draft: true
tags: ["deploy","experience"]
pre : "<b>[工作筆記] </b>"
---

## 基本步驟
1. [在要提供服務的伺服器] 建立 or 取下專案
2. [在要提供服務的伺服器] 如果專案有前後端相關的 config
    (像是前端要指定 hostname & domain name[關於DNS](content/posts/roadmap-developer/backend/internet/dns-and-how-it-works)，後端要設定資料庫連線等) ，
    設定好 config，例如
    - frontend/config
    - application/config/development/database.php
3. [在要提供服務的伺服器] 需要的話，執行 npm install(僅初次需執行) ＆ npm run build(需要重打包就要執行)，把畫面所需的 js 等等打包出來
4. [在要提供服務的伺服器] 設定 nginx 設定檔的內容
    - 例如這種檔案: /etc/nginx/conf.d/abcabc.conf
    - 設定之前請先進行檢查 nginx -t([指令筆記](content/posts/2021/05/nginx))
    - 設定之後除了檢查(nginx -t)以外，還要記得 reload ，才能讓伺服器吃到新的設定內容。
5. [在要提供服務的伺服器] 設定 hostname 對應 ip
    - /etc/hosts
6. [在本地端] 設定 hostname 對應 ip
    - /etc/hosts

## 舉例
今天有個專案 abcabc ，希望部署在遠端伺服器(代稱: server_A)，本地以「 http://abcabc_test 」進行連線。
1. server_A 上取下專案 abcabc (git clone 之類的)
2. abcabc 這個專案需要在 frontend/config/ 的 index.js & env.js 裡設定 domain 資訊，所以在 server_A 上的 abcabc 專案裡的 index.js & env.js ，把「 http://abcabc_test 」設定進去。
3. 在 server_A 上執行 npm install ＆ npm run build
4. 在 server_A 設定 nginx 設定檔的內容
    ```
    server {
            server_name abcabc_test; # hostname

            listen 80;
            root /home/bijen/www/abcabc/frontend/dist; # path of the project (at server_A)
            access_log /var/log/nginx/access.log;
            error_log /var/log/nginx/error.log;
            index index.html;

            error_page  404 /404.php;
            [設定未完，下略]
    }
    ```
5. (& 6.)在 server_A & local 設定 /etc/hosts
    ```
    [ip_of_server_A]  abcabc_test
    ```

## 參考資料
- []()
