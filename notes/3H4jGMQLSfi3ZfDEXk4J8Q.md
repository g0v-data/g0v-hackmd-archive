---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20250722 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- 線上出席：
- 實體出席：bil, mrorz, nonumpa
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## 本次會議待追蹤項目 (由 2025/07/14 會議記錄結案)

*   **[bil]** IT Matters 社會影響力獎報名
    * 榮譽型，要寫 20p
    * 月底寫得出來就交
    * 公司版的未來大人物
*   **[mrorz]** 回信 joyharvest
    - 已完成
    - 對方已寫回應
    - [好榜樣](https://cofacts.tw/article/6F3eKpcBfs35m9MiHVHu)，未來類似 case 都應該朝此方向處理 [name=bil]
*   **[Johnson]** 資訊安全權限設定
    * 未完成
*   **CCPRIP - Analytics**: Opendata trend & LINE Bot usage 報表問題
    * 未完成  
*   **cofacts.ai**: Groundness Check agent 實作
    * 未完成 
*   **Claude Code Action**: 連接到 Vertex AI
    * 未完成 
*   **rumors-site PR #608**: [chingweih] 修復後下週測試
    * 尚未看到 
*   **url-resolver 重構**: See issue https://github.com/cofacts/rumors-api/issues/374
    * 之前直接用 puppeteer [name=nonumpa]
    * 如果要分 snapshot，一個是 URL preview 另一個是在背景執行 (archive snapshot)
    * URL preview: 需要 JS / 不需要 JS
    * Fetch --> Cloudflare puppeteer
    * 有的 URL 是 PDF，archivebox 可能會處理，但應該不多 [name=mrorz]
      * PDF 在 LINE 上會有 preview 嗎？ [name=nonumpa]
    * TODO: 把討論更新到 issue comment 裡並附上本次會議連結
    * TODO: https://github.com/cofacts/rumors-api/issues/373 跟 https://github.com/cofacts/rumors-api/issues/374 重複啦，把其中一個 mark duplicate

## 來自 Discord 頻道

### general
- **日本 AI 不實訊息反制策略分享**
  - `Peter@g0v-tw` 分享了關於日本應對 AI 假訊息策略的文章：[洪耀南專欄：AI參一咖 日本選舉正被毒化--上報](https://www.upmedia.mg/news_info.php?Type=2&SerialNo=234823)

- **Cofacts API 使用討論**
  - 社群成員 `bestian@g0v-tw` 詢問是否能透過 API 從其他網站發送查核請求。
  - `mrorz@g0v-tw` 回應有 `CreateArticle` 的 API，但目前仍希望以 LINE 的訊息為主，待未來有更好的查核能力後再考慮擴大。

### github-activities
- **[cofacts/beta-ai] PR #3: feat: upgrade google-adk to v1.4.2**
  - `gemini-code-assist[bot]` 對此 PR 提出了多項 review comment，提醒 `google-adk` 版本跳升幅度大，需注意相容性並進行完整測試。
  - 此 PR 在 `MrOrz` review 後關閉。
  - PR 連結: https://github.com/cofacts/beta-ai/pull/3

- **[cofacts/rumors-site] PR #609: Feat: editor list markdown-like UX**
  - 新的 PR，旨在改善編輯器中列表的 Markdown 使用體驗。
  - `gemini-code-assist[bot]` 提供了程式碼 review，包含潛在的 race condition、效能優化建議，以及列表樣式偵測邏輯的修正。
  - PR 連結: https://github.com/cofacts/rumors-site/pull/609
  - We just wait [name=mrorz]

- **[cofacts/rumors-site] PR #608: feat: Show URL title in article list**
  - `MrOrz` 針對此 PR 提出 review，指出直接顯示 URL 可能導致排版過寬，建議限制顯示的 URL 數量或實作更緊湊的顯示方式。
  - `gemini-code-assist[bot]` 則點出程式碼中潛在的 crash 風險，因 `hyperlinks` prop 可能包含 `null` 值。
  - PR 連結: https://github.com/cofacts/rumors-site/pull/608
  - Action item: 直接 deploy 到 staging，下週試試看 [name=mrorz]

---

## LLM based Topic Classifier
- https://github.com/cofacts/worker/pull/1
- 有點 over-engineer?
    - 拆步驟一次處理很多 article 要做很多事，單一 article 要分類會簡單很多
    - batch processing 會花數分鐘到數小時不等（24hr 內完成），改 prompt 重測也很花時間
    - batch processing 可以享半價優惠，但本來分類的 cost 就不大
- 寫都寫了 vs 改寫到 rumors-api 直接呼叫？
    - 放在 rumors-api 之後又想改成 batch 怎麼辦 [name=nonumpa]
        - 難度在「改寫成 batch」本身，生出 prompt 的核心邏輯很好抽
    - 做實驗的話，一筆一筆打與 batch 誰快？不知道 [name=mrorz]
        - 一筆一筆打應該要 rate limit
        - batch 時間每次不同，三分鐘回來的時候比一筆一筆快
- 分數不對，如 title emoji 導致 ID 對不到 https://langfuse.cofacts.tw/project/cmc6kvvfg0003lr08sbchn986/traces/7c8b9eed-b2e1-4b77-8314-4b18a92461f4
    - 已經試著移除部分「AI only」category
    - Reason 應該放在 category 之前才有 CoT 之效
    - 再修改 bug、確認 benchmark 合理

## :calendar: Next meeting

- 小學校到 9/21，bil 課到 8 月中
- bil, mrorz, nonumpma 週一週二都可以
- 下次會議 7/29
- 8/18 恢復週一