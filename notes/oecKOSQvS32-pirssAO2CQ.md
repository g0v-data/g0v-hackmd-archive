
# SpotDiff GA 後台說明

## Data Studio（GA 資料整理過後的 dashboard）
一般看這個就好
Data Studio 連結：https://datastudio.google.com/reporting/3210d668-89af-4b9a-9756-cdcabd69c21f/page/hxlrC


---


## GA（想看原始資料）
GA 連結：https://analytics.google.com/analytics/web/#/p312956266/reports/intelligenthome?params=_u..nav%3Dmaui&collectionId=life-cycle

#### 網頁標題
`${title}="大家來找廠 | 動手指拆工廠 | "`
https://spot.disfactory.tw/#/ `${title}首頁`
https://spot.disfactory.tw/#/tutorial `${title}教學`
https://spot.disfactory.tw/#/game `${title}辨識`
https://spot.disfactory.tw/#/ending `${title}結束`


#### Event name
開始辨識 - start-game
確認送出 - send-answer
再玩一輪 - play-again
分享 - share
看關於專案 - view-about

#### 從 GA 看來源媒介
![ga4](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6cfa4998c2e964abca1387353d819a6e.png)

---

## GTM（埋事件用的）

GTM 連結：https://tagmanager.google.com/#/container/accounts/6000465837/containers/63750184/workspaces/6

目前 staging, prod 都是用同一個
![gtm](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_91f1d50c9854196974511d7d8ebff572.png)
