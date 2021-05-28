---
title: "Select Data"
menuTitle: "報表資料撈取"
date: 2020-11-30T18:04:49+08:00
publishDate: 2020-11-30T18:04:49+08:00
draft: false
tags: ["SQL","experience"]
pre : "<b>[工作筆記] </b>"
---

# 原則

在決定查詢條件時，先確定報表撈取的目標(為了什麼目的-Why、想看到哪些欄位、如果有一對多的資料時誰該當主表)
* Why
    為了什麼目的？
* Where
    資料在哪些表( table )裡？
* What
    想看到哪些欄位？
* Who
    + 是不是只要特定範圍的資料？(以「身份」作為限縮條件)
    + 誰要看？需求是什麼？
* When
    是不是只要特定範圍的資料？(以「時間」作為限縮條件)
* How
    決定 SQL , Subquery? Join?......?

# 注意事項

* 如果有一對多的資料時誰該當主表？
    + 依照需求判斷，想要長出怎樣的表？
        - e.g. table A 對 table B 為一對多 ( table A 1--* table B )
        - 如果今天想看的是每筆 B 的 record 對應到 A 的資料，也就是「當 B 有 2 筆(b1,b2)、對應到一筆A資料(a1)時，總資料要有 2 筆」時，應該是這樣：
            ```sql
                SELECT *
                FROM table_B
                JOIN table_A
            ```
        - 相反的，如果只在乎能對應到任一 B record 的 table A 資料，會變成：
            ```sql
                SELECT *
                FROM table_A
                JOIN table_B
            ```

## 參考資料
- []()

> 這很基本，小心不要迷失自己！
