---
title: "Musicxml 格式初步理解"
menuTitle: "Basic about musicxml"
date: 2022-01-03T11:24:00+08:00
publishDate: 2022-01-03T11:24:00+08:00
draft: false
tags: ["music","musicxml"]
pre : "<b>[製譜之旅] </b>"
---

摘要：
- musicxml 是一種 xml 格式的延伸，主要作用是以人眼可讀、同時網頁可辨識的約定格式來標示譜面資訊
- 雖然如上宣稱，但因為實際的譜面資訊多，約定格式組合之後不易讀，所以還是需要依靠軟體轉換為五線譜或其他常用譜面
- 好處是能夠用文字文本的形式儲存音樂，相較於 MIDI 格式，能保留較齊全的演奏指示

疑問：
- 似乎要跟 Lilypond 所採用 ABC記譜法(ABC notion) 取得平衡點，盡可能用簡潔文字紀錄可以跨平台呈現的譜面？

我的需求：
- 用文本儲存音樂資訊，可任意轉換為五線譜與簡譜
    - 用文本儲存音樂資訊，可任意轉換為五線譜
        - musicxml + musescore 已可達成雙向轉換的功能
    - 用文本儲存音樂資訊，可任意轉換為簡譜
        - TODO 

## 參考資料
- [Wiki:ABC記譜法](https://zh.wikipedia.org/zh-tw/ABC%E8%AE%B0%E8%B0%B1%E6%B3%95)
- [Wiki:MusicXML](https://zh.wikipedia.org/zh-tw/MusicXML)
一個中音 C 在 MusicXML 要這樣記才行(C大調，G譜號，4/4拍，包含一個中央C全音符)
```xml=
<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<!DOCTYPE score-partwise PUBLIC
    "-//Recordare//DTD MusicXML 3.1 Partwise//EN"
    "http://www.musicxml.org/dtds/partwise.dtd">
<score-partwise version="3.1">
  <part-list>
    <score-part id="P1">
      <part-name>Music</part-name>
    </score-part>
  </part-list>
  <part id="P1">
    <measure number="1">
      <attributes>
        <divisions>1</divisions>
        <key>
          <fifths>0</fifths>
        </key>
        <time>
          <beats>4</beats>
          <beat-type>4</beat-type>
        </time>
        <clef>
          <sign>G</sign>
          <line>2</line>
        </clef>
      </attributes>
      <note>
        <pitch>
          <step>C</step>
          <octave>4</octave>
        </pitch>
        <duration>4</duration>
        <type>whole</type>
      </note>
    </measure>
  </part>
</score-partwise>
```
- [Magenta魔改记-2：数据格式与数据集](https://zhuanlan.zhihu.com/p/49539387)
    - 解說 MusicXML 格式
- [了解MusicXML](https://www.himachi.cn/2018/10/18/music-xml.html)
    - 詳細說明了 MusicXML 的背景觀念
- [宅學習: MusicXML](https://sls.weco.net/node/9182)
- [w3c 的musicxml文件](https://www.w3.org/2017/12/musicxml31/)