---
title: "Hugo 的列表功能"
menuTitle: "Hugo_list Page"
date: 2021-08-11T16:15:59+08:00
publishDate: 2021-08-11T16:15:59+08:00
draft: true
tags: ["github page","hugo"]
pre : "<b>[架個部落格] </b>"
---

想要自動產生像這樣的列表，但還沒實驗成功：
TODO!

- yyyy-mm-nn : [article title] article description (link)
- yyyy-mm-nn : [article title] article description (link)
- yyyy-mm-nn : [article title] article description (link)


theme "learn" 有 [Children](https://learn.netlify.app/en/shortcodes/children/) 這個 shortcodes 可用，但我還沒找到自訂 description 以及顯示文章日期的方法。
learn 的 short code 是寫在 `.md` 裡。

hugo 的列表頁好像也有參數可以調，可能可以試看看
https://gohugo.io/templates/lists/

但這樣會變成需要額外客製自己的頁面，要注意不要跟框架衝突。


## 參考資料
- [learn 主題的 shortcodes](https://learn.netlify.app/en/shortcodes/)
    - learn 主題的 shortcodes ，種類不算少
- [shortcodes](https://gohugo.io/content-management/shortcodes/)
    - hugo 原生的 shortcodes ，要寫在 `.html` 裡。
- [Create Your Own Shortcodes](https://gohugo.io/templates/shortcode-templates/)
    - hugo 可以客製 shortcodes
- [Content Summaries](https://gohugo.io/content-management/summaries/)
    - hugo 的摘要運作方式

