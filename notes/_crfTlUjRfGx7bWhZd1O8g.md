---
title: "捐血動員系統"
tags: hackpad
---

# 捐血動員系統

> [點此觀看原始內容](https://g0v.hackpad.tw/yRBt8WsGdvt)

> 歡迎大家集思廣益！
> [name=water s]


## 動機

幾次重大災難總能激起熱心熱血民眾前往捐血，但捐出來的血液有其==保存期限(全血約35天)==問題，且一個人兩次捐血中間==需間隔====二====個月==以上。若短時間大量集中進入捐血中心，可能造成存血在時間與空間上調配不均衡以致浪費的狀況發生。
> 不曉得目前若一般情況下，捐血中心血液的浪費率有多少...
> [name=water s]

徽章清單：（名稱．任務）
    - 新手勇者．捐血次數1次以上
    - 聖者之杖．分離術1次以上
    - 鋼鐵鬥士．500cc 1次以上
    - 永恒之塔．捐血 250cc 達連續4次以上
## 目的

若有一系統可根據即時血庫存量，動態調配、選擇性 (地點、血型、人數) 動員(通知)熱心熱血民眾，在需要的時間點前往捐血。當參與民眾數量能達總捐血人數一定比例以上，應可減少血液浪費。==達到平時儲血於民，有需要時，可正確呼喚出需求的血液。==

## 捐血->檢驗->保存->使用流程

待補...


### 捐血間隔

| 每次捐血量 | 應間隔時間 |
| --- | --- |
| 250 cc | 2個月以上 |
| 500 cc (60kg以上) | 3個月以上 |
| 分離術血小板 | 2周以上 |
男性: 1500cc/year 以內
女性: 1000cc/year 以內
分離術血小板每年以24次為上限
資料來源：[http://www.blood.org.tw/internet/taichung/docDetail.aspx?uid=7493&pid=6949&docid=31084](http://www.blood.org.tw/internet/taichung/docDetail.aspx?uid=7493&pid=6949&docid=31084)

## 需求

###  App Client

- 靜態資訊提供
    - 提供捐血地點相關資訊(地圖、導航)
    - 提供各地血庫即時血量資訊
- 登錄使用者個人資訊
    - 活動區域(地點)
    - 血型
    - 我每次捐多少血 (250/500/不一定)
    - 是否願意接受即時動員？
    - 可直接看到個人捐血報告(需與捐血中心配合)
> 捐血報告有範本嗎？
> [name=Yuren J]

> 捐血完大約一週以內(?) 會收到一份以身分證字號加密的pdf檔案，參考大概是這樣的內容：[https://dl.dropboxusercontent.com/u/10852842/report.png](https://dl.dropboxusercontent.com/u/10852842/report.png)
> [name=water s]

    - 判斷能否捐血
        - 上一次捐血時間 / cc 數
        - 今年已捐血多少 cc
        - 性別
> 為什麼性別有差呢？無論有沒有生理期，似乎都是以捐血前扎針測血紅素為準。
> [name=Johnson L]

> 個人推測是上述所提及的：男性: 1500cc/year 以內、女性: 1000cc/year 以內。
> [name=張家齊]

        - 體重
        - 最近使用藥物/手術情況（捐血中心有各情況捐血間隔參考表）
        - 前夜睡眠是否足 8 小時
        - 是否用過餐（早上捐一定要用過早餐，下午捐一定要用過午餐）

### Server端

- 根據動員情況與效度 分析調整動員方式
- 可以捐 250 / 500 不同 cc 的類型

## 動員流程

某地某血型血庫存量低於警示值 -\> 呼叫n名符合資格(地點、血型、可捐血)民眾 -> 民眾回覆：我最近可以去捐血(1d/3d/5d) -> 根據回覆率%再呼叫適當人數的民眾前往捐血

## 推廣方式

- 遊戲化設計？
> 可以設計 badge system
> [name=Yuren J]

> 血型組隊一起捐
> [name=Moon C]

- 配合捐血單位推廣
- 捐血回饋的鼓勵？
> 當血液被使用的時候有通知，待驗證
> [name=Moon C]

> 捐血的時候會給集點卡，可以換小禮物，不過禮物內容好像不太一定。集點規則寫在集點卡的背面：
> [name=Johnson L]

> ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_f3c6a44eecc36b884e07b4cd901b6eaf)
    
> [name=Johnson L]


> 再來就是，偶爾會有捐血送牛排 5 折 or 電影票的活動。活動當日捐血車就會大排長龍，是拿到號碼牌之後到附近晃個兩小時，回來都還要再等三十分鐘的那種人數。ptt 省錢板 搜尋「捐血」有相關資訊。
> [name=Johnson L]


> 最後，當你捐滿一定次數，會有一張對折的 A4 紙寄到你家，長得像這樣（不知道算不算回饋？ :P）
> [name=Johnson L]

> ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_81f06ccf297cf73e76026778b5048ab8)
    
> [name=Johnson L]


## 其他

- 個人隱私問題？
> 讓使用者自己填的話應該就還好
> [name=Yuren J]


## 實作細節

> 週六 (7/4) 我會先試做一個 mobile web app 的版本，理論上之後只要用 Cordova 包裝起來後用 Alarm API 就可以實作通知的功能，剩下的都可以用一般的 web 實作。
> [name=Yuren J]

> 第一階段可以實作：
> [name=劉宇庭]

> 1\. 各地捐血中心血量資訊
> [name=劉宇庭]

> 2\. 用戶匿名註冊（所屬捐血中心．血型）
> [name=劉宇庭]

> 3\. 當血庫存量偏低時，通知50名符合條件的用戶，每天10am檢查一次，通知過的用戶7日內不再通知（推播GCM/APNS）。
> [name=劉宇庭]

## 國外相關案例

[BLOODBOOK](https://www.youtube.com/watch?v=ZNxSg6GlBn4) (印尼)
## 相關連結

- g0v Log: [http://logbot.g0v.tw/channel/g0v.tw/2015-06-29#22](http://logbot.g0v.tw/channel/g0v.tw/2015-06-29#22)
- BloodtoGive熱血樂捐: [http://bloodtogive.azurewebsites.net/index.php](http://bloodtogive.azurewebsites.net/index.php)
- 血液相關資訊: [http://www.blood.org.tw/Internet/LifeCare40year/docDetail.aspx?uid=7588&pid=7587&docid=34764](http://www.blood.org.tw/Internet/LifeCare40year/docDetail.aspx?uid=7588&pid=7587&docid=34764)

