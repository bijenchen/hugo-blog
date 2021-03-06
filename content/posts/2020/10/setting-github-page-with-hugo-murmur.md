---
title: "關於：用 hugo 搭配 github page 打造一個自己的部落格"
date: 2020-10-02T18:05:44+08:00
draft: false
hidden : true
tags: ["github page","hugo","toml","git","git submodule"]
pre : "<b>[架個部落格] </b>"
---

<!-- TOC -->
- [緣起](#緣起)
- [碰壁紀錄](#碰壁紀錄)
- [節外生枝](#節外生枝)
- [後記](#後記)
- [參考資料](#參考資料)

<!-- 內文 -->
## 緣起
做這件事的初衷其實是我想要把 github 當學習紀錄來用，順便讓自己熟悉 git 的使用。
雖然可以單純把每篇筆記做成 .md 檔案放到 github 裡，但是在檢視上似乎又不是非常方便，用手機看 github 時情感上覺得不太順眼，所以想要用 github.io 建立一個靜態網站當作部落格使用。

再來，由於對調校前端畫面沒什麼興趣，想要找現成的畫面模板套不同的文章內容，讓維護部落格這件事情可以最單純化，所以搜尋「 github blog 」看看大家都是怎麼做。找到[這篇](https://ithelp.ithome.com.tw/articles/10198964)和[這篇](https://medium.com/@allen6997535/%E5%BB%BA%E7%AB%8B%E4%B8%80%E5%80%8B%E5%B1%AC%E6%96%BC%E8%87%AA%E5%B7%B1%E7%9A%84-%E7%A8%8B%E5%BC%8F-%E9%83%A8%E8%90%BD%E6%A0%BC-4d295ed96236)，得到了看起來派得上用場的三個新名詞「 Jekyll 」、「 hexo 」和「 hugo 」，丟去 google 搜尋後大致知道這三個都是「靜態網站生成器」，主要的功能是提供模板與網頁生成引擎(參考的是[這篇](https://michaelchen.tech/technical-blogging/static-site-generator/))，讓我們可以在不必研究網頁要如何長出來的情況下運作一個靜態網站。

(但是我的直覺告訴我：「網頁生成引擎如何運作」這個知識對後端工程師來說逃得了一時、逃不了一世。嗯......希望未來的自己來打臉現在的我？ XD )

因為我相信實際使用之後才能真正體會三者的差異以及找出自己的偏好，所以借助[網路上的比拚文](https://raychiutw.github.io/2019/Static-Site-Generator-Comparison/)簡單判斷後，就決定從 hugo 開始實驗，反正之後發現不喜歡就換一個嘛～

## 碰壁紀錄
* 遇到 GitHub "fatal: remote origin already exists"
    + 處理方式：重新指定遠端數據庫位置
        ```
            git remote set-url origin git@github.com:[your_github_account]/[repository].git
        ```
        - your_github_account:遠端數據庫擁有者的帳號名稱
        - repository:遠端數據庫名稱
        - `git remote set-url origin` 後面接的就是在 github 上想要用 ssh 下載專案時顯示的專案位址

* 遇到 error:src refspec master does not match any
    + 原因：沒有進行第一次 commit 就想 git push (這真的太瞎了，是想推個鬼？到底有多迷惘 XD)
    + 處理方式：每次開啟新的專案想要進行版本控制時，一定要記得先從 `git init` 開始，新增檔案後進行 first commit ，接著就能做平常熟悉的 git push 了～

* 搞不懂 git submodule 在幹嘛
    + 目前模糊的理解是： submodule 就是以「引用」的概念去連結別的專案，不參與開發而是單純使用別的專案的內容，所以理論上應該是進行 git pull 居多

* 沒辦法發布最新版的內容？
    + public 要 commit & push
    + hugo site 要把 commit 過的 public/ 整個資料夾 commit & push 進 hugo site repository
    + draft 設定要從 true 改成 false

* 找不到主頁
    + 原本想按照 theme 的建議，在 content 層加上 _index.md 檔案，但是有了 content/_index.md 後 hugo 在長 public 檔案時反而無法產生 index.html & index.xml ，導致網站找不到主頁。所以唯獨 content 層不建立 _index.md ，主頁問題日後再議。

## 節外生枝
* 想在 VS code 看到漂亮一點的 toml 檔
    + 在 VS code 的延伸模組搜尋關鍵字 TOML ，選一個看起來大家都在用的套件，例如 Better TOML 。
    + 安裝套件 Better TOML ，檔案會好讀很多。

## 後記
雖然各種跌撞碰壁，還因為個人心理狀態的關係遇到一點點卡關就懷疑人生。

但最後把東西做出來時真的很快樂～

比起實作，「寫筆記」這件事對我自己的挑戰更大，尤其是需要逐個步驟重現時超累。但是不趁實作完的當下紀錄的話，下次可能會從記憶一片空白開始。所以，為了對以後的自己好一點，現在就認真把筆記寫下來吧！

另外，因為我跑去翻了 public 資料夾裡面的 html 檔，想看看會是怎樣的結構，發現 hugo 自己產生的 html 檔案也太醜了吧！！要不是為了套模板，我應該無法忍受下去。哪一天我想不開去學了切版&前端以後，看我不把你換掉！

還是想試試「簡潔乾淨的模板，依照頁面引入不同的 md 檔」這樣的做法。

* 另外記一下耗費時間：從 0 開始到完成筆記 = 14.5 hr
    + 搞懂靜態網頁產生器是啥 Jekyll, hexo, hugo
    + 搞懂如何使用 github.io ，包含複習 git init ......
    + 撰寫筆記
    + 本地測試 & 實際部署
    + 挑theme XD

## 參考資料
* [[Ting's筆記Day2] 在Github用Jekyll創建自己的blog](https://ithelp.ithome.com.tw/articles/10198964)
    + 獲得知識
        - github Page 可以搭 Jekyll, hexo, hugo 來產生靜態網站。
* [建立一個屬於自己的(程式)部落格！](https://medium.com/@allen6997535/%E5%BB%BA%E7%AB%8B%E4%B8%80%E5%80%8B%E5%B1%AC%E6%96%BC%E8%87%AA%E5%B7%B1%E7%9A%84-%E7%A8%8B%E5%BC%8F-%E9%83%A8%E8%90%BD%E6%A0%BC-4d295ed96236)
    + 獲得知識
        - Medium 目前還不支援 Markdown 語法，要用作技術文章部落格不太方便。
* [使用靜態網頁產生器 (Static Site Generator) 製作網站](https://michaelchen.tech/technical-blogging/static-site-generator/)
    + 獲得知識
        - 動態網站資安如果做得不好，會成為駭客攻擊的破口。靜態網站因為不必連資料庫，沒有這層煩惱。
        - 靜態網站生成器分為三個部分：網頁內容 (content)、模板 (template)、網頁生成引擎 (site-generating engine)
* [靜態網站產生器大比拚](https://raychiutw.github.io/2019/Static-Site-Generator-Comparison/){:target="_blank"}
    + 獲得知識
        - Jekyll, Hugo, Hexo 三者目前都是免費和開源。
        - Jekyll 文長累積久了可能會變肥變慢。
        - Hexo 雖然看起來有豐富的中文文件可以參考，但看到缺點是「錯綜複雜的 npm 生態」只好先不要，要節外生枝研究 npm 如何錯綜複雜之後再說(逃走)。
* [Better TOML](https://marketplace.visualstudio.com/items?itemName=bungcip.better-toml)
* 關於重新指定遠端數據庫位置
    - [GitHub “fatal: remote origin already exists”](https://stackoverflow.com/questions/10904339/github-fatal-remote-origin-already-exists)
    - [[Git筆記] 如何移除 remote origin](https://andy6804tw.github.io/2019/01/04/git-remove-remote/)
* 關於沒有進行首次 commit
    - [Git常見錯誤與操作：error: src refspec master does not match any解決辦法](https://www.itread01.com/content/1546763944.html)
        - 雖然我對這個網站的內容比較有戒心，但是這篇文章給迷惘的我當頭棒喝，所以還是記下來！
* 可以經常複習一下的 git 教學
    - [為你自己學 Git:新增、初始 Repository](https://gitbook.tw/chapters/using-git/init-repository.html)
* git submodule 的觀念
    - [Git Submodule 的認識與正確使用！](https://josephj.com/entry.php?id=342)
    - [Git Submodule 介紹與使用](https://blog.wu-boy.com/2011/09/introduction-to-git-submodule/)