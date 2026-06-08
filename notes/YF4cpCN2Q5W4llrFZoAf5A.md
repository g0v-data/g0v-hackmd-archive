# 20260609 會議記錄

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

### 小聚檢討
- [ ]

## 本週確認事項

## 本週大松成果

## Action items



# 2026/06/02 – 06/08 生產環境週報

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