---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20231108 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：nonumpa, zoey, mrorz, bil, T
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## CCPRIP

### [Comm] Transcript

> [name=nonumpa]

- OpenAI 釋出 Whisper V3 [name=mrorz]
    - 沒提到 hallucination，悲觀猜測一樣爛 https://github.com/openai/whisper/discussions/1762
    - 在測資上中文幾乎沒啥改進
    - API 還沒升級

### [Comm] ChatGPT-aid fact checking

> https://g0v.hackmd.io/@cofacts/rd/%2FmU8qi721RZeAQ9PDfj7XRA

技術：[Assistant API](https://platform.openai.com/docs/assistants/overview)
- 自動管理對話紀錄
- 提供 "Knowledge"
    - 檔案的形式
    - 會自動 index，在後續的對話中有需要時會查找
- Function calling

對話式的 Fact check assistant
- Cofacts 每個訊息頁面一個 thread
- 對話每個登入後的使用者都可以用
- 開啟 thread：LINE 使用者 / Cofacts 查核協作者選擇開啟
- 開串起手式
    - 訊息、類似訊息、類似訊息的回應
    - 初步分析結果
    - Fact check organization (custom search engine) search result
    - [以圖找圖](https://cloud.google.com/vision/docs/detecting-web)
- LINE 使用者、查核協作者可用自然語言與 fact check assistant 互動
    - 提供線索
        - 爬取網址內容
        - 跟「我想補充」有點重疊
    - 彙整資料與現有資訊
    - 重新爬一次 google search (可能過去沒有現在有)
    - 針對資訊進行計算（code intepreter）
- 其他
    - AI 在對話中注意對話是否離題（均須與原始訊息、查證有關）
    - 提供使用者檢舉功能
    - 可 summarize 目前討論結果，讓其他查核協作者快速耕上（等到有很多人用時再說）

:::info
先在 OpenAI playground 試試看再說
:::


## Article group / cooccurrences

還在想先修復 https://github.com/cofacts/rumors-line-bot/issues/327
Rewriting postback handler again...... https://github.com/cofacts/rumors-line-bot/pull/369/files
- postback handler 只有一個 input string --> 可以支援 postback 是 object 等
- postback handler 會在其他 handler 呼叫，需要更簡單的 signature
    - 直接指定 postback 而不用蓋一整個 postback event 進去
    - 取代 `server_choose` event
- unit test 更新


## Site change

Mobile site 沒有捐款連結的 link --> 開票 https://github.com/cofacts/rumors-site/issues/553
- 放右邊
- landing page 可以做 footer

## 小聚籌備

- 2023/11/18 (六) 2pm - 5pm
  - 新營市民學堂
- [ ] 食物
- [ ] 場地費：MrOrz 攜帶尾款 2500
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
- [x] 投放目標：雲嘉南 30000 人
  - 提早推播: 11/3
  - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e8a1b017408c430e0559378744d883f8.png)
  - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ecb4340e5f99031c12a09ef2308679ac.png)
- [x] KKTIX: https://cofacts.kktix.cc/events/cofactseditor39
- [x] 誰會來呢：rosalind, nonumpa, mroz
- [ ] 記得帶：貼紙、環保杯
- [x] LINE 文案
- [x] VOOM 發文

台北 --> 新營：
高鐵嘉義站 --> 黃 9 --> 新營站
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1e23808e442414a09e5ecea1b0379c63.png)

:::success
下週邀請 rosalind 一起過 rundown
:::

## Hypercerts 回溯公眾投資

- 把 blocto 加入文件、各自聯繫參與者
- 12/15 一次計算+發證
- 核心參與者有查核也會計算
- 週五訪談
