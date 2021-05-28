---
title: "想要一個音訊轉簡譜的服務"
menuTitle: "許願池:音訊轉簡譜"
date: 2021-05-05T10:33:34+08:00
publishDate: 2021-05-05T10:33:34+08:00
draft: true
tags: ["wishing well","musical notation"]
pre : "<b>[許願池] </b>"
---

## 目標

輪姐出譜需要額外花時間，希望可以用電腦自動做到，以便大量出譜。

## 想像流程:使用者

```sequence
user->service: upload audio file
Note right of service: service do something
service-->user: numbered musical notation
```

## 服務要如何做？
- 音訊格式很多，但是 MIDI(Musical Instrument Digital Interface) 格式容易跨軟硬體支援，所以最終輸入格式採用 MIDI ?
    - MIDI 轉樂譜應該已有既有套件可用
    - MIDI 2.0 很可能有更多樂曲設定可用，有未來的功能擴充性？
      - [MIDI ORG: Synth and Software's MIDI 2.0 interview](https://www.midi.org/midi-articles/synth-and-software-s-midi-2-0-interview)
      - [MIDI ORG: Tutorial_on_MIDI_and_Music_Synthesis_96-1-4_rc1](https://drive.google.com/file/d/1YKtkVeoR4ZHW4vCSs5oGq3pIKcyKL3Wj/view?usp=sharing)
- 

## 材料收集

- Lilypond 可顯示音符數字
    - [Lilypond numbered musical notation: Numbers as easy note heads](http://lilypond.org/doc/v2.14/Documentation/notation/note-heads)

- 超可愛的，可以學彈琴
    - [pianobooster: 官網](https://www.pianobooster.org/)
    - [pianobooster: source code(C++)](https://github.com/pianobooster/PianoBooster)

- Python packages
    - [list about music](https://wiki.python.org/moin/PythonInMusic)
    - notation package for Python with MIDI file: mingus
        - [midi_file_in](http://bspaans.github.io/python-mingus/doc/wiki/refMingusMidiMidi_file_in.html)
    - python-midi
        - [python-midi](https://github.com/vishnubob/python-midi)

- 頻率對照表
    - [Note names, MIDI numbers and frequencies](https://newt.phys.unsw.edu.au/jw/notes.html)

- MacOS 系列的音訊轉音名套件(用來做Apple App):AudioKit
    - [AudioKit](https://github.com/AudioKit/AudioKit)
    - [應用示範：寫一個吉他調音器 App](https://www.youtube.com/playlist?list=PLUJ4J369lEBunVt8sWAjZ66JgHMCB7FLH)

- 無關但好像很有趣
    - [輕鬆解讀聲音的品質](http://www.p53studio.com/cargocultscience/spel-audio-analysis/)
        - 分析聲音訊號(audio input)
            - 商業版的套裝軟體 Matlab
                - 資料視覺化，可將訊號轉成 2D/3D 圖
            - 開放原始碼軟體 Octave
                - 資料視覺化，可將訊號轉成 2D/3D 圖
            - Python 語言的軟體套件 (PythonInMusic)
                - 音源處理套件
            - Spek
                - 將訊號轉成波形搭配色譜的影像


## 案外案
想要把文字音名轉成頻率數值，作成歌謠班同學們能力值培養歷程的數據化圖表。
明明 wiki 都有對照表了，怎麼可能沒有套件或現成公式可以用！！
大家都在問要如何在 google 相關雲端文件寫樂譜，很少人在意頻率值這件事嗎？
就算頻率這件事還是稍有爭執，但還是可以選一個標準來用用啊～～～ Q_Q
拜託給我個 A4 = 440Hz 啊啊啊！