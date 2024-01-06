---
tags: hackathon, 提案, UX
---

# Google Meet 作為簡報投影 destination

## Why
- 上次成果報告的時候自己當了一次主持人，發現用講台電腦流程上很卡
    - 到 Google Sheet 提案列表滑到後面（而且縮放比例很大，所以要難操作XD）
    - 找到簡報連結，點開，打開之後要跑一陣子，又要點「全螢幕顯示」按鈕
    - 換下一個人的時候，要關掉 tab，再回到提案列表找下一個簡報連結，重複到最開始的狀況
- 以上這些操作為了避免 presenter 不熟悉電腦操作，主持人操作比較保險，但理論上要串場的主持人此時就無法好好串場QQ 而且這個操作浪費蠻多時間，如果講者自己不熟悉切換也非常容易 fail
- 但又不能 fallback 到接 HDMI 或 3.5 音源線，因為不同設備可能會有設備問題，加上切換 OS 的音源輸出或 screen mirror settings 更浪費時間，所以當初才用講台電腦作為顯示的 destination
- 還有辦法優化換場方式嗎？

## Solution
- 去 OpenAI 開會發現一個很聰明的方式，他們會讓投影機直接輸出 Google Meet 通話
- 投影簡報的講者不用 HDMI 拔來拔去，只要直接用筆電分享畫面到 Google Meet 通話就好，流程上順非常多
- 就算需要輸出音訊，只要用在加入通話前選「Present Now」按鈕選擇 Chrome 分頁標籤就可以順利分享音訊
    - Paul 已經跟任翔雙邊測試過了，PC and Mac 都 work

## Benefits
- 換場流程就是順
- 演講者可以直接用自己的裝置，操作熟悉
- 直播可以直接透過 Google Meet 畫面轉播超清楚的投影片畫面
- 中研院的無線網路蠻穩的，講台電腦印象中也有接實體網路線？

## How does it work
### To projector
- 講台電腦專門連接投影機，登入開 google meet
- 用 chromium based browser 可能比較穩定
- 記得開該次 Google Meet 管理權限給主持人自己的 Google 帳號
- 需將預設加入會議室的所有音訊和視訊輸入 disable，只留講者有權限

### To presenter
- 主持人要把 Google Meet 連結用 Slack 傳給演講者，讓他可以直接用自己的裝置進 Google meet 聊天室
    - 或藏在提案列表裡

####  若需要分享音訊有三點限制
- 只能用 chromium based browser 才能分享音訊
- 只能點選「present now」而不是「companion mode」（華語好像叫做夥伴模式？）
- 只有分享分頁才能分享音訊
- 分享整個 screen 或單個 app 都不行
    - 如果要分享 app 的聲音，只能拿麥克風督

## Requirements 
- 有無限制通話時數的 Google 帳號來開 Meet 通話（其實超過一小時的帳號就可以啦）

## fallback
- 拉 HDMI 和音源線，主持人還是要在舞台旁待命，如果 google meet 爆掉或網路斷線可以直接把本來連接投影機的講台電腦 HDMI 拉到講者 device

## potential downside
- 如果需要透過 chromium browser tab 以外的程式放聲音，只能緊急接 3.5 mm headphone jack 或拿麥克風督筆電喇叭
- 但預錄影片還是得用講台電腦播QQ
- 如果演講者沒有自備筆電，只能繼續用講台電腦操作

## trivia
- （optional）或許可以直接用 Google TV or chromecast 裝置
- 是不是應該要在提案列表上新增一個欄位問有沒有需要播放音訊？