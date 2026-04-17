---
title: 從 CDN 畢業，用 Vite 建立真正的專案
tags: [114_下學期_互動程式設計]

---

# Vue.js 進階入門講義
## 從 CDN 畢業，用 Vite 建立真正的專案

> 難度：入門之後 ★★☆☆☆  
> 前置：已完成《Vue.js 入門講義》  
> 目標：安裝 Vite 專案、認識元件、完成「記帳本」並發布到 GitHub Pages

---

## 本講義會學到什麼？

入門講義用的是 **CDN 版**（直接引入 Vue，一個 HTML 搞定）。  
這份講義升一個台階：

| 入門（已學） | 本講義（新學） |
|---|---|
| 一個 HTML 檔案 | 用 Vite 建立完整專案資料夾 |
| 直接在瀏覽器開啟 | 用 `npm run dev` 啟動本地伺服器 |
| 所有程式碼在一起 | 拆成多個 `.vue` 元件檔案 |
| 只能自己看 | 發布到 GitHub Pages，任何人都能瀏覽 |

完成後的成果：一個有**新增、刪除、統計**功能的記帳本網頁，並且可以用網址分享給朋友！

---

## 第一章：安裝前的準備

### 1.1 需要安裝什麼？

只需要安裝一個東西：**Node.js**

Node.js 是讓 JavaScript 在電腦上（不只是瀏覽器）執行的環境，Vite、npm 都靠它運作。

### 1.2 安裝 Node.js

1. 前往官網：**https://nodejs.org**
2. 點選左邊的 **LTS 版本**（長期支援版，比較穩定）
3. 下載後一路點「下一步」安裝完成

> **電腦教室沒有安裝權限？**  
> 使用線上版：前往 **https://stackblitz.com** → 點 New Project → Vue  
> StackBlitz 在瀏覽器裡內建了完整的 Node.js，不需要安裝任何東西！

### 1.3 確認安裝成功

安裝完後，打開「命令提示字元」（Windows）或「終端機」（Mac）：

- **Windows**：按 `Win + R`，輸入 `cmd`，按 Enter
- **Mac**：按 `Command + 空白鍵`，搜尋「終端機」

輸入以下兩行指令，按 Enter：

```bash
node --version
```

```bash
npm --version
```

如果看到版本號（例如 `v20.11.0` 和 `10.2.4`），代表安裝成功！

---

在L110上課需要如果出現錯誤，需要加上

有以下錯誤訊息  
npm : C:\\Program Files\\nodejs\\npm.ps1 檔案無法載入。檔案 C:\\Program Files\\nodejs\\npm.ps1 未經數位簽署。您無法在目前的系統上執行此指令碼。如需關於執行指令碼及設定執行原則的詳細資訊，請參閱 about\_Execution\_Policies (網址為 https:/go.microsoft.com/fwlink/?LinkID=135170)。位於 線路:1 字元:1+ npm -v+ ~~~ + CategoryInfo : SecurityError: (:) \[\], PSSecurityException + FullyQualifiedErrorId : UnauthorizedAccess  

  

則

這是 Windows PowerShell 的執行原則限制問題，解決方法很簡單：

解決方法
----

在 PowerShell 以系統管理員身分執行，輸入以下指令：



```tex!
Set\-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned
```

輸入 `Y` 確認後，再試一次 `npm -v` 即可。

---

說明
--

Windows 預設的 PowerShell 執行原則是 `Restricted`，會封鎖所有未經簽署的 `.ps1` 腳本（包含 npm.ps1）。

`RemoteSigned` 的意思是：

-   本機腳本可以直接執行
-   從網路下載的腳本需要數位簽署才能執行

這是安全且常見的設定，不會有風險。

---

如果不想改全域設定
---------

可以改用 命令提示字元（CMD） 執行 npm，不受 PowerShell 執行原則影響：

npm -v

或在 VS Code 終端機設定中，將預設 shell 改為 Command Prompt 而非 PowerShell。

---

## 安裝Git

