# 20250916 會議記錄

:::info
- [所有會議記錄](https://gov.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：bil, Helen, mrorz
- 線上出席：
- https://meet.google.com/mrz-dgrd-pri
:::

## 上次會議待追蹤項目

### No Updates
*   **[Johnson]** 資訊安全權限設定
*   **CCPRIP - Analytics**: Opendata trend & LINE Bot usage 報表問題
*   **cofacts.ai**: Groundness Check agent 實作 (追蹤提案與文件)
*   **[nonumpa, mrorz]** LLM based Topic Classifier: 追蹤 bug 修復與 benchmark 結果

### Updates
*   **[mrorz]** 準備面海松要用的中文講義、Cofacts 傳單與貼紙。
    *   攜帶的十數張英文講義發光了（家裡還有）
*   **[mrorz]** 撰寫混合式 URL resolver 的設計文件 (Ref: [worker#2](https://github.com/cofacts/worker/issues/2))。
*   **[mrorz]** 著手進行 `cofacts/devops-manual` 的撰寫。
    *   要先把 env-files 移出去才能寫
*   **[mrorz]** 設定 cofacts-api 的 303 redirect。
    >  2025/9/13 1:52pm cofacts.g0v.tw / cofacts-api.g0v.tw 的 request 現在都會轉到 cofacts.tw domain 由 Cloudflare 管理囉
    > https://github.com/g0v/domain/pull/90
*   **[bil]** 準備十月小聚，預定小樹屋。


## 0914 downtime

- **服務不穩定**: 9/14 發生了服務不穩定的狀況，`url-resolver` 負載過高。重啟 `url-resolver` 及 API 後服務恢復正常。
    > nonumpa@g0v-tw: 我 9.18 的時候看 url resolver load 200%，先重啟 url resolver ，發現 api 還是連不上的，再重啟 api，就好了

db 17:26 左右出現 gc 的 log
db 剛好在 21:17 重啟
https://cloudlogging.app.goo.gl/1WSpg5rRY6ETY9HH9

### Linode
![](https://g0v.hackmd.io/_uploads/SJICDKEsle.png)

19:10 load 下降
19:40 load 又開始變高

## GitHub Activities

### [cofacts/beta-ai](https://github.com/cofacts/beta-ai)
- **New Issue**: [[AI] connect to VertexAiSessionService](https://github.com/cofacts/beta-ai/issues/9)
- **Discussion**: [[AI] Notes on Langfuse integration](https://github.com/cofacts/beta-ai/issues/6) - MrOrz initiated a discussion with Claude AI about integrating Langfuse into the ADK project.

### [cofacts/rumors-deploy](https://github.com/cofacts/rumors-deploy)
- **New Pull Request**: [Move all environment variables to dedicated env files](https://github.com/cofacts/rumors-deploy/pull/38) - To improve configuration management.

### [cofacts/takedowns](https://github.com/cofacts/takedowns)
- Several spam users were taken down.

## Communication

### Generative AI 小聚
https://docs.google.com/presentation/d/18NGr_DCACysX_yi3IhqRAIlWZ9uPFpsX4Ju2HGZKNF0/edit

### Legal Email

