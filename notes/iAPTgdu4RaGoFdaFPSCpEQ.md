---
tags: cofacts, meeting note
GA: UA-98468513-3
---

下次會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- NPO Hub: bil, nonumpa, mrorz
- 線上出席：
- Gather Town: https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## 本次會議待追蹤項目

*   **謠言惑眾獎**: MyGoPen 會提供新的名單。
*   **大松檢討**: 九月考慮在高雄或台南舉辦面海松，希望邀請 OpenDream 工程師或設計師。
*   **beta.cofacts.ai**: staging machine 環境設定 (Cloudflare tunnel, Access)。
*   **Open165 重構**: Open165 重構相關 PR (Open165/worker #5, Open165/site #37) 已開啟，但尚未測試。
    *   Open165 TODOs: 將 DB schema 移動到 worker 管理、在 worker 中建立子 workflow、建立資料交換格式、Website display。
*   **小聚籌備 (06/15)**: 確認食物、投放目標設定 (06/03 推播，目標雙北)、KKTIX 活動頁面、LINE 文案、VOOM 發文、FB 發文、攜帶物品 (貼紙、不太環保杯)。


## 會前準備事項

### 自上次會議 (2025-05-19) 以來的重要更新與討論

```markdown
### Discord 訊息摘要 (2025-05-19 至 2025-05-26)

**General Channel (#general)**

*   **mglee@g0v-tw** 分享其新出版關於零時政府的書籍，其中有一章介紹 Cofacts，並表示要贈書。連結：https://www.books.com.tw/products/0011020156
*   **chewei 哲瑋@g0v-tw** 提醒 Cofacts 參與 5/25 大松時評估場地位置並填入專案位置圖。
*   NPO Hub 場地使用提醒 (電梯故障, 202 場地 booking)。
*   網站異常與攻擊事件討論 (Cloudflare 警報, 異常流量, WAF 設定調整, swap 滿導致 DB 重開)。
*   **mrorz@g0v-tw** 提到 Google Gemini 2.5 flash 模型值得測試。
*   **mrorz@g0v-tw** 指出 rumors-site 測試因 setup-node 版本舊而失敗。
*   **mrorz@g0v-tw** 分享 LINE 上的關稅計算詐騙訊息。
*   **mrorz@g0v-tw** 分享 Langfuse 上的 Hallucination 案例 (AI 認為台灣沒有 50 元硬幣)。
*   **mrorz@g0v-tw** 分享使用 Roo Code 撰寫 rumors-api PR 的經驗 (PR #365)。
*   討論 takedowns 中 reply 未被抓到問題及 error handling。
*   **mrorz@g0v-tw** 分享 OpenAI 新 audio models 但擔心影像處理問題。
*   **mrorz@g0v-tw** 回報 spam user (外送茶) 未被 LLM 抓出案例。
*   **chewei@g0v-tw** 分享印尼查核組織 MAFINDO，**chihao@g0v-tw** 和 **mrorz@g0v-tw** 回應其知名度，mrorz 補充 MAFINDO 與 Cekfalta 的連結及提到 Cofacts 的聲明稿。
*   **流星若風的烤肉屋@g0v-tw** 提出在機器人端套 LLM 修飾查證語氣的想法，mrorz 認為值得一試。

**Server alerts channel (#server-alerts)**

*   記錄了 cofacts.tw, line-bot.cofacts.tw, api.cofacts.tw 在不同時間點出現 Unhealthy 狀態的警報。

**Github activities channel (#github-activities)**

*   **Open165/worker**: 多個 PR 開啟與關閉，涉及 migrate 165 site sync to Cloudflare Workflows (PR #5), upgrade whoiser (PR #4), lint & format (PR #3), routes and whois endpoints (PR #2), upgrade deps (PR #1)。
*   **Open165/site**: 開啟 PR #37 "Migrate database update to Cloudflare Worker"，關閉 PR #32 "chore(LICENSE): change to AGPL"。有評論提到 Cloudflare Pages 部署狀態以及 Issue #33 "Fix daily update script" 的評論。
*   **cofacts/takedowns**: 多個 "Takedown spam user" PR 開啟與關閉 (PR #234, #233, #232, #231, #229, #228, #227, #225, #224, #223, #222, #221, #218, #217, #215, #216, #214, #213, #212)，部分標示 false positive。MrOrz 開啟 Issue #230 "feat: 將發文頻率納入自動下架 spam 偵測考量"，非umpa 關閉 PR #226 "feat: disable article detection since there are too many false positives"。
*   **cofacts/rumors-site**: MrOrz 開啟並關閉 Issue #604 "test github integration"。
*   **cofacts/rumors-line-bot**: MrOrz 發布 release/20250516，開啟並關閉 PR #408 "Update MgpAwardee.svelte" (涉及 MgpAwardee.svelte 更新)，coveralls 報告測試覆蓋率。
```
