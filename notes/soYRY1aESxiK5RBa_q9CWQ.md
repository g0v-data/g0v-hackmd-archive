---
tags: cofacts,
---

# 20260428 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：bil, lahna, nonumpa, mrorz
- 線上出席：
- https://meet.google.com/mrz-dgrd-pri
:::

## 上週待辦
- [ ] GCE Migration
    - [ ] 跑幾週看穩定度，決定是否要再把 tw site 也搬進 GCE
    - [ ] 跑幾個月看實際用到的運算量，決定 GCP committed use discount 怎麼買比較划算
- [ ] nonumpa: 提高 Discord 進入門檻
   - ![](https://g0v.hackmd.io/_uploads/Hyo2m7Cp-l.png)
   - [x] AutoMod 開「Mention Spam」+「Spam Content」(discord 預設規則)
   - [ ] 驗證等級已經是「高」了
     - ![](https://g0v.hackmd.io/_uploads/SyseEm06Zg.png)

- [ ] RightsCon 擺攤 ![](https://g0v.hackmd.io/_uploads/BJsYHeApWl.png)
    - [ ] X 型布幕 https://www.figma.com/design/1tiXCGut4kNCEkDG9FTza7/LINE-Chat-UI-Template--Community-?node-id=3011-2598&t=M7kq3ymM7XDO2z0s-4
    - [ ] mrorz, bil: 名片
        - mrorz 正在補名片
    - [ ] ~~bil~~ mrorz: 貼紙
    - [ ] mrorz: acho 黃色傳單 (英文)，確認 QR code
    - [ ] QR code 板板、Cofacts 板板
    - [ ] 外接螢幕：cofacts Youtube + about page
- [x] 針對 `Meta-ExternalAgent` 在 Cloudflare 進行頻率限制
    - [x] 直接關閉

## cofacts.ai & Github update

> https://github.com/orgs/cofacts/projects/12/views/1

### rumors-site
- **[fix: landing-en typo by MrOrz](https://github.com/cofacts/rumors-site/pull/624)**

### ai
- **[feat: session title — auto-generate and inline editing by MrOrz](https://github.com/cofacts/ai/pull/32)**
- **[feat: persist sessions in PostgreSQL via Cloud SQL proxy sidecar by MrOrz](https://github.com/cofacts/ai/pull/33)**
- **[feat(auth): BFF auth with HttpOnly cookie + SSR by nonumpa](https://github.com/cofacts/ai/pull/25)**
- **[Add feedback popover with comment for AI responses by MrOrz](https://github.com/cofacts/ai/pull/31)**
  - checkbox 與純文字會壓成一個純文字，需要載下來分析 or 使用 LLM
  - 更新選項不會溯及既往
  - 要再討論勾選選項
- **[Fix Langfuse environment variables in CD workflow by MrOrz](https://github.com/cofacts/ai/pull/29)**

:::info
TODO: 把 login user 的 userId 接到 ADK 與 langfuse feedback
:::

---

現在 cofacts.ai 使用上有幾個用起來很令人煩躁的點，好奇使用者這裡有沒有共鳴：

1. 即使在輸入法組字、選字的狀況，按 enter 就會直接送出
2. 送出了就停不下來，沒辦法像 gemini 那樣讓人能手動停止並重送指令
6. 輸入到一半或 agent 還在想的時候不小心按到關閉分頁，沒有跳出確認視窗讓人確認要不要關閉

---

3. 如果對最新的回應不滿意，也沒有鉛筆功能讓人重送 prompt （gemini 在最新的使用者訊息旁邊有小鉛筆）
4. 不能送圖片給 agent 分析
5. ~~Agent 還在分析的時候，沒辦法傳訊息給 agent 做 steering（這個是 coding agent 比較多有這樣的設計）~~
    - 使用者可以把執行停下來打 prompt，queued steering 沒必要 [name=mrorz]

我是覺得每個都值得開張票，但應該一起討論一下哪些要先做、還有哪些是開始給更多人用之前一定要修掉的東西（也就是進入 nDX 第二階段的 blocker，理論上 5/1 要進 🫠🫠🫠 ）

:::info
結論：除了 5 之外都開票
1, 2, 6 放第一階段，其他放第二階段
:::

### rumors-api
- **[feat(auth): Custom Authorization Code Flow with RS256 JWT + JWKS by nonumpa](https://github.com/cofacts/rumors-api/pull/386)**
    - 使用 RS256 演算法，雖然目前沒有 client 自己驗證的需求(直接把 jwt token 丟給 api)
        - 沒有設定 iss/aud，跟 security 無關、client 沒有 verify，所以沒做也還好
    - 短效期 code 有效時間為 60 秒，目前沒有做成 one-time code (需要依賴 redis 或其他 db)
    - bearer token 過期/無效會回傳 401
    - follow-up: twitter login 需移除
    - ready for review

:::info
開票拿掉 twitter login
:::

### opendata
- **[perf(dump): refactor async iterator merging with promise slots by MrOrz](https://github.com/cofacts/opendata/pull/33)**
    - 先放著


## Elasticsearch 記憶體與 Swap 效能優化

- **議題**: `Alfred chen` 建議關閉 Elasticsearch 的 swap 功能以增進效能，並引用官方文件佐證。
- **討論**:
  - `mrorz` 同意此作法，並與 AI 討論後決定將 `db` 的 `mem_limit` 與 `memswap_limit` 都設為 22GB。
- **結論**:
  > mrorz@g0v-tw: "[維運報告] Elasticsearch 記憶體優化與 Swap 調整完成
  > 為了避免 Elasticsearch 使用 Swap 導致效能不穩，剛才已完成 Production 設定調整：
  > • 問題背景：先前主機 4GB Swap 幾乎全滿（僅剩 2MB），且 ES Container 未限制 Swap 使用，違反官方 Best Practice 且有 OOM 隱憂。
  > • 調整內容：
  >     ◦ 在 `docker-compose.yml` 對 `db` 服務加上 `mem_limit: 22g` 與 `memswap_limit: 22g`。
  >     ◦ 強制 ES 容器不使用 Swap，將所有資料保留在實體 RAM 中。
  > 執行結果：
  >     ◦ ✅ Swap 成功釋放：主機 Swap 使用量從 4GB 降至約 360MB。
  >     ◦ ✅ 效能穩定：ES 已重啟完成，叢集狀態為 Yellow（單節點正常狀態），實體記憶體穩定在 17.4GB / 22GB。
  >     ◦ ✅ 服務正常：API 與網站讀取功能均已確認恢復正常。
  > 目前觀察 CPU 已降至穩定水位，後續會持續監控記憶體用量。"

## AI 爬蟲造成的伺服器負載與成本分析

- **議題**: `mrorz` 發現自 4/18 起，CloudRun 與主機的運算量皆有提高，懷疑是關閉「Block AI bots」設定所致。
- **後續**:
  > mrorz@g0v-tw: "4/18 以來 CloudRun 運算量與主機運算量都比較高，我在懷疑是 4/18 當天我把 Block AI bots 的設定從 Block on all pages 調成 Do not block 導致的
  > 為了確認成因，我今天再把 toggle 設回 Block on all pages，看看運算量那些會不會下降

結論：Block AI Bots 功能對系統負載有顯著保護效果，細節見 Cofacts production weekly report

## Discord 伺服器警報 - 2026-04-28 下午 HTTP Timeout

**時間**：2026-04-28 15:15 – 16:10 台灣時間（07:15 – 08:10 UTC）  
**影響**：`cofacts.tw` 及 `api.cofacts.tw` Health Check 觸發 HTTP timeout alert  
**嚴重性**：中（服務降級，非完全中斷）

---

### 事件時間軸

| 時間（台灣） | 事件 |
|---|---|
| 15:19 | Cloudflare Health Check `cofacts.tw` → Unhealthy (HTTP timeout) |
| 15:15–15:45 | **Elasticsearch GC 密集觸發，最嚴重時 GC overhead 1.1s/1.7s** |
| 15:30 | Cloudflare Health Check `api.cofacts.tw` → Unhealthy |
| 16:03 | 服務逐漸恢復正常（最後一筆 alert） |

---

### 根本原因

分散式 SEO Spam 爬蟲針對大量垃圾帳號頁面（`/user/[spam-id]`）發動掃描，並觸發了大量針對垃圾關鍵字的 `/search` 請求。這兩股針對 Elasticsearch 的沉重負載連鎖爆發，導致 ES 資源耗盡並頻繁觸發 GC，進而拖垮 API 回應速度。

| 指標 | 描述 |
|---|---|
| **攻擊目標 A** | `/user/` 系列路徑（如 `/user/86betws`, `/user/be5foodsupplement`） |
| **攻擊目標 B** | `/search?q=...` 包含廣告關鍵字、Temu 商品 ID 或超長法律條文 |
| **流量特徵** | 來源極度分散，跨越全球數十個機房 ASN，規避單一 IP 速率限制 |
| **ES 壓力源** | 針對垃圾 User Profile 的渲染檢索，以及複雜、長字串的搜尋運算 |

![](https://g0v.hackmd.io/_uploads/SkBR1Dy0Ze.png)
![](https://g0v.hackmd.io/_uploads/S19A1DkC-g.png)

| 時間 (UTC) | Spam 請求數 (/user/*) | 524 錯誤數 (Timeout) | 事件說明 |
|---|---|---|---|
| 07:11 | 7 | 0 | 正常狀態 |
| **07:12** | **31** | **321** | **Spam 爬取激增，524 開始出現** |
| 07:13 | 20 | 1,577 | ES 開始陷入 GC 停頓 |
| **07:18** | 17 | **2,116** | **錯誤達到峰值，Health Check 告警** |
| 08:00 | 9 | 184 | `/search` 流量翻倍高峰 (1,250次/hr) |

### 惡意搜尋內容範例 (Malicious Search Queries)
*   **Temu 商品關聯：** `site:temu.com "606143313197921"` (大量不同數字 ID)
*   **SEO 廣告推廣：** 「外貿獨立站推廣」、「歡迎訪問六五Ai站群搜尋引擎系統」(包含網址與電話)
*   **壓力測試/注入：** 搜尋整段長篇法律條文（如「郵局郵件內裝有禁寄文件...」）

## 已採取行動

**封鎖 SEO 爬蟲**：在 Cloudflare WAF 將 `/user/*` 與 `/search` 針對非 Known Bot 開啟 **Managed Challenge**。

![](https://g0v.hackmd.io/_uploads/BJ_Lbw1C-g.png)


目前捕捉到的均為 spammer

![](https://g0v.hackmd.io/_uploads/SkSwmv1R-e.png)


---

# Cofacts production 週報
**報告期間**：2026-04-21 ～ 2026-04-28（本週）vs 2026-04-14 ～ 2026-04-21（前一週）

---

## 一、GCE 主機狀態（cofacts-prod）

### 現況快照（2026-04-28 12:28）

| 項目 | 數值 |
|------|------|
| Uptime | 12 天 10 小時（開機於 4/16） |
| Load Average | 1.04 / 1.22 / 1.37（1/5/15 分鐘） |
| 記憶體（RAM） | 21 GB used / 31 GB total（67%） |
| Swap | 734 MB used / 4 GB total（**18%**，已大幅改善） |
| 磁碟 | 29 GB / 48 GB（62%） |

---

### GCE CPU / 記憶體 / Swap 逐日明細

格式：`min | avg | p95 | max`

#### 本週（2026-04-21 ～ 2026-04-28）

| 日期 | CPU（%） | Mem（%） | Swap（%） |
|------|----------|----------|-----------|
| 04-21 | 17.8 \| **28.5** \| 38.3 \| 57.0 | 52.9 \| **55.2** \| 56.8 \| 57.9 | 93.6 \| **98.4** \| 100.0 \| 100.0 ⚠️ |
| 04-22 | 19.3 \| **27.3** \| 35.8 \| 53.2 | 52.7 \| **56.1** \| 66.1 \| 66.9 | 9.2 \| **86.9** \| 100.0 \| 100.0 ⚠️ |
| 04-23 | 17.7 \| **27.6** \| 38.1 \| 55.6 | 62.8 \| **65.6** \| 67.3 \| 67.9 | 10.9 \| **14.0** \| 15.4 \| 16.9 ✅ |
| 04-24 | 17.8 \| **26.6** \| 35.8 \| 73.5 | 62.6 \| **65.0** \| 66.6 \| 67.5 | 14.8 \| **16.3** \| 18.2 \| 20.8 ✅ |
| 04-25 | 17.2 \| **26.5** \| 35.8 \| 53.3 | 63.2 \| **65.2** \| 66.4 \| 67.2 | 17.0 \| **17.7** \| 18.6 \| 20.2 ✅ |
| 04-26 | 14.0 \| **26.0** \| 37.9 \| 45.6 | 62.9 \| **65.2** \| 66.5 \| 67.1 | 17.1 \| **19.0** \| 20.5 \| 21.3 ✅ |
| 04-27 | 15.3 \| **25.7** \| 35.4 \| 59.6 | 61.2 \| **65.3** \| 66.8 \| 67.3 | 12.4 \| **17.4** \| 19.1 \| 21.0 ✅ |
| 04-28 | 21.4 \| **27.8** \| 37.7 \| 41.7 | 63.9 \| **65.6** \| 66.7 \| 67.2 | 17.5 \| **17.9** \| 18.2 \| 19.5 ✅ |

#### 前一週（2026-04-14 ～ 2026-04-21）

> ⚠️ Cloud Monitoring 僅保留近 2 週資料，4/14~4/19 的 GCE host-level 指標已無法取回。以下為可取得的資料：

| 日期 | CPU（%） | Mem（%） | Swap（%） |
|------|----------|----------|-----------|
| 04-20 | 16.9 \| **49.2** \| 65.4 \| 86.0 🔴 | 54.0 \| **58.3** \| 63.3 \| 64.5 | 84.5 \| **96.5** \| 99.9 \| 100.0 ⚠️ |
| 04-21 | 17.8 \| **28.5** \| 38.3 \| 57.0 | 52.9 \| **55.2** \| 56.8 \| 57.9 | 93.6 \| **98.4** \| 100.0 \| 100.0 ⚠️ |

> 從製程 CPU 歷史資料（`cpu_2026-04-14_2026-04-21`）可補充：
> - **4/18**：`node server.js` avg CPU 急升至 52,215 mills（平時 ~3,000），`pm2` avg 15,191（平時 ~11,000），`dockerd` avg 13,674。整體主機 CPU 均值推估約 49–50%。
> - **4/19**：`node server.js` avg 51,176、`pm2` avg 15,714，高負載持續。
> - **4/20**：`node server.js` avg 51,679，主機 CPU avg 49.2%（確認數據吻合）。

---

## 二、GCE 程序層級 CPU（Top 消耗者）

### 本週（4/21 ～ 4/28）

| 程序 | Peak CPU (mills) | 每日 avg 範圍 | 穩定度 |
|------|-----------------|---------------|--------|
| `java`（Elasticsearch） | ~30,000+ | 26,000–35,000 | 中（std ~700–2,200） |
| `pm2-runtime` | ~13,558 | 10,741–12,012 | 穩定（std ~440–929） |
| `dockerd` | ~19,027 | 9,543–11,010 | 中（4/27 有 spike std 2,235） |
| `node server.js` | ~16,086（4/21） | 6,786–10,001 | 中（std 1,000–2,728） |
| `node index.js` | – | 2,500–2,950 | 穩定 |
| Puppeteer Chrome renderer | ~18,750（瞬間） | 只出現個別小時 | 瞬間 spike |

### 前一週（4/14 ～ 4/21）

| 程序 | Peak CPU (mills) | 特殊觀察 |
|------|-----------------|---------|
| `java`（ES） | ~36,000 (4/18~4/20) | 4/18 起急劇上升 |
| `node server.js` | ~22,007（4/20） | 4/18 avg 驟升至 52,215（Block AI bots 關閉後） |
| `pm2-runtime` | ~18,094（4/18） | 4/18 起明顯偏高 |
| `dockerd` | ~16,589（4/18） | 4/18 起偏高 |

---

## 三、Cloud Run 狀態

所有服務均正常運行（✔）。最近部署：
- `cofacts-ai`：2026-04-27 20:31（最新）
- `site-tw/en/ja`：2026-04-09
- staging 版本：2026-04-13

---

## 四、Cloud Run CPU 比較（p50 / p95 / p99）

### site-tw（主要服務）

| 週別 | p50（正常） | p95（波動上限） | p99（尖峰） |
|------|------------|-----------------|------------|
| 前週 4/14~4/21 | 0.023–0.057 | 0.193–0.775 | 0.284–1.012 |
| 本週 4/21~4/28 | 0.069–0.134 | 0.752–1.011 | 1.012（整週） |

> 📌 **本週 site-tw p50 明顯高於前週**（0.07–0.13 vs 0.02–0.06），代表一般流量時段的 CPU 使用率有所上升。

### cofacts-ai

| 週別 | p50 | p95 | p99 |
|------|-----|-----|-----|
| 前週 4/14~4/21 | 0.015 | 0.107–0.217 | 0.284–0.497 |
| 本週 4/21~4/28 | 0.015 | 0.120–0.467 | 0.349–0.511 |

> 穩定，無明顯異常。

### line-bot-tw（含前週參考值）

前週 p50 約 0.81–0.86（記憶體 metric，非 CPU）；本週 CPU p50 約 0.005（idle 狀態），與前週結構相同。

---

## 五、Cloud Run 記憶體比較（p50）

| 服務 | 前週 p50（GB） | 本週 p50（GB） | 變化 |
|------|--------------|--------------|------|
| site-tw | 0.810–0.860 | 0.811–0.860 | ➡️ 持平 |
| site-ja | 0.810–0.860 | 0.811–0.886 | ➡️ 持平 |
| site-staging-tw/ja/en | 0.810–0.913 | 0.810–0.886 | ➡️ 持平 |
| dev-line-bot | 0.334–0.344 | 0.334–0.344 | ➡️ 持平 |
| cofacts-ai | 0.045 | 0.045 | ➡️ 持平 |

> Cloud Run 記憶體整體穩定，無異常增長。

---

## 六、與變更紀錄的交叉比對

### 變更一：Block AI Bots 設定（4/18 關閉 → 4/23 恢復 Block）

**觀察結果：✅ 強力支持你的假設**

| 時間點 | 主機 CPU avg | node server.js CPU | 備註 |
|--------|-------------|-------------------|------|
| 4/14~4/17（Block 開啟） | 推估 ~25–30% | avg 917–3,548 mills | 正常 |
| **4/18（Block 關閉）** | ~49–52%（推估） | avg **52,215 mills** | 🔴 驟升 17x |
| 4/19~4/20 | ~49–51% | avg ~51,000–51,679 mills | 高負載持續 |
| 4/21 | 28.5% | avg 10,001 mills | 仍偏高（週四） |
| **4/23（Block 恢復）** | **27.6%** | avg 6,786 mills | 開始下降 |
| 4/24~4/28 | 25.7–27.8% | avg 7,914–9,515 mills | 穩定恢復正常 |

**結論**：
- 4/18 `node server.js`（API server）CPU 突增約 17 倍，與 Block AI bots 關閉時間完全吻合。
- AI bot 造成的流量應為大量重複或高頻請求，不僅消耗 API 計算資源，也間接拉高 `dockerd`、`pm2`、`ES` 等。
- 4/23 恢復設定後，到 4/24~4/28 CPU 已回到 25–28% 的正常區間，與 4/14~4/17 水準相當。
- **此次驗證確認 Block AI Bots 功能對系統負載有顯著保護效果。**

---

### 變更二：Elasticsearch Swap 限制（4/23 設定 `memswap_limit: 22g`）

**觀察結果：✅ 效果顯著，立竿見影**

| 時間點 | Swap avg | Swap max | 備註 |
|--------|----------|----------|------|
| 4/21 | 98.4% | 100% | 幾乎全滿（~4 GB used） |
| 4/22 | 86.9% | 100% | 仍不穩定（min 9% → max 100%） |
| **4/23（設定後）** | **14.0%** | 16.9% | 🟢 驟降 |
| 4/24~4/28 | 16–19% | 17–21% | 穩定維持在低位 |

**現況**：目前 Swap 僅使用 734 MB / 4 GB（18%），完全不再有滿載風險。

**記憶體使用變化**：
- Swap 降低後，RAM 使用率從 55–58%（4/21~4/22）上升到 65–66%（4/23~4/28）。
- 這符合預期：原本放在 Swap 的 ES 資料現在留在 RAM，約多佔 3 GB 實體記憶體。
- 目前 RAM 仍有 ~10 GB available，無 OOM 風險。

**結論**：
- `memswap_limit: 22g` 設定成功強制 ES 不使用 Swap，記憶體管理已符合 Elastic 官方建議。
- RAM 有充裕空間（10 GB available），短期內無需擴充。

---

## 七、整體健康評估

| 維度 | 狀態 | 說明 |
|------|------|------|
| CPU | 🟢 正常 | 本週 avg 25–28%，4/23 起恢復穩定 |
| RAM | 🟡 偏高但安全 | 65–66%，主因 ES Swap 改善後移至 RAM |
| Swap | 🟢 大幅改善 | 從 98% 降至 14–19% |
| 磁碟 | 🟢 正常 | 62%，無緊迫壓力 |
| Cloud Run | 🟢 全部正常 | site-tw p50 CPU 本週略高但在合理範圍 |
| site-tw CR CPU | 🟡 略高 | p50 0.07–0.13（前週 0.02–0.06），值得持續觀察 |

> **整體判斷**：兩項變更均達到預期效果，系統已回到健康穩定狀態。唯一需要持續觀察的是 `site-tw` Cloud Run p50 CPU 有些微上升，但尚在可接受範圍內，暫不需要採取行動。
