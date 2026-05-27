# 開源即時語音翻譯系統 OpenTransLive

## 專案概要
:::info
開源即時語音翻譯系統 OpenTransLive
https://github.com/g0v/OpenTransLive/
:::
OpenTransLive 是一套能夠即時擷取音訊、轉錄成文字，並將文字內容同步翻譯成多種語言的工具。提供現代化的網頁介面，讓使用者能即時查看轉錄結果，更具備獨特的 YouTube 整合介面，為直播或影片提供同步字幕。本系統採用客戶端與伺服器分離架構，利用 WebSocket 技術達成低延遲的即時通訊，並可彈性切換多種語音轉錄引擎（如 WhisperX、OpenAI、Groq）。

## 目標與願景

### 短期目標
*   **提供穩定、高效的即時轉錄服務：** 確保音訊擷取、語音轉錄處理流程的穩定性與低延遲。
*   **打造直覺易用的使用者介面：** 讓使用者能輕鬆在各種模式和裝置下順暢地檢視轉錄內容。
*   **最佳化系統的資源運用：** 在確保功能完整的基礎上，有效降低運算資源的消耗。

### 長期願景
*   **成為社群基礎建設輔助工具：** 提供給廣大台灣開源社群使用做為活動基礎建設，降低語言隔閡。
*   **建立開放且具擴充性的生態系：** 鼓勵開源社群貢獻，並提供更多 API 介面，供第三方應用程式整合。

## 核心功能特色
*   **即時語音轉錄與多引擎支援**
    *   可彈性選用 WhisperX、OpenAI 4o transcribe 或 Groq 進行即時音訊轉錄。
    *   內建進階音訊處理機制，包含重疊緩衝區 (Overlap Buffering)、可自訂的語音偵測能量閾值與停頓閾值，提升轉錄準確度。
*   **多國語言即時翻譯**
    *   利用 GPT 或其他指定 AI 模型，將轉錄內容自動翻譯成多種目標語言。
    *   具備上下文感知翻譯能力，並透過分析對話歷史自動提取關鍵字，提升翻譯的流暢度與品質。
*   **高互動性的使用者網頁介面**
    *   基於 Flask 框架打造的網頁應用，提供多語即時檢視與 YouTube 整合等多種模式。
    *   支援多種檢視版面（網格、單欄）及語言下拉式選單。
    *   顯示 QR Code，方便行動裝置快速連線參與。
*   **YouTube 整合與直播支援**
    *   可直接嵌入 YouTube 播放器，並為其提供同步字幕。
    *   保存轉錄時間碼，自動語 YouTube 直播時間進行同步。
*   **即時同步與通訊**
    *   採用 WebSocket 進行客戶端與伺服器之間的即時雙向通訊。
    *   基於房間 (Room-based) 的管理，確保不同對談的資料隔離與傳輸效率。

## 技術架構（2025 舊版）
本系統採用客戶端與伺服器分離的架構，確保各模組職責分明，易於維護及擴充。

