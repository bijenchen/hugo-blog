---
title: "如何將 MIDI 鍵盤連接至 Musescore2 軟體"
menuTitle: "將 MIDI 鍵盤連接至 Musescore2"
date: 2022-01-02T12:06:21+08:00
publishDate: 2022-01-02T12:06:21+08:00
draft: false
tags: ["music","midi_keyboard","musescore","casiotone","ubuntu"]
pre : "<b>[製譜之旅] </b>"
---
Musescore 版本 2.3.2
環境 Ubuntu 20.04.3 LTS
How to connect the midi keyboard to musescore2(v2.3.2) in ubuntu(20.04.3)

# 以資料傳輸線材連接電腦與 MIDI 裝置
我的 MIDI 裝置是 Casio CT-S300 電子琴，連接方式依照[官網教學](https://web.casio.com/app/zh/play/support/connect.html)，電子琴端使用 Micro-B 的接頭，電腦端用 USB 即可。  
注意，使用 USB 線與轉接頭時要選擇 OTG(On The Go) 類型的線，不能使用純充電用的線喔！如果接頭都對但是接上去沒有訊號，可以檢查一下線材類型～

# 確認系統能夠讀取 MIDI 裝置的訊號
在 ubuntu 裡可以在任一目錄裡輸入指令 `lsusb` 檢查是否有成功讀取外接裝置  
連接前
![](/images/2022/01/music_connect_midi_keyboard_lsusb_before_connction.png)

連接後
![](/images/2022/01/music_connect_midi_keyboard_lsusb_after_connction.png)

# 使用 Musescore2 實時輸入音符
## 在 MIDI 裝置與電腦已連接的情況下，開啟 Musescore2，進入偏好設定的輸入輸出設定
在「編輯(Edit) > 偏好設定(Preferences) > 輸入/輸出(I/O)」當中。偏好設定的位置可能會因為使用的 Musescore 版本而有差異，請找出自己的輸入輸出設定即可，原則上都是放在偏好設定中。
![](/images/2022/01/music_connect_midi_keyboard_musescore_toorbar.png)

## 在輸入輸出設定中，選擇 portAudio 選項，並且找到自己的 MIDI 裝置，儲存後需要重啟 Musescore2
![](/images/2022/01/music_connect_midi_keyboard_musescore_io_portAudio.png)

## 重啟 Musescore2 後，確認開啟了 Musescore2 的 MIDI input 模式後(Toggle 'MIDI input' must be lighted)，在輸入模式中選擇「實時(自動)/ Realtime mode」
![](/images/2022/01/music_connect_midi_keyboard_musescore_toggle_midi_input.png)
![](/images/2022/01/music_connect_midi_keyboard_musescore_note_real_time.png)
此時按下電子琴鍵盤，就可以依照彈奏的音符輸入樂譜囉！


## 參考資料
- [Ubuntu manpages : lsusb](http://manpages.ubuntu.com/manpages/bionic/man8/lsusb.8.html)
  - lsusb 指令
- [musescore 官方教學：MuseScore in Minutes: Lesson 4 - MIDI Keyboard Input](https://youtu.be/IZ1b1aF9lpg)
  - MIDI 裝置讀取設定