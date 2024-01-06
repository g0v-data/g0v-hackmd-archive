---
title: g0v 簡訊實聯
tags: COVID-19, 實聯制, g0v
---
:::info
See also: [1922 簡訊實聯制](https://g0v.hackmd.io/FxudGiM8RSKnpCo4TrMhNg)
<i class="fa fa-home"></i> [g0v 實聯制工具討論紀錄](https://g0v.hackmd.io/@jothon/BJlq5K1tO)
:::

#  g0v 簡訊實聯

1. 操作簡單：掃 QR code > 自動帶出簡訊畫面 > 按下送出 > 接收確認簡訊
2. 速度最快：無需安裝、無需註冊、無需網路
3. 支援容易：智慧型手機可以掃 QR code，非智慧型手機可以手動輸入簡訊內容
4. 保障隱私：僅記錄手機號碼、地點**代碼**、時間，落實「實聯制」而非「實名制」的目標

## Specification

### Send

> 加上個資使用聲明後 QR code bits 比較多，需要比較高的解析度，是否可以省略？ [name=AceChen]
> 如果回傳的回執有個資聲明不知道可不可以⋯⋯但好像太遲了XD [name=RS]

#### QR code format

`SMSTO:[CODE]:[MESSAGE]`

* `[CODE]` = phone number, short code. e.g. `1922`
* `[MESSAGE]` = `[MerchantID]` + `[OPTIONAL]` + `使用聲明`
* `[MerchantID]` = unique 5 digits + 1 check digit
* `[OPTIONAL]` = `delimiter` + party of `N` 需手動輸入
* `delimiter` = ` ` `,` `.` `;` `-` `/` `|` `:` `\n`

###### Example

:::info
`SMSTO:1922:場所代碼：555666 本次實聯簡訊限防疫目的使用`

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5788e868fa284f1362ccbbb03f34f48c.png =200x)
:::

:::info
`SMSTO:1922:555666`

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_47e0a2b9628b02ace097bc1d4ca1061e.png =200x)
:::

#### Text (SMS)

Text `[MESSAGE]` to `[Number]`

###### Example

:::info
手機發簡訊 `555666` 到 `1922`
:::

#### Passive Text (SMS): Optional
:::spoiler
留下手機號碼，由店家/場館發送認證簡訊。可用於候位或入場管制

###### Example

```
請留下您的手機號碼，待有空位時我們會以實聯制簡訊通知您，座位保留十分鐘
```
> 這功能會增加 backend 複雜度和管理權限的問題，可以替代為：使用者確定進入場地後再登記實聯 [name=AceChen]
:::

#### MerchantID 討論

##### 唯一性

MerchantID 必須要在某個接收門號下的命名空間不會重覆，因此若空間使用獨立的接收門號時，MerchantID 可以省略，或是被省略 MerchantID 的訊息預設一個 MerchantID
> 如果是政府機關和電信業者合作的架構下，必須假設接收門號 `[CODE]` 只有一組 e.g. `1922`。`[MerchantID]` 如果 5 碼不夠用的話，另一個方法是店家/場館電話號碼後 6-8 碼 + 2 碼校驗碼，這樣仍保留唯一性，且不超過人類平均短期記憶長度 [name=AceChen]
> 記憶問題原則上不是主要問題，因為不用背下來，不過電話加上校驗碼確實可以，我的想法是如果他的命名空間有成那就可以以全域唯一 (Global Unique) 的方式做，那這樣的話就可以在不需要中央分配管理ID的前提下讓商家自行產生隨機 GUID [name=pichu]
> 
> 記憶長度是考量手動輸入簡訊的時候，從海報上面那串數字轉移到簡訊內容
> 另外，decentralisation 應該是可行但 backend 似乎會複雜很多… [name=AceChen]
> 
> 預留給團體訂位的 `[OPTIONAL]` 似乎會打亂現場流程（見下方「海報及告示範例」），需要 UI/UX 支援。以疫調角度是最好每個人都登記，但仍有家庭帶小孩長輩（無手機）的情況要處理 [name=AceChen]
> 
> 如果是只有四碼的手輸入的ID的話確實很難支援OPTIONAL，也許4碼就是用逗號做分個？ [name=pichu]

##### 匿名性

簡訊機制在2G狀況下有可能被嗅探到。
簡訊內文會在下列設備上留下紀錄：
 * 使用者發送手機
 * 使用者電信商設備
 * 商家電信商設備
 * 商家接收手機

