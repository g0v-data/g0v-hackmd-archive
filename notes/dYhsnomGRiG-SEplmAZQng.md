---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20240708 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- NPO hub 出席：Bil, mrorz, nonumpa
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::


## LINE bot long response handling

票：https://github.com/cofacts/rumors-line-bot/issues/395

Details changed
- No need to transfer progress; build helper function and pass in each handler
- Just record last reply token is sufficient

:::success
可以按照此規劃實作
:::

## Community

- TW LLM 
  > 這個拿來做在地化的事實查核初步分析會不會更好用？只是他資料是2023年4月以前的
  > [name=cai]
  > 本質上 verification checking 比較是RAG的專長，跟有沒有繁體中文在地化，關係不到非常大，當然有比較好的語料訓練對於中文理解可以有幫助，但是模型本身的能力對於邏輯的推斷，跟語料不是唯一相關，可能跟模型大小、訓練方式技巧更有關係一點
  > [name=Chen-Hung, Pai]
  > 
  > 把類似的訊息過去是怎麼回的，作為 few shot example 放在 context window，應該會比抽換 LLM 有效。
  > 目前的規劃：https://g0v.hackmd.io/@cofacts/rd/%2FmU8qi721RZeAQ9PDfj7XRA
  > 不過我也蠻期待 TAME 的語氣與用字遣詞會比其他語言模型更貼近台灣習慣。Cofacts 的 use case 應該也不太會被 llama（TAME 的基礎模型） 的 license 限制。
  > 只是當回到斤斤計較的工程面，這個模型如果沒有人 host API，那麼我們要用的話，不是要砸大錢自架 inference server，就是要用 batch 的形式處理。這樣就沒辦法用在即時回應新訊息了。
  > 即使使用 replicate 這類服務，一旦模型沒人用，下次 API 就會需要解凍才能用，要等待幾分鐘才會回傳結果。
  > [name=mrorz]

- 回報 hallucination [name=cai]
  - 紀錄至 https://g0v.hackmd.io/mU8qi721RZeAQ9PDfj7XRA#20236-%E4%B9%8B%E5%BE%8C%E7%9A%84-hallucination
  - 問題：為何 https://cofacts.tw/article/CnE6PpABd3gcY0Lpo3u- 有 4 個 cooccurrence 但只有一個 reply request ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e1dc46d920f840f20e4dbc4a6daae612.png)
  - 4 個不同人收到同一個圖，圖沒回應過，但 reply request 一直都只有 1
  - LINE bot 在 `choosingArticle` 時會 `SubmitReplyRequestWithoutReason`
    - 使用者回報了 cooccurrence (觸發 `SetCooccurrences` mutation) 並不會幫使用者加上 reply request
    - 要另外點圖，才會 submit empty reply request ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0a8e8b2b7b2f51c117f48acd6e9feaec.png)
    - 明明就已經查到了圖，應該要有 reply request
    - set cooccurrences 的 article id 應該是精確的（不會有逐字稿或比對太差的文字？）因此應該可以在 `ASKING_COOCCURRENCE` 針對沒回應的 article 做 submit new reply requests [name=mrorz]
  - LINE 詢問數也是 0，至少後來的人應該要算 view count ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_cd493e4fe07ab0fca66348bd424dd8a8.png)
    - 以往都是算在 `CHOOSING_ARTICLE` 裡，但 batch 時使用者不一定會點到圖裡
    - 但如果一樣做在 `ASKING_COOCCURRENCE`，那 `CHOOSING_ARTICLE` 可能又會算一次 LINE bot 造訪
    - 但話說回來，反正現在使用者已經可以觸發多次 `CHOOSING_ARTICLE`，每次都會算造訪⋯⋯ [name=mrorz]
    - 而且看起來這個 case 就是大家沒有點 choosing_article 觸發造訪（可能點了第一則文字，發現 chatgpt 回應怪怪的，也沒有回來點點看圖是否有回應）

:::success
開票追蹤
- reply request --> https://github.com/cofacts/rumors-line-bot/issues/396
- bigquery visit event --> 較為次要。現在 create article 的第一人也不會紀錄 LINE bot view event
:::



## Talks
- MTK
- 反詐
- 假訊息判讀 Tiff 7/23 線上

## 小聚籌備

- [x] 日期：08/03（六）
- [ ] 食物：
- [ ] 場地：NPO Hub Foundry（大的那間）- 還沒有借
- [x] 時間：
	- 活動時間：14:00 - 17:00
	- 時間分配
        - 2:00 - 2:20 開場
            - 影片
            - Slido 暖身
        - 2:20 - 2:40 引導註冊網站、介紹評價現有回應
        - 2:40 - 2:50 實作評價
        - 2:50 - 3:10 介紹補充資訊
        - 3:10 - 3:40 實作補充資訊、自我介紹、休息
        - 3:40 - 4:10 介紹撰寫新回應
        - 4:10 - 4:40 實作撰寫新回應
        - 4:40 - 5:00 介紹分類、RSS、合照
- [ ] 投放目標：
  - 推播日：07/24 推播
  - 推播日之前： 
  - 目標：雙北
- [x] KKTIX: https://cofacts.kktix.cc/events/cofactseditor43
- [x] 誰會來呢：bil, mrorz, nonumpa
- [ ] 記得帶：貼紙、環保杯
- [ ] LINE 文案：炎炎夏日，詐騙訊息說：「系統已將您列為風險帳號，進行暫時凍結處理。」該如何辨識與實際幫助家人，08/03（六）14:00-17:00 Cofacts 第43次查核志工培訓工作坊期待你一起來參與協作＝Ｄ
地址：台北市中正區重慶南路三段2號二樓（最近的捷運站是中正紀念堂站2號出口）
- [ ] VOOM 發文
