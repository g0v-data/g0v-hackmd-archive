---
title: nonprofit-helper：零時先輩專案諮詢紀錄
tags: edu, jothon
---

# nonprofit-helper：零時先輩專案諮詢紀錄

:::warning
**零時小學校 4th 專案孵化競賽：零時先輩專案諮詢紀錄**
[🏫 首頁 Homepage](https://g0v.hackmd.io/@jothon/rydvIDluT)
:::

:::success
* 「nonprofit-helper」共有 2 小時的諮詢時間可運用。
* 每位講師所需的諮詢時間由各團隊定義，實際諮詢時數可以與預計諮詢時數不同，但總時數請勿超過可諮詢時數。
* 若需更多時數，請來信申請，零時小學校會根據專案狀況進行評估。
:::

> [TOC]

## 提案優化工作坊回饋：

## 諮詢先輩 1：superbil

### 諮詢時段：2024-02-26 Mon. 21:00 - 22:00

### 諮詢紀錄
#### 目前還缺後端，建議用哪個框架來處理？
- firebase 
    - 不用從頭建一個後端，對新手來說部署和維護都簡單很多
    - 缺點是如果超過 free tier 用量，收費以業界來說算貴的
- Python
    - FastAPI 算簡單很多的框架
- node.js
    - 如果不想用 node，可以用 `node.js alternatives` 或 `awesome node.js` 這個關鍵字去搜尋相關資源
    - https://github.com/sindresorhus/awesome-nodejs#web-frameworks
- next.js
    - 也是參考看看的
#### 發信系統推薦
- gmail 自動化是可以的
    - 如果量很小的話
- GCP based mail services
- AWS based mail services
    - Simple Email Services
#### crawler 推薦
- 用 python 寫比較簡單，可以直接上網找套件
    - beautiful soup
    - selenium
        - 可以模擬真人瀏覽網頁的行為，chromium based browser 比較穩定
        - 記得按照 selenium 官方的建議 setup
        - 上面也會有其他語言的寫法，像是 javascript
#### 網路資源推薦
- awesome list
    - 只要用這個關鍵字找，就可以看到很多人推薦的好用資源清單
    - 請注意
        - repo 更新日期不能太舊，六個月前更新還可以
        - github stars number can be a benchmark
        - 網路資源僅供參考，不能盡信
---

## 諮詢先輩 2：建泰老師

### 諮詢時段：2024-02-23 Fri. 21:00 ~ 22:00
### 諮詢紀錄：
#### 公益社團需要計畫書或編預算等事務的協助
- 通常這樣的提案需要很多證據佐證
    - 提計畫時，主要問題不在寫計畫書，而是需要準備很多相關的資料，把它變成一個有邏輯的論述。
- 很多小組織缺乏能力應付繁文縟節或核銷的規定
    - 就算非營利組織的成員沒有「拒絕申請政府補助」的潔癖，還是得面對核銷、結案等問題，都是寫申請案通過後，才接踵而來的麻煩。
    - 政府非常害怕弊端，所以如果有工具可以協助公益社團儘量縮小所有報銷文件的問題，會很棒。
#### 非營利組織真的有能力處理政府補助案嗎
- 倡議型組織
    - 組織相對弱勢
    - 很窮，很需要政府相關的計畫或案子
        - 政府一定有案子要丟出去給民間做
        - 像是食農教育或淨零碳排
        - 但倡議型組織不一定有足夠資源（學術、技術或行政技能）來承接這些專案
        - 所以真正需要政府資源的人，都拿不到政府資源
        - 
- 產業協會
    - 不缺錢
    - 很多顧問公司背後都是老闆、學者，他們都養很多專人，很多資源接政府案並處理
    - 政府也喜歡，因為核銷和主計肯定很容易就過關

##### 難點
- 要怎麼幫忙接案
    - 比如用爬蟲把所有政府外包的案子集中起來
- 要怎麼幫忙提升真倡議型團體的行政 capacity
    - 做起來的話，也可以讓政府或公務員越來越願意將案子交給私部門來處理
    - e.g. 多元就業計畫，勞動部有派承辦人來輔導協會來寫計畫、甚至將民間找來輔導
    - 如果一般小老百姓也有辦法透過 AI 寫出高品質的企劃書或結案報告，當然政府也會願意將接案子的機會
    - 要協助協會快速了解掌握政府施政方向或政府希望做的方向

#### 要處理的問題
- 會務
- 會計、作帳
    - 會務專員沒有專業，還是要找會計士來問
    - 如果可以直接問 AI，可以省掉很多不必要花的錢
- checklist 
    - 自動產生法規規定必須完成的事項
    - 要可以開放匯入內規
    - 最好系統可以協助幫忙整理出內規給使用者確認

#### 建議
- 目前提案內容太抽象，不夠讓人產生畫面，可以寫「協會要生存下去，很多瑣事不應該花費時間」
- 協會就是很窮、
- 

---

## 諮詢先輩 3：peii

### 諮詢時段：2024-02-28 Wed. 10:00 ~ 11:00

### 諮詢紀錄：

#### 

- 消防員權益促進
- 台北市藝創工會

#### 公益團體的數位轉型


#### 該工具的尺度大小
- 

---

## 諮詢先輩 4：Ronnywang

### 諮詢時段：2024-02-29 Thr. 21:00 ~ 22:00


### 諮詢紀錄：

#### can this stt module work in other's device?
- [github repo](https://github.com/gaborvecsei/whisper-live-transcription)
- seems worked on ronny's device, but comes with 30 seconds approx latency

#### viable stt solution for device comes with no CUDA
- whisper based
    - whisper.cpp
        - [stream](https://github.com/ggerganov/whisper.cpp/tree/master/examples/stream)
- [web speech API](https://www.google.com/intl/en/chrome/demos/speech.html)
    - *way faster than whipser if you need realtime transcription*
    - with decent accuracy in mandarin
    - chrome has to connect to internet
    - safari might just call the local api to achieve the functionality, can work without internet connection
    - firefox didn't implement this feature
    - [`meet.jothon.online`](http://meet.jothon.online/meet/show/g0v-hackath38n) once use this feature to generate realtime transcripts, can learn it from just look up in page source, cause this transcripts didn't transfer to the backend
    - tons of way to keep the transcripts without a backend, like localstorage

#### some attempt
- [discussion](https://g0v-slack-archive.g0v.ronny.tw/index/channel/C055ZJBKZML/2023-07)

- https://gist.github.com/ronnywang/07f597003678982a4a158f07ea6d7533
    - 程式碼放在這裡

- 原理如下：
1. 先用 ffmpeg + streamlink 即時以最低畫質下載 youtube 實況影片，並且以 5 秒為單位存一個 wav 檔
2. 把除了最新的一個 wav 檔以外的即時合併在一起（因為最新的正在寫入中，會無法讀取）
3. 對這個 wav 做 whisper ，根據檔名的 timestamp 加上時間軸可以知道話是幾點鐘講的
4. whisper 最後一句話有可能被切到一半，因此不要輸出最後一句，記下最後一句話的時間，再用之前 whisper 處理的最後一個 wav 檔跟他後面新的 wav 合併在一起，重覆動作 2
#### can stt tech identify different speakers
- whisper.cpp
    - [diarize](https://github.com/ggerganov/whisper.cpp/blob/25d313b38b1f562200f915cd5952555613cd0110/README.md?plain=1#L121)
    - but they just do it by determine which channel and strength that sound coming from

---

## 決選日評審回饋：