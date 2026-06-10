# 20260616 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：
- 線上出席：
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

### url-resolver
- [ ] nonumpa 會對優化項目進行 benchmark
- [ ] Johnson 會 review 已 ready 的 PR

### COSCUP
- [ ] nonumpa 準備 URL resolver 的分享內容
- [ ] yutin 準備多媒體檢索的分享內容

### AI 修正
- [ ] 追蹤並修正影音訊息處理時，模型產生幻覺（腦補）或 `0:00:00` 時間戳的問題
- [ ] 為 AI writer prompt 新增長度與精簡準則
- [ ] 驗證 AI pipeline 有時會跳過 proofreader 的問題
- [ ] 為「自動 rename session 名稱」開票

### 維運
- [ ] 持續觀察 GCE server 的 Swap 用量
- [ ] 處理 `site-tw` Cloud Run 服務的記憶體高壓問題

## GCP Committed Use Discount（CUD）購買方案討論

### 背景

Google Cloud 提供 **Compute Flexible CUD**，一張 commitment 可同時涵蓋 Compute Engine、Cloud Run、GKE，以 Billing Account 為單位，不鎖 project 或 region。

### 目前費用基準（2026-05 實際）

| 項目 | 月費 | CUD 可涵蓋 |
|---|---|---|
| GCE VM（e2-highmem-4 RAM + CPU）| $155 | ✅ |
| Cloud Run CPU（生產 + staging）| $60 | ✅ |
| GCE Carrier Peering egress | $51 | ❌ |
| 其他（disk、Cloud SQL…）| ~$50 | ❌ |
| **可被 CUD 涵蓋的合計** | **~$188/mo（$0.26/hr）** | |

折扣率：GCE E2 為 3 年 46% / 1 年 28%；Cloud Run request-based 為 17%（1 年與 3 年相同）。

### 費用走勢假設

cofacts.ai 預計一年內取代 rumors-site（Cloud Run 生產站），屆時 eligible spend 降至約 **$0.22/hr**（GCE $155 + Cloud Run zh + staging $22）。

### 方案比較（3 年總費用，假設轉移發生於第 12 個月）

| 方案 | 年 1/月 | 年 2-3/月 | **3 年總計** | 比 Google 推薦省 |
|---|---|---|---|---|
| 不買 CUD | $190 | $161 | $6,132 | — |
| Google 推薦：$0.16/hr 全 3 年 | $117 | $117（浪費 $18）| $4,205 | — |
| $0.14/hr 3 年 only | $126 | $102 | $3,964 | +$241 |
| **$0.14/hr 3 年 + $0.02/hr 1 年** ✦ | **$121** | **$102** | **$3,908** | **+$297** |
| $0.13/hr 3 年 + $0.03/hr 1 年 | $123 | $101 | $3,910 | +$295 |

![](https://g0v.hackmd.io/_uploads/SyIwUzvZze.png)

![](https://g0v.hackmd.io/_uploads/rJg-dIGD-Ml.png)


✦ **建議方案**

### 建議方案說明：$0.14/hr 3 年 + $0.02/hr 1 年

- **$0.14/hr 3 年**：涵蓋轉移後的穩定基準用量（GCE 長期存在）
- **$0.02/hr 1 年**：涵蓋目前 Cloud Run 生產站的暫時性用量，到期後不續約
- Cloud Run request-based 的 CUD 折扣 1 年與 3 年相同（均為 17%），無需為即將縮減的用量 commit 3 年
- 即使 cofacts.ai 上線延遲，GCE VM 單獨即可吸收 $0.14/hr commitment，無浪費風險

### 待決事項

- [ ] 確認 cofacts.ai 取代 rumors-site 的預計時程
- [ ] 決定是否採用建議方案，由有 Billing Account 權限者於 GCP Console 購買