---
title: 臺北市水利處雨量站即時監測 — p5.js 講義

---

# 臺北市水利處雨量站即時監測 — p5.js 講義

> **技術框架**：p5.js 1.9.x × Fetch API × 臺北市資料大平臺 OpenData
> **資料提供**：臺北市政府水利處（wic.gov.taipei）
> **適用對象**：創意程式設計學習者、資料視覺化開發者、公民科技應用者

---

## 目錄

1. [專案概述](#1-專案概述)
2. [OpenData 資料集說明](#2-opendata-資料集說明)
3. [API 端點與欄位詳解](#3-api-端點與欄位詳解)
4. [p5.js 程式架構](#4-p5js-程式架構)
5. [API 連線與資料擷取](#5-api-連線與資料擷取)
6. [資料解析與正規化](#6-資料解析與正規化)
7. [視覺化設計說明](#7-視覺化設計說明)
8. [動畫與互動功能](#8-動畫與互動功能)
9. [雨量警戒等級設計](#9-雨量警戒等級設計)
10. [自動更新機制](#10-自動更新機制)
11. [錯誤處理與備用資料](#11-錯誤處理與備用資料)
12. [延伸應用與練習](#12-延伸應用與練習)
13. [常見問題 FAQ](#13-常見問題-faq)
14. [附錄：完整 API 欄位速查](#14-附錄完整-api-欄位速查)

---

## 1. 專案概述

本專案以 **p5.js** 作為核心渲染引擎，即時連接臺北市水利處的雨量觀測站 OpenData API，將分散於全市各行政區的雨量站數據以視覺化方式呈現。

### 1.1 設計目標

| 目標 | 說明 |
|------|------|
| **即時性** | 每 5 分鐘從 API 重新擷取最新雨量數據 |
| **完整性** | 顯示全市所有雨量站的當前觀測值 |
| **直觀性** | 以顏色、動態水柱、粒子效果表達降雨強度 |
| **穩健性** | API 連線失敗時自動切換至示範資料，確保功能不中斷 |

### 1.2 技術棧

```
前端框架：  p5.js 1.9.x（Canvas 2D 渲染，60fps draw loop）
資料來源：  臺北市水利處 OpenData REST API（JSON 格式）
字型：      Share Tech Mono（儀表板數字）+ Rajdhani（標題）
部署方式：  單一 HTML 檔案，無需後端，直接開啟即可使用
```

### 1.3 與 Vue/Chart.js 版本的差異

| 面向 | Vue + Chart.js 版 | p5.js 版 |
|------|-------------------|---------|
| 渲染方式 | DOM + Chart.js Canvas | 純 Canvas（全程 p5.js 繪製） |
| 卡片動畫 | CSS transition | 逐幀 `lerp()` 插值 |
| 互動方式 | 原生 HTML 事件 | `mousePressed()`、`mouseMoved()` |
| 背景特效 | CSS animation | 自訂雨滴粒子系統 |

---

## 2. OpenData 資料集說明

### 2.1 資料集基本資訊

| 項目 | 說明 |
|------|------|
| **資料集名稱** | 臺北市水利處雨量站即時資料 |
| **提供機關** | 臺北市政府水利處（wic.gov.taipei） |
| **資料集說明頁** | https://data.taipei/dataset/detail?id=6f03a0b8-7b98-4eea-8bb9-ba6bfcdc2b8b |
| **資料格式** | JSON |
| **更新頻率** | 每 10 分鐘更新一次（即時觀測） |
| **授權方式** | 政府資料開放授權條款（OGDL）— 可自由下載、分享、加值應用 |
| **資料範圍** | 臺北市 12 個行政區，共約 30+ 雨量觀測站 |

### 2.2 資料集說明網址

```
https://data.taipei/dataset/detail?id=6f03a0b8-7b98-4eea-8bb9-ba6bfcdc2b8b
```

此網址為臺北市資料大平臺（data.taipei）上的資料集詳細說明頁，包含：
- 資料集描述與使用說明
- 欄位清單與資料類型說明
- 歷史版本與更新紀錄
- 其他可用的下載格式（如 CSV）
- 相關授權條款

### 2.3 為什麼選擇這個資料集？

- **即時性**：觀測資料每 10 分鐘更新，非常適合即時監控應用
- **公開免費**：無需付費，提供 API Key（open_rain）即可存取
- **結構簡單**：欄位清晰（僅 5 個主要欄位），易於解析
- **應用價值**：可供市民了解周遭即時降雨狀況，輔助防災判斷

---

## 3. API 端點與欄位詳解

### 3.1 API 端點

```
https://wic.gov.taipei/OpenData/API/Rain/Get?stationNo=&loginId=open_rain&dataKey=85452C1D
```

### 3.2 請求參數說明

| 參數名稱 | 值 | 說明 |
|---------|-----|------|
| `stationNo` | （空白） | 站碼篩選。**空白 = 查詢全部雨量站**；填入特定站碼可只查單站 |
| `loginId` | `open_rain` | 公開登入帳號，無需申請，供一般民眾使用 |
| `dataKey` | `85452C1D` | API 存取金鑰（公開金鑰，可直接使用） |

**指定單一站查詢範例**（假設站碼為 `C0A9G0`）：
```
https://wic.gov.taipei/OpenData/API/Rain/Get?stationNo=C0A9G0&loginId=open_rain&dataKey=85452C1D
```

### 3.3 回傳格式

API 回傳標準 JSON 格式，為一個物件陣列：

```json
[
  {
    "count": 33,
    "stationNo": "C0A9G0",
    "stationName": "貴子坑",
    "recTime": "2024-05-24 15:30:00",
    "rain": 2.5
  },
  {
    "count": 33,
    "stationNo": "C0A9H0",
    "stationName": "百拉卡",
    "recTime": "2024-05-24 15:30:00",
    "rain": 18.6
  }
]
```

### 3.4 五大欄位完整說明

#### ① count — 記錄筆數

| 項目 | 說明 |
|------|------|
| **欄位名稱** | `count` |
| **資料型別** | 整數（Integer） |
| **說明** | 本次 API 查詢所回傳的雨量站**總筆數**（即總監測站數量） |
| **範例值** | `33` |
| **用途** | 驗證資料是否完整；可用於計算百分比、統計摘要 |
| **注意** | 每一筆資料的 `count` 值相同，代表本次查詢共有幾個站的資料 |

```javascript
// 程式碼使用範例
const totalStations = data[0]?.count || data.length;
console.log(`共 ${totalStations} 個雨量站`);
```

---

#### ② stationNo — 站碼

| 項目 | 說明 |
|------|------|
| **欄位名稱** | `stationNo` |
| **資料型別** | 字串（String） |
| **說明** | 每個雨量站的**唯一識別碼**，由英文字母與數字組成 |
| **範例值** | `"C0A9G0"`、`"C0A9H0"`、`"C0A9L1"` |
| **用途** | 作為主鍵（Primary Key），用於識別和篩選特定站台 |
| **命名規則** | 通常由前綴字母（代表機關）加上流水號組成 |

```javascript
// 程式碼使用範例 — 查詢特定站
const targetStation = data.find(s => s.stationNo === 'C0A9G0');

// 依站碼排序
data.sort((a, b) => a.stationNo.localeCompare(b.stationNo));
```

---

#### ③ stationName — 站台名稱

| 項目 | 說明 |
|------|------|
| **欄位名稱** | `stationName` |
| **資料型別** | 字串（String，中文） |
| **說明** | 雨量站的**中文地名名稱**，通常以觀測站所在地點命名 |
| **範例值** | `"貴子坑"`、`"百拉卡"`、`"貓空"`、`"木柵"` |
| **用途** | 顯示在卡片、圖表、地圖標記上，供使用者識別地點 |
| **特性** | 名稱反映地理位置（如山名、溪名、社區名），有助於辨識降雨區域 |

```javascript
// 程式碼使用範例 — 顯示站名
fill(255);
textFont('Noto Sans TC');
textSize(14);
text(station.stationName, cardX + 12, cardY + 28);
```

---

#### ④ recTime — 記錄時間

| 項目 | 說明 |
|------|------|
| **欄位名稱** | `recTime` |
| **資料型別** | 字串（String，日期時間格式） |
| **說明** | 此筆雨量資料的**觀測記錄時間** |
| **格式** | `"YYYY-MM-DD HH:mm:ss"`（24小時制，台灣時間 UTC+8） |
| **範例值** | `"2024-05-24 15:30:00"` |
| **更新頻率** | 每 10 分鐘更新一次，分鐘通常為 00、10、20、30、40、50 |
| **用途** | 顯示資料最後更新時間；判斷資料是否過期 |

```javascript
// 程式碼使用範例 — 解析並顯示時間
const recTime = station.recTime;  // "2024-05-24 15:30:00"

// 轉換為 Date 物件
const dt = new Date(recTime.replace(' ', 'T') + '+08:00');

// 格式化顯示
const timeStr = `${dt.getHours().toString().padStart(2,'0')}:${dt.getMinutes().toString().padStart(2,'0')}`;
// → "15:30"

// 判斷資料是否超過 20 分鐘未更新（可能異常）
const isStale = (Date.now() - dt.getTime()) > 20 * 60 * 1000;
if (isStale) {
  fill(255, 100, 100);  // 以紅色警示過期資料
  text('⚠ 資料可能異常', x, y);
}
```

---

#### ⑤ rain — 雨量值

| 項目 | 說明 |
|------|------|
| **欄位名稱** | `rain` |
| **資料型別** | 浮點數（Float） |
| **單位** | **mm（毫米）** |
| **說明** | 該站在**記錄時間當下的即時觀測雨量值** |
| **範例值** | `0.0`（無雨）、`2.5`、`18.6`、`45.2` |
| **數值範圍** | 通常 0.0 ~ 200.0+ mm（視降雨強度而定） |
| **特殊值** | `-1` 或 `null` 可能代表儀器異常或資料缺失 |
| **時間維度** | 注意：此值通常為**當次觀測區間（10分鐘）的累積雨量**，非小時雨量 |

```javascript
// 程式碼使用範例
const rainValue = parseFloat(station.rain) || 0;

// 雨量等級判斷（以 mm 為單位）
function getRainLevel(mm) {
  if (mm <= 0)    return { label: '無雨',   color: [42, 58, 90]  };
  if (mm < 1)     return { label: '微雨',   color: [0, 212, 255] };
  if (mm < 4)     return { label: '小雨',   color: [0, 255, 136] };
  if (mm < 10)    return { label: '中雨',   color: [255, 184, 0] };
  if (mm < 20)    return { label: '大雨',   color: [255, 107, 0] };
  return           { label: '豪雨',   color: [255, 23,  68]  };
}
```

### 3.5 欄位關係圖

```
API Response Array
│
├── [0] { count: 33, stationNo: "C0A9G0", stationName: "貴子坑", recTime: "...", rain: 2.5 }
├── [1] { count: 33, stationNo: "C0A9H0", stationName: "百拉卡", recTime: "...", rain: 18.6 }
├── [2] { count: 33, stationNo: "C0A9L1", stationName: "貓空",   recTime: "...", rain: 9.2 }
│    ↑          ↑             ↑                ↑              ↑              ↑
│  記錄筆數    站碼（主鍵）   站台名稱       記錄時間       雨量值（mm）
│  [每筆相同] [唯一識別]   [中文地名]  [YYYY-MM-DD HH:mm:ss] [即時觀測]
└── ... (共 count 筆)
```

### 3.6 回傳資料注意事項

1. **`count` 欄位在每筆都相同**：代表本次查詢的總站數，非每站個別的筆數
2. **`rain` 可能為負值或特殊值**：`-1` 通常代表儀器故障，需在程式中過濾
3. **`recTime` 為台灣本地時間（UTC+8）**：直接顯示即可，無需時區轉換
4. **所有站的 `recTime` 幾乎相同**：因為資料是同批次更新的
5. **全站查詢 vs 單站查詢**：`stationNo` 空白 = 全部站；填入特定碼 = 單站

---

## 4. p5.js 程式架構

### 4.1 完整檔案結構

```
taipei-rain-p5.html
│
├── <head>
│   ├── Google Fonts（Share Tech Mono + Rajdhani + Noto Sans TC）
│   ├── p5.js CDN
│   └── <style>（背景雨滴動畫等 CSS 特效）
│
└── <script>（所有 p5.js 程式碼）
    │
    ├── ── 常數設定 ──────────────────────────────
    │   ├── API_URL（臺北市水利處 API 端點）
    │   ├── REFRESH_INTERVAL（更新間隔，預設 300 秒）
    │   ├── 雨量警戒閾值（THRESHOLDS）
    │   └── 顏色系統（COLORS）
    │
    ├── ── 全域狀態變數 ───────────────────────────
    │   ├── stations[]（雨量站資料陣列）
    │   ├── displayStations[]（動畫插值用的顯示陣列）
    │   ├── isLoading（載入狀態）
    │   ├── isLive（是否為即時 API 資料）
    │   ├── lastUpdate（最後更新時間）
    │   ├── selectedDistrict（行政區篩選）
    │   └── rainDrops[]（雨滴粒子陣列）
    │
    ├── preload()
    │   └── 載入字型（p5.js loadFont）
    │
    ├── setup()
    │   ├── createCanvas(windowWidth, windowHeight)
    │   ├── 初始化雨滴粒子系統
    │   └── fetchRainData()（非同步啟動資料擷取）
    │
    ├── draw()（60fps 主迴圈）
    │   ├── background()（清除畫面）
    │   ├── drawRainDrops()（背景雨滴動畫）
    │   ├── if(isLoading) → drawLoadingScreen()
    │   ├── else          → drawDashboard()
    │   │    ├── drawHeader()
    │   │    ├── drawStatBar()
    │   │    ├── drawFilterChips()
    │   │    ├── drawStationCards()（主要卡片）
    │   │    └── drawFooter()
    │   └── drawRainIntensityMap()（可選地圖）
    │
    ├── ── 資料擷取函式 ───────────────────────────
    │   ├── fetchRainData()（async，主要擷取邏輯）
    │   ├── parseAPIResponse(data)（欄位正規化）
    │   └── loadDemoData()（備用示範資料）
    │
    ├── ── 繪製函式 ───────────────────────────────
    │   ├── drawHeader()
    │   ├── drawStatBar()
    │   ├── drawStationCard(s, x, y, w, h)
    │   ├── drawGaugeBar(x, y, w, h, value, max)
    │   ├── drawRainDrops()
    │   └── drawLoadingScreen()
    │
    ├── ── 工具函式 ───────────────────────────────
    │   ├── getRainLevel(mm)（等級判斷）
    │   ├── getRainColor(mm)（顏色映射）
    │   ├── lerpColor2(c1, c2, t)（顏色插值）
    │   └── formatTime(recTime)（時間格式化）
    │
    └── ── 事件函式 ───────────────────────────────
        ├── mousePressed()（點擊互動）
        ├── mouseMoved()（hover 偵測）
        └── windowResized()（RWD 響應）
```

### 4.2 p5.js 生命週期回顧

```javascript
// 只執行一次：載入資源
function preload() {
  monoFont = loadFont('https://fonts.gstatic.com/.../ShareTechMono.ttf');
}

// 只執行一次：初始化
function setup() {
  createCanvas(windowWidth, windowHeight);
  frameRate(60);
  initRainDrops();    // 初始化背景粒子
  fetchRainData();    // 啟動 API 資料擷取（async）
}

// 每幀執行（60fps）：所有視覺更新都在這裡
function draw() {
  background(6, 11, 24);    // 深藍黑底色
  updateRainDrops();         // 更新粒子位置
  drawRainDrops();           // 繪製粒子
  drawDashboard();           // 繪製儀表板內容
}
```

---

## 5. API 連線與資料擷取

### 5.1 fetchRainData() 完整實作

```javascript
const API_URL = 'https://wic.gov.taipei/OpenData/API/Rain/Get' +
  '?stationNo=&loginId=open_rain&dataKey=85452C1D';

async function fetchRainData() {
  isLoading = true;

  try {
    // ① 發送 HTTP GET 請求（含 8 秒超時保護）
    const response = await Promise.race([
      fetch(API_URL, {
        method: 'GET',
        headers: { 'Accept': 'application/json' }
      }),
      new Promise((_, reject) =>
        setTimeout(() => reject(new Error('連線逾時（8秒）')), 8000)
      )
    ]);

    // ② 檢查 HTTP 狀態碼
    if (!response.ok) {
      throw new Error(`伺服器回傳錯誤 HTTP ${response.status}`);
    }

    // ③ 解析 JSON 主體
    const rawData = await response.json();

    // ④ 正規化欄位（因 API 格式可能改變）
    const parsed = parseAPIResponse(rawData);

    if (parsed.length === 0) {
      throw new Error('API 回傳空陣列，無法取得資料');
    }

    // ⑤ 更新全域狀態
    stations = parsed;
    isLive = true;
    lastUpdate = new Date().toLocaleString('zh-TW', { hour12: false });

    console.log(`✅ 成功載入 ${stations.length} 個雨量站資料`);

  } catch (err) {
    // ⑥ 連線失敗 → 自動降級至示範資料
    console.warn('⚠️ API 連線失敗：', err.message);
    console.warn('→ 改用示範資料（功能完整）');
    stations = loadDemoData();
    isLive = false;
    lastUpdate = new Date().toLocaleString('zh-TW', { hour12: false }) + '（示範）';
  } finally {
    // ⑦ 無論成功或失敗，都關閉載入狀態
    isLoading = false;
  }
}
```

### 5.2 自動定時更新

```javascript
const REFRESH_INTERVAL = 300; // 5 分鐘（秒）
let countdown = REFRESH_INTERVAL;

// 在 draw() 中每幀遞減計數
function draw() {
  // ... 其他繪製邏輯 ...

  // 每秒遞減（frameRate=60，每60幀=1秒）
  if (frameCount % 60 === 0) {
    countdown--;
    if (countdown <= 0 && !isLoading) {
      countdown = REFRESH_INTERVAL;
      fetchRainData();  // 重新擷取
    }
  }

  // 顯示倒數進度條
  drawCountdownBar(countdown, REFRESH_INTERVAL);
}
```

### 5.3 CORS 問題說明

跨來源資源共用（CORS）是瀏覽器安全機制，當網頁嘗試從不同網域（如 `wic.gov.taipei`）擷取資料時，瀏覽器會先送出 OPTIONS 預檢請求，確認伺服器是否允許。

```
瀏覽器（你的網頁）  →  OPTIONS 請求  →  wic.gov.taipei API
                    ←  CORS headers  ←
                                        如果有 Access-Control-Allow-Origin: *
                                        ✅ 允許，繼續 GET 請求
                                        如果沒有
                                        ❌ 瀏覽器阻擋，顯示 CORS 錯誤
```

**解決方案**（當 CORS 失敗時）：
```javascript
// 方案 A：使用 CORS Proxy（開發測試用）
const PROXY = 'https://corsproxy.io/?';
const API_URL_PROXIED = PROXY + encodeURIComponent(ORIGINAL_API_URL);

// 方案 B：啟動本地伺服器（而非直接開啟 HTML 檔案）
// python -m http.server 8080
// 然後開啟 http://localhost:8080/rain-dashboard.html

// 方案 C：程式中自動降級至示範資料（本專案採用此方案）
```

---

## 6. 資料解析與正規化

### 6.1 parseAPIResponse() 函式

此函式負責將 API 回傳的原始資料轉換成程式統一使用的格式：

```javascript
function parseAPIResponse(rawData) {
  // 確保是陣列格式
  let arr = Array.isArray(rawData) ? rawData : [];

  return arr
    .map(item => {
      // 安全取值函式（避免 undefined/null）
      const safeStr = (v) => (v !== undefined && v !== null) ? String(v).trim() : '';
      const safeNum = (v) => {
        const n = parseFloat(v);
        return isNaN(n) || n < 0 ? 0 : n;  // 負值（儀器異常）視為 0
      };

      return {
        stationNo:   safeStr(item.stationNo),    // 站碼
        stationName: safeStr(item.stationName),  // 站名
        recTime:     safeStr(item.recTime),       // 記錄時間
        rain:        safeNum(item.rain),          // 雨量值（mm），負值歸零
        count:       parseInt(item.count) || 0,  // 記錄筆數
      };
    })
    .filter(item => item.stationNo !== '');  // 過濾無效資料
}
```

### 6.2 為何需要 safeNum() 處理負值？

```javascript
// API 可能在儀器異常時回傳特殊值
{ stationNo: "C0A9G0", stationName: "貴子坑", rain: -1 }  // -1 = 儀器故障
{ stationNo: "C0A9H0", stationName: "百拉卡", rain: null } // null = 無資料
{ stationNo: "C0A9I0", stationName: "白石湖", rain: "—"  } // 字串 = 特殊標示

// parseFloat("-1") = -1  → 需歸零
// parseFloat(null)  = NaN → 需歸零
// parseFloat("—")   = NaN → 需歸零
```

### 6.3 時間解析

```javascript
function formatRecTime(recTime) {
  // 輸入：" 2024-05-24 15:30:00"（可能前後有空格）
  if (!recTime) return '未知';

  const parts = recTime.trim().split(' ');
  // parts[0] = "2024-05-24"
  // parts[1] = "15:30:00"

  if (parts.length < 2) return recTime;

  const timeParts = parts[1].split(':');
  return `${parts[0]} ${timeParts[0]}:${timeParts[1]}`;
  // 輸出："2024-05-24 15:30"
}

// 在 p5.js 中顯示
textFont(monoFont);
textSize(11);
fill(100, 150, 200);
text('更新：' + formatRecTime(station.recTime), x, y);
```

---

## 7. 視覺化設計說明

### 7.1 整體色彩系統

```javascript
const COLORS = {
  // 背景層
  bg:      [6,   11,  24],   // 深海藍黑（主背景）
  panel:   [10,  16,  32],   // 深藍（頂部面板）
  card:    [13,  21,  48],   // 藍黑（卡片底色）
  cardHov: [17,  32,  64],   // 稍亮（hover 狀態）

  // 強調色
  cyan:    [0,   212, 255],  // 主青色（正常狀態、儀表數字）
  green:   [0,   255, 136],  // 綠色（微小降雨）
  yellow:  [255, 184, 0],    // 黃色（中等降雨）
  orange:  [255, 107, 0],    // 橘色（大雨）
  red:     [255, 23,  68],   // 紅色（豪雨）

  // 文字層
  txt:     [200, 224, 248],  // 主文字
  txt2:    [106, 138, 170],  // 次要文字
  txt3:    [58,  90,  122],  // 說明文字（最淡）
};
```

### 7.2 站牌卡片繪製

```javascript
function drawStationCard(station, x, y, cardW, cardH) {
  const rain = station.rain;
  const level = getRainLevel(rain);

  // ① 卡片底色
  noStroke();
  fill(...COLORS.card);
  rect(x, y, cardW, cardH, 6);

  // ② 頂部警戒色條（3px 高）
  fill(...level.color);
  rect(x, y, cardW, 3, 3, 3, 0, 0);

  // ③ 站名（中文字型）
  textFont(notoFont);
  textSize(14);
  fill(255);
  text(station.stationName, x + 12, y + 22);

  // ④ 雨量 gauge 條（視覺化核心）
  const gaugeMaxMM = 30;  // 30mm = 滿格
  const gaugeW = cardW - 24;
  const gaugeH = 8;
  const gaugeY = y + cardH - 32;

  // 底軌道（灰色）
  fill(30, 45, 70);
  rect(x + 12, gaugeY, gaugeW, gaugeH, 2);

  // 填充條（依雨量比例）
  const fillRatio = Math.min(rain / gaugeMaxMM, 1.0);
  if (fillRatio > 0) {
    // 漸層效果（從左到右顏色加深）
    for (let i = 0; i < gaugeW * fillRatio; i++) {
      const t = i / (gaugeW * fillRatio);
      const c = lerpColorArrays([0, 100, 200], level.color, t);
      stroke(...c);
      strokeWeight(1);
      line(x + 12 + i, gaugeY, x + 12 + i, gaugeY + gaugeH);
    }
    noStroke();
  }

  // ⑤ 雨量數值（Monospace 字型）
  textFont(monoFont);
  textSize(20);
  fill(...level.color);
  textAlign(RIGHT);
  text(rain.toFixed(1), x + cardW - 12, y + cardH - 10);

  textSize(11);
  fill(...COLORS.txt3);
  text('mm', x + cardW - 12, y + cardH + 2);
  textAlign(LEFT);

  // ⑥ 記錄時間
  textSize(10);
  fill(...COLORS.txt3);
  text(formatRecTime(station.recTime), x + 12, y + cardH - 10);
}
```

### 7.3 gauge bar 動畫插值

p5.js 的核心動畫技術：使用 `lerp()` 讓 gauge bar 從舊值平滑過渡到新值：

```javascript
// 全域：儲存每站的「目前顯示高度」（動畫插值用）
let displayRain = {};  // { stationNo: currentAnimValue }

function draw() {
  // 在每幀更新顯示值，朝目標值以 7% 速率靠近
  stations.forEach(s => {
    const current = displayRain[s.stationNo] || 0;
    const target  = s.rain;
    displayRain[s.stationNo] = lerp(current, target, 0.07);
  });

  // 用 displayRain（而非直接用 s.rain）繪製 gauge bar
  // → 產生平滑的水位上升/下降動畫效果
}
```

### 7.4 背景雨滴粒子系統

```javascript
let rainDrops = [];

function initRainDrops() {
  for (let i = 0; i < 150; i++) {
    rainDrops.push({
      x:     random(width),
      y:     random(-height, height),  // 從畫面上方隨機位置開始
      len:   random(8, 25),            // 雨滴長度
      speed: random(6, 14),            // 下落速度
      alpha: random(20, 80),           // 透明度（很透明，只是點綴）
    });
  }
}

function drawRainDrops() {
  stroke(0, 212, 255, 40);  // 淡青色
  strokeWeight(1);
  rainDrops.forEach(drop => {
    // 繪製斜向雨滴線段（微微往右傾斜）
    line(drop.x,           drop.y,
         drop.x + 2,       drop.y + drop.len);  // 右傾 2px = 自然感

    // 下落
    drop.y += drop.speed;

    // 超出畫面底部 → 從頂部重新出現
    if (drop.y > height + drop.len) {
      drop.y = -drop.len;
      drop.x = random(width);
    }
  });
  noStroke();
}
```

---

## 8. 動畫與互動功能

### 8.1 頁面中的所有動畫

| 動畫元素 | 技術 | 效果 |
|---------|------|------|
| 背景雨滴 | 粒子系統（每幀更新位置） | 斜向下落的細雨效果 |
| Gauge 條 | `lerp()` 插值 | 雨量值改變時水位平滑升降 |
| 卡片頂色條 | CSS 顏色過渡 | 警戒等級改變時顏色漸變 |
| 載入動畫 | `sin(frameCount)` | 旋轉點陣 + 進度條脈動 |
| 頂部狀態點 | `sin(frameCount*0.05)` | 綠色呼吸燈（連線中） |
| 倒數進度條 | 每秒遞減 | 線性縮短 |

### 8.2 mouseMoved() — hover 效果

```javascript
let hoveredCard = -1;  // 目前 hover 的卡片索引（-1 = 無）

function mouseMoved() {
  hoveredCard = -1;
  cardBounds.forEach((b, i) => {
    if (mouseX >= b.x && mouseX <= b.x + b.w &&
        mouseY >= b.y && mouseY <= b.y + b.h) {
      hoveredCard = i;
    }
  });
  // 根據 hover 狀態改變游標
  cursor(hoveredCard >= 0 ? HAND : ARROW);
}

// 在 drawStationCard() 中：
function drawStationCard(station, x, y, cardW, cardH, index) {
  const isHovered = (index === hoveredCard);

  // hover 時底色更亮
  fill(...(isHovered ? COLORS.cardHov : COLORS.card));
  rect(x, y, cardW, cardH, 6);

  // hover 時顯示更多資訊（如站碼）
  if (isHovered) {
    textSize(10);
    fill(...COLORS.txt3);
    text(`站碼：${station.stationNo}`, x + 12, y + 38);
  }
}
```

### 8.3 mousePressed() — 點擊篩選

```javascript
function mousePressed() {
  // 點擊行政區 chip → 切換篩選
  districtChips.forEach(chip => {
    if (mouseX >= chip.x && mouseX <= chip.x + chip.w &&
        mouseY >= chip.y && mouseY <= chip.y + chip.h) {
      selectedDistrict = (selectedDistrict === chip.label) ? '全部' : chip.label;
    }
  });

  // 點擊「重新整理」按鈕 → 手動重新擷取 API
  if (isInsideRefreshBtn(mouseX, mouseY)) {
    countdown = REFRESH_INTERVAL;
    fetchRainData();
  }
}
```

---

## 9. 雨量警戒等級設計

### 9.1 等級定義（依 `rain` 欄位值 mm）

| 等級 | 閾值（mm） | 標籤 | 顏色 | 對應情境 |
|------|-----------|------|------|---------|
| 0 | = 0.0 | 無雨 | 灰色 `[42,58,90]` | 乾燥晴天 |
| 1 | 0.0 ~ 1.0 | 微雨 | 青色 `[0,212,255]` | 毛毛雨、濛濛細雨 |
| 2 | 1.0 ~ 4.0 | 小雨 | 綠色 `[0,255,136]` | 一般下雨 |
| 3 | 4.0 ~ 10.0 | 中雨 | 黃色 `[255,184,0]` | 明顯降雨，建議攜傘 |
| 4 | 10.0 ~ 20.0 | 大雨 | 橘色 `[255,107,0]` | 需注意積水 |
| 5 | ≥ 20.0 | 豪雨 | 紅色 `[255,23,68]` | 需注意安全，防範洪水 |

> **注意**：本專案的 `rain` 欄位為**當次觀測時段（約10分鐘）的累積雨量**，並非每小時雨量。與中央氣象署的大雨標準（時雨量≥10mm）有所不同，使用時請依實際 API 資料定義調整閾值。

### 9.2 getRainLevel() 實作

```javascript
const THRESHOLDS = [
  { min: 0,    max: 0,    label: '無雨', color: [42,  58,  90],  level: 0 },
  { min: 0.01, max: 1,    label: '微雨', color: [0,   212, 255], level: 1 },
  { min: 1,    max: 4,    label: '小雨', color: [0,   255, 136], level: 2 },
  { min: 4,    max: 10,   label: '中雨', color: [255, 184, 0],   level: 3 },
  { min: 10,   max: 20,   label: '大雨', color: [255, 107, 0],   level: 4 },
  { min: 20,   max: 9999, label: '豪雨', color: [255, 23,  68],  level: 5 },
];

function getRainLevel(mm) {
  for (const t of THRESHOLDS) {
    if (mm >= t.min && mm < t.max) return t;
    if (mm >= t.min && t.max === 9999) return t;  // 最高等級
  }
  return THRESHOLDS[0];  // 預設無雨
}
```

### 9.3 統計摘要列的警戒計算

```javascript
// 在 drawStatBar() 中計算並顯示各等級統計
const rainingCount = stations.filter(s => s.rain > 0).length;
const alertCount   = stations.filter(s => s.rain >= 10).length;
const maxStation   = stations.reduce((max, s) => s.rain > max.rain ? s : max, stations[0]);
const avgRain      = stations.reduce((sum, s) => sum + s.rain, 0) / stations.length;
```

---

## 10. 自動更新機制

### 10.1 倒數計時與自動更新的完整流程

```javascript
const REFRESH_SEC = 300;  // 5 分鐘 = 300 秒
let countdown = REFRESH_SEC;
let autoRefreshEnabled = true;

function draw() {
  // ... 其他繪製 ...

  // 每秒（60幀）執行一次
  if (frameCount % 60 === 0 && !isLoading) {
    if (autoRefreshEnabled) {
      countdown--;
      if (countdown <= 0) {
        countdown = REFRESH_SEC;
        fetchRainData();   // 自動重新擷取
      }
    }
  }

  // 繪製倒數進度條
  const pct = countdown / REFRESH_SEC;
  // 底軌
  noStroke(); fill(30, 45, 70);
  rect(barX, barY, barW, 3);
  // 進度
  fill(0, 212, 255);
  rect(barX, barY, barW * pct, 3);

  // 顯示剩餘秒數
  textFont(monoFont); textSize(11); fill(100, 150, 200);
  text(`${countdown}s`, barX + barW + 8, barY + 3);
}
```

### 10.2 為何設定 5 分鐘更新？

- **API 更新頻率**：臺北市水利處雨量 API 每 **10 分鐘**更新一次
- **合理的更新頻率**：5 分鐘更新確保不會遺漏最新資料，也不會對伺服器造成過大負擔
- **實際降雨變化**：降雨強度通常不會在 5 分鐘內劇烈變化，此頻率足夠即時

---

## 11. 錯誤處理與備用資料

### 11.1 三層降級策略

```
層級 1：API 連線成功 → 使用即時資料（最優，標示「● LIVE API」）
         ↓ 失敗（CORS / 網路 / 伺服器錯誤）
層級 2：自動切換備用示範資料（標示「● DEMO DATA」，功能完整）
         ↓ 使用者點擊重試
層級 3：再次嘗試連線（回到層級 1）
```

### 11.2 備用示範資料設計原則

```javascript
function loadDemoData() {
  // 模擬真實臺北雨量站分佈
  // 包含各行政區的代表性站台
  // 雨量值反映真實降雨分佈（山區較多，平地較少）
  return [
    { stationNo: 'C0A9G0', stationName: '貴子坑',
      recTime: getCurrentTimeStr(), rain: 18.2, count: 27 },  // 北投山區
    { stationNo: 'C0A9H0', stationName: '百拉卡',
      recTime: getCurrentTimeStr(), rain: 22.6, count: 27 },  // 士林山區（最高）
    { stationNo: 'C0A9L1', stationName: '貓空',
      recTime: getCurrentTimeStr(), rain: 16.5, count: 27 },  // 文山山區
    { stationNo: 'C0A9M0', stationName: '大安',
      recTime: getCurrentTimeStr(), rain: 0.4,  count: 27 },  // 市中心（最低）
    // ... 更多站台 ...
  ];
}

// 取得目前時間字串（格式同 API 的 recTime 欄位）
function getCurrentTimeStr() {
  const now = new Date();
  const pad = n => String(n).padStart(2, '0');
  return `${now.getFullYear()}-${pad(now.getMonth()+1)}-${pad(now.getDate())} ` +
         `${pad(now.getHours())}:${pad(Math.floor(now.getMinutes()/10)*10)}:00`;
}
```

### 11.3 異常資料過濾

```javascript
// 過濾並修正可能的異常資料
function parseAPIResponse(rawData) {
  return rawData
    .map(item => ({
      stationNo:   String(item.stationNo || '').trim(),
      stationName: String(item.stationName || '未知站').trim(),
      recTime:     String(item.recTime || '').trim(),
      rain:        Math.max(0, parseFloat(item.rain) || 0),  // 負值歸零
      count:       parseInt(item.count) || 0,
    }))
    .filter(item =>
      item.stationNo !== '' &&          // 必須有站碼
      item.stationName !== '' &&        // 必須有站名
      item.rain <= 500                  // 雨量超過 500mm 視為異常值過濾
    );
}
```

---

## 12. 延伸應用與練習

### 練習 1：單站歷史折線圖（簡單）
```javascript
// 每次更新時儲存歷史值
const rainHistory = {};  // { stationNo: [v1, v2, v3, ...] }

function fetchRainData() {
  // ... 現有邏輯 ...
  stations.forEach(s => {
    if (!rainHistory[s.stationNo]) rainHistory[s.stationNo] = [];
    rainHistory[s.stationNo].push(s.rain);
    if (rainHistory[s.stationNo].length > 24) {
      rainHistory[s.stationNo].shift();  // 最多保留 24 筆（2小時）
    }
  });
}

// 繪製折線圖
function drawHistory(stationNo, x, y, w, h) {
  const hist = rainHistory[stationNo] || [];
  // 用 beginShape / curveVertex 繪製平滑折線
}
```

### 練習 2：台北地圖定位（進階）
```javascript
// 使用已知的站台座標（需另外查詢）
const stationCoords = {
  'C0A9G0': { lat: 25.13, lng: 121.47, name: '貴子坑' },
  'C0A9H0': { lat: 25.17, lng: 121.54, name: '百拉卡' },
  // ...
};

// 將經緯度轉換為畫布座標（簡單投影）
function latLngToCanvas(lat, lng) {
  const mapLeft = 121.44, mapRight = 121.68;
  const mapTop  = 25.22, mapBottom = 24.98;
  const x = map(lng, mapLeft,   mapRight,  mapX, mapX + mapW);
  const y = map(lat, mapTop,    mapBottom, mapY, mapY + mapH);
  return { x, y };
}
```

### 練習 3：聲音回饋（創意）
```javascript
// 當偵測到豪雨等級時播放提示音
// 使用 p5.js 搭配 Tone.js
import * as Tone from 'tone';

function checkRainAlert(stations) {
  const hasExtreme = stations.some(s => s.rain >= 20);
  if (hasExtreme && !alertPlayed) {
    const synth = new Tone.Synth().toDestination();
    synth.triggerAttackRelease('A4', '0.3');  // 短促警示音
    alertPlayed = true;
  }
}
```

### 練習 4：查詢特定站台
```javascript
// 修改 API 請求，只查詢特定站台
const TARGET_STATION = 'C0A9G0';  // 貴子坑
const SINGLE_STATION_URL =
  `https://wic.gov.taipei/OpenData/API/Rain/Get` +
  `?stationNo=${TARGET_STATION}&loginId=open_rain&dataKey=85452C1D`;

// 可建立下拉選單讓使用者選擇站台
```

---

## 13. 常見問題 FAQ

**Q1：API 回傳的 `rain` 是什麼時間區間的雨量？**
> 此欄位為雨量站在 `recTime` 時間點的**即時觀測值**，通常反映最近 10 分鐘（或當次觀測區間）的累積降雨量（mm）。不同於氣象局的「時雨量」概念，請依實際 API 文件說明使用。

**Q2：`count` 每筆都一樣，要怎麼使用？**
> `count` 代表本次查詢回傳的**總站數**，可用於驗證資料完整性。例如：若 `count` = 33 但陣列長度只有 25，代表部分站台資料可能遺失或延遲。
> ```javascript
> const expectedCount = data[0]?.count || 0;
> const actualCount   = data.length;
> if (actualCount < expectedCount) {
>   console.warn(`資料不完整：預期 ${expectedCount} 筆，實際得到 ${actualCount} 筆`);
> }
> ```

**Q3：為什麼在本地端開啟 HTML 會有 CORS 錯誤？**
> 瀏覽器的安全機制（Same-Origin Policy）會阻止從本地端（`file://`）直接呼叫外部 API。解決方法：
> ```bash
> # 使用 Python 啟動本地伺服器
> python -m http.server 8080
> # 然後開啟 http://localhost:8080/taipei-rain-p5.html
> ```

**Q4：p5.js 的 `fetch()` 和一般 JavaScript 的 `fetch()` 一樣嗎？**
> 是的，p5.js 沒有特別包裝 `fetch()`，直接使用瀏覽器原生的 Fetch API 即可。p5.js 有提供 `loadJSON()`，但不支援自訂 headers 和 timeout，建議改用原生 `fetch()` + `async/await`。

**Q5：可以把此儀表板部署到公開網站嗎？**
> 可以，使用臺北市開放資料無需申請即可商業或非商業應用（OGDL 授權）。但建議：①在頁面上標示資料來源；②注意 API 使用量，避免過於頻繁的請求；③不要在程式碼中直接暴露 dataKey（建議以後端 Proxy 隱藏）。

**Q6：如何取得更多雨量站的資訊（如座標、行政區）？**
> 此 API 的 `rain` 資料集不包含地理座標和行政區。如需這些資訊，可搭配使用：
> - 臺北市資料大平臺上的「雨量站基本資料」資料集
> - 或透過站碼（`stationNo`）查詢水利處提供的站台清單

---

## 14. 附錄：完整 API 欄位速查

### 14.1 API 請求

```
方法：GET
URL：https://wic.gov.taipei/OpenData/API/Rain/Get
參數：
  stationNo  = （空白 = 全部站，填入站碼 = 單站）
  loginId    = open_rain（固定值，公開帳號）
  dataKey    = 85452C1D（固定值，公開金鑰）
```

### 14.2 API 回傳欄位

| 欄位名稱 | 中文說明 | 資料型別 | 範例值 | 備註 |
|---------|---------|---------|-------|------|
| `count` | 記錄筆數（總站數） | Integer | `33` | 每筆資料此值相同 |
| `stationNo` | 站碼 | String | `"C0A9G0"` | 唯一識別碼，可作為主鍵 |
| `stationName` | 站台名稱 | String | `"貴子坑"` | 中文地名 |
| `recTime` | 記錄時間 | String | `"2024-05-24 15:30:00"` | 台灣本地時間（UTC+8） |
| `rain` | 雨量值 | Float | `2.5` | 單位：mm；負值代表儀器異常 |

### 14.3 資料集說明頁

```
URL：https://data.taipei/dataset/detail?id=6f03a0b8-7b98-4eea-8bb9-ba6bfcdc2b8b
平台：臺北市資料大平臺（data.taipei）
授權：政府資料開放授權條款（OGDL）
```

### 14.4 p5.js 常用 API 對照

```javascript
// 畫布
createCanvas(w, h)          // 建立 Canvas
background(r, g, b)         // 清除背景
width / height              // 目前 Canvas 尺寸

// 顏色
fill(r, g, b, a)            // 設定填色
stroke(r, g, b, a)          // 設定線條色
noFill() / noStroke()

// 圖形
rect(x, y, w, h, r)         // 圓角矩形
circle(x, y, d)             // 圓形
line(x1, y1, x2, y2)        // 線段

// 文字
textFont('字型名稱')          // 設定字型
textSize(n)                  // 字體大小
textAlign(H, V)              // 對齊方式
text('內容', x, y)           // 繪製文字

// 動畫數學
lerp(a, b, t)                // 線性插值（t = 0~1）
map(v, in1, in2, out1, out2) // 數值映射
frameCount                   // 目前幀數（累計）
frameRate(fps)               // 設定幀率

// 互動
mouseX / mouseY              // 滑鼠座標
mousePressed()               // 點擊事件
mouseMoved()                 // 移動事件
```

---

*本講義版本：v1.0*
*製作日期：2026 年 5 月*
*資料授權：政府資料開放授權條款（OGDL）— 臺北市資料大平臺*
*程式框架：p5.js（MIT License）— https://p5js.org*
*API 提供：臺北市政府水利處 — https://wic.gov.taipei*
