---
title: "取得一個含有 sub module 的 laravel 專案"
menuTitle: "laravel"
date: 2021-05-05T10:33:34+08:00
publishDate: 2021-05-05T10:33:34+08:00
draft: true
tags: ["laravel","experience","sub module"]
pre : "<b>[工作筆記] </b>"
---

## 準備環境
1. Homestead 環境(已經安裝好 laravel 的虛擬機) [文章參考]()
2. 在 Homestead/ 資料夾中執行 `vagrant up` ，啟動虛擬環境
3. 在 Homestead/ 資料夾中執行 `vagrant ssh`，由本機進入虛擬環境
    *此時命令列應該要看到 vagrant@homestead:~ ，表示已經藉由 ssh 成為虛擬環境(而非本機環境)的使用者。如果不是在 Homestead/ 資料夾裡執行，而是在有安裝 vagrant 的其他資料夾層級執行 `vagrant up`，會另外長出一個新的虛擬環境，此時 `vagrant ssh`進入虛擬機以後，會看到 vagrant@vagrant:~ ，注意不要迷路了！*
4. 在虛擬環境中的同步資料夾 (依照 1. 的參考文章中，這邊的資料夾名為 Code/ ) 執行 git clone，取下有使用 sub module 的 laravel 專案
    1. 〈分歧途徑一〉取專案時使用基本的 git clone 指令，取下專案主體後再更新 submodule
        1. `vagrant@homestead:~/Code$ git clone git@bitbucket.org:[laravel_project].git`
        2. 取下專案主體後，在原地(e.g. homestead 裡的 Code/ ) 執行 `git submodule update --init --recursive` ，更新專案中所有用到的 submodule 版本
    2. 〈分歧途徑二〉取專案時增加參數，使得取出專案時一併更新 submodule
        1. `vagrant@homestead:~/Code$ git clone --recursive git@bitbucket.org:[laravel_project].git`
5. 取得專案主體與更新 submodule 後，即可進行 laravel 專案初始化
    1. composer install
        1. 如果 composer 版本過舊，可能會出現失敗，此時可以參考畫面提示執行 `composer self-update` 之類的指令更新 composer 版本。

## 參考資料
- [SQL CASE](https://www.1keydata.com/tw/sql/sql-case.html)
