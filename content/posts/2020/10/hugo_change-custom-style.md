---
title: "Change Custom Style"
menuTitle: "設定 custom header"
date: 2020-10-18T22:48:56+08:00
publishDate: 2020-10-18T22:48:56+08:00
draft: false
tags: ["github page","hugo"]
pre : "<b>[架個部落格] </b>"
---

## 目標

想要在每篇文章顯示最後更新時間，最好能自動吃存檔時間。

## 過程紀錄

* 閱讀 Learn Theme for Hugo 教學文件的 [Style customization](https://learn.netlify.app/en/basics/style-customization/) 章節，知道了套用主題時，應該在跟 content 同層級的 layouts 放樣板html，如果想要加入自訂 header ，應該在 layouts/partials/ 增加一個名為 custom-header.html 的檔案， Learn Theme 的 header.html 會去吃 custom-header.html 增加到主題的 header 中。
* 閱讀 hugo 官方文件的 [front-matte](https://gohugo.io/content-management/front-matter#predefined) 章節，發現有 last modified 的參數可用 `lastmod` 。
    + 在 hugo 官網搜尋「lastmod」關鍵字，找到 [.Lastmod](https://gohugo.io/variables/git/#lastmod) function 的說明，發現 lastmod 可以吃 git 資訊，但是要設定 config 。 config 詳細的設定也附上了連結「[front matter configuration for dates](https://gohugo.io/getting-started/configuration/#configure-front-matter)」。
* 原本不知道如何寫 custom-header ，但是因為 google 搜尋 hogo LastMod 參數時，找到[這篇](https://willliu.me/blog/history-of-edition-of-hugo/)，看起來應該可以直接用，所以把 lastmod 的 html code 丟進去我自己的 custom-header.html 試試，發現在頁首真的有長出最後編輯的資訊，讚啦！目前這樣就滿足了！

## 參考資料
- [Hugo Blog 進化筆記](https://willliu.me/blog/history-of-edition-of-hugo/)