---
title: 2020/04/05 LINEBot 市容幫手｜8th 小聚會（線上）6
tags: LINE, libot, 里長, 市容幫手
description: 用 LINE BOT 來幫助市民、里長與公務員。
---

## 2020 年 4 月 5 日 LINEbot 市容幫手｜8th 小聚會（線上）


### 討論事項

1. Hello Taipei 的 API 已取得，估計開發時程
2. 給公民委員會的提案簡報

### 會議記錄

#### 公民委員會的提案

小班：加上與 Hello Taiepi 使用的比較？
班班：希望小班能提供一些 work item 放在簡報上
小班：協助訪談需求這一段可以放上去，但需要真的有人願意去找里長

TMONK：疫情關係，是否去訪談里長是一個困擾？
班班：目前應該重點不會放在我們這個專案上
班班：里長訪談希望是民政局、資訊局那邊去做，
TMONK：我有時間的話可以去做訪談，但不確定疫情影響是否會阻礙這件事？
班班：而且現在問，方向是否會有點偏重防疫？
TMONK：是否要詢問民政局、資訊局關於疫情會不會影響到這個專案的進行。

班班：如果資訊局長提出要擴充功能，例如里長專用的 LINEBOT（疫情相關功能）等等，我們團隊是否可以接受？
JAQQ：我們可以就現有的功能去碰里長，等收取到回饋之後我們再去慢慢擴張我們的服務內容比較好。
MARS：有上述的證據證明使用者的需求之後再擴寫功能，會比較容易涵蓋 80% 使用者的需求。



### 結論：
1. API 已取得，JAQQ 跟 Mars 後續有問題交由班班轉達資訊局。
2. 我們服務建議放在 docker 裡面，比較不會因為雲端服務的改變而無法使用服務
3. 我們的服務是類料 Web hooker 的型式，但會需要存資料庫把 line id 對應到案件的編號
4. 資料庫的部份建議看一下 heroku 的資料庫功能
5. 4/8 號晚上 20:00 ，請 JAQQ 說明程式碼給 Mars 與 Tmonk

#### 開會前的功能擴寫的討論
- 用里長的 LINE ID 對應到里長的個人資料
- 上述功能因為要 DEMO 的關係，怕在測試的時候無法做認證所以先不要

#### 需要問資訊局的事
1. 需要跟資訊局取得測試用的 IP 以及測試用 KEY
2. API 中的企業指的是什麼？
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_f232db161492d174bd02f5d578ad3df7)
3. 案件類別代碼只有這些嗎？
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_7f95550546654336ac9df18998ef97fa)

※ 小記一下目前里伯對應的 Form 型態：
* 路燈故障 -> Form 1 ; TYPEA-AC0401
* 公園樹木 -> Form 1 ; TYPEA-AC0402
* 道路坑洞 -> Form 1 ; TYPEA-AC0202
* 交通設施 -> Form 1 ; TYPEA-AC0501
OR -> Form 1 ; TYPEA-AC0502
OR -> Form 1 ; TYPEA-AC0511
* 環境清潔 -> Form 1 ; TYPEA-AC0102
 OR -> Form 8 ; TYPEA-AC0101
 OR -> Form 1 ; TYPEA-AC0213








