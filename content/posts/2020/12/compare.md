---
title: "Compare"
menuTitle: "各種「比較」"
date: 2020-12-18T15:03:13+08:00
publishDate: 2020-12-18T15:03:13+08:00
draft: false
tags: ["compare","experience"]
pre : "<b>[工作筆記] </b>"
---

# 比較差異

# 比較大小
真實世界裡，可以量化、數值化、比較基準一致時，才有「比較大小」的意義。在電腦科學的世界裡也一樣，就算實際上程式不會報錯，也不是所有東西都應該用來比大小。

## 可以比大小的東西
- 數值、數字
- 日期時間(格式應為 timestamp, microsecond, ......，不是字串)
    * php
        + DateTime 系列
    * JavaScript
        + new Date()
        + 將字串變成日期型別 Date.parse()

## 「不要」拿來比大小的東西
- 字串
    * 因為字串會被轉成 ascii code, 依照 ascii code 的順序決定孰大孰小，在通常的情境下，字串比大小並沒有意義，比出來也不見得是預想中的效果。

## 常見錯誤
以下寫法**不好**，就算是在寫筆記或 temp code 也不要這樣寫，會顯得很沒 sence ，或者讓人誤會我們觀念不好。
- 拿字串格式的數字字元比大小
    * '2'>'1'
- 拿字串格式的日期比大小
    * '2020-12-21'>'2020-12-01'

## 參考資料
- [PHP - The DateTime class](https://www.php.net/manual/en/class.datetime.php)
- [PHP - Comparing two dates in PHP](https://www.geeksforgeeks.org/comparing-two-dates-in-php/)
- [JavaScript - Date](https://www.w3schools.com/js/js_dates.asp)
- [JavaScript - How to Compare Two Dates In JavaScript](https://www.c-sharpcorner.com/UploadFile/8911c4/how-to-compare-two-dates-using-javascript/)
- [JavaScript - Date.parse()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/parse)
