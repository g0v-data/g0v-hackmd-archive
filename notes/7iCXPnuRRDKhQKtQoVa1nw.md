---
tags: cofacts,
---

# 20260515 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：
- 線上出席：
- 缺席：
- https://meet.google.com/mrz-dgrd-pri
:::

## 上週待辦

### GCE Migration
- [ ] 跑幾週看穩定度，決定是否要再把 tw site 也搬進 GCE
- [ ] 跑幾個月看實際用到的運算量，決定 GCP committed use discount 怎麼買比較划算

### cofacts.ai tickets
- [x] 將登入使用者的 userId 傳遞給 ADK 與 Langfuse feedback --> https://github.com/cofacts/ai/issues/47

### rumors-api tickets
- [ ] 移除 Twitter 登入功能


## cofacts.ai

> https://github.com/orgs/cofacts/projects/12
- Hybrid search 問題：
- Applying Auth (PR#51)
- Gemini Deep Research? https://drive.google.com/drive/folders/1o9JPEcEptV87y6A7r-T794ZmkfisvMRp
    - 我覺得酷的地方
        - 有結構化的 annotations 列出所有參考資料
        - 偶爾會出現不錯的 infographic
        - API 開得相當友善，很好做成 ADK 的 Long Running Function Tool
    - 我覺得不酷的地方
        - 每跑一次大概要花 10min up，成本 USD 3~5
        - 中途發現不妙也停不下來
        - grounding annotation 有 bug，雖有原文的 start / end 好像是錯的
        - grounding annotation 不會呈現網址和內容，需要系統自己解析，而每次又有接近百個網址要自己解析
    - 先繼續處理出處問題 https://github.com/cofacts/ai/pull/55
- 出處問題 https://docs.google.com/document/d/1sZ4jOsrZPvbJv4QjlMxgbqFsh_pTZNBRs-NbG-HU0rM/edit?tab=t.a8qyopr6sp5



## 主機維運與資安事件
- **Production Disk 升級**:
  - `cofacts-prod` 的開機硬碟已從 HDD (pd-standard) 升級至 SSD (pd-balanced)，停機時間約 10 分鐘。
  - 升級後，讀取延遲從 ~67ms 降至 ~0.9ms (快約 70 倍)。
- **防火牆誤擋事件 (2026/5/4–5/6)**:
  - 為應對 DDoS 攻擊而加嚴的防火牆設定 (Super Bot Fight Mode)，誤將合法的 API 存取 (如 rumors-site SSR) 判定為機器人並加以阻擋。
  - 已新增 WAF 規則`Allow automated access for API`來修復此問題，並計畫導入 Cloudflare One token 作為更根本的存取控制機制。

## GitHub 活動摘要

### cofacts/ai (AI 專案)
- **錯誤修正與功能新增**:
  - **防止 LLM 回應出現幻覺來源 (Hallucinated Sources)**: PR #55 透過移除 context 中的雜訊，並提供結構化的 JSON 格式來源，來確保 AI Agent 使用正確的查核來源。
  - **新增回報選項**: PR #54 新增了「資訊錯誤或過時」的回報選項，讓使用者能針對 AI 的幻覺或過時資訊提供回饋。
  - **對話列表與認證重構**:
    - PR #49 與 Issue #48 改善了對話列表 (sidebar)，包含根據最近使用時間排序、未讀訊息標示等。
    - Issue #53 討論並關閉了關於 Auth 機制重構的提案。
- **發布新版本**:
  - [release/20260509](https://github.com/cofacts/ai/releases/tag/release/20260509)

### cofacts/takedowns (下架處理)
- **垃圾訊息使用者處理**:
  - PR #298 處理了名為「王梔梔」的垃圾訊息使用者，並已完成下架。

## 伺服器狀態
- **DDoS 攻擊後續**: 5/5 伺服器出現了數次 HTTP timeout 與 429 (Too Many Requests) 的錯誤，可能與 DDoS 攻擊後的防禦設定有關。
- **維護期間服務中斷**: 5/6 晚間，由於進行主機硬碟升級，`api.cofacts.tw` 與 `line-bot.cofacts.tw` 等服務曾短暫中斷 (回報 530 錯誤)。


# Cofacts 伺服器週報 (2026/5/5 – 2026/5/14)

> 對比基準：上週 2026/4/29 – 2026/5/6

---

## GCE (cofacts-prod) 主機指標

| 日期 | CPU (min \| avg \| p95 \| max) | Mem (min \| avg \| p95 \| max) | Swap (min \| avg \| p95 \| max) | 備註 |
|------|-------------------------------|-------------------------------|--------------------------------|------|
| 05-06 | 11.9% \| 21.1% \| 28.4% \| 38.0% | 56.4% \| 64.6% \| 67.3% \| 71.5% | 0.0% \| 16.0% \| 31.4% \| 79.4% | 磁碟升級前 |
| 05-07 | 11.2% \| 20.8% \| 25.9% \| 37.1% | 56.1% \| 62.5% \| 66.1% \| 68.1% | 0.0% \| 28.9% \| 55.5% \| 73.7% | 升級過渡期 |
| 05-08 | 11.7% \| 21.4% \| 26.8% \| 43.2% | 49.8% \| 54.4% \| 57.3% \| 62.7% | **71.6% \| 91.0% \| 99.3% \| 100.0%** | **Swap 驟增** |
| 05-09 | 16.6% \| 29.7% \| 48.1% \| 73.0% | 50.3% \| 55.0% \| 59.0% \| 69.1% | 86.8% \| 96.2% \| 99.9% \| 100.0% | CPU 明顯拉升 |
| 05-10 | 18.3% \| **32.2%** \| **52.4%** \| **90.3%** | 50.1% \| 55.3% \| 59.0% \| 78.0% | 90.5% \| 99.1% \| 100.0% \| 100.0% | 當週 CPU 最高峰 |
| 05-11 | 17.0% \| 27.2% \| 35.7% \| 55.8% | 50.4% \| 54.7% \| 56.6% \| 78.2% | 96.1% \| 98.8% \| 99.9% \| 100.0% | 開始穩定 |
| 05-12 | 17.4% \| 25.7% \| 32.1% \| 44.1% | 50.9% \| 54.7% \| 57.4% \| 59.2% | 93.1% \| 96.7% \| 99.6% \| 100.0% | |
| 05-13 | 16.6% \| 23.1% \| 27.0% \| 37.5% | 50.8% \| 54.7% \| 56.5% \| 76.6% | 89.3% \| 96.2% \| 99.7% \| 100.0% | |
| 05-14 | 15.9% \| 25.0% \| 32.4% \| 47.4% | 51.5% \| 54.0% \| 55.6% \| 57.3% | 93.2% \| 97.5% \| 99.6% \| 99.9% | |

**上週同期（4/29–5/6）平均值：** CPU avg ~32–55% (受 5/4 防火牆相關影響飆高)、Mem avg ~62–64%、Swap avg 低 (<30%)

---

## GCE 重點觀察

### 🔴 Swap 接近滿載（最關鍵問題）

磁碟升級（5/7–5/8）重開後，Swap 從 <30% 暴增至 91%+，目前維持在 97% 左右（3.7/4.0 GB 已用）。**然而當前 RAM 仍有約 10GB free，不存在立即 OOM 風險。**

可能成因：Elasticsearch 重啟後 JVM heap 佔用從 ~19 GB 降至 ~15.5 GB，釋出的 RAM 未主動回收 Swap 中被置換出的頁面（Linux 預設行為）。若未來記憶體壓力回升，Swap 無緩衝空間將是風險點。

建議：執行 `swapoff -a && swapon -a` 主動清空 Swap（在離峰時段），確認是否能回到正常水位。

### 🟡 CPU 5/9–5/10 明顯拉升

CPU avg 從 ~21% 升至 32%，max 達 90%。Elasticsearch 和 `node /srv/www/server.js` 同步上升，對應防火牆誤擋解除（5/6 後）流量回補以及 cofacts-ai 流量爆衝（見下方）。5/11 後已逐漸回落至 23–25% avg，屬正常範圍。

### ✅ 記憶體整體改善

Mem 使用率從上週 62–64% 下降至本週 54–55%，原因是 Elasticsearch 重啟後 RSS 由 ~19 GB 降至 ~15.5 GB。RAM 壓力明顯降低。

---

## GCE 主要程序資源分析

| 程序 | 正常範圍 (avg CPU) | 穩定性 | 觀察 |
|------|-------------------|--------|------|
| Elasticsearch | 322K–532K µs/s | 中（std 29K–155K）| 5/9–5/10 大幅拉升，之後回落至 ~373K |
| `node server.js` (API) | 265K–427K µs/s | 中（std 18K–157K）| 同步於 ES；5/9–5/10 有尖峰 |
| `node build/index.js` | 131K–176K µs/s | 穩定（std <32K）| 正常 |
| `cloudflared` | 27K–36K µs/s | 穩定 | 正常 |
| `adk api_server` (cofacts-ai) | 2.6K–3.5K µs/s | 穩定（std <160）| 5/6 起新出現，逐漸趨穩 |

**上週同期 Elasticsearch avg：** 450K–560K µs/s（偏高，受 5/3–5/4 影響）。本週整體 CPU 較正常，但 5/9–5/10 為例外。

---

## Cloud Run 服務分析

### CPU 使用率

| 服務 | 正常範圍 (p50) | 穩定性 (p95/p99) | 觀察 |
|------|---------------|-----------------|------|
| site-tw | 0.06–0.12 cores | p99 ~0.95 | 穩定，接近 1 core 上限 |
| site-staging-tw | 0.01–0.03 cores | p99 最高 1.01 | 偶發尖峰 |
| cofacts-ai | ~0.015 cores | p99 ~0.44 | 穩定 |
| line-bot-en/ja | ~0.005 cores | p99 <0.37 | 低頻使用正常 |

### 記憶體使用率

| 服務 | 正常範圍 (p50) | 穩定性 | 觀察 |
|------|---------------|--------|------|
| site-tw | ~0.79 GB | p99 ~1.01 GB | **接近 1 GB 容器限制，持續滿載** |
| site-staging-tw | ~0.76–0.91 GB | p99 ~1.01 GB | 同上 |
| cofacts-ai | ~0.05 GB | p99 ~0.07 GB | 極低，非常健康 |
| line-bot-en/ja | ~0.33–0.34 GB | p99 ~0.35–0.36 GB | 穩定 |

**site-tw 記憶體持續在容器限制 (1 GB) 邊緣**，與上週相同，無改善。

### 網路流量（site-tw，每日輸出）

| 期間 | 日均流量 |
|------|---------|
| 上週正常 (4/29–5/3) | ~8.2–8.9 GB/天 |
| 防火牆誤擋期 (5/4–5/6) | 8.2 → 7.3 → **3.1 GB** (5/6 驟降) |
| 升級恢復後 (5/7–5/13) | ~6.6–7.2 GB/天 |

流量在防火牆修復後恢復，但仍低於上週水準約 15–20%，可能反映部分使用者行為改變或 Bot Fight Mode 仍在過濾部分請求。

### cofacts-ai 異常流量

5/9–5/10 網路輸出驟增（22.9 MB → 39.5 MB），對應當天 GCE CPU 尖峰，疑與新功能測試或使用量爆衝有關。5/13 部署新版後已恢復正常（5/14 僅 0.22 MB）。

---

## 本週事件影響小結

| 事件 | 時間 | 影響 | 狀態 |
|------|------|------|------|
| 防火牆誤擋 (Super Bot Fight Mode) | 5/4–5/6 | site-tw 流量 5/6 驟降至 3.1 GB，合法 SSR 存取被封鎖 | ✅ 已修復（WAF rule 加入） |
| Production Disk 升級 HDD→SSD | 5/7 | 停機 ~10 分鐘；ES RSS 從 19 GB 降至 15.5 GB；**Swap 異常升至 97%** | ⚠️ 待觀察（Swap 需主動清除） |
| CPU 尖峰 | 5/9–5/10 | avg 32%, max 90%，與流量回補和 cofacts-ai 活躍有關 | ✅ 已回落 |
| cofacts-ai 部署 | 5/13 | 新版本上線，流量穩定 | ✅ 正常 |

---

## 建議行動

1. **（高優先）清除 Swap**：在離峰時段執行 `swapoff -a && swapon -a`，確認 Swap 能正常回收。若無法清除，需排查是否有 memory leak。
2. **（中優先）site-tw 記憶體**：容器持續在 1 GB 邊緣，建議評估是否需調高 Cloud Run memory limit 或優化 SSR 記憶體用量。
3. **（持續追蹤）Cloudflare One token 導入**：作為防火牆誤擋的根本解法，取代 Bot Fight Mode 作為 API 存取控制。

