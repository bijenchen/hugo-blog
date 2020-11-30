---
title: "google sheet 條件格式設定自訂公式"
menuTitle: "google sheet 自訂公式"
date: 2020-11-30T18:05:53+08:00
publishDate: 2020-11-30T18:05:53+08:00
draft: false
tags: ["google sheet","formula","experience"]
pre : ""
---

* 比較 A 欄 與 B 欄差異
    + 套用範圍
        - B1:B100
    + 自訂公式
        - $A1<>$B1
            * 意義：同一列的 A 欄 不等於 B 欄，「$」的作用是鎖定，沒有加「$」的數值會隨著判斷變動
        - 如果有複數條件，用 AND()
            * =AND($A1<>$B1,$C3<>"timestamp")
                + 意義：同上，且同一列的 C 欄 不等於 timestamp

# 注意事項

* 文字要用雙引號「"」包起來

## 參考資料
- [絕對參照與相對參照](https://support.google.com/docs/answer/78413?co=GENIE.Platform%3DDesktop&hl=zh-Hant)
- [Google 試算表函式清單](https://support.google.com/docs/table/25273)
