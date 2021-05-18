---
title: "Nginx 筆記"
menuTitle: "Nginx"
date: 2021-05-18T11:53:26+08:00
publishDate: 2021-05-18T11:53:26+08:00
draft: true
tags: ["network","experience","reverse proxy","nginx"]
pre : "<b>[工作筆記] </b>"
---

## 觀念

當我們想透過瀏覽器訪問服務(專案)時，

遠端 server 上要設定特定 hostname 指向專案位置。

注意： 「 local 端設定 hosts 指引本地在開啟瀏覽器時，特定網址要往哪個 IP 連 」這件事是 client 端的連線處理，跟放在 server 端的 nginx 沒有關係，詳見筆記 [代理與反向代理](/posts/2021/05/proxy_and_reverse_proxy)

## 指令集合

- 測試
  + `sudo nginx -t`
  + 意義：以超級管理員權限執行 test ， 檢查 nginx 設定檔內的語法是否出錯。 // TODO: 待補佐證資料

- 重啟
  + `sudo service nginx reload`
  + 意義：以超級管理員權限執行 reload ， 會重新讀取 nginx 設定檔內的設定並進行指向分配。  // TODO: 待補佐證資料

## 權限不足時顯示的畫面

- 未使用足夠權限的身份執行，導致部分檔案無法讀取。
  + [](https://imgur.com/RwEy5Wd)
  + 解法：使用更高權限的身份執行，或者直接用 sudo (用 sudo 之前，先確定自己清楚當下的行為以及結果喔！)

## 設定舉例

// TODO: 實際意義待查

```
server {
        server_name bijen-project_1; # <-- domain name

        listen 80;
        root /home/bijen/www/project_1/frontend/dist;
        access_log /var/log/nginx/access.log;
        error_log /var/log/nginx/error.log;
        index index.html;

        error_page  404 /404.php;

        location / {
            try_files $uri $uri/ /index.html;
        }

        location /sitemap.xml{
            rewrite ^ /sitemap permanent;
        }

        location ~* \.(jpg|jpeg|gif|css|png|js|ico|html)$ {
            access_log off;
            expires max;
        }

        location ~ /\.ht {
            deny  all;
        }

        location ~ \.php$ {
            include snippets/fastcgi-php.conf;
            fastcgi_pass 127.0.0.1:9001;
            fastcgi_param CI_ENV 'development';
        }
}

server {
        server_name bijen-project_2; # <-- domain name

        listen 80;
        root /home/bijen/www/project_2;
        access_log /var/log/nginx/access.log;
        error_log /var/log/nginx/error.log;
        index index.php;

        error_page  404 /404.php;

        location / {
            allow all;
            try_files  $uri $uri/ /index.php?$args;
            autoindex on;

            autoindex_exact_size off;
            autoindex_localtime on;
        }

        location /sitemap.xml{
            rewrite ^ /sitemap permanent;
        }

        location ~* \.(jpg|jpeg|gif|css|png|js|ico|html)$ {
            access_log off;
            expires max;
        }

        location ~ /\.ht {
            deny  all;
        }

        location ~ \.php$ {
        include snippets/fastcgi-php.conf;
            fastcgi_pass 127.0.0.1:9001;
            fastcgi_param CI_ENV 'development';
        }
}
```

## 參考資料
- [[筆記][Server] Nginx 常用指令](https://gist.github.com/jackyu/6379418)
