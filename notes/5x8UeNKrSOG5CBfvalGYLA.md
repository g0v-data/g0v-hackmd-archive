---
title: 5/16 設計夜車松
tags: COVID-19
---
# 5/16 設計夜車松
至少讓60%的用戶使用才能發揮效果

## 該做的事情
- 先知道爲什麼那些人不願意使用

### 已知UX問題
- 點選“上傳確診者數據”跳出警告彈窗（嚇死人） 
- ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_84ff8ad1b17303dfd43662239f68562d.jpg =50%x50%)
- ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8f785f25725691b0b2f43570deab9943.jpg =50%x50%)

- 文案太長，太不直覺（修改Wording） 
- ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_94025fb7a1458da5e041351c12bd0f66.jpg =50%x50%)
- ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f9ff001c61902f3fbf0e1f922acce3c6.jpg =50%x50%)

### 功能開發
- 下載就送防疫險
- 可以讓使用者同步當前的防疫資訊
    - 衛福部（畫面小卡）
        - 打開藍牙才能看
    - Brief Update
        - 是否會與 Line 功能重疊？
    - 足跡地圖
        - [疑問]法規上是否允許告訴安裝者，目前已比對過哪些案例？資料庫內已有哪些案例？
        - 參考民間社群建置的足跡地圖
            - 收錄中央流行疫情指揮中心公告的確診者足跡、或是政府證實過的足跡 https://bit.ly/2QpgaY6
            - 台灣 COVID-19 案例活動史共筆 https://bit.ly/2QnxzQU
            - 提供民眾可以自行「趨吉避凶」的工具
                 - 行動護身符？
- 記者會Slido功能
    - 給使用者一個魔法棒！！！！！
    - 讓觀眾參與現場問答的部分，有實際的參與感與臨場感！
    - 展露民眾的疑惑，撫慰民心！ 
- 官方實聯制平台


## HMW

### About data

- 減少誤判率，例如不要去追蹤正確 PPE 的第一線人員？
    - 其實關掉藍牙就可以實行這件事，或許沒必要讓這件事變得更簡單？
- 成就系統：增加一個 badge，邀請好友可以增加 badge？

### Before install

- 提升年長者的安裝率
    - 用圖：長輩圖、手寫字、粉筆字，附上 QR Code
    - 對長輩宣傳的教戰手冊：長輩可能問的問題、技術上的問題（資料疑慮？）、用名片的比喻
    - 對年輕人的部份
- 提升用戶對產品的信任度


### Home

- 參考發票存摺，平常可以做為實名制表單工具。每日累積點數（如待在家？），甚至做到點數換物資？
- 整合實聯制與 App 的功能
- 增加定期更新的確診地圖
    - 能否結合類似 Mymap 的功能，來繪製確診足跡地圖？
    - 技術面上不可行：這個 App 背後只記錄「接觸」，而不牽涉定位。
- 列出常見 FAQ
    - 關於 App 本身的 FAQ：我的資料存在哪裡、使用上的問題
    - 其實 CDC 自己有寫一份 [FAQ](https://www.cdc.gov.tw/File/Get/FtLeh9EYUEgtpxZ8acAZUA)，不知道為什麼沒有放在 App 上？
    - 利用 Hackmd 或者 Notion 等功能完整的服務來降低額外開發網頁的成本。