# 20260512 會議記錄

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

### RightsCon 擺攤
- [ ] X 型布幕 https://www.figma.com/design/1tiXCGut4kNCEkDG9FTza7/LINE-Chat-UI-Template--Community-?node-id=3011-2598&t=M7kq3ymM7XDO2z0s-4
- [ ] mrorz, bil: 名片
    - mrorz 正在補名片
- [ ] mrorz: 貼紙
- [ ] mrorz: acho 黃色傳單 (英文)，確認 QR code
- [ ] QR code 板板、Cofacts 板板
- [ ] 外接螢幕：cofacts Youtube + about page

### cofacts.ai tickets
- [ ] 將登入使用者的 userId 傳遞給 ADK 與 Langfuse feedback
- [ ] (第一階段) 輸入法組字時按 Enter 會直接送出訊息
- [ ] (第一階段) 無法中途停止 AI 回應生成
- [ ] (第一階段) 在輸入或生成中關閉分頁沒有提示
- [ ] (第二階段) 讓使用者可以編輯自己的提問
- [ ] (第二階段) 讓使用者可以上傳圖片進行分析

### rumors-api tickets
- [ ] 移除 Twitter 登入功能

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
1.  **全站挑戰 (Managed Challenge)**：
    - **對象**：`dev.cofacts.tw`, `dev-en.cofacts.tw`, `dev-ja.cofacts.tw`
    - **效果**：在 Cloudflare 邊緣攔截 99% 爬蟲，讓 Cloud Run 保持 Scaled to 0。
2.  **精準防禦 (Selective Defense)**：
    - **對象**：`dev-line-bot.cofacts.tw`
    - **規則**：僅允許 User-Agent 包含 `LineBot` 的請求，其餘流量一律套用 `Managed Challenge`。
    - **效果**：阻斷漏洞掃描，同時確保 LINE Webhook 測試功能不受影響。

### 注意事項
- **開發體驗**：開發者手動進入 Staging 網頁時需通過一次性驗證。
- **API 隔離**：`dev-api.cofacts.tw` 由於運行於 VPS，不受喚醒費用影響，暫不強制要求挑戰。

---
**分析者**: Gemini CLI
**日期**: 2026-04-29

