# 20250826 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- 線上出席：
- 實體出席：
- https://meet.google.com/mrz-dgrd-pri
:::

## 本次會議待追蹤項目 (由 2025/08/19 會議記錄結案)

No update
*   **[Johnson]** 資訊安全權限設定
*   **CCPRIP - Analytics**: Opendata trend & LINE Bot usage 报表問題
*   **cofacts.ai**: Groundness Check agent 實作 (追蹤提案與文件)
*   **Claude Code Action**: 追蹤 Vertex AI service account 與其他 repo 的整合進度、credential issue (`https://github.com/cofacts/beta-ai/issues/6`)
*   **[nonumpa, mrorz]** LLM based Topic Classifier: 追蹤 bug 修復與 benchmark 結果
*   **[mrorz]** 確認 Johnson 家是否還有中文講義
    * 我忘記看了⋯⋯

Has updates 
*   **url-resolver update**: 追蹤 Gemini 實驗、unfurl 整合與結果融合，並修復記憶體問題


## CCPRIP
### [Infra] Service issue
>  - `Cofacts monitor 🚨@g0v-tw` 多次發出 api.cofacts.tw, cofacts.tw, line-bot.cofacts.tw 等服務不穩定的警告。
>  - `nonumpa` 回報服務在 2025-08-23 約 10:50 掛掉，13:30 恢復，但 linebot 需要手動重啟。


### [Comm] url context tool experiment result

> Gemini API URL context: https://ai.google.dev/gemini-api/docs/url-context

Conclusion

### [Comm] Youtube on Gemini experiment result

- Gemini API youtube support: https://ai.google.dev/gemini-api/docs/video-understanding#youtube
    - A feature since [March 2025](https://ai.google.dev/gemini-api/docs/changelog#03-12-2025)

#### Adopt this to Cofacts?
