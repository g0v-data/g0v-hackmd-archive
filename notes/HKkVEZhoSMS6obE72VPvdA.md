---
title: "第貳次基礎建設松"
tags: hackpad
---

# 第貳次基礎建設松

> [點此觀看原始內容](https://g0v.hackpad.tw/nog3i777EOZ)


### 什麼是 g0v 基礎建設松？


g0v 社群由「人、坑、松」組成，如何讓參與者容易串連協作，需要更多好用的工具與平台。繼兩年前第零次基礎建設松後\[1\]，揪松團重啟相關計畫，揪碼農筆農一起長期耕耘，希望透過常態經營基礎建設專案，能讓去中心化的分散式工作更有效能。

報名：[http://g0v-jothon.kktix.cc/events/infrath2n](http://g0v-jothon.kktix.cc/events/infrath2n)
基礎建設 hackfoldr: [http://beta.hackfoldr.org/g0v-infras/](http://beta.hackfoldr.org/g0v-infras/)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_79ea53879d948a2507b8cf6419340ed3)


### 預定流程 2016/7/3 週日


    上午 10:30
    檢視目前關卡、可能的解決方案、加入新點子，以及了解各類別的坑進度

    中午 12:00
    Pizza + **各個小坑**分組，**釐清**流程與前置準備

    下午 16:00
    成果分享

    下午 17:00
    決定下次基礎松 / hangout 的時間


### 提案

- 編輯 awesome g0v (ipa)
    - [https://github.com/g0v/awesome-g0v](https://github.com/g0v/awesome-g0v)
        - 請編輯：[https://hackmd.io/s/HymQrZU8](https://hackmd.io/s/HymQrZU8) 今天結束時會匯入 github
    - 專案整理清單：[project pool ](https://g0v.hackpad.tw/VPnworpE5xi)
- g0v Hub (clkao)
    - crawler:
    - editor+PR: [https://github.com/poga/metadata-editor/](https://github.com/poga/metadata-editor/)
    - display
- g0v base map styles
    - 使用 [https://www.mapbox.com](https://www.mapbox.com)
    - [https://github.com/g0v/mapbox-gl-styles/tree/master/styles](https://github.com/g0v/mapbox-gl-styles/tree/master/styles)
    - Mapbox 遊玩心得：
        - 建議不要自己亂配色，使用預設的 style
            - 特殊配色容易干擾「資料」呈現，使用內建配色綽綽有餘。
            - 使用 mapbox 時先挑選適合專案的 style（light / dark / streets）
            - 將 Propreties 裡面的 text fields 由 {name_en} 改為 {name} 語言就會在地化
        - 將配色精力花在==資料呈現==本身
            - Street Map 適合
                - 資料：與地點「細節」相關、需要找到街道的應用
                - Icon 樣式：主要填色在外框上，內 icon 黑色或白色為主。若外框色與背景相近，則可用框線。
                - Icon 配色：鮮豔色彩，盡量從 Street 內有的顏色去找
            - Light Map 適合
                - Icon 樣式：外框為黑灰白，配色以內 icon 為主。
                - Icon 配色：彩度適中配色，不使用太過螢光或太黯淡之色彩。
            - Dark Map 適合
                - Icon 樣式：外框為黑灰白，或甚至不採用外框，配色以內 icon 為主。
                - Icon 配色：超高彩度、亮度可提高之配色
            - ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_a6d6d4f91651d05be96fde31751a9be9)
            - 未整理之測試 Sketch 檔案： [http://d.pr/f/L5AP](http://d.pr/f/L5AP)
- gov2g0v Guide(小鈺)
    - 開放公務員跳坑
    - ~專用hackpad今天要用hackmd才對~
        - [~https://gov2g0v.hackpad.com~](https://gov2g0v.hackpad.com)
    - [http://beta.hackfoldr.org/1VVq3bLLq6g1rLvzDSgPvbhVPUbXAVp17CVNmjQT8Qt8/https%253A%252F%252Fhackmd.io%252Fp%252FHyazu7LU%2523%252F](http://beta.hackfoldr.org/1VVq3bLLq6g1rLvzDSgPvbhVPUbXAVp17CVNmjQT8Qt8/https%253A%252F%252Fhackmd.io%252Fp%252FHyazu7LU%2523%252F)
    - 規劃另一個坑：g0v2gov Guide，

Planning
- g0v.tw
    - 捐款入口統整
- hack.g0v.tw 優化
-
- hackpad cleanup
- hackpad migration (AceChen)
    - history export (to json format)
    -



## 成果報告小紀錄

- Ronny: g0v.json editor [https://ronnywang.github.io/g0vjson-editor/](https://ronnywang.github.io/g0vjson-editor/)
    - 輸入 repo 後有警語
    - g0v json 不符合需求，需要再定義欄位
    - clkao: poga 已經開 PR，這可以接起來嗎？ronny: 需要重刻
- superbil: Hackfoldr iOS 增加兩功能
    - [https://github.com/Superbil/hackfoldr-iOS](https://github.com/Superbil/hackfoldr-iOS)
    - APP 上開 hackfoldr
- 阿端：search engin
    - repo: [https://github.com/g0v/search-hackpad-g0v](https://github.com/g0v/search-hackpad-g0v)
- kirby: g0v project 前台
- even: g0v style mapbox
    - 心得在上（請往上捲）
    - clkao: 秘訣是不是該放在 style guide?
- Jme: g0v issue tracker
    - 上次API好了，這次作前端
    - 先放在自己的repo，之後再搬
- kcliu: 官網自動出現活動 banner
    - [https://github.com/g0v/g0v.tw](https://github.com/g0v/g0v.tw)
- jimyeh (lemonlatte): 一鍵開大松
    - [https://github.com/g0v/OneButton](https://github.com/g0v/OneButton)
    - google doc 自動產生
- Andy: hackpad search engin
    - 變成 json api，有獨立 api 可搜尋，可再接前端
- shelling:
- 小鈺：gov2g0v
    - [http://beta.hackfoldr.org/1VVq3bLLq6g1rLvzDSgPvbhVPUbXAVp17CVNmjQT8Qt8/https%253A%252F%252Fhackmd.io%252Fp%252FHyazu7LU%2523%252F](http://beta.hackfoldr.org/1VVq3bLLq6g1rLvzDSgPvbhVPUbXAVp17CVNmjQT8Qt8/https%253A%252F%252Fhackmd.io%252Fp%252FHyazu7LU%2523%252F)





