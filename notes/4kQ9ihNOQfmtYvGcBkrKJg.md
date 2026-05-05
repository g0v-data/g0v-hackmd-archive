# 20260505 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：mrorz, bil, lahna, nonumpa
- 線上出席：
- https://meet.google.com/mrz-dgrd-pri
:::

## 上週待辦

### GCE Migration
- [ ] 跑幾週看穩定度，決定是否要再把 tw site 也搬進 GCE
- [ ] 跑幾個月看實際用到的運算量，決定 GCP committed use discount 怎麼買比較划算

### ~~RightsCon 擺攤~~

> [RightsCon cancelled](https://www.rightscon.org/rc26-statement/)

- [x] X 型布幕 https://www.figma.com/design/1tiXCGut4kNCEkDG9FTza7/LINE-Chat-UI-Template--Community-?node-id=3011-2598&t=M7kq3ymM7XDO2z0s-4 ![](https://g0v.hackmd.io/_uploads/HJgsl_SwAbg.png =x300)
- [x] mrorz, bil: 名片
    - mrorz 正在補名片
- [ ] mrorz: 貼紙
- [ ] mrorz: acho 黃色傳單 (英文)，確認 QR code
- [ ] QR code 板板、Cofacts 板板
- [ ] 外接螢幕：cofacts Youtube + about page

### cofacts.ai tickets
- [ ] 將登入使用者的 userId 傳遞給 ADK 與 Langfuse feedback



### rumors-api tickets
- [ ] 移除 Twitter 登入功能

# Cofacts.ai update

> https://github.com/orgs/cofacts/projects/12

| # | 標題 | Phase |
|---|------|-------|
| [#35](https://github.com/cofacts/ai/issues/35) | Fix: IME 組字期間按 Enter 不應送出訊息 | Phase 1 |
| [#36](https://github.com/cofacts/ai/issues/36) | Feat: 新增停止 agent 回應的按鈕 | Phase 1 |
| [#37](https://github.com/cofacts/ai/issues/37) | Feat: 關閉分頁前顯示確認提示 | Phase 1 |
| [#38](https://github.com/cofacts/ai/issues/38) | Feat: 最後一則使用者訊息可編輯重送（鉛筆功能） | Phase 2 |
| [#39](https://github.com/cofacts/ai/issues/39) | Feat: 支援圖片輸入 | Phase 2



# 上次會議至今的重點事件與討論

## 伺服器狀態

- **`server-alerts`**: 在 5/4 到 5/5 期間，Cloudflare 發出了多次關於 `cofacts.tw`、`line-bot.cofacts.tw` 和 `api.cofacts.tw` 的服務不健康警示，原因包含 HTTP timeout、502、429、530 等錯誤，推測與 DDoS 攻擊有關。
- **SEO Spam**: 在 4/29，`mrorz` 提到前一日的伺服器不穩定，疑似是 SEO spam 造成，目前已透過 managed challenge 處理。


## GitHub 開發進度

### rumors-api

- **[PR #388: [draft] Vector search](https://github.com/cofacts/rumors-api/pull/388)**:
  - `yutin1987` 開了新的 PR，正在進行向量搜尋功能的開發。
  - `gemini-code-assist` bot 提出了一些程式碼建議。

- **[PR #386: feat(auth): Custom Authorization Code Flow with RS256 JWT + JWKS](https://github.com/cofacts/rumors-api/pull/386)**:
  - 這個 PR 已經部署到 staging 環境，並且 `MrOrz` 已確認功能正常。
  - Production: `JWT_PRIVATE_KEY`, `JWT_PUBLIC_KEY` added to production env & staging env

### rumors-db

- **[PR #78: [draft] feat: add embeddings field for hybrid search](https://github.com/cofacts/rumors-db/pull/78)**:
  - `yutin1987` 新增了 `embeddings` 欄位以支援混合搜尋。

### ai

- **[Release release/20260504](https://github.com/cofacts/ai/releases/tag/release/20260504)**:
  - `MrOrz` 發布了新版本。

- **[PR #46: feat: warn before leaving with unsaved input or active stream](https://github.com/cofacts/ai/pull/46)**:
  - `MrOrz` 新增了在關閉分頁前，若有未儲存的輸入或正在進行的回應，會跳出提示的功能。
  - server function env var 會讀不到 [name=nonumpa]
      - 好像是因為 client side 也讀到 env var
      - 可能需要阻止 client 去讀 server，[`*.server.ts` 檔名](https://tanstack.com/start/latest/docs/framework/react/guide/execution-model#marking-whole-files-server--or-client-only)可能有用

- **[PR #43: Hide mock right side panel and mobile FAB](https://github.com/cofacts/ai/pull/43)**:
  - 隱藏了右側面板的 UI。

:::success
開一張票追蹤 https://github.com/cofacts/ai/pull/25 login 機制 merge 後要做：
- 要把 user ID 放進 ADK endpoint，使大家的 side panel 不同
- Langfuse feedback 要記錄 user id
- Tanstack 的 server function / API endpoint 確保沒有登入就不能和 bot 聊天
    - 沒登入就不要顯示聊天介面
:::

:::success
問開發者是否需要 Claude
https://docs.cloud.google.com/identity/docs/editions
:::

### devops

- **[PR #6: docs: document Cloud SQL setup for cofacts.ai ADK sessions](https://github.com/cofacts/devops/pull/6)**:
  - `gemini-code-assist` bot 建議在文件中補充 Cloud SQL Proxy 的 log 查看指令以及 IAM database authentication 的使用者名稱說明。

- https://github.com/cofacts/devops/pull/7




## 小聚籌辦

- 挑時間跟挑場地，青職基地都借滿了
https://thehapp.com/space/624
新北市板橋區中山路一段 265 巷 2 弄 1 號 2 樓 - 201 房
https://thehapp.com/space/574
臺北市中正區忠孝西路一段50號 B3樓-B306房
- Candidate: 6/7 (日)、6/14 (日)

- 週六早上
    - [x] KKTIX 行前通知：提醒時間、使用電腦而非手機
  > Hello 你好，
	>
	> 本週日就是 6 月 7 日查核志工培訓囉！
	>
	> 志工培訓需要大量查詢資料，請自備筆電 💻 與充電器 🔌 並帶著愉快的心情來參加。帶順手的平板也可以的！如果願意協助編修影片逐字稿，請自備耳機唷🎧！ 另外這次的活動會有瑞士新蘇黎世報的紀錄片採訪進行一定距離外的活動紀錄，不願意入鏡是絕對沒有問題的，我們尊重每個人的肖像權。
	>
	> 🕒 時間：06/07（日）14:00 - 17:00
	> 📍 地點：新北市青年局青職基地2樓 / 新北市板橋區民權路170號2樓(近板橋捷運站)
	> 
	> 費用全免，會很準時開始。若不克前往，記得取消報名 :)
	> 
	> Cofacts 真的假的 查核協作 VIP 臉書社團在這裡 👉 https://www.facebook.com/groups/cofacts
	> Cofacts 真的假的 查核協作 Discord 在這裡 👉  https://cofacts.tw/discord
	> 說你會來查核小聚優先加入 ＝Ｄ
	> 
	> 感謝你的閱讀。
	>
	> 那麼明天見囉😊
	>
	> 比鄰敬上
    - [x] 開場使用材料更新：https://docs.google.com/presentation/d/1N9DxoN1NuxdtQILkcV67y_q8EM8CJF5GhoYLcCKFpAc/edit [name=mrorz]
	- [x] 準備 Slido `#cofacts`
		- [x] 放投影片網址
- 當日準備 / 攜帶
    - [ ] 樓下用的標語 - bil
    - [ ] **拍照用大布條**
    - [ ] 貼紙 - orz, bil
    - [ ] 黏土 - orz
    - [ ] 手板 - bil
    - [ ] 講義 - bil
    - [ ] 一次性杯子 - bil
    - [ ] 延長線 - bil
        - 比鄰有 5 條
    - [ ] ~~Wifi 機 - mrorz~~ 網路夠穩
        - [ ] ~~rt-ax57 go~~
        - [ ] ~~電源線~~
    - [ ] 多帶一條 type-c 公公線 for dongle 的電
    - [ ] 備用 wifi 機 [name=nonumpa]
- 13:00 - 場佈 [排法](https://g0v.hackmd.io/9IEjq11XSwCyES_VFn8JEg#%E5%B0%8F%E8%81%9A%E6%AA%A2%E8%A8%8E) ![](https://docs.google.com/drawings/d/e/2PACX-1vSZhu49XCUS50miXVUNYO9taFST862ov-EY3zD03qcPy9edM8qU5Q6QpCTFRpzQBwcCQX78pblmzi39/pub?w=943&h=652)
  - 桌子一邊 4 張椅子
  - [ ] 簽到（問飲料）
  - [ ] 排桌子椅子 
  - [ ] 投影位置？
  - [ ] 麥克風
  - [ ] 延長線佈置
  - [ ] 門口黏引導牌
  - [ ] WIFI
      - [ ] 佈機，手機 USB 選擇網路分享，等待白燈亮
      - [ ] 用 ASUS Device Discovery 確認可連線到 ASUS
  - [ ] 投影的電腦用 google chrome 開好
    - [ ] Google Chrome tab: [投影片](https://docs.google.com/presentation/d/1N9DxoN1NuxdtQILkcV67y_q8EM8CJF5GhoYLcCKFpAc/edit)
    - [ ] Google Chrome tab: [Bignum](https://cofacts.github.io/community-builder/#/bignum/setup)
- [ ] browser tabs
    - [ ] Google Chrome tab: [KKTIX](https://cofacts.kktix.cc/events/cofactseditor53)
    - [ ] Google Chrome tab: [Slido admin](https://admin.sli.do/event/rFQZd27cVvgEMyJAgv4BqT/polls)
    - [ ] Google Chrome tab: [Slido](https://wall.sli.do/event/rFQZd27cVvgEMyJAgv4BqT/?section=215e56d0-a002-4b7e-9bf0-c58acbacc9bf)
    - [ ] Google Chrome tab: [開場影片](https://www.youtube.com/playlist?list=PLz8KCDL90tNWn16J2xBzl53imUiDbNOzs)
    - [ ] BGM
    - [ ] Analytics
- 14:00 - 14:20 開場
    - 放[長影片](https://www.youtube.com/playlist?list=PLz8KCDL90tNWn16J2xBzl53imUiDbNOzs) 8min
    - 場地、Slido、Cofacts 機器人系統簡介
- 14:20 - 14:40：引導 註冊網站、介紹評價現有回應
- 14:40 - 14:50：實作評價
    - 讓大家從網站找訊息按讚
- 14:50 - 15:10 介紹補充資訊
- 15:10 - 15:40 實作補充資訊、自我介紹、休息
    - 閒聊「看到覺得最好的回應、覺得哪裡好」
- 15:40 - 16:10：介紹撰寫新回應
- 16:10 - 16:40：實作撰寫新回應
    - 大家從網站挑選「一篇」覺得最有興趣的回
- 16:40 - 17:00 介紹 RSS、社群、合照




# Staging 環境高額費用分析與處理決策 (2026-04-29)

## 1. 問題背景
監控發現 GCP Staging 環境（Cloud Run）每月產生約 $150 USD 的費用。
經查主要支出來自於 `Services CPU` 與 `Network Data Transfer Out`。
雖然 Staging 網頁（如 `dev.cofacts.tw`）已設定 `x-robot-tag: noindex`，但費用仍居高不下。

## 2. 流量分析報告 (過去 7 天)

根據 Cloudflare GraphQL Analytics 資料，Staging 環境遭受大量商業爬蟲存取：

### 網域流量概觀
| 網域 | 總請求數 (7 Days) | 流量性質 |
| :--- | :--- | :--- |
| `dev.cofacts.tw` | 319,731 | 商業爬蟲 (Meta, DotBot, Amazon) |
| `dev-ja.cofacts.tw` | 131,838 | 商業爬蟲 (Amazon, Applebot) |
| `dev-en.cofacts.tw` | 78,364 | 商業爬蟲 (Amazon, Applebot) |
| `dev-line-bot.cofacts.tw` | ~2,000 | 惡意漏洞掃描 (Vulnerability Probing) |
| `dev-api.cofacts.tw` | 391,906 | 內部 SSR 請求 (由上述網頁喚醒) |

### 主要爬蟲來源 (`dev.cofacts.tw`)
- **Meta-webindexer (Facebook)**: ~15.6 萬次 (49%)
- **DotBot (Moz.com)**: ~7.8 萬次 (24%)
- **Amazon SearchBot**: ~4.2 萬次 (13%)

### 漏洞掃描特徵 (`dev-line-bot.cofacts.tw`)
- **惡意路徑**: 大量請求 `wp-kikikoko.php`, `radio.php`, `alfa-rex.php7` 等非預期路徑。
- **特徵**: User-Agent 多為空字串，來源 IP 雜亂，顯然在探測 Web Shell 或 WordPress 漏洞。

## 3. 根本原因分析
1.  **Serverless 喚醒機制**：只要有請求進入，Cloud Run 就會喚醒實例。
2.  **爬蟲無視標籤**：即便有 `noindex`，爬蟲仍必須下載並渲染頁面後才能讀取標籤。
3.  **SSR 連鎖反應**：網頁端的 SSR 會同步喚醒 API 端的 Cloud Run，導致雙倍計費。
4.  **無差別探測**：Bot 會掃描所有子網域的常見漏洞路徑，持續產生喚醒成本。

## 4. 處理決策
為了立即止血並將 Staging 費用降至最低，決定採取以下行動：

### 決策：Cloudflare WAF 分級防禦
1.  **全站挑戰 (Managed Challenge)**： ![](https://g0v.hackmd.io/_uploads/ByvBa51Cbg.png)
    - **對象**：`dev.cofacts.tw`, `dev-en.cofacts.tw`, `dev-ja.cofacts.tw`
    - **效果**：在 Cloudflare 邊緣攔截 99% 爬蟲，讓 Cloud Run 保持 Scaled to 0。
2.  **精準防禦 (Selective Defense)**： ![](https://g0v.hackmd.io/_uploads/BymUa91R-g.png)
    - **對象**：`dev-line-bot.cofacts.tw`
    - **規則**：僅允許 User-Agent 包含 `LineBot` 的請求，其餘流量一律套用 `Managed Challenge`。
    - **效果**：阻斷漏洞掃描，同時確保 LINE Webhook 測試功能不受影響。

### 注意事項
- **開發體驗**：開發者手動進入 Staging 網頁時需通過一次性驗證。
- **API 隔離**：`dev-api.cofacts.tw` 由於運行於 VPS，不受喚醒費用影響，暫不強制要求挑戰。

---
**分析者**: Gemini CLI
**日期**: 2026-04-29

### 5/5 追蹤

![](https://g0v.hackmd.io/_uploads/HyHh4QvC-e.png)

4/30 CloudRun 3.33 USD/day
5/1, 5/2 應有 consume free credit
5/3 開發時有暫時把 staging 的防火牆關掉，5/4 開回去。
5/4 CloudRun 2.83 USD/day 

Approximate monthly cost: 3USD * 30 ~= 100USD
(應該大多是 Cofacts production site)

# 2026-05-04 DDoS 攻擊調查報告

## 時間軸

| 時間 | 事件 |
|------|------|
| 2026-04-30 | Cloudflare threats 從 ~10k/day 暴增至 **113k/day**（平常 10 倍），攻擊開始 |
| 2026-05-01 | GCE swap 開始爆滿（95%+），API 回應開始變慢 |
| 2026-05-04 13:15 TWN | 攻擊出現最大尖峰，POST `/graphql` 達 **2,130 req/min** |
| 2026-05-04 13:36 TWN | 攻擊自然衰退 |
| 2026-05-04 14:00 TWN | 流量回到正常水位 |
| 2026-05-04 14:41 TWN | 部署 Cloudflare WAF Custom Rule + Rate Limiting Rule |
| 2026-05-04 ~14:55 TWN | 重啟 `rumors-deploy-api-1`, `rumors-deploy-site-ja-1` 與 `rumors-deploy-site-en-1` |

---

:::spoiler 細節分析

## GCE 機器影響

### 每日資源使用量（min \| avg \| p95 \| max）

| 日期 | CPU | 記憶體 | Swap |
|------|-----|--------|------|
| 04-28 | 17% \| 28% \| 49% \| 100% | 63% \| 66% \| 68% \| 91% | 13% \| 18% \| 20% \| 61% |
| 04-29 | 19% \| 32% \| 49% \| 82% | 63% \| 66% \| 67% \| 80% | 18% \| 20% \| 21% \| 24% |
| 04-30 | 19% \| 29% \| 39% \| 72% | 61% \| 66% \| 68% \| 68% | 18% \| 28% \| 52% \| 53% |
| **05-01** | 16% \| 29% \| 38% \| 48% | 53% \| 56% \| 58% \| 66% | 68% \| **95%** \| 100% \| 100% |
| 05-02 | 18% \| 27% \| 35% \| 45% | 53% \| 56% \| 58% \| 64% | 97% \| **99%** \| 100% \| 100% |
| 05-03 | 16% \| 32% \| 46% \| 56% | 54% \| 56% \| 59% \| 61% | 98% \| **99%** \| 100% \| 100% |
| **05-04** | 27% \| **45%** \| **100%** \| 100% | 54% \| 60% \| **85%** \| 88% | 99% \| **99%** \| 100% \| 100% |

### 尖峰時即時狀態（攻擊中，~06:15 UTC）

```
Load average: 15.26, 14.12, 14.25   ← 4 vCPU 機器，正常應 < 4
RAM: 25GB / 31GB 已用，6.3GB 可用
Swap: 3.9GB / 4.0GB（97.5%）
```

### 重啟後恢復狀態（~07:05 UTC）

```
Load average: 0.93, 1.20, 2.29   ✅
RAM: 17GB / 31GB 已用，13GB 可用   ✅（釋放 8GB）
Swap: 3.8GB / 4.0GB（持續釋放中）
```

### Process 層級異常（05-04）
- `node /srv/www/build/index.js`（`api-1`）：RSS 從正常 ~150MB 飆至最高 **4,401 MB**
- `node /srv/www/server.js`（`site-en-1` + `site-ja-1`，Next.js）：RSS 從正常 ~400MB 飆至最高 **2,702 MB**

---

## Cloudflare 流量分析

### 每日 Requests / Threats

| 日期 | Requests | Threats | Cache Rate | Uniques |
|------|----------|---------|------------|---------|
| 04-28 | 1,199,961 | 6,671 | 19% | 86,072 |
| 04-29 | 1,295,008 | 10,694 | 18% | 69,954 |
| **04-30** | 1,202,124 | **113,771** | 18% | 73,054 |
| **05-01** | 1,124,875 | **100,434** | 15% | 64,928 |
| **05-02** | 1,045,371 | **83,542** | 16% | 80,249 |
| **05-03** | 1,164,416 | **69,684** | 15% | 166,065 |
| 05-04（截至06:00）| 396,593 | 12,272 | 16% | 72,253 |

### 尖峰小時（05:00–06:00 UTC = 13:00–14:00 TWN）

| 時段 | Requests | Uniques | Cache Rate |
|------|----------|---------|------------|
| 04:00–05:00 | 62,402 | 12,161 | 17% |
| **05:00–06:00** | **87,158** | **27,331** | **7%** |
| 06:00–07:00 | 55,867 | 10,651 | 20% |

### 尖峰小時 Top Paths（05:00–06:00 UTC）

| Path | Method | Status | Count |
|------|--------|--------|-------|
| `/graphql` | POST | **524**（Origin timeout）| **25,524** |
| `/graphql` | GET | 403 | 8,831 |
| `/graphql` | POST | 200 | 6,466 |
| `/graphql` | POST | 499 | 2,871 |

### 分鐘級尖峰（POST /graphql，UTC）

| 時間（TWN）| req/min |
|-----------|---------|
| 13:15 | 289（開始爬升）|
| 13:25 | 1,451 |
| **13:31** | **2,130**（最高峰）|
| 13:36 | 698（開始衰退）|
| 13:44 | 383 |
| 14:00 | 263 |

---

## 攻擊來源分析

### 1:15pm 後新出現的 ASN（確認攻擊者）

| ASN | 業者 | 30min requests | 唯一 IP 數（攻擊 1hr）| 性質 |
|-----|------|----------------|----------------------|------|
| 212238 | Datacamp Limited | 5,578 | 2,593 | 常見 bot hosting |
| 9009 | M247 Europe SRL | 4,655 | 2,040 | VPN/proxy hosting |
| 3257 | GTT Communications | 2,975 | 1,389 | 中繼/hosting |
| 210906 | UAB Bite Lietuva | 1,999 | 919 | 立陶宛 hosting |
| 203020 | HostRoyale Technologies | 1,746 | 1,078 | 廉價 hosting |
| 62874 | Web2Objects LLC | 1,541 | 717 | Hosting |
| 7979 | Servers.com | 1,422 | 669 | 資料中心 |
| 11798 | Ace Data Centers | 1,422 | — | 資料中心 |
| 46635 | Contact Consumers | 1,417 | 648 | 可疑 |
| 396356 | Latitude.sh | 1,173 | 555 | 雲端 hosting |
| **396319** | **Oxylabs** | **1,021** | **478** | ⚠️ 已知 residential proxy 服務 |
| **合計** | | **24,949** | **≥ 11,086** | |

攻擊共動用 **超過 11,000 個唯一 IP**，平均每個 IP 在攻擊 1 小時內只打了 **2.1 次**——這是典型的大型 botnet 分散低速爬取，每個節點行為極為溫和，per-IP rate limiting 完全無效。

Oxylabs 的 478 個 IP 為 residential proxy（真實用戶裝置被當成代理），IP 信譽比純 hosting IP 更乾淨，更難封鎖。

### 攻擊中流量暴增的 GCP IP

| IP | 攻擊前（75分鐘）| 攻擊中（30分鐘）| req/min |
|----|----------------|----------------|---------|
| `34.81.219.20` | 35 req | **18,785 req** | **626/min** |
| `34.34.244.128` | — | 917 req | 30/min |
| `34.34.244.150` | — | 905 req | 30/min |
| `34.34.244.146` | — | 854 req | 28/min |
| `34.34.244.129` | 42 req | 756 req | 25/min |

**重要：`34.81.219.20` 是 GCE 機器自己的 ephemeral external IP。**
已從 WAF block rule 移除，避免封鎖自己的服務。

---

## API Log 分析

### 攻擊期間（05:15–05:45 UTC）Apollo log 組成

| appId | Operations | 筆數 |
|-------|-----------|------|
| WEBSITE | LoadArticlePage (302), LoadReplyPage (97), LoadProfilePage (11), ... | **475** |
| RUMORS_LINE_BOT | anonymous（`ListArticlesInInitState`）| 1 |

### ListArticlesInInitState 的來源

- **appId: RUMORS_LINE_BOT**，且 headers 為空 `{}`
- 空 headers 代表沒有 Cloudflare 加的 `cf-connecting-ip`，即從**內部 Docker network** 進來
- 確認：GCE 上的 LINE bot（zh-1）使用 `http://api:5000/graphql`（內部 URL），不過 Cloudflare
- 結論：這些是**正常的 LINE bot 流量**，與攻擊無關

### 攻擊請求特徵

- `user-agent: node`（Node.js 服務）
- `x-app-id: RUMORS_SITE`
- 來自 `34.81.219.20`（GCE 自身 IP）
- 全部是 WEBSITE 類型的 operations

### Slow requests（>5s）

攻擊期間 297 筆 slow requests，response time 最長達 **121 秒**（正常應 < 1s）。

---

## 網站頁面流量（article / reply / user）

### 攻擊前後總流量對比（Cloudflare 實測）

| 路徑 | 攻擊前 04:00–05:00 UTC | 攻擊中 05:00–06:00 UTC | 增幅 |
|------|----------------------|----------------------|------|
| `/article/*` | 20,270 req/hr → **338/min** | 33,406 req/hr → **557/min** | +65% |
| `/reply/*` | 4,769 req/hr → **79/min** | 20,028 req/hr → **334/min** | **+323%** |
| `/user/*` | 2,533 req/hr → **42/min** | 2,505 req/hr → **42/min** | 0% |
| **合計** | **459/min** | **933/min** | **+103%** |

攻擊新增頁面流量 **+474/min**，POST /graphql 同期增加 **+502/min**，兩者吻合（誤差在 cache 範圍內），確認 **1 page load → 1 SSR graphql call，無倍增效應**。

`/user/` 無異動，攻擊不針對使用者頁面。`/reply/` 攻擊增幅最大（4x）。



### 各攻擊 ASN 的實際攻擊目標

所有已識別的攻擊 ASN **都在打網站頁面，不是直接打 API**：

| ASN | 業者 | 攻擊路徑 | Response |
|-----|------|---------|----------|
| 212238 | Datacamp | GET `/article/`, `/reply/` | 504 / 499 |
| 3257 | GTT | GET `/article/`, `/reply/` | 504 |
| 9009 | M247 | GET `/user/899betbrasil`, `/reply/` | 504 / 524 |
| 396319 | Oxylabs | GET `/article/`, `/reply/` | 499 / 504 |

504 = Cloudflare gateway timeout（網站 SSR 等不到 API 回應）。

### 攻擊期間被打最多的頁面（05:00–06:00 UTC，全 zone）

> 最高僅 54 hits/hr，無任何單一頁面被集中轟炸，確認廣撒式爬取。混合有機流量與攻擊流量。

**Top 25 Article**

| 名次 | Path | hits |
|------|------|------|
| 1 | `/article/1mp3tqxu72w9l` | 54 |
| 2 | `/article/28aglx09u87uo` | 53 |
| 3 | `/article/zlmhzr4jqg5z` | 48 |
| 4 | `/article/1oghg5de9e595` | 35 |
| 5 | `/article/38lw4mgm99gfj` | 34 |
| 6 | `/article/1jiu4uncp48e8` | 34 |
| 7 | `/article/2bv8rqylegiv1` | 31 |
| 8 | `/article/1l9shlk9bj0a1` | 30 |
| 9 | `/article/gAH4H-w35DviD4wBzCP9Xa_9v_2AAYABgQGCI6Af__8` | 27 |
| 10 | `/article/1ctfvezoo1hfi` | 26 |
| 11 | `/article/sfmhQocBn6k8q-JUPIO2` | 25 |
| 12 | `/article/3l5h0823kawlo` | 25 |
| 13 | `/article/9vl6rocBn6k8q-JUVfjs` | 22 |
| 14 | `/article/7i5r8u2tom2f` | 21 |
| 15 | `/article/qvxvpd1aulc8` | 20 |
| 16 | `/article/275puqbpm5thg` | 20 |
| 17 | `/article/E0cW4ZwBB0eXeo828eCG` | 20 |
| 18 | `/article/1a13uy3ff7p0w` | 20 |
| 19 | `/article/iWvexogBvEj1WkaUhyIb` | 19 |
| 20 | `/article/nBQBNJYBW80L-hejtGq7` | 19 |
| 21 | `/article/Wfw3boYBC7Q3lHuUAQRF` | 19 |
| 22 | `/article/6qvloxrr8skj` | 19 |
| 23 | `/article/1qoupsbx9ay8d` | 19 |
| 24 | `/article/2q2f5ud05uf6j` | 18 |
| 25 | `/article/3plaq6oc416ua` | 18 |

**Top 25 Reply**

| 名次 | Path | hits |
|------|------|------|
| 1 | `/reply/CmZ5AGIBbyB_hvRut2b-` | 22 |
| 2 | `/reply/m_mJWocBn6k8q-JUnZtm` | 17 |
| 3 | `/reply/vv3yWmcBP8Wrztiv8YIu` | 16 |
| 4 | `/reply/is8L4IkBrkRFoI6rFmoi` | 15 |
| 5 | `/reply/2gYBDHEBrhVJn3LNSPK9` | 15 |
| 6 | `/reply/KSZDvoABvUvLpBdgydoU` | 15 |
| 7 | `/reply/9HJwDJEBd3gcY0LpDbA5` | 14 |
| 8 | `/reply/O_1TFWcBP8Wrztiv8nz9` | 13 |
| 9 | `/reply/KmQX-WoBFV14knB46y_u` | 13 |
| 10 | `/reply/XUK9hnoBgBgcuemXEITM` | 13 |
| 11 | `/reply/AV5NShGJyCdS-nWhufgd` | 12 |
| 12 | `/reply/ebd9xpIBDfH0hhhZaI4E` | 12 |
| 13 | `/reply/Blan3GEBbyB_hvRux6Vb` | 12 |
| 14 | `/reply/dnIunpABd3gcY0Lp-A6Z` | 11 |
| 15 | `/reply/GiUI-H4BvUvLpBdgBi-1` | 11 |
| 16 | `/reply/I_rlh4QBC7Q3lHuUAzyp` | 11 |
| 17 | `/reply/AV2E6BsxyCdS-nWhudJe` | 11 |
| 18 | `/reply/_h6jHWQBSH_MLFhIHmV6` | 11 |
| 19 | `/reply/JPf8I40BAjOeMOkl6Hzd` | 11 |
| 20 | `/reply/JGO7BY8BUCqzrknpwkzQ` | 10 |
| 21 | `/reply/hpkbyXQB9w1KR1Ik3Tyj` | 9 |
| 22 | `/reply/_PTGq3sBqH8xU4AwTqdB` | 9 |
| 23 | `/reply/-B7NRGMBSH_MLFhI9l8E` | 9 |
| 24 | `/reply/AV4NP3IFyCdS-nWhuewU` | 9 |
| 25 | `/reply/I8OsiXwBucwAqrbaaAp6` | 9 |

### 已排除的假說

- **攻擊者直接 flooding POST `/graphql`**：確認所有攻擊 ASN 打的都是 GET 網站頁面，不是 API
- **SSR retry storm**：rumors-site 無 retry 邏輯，graphql 增幅（2.7x）與頁面增幅（3x）吻合，無倍增
- **攻擊者使用 `moreLikeThis` query**：只找到 3 筆，且來自 LINE bot 內部呼叫，非主要攻擊手法
- **`34.81.219.20` 是攻擊者**：這是 GCE 自己的 ephemeral IP，是 SSR 的正常出口
- **攻擊者自動操作 LINE bot 觸發 moreLikeThis**：LINE bot 在攻擊期間只記錄到 1 筆，volume 沒有明顯上升

:::

## 攻擊全貌（結論）

攻擊者**並非直接 flooding POST `/graphql`**，而是透過打網站頁面間接觸發 SSR API 呼叫：

```
攻擊者（Datacamp / M247 / GTT / Oxylabs 等）
  → GET /article/<id>、/reply/<id>、/user/<id>（800 req/min）
  → site-tw（Cloud Run）/ site-en、site-ja（GCE）做 SSR
  → SSR 向 api.cofacts.tw 送 POST /graphql（LoadArticlePage 等）
  → ~800 concurrent SSR 連線同時打 API，每個等 116s+
  → Elasticsearch 撐不住，所有 query 變慢形成正回饋
  → Cloudflare 等 100s 後對所有連線回 524 / 504
  → Swap 爆滿（99%+）、Load avg 15+、API 全面 524
```

`34.81.219.20`（GCE external IP）的 18,785 POST /graphql（其中 86% 為 524）是 **site-en/ja SSR 的正常呼叫**，因 API 過載而全數 timeout，非獨立攻擊行為，也無 retry。


### 攻擊行為模式：全庫廣撒爬取

攻擊者為爬蟲，不執行 JavaScript。每個 ASN 在 30 分鐘內打了數百至數千個不同的 article / reply ID，每篇僅被打 2–13 次，是**系統性掃描全庫**的行為，不針對特定議題文章。

| ASN | 30min 內單篇最高 | 分布 |
|-----|----------------|------|
| Datacamp | 13 次 | 大量不同 article ID，多數 3–6 次/篇 |
| M247 | 6 次 | 大量不同 article ID，多數 3–5 次/篇 |
| GTT | 5 次 | 大量不同 article ID，多數 2–4 次/篇 |

估計 Datacamp 單一 ASN 在 30 分鐘內觸及 **~1,000 篇不同 article**（5,578 req ÷ 平均 5 次/篇）。

---

## 已部署的防禦措施

### Cloudflare Custom Rule「20260504 attack mitigation」（2026-05-05 更新）
```
(ip.src.asnum in {212238 9009 3257 210906 203020 62874 7979 11798 46635 396356 396319})
```
Action: Managed Challenge
覆蓋範圍：所有路徑（已移除原本只限 `/graphql` 的限制），攻擊的 `/article/`、`/reply/` 路徑亦受到保護。

> 注意：原本也 block 了 `34.81.219.20`，確認為 GCE 自身 IP 後已移除。

### Cloudflare Rate Limiting Rule「Prevent fast access」
```
(http.request.uri matches r"/(article|reply)/" and not cf.bot_management.verified_bot)
or
(http.host eq "api.cofacts.tw" and http.request.method eq "POST"
  and http.request.uri.path wildcard "/graphql")
```
原有規則：`/(article|reply)/` 10秒 7次
新增：`api.cofacts.tw` POST `/graphql` 加上頻率限制

### Super Bot Fight Mode（2026-05-05 啟用）

- Definitely automated → Managed Challenge
- Likely automated → Managed Challenge

針對 Datacamp / M247 / GTT 等已知 bot hosting 網路自動 challenge，不需手動維護 ASN list。

> 注意：Oxylabs 為 residential proxy 服務，使用真實住宅 IP，SBFM 的 ML bot 偵測無法識別，為現行防禦的缺口。

### 為何 Rate Limiting 未能阻擋攻擊

Rate limiting 是**針對每個 IP** 計算，而攻擊為分散式低速（low-and-slow distributed）爬取：

- 11 個 ASN × 大量不同 IP，攻擊總量約 832 req/min
- 假設 500 個攻擊 IP：每個 IP 平均僅 **1.7 req/min**，遠低於任何合理門檻
- 每個 IP 打不同的 article/reply ID，每篇各自只被打 2–13 次

Per-IP rate limiting 對此類攻擊完全無效。ASN block 才有效，因為是封整個網路段。

---

## 後續建議防禦措施

### 近期（Cloudflare 設定）

**考慮啟用「Challenge foreign non-bot access」**

目前 SBFM 無法識別 Oxylabs（residential proxy）——攻擊者透過真實住宅 IP 作為代理，ML bot 偵測看不出來。啟用此選項可 challenge 非 TW 的非 bot 流量，但副作用是合法的海外用戶（例如使用英文版的用戶）也會被 challenge，需評估影響後再決定。

### 中期（程式面）

**SSR fetch 加 timeout**

`lib/fetchAPI.js` 目前無 timeout，攻擊期間每個 SSR connection 卡了 116 秒，大量 connection 堆積耗盡 RAM 與 swap。加入 10 秒 timeout：

```js
fetch(url, {
  signal: AbortSignal.timeout(10000),
  ...options,
})
```

**讓 Cloudflare 快取 article/reply 頁面（最根本的解法）**

攻擊的放大效果：1 page request → 1 SSR → 1 Elasticsearch query。若 article/reply 頁面能被 Cloudflare 快取（哪怕 5 分鐘），攻擊者拿到 cache hit，完全不觸發 SSR，攻擊鏈斷掉。

攻擊期間 cache rate 僅 7%，幾乎每個請求都打到 origin。需在 Next.js 的頁面加 `Cache-Control: public, max-age=300, stale-while-revalidate=60`，並確認 Cloudflare 設定允許快取這些路徑。

| 優先 | 措施 | 狀態 | 工程量 |
|------|------|------|--------|
| 完成 | WAF rule 覆蓋所有路徑（移除 /graphql 限制） | ✅ 已部署 | — |
| 完成 | 開啟 Super Bot Fight Mode | ✅ 已部署 | — |
| 近期 | 評估啟用 Challenge foreign non-bot access（Oxylabs 缺口）| 待決定 | 5 分鐘，有副作用 |
| 中期 | SSR fetch timeout（10s）| 待實作 | 小改 |
| 中期 | Cloudflare 頁面快取 | 待實作 | 需測試 Cache-Control 對 SSR 的影響 |

## 問題

old.cofacts.tw 與 cofacts.ai 一度被新的 WAF 阻擋
- cofacts.ai, dev.cofacts.ai
    - 無法送出新訊息（500）
        - 先寫死 source IP = cofacts-prod 時 skip all rules 來規避
    - 無法載入舊訊息（原因不明）
- old.cofacts.tw 無法載入訊息列表
- production line bot 是不是也被掃了？流量應該要大多來自 LINE bot、LIFF 瀏覽、API 拉檔案 （content endpoint）

:::success
持續觀察穩定度
:::
