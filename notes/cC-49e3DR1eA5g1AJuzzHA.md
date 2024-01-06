---
title: "動民主家族土砲區 - 整體開發方向"
tags: hackpad
---

> [點此觀看原始內容](https://g0v.hackpad.tw/CqldbNZaFhM)


### 目前計畫

1.  凡是需要持續參與的公民行動，都替它做一個對應的服務
    - 找零感可參考 [目前已發想的服務](http://hack.g0v.tw/don-democracy/iBRhXaRlfZh) ，想到新的歡迎繼續在裡面補完
2.  每個服務提供某一個統一格式的 api
    - 一個是給時間軸用的
    - 另一個是給列表用的
3.  另寫一個服務接收 api，把所有其他服務串起來，變成公民臉書
    - [公民臉書示意圖](http://g0v.github.io/don-republic/public/)

### 介面藍圖

- 每個獨立服務各自用自己喜歡的 UI
- 如果對 UI 沒有想法，就用公民臉書的通用 UI
- 公民臉書通用 UI 說明
    - nav bar 的用途類似 google 的那條，需要時也可以做成 tabzilla 那種可以收起來的
        - 左上角可回到公民臉書首頁
        - 右上角可登入、設定
        - 中間可連到各服務自己的首頁（議題、提案、專案、公聽、記者會、真度計、……等，預計會跟 google apps 一樣一直擴充）
    - 公民臉書首頁
        - 沒有 header 區塊
        - 左邊有類 facebook 的 sidebar，sidebar 內容由使用者自訂釘選
            - sidebar 加 navbar，整個畫面的導覽邏輯是「上面是系統全域的，左邊是我自訂的」
        - 右邊內容區域是對應的 timeline / stream，顯示從各服務 api 抓進來的內容
        - 在公民臉書內，sidebar 就等於 navbar，瀏覽過程中基本上一直都會在，只有在點進去最底層單一的 entry 中的時候才沒有 sidebar。（layout 保持穩定，不要像 facebook 一樣，sidebar 一下出現一下消失，明明看起來是同一層的東西點進去卻像跑到另一個網站… >_<）
    - 公民臉書底下各服務首頁
        - 有 header 區塊以資區別，讓人知道現在不是在首頁喔，是在某個特定服務頁
        -

