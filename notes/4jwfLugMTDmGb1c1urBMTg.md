---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20250812 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- 線上出席：nonumpa
- 實體出席：bil, mrorz
- https://meet.google.com/mrz-dgrd-pri
:::

## 本次會議待追蹤項目 (由 2025/08/05 會議記錄結案)

*   **[Johnson]** 資訊安全權限設定
    * Not yet
*   **CCPRIP - Analytics**: Opendata trend & LINE Bot usage 報表問題
    * Not yet
*   **cofacts.ai**: Groundness Check agent 實作
    * Update on proposals
      * 團隊介紹
      * 補充資料：screenshot + 英文介紹 as an early proof-of-concept
    * 相關資訊
      * Deep research implementation: https://github.com/google/adk-samples/blob/main/python/agents/gemini-fullstack/app/agent.py
      * Langfuse integration: 參考 https://github.com/langfuse/langfuse/issues/6588#issuecomment-3056208403 override `run_sse` endpoint
      * If async tools are in separate traces, apply this https://github.com/langfuse/langfuse/issues/8216#issuecomment-3176792995
      * 整理到 RD 文件 or https://github.com/cofacts/beta-ai/ issue
*   **Claude Code Action**: 連接到 Vertex AI
    * Sample: https://github.com/cofacts/rumors-api/pull/375/files
    * Apply to others
        * rumors-site: action 已經有 service account, 但權限不對（用來 deploy 的，預設[沒 predict role](https://github.com/cofacts/rumors-site/actions/runs/16904423637/job/47890765372#logs)）
        * 其他還要設定 service accunt
        * 想要開一個專門用來放在 Github organization 裡 call vertex ai 的 service account
            * Role: [Vertex AI Platform Express User](https://cloud.google.com/vertex-ai/docs/general/access-control#aiplatform.expressUser), or any other role with just `aiplatform.endpoints.predict` permission
*   **[nonumpa, mrorz]** LLM based Topic Classifier: 修復 bug 並確認 benchmark
*   **小聚籌備**:
    *   [x] 發布 VOOM 貼文
    *   [x] 發布 FB 貼文



## url-resolver update

新想法：[用 Gemini + URL Context tool](https://github.com/cofacts/rumors-api/issues/373#issuecomment-3177644376)
- 請 AI [做個 branch 看看](https://github.com/cofacts/rumors-api/pull/377)
- Follow-up:
    - 跑實驗
    - 看要不要把 url-resolver 的 unfurl 拉到這裡來做
    - LLM 其實會自己抽 URL，我們似乎不需要自己抽 URL XD
    - 融合 unfurl + LLM result
- 我猜會遇到 [recitation error](https://ai.google.dev/gemini-api/docs/troubleshooting#recitation-issue) （[社群回報](https://issuetracker.google.com/issues/331677495?pli=1)），但不測不知道 [name=mrorz]


## 上次(06/15)小聚檢討

> https://g0v.hackmd.io/9IEjq11XSwCyES_VFn8JEg?view#%E5%B0%8F%E8%81%9A%E6%AA%A2%E8%A8%8E

- **場地**: 新的桌子排法。
- **報到率**: 約 50% (報名 30 人，報到 15 人)，建議維持 30 人報名上限。
- **時間**: 大多數人遲到，開場影片很重要。
- **時間分配**:
    - 評價環節可以再縮短。
      - 10 分鐘已經不能再短啦，包含下課 [name=mrorz]
    - 自我介紹環節很重要。
- **網路**: 現場網路順暢。

> 報名現況 https://cofacts.kktix.cc/events/cofactseditor48

## 小聚 rundown


- 週六早上
    - [x] KKTIX 行前通知：提醒時間、使用電腦而非手機
    > Hello 你好，
	>
	> 本週日就是 08 月 17 日查核志工培訓囉！
	>
	> 志工培訓需要大量查詢資料，請自備筆電 💻 與充電器 🔌 並帶著愉快的心情來參加。帶順手的平板也可以的！如果願意協助編修影片逐字稿，請自備耳機唷🎧！
	>
	> 🕒 時間：08/17（日）14:00 - 17:00
	> 📍 地點：新北市青年局青職基地2樓 / 新北市板橋區民權路170號2樓(近板橋捷運站)
	> 
	> 費用全免，會很準時開始。若不克前往，記得取消報名 :)
	> 
	> Cofacts 真的假的 查核協作 VIP 臉書社團在這裡 👉 https://www.facebook.com/groups/cofacts
	> Cofacts 真的假的 查核協作 Discord 在這裡 👉  https://cofacts.tw/discord
	> 說你會來查核小聚優先加入 ＝Ｄ
	> 
	> 感謝你的閱讀。
	>
	> 那麼明天見囉😊
	>
	> 比鄰敬上
    - [x] 開場使用材料更新：https://docs.google.com/presentation/d/1N9DxoN1NuxdtQILkcV67y_q8EM8CJF5GhoYLcCKFpAc/edit [name=mrorz]
	- [x] 準備 Slido `#cofacts`
		- [x] 放投影片網址
- 當日準備 / 攜帶
    - [ ] 樓下用的標語 - bil
    - [x] 貼紙 - orz, bil
    - [x] 黏土 - orz
    - [ ] 手板 - bil
    - [ ] 講義 - bil
    - [ ] 一次性杯子 - bil
    - [ ] 延長線 - bil / mrorz
        - 比鄰有三條
    - [x] Wifi 機 - mrorz
        - [x] rt-ax57 go
        - [x] 電源線
    - [x] 多帶一條 type-c 公公線 for dongle 的電
    - ~~[ ] 備用 wifi 機 [name=nonumpa]~~ 人少不用
- 13:00 - 場佈 [排法](https://docs.google.com/drawings/d/1yyAbWFmCC16Ur0lEf7m3szZVZ7en1rSpXx8BHlyrcN0/edit)
  - 桌子一邊 4 張椅子
  - 工人先把下面兩張桌子佔起來 + 移走椅子，參與者自然就會坐到螢幕前
  - [ ] 簽到（問飲料）
  - [ ] 排桌子椅子 
  - [ ] 投影位置？
  - [ ] 麥克風
  - [ ] 延長線佈置
  - [ ] 門口黏引導牌
  - [ ] WIFI
      - [ ] 佈機，手機 USB 選擇網路分享，等待白燈亮
      - [ ] 用 ASUS Device Discovery 確認可連線到 ASUS
  - [ ] 投影的電腦用 google chrome 開好
    - [ ] Google Chrome tab: [投影片](https://docs.google.com/presentation/d/1N9DxoN1NuxdtQILkcV67y_q8EM8CJF5GhoYLcCKFpAc/edit)
    - [ ] Google Chrome tab: [Bignum](https://cofacts.github.io/community-builder/#/bignum/setup)
- [ ] browser tabs
    - [ ] Google Chrome tab: [KKTIX](https://cofacts.kktix.cc/events/cofactseditor47)
    - [ ] Google Chrome tab: [Slido admin](https://admin.sli.do/event/rFQZd27cVvgEMyJAgv4BqT/polls)
    - [ ] Google Chrome tab: [Slido](https://wall.sli.do/event/rFQZd27cVvgEMyJAgv4BqT/?section=215e56d0-a002-4b7e-9bf0-c58acbacc9bf)
    - [ ] Google Chrome tab: [開場影片](https://www.youtube.com/playlist?list=PLz8KCDL90tNWn16J2xBzl53imUiDbNOzs)
    - [ ] BGM
    - [ ] Analytics
- 14:00 - 14:20 開場
    - 放[長影片](https://www.youtube.com/playlist?list=PLz8KCDL90tNWn16J2xBzl53imUiDbNOzs) 8min
    - 場地、Slido、Cofacts 機器人系統簡介
- 14:20 - 14:40：引導註冊網站、介紹評價現有回應
- 14:40 - 14:50：實作評價
    - 讓大家從網站找訊息按讚
- 14:50 - 15:10 介紹補充資訊
- 15:10 - 15:40 實作補充資訊、自我介紹、休息
    - 閒聊「看到覺得最好的回應、覺得哪裡好」
- 15:40 - 16:10：介紹撰寫新回應
- 16:10 - 16:40：實作撰寫新回應
    - 大家從網站挑選「一篇」覺得最有興趣的回
- 16:40 - 17:00 介紹 RSS、社群、合照

