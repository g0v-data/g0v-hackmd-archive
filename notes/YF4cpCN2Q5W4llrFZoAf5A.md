# 20260609 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：bil, mrorz, nonumpa
- 線上出席：ggm
- https://meet.google.com/mrz-dgrd-pri
:::

## 上週待辦

### GCE Migration
- [ ] 跑幾週看穩定度，決定是否要再把 tw site 也搬進 GCE
- [ ] 跑幾個月看實際用到的運算量，決定 GCP committed use discount 怎麼買比較划算

### Kaggle
- [ ] 手動在 johnson 個人帳號上傳，並處理授權條款
- [ ] 研究自動化上傳
- [ ] 申請 Org 帳號


## 🗓️ Since last meeting

### 💬 General Discussions

- **mrorz@g0v-tw**:
  > 中午推播之後，[小聚報名](https://cofacts.kktix.cc/events/cofactseditor53)人數來到 18 了 🎉

### ⚙️ Server Health & Maintenance

- On 2026-06-02, **mrorz@g0v-tw** restarted the database to apply new RAM and swap settings.
- There were several health check alerts for `cofacts.tw`, `api.cofacts.tw`, and `line-bot.cofacts.tw` on 2026-06-06 and 2026-05-25, indicating "Unhealthy" status due to "Response code mismatch error" and "HTTP timeout occurred".

### 💻 GitHub Activities

- **New Pull Requests & Reviews in `cofacts/ai`**:
  - [fix: handle missing functionResponse.id during SSE streams](https://github.com/cofacts/ai/pull/86) 還在找原因
  - [refactor: chatCacheKey factory for TanStack Query chat cache key](https://github.com/cofacts/ai/pull/85)
  - [feat: display Google Search suggestion pills from investigator](https://github.com/cofacts/ai/pull/83)
- **New Release**:
  - A new release **[release/20260606](https://github.com/cofacts/ai/releases/tag/release/20260606)** was published for `cofacts/ai`.
  - Gemini API 改 Vertex AI (a.k.a enterprise agent platform)
      - local 需要 application default credential, production 時是使用 cofacts-ai 的 service account
      - 未來可以換 Vertex AI model garden 上的任何 model 來比較 performance
  - 設定 artifact store
      - local 是 in-memory storage
      - 未來使用者貼圖片進 session，就會繼續用 artifct store
- **New Issue**:
  - [Long multimodal runs hit ~300s request timeout with no final answer](https://github.com/cofacts/ai/issues/84)

## Cofacts.ai

> https://github.com/orgs/cofacts/projects/12/

![](https://g0v.hackmd.io/_uploads/SyW0e_HWfe.png)

- 兩天 AI 使用較多，一天 6USD
- 可再觀察用量

### url-resolver

computer use 的問題
- 給 gemini 的 prompt，可能 context 塞太多
- 和 cloudflare 無關

[ready] update deps
https://github.com/cofacts/url-resolver/pull/73

using cloudflare cdp
https://github.com/cofacts/url-resolver/pull/72

optimization
https://github.com/cofacts/url-resolver/pull/74
- extractStatic: 好像有另一個 library [name=mrorz]
- 會做 benchmark 看看實際效果 [name=nonumpa]

:::info
Johnson - review ready 的 PR
:::

討論
- dependency attack 
    - https://www.ossprey.com/blog/the-complete-teampcp-campaign
    - https://blog.huli.tw/2026/05/25/dive-into-npm-supply-chain-attack/
    - 新增 deps 時把版本鎖在一個月以前的 (npm install --before=2026-05-09)
- gemini-coding-assistant free 版本好像會下架

### 人事
- Scientist - Friday 10:00~11:00 綠線
- 資料建置工作小組
- UI/UX designer
    - Design system / components on pencil.dev or Penpot (migrate from Figma)
    - Cofacts.tw + cofacts.ai 融合之後的設計

### TODO

- 自動 rename session 名稱 --> LLM summarize user input，開票

## COSCUP

8/8, 8/9

https://pretalx.coscup.org/coscup-2026/talk/review/PKWSB3RSZPPGSVCNKNCZX3DNBCRZLCGV

- cofacts.ai 分享
- 不是只有帶風向的人能用 AI，查核者也該用
- AI: context + multi-agent 架構
- Context
    - URL resolver [name=nonumpa]
    - 多媒體檢索 [name=yutin]
- 分工 / 角色扮演來寫出能跨越同溫層的查核回應
    - 資訊：investigator / verifier 
    - 感受：proofreader
    - Writer 會調配順序
    - 目標：寫查核回應
- 人與 AI 的互動：挑一些酷的 Langfuse trace 來復盤
    - 人可以提供方向、sense、自己找的線索
    - AI 可以做情緒勞動、筆墨、機械性的查證與整理

## 小聚檢討

https://g0v.hackmd.io/DnfCeK1qR1ijXI9dEDMAew
- 報到率超高（幾乎都來了）
- 天氣
- 推播開門見山，避開開頭謠言：志工、免費、工作坊、參加
- ![](https://g0v.hackmd.io/_uploads/B1eboaKHWGe.png)
- 新桌椅擺放方式很棒 https://docs.google.com/drawings/d/1Xho1b6JtMrlBsJ5UGCDvcK6phxXnPLznj-pz7xQEG4g/edit ![](https://docs.google.com/drawings/d/e/2PACX-1vT4JtlvPFdcg5NLMZFmvFWIVvjIJ4jjOtJaH26-zR8fsHxYO-1bhY1PG-jDXBMmtJDJKB9sGIfePKYq/pub?w=943&h=652)
    - 未來要求不要開電視牆、使用投影機
    - 樓下的鐵桌很重，邊緣銳利
- 新教材 w/ cofacts.ai
- 樓下插座被封起來了，不希望我們用更多電
- 需要更多時間佈置
- wifi 不給力，需要 travel router 接 5G
    - 也有人用自己的


# 週會彙整：2026/6/2 – 6/9 使用狀況、Feedback 與 Prompt 迭代

## 1. 總覽數字（過去 7 天）

| 指標 | 數量 |
|---|---|
| Sessions | 61 |
| Traces（`invocation [cofacts_ai]`） | 71 |
| 使用者評分（`user-thumbs`） | 14 |

**Thumbs 分布**：👍 4　／　😐 1（中性 0）　／　👎 9

評分覆蓋率偏低（14/71 ≈ 20%），負評集中在 6/6，且幾乎全與**影音訊息處理**有關。系統 pipeline：orchestrator(writer) → investigator(搜尋) / verifier(看影音、查證) / proofreader_dpp/tpp/kmt(校稿)，全跑在 `gemini-3-flash-preview` / `gemini-3.1-flash-lite`。

---

## 2. Feedback 彙整（按主題）

### 🔴 A. 影音被「腦補 / 複誦播放內容」— 最大痛點（6/6 共 7 則負評）
| 時間 (UTC) | 評分 | 留言 |
|---|---|---|
| 6/6 10:00 | 👎 | 莫名回傳自創影片台詞 |
| 6/6 10:01 | 👎 | 故障 |
| 6/6 10:02 | 👎 | 最一開始有亂碼 |
| 6/6 10:02 | 👎 | 亂碼 |
| 6/6 18:56 | 👎 | 一直輸出 0:00 然後也沒真的去呼叫 proof reader |
| 6/6 19:02 | 👎 | 00 是什麼 |
| 6/6 19:03 | 👎 | 莫名的 0:00:00 |

➡️ 症狀一致：orchestrator 拿到時序媒體後**複誦/腦補影片台詞、吐出 `0:00:00` 時間戳、亂碼**，而且有時 pipeline 沒跑完（沒呼叫 proofreader）。

### 🔴 B. 出處查證不實（6/7 共 2 則）
| 時間 (UTC) | 評分 | 留言 |
|---|---|---|
| 6/7 08:40 | 👎 | ☑ 篇幅過長 |
| 6/7 08:47 | 👎 | ☑ 回應文字與出處不符／原文訊息未提及 21 萬之訊息 |

### 🟢 C. 正面回饋 — 出處與文筆獲肯定
| 時間 (UTC) | 評分 | 留言 |
|---|---|---|
| 6/6 10:30 | 👍 | ☑出處精準 ☑具說服力 ☑語氣適合／「寫得很好耶！出處也很準！」 |
| 6/7 06:49 | 👍 | ☑ 出處精準 |
| 6/7 08:08 | 👍 | （無留言） |
| 6/8 14:41 | 👍 | ☑ 出處精準 |

「出處精準」被肯定 3 次 — 直接印證下方 Theme 1 的 source-grounding 改動見效。

---

## 3. Prompt 迭代時間軸（本週兩大主軸）

### Theme 1 ── Writer 編排紀律 + 出處查證嚴謹度（6/1，對應 Feedback B/C）

| Commit | 內容 |
|---|---|
| `7931d10` | 新增 **Working Discipline**：一次一個 tool、先看再查、維護 editorial-constraints 清單、draft 前重印 checklist、**沒被 verifier ✓ 的事實/數字不得進稿** |
| `57934a8` | 放寬：允許平行跑 tool，**唯一硬規則改成「`draft_factcheck_response` 不得與其他 tool 同回合」** |
| `107743a` | 把 Working Discipline 併入單一 Orchestration Process，降低指令重複/衝突 |
| `0cb1a8a` | `grounding_supports` 從「證據」**降級為雜訊提示**（Google grounding 會 over-attribute，一句話常被掛 4–9 個來源） |
| `adf784d` | **直接移除 `grounding_supports`**；明訂「investigator 只 DISCOVER 候選來源，verifier 才 CONFIRM」 |
| `b9d73d7` | editorial constraints 範例改為通用描述（避免被特定例子帶偏） |

➡️ 核心轉變：**「來源清單長 ≠ 知道哪句話有哪個出處」**，最終引用一律只能來自 verifier 標 ✓ 的 URL。這正是「出處精準」好評的來源；但 6/7 的「回應文字與出處不符」顯示**仍有漏網**，verifier-confirm 規則尚未 100% 落實。

### Theme 2 ── 影音媒體改走 Vertex AI 原生 gs:// + 逐字稿分工（6/3–6/6，對應 Feedback A）

| Commit | 內容 |
|---|---|
| `8166f48`→`1c3cd7a`→`07cd1b3`→`4d3041c` | 改用 **Vertex AI 原生 `gs://`** 把 Cofacts 媒體餵給 Gemini（含過期 signed URL 重簽） |
| **`02b63f3`** ⭐ | **關鍵 prompt 改動**：`_WRITER_INJECTED_TYPES = {"IMAGE"}` — **VIDEO/AUDIO 不再注入 writer**（理由註解明寫：時序媒體會讓 orchestrator「敘述/虛構播放內容而非編排」）。改為 writer 讀逐字稿、verifier 負責看影音並回傳**逐條、編號、不可合併的 claim inventory** |
| `71311b5`→`617a090` | writer 把 article 的 `attachmentUrl`(`gs://`) 原封不動交給 verifier（禁止自己重組 storage URL / 傳網頁 URL 害 verifier crash） |
| `fc8ab69` | 即使逐字稿看似完整，**VIDEO/AUDIO 仍強制至少一次 verifier 實際觀看**（補視覺層：畫面文字、logo、人物） |

➡️ 這整批就是針對「自創影片台詞 / 0:00:00 / 亂碼」的根因修復——把會讓 orchestrator 失控的時序媒體從它手上拿掉。

---

## 4. 因果對照與待追蹤（建議週會討論）

- ⚠️ **影音腦補可能尚未根治**：6/6 下午（18:56–19:03，晚於當天早上的 `02b63f3`/`fc8ab69` 修復）仍連續收到 3 則「0:00:00」負評。代表 `IMAGE-only` 注入 + verifier 分工**還沒完全擋掉 orchestrator 吐時間戳**，需追進這幾個 trace 確認是新版還是舊版部署。
- ⚠️ **「篇幅過長」(6/7) 目前沒有對應的 prompt 改動** — writer 的輸出長度沒有任何 instruction 約束，建議補一條長度/精簡準則。
- ⚠️ **「沒呼叫 proofreader」**：Working Discipline 雖規範「draft 前要完成 proofreader review」，但實際 trace 仍有跳過 → 編排紀律的遵循度待驗證。
- ⚠️ **「回應文字與出處不符」**：verifier-confirmed-only 規則已寫死，仍出現不符，建議納入 LLM-as-judge 自動評測（出處一致性）追蹤。
- ✅ **出處精準（×3 好評）**：Theme 1 的 grounding 改革成效明確，可作為本週亮點。


# 2026/06/02 – 06/08 Production 環境週報

---

**GCE 伺服器 (cofacts-prod)**

| 日期  | CPU (avg/max) | Mem (avg/max) | Swap (avg/max) |
| ----- | ------------- | ------------- | -------------- |
| 06/02 | 24% / 40%     | 60% / 70%     | 69% / 100%     |
| 06/03 | 21% / 33%     | 66% / 78%     | 22% / 26%      |
| 06/04 | 40% / 73%     | 66% / 85%     | 34% / 38%      |
| 06/05 | 60% / 86%     | 69% / 83%     | 35% / 39%      |
| 06/06 | 63% / 95%     | 69% / 84%     | 36% / 38%      |
| 06/07 | 55% / 78%     | 69% / 86%     | 42% / 50%      |
| 06/08 | 55% / 78%     | 68% / 89%     | 48% / 50%      |

目前狀態：磁碟 67%、RAM 21/31 GB、Swap 2/4 GB、uptime 33 天。

**CPU 上升原因：** Elasticsearch 與 API server (node) 的 CPU 消耗從 06/04 起顯著上升，Elasticsearch 從原本約 40% 單核升至 06/06 的 124% 單核。

**Swap 說明：**
- 06/02 曾短暫達 100%，之後恢復正常
- 06/02 23:22 已為 Elasticsearch 設定 memory lock（`mlockall: true` 確認生效）
- Elasticsearch 目前仍有約 360 MB 殘留在 swap，為設定前已換出的舊 pages，不影響運作
- Swap 目前最大用量來自 `python main.py`（cofacts-ai，約 611 MB），其次為 redis（84 MB）
- Swap 整體有緩慢上升趨勢（06/08 達 48%），持續觀察中

---

**Cloud Run 服務**

| 服務                | 狀態          | 備註                                    |
| ------------------- | ------------- | --------------------------------------- |
| site-tw             | ⚠️ 記憶體高壓 | p50 記憶體 80%+，p99 超過分配上限       |
| cofacts-ai          | ✅ 正常       | 06/07 部署新版本（改用 python main.py） |
| line-bot (tw/en/ja) | ✅ 正常       | 資源穩定                                |
| site-staging 系列   | ✅ 正常       | 記憶體用量偏高但穩定                    |

所有 Cloud Run 服務目前皆為運作中（✔）。