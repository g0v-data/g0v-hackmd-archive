---
title: "走橋流產品企畫術"
tags: hackpad
---

# 走橋流產品企畫術

> [點此觀看原始內容](https://g0v.hackpad.tw/EkSC4a4fgkC)

如何以邊走邊橋 (walk-around) 的方式在 g0v 規劃軟體專案

### walk-around step by step


```
step 1 想像第一眼要給 user 看到什麼？於是畫了首頁的 wireframe
step 2 但是從首頁按鈕點進去內頁以後要幹嘛呢？此時腦袋就會開始一片空白
step 3 於是只好乖乖畫流程圖或者寫 user story，邊畫邊想使用者會先這樣、然後會那樣…
step 4 畫了一兩幅流程圖，突然覺得自己看到一束光
step 5 於是又回到 wireframe，把流程圖裡的功能變成按鈕跟頁面區塊塞進來
step 6 等流程圖裡有的功能都塞進 wireframe 以後，又不知道接下來要幹嘛了
step 7 於是又回去畫流程圖
step 8 反覆幾次以後，有天突然覺得很煩，整件事情不就這樣而已嗎我幹嘛搞那麼久咧？
step 9 於是開了 repo 不管三七二十一直接兜 html 跟 css
step 10 兜完 html 跟 css 以後，因為沒資料於是又卡住
step 11 於是開始弄資料，比較沒種的手刻假 json，比較有種的直接幹 api 出來
wireframe ←→ flow chart / user story
    ↓
html mockup
    ↓
data / api

```
註：
- 如果在 step 4 跟 step 5 之間卡住，通常代表腦內的 ui library 沒建好，需要一邊思考自己想要的功能，一邊翻閱 [semantic ui](http://semantic-ui.com/) 、[jquery ui](http://jqueryui.com/demos/) 、[android design guide](https://developer.android.com/design/patterns/index.html) 、[apple human interface guidelines](https://developer.apple.com/library/ios/documentation/userexperience/conceptual/mobilehig/Anatomy.html#//apple_ref/doc/uid/TP40006556-CH24-SW1)  的 ui component 範例，尋找可以套用到這個功能上的元件，每次找到，就會在腦內建立一個功能-元件連結。幾次以後腦內的 ui library 會漸漸成形，開始不需要看範例就能想像什麼功能要用哪個 ui component。
- 如果在 step 7 跟 step 8 之間卡住，通常代表專案規模太大，需要出動次元斬將專案切割成幾個不同的模組。

### wireframe / flow chart tools


#### 手繪

- windows journal
- linux xournal
#### 拉框

- moqups
- libreoffice draw
- google docs drawing

### user story format


[justin style](https://g0v.hackpad.tw/g0v.tw-User-Story-style-lDKb0dKIdJR)
[kktix style](https://g0v.hackpad.tw/User-Story-kktix-style-JouO9fcJvnN)
[socialtext style](https://g0v.hackpad.tw/User-Story-Socialtext-Style-mvxkbtlXlDf)
freestyle：只有 socialtext style 的 nested checklist，使用者即自己的狗食適用