![](https://g0v.hackmd.io/_uploads/S1RYABARel.png)


| 位置 | 名稱 | 說明 |
| -- | -- | -- |
|Client|Pyaudio Speechrecognition|音訊處理 & VAD 斷句偵測|
|Client|OpenAI 4o Transcribe|語音轉錄文字 (正確率較高)|
|Client|WhisperX|語音轉錄文字 (時間碼較精準)|
|Client|OpenAI GPT-4.1|文字校正與關鍵字提取|
|Client|OpenAI GPT-4.1|即時翻譯|
|Client|OpenCC|簡繁轉換|
|Client|Socketio|同步結果至伺服端|
|Server|Flask|網頁前後端框架|
|Server|Socketio|接收 Client 端結果，同步至使用者端|

## 技術架構（2026 新版）
請見 [live_server README.md](https://github.com/g0v/OpenTransLive/blob/main/live_server/README.md) 以及 [milestone.md](https://github.com/g0v/OpenTransLive/blob/main/milestone.md)

## 時程規劃與成果
### 2025/11
- 11/23 大松提案、同步測試（要先跟揪松溝通）

#### 相關成果
- [2025/11/23 大松提案](https://www.youtube.com/watch?v=C_9RNJsI56E)
- [2026/01/25 大松提案](https://www.youtube.com/watch?v=9uTR4muU3aY)
- [2026/03/29 大松提案](https://www.youtube.com/watch?v=lR0WShurIjo)


### 2025/12
- 開發一個純瀏覽器版的 MVP，打開網頁就可以直接使用
- 調整 WebSocket 的傳輸方式
- 研究改用 OpenAI Real-time API 的可行性
    > 於 2026/01 選擇使用 Elevenlabs Scribe V2 Realtime 表現較好
- 建立 docker file，讓使用者能夠快速部屬

#### 相關成果
| 時間 | Commit | 對應項目 | 說明 |
|---|---|---|---|
| 2025-11-22 | 7eb521a | Web 版雛形 | 重整為 `live_server`、`transcribe_client`、`realtime_client`，新增網頁模板與服務架構。 |
| 2025-11-26 | 6f50a9e | 使用者建立 session | 使用者可建立 session，系統產生 secret key，新增 panel 頁面。 |
| 2025-12-22 | 0ad34f2 | WebSocket / Docker / DB 基礎 | 改寫為 FastAPI、Redis、MongoDB，新增 `Dockerfile` 與 `docker-compose.yml`。 |

![](https://g0v.hackmd.io/_uploads/Sy6hCDbeMe.png)

### 2026/01~02
- 建立使用者帳號系統
- 改用資料庫儲存字幕結果
- 提供多種格式匯出選項 (srt, vtt, txt)

#### 相關成果
| 時間 | Commit | 對應項目 | 說明 |
|---|---|---|---|
| 2026-03-10 | c12f3a7 | 使用者帳號系統 | 新增 email OTP 登入、管理後台與即時轉錄權限管理。 |
| 2026-04-16 | e1be265 | 字幕資料儲存 | 將轉錄資料移到獨立 segments collection，改善管理與查詢基礎。 |
| 2026-04-21 | 32cd088 | 歷史紀錄管理 | 新增字幕編輯頁與 session segments 管理 API。 |
| 2026-04-23 | 25f77ef | 匯出功能 | 新增單語言 SRT 匯出。 |

![](https://g0v.hackmd.io/_uploads/r1R0CvWezx.png)

### 2026/03~04
- 串接大型語言模型，自動摘要與抓出關鍵字
    > 多方嘗試後，目前採用 GPT-OSS-120B 有較好的品質/速度平衡
- 建立讓使用者可以自己上傳專業字詞庫的系統
- 讓使用者可以從歷史紀錄頁面方便地搜尋、管理跟匯出


#### 相關成果
| 時間 | Commit | 對應項目 | 說明 |
|---|---|---|---|
| 2026-03-06 | f9bc8ff | 專業字詞 / 關鍵字 | 新增 session keywords API 與 panel 編輯介面。 |
| 2026-04-09 | b536b0f | 自動關鍵字 | 將關鍵字改為頻率字典，加入抽取與排序邏輯。 |
| 2026-04-21 | 32cd088 | 歷史紀錄管理 | 新增字幕編輯頁與 session segments 管理 API。 |
| 2026-05-06 | a698ad2 | 使用者自訂字詞庫 | 新增 text dictionary API 與 panel UI，翻譯流程會套用使用者定義替換。 |

![](https://g0v.hackmd.io/_uploads/r1gpQJd-xzl.png)

### 2026/05
- 目標在 g0v summit 2026 全面應用

#### 相關成果
見  [g0v-summit-2026](#20260523-24-g0v-summit-2026)

> [name=ch-review] 這是什麼？


## 專案行政（2025 至 2026 年 5 月）
### 預算
- 總額：新台幣 20 萬元整
- 經費來源：數位民主工作小組 D2WG

### 撥款流程
- 2025 年 12 月初：撥款 40%
- 2026 年 2 月底至 3 月初：進度確認後撥款 30%
- 2026 年 5 月底（summit 後）：進度確認後撥款 30%

### 專案參與人員
- 開發者：SeanGau
- 開發進度確認及協調：chihao（2026 為志工）
- 行政管理：王頌（2026 為志工）

## 應用案例
### 2025 面海松
本專案起源於 [2025 g0v 面海松](https://g0v.hackmd.io/@fto/book/%2FUJCmd7kiSROiO1cc7J0lGw)，於現場即時投影4國語言（華英日韓）的字幕，講者可以使用自己的母語進行發表，能更清楚的表達內容。

#### 活動結束後收到評價
- 隨時可以回看得字幕非常方便，不小心放空也可以很快跟上
- 協助翻譯的時候，有逐字稿可以看非常有幫助
- 能用母語發表超棒，很多詞不知道英文要怎麼講

#### 會後檢討
- 轉錄+翻譯延遲大約 5~10 秒，QA 環節影響較明顯
- 收音敏感度高，音量過大過小都會轉錄不出來文字
- 字幕架設角度應考量會眾視線方向
- 如果可以事前蒐集關鍵字會更好的改善品質

![](https://g0v.hackmd.io/_uploads/S1xUoVDJk-g.png)
![](https://g0v.hackmd.io/_uploads/Skxzc8wy1Wx.png)

> [name=ch-review] summit 前是不是也有一些其他應用情境，也請任翔簡要記錄一下

### 2026/05/23~24 g0v summit 2026

![](https://g0v.hackmd.io/_uploads/S1Gotv-xze.png)

> [name=ch-review] 請說明上圖用意

> [name=ch-review] 是否能向 summit 索取系統運行實況照片（有嗎？），並更細緻描述應用情形

> [name=ch-review] 我個人有注意到 summit day 1 R0 isabel keynote 提到「矽基工程師」AI 偵測不出來也無法翻譯，可以當成有趣的小發現記錄下來。社群往往是發明新詞（包括黑話）的地方，也許這個專案可以設計關鍵詞社群協作機制，未來發放大家一起來建具備 g0v 社群特色的辭典，甚至開放到 FtO 社群變成東亞特色？

#### 會後檢討

- 5軌 * 華英日韓 4語即時翻譯，讓會眾可以掃描 QRCode 於自己手機觀看，尖峰約50人在線使用
- Tokens 用量超乎預期，觸碰到 Provider 的 TPM Rate Limit，應急方案是調高翻譯的間隔（1.5s -> 3s）並改用較貴的服務方案。
    > 使用 Scribe V2 Realtime 搭配 GPT-OSS-120B 可以在2秒甚至更快的時間內處理完翻譯，故稍微調高翻譯間隔沒有明顯影響觀看體驗
- Redis 目的是提供較穩定快速的 In memory database，但卻造成 Overload 導致伺服器當機，故調整了 Redis 的記憶體使用上限及舊資料的拋棄策略
- 兩天下來的 API 用量：
    Scribe V2 Realtime: 144K Credits = $31.31USD
    ![](https://g0v.hackmd.io/_uploads/SklFCedZeGg.png)
    Groq: $35.29 USD
    ![](https://g0v.hackmd.io/_uploads/r1UN-dblGl.png)
- 因為 Rate Limit 及 API 費用的問題，完全開放給社群使用不太實際，也許先採用專案合作的方式進行

> [name=ch-review] 是否能請任翔追加未來半年（2026/6-12）應用規劃，例如 9 月首爾面海松？