### 安裝 Git 並設定（第一次）

打開命令提示字元，輸入（把名字和信箱換成你的）：

```
git config --global user.name "你的名字"
git config --global user.email "你的信箱@gmail.com"
```

> 確認 Git 有安裝：`git --version`  
> 沒有的話到 **[https://git-scm.com](https://git-scm.com)** 下載安裝



---

## 第二章：用 Vite 建立 Vue 專案

### 2.1 什麼是 Vite？

**Vite**（唸作「威特」）是幫你建立 Vue 專案的工具。  
就像蓋房子前要先打地基，Vite 幫你準備好所有必要的檔案和設定，讓你可以專心寫程式。

### 2.2 建立專案（只需要做一次）

在命令提示字元 / 終端機，輸入以下指令：

**步驟一：建立專案**

```bash
npm create vite@latest my-notebook
```

> `my-notebook` 是你的專案名稱，可以換成任何英文名稱（不能有空格）

執行後會問你幾個問題，用方向鍵選擇，按 Enter 確認：

```
✔ Select a framework › Vue          ← 選 Vue
✔ Select a variant  › JavaScript    ← 選 JavaScript（不是 TypeScript）
```

**步驟二：進入專案資料夾**

```bash
cd my-notebook
```

**步驟三：安裝所需套件**

```bash
npm install
```

> 這一步會下載所有必要的程式庫，第一次可能需要等 1～2 分鐘

**步驟四：啟動開發伺服器**

```bash
npm run dev
```

看到這個畫面代表成功：

```
  VITE v5.x.x  ready in 300 ms

  ➜  Local:   http://localhost:5173/
  ➜  Network: use --host to expose
```

**步驟五：在瀏覽器開啟**

打開瀏覽器，輸入網址：`http://localhost:5173`

你應該會看到 Vue 的預設歡迎畫面！

> 💡 **要停止伺服器**：在命令提示字元按 `Ctrl + C`

### 2.3 認識專案資料夾

打開你的 `my-notebook` 資料夾，結構長這樣：

```
my-notebook/
├── src/
│   ├── components/       ← 放元件的地方（本講義重點）
│   ├── App.vue           ← 主要的 Vue 檔案
│   └── main.js           ← 程式的入口點
├── index.html            ← 網頁的骨架
├── package.json          ← 專案設定（記錄用了哪些套件）
└── vite.config.js        ← Vite 的設定
```

> 你主要只需要動 `src/` 資料夾裡的檔案！

### 2.4 認識 .vue 檔案

Vite 版的 Vue 每個檔案都是 `.vue` 格式，結構固定分三個區塊：

```vue
<template>
  <!-- 這裡寫 HTML 畫面 -->
  <h1>{{ title }}</h1>
</template>

<script setup>
// 這裡寫 JavaScript 邏輯
import { ref } from 'vue'
const title = ref('我的記帳本')
</script>

<style scoped>
/* 這裡寫 CSS 樣式（scoped 代表只影響這個元件）*/
h1 {
  color: #333;
}
</style>
```

> 和入門版的差別：邏輯從 `data()` 改成 `ref()`，這是 Vue 3 的現代寫法

---

## 第三章：ref 與 computed 的新寫法

入門版用 `data()` 和 `computed`，Vite 版改用 `ref()` 和 `computed()`。  
功能完全一樣，只是寫法不同。

### 3.1 ref：取代 data()

```javascript
// 入門版（CDN）的寫法
data() {
  return {
    count: 0,
    name: '小明'
  }
}

// Vite 版的寫法（本講義用這個）
import { ref } from 'vue'

const count = ref(0)       // 數字
const name  = ref('小明')  // 字串
```

**使用時的差異**：在 JavaScript 裡要加 `.value`，在 `<template>` 裡不用：

```javascript
// JavaScript 裡要加 .value
count.value++
console.log(name.value)   // "小明"
```

```html
<!-- template 裡不用加 .value，Vue 自動處理 -->
<p>{{ count }}</p>
<p>{{ name }}</p>
```

### 3.2 computed：寫法幾乎一樣

```javascript
// 入門版（CDN）
computed: {
  total() {
    return this.price * this.qty
  }
}

// Vite 版
import { ref, computed } from 'vue'

const price = ref(100)
const qty   = ref(3)

const total = computed(() => price.value * qty.value)
// 使用時直接 {{ total }}，不需要加 .value（template 自動處理）
```

### 3.3 methods：改成直接定義函式

```javascript
// 入門版（CDN）
methods: {
  addItem() {
    this.count++
  }
}

// Vite 版：直接寫函式，不需要 methods 包覆
function addItem() {
  count.value++
}
```

## 實際上的APP.vue

```vue=

<template>
  <!-- 這裡寫 HTML 畫面 -->
  <h1>{{ title }}</h1>
  <p>計數: {{ count }}</p>
  <p>姓名: {{ name }}</p>
  <p>總金額: {{ total }}</p>
</template>

<script setup>
// 這裡寫 JavaScript 邏輯

import { ref, computed } from 'vue'
const title = ref('我的記帳本')
const price = ref(100)
const qty   = ref(3)

const total = computed(() => price.value * qty.value)
// 使用時直接 {{ total }}，不需要加 .value（template 自動處理）
const count = ref(0)       // 數字
const name  = ref('小明')  // 字串
</script>

<style scoped>
/* 這裡寫 CSS 樣式（scoped 代表只影響這個元件）*/
h1 {
  color: #ec0d0d;
}
</style>
```

### 快速對照表

| 功能 | 入門版（CDN）| Vite 版（本講義）|
|---|---|---|
| 資料 | `data() { return { x: 0 } }` | `const x = ref(0)` |
| 計算 | `computed: { y() { return this.x + 1 } }` | `const y = computed(() => x.value + 1)` |
| 函式 | `methods: { fn() { this.x++ } }` | `function fn() { x.value++ }` |
| 讀取（JS）| `this.x` | `x.value` |
| 讀取（HTML）| `{{ x }}` | `{{ x }}` （一樣！）|

---

## 第四章：認識元件（Component）

### 4.1 為什麼要用元件？

想像你的記帳本有很多筆記錄，每筆記錄長得一樣：

```
[ 早餐 / 早餐店 / $80 / 刪除 ]
[ 午餐 / 便當店 / $100 / 刪除 ]
[ 晚餐 / 滷肉飯 / $60 / 刪除 ]
```

如果用 `v-for` 重複顯示，每筆記錄的 HTML 都是一樣的結構。  
我們可以把「一筆記錄的 HTML + 樣式」抽出來，做成一個**可以重複使用的元件**。

### 4.2 建立第一個元件

在 `src/components/` 資料夾裡，建立一個新檔案 `RecordItem.vue`：

```vue
<template>
  <div class="record-item">
    <span class="record-category">{{ record.category }}</span>
    <span class="record-note">{{ record.note }}</span>
    <span class="record-amount">- ${{ record.amount }}</span>
    <button class="delete-btn" @click="$emit('delete', record.id)">
      刪除
    </button>
  </div>
</template>

<script setup>
// defineProps：宣告這個元件會接收哪些資料
defineProps({
  record: {
    type: Object,
    required: true
  }
})

// defineEmits：宣告這個元件會發出哪些事件
defineEmits(['delete'])
</script>

<style scoped>
.record-item {
  display: flex;
  align-items: center;
  gap: 12px;
  background: white;
  padding: 12px 16px;
  margin-bottom: 8px;
  border-radius: 8px;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.08);
}
.record-category {
  background: #e8f4fd;
  color: #1a5ea8;
  padding: 2px 10px;
  border-radius: 99px;
  font-size: 13px;
  white-space: nowrap;
}
.record-note {
  flex: 1;
  color: #444;
}
.record-amount {
  color: #c84b2f;
  font-weight: bold;
  white-space: nowrap;
}
.delete-btn {
  padding: 4px 10px;
  background: #fee;
  color: #c84b2f;
  border: 1px solid #fcc;
  border-radius: 6px;
  cursor: pointer;
  font-size: 13px;
}
.delete-btn:hover {
  background: #c84b2f;
  color: white;
}
</style>
```

**這個元件做了什麼？**

- `defineProps`：告訴 Vue「我需要從外部傳入一個 `record` 物件」
- `$emit('delete', record.id)`：當使用者點刪除，通知父元件「有人要刪除這筆 id 的記錄」
- `scoped`：這裡的 CSS 只影響這個元件，不會影響其他地方

### 4.3 在主畫面使用元件

修改 `src/App.vue`，引入並使用 `RecordItem`：

```vue
<template>
  <div class="app">
    <h1>💰 我的記帳本</h1>

    <!-- 統計區 -->
    <div class="summary">
      <div class="summary-card">
        <p class="summary-label">本月支出</p>
        <p class="summary-amount">$ {{ totalAmount }}</p>
      </div>
      <div class="summary-card">
        <p class="summary-label">記錄筆數</p>
        <p class="summary-amount">{{ records.length }} 筆</p>
      </div>
    </div>

    <!-- 新增表單 -->
    <div class="form">
      <select v-model="newCategory">
        <option value="">選擇類別</option>
        <option value="飲食">🍜 飲食</option>
        <option value="交通">🚌 交通</option>
        <option value="購物">🛍️ 購物</option>
        <option value="娛樂">🎬 娛樂</option>
        <option value="其他">📦 其他</option>
      </select>
      <input v-model="newNote"   placeholder="說明（例：午餐便當）" />
      <input v-model="newAmount" placeholder="金額" type="number" />
      <button @click="addRecord">新增</button>
    </div>

    <!-- 錯誤提示 -->
    <p v-if="errorMsg" class="error">⚠️ {{ errorMsg }}</p>

    <!-- 記錄列表：使用 RecordItem 元件 -->
    <p v-if="records.length === 0" class="empty-hint">
      還沒有記錄，新增第一筆吧！
    </p>
    <RecordItem
      v-for="record in records"
      :key="record.id"
      :record="record"
      @delete="deleteRecord"
    />
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import RecordItem from './components/RecordItem.vue'

// ── 資料 ──────────────────────────────────
const records    = ref([])      // 所有記帳記錄
const newCategory = ref('')     // 新增表單：類別
const newNote    = ref('')      // 新增表單：說明
const newAmount  = ref('')      // 新增表單：金額
const errorMsg   = ref('')      // 錯誤訊息
let   nextId     = 1            // 自動遞增的 id

// ── 計算屬性 ──────────────────────────────
const totalAmount = computed(() =>
  records.value.reduce((sum, r) => sum + r.amount, 0)
)

// ── 函式 ──────────────────────────────────
function addRecord() {
  // 清除舊錯誤
  errorMsg.value = ''

  // 驗證輸入
  if (!newCategory.value) {
    errorMsg.value = '請選擇類別'
    return
  }
  if (!newNote.value.trim()) {
    errorMsg.value = '請填寫說明'
    return
  }
  if (!newAmount.value || Number(newAmount.value) <= 0) {
    errorMsg.value = '請填寫正確的金額'
    return
  }

  // 新增一筆記錄
  records.value.push({
    id:       nextId++,
    category: newCategory.value,
    note:     newNote.value.trim(),
    amount:   Number(newAmount.value),
  })

  // 清空表單
  newCategory.value = ''
  newNote.value     = ''
  newAmount.value   = ''
}

function deleteRecord(id) {
  records.value = records.value.filter(r => r.id !== id)
}
</script>

<style>
/* 全域樣式（沒有 scoped）*/
* { box-sizing: border-box; margin: 0; padding: 0; }
body {
  font-family: sans-serif;
  background: #f0f4f8;
  min-height: 100vh;
}
</style>

<style scoped>
.app {
  max-width: 560px;
  margin: 0 auto;
  padding: 24px 20px;
}
h1 {
  font-size: 24px;
  color: #2a1f14;
  margin-bottom: 20px;
  text-align: center;
}

/* 統計卡片 */
.summary {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
  margin-bottom: 20px;
}
.summary-card {
  background: white;
  border-radius: 10px;
  padding: 16px;
  text-align: center;
  box-shadow: 0 1px 4px rgba(0,0,0,0.08);
}
.summary-label  { font-size: 13px; color: #888; margin-bottom: 6px; }
.summary-amount { font-size: 22px; font-weight: bold; color: #2a1f14; }

/* 新增表單 */
.form {
  display: flex;
  gap: 8px;
  margin-bottom: 12px;
  flex-wrap: wrap;
}
.form select,
.form input {
  padding: 9px 12px;
  border: 1px solid #ddd;
  border-radius: 8px;
  font-size: 14px;
  background: white;
}
.form select { flex: 0 0 auto; }
.form input[placeholder="說明（例：午餐便當）"] { flex: 1; min-width: 120px; }
.form input[type="number"] { width: 90px; }
.form button {
  padding: 9px 18px;
  background: #2a7ae2;
  color: white;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  font-size: 14px;
  white-space: nowrap;
}
.form button:hover { background: #1a5ea8; }

/* 訊息 */
.error      { color: #c84b2f; font-size: 13px; margin-bottom: 10px; }
.empty-hint { color: #aaa; text-align: center; padding: 32px 0; font-size: 15px; }
</style>
```

---

## 第五章：加入分類篩選功能

學習用 `computed` 搭配 `v-model` 做資料篩選，這是很常見的互動模式。

在 `App.vue` 的 `<script setup>` 新增這幾行：

```javascript
// 目前選擇的篩選類別（空字串 = 顯示全部）
const filterCategory = ref('')

// 篩選後的記錄
const filteredRecords = computed(() => {
  if (!filterCategory.value) return records.value
  return records.value.filter(r => r.category === filterCategory.value)
})
```

在 `<template>` 新增篩選列，並把 `v-for` 改用 `filteredRecords`：

```html
<!-- 篩選列（放在新增表單下方）-->
<div class="filter-bar">
  <span>篩選：</span>
  <button
    :class="{ active: filterCategory === '' }"
    @click="filterCategory = ''"
  >全部</button>
  <button
    v-for="cat in ['飲食','交通','購物','娛樂','其他']"
    :key="cat"
    :class="{ active: filterCategory === cat }"
    @click="filterCategory = cat"
  >{{ cat }}</button>
</div>

<!-- 記錄列表改用 filteredRecords -->
<RecordItem
  v-for="record in filteredRecords"
  :key="record.id"
  :record="record"
  @delete="deleteRecord"
/>
```

新增對應的 CSS：

```css
.filter-bar {
  display: flex;
  align-items: center;
  gap: 6px;
  margin-bottom: 14px;
  flex-wrap: wrap;
}
.filter-bar span {
  font-size: 13px;
  color: #888;
}
.filter-bar button {
  padding: 4px 12px;
  border: 1px solid #ddd;
  border-radius: 99px;
  background: white;
  cursor: pointer;
  font-size: 13px;
  color: #555;
}
.filter-bar button.active {
  background: #2a7ae2;
  color: white;
  border-color: #2a7ae2;
}
```

---

## 第六章：完整的 App.vue

把前面所有內容整合，這是最終的完整版 `App.vue`，可以直接複製貼上：

```vue
<template>
  <div class="app">
    <h1>💰 我的記帳本</h1>

    <!-- 統計 -->
    <div class="summary">
      <div class="summary-card">
        <p class="summary-label">本月支出</p>
        <p class="summary-amount">${{ totalAmount }}</p>
      </div>
      <div class="summary-card">
        <p class="summary-label">記錄筆數</p>
        <p class="summary-amount">{{ filteredRecords.length }} / {{ records.length }} 筆</p>
      </div>
    </div>

    <!-- 新增表單 -->
    <div class="form">
      <select v-model="newCategory">
        <option value="">選擇類別</option>
        <option value="飲食">🍜 飲食</option>
        <option value="交通">🚌 交通</option>
        <option value="購物">🛍️ 購物</option>
        <option value="娛樂">🎬 娛樂</option>
        <option value="其他">📦 其他</option>
      </select>
      <input v-model="newNote"   placeholder="說明（例：午餐便當）" />
      <input v-model="newAmount" placeholder="金額" type="number" min="1" />
      <button @click="addRecord">新增</button>
    </div>
    <p v-if="errorMsg" class="error">⚠️ {{ errorMsg }}</p>

    <!-- 篩選列 -->
    <div class="filter-bar">
      <span>篩選：</span>
      <button :class="{ active: filterCategory === '' }" @click="filterCategory = ''">全部</button>
      <button
        v-for="cat in categories" :key="cat"
        :class="{ active: filterCategory === cat }"
        @click="filterCategory = cat"
      >{{ cat }}</button>
    </div>

    <!-- 記錄列表 -->
    <p v-if="records.length === 0" class="empty-hint">還沒有記錄，新增第一筆吧！</p>
    <p v-else-if="filteredRecords.length === 0" class="empty-hint">這個類別還沒有記錄</p>
    <RecordItem
      v-for="record in filteredRecords"
      :key="record.id"
      :record="record"
      @delete="deleteRecord"
    />
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import RecordItem from './components/RecordItem.vue'

// ── 資料 ──────────────────────────────────────────────
const records        = ref([])
const newCategory    = ref('')
const newNote        = ref('')
const newAmount      = ref('')
const errorMsg       = ref('')
const filterCategory = ref('')
let   nextId         = 1

// ── 計算屬性 ──────────────────────────────────────────
const totalAmount = computed(() =>
  records.value.reduce((sum, r) => sum + r.amount, 0)
)

const categories = ['飲食', '交通', '購物', '娛樂', '其他']

const filteredRecords = computed(() => {
  if (!filterCategory.value) return records.value
  return records.value.filter(r => r.category === filterCategory.value)
})

// ── 函式 ──────────────────────────────────────────────
function addRecord() {
  errorMsg.value = ''
  if (!newCategory.value)               { errorMsg.value = '請選擇類別'; return }
  if (!newNote.value.trim())            { errorMsg.value = '請填寫說明'; return }
  if (!newAmount.value || Number(newAmount.value) <= 0) { errorMsg.value = '請填寫正確金額'; return }

  records.value.push({
    id:       nextId++,
    category: newCategory.value,
    note:     newNote.value.trim(),
    amount:   Number(newAmount.value),
  })

  newCategory.value = ''
  newNote.value     = ''
  newAmount.value   = ''
}

function deleteRecord(id) {
  records.value = records.value.filter(r => r.id !== id)
}
</script>

<style>
* { box-sizing: border-box; margin: 0; padding: 0; }
body { font-family: sans-serif; background: #f0f4f8; min-height: 100vh; }
</style>

<style scoped>
.app { max-width: 560px; margin: 0 auto; padding: 24px 20px; }
h1   { font-size: 24px; color: #2a1f14; margin-bottom: 20px; text-align: center; }

.summary { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; margin-bottom: 20px; }
.summary-card   { background: white; border-radius: 10px; padding: 16px; text-align: center; box-shadow: 0 1px 4px rgba(0,0,0,0.08); }
.summary-label  { font-size: 13px; color: #888; margin-bottom: 6px; }
.summary-amount { font-size: 22px; font-weight: bold; color: #2a1f14; }

.form { display: flex; gap: 8px; margin-bottom: 8px; flex-wrap: wrap; }
.form select,
.form input   { padding: 9px 12px; border: 1px solid #ddd; border-radius: 8px; font-size: 14px; background: white; }
.form input[type="number"] { width: 90px; }
.form button  { padding: 9px 18px; background: #2a7ae2; color: white; border: none; border-radius: 8px; cursor: pointer; font-size: 14px; }
.form button:hover { background: #1a5ea8; }

.error      { color: #c84b2f; font-size: 13px; margin-bottom: 10px; }
.empty-hint { color: #aaa; text-align: center; padding: 32px 0; font-size: 15px; }

.filter-bar { display: flex; align-items: center; gap: 6px; margin-bottom: 14px; flex-wrap: wrap; }
.filter-bar span   { font-size: 13px; color: #888; }
.filter-bar button { padding: 4px 12px; border: 1px solid #ddd; border-radius: 99px; background: white; cursor: pointer; font-size: 13px; color: #555; }
.filter-bar button.active { background: #2a7ae2; color: white; border-color: #2a7ae2; }
</style>
```

---

## 第七章：上傳到 GitHub 並發布網站

完成記帳本之後，要讓別人也能用瀏覽器打開看到它！

### 7.1 需要的帳號

前往 **https://github.com** 註冊一個免費帳號（沒有的話）。  
建議使用 Gmail 信箱，比較不會有驗證問題。

### 7.2 在 GitHub 建立倉庫

1. 登入 GitHub，點右上角的 **+** → **New repository**
2. **Repository name** 填：`my-notebook`
3. 選 **Public**（GitHub Pages 免費版需要 Public）
4. **不要**勾選任何 Initialize 選項
5. 點 **Create repository**

### 7.3 設定 Vite 的 base 路徑

因為 GitHub Pages 的網址是 `帳號.github.io/倉庫名稱`，Vite 需要知道這個路徑。

打開 `vite.config.js`，修改成：

```javascript
import { defineConfig } from 'vite'
import vue from '@vitejs/plugin-vue'

export default defineConfig({
  plugins: [vue()],
  base: '/my-notebook/',   // ← 加上這行，填你的倉庫名稱
})
```

### 測試過後建議改為
```javascript
base: './',
```

> ⚠️ `my-notebook` 要和你在 GitHub 建立的倉庫名稱一樣！

### 7.4 建立自動部署設定

在專案根目錄建立資料夾和檔案：

路徑：`.github/workflows/deploy.yml`

（先建立 `.github` 資料夾，再建立 `workflows` 資料夾，再建立 `deploy.yml` 檔案）

貼入以下內容：

```yaml
name: 部署到 GitHub Pages

on:
  push:
    branches: [main]

permissions:
  contents: read
  pages: write
  id-token: write

jobs:
  deploy:
    runs-on: ubuntu-latest
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    steps:
      - uses: actions/checkout@v4

      - uses: actions/setup-node@v4
        with:
          node-version: 20

      - name: 安裝套件
        run: npm install

      - name: 打包專案
        run: npm run build

      - uses: actions/configure-pages@v4

      - uses: actions/upload-pages-artifact@v3
        with:
          path: dist

      - uses: actions/deploy-pages@v4
        id: deployment
```

> **這個檔案的意思**：每次你把程式碼推到 GitHub，GitHub 會自動幫你執行「安裝套件 → 打包 → 發布」，完全不需要你手動操作！

### 7.5 安裝 Git 並設定（第一次）

打開命令提示字元，輸入（把名字和信箱換成你的）：

```bash
git config --global user.name "你的名字"
git config --global user.email "你的信箱@gmail.com"
```

> 確認 Git 有安裝：`git --version`  
> 沒有的話到 **https://git-scm.com** 下載安裝

### 7.6 推送程式碼到 GitHub

在命令提示字元，確認你在 `my-notebook` 資料夾裡，然後依序輸入：

```bash
git init
```

```bash
git add .
```

```bash
git commit -m "完成記帳本專案"
```

```bash
git branch -M main
```

```bash
git remote add origin https://github.com/你的帳號/my-notebook.git
```

> ⚠️ `你的帳號` 換成你的 GitHub 帳號名稱

```bash
git push -u origin main
```

**第一次推送會要求登入 GitHub：**
- 使用者名稱：你的 GitHub 帳號
- 密碼：**不是** GitHub 密碼，要用 Personal Access Token

**取得 Personal Access Token：**
1. GitHub 右上角頭像 → **Settings**
2. 最下方 **Developer settings** → **Personal access tokens** → **Tokens (classic)**
3. **Generate new token (classic)**
4. Note 隨便填，Expiration 選 90 days，勾選 **repo**
5. 點 **Generate token**，複製那串文字
6. 回到命令提示字元，密碼欄位貼上這串文字（貼上時不會顯示，正常的）

### 7.7 開啟 GitHub Pages

推送成功後：

1. 到你的 GitHub 倉庫頁面
2. 點上方 **Settings**
3. 左側選 **Pages**
4. **Source** 選 **GitHub Actions**
5. 點 **Save**

### 7.8 等待部署完成

1. 點倉庫上方的 **Actions** 頁籤
2. 可以看到部署流程在跑（橘色圓圈 = 進行中，綠色勾勾 = 成功）
3. 大約 1～2 分鐘後，回到 **Settings → Pages**
4. 上方會顯示你的網址：

```
Your site is live at https://你的帳號.github.io/my-notebook/
```

5. 點進去，你的記帳本就在網路上了！🎉

### 7.9 之後更新程式碼

每次修改程式碼後，只需要三行指令就能自動更新網站：

```bash
git add .
git commit -m "更新說明（例：新增篩選功能）"
git push
```

等 1～2 分鐘，GitHub Actions 自動重新部署，網站就更新了！

---

## 第八章：本講義學到了什麼

| 概念 | 說明 |
|---|---|
| Vite 專案 | 用 `npm create vite@latest` 建立，`npm run dev` 啟動 |
| `.vue` 檔案 | `<template>` + `<script setup>` + `<style scoped>` 三區塊 |
| `ref()` | 取代 `data()`，讀取要加 `.value` |
| `computed()` | 和入門版一樣，只是寫法更簡潔 |
| 元件 | 獨立的 `.vue` 檔案，用 `defineProps` 接收資料，`defineEmits` 發出事件 |
| GitHub Pages | 配合 `deploy.yml`，推送後自動部署網站 |

---

## 常見問題

**Q：`npm run dev` 跑完後關掉命令提示字元，網站還在嗎？**  
A：開發伺服器只在你電腦上跑。關掉後 `localhost:5173` 就看不到了，但 GitHub Pages 的網址不受影響。

**Q：我修改了檔案，`localhost:5173` 畫面沒有更新？**  
A：Vite 會自動偵測變更並更新畫面，不需要重新整理。如果真的沒更新，試試手動按 `F5`。

**Q：`git push` 出現錯誤怎麼辦？**  
A：最常見的原因是 Token 過期。重新產生一個 Personal Access Token，再 push 一次。

**Q：GitHub Actions 顯示紅色 ✗ 怎麼辦？**  
A：點進去看錯誤訊息。最常見是 `vite.config.js` 的 `base` 路徑和倉庫名稱不一樣。

---

## 下一步

完成這份講義後，你已經能夠：
- 建立真正的 Vue 專案（不只是一個 HTML 檔案）
- 把 UI 拆成可重用的元件
- 把作品發布到網路上

下一步建議學習：
- **Vue Router**：讓專案有多個頁面（點餐頁、廚房頁、管理頁）
- **Pinia**：讓多個元件共享同一份資料
- **Axios**：呼叫後端 API 取得真實資料

這些在《Vue.js 進階講義》中都有完整說明！

---

*Vue.js 官方文件（中文）：https://cn.vuejs.org*  
*Vite 官方文件：https://cn.vitejs.dev*  
*GitHub Pages 說明：https://pages.github.com*

![image](https://hackmd.io/_uploads/rkq6hRphZe.png)

![image](https://hackmd.io/_uploads/HkR53CphWg.png)

![image](https://hackmd.io/_uploads/SyNO2CahZx.png)

![image](https://hackmd.io/_uploads/HyWVhRT2-e.png)
