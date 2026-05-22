---
title: React 政府開放資料地圖 實作講義
tags: [114_下學期_互動程式設計]

---

# ⚛️ React 政府開放資料地圖 實作講義
### YouBike 即時站點 × 公車即時追蹤 × Leaflet × TDX × GitHub Pages

---

> **適用對象**：具備基礎 HTML/CSS/JavaScript 概念，想學習 React 框架的學習者  
> **完成目標**：用 React 18 製作一個結合政府開放資料與地圖的響應式網頁，並部署到 GitHub Pages

---

## 📋 目錄

1. [專案概覽](#1-專案概覽)
2. [React 與 Vue 的差異比較](#2-react-與-vue-的差異比較)
3. [環境安裝](#3-環境安裝)
4. [單機測試（本機開發）](#4-單機測試本機開發)
5. [專案結構說明](#5-專案結構說明)
6. [核心程式碼解說](#6-核心程式碼解說)
7. [TDX API 設定與 429 錯誤處理](#7-tdx-api-設定與-429-錯誤處理)
8. [上傳到 GitHub 並部署](#8-上傳到-github-並部署)
9. [響應式設計說明](#9-響應式設計說明)
10. [與 AI 對話：進一步擴充](#10-與-ai-對話進一步擴充)
11. [常見問題排查](#11-常見問題排查)

---

## 1. 專案概覽

### 1.1 系統架構

```
使用者瀏覽器（手機 / 平板 / 電腦）
          │
          ▼
┌─────────────────────────────────┐
│       React 18 前端介面          │  ← GitHub Pages 部署
│  ┌─────────────┐ ┌───────────┐  │
│  │YouBike 頁面  │ │ 公車頁面  │  │
│  │ - 站點地圖  │ │ - 即時位置│  │
│  │ - 可借/可還 │ │ - 站牌路線│  │
│  └─────────────┘ └───────────┘  │
│  ┌──────────────────────────┐   │
│  │  Leaflet + OpenStreetMap  │   │  ← 完全免費地圖
│  └──────────────────────────┘   │
└───────────────┬─────────────────┘
                │ fetch（無需付費）
                ▼
┌─────────────────────────────────┐
│   TDX 交通部運輸資料平台          │  ← 政府免費開放資料
│  - YouBike 站點位置              │
│  - YouBike 即時車輛數            │
│  - 公車即時 GPS 位置             │
│  - 公車站牌資料                  │
└─────────────────────────────────┘
```

### 1.2 使用技術（全部免費）

| 技術 | 用途 | 費用 |
|------|------|------|
| React 18 | 前端框架 | 免費開源 |
| Vite | 開發工具 / 打包 | 免費開源 |
| Leaflet.js | 互動式地圖 | 免費開源 |
| OpenStreetMap | 地圖圖層 | 永久免費 |
| TDX API | 政府交通資料 | 免費（有限速）|
| GitHub Pages | 網站部署 | 免費 |

### 1.3 功能一覽

| 功能 | 說明 |
|------|------|
| 🚲 YouBike 站點地圖 | 全台各城市站點即時可借/可還數量 |
| 🎨 顏色分類標記 | 紅=無車、橘=少量、黃=普通、綠=充足 |
| 🔍 搜尋與篩選 | 依名稱搜尋、依狀態篩選站點 |
| 📊 統計資訊 | 即時顯示總站點數、可借車輛、可還空位 |
| 🚌 公車即時追蹤 | 在地圖上看到公車目前位置 |
| 📍 路線站牌 | 顯示路線站牌順序與位置 |
| 🔄 自動更新 | 每 60 秒自動重新載入資料 |
| 📱 響應式設計 | 手機、平板、電腦自動調整版面 |
| 🔑 TDX 帳號設定 | 可選填帳號提高 API 配額 |

---

## 2. React 與 Vue 的差異比較

如果你學過 Vue，以下對照表幫助你快速理解 React：

### 2.1 核心概念對照

| 概念 | Vue 3 寫法 | React 18 寫法 |
|------|-----------|--------------|
| 響應式變數 | `const count = ref(0)` | `const [count, setCount] = useState(0)` |
| 修改變數 | `count.value++` | `setCount(count + 1)` |
| 計算屬性 | `const total = computed(() => ...)` | `const total = useMemo(() => ..., [deps])` |
| 生命週期（載入後）| `onMounted(() => ...)` | `useEffect(() => ..., [])` |
| 生命週期（離開前）| `onUnmounted(() => ...)` | `useEffect(() => { return () => 清除 }, [])` |
| 邏輯復用 | Composable（`.js` 函式）| Custom Hook（`use` 開頭的函式）|
| DOM 參考 | `const el = ref(null)` + `ref="el"` | `const el = useRef(null)` + `ref={el}` |
| 樣式隔離 | `<style scoped>` | CSS Modules（`.module.css`）|

### 2.2 模板語法對照

| 功能 | Vue | React（JSX）|
|------|-----|------------|
| 顯示變數 | `{{ name }}` | `{name}` |
| 動態 class | `:class="{ active: isActive }"` | `className={isActive ? 'active' : ''}` |
| 點擊事件 | `@click="handleClick"` | `onClick={handleClick}` |
| 條件顯示 | `v-if="show"` | `{show && <Component />}` |
| 列表渲染 | `v-for="item in list" :key="item.id"` | `{list.map(item => <div key={item.id}>)}` |
| 雙向綁定 | `v-model="value"` | `value={val} onChange={e => setVal(e.target.value)}` |

### 2.3 元件結構對照

**Vue：**
```vue
<template>
  <div>{{ message }}</div>
</template>

<script setup>
import { ref } from 'vue'
const message = ref('Hello Vue!')
</script>

<style scoped>
div { color: red; }
</style>
```

**React（JSX）：**
```jsx
import { useState } from 'react'
import styles from './Component.module.css'

export default function Component() {
  const [message] = useState('Hello React!')

  return (
    <div className={styles.text}>{message}</div>
  )
}
```

> 💡 **React 最大不同點：HTML 寫在 JavaScript 裡（JSX），不是分開的 `<template>`。**

---

## 3. 環境安裝

### 3.1 安裝 Node.js

```bash
# 確認是否已安裝（需要 18 以上版本）
node --version

# 沒有安裝請至 https://nodejs.org 下載 LTS 版本
```

### 3.2 下載並解壓縮專案

1. 下載 `react-opendata.zip`
2. 解壓縮到任意資料夾，例如：`D:\projects\react-opendata`
3. 用 VS Code 開啟該資料夾

### 3.3 安裝專案依賴套件

開啟終端機（VS Code 內按 `` Ctrl + ` ``），執行：

```bash
# 進入專案資料夾
cd react-opendata

# 安裝所有依賴套件
npm install
```

安裝完成後，資料夾會多出 `node_modules/` 目錄（約 100MB，不需上傳到 GitHub）。

---

## 4. 單機測試（本機開發）

### 4.1 啟動開發伺服器

```bash
npm run dev
```

成功後終端機會顯示：

```
  VITE v5.x.x  ready in 300 ms

  ➜  Local:   http://localhost:5173/
  ➜  Network: http://192.168.x.x:5173/
```

開啟瀏覽器，輸入 `http://localhost:5173/` 即可看到網頁。

### 4.2 本機開發的特色

| 功能 | 說明 |
|------|------|
| 熱更新（HMR） | 存檔後瀏覽器自動重新整理，不需手動重新整理 |
| 錯誤提示 | 程式碼有錯誤會直接顯示在瀏覽器畫面上 |
| 速度快 | Vite 使用原生 ES Module，啟動幾乎瞬間完成 |

### 4.3 修改後測試流程

```
修改 .jsx 或 .css 檔案
        ↓
儲存檔案（Ctrl + S）
        ↓
瀏覽器自動更新（不需重新整理）
        ↓
確認修改結果
```

### 4.4 手動打包測試

若想測試上線版本的效果：

```bash
# 打包成正式版本
npm run build

# 本機預覽打包結果
npm run preview
```

預覽網址通常是 `http://localhost:4173/react-opendata/`

### 4.5 開發工具建議

安裝 VS Code 擴充套件：

| 套件名稱 | 功能 |
|---------|------|
| **ES7+ React/Redux/React-Native snippets** | 快速建立 React 元件 |
| **Prettier** | 程式碼自動排版 |
| **ESLint** | 程式碼錯誤提示 |
| **Auto Rename Tag** | 自動同步修改 HTML 標籤 |

---

## 5. 專案結構說明

```
react-opendata/
│
├── 📄 index.html              ← 網頁進入點（只有一個空的 <div id="root">）
├── 📄 vite.config.js          ← Vite 設定（base 路徑要改）
├── 📄 package.json            ← 專案資訊與依賴套件清單
├── 📄 .gitignore              ← Git 忽略清單
│
├── 📁 public/                 ← 靜態資源（直接複製到輸出）
│
├── 📁 src/                    ← 所有 React 原始碼
│   │
│   ├── 📄 main.jsx            ← React 程式進入點（掛載 App 到 DOM）
│   ├── 📄 App.jsx             ← 主元件（標籤切換 + TDX 帳號設定）
│   ├── 📄 App.module.css      ← App 的樣式（CSS Modules）
│   ├── 📄 index.css           ← 全域樣式（字體、reset）
│   │
│   ├── 📁 hooks/              ← 自訂 Hook（邏輯層）
│   │   ├── 📄 tdxToken.js     ← TDX Token 管理（快取、自動更新）
│   │   ├── 📄 useYouBike.js   ← YouBike 資料載入邏輯
│   │   └── 📄 useBus.js       ← 公車資料載入邏輯
│   │
│   └── 📁 components/         ← 元件（畫面層）
│       ├── 📄 LeafletMap.jsx   ← 可重用地圖元件
│       ├── 📄 YouBikeView.jsx  ← YouBike 頁面（整合地圖 + 面板）
│       ├── 📄 YouBikePanel.jsx ← YouBike 左側控制面板
│       ├── 📄 YouBikePanel.module.css
│       ├── 📄 BusView.jsx      ← 公車頁面
│       └── 📄 BusView.module.css
│
└── 📁 .github/workflows/
    └── 📄 deploy.yml          ← GitHub Actions 自動部署設定
```

> 💡 **React 的分層概念：**
> - `hooks/` = 資料層（抓資料、處理邏輯）
> - `components/` = 畫面層（顯示、互動）
> - 兩者分開，讓程式碼更易維護

---

## 6. 核心程式碼解說

### 6.1 自訂 Hook：useYouBike.js

自訂 Hook 是 React 邏輯復用的方式（類似 Vue 的 Composable）：

```javascript
// src/hooks/useYouBike.js

import { useState, useEffect, useCallback } from 'react'

export function useYouBike(city, clientId, clientSecret) {
  // useState：定義響應式狀態
  const [stations,   setStations]   = useState([])   // 站點資料
  const [isLoading,  setIsLoading]  = useState(false) // 載入中？
  const [error,      setError]      = useState(null)  // 錯誤訊息
  const [lastUpdate, setLastUpdate] = useState('')    // 最後更新時間

  // useCallback：避免函式每次渲染都重新建立
  const load = useCallback(async () => {
    setIsLoading(true)
    try {
      // ... 抓 API 資料 ...
      setStations(merged)             // 更新站點資料
      setLastUpdate(new Date()...)    // 更新時間
    } catch (err) {
      setError(err.message)
    } finally {
      setIsLoading(false)
    }
  }, [city, clientId, clientSecret])  // 依賴項目：這些改變時重新建立函式

  // useEffect：元件掛載時執行，類似 Vue 的 onMounted
  useEffect(() => {
    load()                               // 立即執行一次
    const timer = setInterval(load, 60000) // 每 60 秒自動更新

    // return 的函式在元件離開時執行（類似 Vue 的 onUnmounted）
    return () => clearInterval(timer)
  }, [load])  // load 函式改變時重新執行

  // 回傳外部需要的資料和函式
  return { stations, isLoading, error, lastUpdate, reload: load }
}
```

**使用方式（在元件裡）：**

```jsx
// 就像 Vue 的 Composable：const { stations } = useYouBike(city)
const { stations, isLoading, error, lastUpdate, reload } = useYouBike(
  city, clientId, clientSecret
)
```

### 6.2 CSS Modules（樣式隔離）

React 沒有 Vue 的 `<style scoped>`，改用 CSS Modules 達到相同效果：

```css
/* YouBikePanel.module.css */
.card {
  background: #0f172a;
  border-radius: 10px;
  /* 這個 .card 只作用於這個元件，不會污染全域 */
}
```

```jsx
// YouBikePanel.jsx
import styles from './YouBikePanel.module.css'

export default function YouBikePanel() {
  return (
    // 使用 styles.xxx 引用，Vite 會自動加上唯一雜湊
    // 實際 class 會變成 .card_a1b2c3 這樣的格式
    <div className={styles.card}>...</div>
  )
}
```

### 6.3 forwardRef：讓父元件控制地圖

React 的 `ref` 只能往下傳，`forwardRef` 讓子元件把方法暴露給父元件：

```jsx
// LeafletMap.jsx
import { forwardRef, useImperativeHandle, useRef, useEffect } from 'react'
import L from 'leaflet'

// forwardRef：把父元件傳來的 ref 接住
const LeafletMap = forwardRef(function LeafletMap({ center, zoom }, ref) {
  const mapEl  = useRef(null)   // 綁定 DOM 元素
  const mapRef = useRef(null)   // 存 Leaflet 地圖實例

  // useImperativeHandle：定義父元件可以呼叫什麼方法
  useImperativeHandle(ref, () => ({
    getMap: () => mapRef.current   // 父元件呼叫 mapRef.current.getMap() 取得地圖
  }))

  useEffect(() => {
    mapRef.current = L.map(mapEl.current).setView(center, zoom)
    L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png').addTo(mapRef.current)
    return () => { mapRef.current?.remove() }   // 清除地圖
  }, [])

  return <div ref={mapEl} style={{ width:'100%', height:'100%' }} />
})

export default LeafletMap
```

**父元件使用地圖：**

```jsx
// YouBikeView.jsx
const mapRef = useRef(null)

// 取得地圖實例，呼叫 Leaflet 的方法
const map = mapRef.current?.getMap()
map.setView([lat, lng], 17)

return <LeafletMap ref={mapRef} center={[25.04, 121.53]} zoom={13} />
```

### 6.4 條件渲染（v-if 的 React 版）

```jsx
{/* Vue 的 v-if="isLoading" */}
{isLoading && <div className={styles.loading}>⏳ 載入中...</div>}

{/* Vue 的 v-if="error" v-else-if="success" */}
{error   && <div className={styles.error}>❌ {error}</div>}
{!error && stations.length > 0 && <div className={styles.success}>✅ 載入完成</div>}

{/* Vue 的 v-for="s in stations" :key="s.uid" */}
{stations.map(s => (
  <div key={s.uid} className={styles.card}>
    {s.name}
  </div>
))}
```

---

## 7. TDX API 設定與 429 錯誤處理

### 7.1 什麼是 429 錯誤？

```
HTTP 429 Too Many Requests
```

TDX 對沒有填帳號的使用者，每個 IP 每秒有請求次數限制。  
YouBike 功能需要同時打兩支 API（站點位置 + 即時車輛數），很容易超過限制。

### 7.2 三層防護機制

**第一層：Token 快取（tdxToken.js）**

```javascript
let cachedToken = null
let tokenExpiry = 0

export async function getTDXToken(clientId, clientSecret) {
  // Token 還有效就直接回傳，不重複申請
  if (cachedToken && Date.now() < tokenExpiry) return cachedToken

  // 向 TDX 取得新 Token
  const res = await fetch('https://tdx.transportdata.tw/auth/.../token', {
    method: 'POST',
    body: `grant_type=client_credentials&client_id=${clientId}&client_secret=${clientSecret}`
  })
  const data = await res.json()
  cachedToken = data.access_token
  tokenExpiry = Date.now() + ((data.expires_in - 60) * 1000) // 提前 60 秒更新
  return cachedToken
}
```

**第二層：無 Token 時加延遲**

```javascript
// 不帶 Token 時，兩支 API 之間等 500 毫秒
if (!token) await new Promise(r => setTimeout(r, 500))
```

**第三層：429 明確提示**

```javascript
if (res.status === 429) {
  throw new Error('請求次數超過限制（429）。請填入 TDX Client ID/Secret。')
}
```

### 7.3 申請 TDX 帳號步驟

1. 前往 [tdx.transportdata.tw](https://tdx.transportdata.tw)
2. 點選右上角「加入會員」→ 填寫資料 → 審核通過（約 1 個工作天）
3. 登入後點右上角「會員中心」→「API 金鑰」
4. 複製 **Client ID** 和 **Client Secret**

### 7.4 在網頁填入帳號

1. 點選右上角「⚙️ TDX 帳號」
2. 填入 Client ID 和 Client Secret
3. 按「💾 套用」
4. 重新整理資料

> 帳號只存在瀏覽器記憶體，關閉頁面就清除，不會外洩。

---

## 8. 上傳到 GitHub 並部署

### 8.1 第一步：修改 vite.config.js

```javascript
// vite.config.js
export default defineConfig({
  plugins: [react()],
  base: '/react-opendata/'   // ← 改成你的 GitHub Repository 名稱（一定要一樣！）
})
```

### 8.2 第二步：建立 GitHub Repository

1. 前往 [github.com](https://github.com) → 右上角「+」→「New repository」
2. Repository name 填入：`react-opendata`（要和 `vite.config.js` 的 `base` 一致）
3. 選 **Public**
4. 點「Create repository」

### 8.3 第三步：初始化 Git 並推送

在終端機執行（請替換 `你的帳號`）：

```bash
# 初始化 Git
git init

# 加入所有檔案
git add .

# 第一次提交
git commit -m "feat: React 政府開放資料地圖初始版本"

# 設定主分支為 main
git branch -M main

# 連結你的 GitHub Repository
git remote add origin https://github.com/你的帳號/react-opendata.git

# 推送到 GitHub
git push -u origin main
```

### 8.4 第四步：GitHub Actions 自動部署

推送後，GitHub 會自動執行 `.github/workflows/deploy.yml` 進行部署：

```
git push
    │
    ▼
GitHub Actions 啟動
    │
    ├─ 安裝 Node.js 24
    ├─ npm install
    ├─ npm run build（產生 dist/ 資料夾）
    └─ 推送 dist/ 到 gh-pages 分支
```

前往 GitHub Repository → **Actions** 頁面，確認最新一筆顯示綠色 ✅。

### 8.5 第五步：開啟 GitHub Pages

1. 進入 Repository → **Settings → Pages**
2. Source：`Deploy from a branch`
3. Branch：選 **`gh-pages`**，資料夾選 **`/ (root)`**
4. 點 **Save**

等待 1～2 分鐘，網址出現：

```
https://你的帳號.github.io/react-opendata/
```

### 8.6 之後更新程式碼的流程

```bash
# 修改程式碼後
git add .
git commit -m "fix: 修正 YouBike 顯示問題"
git push
```

推送後 GitHub Actions 會自動重新 build 並部署，約 2～3 分鐘生效。

### 8.7 deploy.yml 設定說明

```yaml
name: Deploy React to GitHub Pages

on:
  push:                    # ← 觸發條件：推送到 main 分支時
    branches: [main]

permissions:
  contents: write          # ← 允許 Actions 寫入 gh-pages 分支

jobs:
  deploy:
    runs-on: ubuntu-latest
    env:
      FORCE_JAVASCRIPT_ACTIONS_TO_NODE24: true   # ← 使用 Node.js 24
    steps:
      - uses: actions/checkout@v4               # 下載程式碼

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '24'

      - name: Install dependencies
        run: npm install                         # 安裝套件

      - name: Build
        run: npm run build                       # 打包

      - name: Deploy to GitHub Pages
        uses: peaceiris/actions-gh-pages@v4
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./dist                   # 把 dist/ 推到 gh-pages 分支
```

---

## 9. 響應式設計說明

本專案採用 **CSS 媒體查詢（Media Query）** 實現響應式，不需要安裝任何 CSS 框架。

### 9.1 三個斷點

```css
/* 手機（< 640px）：單欄垂直排列 */
@media (max-width: 640px) {
  .layout { flex-direction: column; }
  .panel  { width: 100%; max-height: 50vh; }
}

/* 平板（640px ～ 1024px）：側欄縮小 */
@media (max-width: 1024px) {
  .panel { width: 280px; }
}

/* 電腦（> 1024px）：正常雙欄 */
/* 預設就是這個，不需要 media query */
```

### 9.2 各裝置顯示效果

```
電腦（1024px 以上）
┌──────────────┬───────────────────────────────┐
│  左側面板     │         地圖                  │
│  (340px)     │         (剩餘寬度)            │
│  站點列表    │                              │
│  控制選項    │   🚲 🚲  🚲 🚲             │
└──────────────┴───────────────────────────────┘

手機（640px 以下）
┌─────────────────────────┐
│  標題 / 標籤              │
├─────────────────────────┤
│  左側面板（50% 高度）     │
│  站點列表                │
├─────────────────────────┤
│  地圖（50% 高度）         │
│   🚲 🚲  🚲 🚲          │
└─────────────────────────┘
```

---

## 10. 與 AI 對話：進一步擴充

### 💬 對話範例 1：加入空氣品質 AQI

> 「幫我在現有的 React 專案加入第三個頁籤『空氣品質』，從環保署開放資料 API 讀取全台各測站的 AQI 數值，在地圖上用顏色圓點顯示（綠=良好、黃=普通、紅=不良）」

**環保署 AQI API（完全免費，無需申請）：**
```
https://data.epa.gov.tw/api/v2/aqx_p_432?api_key=anonymousUser&format=json
```

---

### 💬 對話範例 2：加入搜尋歷史

> 「幫我用 localStorage 記住最近 5 次搜尋過的公車路線，在搜尋框下方顯示歷史紀錄，點擊可以直接再次搜尋」

---

### 💬 對話範例 3：加入路線比較

> 「在公車頁面加入一個比較模式，可以同時查詢兩條路線，用不同顏色的標記區分兩條路線的公車」

---

### 💬 對話範例 4：加入夜間模式

> 「加入一個日/夜間模式切換按鈕，夜間模式時整個介面改成深色，地圖也換成暗色圖層」

**可以使用的深色地圖圖層（免費）：**
```javascript
// CartoDB 深色地圖圖層（免費）
L.tileLayer('https://{s}.basemaps.cartocdn.com/dark_all/{z}/{x}/{y}{r}.png')
```

---

### 🎨 可以改成的畫面風格

| 說這句話 | 效果 |
|---------|------|
| 「改成日式極簡風格，白色背景搭配墨綠色」 | 全站配色改變 |
| 「把地圖標記改成自訂圖片 PNG 圖示」 | Leaflet 自訂 marker |
| 「加入站點詳細資料彈出視窗，點擊卡片後從右側滑入」 | Drawer 側欄效果 |
| 「加入數據統計圖表，顯示各區域 YouBike 可用率」| 整合 Recharts 圖表庫 |

---

## 11. 常見問題排查

### 11.1 npm install 失敗

```bash
# 清除快取後重試
npm cache clean --force
npm install
```

### 11.2 本機可以，但 GitHub Pages 顯示空白

確認 `vite.config.js` 的 `base` 和 Repository 名稱完全一致：

```javascript
// ❌ 錯誤（Repository 名稱是 react-opendata，base 寫錯）
base: '/myapp/'

// ✅ 正確
base: '/react-opendata/'
```

### 11.3 429 Too Many Requests

| 解法 | 說明 |
|------|------|
| 申請 TDX 帳號 | 有 Token 後配額大幅提高 |
| 稍後再試 | 等 1 分鐘後限制自動解除 |
| 減少切換頻率 | 避免快速重複點擊城市選擇 |

### 11.4 地圖不顯示（灰色或空白）

```javascript
// 確認 Leaflet CSS 有正確載入（index.html 裡）
<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
```

### 11.5 YouBike 顯示 NaN

這是 TDX 兩支 API 的 StationUID 格式不一致問題。  
本專案已用雙重比對解決，若仍有問題，在瀏覽器按 F12 查看 Console 確認 API 回傳格式。

### 11.6 Windows PowerShell 指令不認識

PowerShell 沒有 `grep`，改用：

```powershell
# 搜尋檔案內容
Select-String -Path "src\*.jsx" -Pattern "useState"

# 查看檔案內容
type src\App.jsx
```

---

## 📚 延伸學習資源

| 資源 | 連結 |
|------|------|
| React 官方文件 | https://react.dev |
| React Hooks 說明 | https://react.dev/reference/react |
| Vite 官方文件 | https://vitejs.dev |
| Leaflet.js 文件 | https://leafletjs.com/reference.html |
| TDX API 文件 | https://tdx.transportdata.tw/api-service/swagger |
| CSS Modules 說明 | https://github.com/css-modules/css-modules |
| GitHub Actions 文件 | https://docs.github.com/actions |
| OpenStreetMap | https://www.openstreetmap.org |

---

## 🚀 完成後可以繼續學習

```
本專案（React + Leaflet + TDX）
        ↓
加入 React Router（多頁面路由）
        ↓
加入 Zustand 或 Redux（全域狀態管理）
        ↓
加入 React Query（更強大的 API 管理）
        ↓
加入 TypeScript（靜態型別檢查）
        ↓
進階 React 開發者！🎉
```

---

*本講義由 Claude (Anthropic) 協助產生 ✦ 技術版本：React 18 · Vite 5 · Leaflet 1.9 · TDX API v2*
