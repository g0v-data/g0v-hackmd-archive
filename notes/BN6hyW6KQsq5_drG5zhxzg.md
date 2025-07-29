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
*   **[Johnson]** 資訊安全權限設定 - not yet
*   **CCPRIP - Analytics**: Opendata trend & LINE Bot usage 報表問題 - not yet
*   **cofacts.ai**: Groundness Check agent 實作 - 本次有更新
*   **Claude Code Action**: 連接到 Vertex AI - not yet, 先用 Jules 吧
*   **[nonumpa, mrorz]** LLM based Topic Classifier: 修復 bug 並確認 benchmark - not yet
*   **[mrorz]** url-resolver 重構: 更新 issue comment 並處理重複 issue
    * 已經 consolidate 到一張票：https://github.com/cofacts/rumors-api/issues/373

## :potable_water: Release pipeline

### :rocket: Staging

#### :globe_with_meridians: Site

https://github.com/cofacts/rumors-site/pull/609

- 測測看手機 / 電腦撰寫查核回應
- 測測看按 bullet point / number 是否符合預期

##### Release Blocker

##### 未竟項目

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

## 小聚籌備
08/17 (日) 2pm - 5 pm 
- OK: 
- 辦在青職基地
- [ ] 食物：
- [ ] 場地：新北市青年局青職基地
- [ ] 時間：13:00 擺桌子場佈
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
  - 推播日：08/03（7/29 設定）
  - 目標：雙北
- [ ] KKTIX: https://cofacts.kktix.cc/events/cofactseditor48
- [ ] 誰會來呢： 
- [ ] 記得帶：貼紙、不太環保杯 (bil)
- [ ] LINE 文案： Cofacts 真的假的 第 48 次志工查核工作坊需要你的加入，活動完全免費，（請自備電腦）06/15(日)下午，地點青職基地，最近的捷運站是捷運板橋站1號出口，連結內報名：https://cofacts.kktix.cc/events/cofactseditor48
- [ ] VOOM 發文
- [ ] FB 發文

