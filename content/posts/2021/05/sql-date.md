---
title: "SQL Syntax : DATE_PART"
menuTitle: "SQL 裡 DATE_PART 的用法"
date: 2021-05-28T10:39:08+08:00
publishDate: 2021-05-28T10:39:08+08:00
draft: true
tags: ["SQL", "experience", "PostgreSQL", "DATE_PART"]
pre : "<b>[工作筆記] </b>"
---

PosgreSQL 裡有函數可以辦到「擷取日期片段」的目標，寫法如下：

`DATE_PART(field,source)`

- `source` 參數 : 指定要擷取的對象，必須為時間格式 `TIMESTAMP`, `TIME`, or `INTERVAL` ，如果傳入的值被判斷為 `DATE` 格式，會被函數轉成 `TIMESTAMP` 進行運算。
- `field` 參數 : 指定要擷取的時間單位，例如：世紀、年、月、日、時、毫秒等等。
    * 可用的值(例示非列舉) // TODO: 補上文件佐證，看能不能列舉完。
        + century
        + decade
        + year
        + month
        + day
        + days : 計算時間區段的天數， source 參數需填入 `INTERVAL` 格式的值

            使用示範
            ```sql
                date_part( 'days', ( `start_date` - `end_date` ) ) AS "expire_days"
            ```
        + hour
        + minute
        + second
        + microseconds
        + milliseconds
        + dow : 每週的第幾天
        + doy : 每年的第幾天
        + epoch
        + isodow
        + isoyear
        + timezone
        + timezone_hour
        + timezone_minute

## 參考資料
- [PostgreSQL Tutorial](https://www.postgresqltutorial.com/)
    * PostgreSQL 好用教學網站
- [PostgreSQL DATE_PART Function](https://www.postgresqltutorial.com/postgresql-date_part/)
