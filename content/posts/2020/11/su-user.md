---
title: "Su User"
menuTitle: "在 linux 裡用指令切換使用者"
date: 2020-11-17T11:45:41+08:00
publishDate: 2020-11-17T11:45:41+08:00
draft: false
tags: ["command in linux","su","experience"]
pre : "<b>[工作筆記] </b>"
---

**這個單元有點邪惡，除非必要否則不要擅自進行。**

在 linux 中想要偽裝成別的使用者操作的話，可以使用 su ( switch user ) 切換使用者。

使用的情境像是「要替已經下班的某位同事更新測試機程式」之類的狀況，因為對方的測試機只有當事人能 pull code，所以只好切換成對方的身份進行。

要注意的是，**請確認對方真的沒有登入連線在做事**，否則我幫對方 pull code ，可能會把對方正在執行中或修改中的東西蓋掉！

## 作法
- 有 sudo 權限的情況下
    - 使用 sudo su [對方使用者名稱] 指令切換
        ```
        $ sudo su [user_name]
        ```
    -  要求輸入「執行 sudo 指令的使用者」的密碼
    -  commend line 最前面會出現對方使用者帳號
        ```
        對方使用者名稱@機器名稱:所在路徑$
        my_partner@my_machine:/home/my_partner_folder$
        ```
    - 使用完畢輸入 exit 指令，跳出偽裝
        ```
        $ exit
        ```

## 參考資料
這是不用 sudo 的版本
- [How to Use the su Command in Linux with Examples](https://phoenixnap.com/kb/su-command-linux-examples)
