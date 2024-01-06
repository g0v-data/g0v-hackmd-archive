---
title: Rentea 第 3 次小聚
tags: Rentea
---
# Rentea 第 3 次小聚
- 時間： 2019-11-26 (二) 19:00 - 21:00
- 地點： [NPO Hub](https://g0v.hackmd.io/BNHyH7ESSxSlu12BV2U9TQ)，四樓會議室（捷運中正紀念堂步行 7 分鐘）
  - [台北市中正區重慶南路三段 2 號](https://goo.gl/maps/LAXhWdwUAXV3aUHv6) 
  - 場地備有飲水機，請自備杯子水壺
  - 上樓須門禁，請先到一樓內側按電鈴，或在 rentea@slack 找人開門 ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_f40e9eb6c5c7368d9a731072069ff930)
- 專案資訊：
   - [Hackfoldr](https://beta.hackfoldr.org/rentea) / [Slack](https://g0v-tw.slack.com/messages/CJTBP7YRK/details/)
   - [Figma Wireframe](https://www.figma.com/file/Z0Wsc63DYpXLouSC7vvpw5aR/rental?node-id=0%3A1)
   - [程式開發指南](https://g0v.hackmd.io/jg_TRTEbRxyV-osQptSqwQ) / [爬蟲設計](https://g0v.hackmd.io/Bv_1JeHoT1O8gIjFBEJROg?view#%E8%A8%8E%E8%AB%96%E7%B4%80%E9%8C%84%E3%80%81%E7%B5%90%E8%AB%96%E3%80%81%E5%BE%85%E4%BD%9C) / [資料庫設計](https://g0v.hackmd.io/BFd56MJAQqu242x_oqYP2w)
   - 螢幕分享區： https://meet.jit.si/rentea


## 參加者打卡區

想要參加的人請先在這裡打卡，方便確定人數，也記得寫一下想來作什麼，可以是開發東西、學程式、幫忙紀錄，或是任何想做的事情都可以～

- ddio: 
   - 真的要發表[爬蟲參數實驗](https://github.com/rentea-tw/rentea-crawler/issues/4)成果，會寫在[這篇 hackmd](https://g0v.hackmd.io/kAxJ9UdKSIu5sTxIp-r_Nw) XD
   - 聊聊最近的[豬豬又輸一次事件](https://g0v-tw.slack.com/archives/CJTBP7YRK/p1574682937002300)，想想與初衷相容的的方向，例如大平台化、開放資料、[租屋條件推薦](https://hackmd.io/ug_xoJLESuydr7HwOywxxA)
- Steven: 將Sentry 增加到Scrapy上面，並且連續開伺服器幾天看能不能收到錯誤
- Jerry: 第一次參加XD，先聽聽看、聊聊看，可能會來寫Mobile App
- 星翰：spider測試
- York:補進度
:::info
<i class="fa fa-home fa-lg fa-fw"></i> [回到 Hackfoldr](https://beta.hackfoldr.org/rentea/https%253A%252F%252Fhackmd.io%252Fs%252FSJbOIFHpE)
:::
## 現場小記

聊聊豬豬事件

### 被告的經驗，有因為作開源專案而被告的準備嗎？

- 拘役 60 天以下是單人房，可以帶筆墨紙硯，每天定時運動
- 但公平交易法是罰錢
- 不一定排斥被告，也代表被肯定（？）

### 可能的方向 

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_3f7bf8cf1bc5ac7ced62518a93e76558)

1. 維持同市場（租屋搜尋服務），增加公益性，製造社會壓力

   - 通用的租屋平台，包含崔媽媽、各大租屋網站、其他小眾網站，例如品牌公寓、留學生租屋平台
   - 找崔媽媽作更好用的租屋平台
      - 就要討論和 ngo 合作的模式（[參考資料](https://g0v.hackmd.io/HooZPg0KSN25KcmkgRPB4A)）
      - 崔媽媽已經有租屋平台了
   - 改善找屋的使用體驗（Rentea 既有目標）
   - 開放使用資料，促進市場透明度與效率（Rentea 既有目標）
2. 不做租屋搜尋服務，但也解決某些租屋市場的不合理、或增進市場效率
   1. `點子` 市價查詢網站，使用者下條件，網站根據歷史資料，提供租金分佈、熱門程度資訊，協助了解市場定價
   2. `點子` 民眾直接給定價、競標，反應找屋者可接受的條件與價格
   3. `點子` 條件修改機器人，使用者下條件 + 預計租金後，網站根據歷史資料，提供 N 種「放寬 xx 條件」、「少掉某些設施」後，就能達到目標的方法，幫助找屋者了解市場的選項
   4. `點子` 讓使用者標註看到的物件為：價格可接受、不可接受、不確定，當作分類器的訓練資料，可以當作開放資料集，也可訓練好之後當作分類機器人
      - 可能會有負面效果，例如可解釋性差，產生無法負責的評價
   5. 以上點子都只是協助，要找到目前可出租的物件，都還是要去租屋網站搜尋
      - 是否會影響刊登者刊登廣告的意願？
      - 要先考慮是否是同一個市場，才需要考慮有沒有用不公平的方式 && 造成競爭

### 小結

1. 專案方向待決定
   - 可以維持繼續作租屋搜尋服務，但需要增加更多公益性、提昇效率，而非單純呈現
   - 也可以在滿足「解決租屋者的租屋困難」的目標下，轉作其他題目
   - 歡迎提自己想要作什麼，也可參考相關社群或議題
2. 相關社群或議題
   - 週四會聊 [NGO 與開源組織](https://www.facebook.com/events/2844780068907399/)，[會前資訊](https://g0v.hackmd.io/HooZPg0KSN25KcmkgRPB4A)
   - 對爬蟲有興趣，可參考 g0v slack #disinfo 
3. 12 月小聚暫停，但有人想提議下一步，或想接下去作的話，就依然繼續


