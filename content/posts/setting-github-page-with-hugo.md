---
title: "用 hugo 搭配 github page 打造一個自己的部落格"
date: 2020-10-02T14:26:05+08:00
draft: true
---


## 目標
在 github.io 上產生一個用 hugo 打造的個人主頁 : https://your-github-account.github.io

[契機在這邊](/murmur/murmur-setting-github-page-with-hugo/)

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
#### 4. 接下來，因為我選擇的主題是 [Hugo Learn Theme](https://github.com/matcornic/hugo-theme-learn) ，所以按照官方文件安裝主題。
- 在 hugo site 的結構裡找到 themes 資料夾，在 themes 資料夾裡執行 git clone ，把主題所用到的程式碼從遠端抓下來。
    ```
        ## 進入 themes 資料夾
        cd themes/

        ## 從指定網址取下最新版本的 "Hugo Learn Theme" 程式碼
        git clone https://github.com/matcornic/hugo-theme-learn.git
    ```
- 下載完成後就可以在 themes 資料夾看到新增的資料夾「 hugo-theme-learn 」， hugo-theme-learn 裡面會有呈現 Hugo Learn Theme 所需要的資料夾結構與檔案。
- 接著打開 config.toml ，新增 theme 項目並指定特定主題，設定完存檔即可。
    ```toml
        # 基本的 config 內容
        baseURL = "http://example.org/"
        languageCode = "en-us"
        title = "My New Hugo Site"

        # 我們現在新增的 config 項目，關於主題的指定
        theme = "hugo-theme-learn"
    ```
#### 5. 增加一篇文章
下面這個指令的意思是：在 content 裡增加一個 posts 資料夾，並且在 posts 裡產生一個檔案 my-first-post.md
```
    hugo new posts/my-first-post.md
```
#### 6. 在本地預覽網站(含草稿)
執行以下指令，告訴 hugo 啟動 server 並且連草稿一併顯示。
```
    hugo server -D
```
執行完畢後，即可依照 terminal 上顯示的提示，進入 http://localhost:1313/ 預覽網站。

### 以 github 建立個人主頁

#### 1. 未完成

### 發布至 github.io


## 參考資料
* [hugo 官方文件 Getting Started](https://gohugo.io/getting-started/usage/)
* [hugo 可以設定的 config 項目](https://gohugo.io/getting-started/configuration/)
* [Hugo 快速安裝教學](https://raychiutw.github.io/2019/Hugo-%E5%BF%AB%E9%80%9F%E5%AE%89%E8%A3%9D%E6%95%99%E5%AD%B8/)
    + 獲得知識
        - 很實用，基本上照著做就會成功！推推～
        - 關於 hugo 專案裡個資料夾的用途介紹
* [Hugo教學：部落格網站](https://coolgood88142.github.io/zh-tw/posts/hugo/)
    + 獲得知識
        - 關於部署到 github.io 的部分，幾乎都是參考這篇文章。
* [運用Github+Hugo免費部署靜態網站](https://medium.com/@jerrywu_3165/%E9%81%8B%E7%94%A8github-hugo%E5%85%8D%E8%B2%BB%E9%83%A8%E5%B1%AC%E9%9D%9C%E6%85%8B%E7%B6%B2%E7%AB%99-b92013c25956)
    + 獲得知識
        - 知道大致執行的步驟，以及選好的 hugo themes 要放在 hugo site 的哪個層級裡。但是這篇文章教的做法是剪剪貼貼檔案的方式，感覺會有風險、不太喜歡，所以僅作參考。
* [Hugo Learn Theme ](https://github.com/matcornic/hugo-theme-learn)
* [Hugo Learn Theme Demo](https://learn.netlify.app/en/)