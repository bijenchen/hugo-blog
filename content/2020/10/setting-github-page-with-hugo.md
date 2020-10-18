---
title: "用 hugo 搭配 github page 打造一個自己的部落格"
menuTitle: "hugo blog"
date: 2020-10-02T14:26:05+08:00
publishDate : 2020-10-02T14:26:05+08:00
draft: false
tags: ["github page","hugo"]
pre : "<b>[架個部落格] </b>"
---

<!-- TOC -->
- [目標](#目標)
- [前置作業](#前置作業)
- [執行步驟](#執行步驟)
    - [使用 hugo 產生靜態網頁](#使用-hugo-產生靜態網頁)
        - [1. 安裝 hugo](#1-安裝-hugo)
        - [2. 安裝完之後可以確認一下是否成功安裝。](#2-安裝完之後可以確認一下是否成功安裝)
        - [3. 成功安裝後，產生 hugo 架構的網頁專案檔案。](#3-成功安裝後產生-hugo-架構的網頁專案檔案)
        - [4. 將整個專案加入 git 版本控制](#4-將整個專案加入-git-版本控制)
        - [5. 安裝主題](#5-安裝主題)
        - [6. 增加一篇文章](#6-增加一篇文章)
        - [7. 在本地預覽網站(含草稿)](#7-在本地預覽網站含草稿)
    - [建立 Repository](#建立-repository)
        - [1. 建立自己的 github.io Repository](#1-建立自己的-githubio-repository)
        - [2. 建立自己 hugo site 的 Repository](#2-建立自己-hugo-site-的-repository)
    - [發布至 github.io](#發布至-githubio)
        - [1. 確認想發布的文章已經完稿(已非草稿狀態)](#1-確認想發布的文章已經完稿已非草稿狀態)
        - [2. 在 hugo site 專案資料夾中產生一個 public 資料夾， public 資料夾要引用自己的 github.io 的專案內容](#2-在-hugo-site-專案資料夾中產生一個-public-資料夾-public-資料夾要引用自己的-githubio-的專案內容)
        - [3. 將 hugo site 裡編輯過的內容轉成網頁內容](#3-將-hugo-site-裡編輯過的內容轉成網頁內容)
        - [4. 將產生的 public 的內容推上 github.io repository](#4-將產生的-public-的內容推上-githubio-repository)
        - [5. 將長出來的 public 資料夾 push 上 your-hugo-repository](#5-將長出來的-public-資料夾-push-上-your-hugo-repository)
        - [6. 打開自己的 github.io 頁面，即可看到更新](#6-打開自己的-githubio-頁面即可看到更新)
- [參考資料](#參考資料)

<!-- 內文 -->
## 目標
在 github.io 上產生一個用 hugo 打造的個人主頁 : https://your-github-account.github.io

[契機和碰壁紀錄在這邊](/content/2020/10/setting-github-page-with-hugo-murmur/)


## 前置作業
1. 擁有一個 github 帳號，而且自己的 domain name 「 your-github-account.github.io 」還沒被佔用。
2. macOS 中可以使用 Homebrew 進行安裝工作。(目前只實驗到 mac 環境 Q_Q )

## 執行步驟

### 使用 hugo 產生靜態網頁
#### 1. 安裝 hugo
```
brew install hugo
```
#### 2. 安裝完之後可以確認一下是否成功安裝。
這時候可以看一下版本(version)或者使用說明(help)，如果下了指令後有出現對應的內容，就代表有安裝到指定程式。

* 看版本
    ```
    hugo version
    ```
* 看使用說明
    ```
    hugo --help
    ```
#### 3. 成功安裝後，產生 hugo 架構的網頁專案檔案。
your-website-name 請填入想取的名字。

指令 `hugo new site` 會為我們自動產生依據 hugo 網站結構規範的檔案與資料夾組合，

檔案跟資料夾要按照 hugo 的要求放， hugo server 在生成網頁時才不會找不到檔案。
```
hugo new site your-website-name
```
#### 4. 將整個專案加入 git 版本控制
在 your-website-name 資料夾內執行以下指令，讓 git 知道這整個資料夾要被 git 追蹤
```
git init
```
#### 5. 安裝主題
接下來，因為我選擇的主題是 [Hugo Learn Theme](https://github.com/matcornic/hugo-theme-learn) ，所以按照主題的官方文件安裝主題。

- 在 hugo site 的結構裡找到 themes 資料夾，在 themes 資料夾裡執行 git clone ，把主題所用到的程式碼從遠端抓下來。
    ```
    ## 進入 themes 資料夾
    cd themes/

    ## 從指定網址取下最新版本的 "Hugo Learn Theme" 程式碼
    git clone https://github.com/matcornic/hugo-theme-learn.git

    ## 如果不打算異動別人做好的主題，或者想要跟著別人的專案更新，可以用以下指令取代 git clone ，但是我並不打算頻繁更新主題，所以沒有選擇這個做法。
    git submodule add -f https://github.com/matcornic/hugo-theme-learn.git
    ```
- 下載完成後就可以在 themes 資料夾看到新增的資料夾「 hugo-theme-learn 」， hugo-theme-learn 裡面會有呈現 Hugo Learn Theme 所需要的資料夾結構與檔案。
- 接著打開 config.toml ，新增 theme 項目並指定特定主題，設定完存檔即可。
    ```toml
    # 基本的 config 內容
    # 這邊是設定部落格首頁的地方，在我們的情境裡應該要輸入自己的 github.io 主頁網址 https://your-github-account.github.io
    baseURL = "http://example.org/"

    # 設定網站的預設語系用
    languageCode = "en-us"

    # 設定網站的標題用，會顯示在瀏覽器頁籤上的那個名字
    title = "My New Hugo Site"

    # 額外的 config 內容
    # 例如我們現在新增的 config 項目，關於主題的指定
    theme = "hugo-theme-learn" # 這邊要寫 themes/ 裡面裝著主題專案程式碼的資料夾名稱
    ```
#### 6. 增加一篇文章
下面這個指令的意思是：在 content 裡增加一個 posts 資料夾，並且在 posts 裡產生一個檔案 my-first-post.md
```
hugo new posts/my-first-post.md
```
#### 7. 在本地預覽網站(含草稿)
執行以下指令，告訴 hugo 啟動 server 預覽並且連草稿一併顯示。
```
hugo server -D
```
執行完畢後，即可依照 terminal 上顯示的提示，進入 http://localhost:1313/ 預覽網站。

### 建立 Repository

#### 1. 建立自己的 github.io Repository
- 目的：用來當作發布網頁內容的地方
- 新增一個 github repository ， Repository name 設定為： [your-github-account].github.io 。個人主頁不能選「 Private 」，請維持為預設值「 Public 」。非必填的都可以暫不理會，所以不理會(README, .gitignore, license 之類的)

#### 2. 建立自己 hugo site 的 Repository
- 目的：用來作 hugo site 版本控管的地方
- 新增一個 github repository ， Repository name 喜歡設定什麼都可以，以下用： [your-hugo-repository] 代稱
- 將自己的 hugo site 加入被 git 控管行列
    - *僅首次需執行*
    - 使用指令 pwd 確認自己身在何方，應該要在專案資料夾裡
        ```
        pwd
        [project_path]/your-website-name
        ```
        ```
        git init
        ```
- 將 hugo site 專案指向遠端，按照 github 網頁上的 push an existing repository from the command line 裡的提示執行即可，執行位置一樣在專案資料夾裡

### 發布至 github.io

#### 1. 確認想發布的文章已經完稿(已非草稿狀態)
在文章 .md 檔的設定 draft 應該要是 false 喔～設定為 true 的發布後看不到！
```toml
draft: false
```

#### 2. 在 hugo site 專案資料夾中產生一個 public 資料夾， public 資料夾要引用自己的 github.io 的專案內容
- *本步驟只有第一次需要設定*
- 一樣使用指令 pwd 確認自己身在何方，應該要在專案資料夾裡
    ```
    pwd
    # terminal 會顯示目前所在位置的絕對路徑
    # 例如： [project_path]/your-website-name
    ```
- 引用自己的 github.io 專案，放到名為 public 的資料夾中。
    - 如果先建立 public 資料夾，會撞名產生衝突，所以不必事先手動建立 public 資料夾。
    ```
    git submodule add -f https://github.com/your-github-account/your-github-account.github.io.git public
    ```

#### 3. 將 hugo site 裡編輯過的內容轉成網頁內容
- 在專案資料夾裡裡執行下列指令
    - 這個步驟會按照 hugo site 的專案結構，將 .md 檔案變成 hugo 靜態網站對應位置的 html 檔案，並填進 public 資料夾中。 public 資料夾的內容就會是發布出去的網頁內容。
    ```
    hugo
    ```
#### 4. 將產生的 public 的內容推上 github.io repository
- 進入 public 資料夾
    ```
    cd public
    ```
- 將 public 資料夾加入被 git 控管行列
    - *僅首次需執行*
    ```
    git init
    ```
- 將 public 資料夾指向遠端的 repository
    - *僅首次需執行*
    ```
    git remote add origin https://github.com/your-github-account/your-github-account.github.io.git
    ```
- 將變動推上遠端的 repository
    ```
    git add . # 因為這邊要無腦推，不用檢查是否有 bug (信任 hugo 自動產生的檔案)，所以直接用 . 表示將全部異動加入要 commit 的內容中
    git commit -m "my-first-hugo"
    git push origin master # 這邊要寫遠端的主分支，如果 master 已改名成 main 要記得換一下
    ```
#### 5. 將長出來的 public 資料夾 push 上 your-hugo-repository
- 推上 your-hugo-repository 以後，才能看到對應的更新內容
    - 移動到專案資料夾的層級
        ```
        # 因為前一個步驟在 public 資料夾裡，所以這邊可以執行「移到外一層」的指令
        cd ..
        # 或者直接指定要移到專案所在的絕對路徑也行
        cd [project_path]/your-website-name/
        ```
    - 將變動推上 your-hugo-repository ，這邊檢查變動內容的話，應該只有 public 資料夾中的檔案而已
        ```
        git add . # 因為這邊也要無腦推，不用檢查是否有 bug
        git commit -m "寫些推版註解吧"
        git push origin master # 這邊要寫遠端的主分支，如果 master 已改名成 main 要記得換一下
        ```
#### 6. 打開自己的 github.io 頁面，即可看到更新

## 參考資料
* [hugo 官方文件 Getting Started](https://gohugo.io/getting-started/usage/)
* [hugo 可以設定的 config 項目](https://gohugo.io/getting-started/configuration/)
* [Hugo 快速安裝教學](https://raychiutw.github.io/2019/Hugo-%E5%BF%AB%E9%80%9F%E5%AE%89%E8%A3%9D%E6%95%99%E5%AD%B8/)
    + 獲得知識
        - 很實用，基本上照著做就會成功！推推～
        - 關於 hugo 專案裡個資料夾的用途介紹
* [Hugo教學：部落格網站](https://coolgood88142.github.io/zh-tw/posts/hugo/)
    + 獲得知識
        - 關於部署到 github.io 的部分，幾乎都是參考這篇文章。也是實用推推～
* [運用Github+Hugo免費部署靜態網站](https://medium.com/@jerrywu_3165/%E9%81%8B%E7%94%A8github-hugo%E5%85%8D%E8%B2%BB%E9%83%A8%E5%B1%AC%E9%9D%9C%E6%85%8B%E7%B6%B2%E7%AB%99-b92013c25956)
    + 獲得知識
        - 知道大致執行的步驟，以及選好的 hugo themes 要放在 hugo site 的哪個層級裡。但是這篇文章教的做法是剪剪貼貼檔案的方式，感覺會有風險、不太喜歡，所以僅作參考。
* [Hugo Learn Theme ](https://github.com/matcornic/hugo-theme-learn)
* [Hugo Learn Theme Demo](https://learn.netlify.app/en/)
* [Git教學：如何 Push 上傳到 GitHub？](https://gitbook.tw/chapters/github/push-to-github.html)
    + 獲得知識
        - 回憶一下新增 repository 看到的畫面
* [Day 15. Hugo Content - 文章狀態與 Q&A](https://ithelp.ithome.com.tw/articles/10245482?sc=hot)
    + 獲得知識
        - 文章要發布時記得把 draft 設定為 false