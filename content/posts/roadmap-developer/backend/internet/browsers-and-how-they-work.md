---
title: "Browsers and How They Work"
menuTitle: "瀏覽器"
date: 2020-10-19T00:12:47+08:00
publishDate: 2020-10-19T00:12:47+08:00
draft: false
tags: ["roadmap-developer","internet","browser"]
pre : '<i class="fas fa-globe" style="margin: 3px;"></i>'
---
# 瀏覽器有哪些 ? 他們是如何運作 ?

## 瀏覽器有哪些

瀏覽百家爭鳴欸！光是版面引擎(layout engines)就有 6 套以上！

然後行動裝置的網頁瀏覽器又是另一個戰場。還有只顯示文字不顯示圖片的瀏覽器，長知識！@A@

## 如何運作

- The User Interface
- The Browser Engine
- The Rendering Engine
- Networking
- JavaScript Interpreter
- UI Backend
- Data Persistence/Storage

html,css 的部分由 Rendering Engine (layout engines) 負責解析，解析後拋給瀏覽器(Browser Engine)引擎。
JavaScript 編譯出來的內容也由 Rendering Engine 收集、網路連線也是 Rendering Engine 處理。

Browser Engine 負責拿 Rendering Engine 給的資料和 Storage 的內容去長畫面給人類看。

## 參考資料
- [wiki](https://en.wikipedia.org/wiki/List_of_web_browsers)
- [How does web browsers work?](https://medium.com/@monica1109/how-does-web-browsers-work-c95ad628a509)