以及中間可能使用的第三方平台，其中在使用者發送手機中訊息可以被使用者自行刪除，但使用者忘記刪除的狀況有可能被作為跟蹤工具所使用。
> 使用者手機內的簡訊可以視為 privacy，也就是只有使用者可以 access，簡訊實聯可能管不到這一塊？ [name=AceChen]

因技術限制， QR Code 所產生的首次進入連結不易隨時間自動變換。若採 nfc 為載體則有機會每次發送不同商家偽ID

但倘若商家願意配合每日張貼新 QR Code，則昨日之商家ID與今日不同，攻擊者無法透過昨日之商家ID推定今日之商家ID，進而降低被追蹤風險。
> 一個比較複雜（也違背初衷）的方法是 QR code 導向 url 然後每次產生不同的簡訊內文再傳回來。但如果要走 url 的話其他方案（見本共筆最後的「其他實聯制系統」）會更適合 [name=AceChen]
> 其實走URL也不是不行，準確來說是 HTTP, HTTP 之後還是可以產生 smsto 的連結的，對使用者來說還是一瞬的使用者體驗 [name=pichu]
> 
> 備註：走 URL 可能會有的問題：
> 1. 需要網路，需要網站，對使用者端有比較高的限制（需可上網）
> 2. 可能會 URL injection/DNS hijacking attack，相較 `SMSTO:` 而言使用者端較難以察覺 [name=AceChen]

##### 偽造輸入

指使用者可能修改簡訊內容偽造輸入的狀況。
> 很難解決，應該可以直接列入 bug... [name=AceChen]
> 
> 在簡訊的發信號碼其實是難以偽造的，但是是對於一般民眾而言，倘若民眾的手機

##### 遠端偽造輸入

指使用者並不在現場但是偽造紀錄造成防疫作業上混亂的狀況，在固定時間內的商家編號資料若被攻擊者的夥伴將資訊傳送給在遠端的夥伴時即可能成立攻擊。

對於此攻擊必須要記錄來源手機號碼，並在疫調時將重要層度分層，把正常使用者與疑似偽造使用者做區隔。
> 目前可能只能在電信端/Server side 偵測和避免 DoS，並要有店家/場館的直接聯絡機制
> e.g. 遭到攻擊時系統發出警告，更換 `[MerchantID]` 同時重新產生新的 QR code，並在一段 buffer time 後 revoke 舊的 `[MerchantID]` [name=AceChen]

##### 可手動輸入

在使用者手機相機故障的狀況下，掃描 QR Code 自動完成可能會有問題，因此需要手動輸入，手動輸入的情況下必須避免同時使用 `I` `l` `1` 等印刷後不容易區分的符號，同時需要將號碼分組，舉例來說 `04332-4431-6654` 這樣的印刷方式人眼讀取上比 `0433244316654` 來得簡單，系統需要在解析MerchantID時自動忽略 `-` 符號。
> 補充：後端需要 parser 各種可能的輸入情境
> e.g. 全形數字, i.e. `１` `２` `３` `－`，各種 delimiter, i.e. 忽略空格 ` ` `　` 以避免 typo
> 也可以利用回傳訊息適當顯示 error/hint
> 另外，在印刷上使用 ` ` 作為區分符號或許可以避免使用者誤解 `-` 為必要輸入字符 e.g. `0433 2443 1665` [name=AceChen]

##### 易記性與防呆設計

基於人類短期記憶的長度約為 $7\pm2$ 位數，考量手動輸入簡訊的必要情況，`[MerchantID]` 盡量不超過 10 位數字 e.g. `5566 5566`

`[MerchantID]` 同時需避免以 `0` 開頭，以防止民眾手誤填反 `[CODE]` 和 `[MerchantID]` 而造成簡訊 recipient 為 `[MerchantID]` 送到真的電話號碼造成困擾

##### 校驗碼 check digit

校驗碼提供第一層的遠端攻擊保護以及防止輸入錯誤，為避免猜測攻擊，校驗碼生成需要加入隨機種子 seed，或者不公開演算法

##### `[MerchantID]` 碰撞

綜合上面各種因素考量，以及隨時更換 `[MerchantID]` 的需求，需要有 database 儲存已經使用過的 `[MerchantID]` 以避免碰撞

---

### Receive

> 有沒有情況是只需要登記不需要確認？ [name=AceChen]
> 場地管理人不想付簡訊費用的情況，像是非營利用的場地，例如公廁？ [name=pichu]

`[REPLY] [MerchantID] [OPTIONAL] [TIMESTAMP]`

