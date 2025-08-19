# 20250819 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- 線上出席：
- 實體出席：
- https://meet.google.com/mrz-dgrd-pri
:::

## 本次會議待追蹤項目 (由 2025/08/12 會議記錄結案)

*   **[Johnson]** 資訊安全權限設定
*   **CCPRIP - Analytics**: Opendata trend & LINE Bot usage 報表問題
*   **cofacts.ai**: Groundness Check agent 實作 (追蹤提案與文件)
    *   安裝完畢：
    	* 	cofacts/rumors-site
		* 	cofacts/rumors-line-bot
		* 	cofacts/takedowns
		* 	cofacts/rumors-db
		* 	cofacts/collab-server
		* 	cofacts/community-builder
		* 	cofacts/opendata
		* 	Open165/site
		* 	Open165/worker
    *   https://github.com/cofacts/beta-ai/issues/6 遇到會自曝 credential 的問題，需要 gitignore
*   **Claude Code Action**: 追蹤 Vertex AI service account 與其他 repo 的整合進度
*   **[nonumpa, mrorz]** LLM based Topic Classifier: 追蹤 bug 修復與 benchmark 結果
*   **url-resolver update**: 追蹤 Gemini 實驗、unfurl 整合與結果融合
*   **小聚檢討**: 檢討 08/17 小聚成效與回饋

## 小聚檢討

> 小松果：https://hackmd.io/18TlZVPxRhGydowu_nknjg

- 中文講義沒了，確認 Johnson 家是否還有貨 [name=mrorz]

## 上週重點摘要

*   **新功能請求**:
    *   使用者 Momoka 詢問如何在回應中上傳圖片，mrorz 回覆目前沒有這個功能，建議可以先上傳到其他圖床再貼連結。
*   Claude Code Action 
*   **系統狀況**:
    *   過去一週有多個時間點服務（cofacts.tw, api, line-bot）發生不穩或中斷的狀況，mrorz 已處理。


## CCPRIP


### [Infra] Downtimes

#### 2025-08-17 01:40 UTC

- cofacts.tw 和 api.cofacts.tw 服務中斷。
- MrOrz 於 02:27 UTC 開始處理
    > mrorz@g0v-tw: 網站好像死翹翹但伺服器看起來很好

#### 2025-08-18 00:00 UTC

- line-bot.cofacts.tw, api.cofacts.tw, cofacts.tw 服務中斷。
- MrOrz 於 00:46 UTC 開始處理
    > mrorz@g0v-tw: 又倒站

#### 2025-08-18 02:23 UTC

- line-bot.cofacts.tw, api.cofacts.tw, cofacts.tw 服務中斷。
- MrOrz 於 02:25 UTC 開始處理
    > mrorz@g0v-tw: 又倒站 orz

#### 2025-08-18 07:50 UTC

- api.cofacts.tw, cofacts.tw, line-bot.cofacts.tw 服務中斷。
- MrOrz 於 07:53 UTC 開始處理
    > mrorz@g0v-tw: 今天是怎樣 orz

#### 2025-08-18 14:07 UTC

- line-bot.cofacts.tw, cofacts.tw, api.cofacts.tw 服務中斷。
- MrOrz 於 18:38 UTC 發布更新
    > mrorz@g0v-tw: 10:33 的時候看起來大部分服務都復活，但 line bot 一直在 exit 狀態
    > 現在我才手動開啟

#### 2025-08-19 05:08 UTC

- cofacts.tw, line-bot.cofacts.tw, api.cofacts.tw 服務中斷。
- MrOrz 於 05:24 UTC 開始處理
    > mrorz@g0v-tw: api 爆炸




