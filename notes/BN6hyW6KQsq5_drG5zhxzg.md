---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20250729 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- 線上出席：
- 實體出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## 本次會議待追蹤項目 (由 2025/07/22 會議記錄結案)

*   **[bil]** IT Matters 社會影響力獎報名
*   **[Johnson]** 資訊安全權限設定
*   **CCPRIP - Analytics**: Opendata trend & LINE Bot usage 報表問題
*   **cofacts.ai**: Groundness Check agent 實作
*   **Claude Code Action**: 連接到 Vertex AI
*   **[mrorz]** rumors-site PR #608: deploy 到 staging，供下週測試
*   **[nonumpa, mrorz]** LLM based Topic Classifier: 修復 bug 並確認 benchmark
*   **[mrorz]** url-resolver 重構: 更新 issue comment 並處理重複 issue
    * 已經 consolidate 到一張票：https://github.com/cofacts/rumors-api/issues/373

## Github Activities

- cofacts/rumors-site **[PR #609: Feat: editor list markdown-like UX](https://github.com/cofacts/rumors-site/pull/609)**
- cofacts/beta-ai **[PR #4: Implement Cofacts AI Multi-Agent System for Fact-Checking](https://github.com/cofacts/beta-ai/pull/4)**
- cofacts/worker **[PR #1: feat: implement rumor classification workflow with OpenAI batch API](https://github.com/cofacts/worker/pull/1)**

## CCPRIP [Infra] 服務穩定性問題
- `mrorz` 於 7/24 及 7/28 回報 `url-resolver` 服務因記憶體問題造成網站和 LINE bot 數次倒站。
- Issue: https://github.com/cofacts/rumors-api/issues/373

### 2025/07/24 伺服器不穩定事件

*   **發生時間**: 警報約於 `07:49 UTC` 開始，影響範圍包含 `api.cofacts.tw`、`cofacts.tw` 及 `line-bot.cofacts.tw`。
*   **問題判斷**:
    *   `mrorz` 於 `08:34 UTC` 上線查看，判斷是 `url-resolver` 服務發生問題，導致 CPU loading 飆高。
*   **處理過程**:
    *   `mrorz` 於 `08:42 UTC` 左右重啟 (restart) `url-resolver` 服務。
    *   重啟後，伺服器負載緩慢下降，服務逐漸恢復。
*   **事件結束**:
    *   主要的服務中斷在 `url-resolver` 重啟後獲得解決。不過在約 `12:51 UTC` 時，`mrorz` 發現 `line-bot` 服務並未自動恢復，手動將其重啟。

### 2025/07/28 伺服器倒站事件

*   **發生時間**: 警報約於 `05:53 UTC` 開始，`mrorz` 於 `06:01 UTC` 確認網站與 LINE Bot 全面中斷。
*   **問題判斷**:
    *   `mrorz` 於 `06:05 UTC` 初步判斷，問題根源同樣是 `url-resolver` 服務，因記憶體（RAM）使用量超過 2GB 而卡死，連帶影響到 API 伺服器，導致請求超時 (timeout)。
*   **處理過程**:
    *   `mrorz` 於 `06:07 UTC` 重啟 `url-resolver` 服務。
    *   `06:17 UTC` 時，`mrorz` 進一步發現 API 伺服器雖然容器 (container) 仍在，但已無反應，因此執行 `docker-compose restart` 重啟 API 服務。
*   **事件結束**:
    *   `mrorz` 於 `06:22 UTC` 回報「全系統恢復」，服務回復正常。

## CCPRIP [Comm] Cofacts.ai

- https://beta.cofacts.ai/dev-ui/?app=cofacts_ai
- https://g0v.hackmd.io/mU8qi721RZeAQ9PDfj7XRA#Use-cases-and-usage
- Milestones & M0 plan