* `[REPLY]` = status of registration
* `[MerchantID]` = for customers to check
* `[OPTIONAL]` = optional message
* `[TIMESTAMP]` = for record


###### Example

:::success
Success
`實聯制登記成功\n555666\nYYYY-MM-DDTHH:mm\n[關懷文字]\nContact-information registration completed: location 555666.\nFlatten the curve!`
:::

:::danger
Fail
`實聯制登記失敗\n查無此地點\nYYYY-MM-DDTHH:mm\nContact-information registration failed: location not found`
:::

:::warning
Alert
`實聯制登記成功\n555666\n此地點可能人數較多，請保持社交距離\nYYYY-MM-DDTHH:mm\nContact-information registration completed: location 555666\nPlease practicing social distancing`
:::

:::danger
Fail
`實聯制登記失敗\n輸入格式錯誤\nYYYY-MM-DDTHH:mm\nContact-information registration failed: wrong format`
:::

---

## 實作及架構

### 以政府與電信業者合作為例：「[1922 簡訊實聯制](https://g0v.hackmd.io/FxudGiM8RSKnpCo4TrMhNg)」

```sequence
Note over User: [NUMBER]
User->Telecom: SMSTO:[CODE]:[MerchantID]
Note over CDC: [MerchantID]
Telecom->CDC: verify [MerchantID]
CDC-->Telecom: valid
Telecom-->User: [REPLY][MerchantID][TIMESTAMP]
Note over Telecom: Save [[NUMBER],[MerchantID],[TIMESTAMP]]
CDC->Telecom: [NUMBER] of positive cases
Telecom-->CDC: [[MerchantID],[TIMESTAMP]]
CDC->Telecom: [MerchantID],[TIMESTAMP]
Telecom-->CDC: [[NUMBER]] of close contacts
CDC->User: Contact tracing
```

* 電信業者只有 `[NUMBER]` `[MerchantID]` `[TIMESTAMP]` 沒有對應店家/場館資訊
* 電信業者依照台灣電子圍籬延伸的法律，於 28 天後刪除紀錄
* 店家/場館只能查看使用者收到的確認簡訊，沒有任何個人資訊
* CDC 只有 `[MerchantID]` 對應的店家/場館資訊，除非疫調，沒有任何個人資訊

### 以第三方簡訊接收業者為例 (Twilio)

```sequence
Note over User: [NUMBER]
User->Telecom: SMSTO:[CODE]:[MerchantID]
Telecom->Twilio: SMSTO:[CODE]:[MerchantID]
Note over Twilio: Save [[NUMBER],[MESSAGECONTENT],[TIMESTAMP]]
Twilio->Merchant: [[NUMBER]]
Note over Merchant: Save [[MerchantID], [NUMBER], [TIMESTAMP]]
Merchant-->Twilio: [REPLY][MerchantID][TIMESTAMP]
Twilio-->Telecom: [REPLY][MerchantID][TIMESTAMP]
Telecom-->User: [REPLY][MerchantID][TIMESTAMP]

CDC->Merchant: [NUMBER] of positive cases
Merchant-->CDC: [[MerchantID],[TIMESTAMP]]
CDC->Merchant: [MerchantID],[TIMESTAMP]
Merchant-->CDC: [[NUMBER]] of close contacts
CDC->User: Contact tracing
```

* 使用者資訊保存責任在場地負責人
* 使用第三方服務可能產生費用（每通約新台幣3元以下)
* 第一封訊息由顧客支付，第二封訊息由商家支付 
* 第三方服務會進行訊息儲存，增加備份點
* 合理利用時間經過後要手動刪除第三方服務上歷史紀錄
* 商家本身可以看到訊息紀錄，可彙整為 CSV
* 回應訊息可由商家自定
* 系統較為分散，流量集中點在 Twilio，商家伺服器可以分別實作
* 目前已有開源示範程式碼 https://github.com/PichuChen/QRSMS

### 以 Android App 為例

```sequence
Note over User: [NUMBER]
User->Telecom: SMSTO:[CODE]:[MerchantID]
Telecom->Merchant: SMSTO:[CODE]:[MerchantID][MESSAGECONTENT],[TIMESTAMP]]
Note over Merchant: Save [[MerchantID], [NUMBER], [TIMESTAMP]]
Merchant-->Telecom: [REPLY][MerchantID][TIMESTAMP]
Telecom-->User: [REPLY][MerchantID][TIMESTAMP]

CDC->Merchant: [NUMBER] of positive cases
Merchant-->CDC: [[MerchantID],[TIMESTAMP]]
CDC->Merchant: [MerchantID],[TIMESTAMP]
Merchant-->CDC: [[NUMBER]] of close contacts
CDC->User: Contact tracing
```

