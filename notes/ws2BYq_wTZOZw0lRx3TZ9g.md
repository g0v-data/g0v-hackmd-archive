---
title: "立院影城"
tags: hackpad
---

# 立院影城

> [點此觀看原始內容](https://g0v.hackpad.tw/SJpitJIcUjV)


單次會議的全日影片跟片段，用一個含有 waveform 的時間軸(參考 soundcloud, 上面還有小頭像) 表示有聲音的部份，讓 user 可以快速跳到各段，並提供「含時間點的 permalink」

授權方式: MIT
使用資料: api.ly
專案目前狀態: prototype

## 目標與功能（要如何解決）

使 IVOD 可選段落觀看，即時討論。

## 實做細節


協作工具
- github repo：  [http://github.com/g0v/ly.g0v.tw](http://github.com/g0v/ly.g0v.tw)

TODO:
- [ ] web front-end
    - [ ] 會議選擇 widget ( chooser 應該可以稍微設計一下成為一個可重用的 widget... 預設 dropdown 顯示目前的會議種類（同委員會）前後幾次... 然後選的時候旁邊有按鈕可以找別種會議, 或者按照日期查詢... )  [g0v/ly.g0v.tw#22](https://github.com/g0v/ly.g0v.tw/issues/22)
    - [ ] 單次會議會有多天，需要呈現多個 waveform  [g0v/ly.g0v.tw#23](https://github.com/g0v/ly.g0v.tw/issues/23)
    - [ ] hover 小頭顯示委員資訊 (+中型 avatar?)  [g0v/ly.g0v.tw#24](https://github.com/g0v/ly.g0v.tw/issues/24)
    - [ ] x 軸顯示時間、日期  [g0v/ly.g0v.tw#25](https://github.com/g0v/ly.g0v.tw/issues/25)
    - [ ] 當 youtube 在播的時候有個紅 bar 在跑, 表示目前位置  [g0v/ly.g0v.tw#26](https://github.com/g0v/ly.g0v.tw/issues/26)
    - [ ] 縮放 waveform timeline ? 如 google viz api 那種 timeline, scrollbar + selected range  [g0v/ly.g0v.tw#27](https://github.com/g0v/ly.g0v.tw/issues/27)
    - [ ] 含 date/timecode 的 permalink  [g0v/ly.g0v.tw#28](https://github.com/g0v/ly.g0v.tw/issues/28)
    - [ ] 點到委員 clip 範圍, 切換至單 clip HQ video, 結束後切回全日 clip or next clip  [g0v/ly.g0v.tw#29](https://github.com/g0v/ly.g0v.tw/issues/29)
- [ ] web back-end
    - [ ] 全日影片 waveform (kcwu) (轉 wav 檔 > 2g 會炸掉, 需要用 w64 或拆成小檔處理)  [g0v/api.ly#33](https://github.com/g0v/api.ly/issues/33)
    - [ ] 影片實際開始時間 (first frame timestamp) 校正  [g0v/api.ly#34](https://github.com/g0v/api.ly/issues/34)
    - [ ] data integrity check - 缺資料, 多資料  [g0v/api.ly#35](https://github.com/g0v/api.ly/issues/35)


## 成果展示（規劃文件、雛形/草稿、原型/初稿、正式發佈/完稿）


[http://ly.g0v.tw/sittings/08-04-YS-06/video](http://ly.g0v.tw/sittings/08-04-YS-06/video)

## 開發者

clkao
walkingice
tkirby
alicewei

