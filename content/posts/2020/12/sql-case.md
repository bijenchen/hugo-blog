---
title: "SQL Syntax : CASE"
menuTitle: "SQL 裡 CASE 的用法"
date: 2020-12-21T15:18:34+08:00
publishDate: 2020-12-21T15:18:34+08:00
draft: false
tags: ["SQL","experience","CASE"]
pre : "<b>[工作筆記] </b>"
---

```sql=
SELECT CASE ("欄位名")
  WHEN "條件1" THEN "結果1"
  WHEN "條件2" THEN "結果2"
  ...
  [ELSE "結果N"]
  END
FROM "表格名";
```

## 參考資料
- [SQL CASE](https://www.1keydata.com/tw/sql/sql-case.html)
