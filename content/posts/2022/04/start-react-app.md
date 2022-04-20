---
title: "新增一個 React 專案"
menuTitle: "Start A React App"
date: 2022-04-20T17:32:35+08:00
publishDate: 2022-04-20T17:32:35+08:00
draft: true
tags: [""]
pre : "<b>[] </b>"
---

# 注意事項
- react.js & next.js 是同源的專案，react 是最輕巧的基本款。
- 最基本的 react app 有成功建立的話，代表基本環境的設定都沒出錯。
- npx 指令要在 npm 5.2 以上的版本才有
- `npx create-react-app my-app` 這個指令也會要求 node 版本，此次我升到 v16.14.2
    - 如何升級 node 版本
        - 強制清除任何版本鎖定因素： `sudo npm cache clean -f`
        - npm 在全域安裝 node： `sudo npm install -g n`
        - 取得特定版本的 node 
            - 穩定版 `sudo n stable`
            - 最新版 `sudo n latest`
    - 確認自身的 node 版本
        - `node --version`

# 運行 react app
## 在喜歡的目錄下執行 create 指令
- 移動到使用者的 project > react 目錄中： `cd ~/project/react/`
- 執行建立 app 的指令(app 名稱為「my-app」，可任意更換)： `npx create-react-app my-app`
- 移動到 app 目錄中： `cd my-app`
- 啟動 react app： `npm start`
- 在指定的 port (預設是3000)上可以看到啟動後的 app 畫面

## 參考資料
- [react 官網](https://create-react-app.dev/docs/getting-started)
- [How can I update my nodeJS to the latest version?](https://askubuntu.com/questions/426750/how-can-i-update-my-nodejs-to-the-latest-version)
    - 如題，更新 node 的指令
- [Upgrading Node.js to latest version](https://stackoverflow.com/questions/10075990/upgrading-node-js-to-latest-version)
    - 如題，更新 node 的指令

- [Node.js Port 3000 already in use but it actually isn't?](https://stackoverflow.com/questions/39322089/node-js-port-3000-already-in-use-but-it-actually-isnt)
    - 強制關閉 node 服務時如果導致預設 port 未成功釋出，可以強制釋出 port
    - `npx kill-port 3000`
- [How does NPM exit or close after NPM run dev is turned on?](https://developpaper.com/question/how-does-npm-exit-or-close-after-npm-run-dev-is-turned-on/)
    - CTRL + D Ctrl + C is not good, or will the port occupy
    - CTRL + Z 也會導致 port 無法成功釋放