* 使用者資訊保存責任在場地負責人的Android手機上
* 場地負責人需要暴露自己電話號碼給顧客
* 沒有第三方服務，和客戶網內互打可能免費
* 第一封訊息由顧客支付，第二封訊息由商家支付 
* 第三方服務會進行訊息儲存，增加備份點
* 合理利用時間經過後要手動刪除第三方服務上歷史紀錄
* 商家本身可以看到訊息紀錄，可彙整為 CSV，可在 Android App 上面看到紀錄，適合小吃店或攤販確認有成功收到
* 紀錄本身較容易彙總匯出
* 回應訊息可由商家自定
* 系統較為分散，沒有星狀單一節點
* PoC 還沒寫

---

#### 3rd-party commercial services

* [Twilio Programmable Messaging API](https://www.twilio.com/messaging-api)
* [Vonage/Nexmo SMS API](https://www.vonage.com/communications-apis/sms/)

---

## 海報及告示範例

:::success
```graphviz
digraph hierarchy {
bgcolor="transparent"
node [fontname=Courier,shape=box]
Start [label="簡訊實聯：請選擇下列任一種登記方式 ✅\nContact-information registration: choose one below"]
QR [label="[QR CODE HERE] 📷
掃描二維條碼，按下簡訊送出 📤\nScan QR code and text it"]
Text [label="📝\n簡訊輸入 5566 5566 傳送到 1922 📲\nText 5566 5566 To 1922"]
Receive [label="接收確認簡訊 📩\nReceive confirmation"]
Pass [label="給工作人員看確認簡訊 📱\nShow confirmation to Staff"]

Start -> {QR Text}
{QR Text} -> Receive
Receive -> Pass [label="歡迎向工作人員詢問 💬\nHaving trouble?\nFeel free to ask questions"]
}
```
:::

---

## 使用申請規劃

**注意：非「[1922 簡訊實聯制](https://g0v.hackmd.io/FxudGiM8RSKnpCo4TrMhNg)」**

### Submit

To database server

###### *為必填欄位

`名稱*`
`類別（可自訂）`
`詳細地點*`
`聯絡人姓名*`
`聯絡人手機（聯絡及認證用）*`
`聯絡人電話（市話或備用手機）`
`Email`
`備用聯絡人姓名`
`備用聯絡人電話（市話或手機）`
`統一編號（僅供企業使用）`
> 1. 有準確的地理資訊作為 contact tracing
> 2. 有聯絡人可以通知接觸確診者以及清消
> 3. 但盡量不要求太多資料，以免攤販店家擔心查稅
> 4. 地點不限門牌地址，方便攤販使用
> 5. 統一編號可供連鎖企業或組織內部警示
> [name=AceChen]

### Return

`[MerchantID]`
`QR code PNG/SVG`
`Poster/Flyer A4 PDF (Ch+En)`
`Customer manual PDF`
`Merchant manual PDF`
`URL to request new [MerchantID]`

---

## Feature request

- [ ] 取消登記
  > 可能需要另外發送取消登記訊息？ eg. 場地編號: xxx\n取消登記 但是實作上可能變成每日批次處理刪除 [name=pichu]
  > 可以傳送簡單字串 e.g. `cancel:555666` 然後系統會取消使用者在店家 `555666` 的最後一筆紀錄 [name=AceChen]
  > 傳送簡單字串沒有傳送商家編號的問題在於門號數量可能不夠多，因此可能有多家分店需要共用同一門號的狀況，另外要注意簡訊在一定字數內費用相同，因此可以在合理範圍內寫清楚，增加未來可擴充性 [name=pichu]
- [ ] 英文簡訊或中英並列
  > 發送用範本可以產生英語或他國語言 QR Code, 內文不要使用到保留符號 (:), 伺服器實作抓 : 和 \n 進行 Parsing, 抓訊息前三個Byte作為語言特徵辨識碼即可實作 i18n [name=pichu]
  > 簡訊可以判斷使用者手機的語言嗎？我是考慮對於外語人士來說，他們看不懂按下送出和接收確認的簡訊。回傳的確認簡訊可以先用中英文並列，70 字應該放得下 [name=AceChen]
- [ ] 其他語言/語言切換
- [ ] 防止濫用或惡作劇 e.g. 增加校驗碼
  > 在濫用風險較高地區，例如學校，可以考慮用電子動態生成 QR Code，在次行增加隨機碼，隨機碼可考慮15分鐘亂數生成，系統在檢核隨機碼不同時回應新增失敗（但仍應紀錄進系統並進行標記來源號碼）[name=pichu]
  > 在傳統店面或一般應用，如果 `[MerchantID]` 被濫用，如遠端攻擊，則可申請更換。但因為印製新的 QR code 需要時間，在 backend 可能先需要某種異常偵測 [name=AceChen]
- [ ] 系統廣播 e.g. 人數過多
- [ ] 查詢個人歷史紀錄
  > 請使用者自己翻閱自己的簡訊發送紀錄？ [name=pichu]
  > 假設使用者刪掉簡訊收發紀錄，可以傳簡訊 e.g. `SMSTO:1922:history 1d` 則回傳過去一天登記過的 `[MerchantID]` `[TIMESTAMP]` [name=AceChen]
  > 好像可以，不過不知道會不會內容太多導致分多頁，也許這邊可以變成回傳一個網址讓使用者去點？ [name=pichu]
- [ ] legacy phone support
  > 不確定舊手機是否用 `\n` 換行 [name=AceChen]

---

## Slack 討論串

### 構想
https://g0v-tw.slack.com/archives/CTMK5QPA8/p1621090281023000
:::spoiler
> 實聯制的背後是傳統疫調希望掌握一切的習慣延伸，但臺灣社交距離app 本身就可以做到記錄，如果要用陰謀論去看應該沒有一個方式是不能刻意繞過的
> [name=kiang]
> 
> 所謂想掌握一切，那是最早的實名制。會推出實聯制指引，是為了儘量達成接觸通知，而不用蒐集實名等個資。
> 社交距離 ENS 是一種接觸通知的方式，但現行 App 通知範圍的計算方式，和目前實聯制在同時段內，室內全部都算可能接觸者（例如：即使保持距離仍可能接觸物品而間接傳染，或通風較為不良時氣溶膠傳染）有些不同。
> 我覺得現在實聯制是 UX（包括設定和通知流程）需要改進，不確定貿然廢除的效益。
> [name=au] 
> 
> 不確定既有接觸通知架構能否延伸，像是特定類型標記只要接觸無論時間長短就直接記錄，這樣一來店家可以採購或是運用現有設備在店門口放置，進門的所有人就會在自己的手機中保有店家設備產生的代碼，進而在店家顧客確診後運用既有架構通知其他人
> 實聯制太多問題，大量個資被不熟悉資安概念的店家保留，或是許多人習慣留假資料，徒具形式吧
> [name=kiang]
> 
> 如果對特定用戶端去定義延伸到極短時間都算接觸，同時也是提高中繼攻擊、重送攻擊的風險。我覺得值得探討，但要考慮「店家」並不是藥師、醫事人員，而有各種動機。
> 今天在這裡看到掃 QR 送實聯制簡訊到店家實聯制專用門號，這樣只蒐集手機號碼、時間、店家號碼三個欄位的方案，我覺得很有創意，而且比較沒有留假資料的動機。
> 如果不希望電信商聚合這個資訊，用其他即時傳訊軟體也可以模擬。
> [name=au] 
>
> 看起來 CDC 的「防疫新生活運動：實聯制措施指引」只要求「蒐集之個人資料項目：蒐集資料應符合最少侵害原則，如電話號碼。」
那我完全同意 @au 提出來的，掃 QR code 送簡訊到店家，這樣未來有手機號碼可以聯絡得到人就好。或者平板/手寫電話號碼，店家送簡訊到手機，只要點下簡訊裡面的連結（或回覆簡單訊息 e.g. "yes"，適用於沒有網路的人）就可以 verify 手機號碼
美國有 Twilio/Nexmo 之類的簡訊 API 可以收發 SMS，我猜台灣應該也有類似的服務
對於不想用 SMS 暴露資訊/沒手機 的人，還是要有紙本作備案
> [name=AceChen]
> 
> sms 服務不難，只是會有延伸的費用產生，也要能夠自動彙整資料才可以降低店家的使用門檻吧
> [name=kiang]
> 
> FYI: Twilio/Nexmo etc. 可以串台灣的四大電信，簡訊收發單價不算貴，專用號碼比較花錢
> [name=AceChen]
> 
> Twilio 很貴 XD ，對比台灣在地的簡訊收費服務，但 Twilio 的確整合得很好
> [name=kiang]
:::

### Mockup
https://g0v-tw.slack.com/archives/CTMK5QPA8/p1621143493126000
:::spoiler
> 這種系統叫「簡訊實聯」如何（剛想到的名稱）？或是有更容易記的名字。剛 mock up 了一下。
> `場所代碼：88888888888`
> `本次實聯簡訊限防疫目的使用。`
> ![](https://files.slack.com/files-pri/T02G2SXKM-F022DTZSK3K/______.png)
> [name=au]
> 
> 這樣一來變成顧客要負擔簡訊費用、店家要自己彙整資料， https://covid19.mutix.co/ 的作法如果能夠移植到政府端會不會單純些？
> [name=kiang]
> 
> 之前 eMask 用 `1919` 處理簡訊的經驗是，電信商可以把簡碼轉成五大電信各自的全碼。在不跨網的情況，應該可以吸收雙向的簡訊費用（也就是顧客免費）。
> 至於彙整資料，如果給各電信商彙整呢？（假設電信商無法取得場所代碼往店家的 mapping。）
> 也就是切開 1. 驗證服務：確認店家身分發出代碼 2. 電信服務：單純收代碼簡訊
> 需要發出通知接觸時，電信服務依場所代碼發，但是看不到店家身分這樣。
> [name=au]
> 
> 固定代碼就會有預期外蒐集疑慮，所以才說直接環繞著社交距離 app 去延伸，只要要求店家裡面每個店員必須安裝，願意的話在門口確認進入顧客有安裝、開啟
> [name=kiang]
> 
> 具體是哪種預期外蒐集呢（假設所有人都是傳到 `1922` 而各電信商也都有做 28 day rotation）
> [name=au]
> 
> 好奇實聯制實際應用的比率，以及後續延伸通知的錯誤率，看到太多的記錄都是錯誤的
> 因為店家代碼是固定的，電信商過程中如果刻意保留這些登入記錄，累積的資料就會有延伸消費行為分析的商業價值
> [name=kiang]
> 
> 從 ENS App 來打卡當然也是一招。英國的 NHS App 就是這樣做，不過他們的 Check In 通知方式也和 ENS Protocol 是脫勾的。
另外就是這樣就要額外要拍照權限了，再另外就是簡訊比較可以給 feature phone（或舊手機）用。
> 只要走簡訊，即使傳給店家而非 `1922`，電信商如果要違法攔截簡訊，似乎不能用技術阻止。這樣就必須架在 E2EE 通訊層上了。
目前的想法是設計文字裡有 `本次實聯簡訊限防疫目的使用`。
> [name=au]
> 
> 我是支持 ENS App 打卡的，如果 apple/google 願意，目前台灣 feature phone 應該已經很少見？
> [name=kiang]
> 
> 英國的做法是不走 ENS Protocol 只是把打卡加在同一個 app 裡。 https://create-qr-code-poster.service.gov.uk/createposter/contact-details
> [name=au]
> 
> 我想 ENS Protocol app 在 apple/google 都會有特別的審查，如果可以任意加功能大概就不會像現在這麼單純了 XD
> [name=kiang]
> 
> 很棒的提醒，簡訊不用等 App Store 審查，手機應該都有內建簡訊功能 XD
> [name=au]
> 
> 而且簡訊的話，非智慧型手機也能使用。
> [name=Kate Lee]
> 
> 那就來寫簡訊程式了，感謝 @pichuchen 和 Kate 率先提出這個物美價廉（免費簡訊實聯！）的主意。
> [name=au]
> 
> 如果可以談到顧客免費的話，在簡訊連結上的使用者體驗應該會是最好的，而且連手機驗證都做完了，不用擔心像我這種每次都被問「你這是4還是9」的人。
> ENS app 目前還有個無解問題是手機版本太低
> 然後大多數店家和顧客可以接受的方案是Google表單 + 紙本並行制。
> 簡訊的部分我印象是twillo這類的有API 可以收，如果可以爭取到免費的話那系統應該可以再回應一封 「全聯民權店於 XX 點XX分已收到您的資料了」 作為現場讓店員目視確認的證明
> [name=pichuchen]
> 
> 回應的格式要想想，如果有「全聯民權店」的話等於使用者的簡訊紀錄裡會有任何人（而不是疫調者）可還原的場所足跡。或許還是用店碼（場所碼）放在簡訊裡即可。
> 然後如果店碼被改到，再出錯誤訊息即可，沒回訊就是成功。
> [name=au]
> 
> 如果是使用者自己可以還原我覺得還可以，如果他不希望給有辦法拿到他手機的人看到足跡（通常是另一半）那他可以按刪除簡訊，對一般人來說我覺得困難點還是在假如我被檢測出確診時，我很難想起來到底上禮拜三有沒有去全聯還是全家這樣
> 以前我用android手機的時候Google地圖會幫我記錄足跡，後來我覺得怪怪的，在iPhone上就沒用了，不過我換成是在餐廳之類的地方可能會亂拍照，這樣在相簿裡面我自己就還是可以大致上知道足跡
> 不過其實發送紀錄中已經有該場所ID了，所以回應訊息中沒有場所足跡的話其實也還好，就是到時候再找地方還原場所ID這樣
> 或者是場所ID直接用中文作為場所ID? 這樣打錯的機會說不定更低
> [name=pichuchen]
> 
> 我覺得場所ID還原到地點應該是給疫調者做的事情... 應該不需要靠確診者來。至於接觸通知只要能送給同場所ID同天入場的人就好了？場所ID我想絕大多數人都是用掃的，只是要給店員看一眼。
> [name=au]
> 
> 其實我現在不太確定是疫調者他會怎麼知道確診者去過哪些場所這件事，因為感覺像是憑記憶，實聯制目前的做法看起來也是憑記憶？
> [name=pichuchen]
> 
> 如果場所都有做簡訊實聯，那在電信端可以從確診者手機號產生出店碼列表，再找註冊端還原到場所列表即可。
> 紙筆實聯的話確實是憑記憶～
> [name=au]
> 
> 誒對，如果是簡訊實聯的話那就可以請電信端配合了
> [name=pichuchen]
:::

### 延伸討論
https://g0v-tw.slack.com/archives/CTMK5QPA8/p1621182561272700
:::spoiler
> 實聯制的部分，目前我認為最好用的還是有人幫忙付錢的「簡訊實聯」（暫定）
> https://g0v-tw.slack.com/archives/CTMK5QPA8/p1621143493126000
> 目前除了他是中心化的系統不知道會不會壓力過載以外，目前還沒有想到什麼大問題
> [name=pichuchen]
> 
> 會不會像上次口罩一樣突然帳單爆炸XDDDD
> [name=ky]
> 
> 可以點進去討論串，如果政委能夠協調簡訊費用的話，其實這個作法可以在很短的時間做完電話號碼驗證
> 如果是最早一開始想到的作法，簡訊費用是由消費者而非店家付的
> 但是 1.5/每次進入 其實也是很便宜的費用就是了（相較於工程師人力）
> [name=pichuchen]
> 
> 內容一樣是填名字 電話 人數嗎？
> [name=cai]
> 
> 內容只有店家編號
> 人數可填可不填
> 電話在簡訊發送時就會記錄下來了
> 所以對使用者來說情境就是：
> 1. 掃描 QR Code
> 2. 確認內容按下送出
> 3. 把畫面給店員看
> 
> [name=pichuchen]
> 
> 那非智慧型的手機就是走回紙本版？
> [name=cai]
> 
> 非智慧型手機走回紙本沒錯，基本上是改良QR Code + 問卷這樣
> [name=pichuchen]
> 
> 如果是發簡訊的話，非智慧型手機也可以吧？只是要手打就是了
> [name=Stimim]
> 
> recap:
> QR code 對會使用智慧型手機的人比較快，掃完 QR code 自動帶出 parameters，確認就送出了
> 對於不會使用、或沒有智慧手機的人，就是傳簡訊給特定的電話號碼（可能需要短碼），不過因為不會自動帶出店家或顧客資訊，可能要 append 一些文字在簡訊裡面
> 對於沒有帶手機，亦或不想使用這方法的人，就走傳統紙本，但至少有做到分流，使用紙本的人應該不會太多而塞車。但是應該隨時要有紙本作為備案~~以免電信公司機房被關錯開關~~
> [name=AceChen]
> 
> 用簡訊在隱私方面有特別的優勢嗎？
> [name=Cheng]
> 
> 與問卷相比沒有，但是正確性高很多，打錯的機率會大幅下降，可能問卷一千次按錯一位數，簡訊完全不會按錯
> [name=pichuchen]
> 
> 那與需手機號碼註冊的，像 tracetogether 此類相比又有何優勢？
> [name=Cheng]
> 
> 他不用註冊，使用者流程極短
> [name=pichuchen]
> 
> 我同意目前簡訊算是收集最少資訊但又勉強剛好足夠資訊提供疫調：
> 簡訊會暴露使用者的手機號碼，但只要特別對電信業者規範，不得作為其他用途且有個資保留期限。相對下我覺得對 SurveyCake/Google Sheets etc. 的規範會更繁雜，畢竟線上問卷/表單不是只作為實聯制用
> 簡訊的流程應該目前最短的，而且不需要註冊，不需要網路。當然有網路的話透過 SMS gateway 發簡訊不用錢（台灣有嗎？）上面 @au 也提到可能有其他辦法吸收簡訊費用
> 透過簡訊回傳可以確認 1-to-1 mapping 不用擔心目前線上表單/問卷形式會有的填錯或亂填的問題（台灣的 prepaid phone 需要證件嗎？）
> 有手機號碼的話，最糟的情況下還是可以用目前的數位圍籬去框列接觸者，這部份隱私的侵害在目前傳染病防治法下大概很難避免，但是基本的公告要有 e.g. 此簡訊實聯作為 blahblah
> [name=AceChen]
> 
> 每個店家自己可以選擇實作方式為我認為這還是在自由範圍內，畢竟各個解決方案互相競爭，那這樣能夠最小侵害人民權益使用者流程最好的會勝出這樣，而不是只有地方政府發包的會勝出。
> 而且分散運作可以一定程度上增加效率，如果今天紙本實聯制表單是要由中央印刷後發到每個店家，可能下個月都還拿不到
> 但是講清楚規則之後大家就自己Word做一做就列印了
> [name=pichuchen]
> 
> 我完全同意，實聯制需要一些不同的系統，有些大公司可能想要用內部系統來結合會員卡之類的。政府可以也開發一套讓大家自由選擇，但對於不想要把個人行蹤資料交給政府保管的人，就可以選擇 covid19.mutix.co 之類的
> 不同的實聯制系統也是一種 redundancy ~~以免有人關錯開關~~，我個人是希望簡訊實聯可以最廣泛
> 但在一開始百家爭鳴的階段，大家的個資在一些權限不明的網路表單上流傳，令人擔心啊… QQ
> 另外想提醒的是，目前 Exposure Notification System e.g. 臺灣社交距離App 無法代替實聯制，技術和目的都不太一樣
> [name=AceChen]

https://g0v-tw.slack.com/archives/CTMK5QPA8/p1621185997302200
> 這個 SMS 的實聯制什麼時候可以上線？
> [name=Cheng]
> 
> 要做應該是在一天內可以做，但是要看實際上的實作架構，目前後端的作法有想到更好的作法，只要店家下載Android APP就行了
不過現有的Google表單其實也很好用，到底需不需要換掉其實也很難說
> [name=pichuchen]
> ![](https://files.slack.com/files-pri/T02G2SXKM-F021YLJJM45/image.png)
> 手機掃描之後按送出，這樣我就能記錄到你的電話了
> 就是我那邊那串提到的東西， 不過這樣玩會有費用，雖然不高，比起工程師開發成本來說更低，但是有費用就會有導入障礙
> twilio 會收到的東西是這樣
>`ToCountry=US&ToState=TX&SmsMessageSid=SM16426f14fe1828f5a54af0facb014ba4&NumMedia=0&ToCity=LEWISVILLE&FromZip=&SmsSid=SM16426f14fe1828f5a54af0facb014ba4&FromState=&SmsStatus=received&FromCity=&Body=%E5%BA%97%E5%AE%B6%E7%B7%A8%E8%99%9F%EF%BC%9A+MR-0001%0D%0A%E5%BA%97%E5%AE%B6%E5%90%8D%E7%A8%B1%EF%BC%9A%E5%85%A8%E8%81%AF%E8%98%86%E6%B4%B2%E6%B0%91%E6%97%8F%E5%BA%97&FromCountry=TW&To=%2B12143076679&ToZip=75028&NumSegments=1&MessageSid=SM16426f14fe1828f5a54af0facb014ba4&AccountSid=AC9580cc337301853824e2fea53bddffd7&From=%2B88xxxxxxxxxx&ApiVersion=2010-04-01`
> 然後這邊有個缺點是個資還是會進第三方公司 (twillio) 所以要做好一點在想可能是寫成Android APP 然後收簡訊，這樣店家只要準備一隻Android手機就行了，放口袋或是充電中都可以
> [name=pichuchen]
:::


## 其他實聯制系統

* [1922 簡訊實聯制](https://g0v.hackmd.io/FxudGiM8RSKnpCo4TrMhNg)
* [實聯制 | 電子化解決方案](https://covid19.mutix.co/)
* [台灣加密型實聯制](https://twlink.app/)
* [COVID-19防疫實聯制措施](https://sites.google.com/email.nchu.edu.tw/slimz/)