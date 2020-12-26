---
title: "Index of Database"
menuTitle: "資料庫的索引"
date: 2020-12-22T09:12:41+08:00
publishDate: 2020-12-22T09:12:41+08:00
draft: false
tags: ["SQL","experience","index","database"]
pre : "<b>[工作筆記] </b>"
---

# 索引的目的
為了讓找資料更快。但是這個「更快」是跟誰比較？是跟「沒有索引時從頭逐項查找」相比。

# 在查詢資料時索引值的用處

舉例有個資料表長這樣:
table_A
| column | is index ? |
|:------:|:----------:|
|   id   |      v     |
|  name  |            |

- 如果現在搜尋的是索引欄位 
    `SELECT * FROM table_A WHERE id = 3` 
    會用 B+ 樹的概念搜尋
- 如果現在搜尋的不是索引欄位 
    `SELECT * FROM table_A WHERE name = "Dingo"` 
    跟沒設定索引一樣，只能逐筆找

# 索引類型
在 InnoDB 中，它有提供的索引基本上分為兩大類 :
* clustered Index
* secondary Index
    - 覆蓋索引 ( covering index ) (預設)
        + 內涵:????
    - 連合索引 ( compound index )
        + 內涵:用複數欄位組合成一組索引，建立的順序會影響 index 是否能成功使用以及 WHERE 條件如何下。
    - 前綴索引 ( prefix index )
        + 內涵:????
    - 唯一索引 ( unique index )
        + 內涵:只有這個索引值是具有「必定唯一」的特性，其他種類的索引值都能重複。 unique index 可以做為 clustered Index 的索引值。




## 疑問

- from [B+樹](https://mark-lin.com/posts/20190911/)
    * 平衡二元搜尋樹 ( Balanced BST )
        + 時間複雜度怎麼判斷？
        + i/o 問題？
        + B 樹的設計概念開始看不懂

<!-- ## 暫時不想面對的 -->

## 參考資料
- [wiki](https://zh.wikipedia.org/wiki/%E6%95%B0%E6%8D%AE%E5%BA%93%E7%B4%A2%E5%BC%95)
- [30-11 之資料庫層的核心 - 索引結構演化論 B+樹](https://mark-lin.com/posts/20190911/)
- [30-12 之資料庫層的核心 - MySQL 的索引實現](https://mark-lin.com/posts/20190912/)
- [30-13 之資料庫層的優化 - 索引設計與雷區](https://mark-lin.com/posts/20190913/)
