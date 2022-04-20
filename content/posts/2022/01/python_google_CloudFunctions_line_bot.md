---
title: "在 Google Cloud Platform(GCP) 上建立一個無伺服器(serverless)的 Python Line 機器人服務"
menuTitle: "Python google CloudFunctions line bot"
date: 2022-01-17T12:00:33+08:00
publishDate: 2022-01-17T12:00:33+08:00
draft: false
tags: ["Python","LINE Bot","GCP","Google Cloud Platform","Cloud Functions","serverless"]
pre : "<b>[身為工程師就是要偷懶] </b>"
---
## 緣起
合租的地方開了一次小會議，決定更新已不敷使用的公共區域打掃規則，  
為了讓大家逐漸適應新規則，起心動念寫一個提醒機器人負責固定提醒掃地時間～  

之前製作機器人都需要一個伺服器維持運作，  
但 GCP 上有提供無伺服器的服務，能夠讓我放這種小到不行的小服務，  
因此決定來試用看看～

## 實做
### 佈署步驟
#### 1. 取得 LINE Bot Token
首先要有一支正常運作的程式，再來考慮佈署的問題。  
LINE Bot 最簡易的版本可以參考 [Pyladies 入門活動的教學](https://marsw.github.io/Python-Tutorial/07_v2_applications.slides.html#/2) ，我們需要做的只有「取得 LINE API Token 」這件事而已。
#### 啟用 GCP 服務
python_google_CloudFunctions_line_bot_gcp_01_start
#### 佈署上 Cloud Functions
##### 設定環境變數
##### 設定入口 function
#### 測試程式運作正常


### 程式碼
```python
# importing requests module for post to LINE
import requests
# importing os module for using environment variables
import os
# importing datetime module for now()
import datetime

def clean_up_notify(request):
    # 設定提醒規則，未來可因應需求更新
    # 每月第一天：「工作交換」提醒
    first_day = 1
    # 每月日期尾數為5：「打掃」提醒
    notify_days = [5,15,25]

    # 引入預先設定好的環境變數，原則上不異動
    # 要讓使用者收到的訊息
    msg         = os.environ['NOTIFY_MESSAGE']
    msg_monthly = os.environ['NOTIFY_MESSAGE_MONTHLY']
    msg_days    = os.environ['NOTIFY_MESSAGE_DAYS']
    # LINE API
    # API 對接 token
    token = os.environ['TOKEN']
    # API 對接路徑
    url = os.environ['LINE_API_URL']
    # API 指定 headers
    headers = {
        "Authorization": "Bearer " + token,
        "Content-Type" : "application/x-www-form-urlencoded"
    }

    # using now() to get current time
    current_time = datetime.datetime.now()

    is_first_day   = True if current_time.day == first_day   else False
    is_notify_days = True if current_time.day in notify_days else False

    payload = {'message': msg}

    if is_first_day or is_notify_days:

        if is_first_day :
            payload = {'message': msg_monthly}
        elif is_notify_days :
            payload = {'message': msg_days}

        r = requests.post(url, headers = headers, params = payload)
    else : # debug 用，這段可以不要
        print('current_time')
        print(current_time)
        r = requests.post(url, headers = headers, params = payload)

```

## 參考資料
- [使用 Python+Google Cloud Platform+Line Bot 自動執行例行瑣事](https://medium.com/zrealm-ios-dev/%E4%BD%BF%E7%94%A8-python-google-cloud-platform-line-bot-%E8%87%AA%E5%8B%95%E5%9F%B7%E8%A1%8C%E4%BE%8B%E8%A1%8C%E7%91%A3%E4%BA%8B-70a1409b149a)
    - 可用的參考文章！
- [Cloud Functions:Using Environment Variables](https://cloud.google.com/functions/docs/configuring/env-var?authuser=1&_ga=2.209523350.-547778327.1636687995&_gac=1.258971128.1641968912.Cj0KCQiA8vSOBhCkARIsAGdp6RQQKk35zR8qbNRlel00IkmMICgWVRj46vuxvm-3-3vtLAWbIiPWuQwaAr8TEALw_wcB)
    - 關於 Cloud Functions 的環境變數
- [Setting environment variables in Google Colab](https://newbedev.com/setting-environment-variables-in-google-colab)
    - Python 環境變數的引用方法
- [Python: Date and Time](https://www.w3resource.com/python/python-date-and-time.php)
- [using now() to get current time](https://www.geeksforgeeks.org/get-current-date-using-python/)
- [How to get current date and time in Python?](https://www.programiz.com/python-programming/datetime/current-datetime)
    - 久久用一次時間判斷，查一下XD
    - 因為是自己在用的小功能，不用去管時區或者更五花八門的設定，只用了最單純的 now()
- [[Flask 教學] LINE-Bot GCP 部署(Docker+Flask+Nginx)]()
    - 沒有用到，但可以看看，server 版的 Python LINE Bot
- [PyLadies 活動：Python入門(週末密集充實版)](https://marsw.github.io/Python-Tutorial/07_v2_applications.slides.html#/2)
    - 基本的Line API 使用
- [PyLadies 活動： Line Bot 教學工作坊 - part 1 Pyladies Taiwan x 女人迷](https://tw.pyladies.com/~marsw/linebot_workshop_womany_01.slides.html#/6)
    - 親切教學
- [PyLadies 活動：：Line Bot 教學工作坊 - part 2 Pyladies Taiwan x 女人迷](https://tw.pyladies.com/~marsw/linebot_workshop_womany_02.slides.html#/1)
    - 使用 Python Line module 的範例

