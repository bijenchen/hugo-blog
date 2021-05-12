---
title: "版本控制相關"
menuTitle: "Git - Version Control / Basic Usage of Git"
date: 2021-05-12T15:13:34+08:00
publishDate: 2021-05-12T15:13:34+08:00
draft: true
tags: ["roadmap-developer","general","git"]
pre : '<i class="fas fa-key" style="margin: 3px;"></i>'
---

## 版本控制的目的

避免功能開發的過程中出現混亂，讓不應推出的程式碼混雜在即將推出的分支中。

## 目前較知名的版本控制流程

- git flow
    + 共用 repository, 原則上只有確定要推出的功能才會合進 main(master)，所以有 release, development 等設計
- github flow
    + 因為開發者都有自己的 repository, 所以大家都是從自己的 main(master) 出發，功能會匯集到自己的 main(master)，再對推出服務的主 repository 發送合併請求( pull request )
- gitlab flow
    + 還沒搞懂 Q_Q


## 參考資料
- [三種版控流程](https://medium.com/@lf2lf2111/%E4%B8%89%E7%A8%AE%E7%89%88%E6%8E%A7%E6%B5%81%E7%A8%8B-29c82f5d4469)
    + 如標題，三種流程的簡介
- [Introduction to GitLab Flow](https://docs.gitlab.com/ee/topics/gitlab_flow.html)
    + gitlab 官方文件，說明為何會推出 gitlab flow 此機制。宣稱是結合 git flow & github flow 的優點，但我還沒搞懂哪裡比較優了......
- [筆記：TBD是三小?---What is Trunk Based Development?](https://nedwu13.blogspot.com/2014/01/tbd-what-is-trunk-based-development.html)
    + 另一種流程： Trunk Based Development, 但又更少碰到，先存參。