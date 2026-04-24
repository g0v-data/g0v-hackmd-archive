---
title: Vue.js 串接 Google Sheets 講義
tags: [114_下學期_互動程式設計]

---

# Vue.js 串接 Google Sheets 講義
## 用 Google 試算表當免費資料庫，做一個真實可用的學生成績管理系統

> 難度：★★★☆☆  
> 前置：已完成《Vue.js 進階入門講義》  
> 完成後：Vue 前端 ↔ Google Apps Script API ↔ Google Sheets 資料庫，全部免費，部署到 GitHub Pages

---
https://cfchengit.github.io/20260423/

## 為什麼用 Google Sheets 當資料庫？

| 比較項目 | 一般資料庫 | Google Sheets |
|---|---|---|
| 費用 | 需要租用伺服器（每月數百～數千元）| **完全免費** |
| 安裝設定 | 複雜，需要後端知識 | **不需要**，瀏覽器操作 |
| 查看資料 | 需要用工具連線 | **直接開啟試算表**就能看 |
| 編輯資料 | 需要寫 SQL 或用管理界面 | **直接在格子裡改** |
| 適合情境 | 大型商業系統 | 課堂練習、小型專案、個人工具 |

---

## 整體架構

```
你的 Vue 網頁（GitHub Pages）
        │
        │ 發送 HTTP 請求（GET / POST）
        ▼
Google Apps Script（當作 API 伺服器）
        │
        │ 讀取 / 寫入試算表資料
        ▼
Google Sheets（當作資料庫）
```

**三個角色：**
- **Vue** — 使用者看到的畫面，負責顯示資料和接收輸入
- **Google Apps Script** — 中間人，把 Vue 的請求轉換成試算表操作
- **Google Sheets** — 真正存資料的地方

---

## 目錄

1. [第一步：建立 Google Sheets 試算表](#第一步建立-google-sheets-試算表)
2. [第二步：建立 Google Apps Script API](#第二步建立-google-apps-script-api)
3. [第三步：測試 API 是否正常運作](#第三步測試-api-是否正常運作)
4. [第四步：建立 Vue 專案](#第四步建立-vue-專案)
5. [第五步：實作讀取功能](#第五步實作讀取功能get-請求)
6. [第六步：實作新增功能](#第六步實作新增功能post-請求)
7. [第七步：實作刪除與更新功能](#第七步實作刪除與更新功能)
8. [第八步：完整程式碼整合](#第八步完整程式碼整合)
9. [第九步：上傳到 GitHub Pages](#第九步上傳到-github-pages)
10. [常見問題排查](#常見問題排查)

---

## 第一步：建立 Google Sheets 試算表

### 1-1 建立試算表

1. 前往 **https://sheets.google.com**（需要登入 Google 帳號）
2. 點左上角的 **+** 建立新的試算表
3. 點左上角的標題「無標題的試算表」，改名為：**學生成績管理**

### 1-2 建立工作表結構

我們要做一個「學生成績管理」系統，需要兩個工作表：

**工作表一：students（學生名單）**

點底部的工作表標籤，把「工作表1」重新命名為 **students**（在標籤上按兩下）

在第一列（標題列）填入以下內容，每個欄位佔一個格子：

| A | B | C | D |
|---|---|---|---|
| id | name | class | email |

從第二列開始填入範例資料：

| A | B | C | D |
|---|---|---|---|
| id | name | class | email |
| 1 | 王小明 | 三年一班 | ming@example.com |
| 2 | 李小華 | 三年一班 | hua@example.com |
| 3 | 張小美 | 三年二班 | mei@example.com |
| 4 | 陳大偉 | 三年二班 | wei@example.com |

**工作表二：scores（成績記錄）**

點底部 **+** 新增工作表，命名為 **scores**

填入以下標題列和範例資料：

| A | B | C | D | E |
|---|---|---|---|---|
| id | student_id | subject | score | date |
| 1 | 1 | 數學 | 85 | 2024-01-15 |
| 2 | 1 | 英文 | 92 | 2024-01-15 |
| 3 | 2 | 數學 | 78 | 2024-01-15 |
| 4 | 3 | 數學 | 95 | 2024-01-15 |

### 1-3 記錄試算表 ID

試算表建立好後，看瀏覽器的網址列：

```
https://docs.google.com/spreadsheets/d/【這裡就是試算表ID】/edit
```

把這串 ID 複製起來，等一下會用到。

> 💡 **試算表 ID 是什麼？**  
> 就是一串像 `1BxiMVs0XRA5nFMdKvBdBZjgmUUqptlbs74OgVE2upms` 的隨機字串，  
> Google 用它來識別你的試算表，每個試算表都不一樣。

---

## 第二步：建立 Google Apps Script API

Google Apps Script（簡稱 GAS）可以讓你用 JavaScript 操控 Google 試算表，並把程式部署成一個公開的 API 網址。

### 2-1 開啟 Apps Script

在 Google Sheets 頁面，點上方選單：**擴充功能** → **Apps Script**

瀏覽器會開啟 Apps Script 的編輯器。

### 2-2 貼入 API 程式碼

把編輯器裡原本的內容**全部清空**，貼入以下程式碼：

```javascript
// ====================================================
// 學生成績管理系統 - Google Apps Script API
// ====================================================

// ⚠️ 把下面的 ID 換成你的試算表 ID
const SPREADSHEET_ID = '你的試算表ID放這裡'

// ── 工具函式 ─────────────────────────────────────────

// 取得指定名稱的工作表
function getSheet(name) {
  return SpreadsheetApp.openById(SPREADSHEET_ID).getSheetByName(name)
}

// 統一的成功回應格式
function success(data) {
  return ContentService
    .createTextOutput(JSON.stringify({ success: true, data: data }))
    .setMimeType(ContentService.MimeType.JSON)
}

// 統一的失敗回應格式
function fail(message) {
  return ContentService
    .createTextOutput(JSON.stringify({ success: false, error: message }))
    .setMimeType(ContentService.MimeType.JSON)
}

// 把工作表的資料轉成物件陣列
// 第一列當作欄位名稱（key），其餘列是資料
function sheetToObjects(sheet) {
  const rows = sheet.getDataRange().getValues()
  if (rows.length <= 1) return []   // 只有標題列，沒有資料

  const headers = rows[0]           // 第一列是欄位名稱
  const dataRows = rows.slice(1)    // 其餘是資料

  return dataRows.map(function(row) {
    var obj = {}
    headers.forEach(function(header, index) {
      obj[header] = row[index]
    })
    return obj
  })
}

// 產生新的 ID（取目前最大 ID + 1）
function generateId(sheet) {
  var rows = sheet.getDataRange().getValues()
  if (rows.length <= 1) return 1    // 還沒有資料，從 1 開始

  var ids = rows.slice(1).map(function(row) {
    return Number(row[0]) || 0
  })
  return Math.max.apply(null, ids) + 1
}

// ── GET 請求處理（讀取資料）─────────────────────────

function doGet(e) {
  var action = e.parameter.action

  try {
    if (action === 'getStudents')  return handleGetStudents()
    if (action === 'getScores')    return handleGetScores(e.parameter)
    return fail('不認識的 action：' + action)
  } catch(err) {
    return fail('伺服器錯誤：' + err.message)
  }
}

// 取得所有學生
function handleGetStudents() {
  var sheet = getSheet('students')
  var students = sheetToObjects(sheet)
  return success(students)
}

// 取得成績（可以用 student_id 篩選）
function handleGetScores(params) {
  var sheet = getSheet('scores')
  var scores = sheetToObjects(sheet)

  // 如果有傳 student_id，只回傳這位學生的成績
  if (params.student_id) {
    scores = scores.filter(function(s) {
      return String(s.student_id) === String(params.student_id)
    })
  }

  return success(scores)
}

// ── POST 請求處理（新增 / 修改 / 刪除）─────────────

function doPost(e) {
  try {
    var body = JSON.parse(e.postData.contents)
    var action = body.action

    if (action === 'addStudent')    return handleAddStudent(body)
    if (action === 'addScore')      return handleAddScore(body)
    if (action === 'deleteStudent') return handleDeleteStudent(body)
    if (action === 'updateScore')   return handleUpdateScore(body)

    return fail('不認識的 action：' + action)
  } catch(err) {
    return fail('伺服器錯誤：' + err.message)
  }
}

// 新增學生
function handleAddStudent(body) {
  var sheet = getSheet('students')
  var newId = generateId(sheet)

  sheet.appendRow([
    newId,
    body.name,
    body.class,
    body.email || ''
  ])

  return success({ id: newId, message: '學生新增成功' })
}

// 新增成績
function handleAddScore(body) {
  var sheet = getSheet('scores')
  var newId = generateId(sheet)
  var today = new Date().toISOString().split('T')[0]  // YYYY-MM-DD

  sheet.appendRow([
    newId,
    body.student_id,
    body.subject,
    Number(body.score),
    body.date || today
  ])

  return success({ id: newId, message: '成績新增成功' })
}

// 刪除學生（根據 id 找到那列並刪除）
function handleDeleteStudent(body) {
  var sheet = getSheet('students')
  var rows = sheet.getDataRange().getValues()

  for (var i = 1; i < rows.length; i++) {
    if (String(rows[i][0]) === String(body.id)) {
      sheet.deleteRow(i + 1)  // 工作表的列從 1 開始，所以要 +1
      return success({ message: '學生刪除成功' })
    }
  }

  return fail('找不到 id = ' + body.id + ' 的學生')
}

// 更新成績
function handleUpdateScore(body) {
  var sheet = getSheet('scores')
  var rows = sheet.getDataRange().getValues()

  for (var i = 1; i < rows.length; i++) {
    if (String(rows[i][0]) === String(body.id)) {
      // 第 4 欄（index 3）是 score
      sheet.getRange(i + 1, 4).setValue(Number(body.score))
      return success({ message: '成績更新成功' })
    }
  }

  return fail('找不到 id = ' + body.id + ' 的成績記錄')
}
```

### 2-3 修改試算表 ID

找到第 5 行：

```javascript
const SPREADSHEET_ID = '你的試算表ID放這裡'
```

把 `你的試算表ID放這裡` 換成你在第一步複製的試算表 ID。

例如：

```javascript
const SPREADSHEET_ID = '1BxiMVs0XRA5nFMdKvBdBZjgmUUqptlbs74OgVE2upms'
```

### 2-4 儲存並部署

**儲存程式碼：**

點上方的 **💾 儲存** 按鈕（或按 `Ctrl + S`）

**部署為網頁應用程式：**

1. 點右上角的 **部署** 按鈕 → **新增部署**
2. 點「類型」旁邊的 ⚙️ 齒輪圖示 → 選 **網頁應用程式**
3. 填入設定：
   - **說明**：學生成績 API（隨意填）
   - **執行身分**：**我**（使用你的 Google 帳號權限）
   - **誰可以存取**：**所有人**（包含匿名使用者）
4. 點 **部署**
5. 第一次部署會要求授權，點 **授予存取權**，選你的 Google 帳號，點 **允許**
6. 部署成功後，複製 **網頁應用程式 URL**

網址格式長這樣：
```
https://script.google.com/macros/s/AKfycbz.../exec
```

> ⚠️ **重要**：這個 URL 就是你的 API 網址，把它記下來，等一下 Vue 程式碼會用到。

---

## 第三步：測試 API 是否正常運作

在建立 Vue 之前，先用瀏覽器測試 API 是否正常。

### 3-1 測試 GET 請求（讀取學生）

把以下網址貼到瀏覽器（把 `你的網址` 換成你的 Apps Script URL）：

```
https://script.google.com/macros/s/你的網址/exec?action=getStudents
```

如果成功，你應該看到類似這樣的 JSON 資料：

```json
{
  "success": true,
  "data": [
    { "id": 1, "name": "王小明", "class": "三年一班", "email": "ming@example.com" },
    { "id": 2, "name": "李小華", "class": "三年一班", "email": "hua@example.com" }
  ]
}
```

### 3-2 測試 GET 請求（讀取特定學生的成績）

```
https://script.google.com/macros/s/你的網址/exec?action=getScores&student_id=1
```

應該看到 id=1 的學生的所有成績。

### 3-3 如果看到錯誤

| 錯誤訊息 | 原因 | 解決方式 |
|---|---|---|
| `{ "success": false, "error": "..." }` | 試算表 ID 錯誤 | 確認 SPREADSHEET_ID 是否正確 |
| `You do not have permission` | 沒有授權 | 重新部署，重新授權 |
| 網頁顯示 Google 登入畫面 | 存取權限設錯 | 部署時確認選「所有人」|
| 空的 data 陣列 | 工作表名稱錯誤 | 確認工作表名稱是 `students` 和 `scores` |

---

## 第四步：建立 Vue 專案

### 4-1 建立專案

```bash
npm create vite@latest my-grade-system
cd my-grade-system
npm install
```

### 4-2 安裝 Axios

```bash
npm install axios
```

### 4-3 建立 API 設定檔

建立 `src/api/sheets.js`，統一管理所有 API 呼叫：

```javascript
// src/api/sheets.js
import axios from 'axios'

// ⚠️ 把這裡換成你的 Apps Script 部署 URL
const API_URL = 'https://script.google.com/macros/s/你的網址/exec'

// 建立 axios 實例
const api = axios.create({
  // Google Apps Script 的 CORS 限制，需要這個設定
  headers: { 'Content-Type': 'text/plain' }
})

// ── 學生相關 API ──────────────────────────────────

// 取得所有學生
export async function getStudents() {
  const res = await api.get(`${API_URL}?action=getStudents`)
  if (!res.data.success) throw new Error(res.data.error)
  return res.data.data
}

// 新增學生
export async function addStudent(studentData) {
  const res = await api.post(API_URL, {
    action: 'addStudent',
    ...studentData
  })
  if (!res.data.success) throw new Error(res.data.error)
  return res.data.data
}

// 刪除學生
export async function deleteStudent(id) {
  const res = await api.post(API_URL, {
    action: 'deleteStudent',
    id: id
  })
  if (!res.data.success) throw new Error(res.data.error)
  return res.data.data
}

// ── 成績相關 API ──────────────────────────────────

// 取得成績（可傳入 student_id 篩選）
export async function getScores(studentId = null) {
  const url = studentId
    ? `${API_URL}?action=getScores&student_id=${studentId}`
    : `${API_URL}?action=getScores`
  const res = await api.get(url)
  if (!res.data.success) throw new Error(res.data.error)
  return res.data.data
}

// 新增成績
export async function addScore(scoreData) {
  const res = await api.post(API_URL, {
    action: 'addScore',
    ...scoreData
  })
  if (!res.data.success) throw new Error(res.data.error)
  return res.data.data
}

// 更新成績
export async function updateScore(id, newScore) {
  const res = await api.post(API_URL, {
    action: 'updateScore',
    id: id,
    score: newScore
  })
  if (!res.data.success) throw new Error(res.data.error)
  return res.data.data
}
```

> 💡 **為什麼 Content-Type 要用 `text/plain`？**  
> Google Apps Script 的 CORS（跨來源資源共享）設定限制，直接用 `application/json` 會被瀏覽器擋掉。  
> 改成 `text/plain` 就不會觸發瀏覽器的「預檢請求」，可以正常傳送。  
> Apps Script 端用 `JSON.parse(e.postData.contents)` 照樣能解析。

---

## 第五步：實作讀取功能（GET 請求）

### 5-1 建立學生列表元件

建立 `src/components/StudentList.vue`：

```vue
<template>
  <div class="student-list">
    <div class="list-header">
      <h2>學生名單</h2>
      <span class="count">共 {{ students.length }} 人</span>
    </div>

    <!-- 載入中 -->
    <div v-if="loading" class="status-msg">⏳ 載入中...</div>

    <!-- 錯誤 -->
    <div v-else-if="error" class="error-msg">❌ {{ error }}</div>

    <!-- 學生列表 -->
    <div v-else>
      <p v-if="students.length === 0" class="empty-msg">還沒有學生資料</p>

      <div
        v-for="student in students"
        :key="student.id"
        class="student-row"
        :class="{ selected: selectedId === student.id }"
        @click="$emit('select', student)"
      >
        <div class="student-info">
          <span class="student-name">{{ student.name }}</span>
          <span class="student-class">{{ student.class }}</span>
        </div>
        <div class="student-actions">
          <span class="student-email">{{ student.email }}</span>
          <button class="btn-delete" @click.stop="$emit('delete', student.id)">
            刪除
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
defineProps({
  students:   { type: Array,   default: () => [] },
  loading:    { type: Boolean, default: false },
  error:      { type: String,  default: null },
  selectedId: { type: Number,  default: null },
})

defineEmits(['select', 'delete'])
</script>

<style scoped>
.student-list { background: white; border-radius: 12px; padding: 20px; }

.list-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 16px;
}
h2    { font-size: 18px; color: #333; }
.count { font-size: 13px; color: #888; background: #f0f0f0; padding: 3px 10px; border-radius: 99px; }

.status-msg { color: #888; text-align: center; padding: 20px 0; }
.error-msg  { color: #c84b2f; background: #fff3f0; border-radius: 8px; padding: 12px; font-size: 14px; }
.empty-msg  { color: #aaa; text-align: center; padding: 20px 0; font-size: 14px; }

.student-row {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 12px;
  border-radius: 8px;
  cursor: pointer;
  transition: background 0.15s;
  margin-bottom: 4px;
}
.student-row:hover   { background: #f5f5f5; }
.student-row.selected { background: #e8f0fb; }

.student-info  { display: flex; align-items: center; gap: 10px; }
.student-name  { font-weight: 600; color: #333; }
.student-class { font-size: 13px; color: #888; background: #f0f0f0; padding: 2px 8px; border-radius: 4px; }

.student-actions { display: flex; align-items: center; gap: 10px; }
.student-email   { font-size: 13px; color: #aaa; }

.btn-delete {
  padding: 4px 12px;
  background: #fff0f0;
  color: #c84b2f;
  border: 1px solid #ffcdd2;
  border-radius: 6px;
  cursor: pointer;
  font-size: 12px;
}
.btn-delete:hover { background: #c84b2f; color: white; }
</style>
```

### 5-2 建立成績列表元件

建立 `src/components/ScoreList.vue`：

```vue
<template>
  <div class="score-list">
    <div class="list-header">
      <h2>
        {{ studentName ? studentName + ' 的成績' : '選擇學生查看成績' }}
      </h2>
      <span v-if="scores.length > 0" class="avg-badge">
        平均 {{ avgScore }} 分
      </span>
    </div>

    <div v-if="!studentName" class="hint-msg">
      👈 點左側學生查看其成績
    </div>

    <div v-else-if="loading" class="status-msg">⏳ 載入成績...</div>

    <div v-else-if="scores.length === 0" class="empty-msg">
      這位學生還沒有成績記錄
    </div>

    <div v-else class="score-table">
      <div class="table-head">
        <span>科目</span>
        <span>成績</span>
        <span>日期</span>
        <span>操作</span>
      </div>
      <div
        v-for="score in scores"
        :key="score.id"
        class="table-row"
      >
        <span class="subject">{{ score.subject }}</span>
        <!-- 編輯模式 / 顯示模式 切換 -->
        <span v-if="editingId !== score.id" class="score-value" :class="scoreClass(score.score)">
          {{ score.score }} 分
        </span>
        <input
          v-else
          v-model.number="editValue"
          type="number"
          class="score-input"
          min="0" max="100"
        />
        <span class="date">{{ score.date }}</span>
        <div class="row-actions">
          <!-- 非編輯狀態：顯示「編輯」按鈕 -->
          <template v-if="editingId !== score.id">
            <button class="btn-edit" @click="startEdit(score)">編輯</button>
          </template>
          <!-- 編輯狀態：顯示「儲存」和「取消」 -->
          <template v-else>
            <button class="btn-save" @click="$emit('update', score.id, editValue)">儲存</button>
            <button class="btn-cancel" @click="editingId = null">取消</button>
          </template>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const props = defineProps({
  scores:      { type: Array,  default: () => [] },
  studentName: { type: String, default: null },
  loading:     { type: Boolean, default: false },
})

defineEmits(['update'])

// 行內編輯狀態
const editingId = ref(null)
const editValue = ref(0)

function startEdit(score) {
  editingId.value = score.id
  editValue.value = score.score
}

// 計算平均分數
const avgScore = computed(() => {
  if (!props.scores.length) return 0
  const sum = props.scores.reduce((s, sc) => s + Number(sc.score), 0)
  return Math.round(sum / props.scores.length)
})

// 根據分數給不同的顏色 class
function scoreClass(score) {
  if (score >= 90) return 'score-excellent'
  if (score >= 70) return 'score-good'
  if (score >= 60) return 'score-pass'
  return 'score-fail'
}
</script>

<style scoped>
.score-list { background: white; border-radius: 12px; padding: 20px; }

.list-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 16px;
}
h2 { font-size: 18px; color: #333; }
.avg-badge {
  font-size: 13px;
  background: #e8f4f0;
  color: #2e6b4f;
  padding: 3px 12px;
  border-radius: 99px;
  font-weight: 600;
}

.hint-msg   { color: #bbb; text-align: center; padding: 30px 0; font-size: 15px; }
.status-msg { color: #888; text-align: center; padding: 20px 0; }
.empty-msg  { color: #aaa; text-align: center; padding: 20px 0; font-size: 14px; }

/* 成績表格 */
.table-head, .table-row {
  display: grid;
  grid-template-columns: 1fr 1fr 1.2fr 1fr;
  align-items: center;
  gap: 8px;
  padding: 10px 12px;
}
.table-head {
  font-size: 12px;
  color: #999;
  border-bottom: 1px solid #f0f0f0;
  font-weight: 600;
}
.table-row {
  border-bottom: 1px solid #f8f8f8;
}
.table-row:last-child { border-bottom: none; }

.subject { font-weight: 500; color: #333; }
.date    { font-size: 13px; color: #999; }

/* 成績顏色 */
.score-value      { font-weight: 700; font-size: 15px; }
.score-excellent  { color: #2e6b4f; }
.score-good       { color: #1a5ea8; }
.score-pass       { color: #c9962a; }
.score-fail       { color: #c84b2f; }

/* 行內編輯輸入框 */
.score-input {
  width: 70px;
  padding: 4px 8px;
  border: 2px solid #2a7ae2;
  border-radius: 6px;
  font-size: 14px;
  font-weight: 600;
}

.row-actions { display: flex; gap: 6px; }

.btn-edit   { padding: 3px 10px; background: #f0f0f0; color: #555; border: none; border-radius: 5px; cursor: pointer; font-size: 12px; }
.btn-edit:hover { background: #e0e0e0; }
.btn-save   { padding: 3px 10px; background: #2e6b4f; color: white; border: none; border-radius: 5px; cursor: pointer; font-size: 12px; }
.btn-cancel { padding: 3px 10px; background: #f0f0f0; color: #555; border: none; border-radius: 5px; cursor: pointer; font-size: 12px; }
</style>
```

---

## 第六步：實作新增功能（POST 請求）

### 6-1 建立新增學生表單元件

建立 `src/components/AddStudentForm.vue`：

```vue
<template>
  <div class="form-card">
    <h3>新增學生</h3>

    <div class="form-body">
      <div class="field">
        <label>姓名 <span class="required">*</span></label>
        <input v-model="form.name" placeholder="例：王小明" />
      </div>
      <div class="field">
        <label>班級 <span class="required">*</span></label>
        <input v-model="form.class" placeholder="例：三年一班" />
      </div>
      <div class="field">
        <label>Email</label>
        <input v-model="form.email" placeholder="例：ming@example.com" type="email" />
      </div>
    </div>

    <p v-if="errorMsg" class="error-msg">⚠️ {{ errorMsg }}</p>

    <div class="form-actions">
      <button
        class="btn-submit"
        @click="submit"
        :disabled="submitting"
      >
        {{ submitting ? '新增中...' : '＋ 新增學生' }}
      </button>
    </div>
  </div>
</template>

<script setup>
import { ref, reactive } from 'vue'

const emit = defineEmits(['added'])

const form = reactive({
  name:  '',
  class: '',
  email: ''
})
const errorMsg  = ref('')
const submitting = ref(false)

async function submit() {
  // 驗證必填欄位
  errorMsg.value = ''
  if (!form.name.trim())  { errorMsg.value = '請填寫姓名'; return }
  if (!form.class.trim()) { errorMsg.value = '請填寫班級'; return }

  submitting.value = true
  // 通知父元件執行新增，把表單資料傳出去
  emit('added', { ...form })
}

// 讓父元件可以呼叫這個函式來重置表單
function reset() {
  form.name  = ''
  form.class = ''
  form.email = ''
  errorMsg.value   = ''
  submitting.value = false
}

// 把函式暴露給父元件使用
defineExpose({ reset })
</script>

<style scoped>
.form-card {
  background: white;
  border-radius: 12px;
  padding: 20px;
}
h3 { font-size: 16px; color: #333; margin-bottom: 16px; }

.form-body { display: flex; flex-direction: column; gap: 12px; margin-bottom: 12px; }

.field label {
  display: block;
  font-size: 13px;
  color: #666;
  margin-bottom: 5px;
  font-weight: 500;
}
.required { color: #c84b2f; }
.field input {
  width: 100%;
  padding: 9px 12px;
  border: 1px solid #ddd;
  border-radius: 8px;
  font-size: 14px;
}
.field input:focus {
  outline: none;
  border-color: #2a7ae2;
}

.error-msg { color: #c84b2f; font-size: 13px; margin-bottom: 10px; }

.btn-submit {
  width: 100%;
  padding: 11px;
  background: #2a7ae2;
  color: white;
  border: none;
  border-radius: 8px;
  font-size: 14px;
  font-weight: 600;
  cursor: pointer;
}
.btn-submit:hover:not(:disabled) { background: #1a5ea8; }
.btn-submit:disabled { background: #aaa; cursor: not-allowed; }
</style>
```

### 6-2 建立新增成績表單元件

建立 `src/components/AddScoreForm.vue`：

```vue
<template>
  <div class="form-card">
    <h3>新增成績</h3>

    <p v-if="!selectedStudent" class="no-student">請先點選左側的學生</p>

    <div v-else>
      <p class="selected-hint">正在新增：<strong>{{ selectedStudent.name }}</strong> 的成績</p>

      <div class="form-body">
        <div class="field">
          <label>科目 <span class="required">*</span></label>
          <select v-model="form.subject">
            <option value="">選擇科目</option>
            <option v-for="s in subjects" :key="s" :value="s">{{ s }}</option>
          </select>
        </div>
        <div class="field">
          <label>成績 <span class="required">*</span>（0 ~ 100）</label>
          <input v-model.number="form.score" type="number" min="0" max="100" placeholder="輸入分數" />
        </div>
        <div class="field">
          <label>日期</label>
          <input v-model="form.date" type="date" />
        </div>
      </div>

      <p v-if="errorMsg" class="error-msg">⚠️ {{ errorMsg }}</p>

      <button
        class="btn-submit"
        @click="submit"
        :disabled="submitting"
      >
        {{ submitting ? '新增中...' : '＋ 新增成績' }}
      </button>
    </div>
  </div>
</template>

<script setup>
import { ref, reactive } from 'vue'

const props = defineProps({
  selectedStudent: { type: Object, default: null }
})

const emit = defineEmits(['added'])

const subjects = ['國文', '英文', '數學', '自然', '社會', '物理', '化學', '生物']

const form = reactive({
  subject: '',
  score:   '',
  date:    new Date().toISOString().split('T')[0]   // 預設今天
})
const errorMsg   = ref('')
const submitting = ref(false)

async function submit() {
  errorMsg.value = ''
  if (!form.subject)                           { errorMsg.value = '請選擇科目'; return }
  if (form.score === '' || form.score < 0 || form.score > 100) {
    errorMsg.value = '請輸入 0 到 100 之間的分數'; return
  }

  submitting.value = true
  emit('added', {
    student_id: props.selectedStudent.id,
    subject:    form.subject,
    score:      form.score,
    date:       form.date,
  })
}

function reset() {
  form.subject = ''
  form.score   = ''
  form.date    = new Date().toISOString().split('T')[0]
  errorMsg.value   = ''
  submitting.value = false
}

defineExpose({ reset })
</script>

<style scoped>
.form-card { background: white; border-radius: 12px; padding: 20px; }
h3 { font-size: 16px; color: #333; margin-bottom: 16px; }

.no-student    { color: #aaa; text-align: center; padding: 16px 0; font-size: 14px; }
.selected-hint { font-size: 14px; color: #555; margin-bottom: 14px; background: #f0f6ff; padding: 8px 12px; border-radius: 6px; }

.form-body { display: flex; flex-direction: column; gap: 12px; margin-bottom: 12px; }
.field label { display: block; font-size: 13px; color: #666; margin-bottom: 5px; font-weight: 500; }
.required { color: #c84b2f; }
.field input, .field select {
  width: 100%;
  padding: 9px 12px;
  border: 1px solid #ddd;
  border-radius: 8px;
  font-size: 14px;
  background: white;
}
.field input:focus, .field select:focus { outline: none; border-color: #2a7ae2; }

.error-msg { color: #c84b2f; font-size: 13px; margin-bottom: 10px; }

.btn-submit {
  width: 100%;
  padding: 11px;
  background: #2e6b4f;
  color: white;
  border: none;
  border-radius: 8px;
  font-size: 14px;
  font-weight: 600;
  cursor: pointer;
}
.btn-submit:hover:not(:disabled) { background: #1e4f38; }
.btn-submit:disabled { background: #aaa; cursor: not-allowed; }
</style>
```

---

## 第七步：實作刪除與更新功能

刪除和更新的邏輯都在 `App.vue` 裡統一處理，透過呼叫 `src/api/sheets.js` 的函式完成。

---

## 第八步：完整程式碼整合

### 最終的 App.vue

```vue
<template>
  <div class="app">
    <!-- 頂部標題列 -->
    <header class="app-header">
      <h1>📊 學生成績管理系統</h1>
      <div class="header-status">
        <span v-if="globalLoading" class="loading-dot">⏳</span>
        <span v-if="toastMsg" class="toast" :class="toastType">{{ toastMsg }}</span>
      </div>
    </header>

    <div class="layout">
      <!-- 左欄：學生名單 + 新增學生 -->
      <aside class="left-panel">
        <AddStudentForm
          ref="addStudentForm"
          @added="onAddStudent"
        />
        <StudentList
          :students="students"
          :loading="loadingStudents"
          :error="studentsError"
          :selectedId="selectedStudent?.id"
          @select="onSelectStudent"
          @delete="onDeleteStudent"
        />
      </aside>

      <!-- 右欄：成績列表 + 新增成績 -->
      <main class="right-panel">
        <AddScoreForm
          ref="addScoreForm"
          :selectedStudent="selectedStudent"
          @added="onAddScore"
        />
        <ScoreList
          :scores="scores"
          :studentName="selectedStudent?.name"
          :loading="loadingScores"
          @update="onUpdateScore"
        />
      </main>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

// 元件
import StudentList    from './components/StudentList.vue'
import ScoreList      from './components/ScoreList.vue'
import AddStudentForm from './components/AddStudentForm.vue'
import AddScoreForm   from './components/AddScoreForm.vue'

// API 函式
import {
  getStudents, addStudent, deleteStudent,
  getScores, addScore, updateScore
} from './api/sheets.js'

// ── 狀態 ──────────────────────────────────────────
const students       = ref([])
const scores         = ref([])
const selectedStudent = ref(null)

const loadingStudents = ref(false)
const loadingScores   = ref(false)
const studentsError   = ref(null)
const globalLoading   = ref(false)

// 通知訊息
const toastMsg  = ref('')
const toastType = ref('success')   // 'success' | 'error'

// 表單元件的 ref（用來呼叫 reset 方法）
const addStudentForm = ref(null)
const addScoreForm   = ref(null)

// ── 通知工具函式 ──────────────────────────────────
function showToast(msg, type = 'success') {
  toastMsg.value  = msg
  toastType.value = type
  setTimeout(() => { toastMsg.value = '' }, 3000)
}

// ── 學生相關操作 ──────────────────────────────────

// 頁面載入時取得學生名單
async function loadStudents() {
  loadingStudents.value = true
  studentsError.value   = null
  try {
    students.value = await getStudents()
  } catch (e) {
    studentsError.value = '載入學生失敗：' + e.message
  } finally {
    loadingStudents.value = false
  }
}

// 點選學生：同時載入這位學生的成績
async function onSelectStudent(student) {
  selectedStudent.value = student
  loadingScores.value   = true
  try {
    scores.value = await getScores(student.id)
  } catch (e) {
    showToast('載入成績失敗：' + e.message, 'error')
  } finally {
    loadingScores.value = false
  }
}

// 新增學生
async function onAddStudent(formData) {
  globalLoading.value = true
  try {
    await addStudent(formData)
    await loadStudents()             // 重新載入學生名單
    addStudentForm.value?.reset()    // 清空表單
    showToast('✅ 學生新增成功！')
  } catch (e) {
    showToast('新增失敗：' + e.message, 'error')
    addStudentForm.value?.reset()    // 即使失敗也要重置 submitting 狀態
  } finally {
    globalLoading.value = false
  }
}

// 刪除學生
async function onDeleteStudent(id) {
  if (!confirm('確定要刪除這位學生嗎？')) return

  globalLoading.value = true
  try {
    await deleteStudent(id)
    await loadStudents()

    // 如果刪除的是目前選取的學生，清空右側成績
    if (selectedStudent.value?.id === id) {
      selectedStudent.value = null
      scores.value = []
    }
    showToast('✅ 學生已刪除')
  } catch (e) {
    showToast('刪除失敗：' + e.message, 'error')
  } finally {
    globalLoading.value = false
  }
}

// ── 成績相關操作 ──────────────────────────────────

// 新增成績
async function onAddScore(formData) {
  globalLoading.value = true
  try {
    await addScore(formData)
    // 重新載入這位學生的成績
    scores.value = await getScores(selectedStudent.value.id)
    addScoreForm.value?.reset()
    showToast('✅ 成績新增成功！')
  } catch (e) {
    showToast('新增失敗：' + e.message, 'error')
    addScoreForm.value?.reset()
  } finally {
    globalLoading.value = false
  }
}

// 更新成績
async function onUpdateScore(scoreId, newScore) {
  globalLoading.value = true
  try {
    await updateScore(scoreId, newScore)
    scores.value = await getScores(selectedStudent.value.id)
    showToast('✅ 成績更新成功！')
  } catch (e) {
    showToast('更新失敗：' + e.message, 'error')
  } finally {
    globalLoading.value = false
  }
}

// 頁面載入時執行
onMounted(() => {
  loadStudents()
})
</script>

<style>
* { box-sizing: border-box; margin: 0; padding: 0; }
body { font-family: sans-serif; background: #f0f4f8; min-height: 100vh; }
</style>

<style scoped>
.app { max-width: 1100px; margin: 0 auto; padding: 20px; }

/* 頂部標題 */
.app-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 20px;
}
h1 { font-size: 22px; color: #2a1f14; }

/* 通知 Toast */
.toast {
  font-size: 14px;
  padding: 6px 14px;
  border-radius: 8px;
  font-weight: 500;
}
.toast.success { background: #d4edd9; color: #2e6b4f; }
.toast.error   { background: #fde8e8; color: #c84b2f; }
.loading-dot   { font-size: 18px; }

/* 兩欄佈局 */
.layout {
  display: grid;
  grid-template-columns: 340px 1fr;
  gap: 20px;
  align-items: start;
}

/* 左右欄各自的間距 */
.left-panel, .right-panel {
  display: flex;
  flex-direction: column;
  gap: 16px;
}

/* 手機版改單欄 */
@media (max-width: 700px) {
  .layout { grid-template-columns: 1fr; }
}
</style>
```

---

## 第九步：上傳到 GitHub Pages

### 9-1 建立 GitHub 倉庫

1. 前往 **https://github.com**，登入帳號
2. 點 **+** → **New repository**
3. Repository name 填：`my-grade-system`
4. 選 **Public**，不勾選任何 Initialize 選項
5. 點 **Create repository**

### 9-2 設定 Vite 路徑

打開 `vite.config.js`：

```javascript
import { defineConfig } from 'vite'
import vue from '@vitejs/plugin-vue'

export default defineConfig({
  plugins: [vue()],
  base: '/my-grade-system/',   // ← 和倉庫名稱一樣
})
```

### 9-3 建立自動部署設定

建立 `.github/workflows/deploy.yml`：

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
      - run: npm install
      - run: npm run build
      - uses: actions/configure-pages@v4
      - uses: actions/upload-pages-artifact@v3
        with:
          path: dist
      - uses: actions/deploy-pages@v4
        id: deployment
```

### 9-4 推送到 GitHub

```bash
git init
git add .
git commit -m "完成學生成績管理系統"
git branch -M main
git remote add origin https://github.com/你的帳號/my-grade-system.git
git push -u origin main
```

> 推送時輸入 GitHub Personal Access Token 當密碼  
> 取得方式：GitHub → Settings → Developer settings → Personal access tokens → Generate new token → 勾選 repo

### 9-5 開啟 GitHub Pages

1. 倉庫 → **Settings** → **Pages**
2. **Source** 選 **GitHub Actions** → Save
3. 點 **Actions** 頁籤，等綠色勾勾（約 1～2 分鐘）
4. 網址：`https://你的帳號.github.io/my-grade-system/`

---

## 常見問題排查

### 問題一：API 回傳資料，但 Vue 畫面沒有更新

**原因**：試算表 ID 或工作表名稱有誤，或 Apps Script 尚未重新部署。

**解決**：
1. 先用瀏覽器直接測試 API 網址，確認能取到資料
2. 檢查工作表名稱是否完全對應（`students`、`scores`，區分大小寫）
3. 修改 Apps Script 後，必須重新部署（**部署 → 管理部署 → 編輯 → 新增版本 → 部署**）

### 問題二：POST 請求失敗，瀏覽器 Console 顯示 CORS 錯誤

**原因**：Content-Type 設定問題。

**解決**：確認 `src/api/sheets.js` 裡的 axios 設定有：

```javascript
headers: { 'Content-Type': 'text/plain' }
```

### 問題三：Apps Script 顯示「授權失敗」

**原因**：試算表和 Apps Script 的 Google 帳號不同。

**解決**：確認開啟 Apps Script 時，Google 帳號和試算表是同一個帳號。

### 問題四：新增資料後，畫面沒有自動更新

**原因**：忘記在成功後重新呼叫讀取函式。

**解決**：確認 `onAddStudent` 和 `onAddScore` 函式裡有 `await loadStudents()` / `await getScores(...)`。

### 問題五：GitHub Pages 部署後出現空白頁面

**原因**：`vite.config.js` 的 `base` 路徑設定不正確。

**解決**：確認 `base: '/倉庫名稱/'` 和 GitHub 的倉庫名稱完全一樣（含大小寫）。

---

## 完整專案結構

```
my-grade-system/
├── .github/
│   └── workflows/
│       └── deploy.yml          ← 自動部署設定
├── src/
│   ├── api/
│   │   └── sheets.js           ← 所有 API 呼叫函式
│   ├── components/
│   │   ├── StudentList.vue     ← 學生名單顯示元件
│   │   ├── ScoreList.vue       ← 成績列表 + 行內編輯
│   │   ├── AddStudentForm.vue  ← 新增學生表單
│   │   └── AddScoreForm.vue    ← 新增成績表單
│   ├── App.vue                 ← 主元件（統一處理 API 呼叫）
│   └── main.js
├── index.html
├── package.json
└── vite.config.js
```

---

## 這個專案學到了什麼

| 概念 | 在這個專案怎麼用 |
|---|---|
| Google Sheets 當資料庫 | 試算表存學生和成績，直接在格子裡看和改 |
| Google Apps Script | 把試算表操作包裝成 HTTP API |
| `doGet(e)` | 根據 `e.parameter.action` 分派讀取操作 |
| `doPost(e)` | 根據 `body.action` 分派寫入操作 |
| `sheetToObjects()` | 把試算表第一列當 key，把每列資料轉成物件 |
| `axios.get()` | Vue 呼叫 API 讀取資料 |
| `axios.post()` | Vue 呼叫 API 寫入資料 |
| `Content-Type: text/plain` | 解決 Google Apps Script 的 CORS 問題 |
| `defineExpose({ reset })` | 讓父元件可以呼叫子元件的方法 |
| `onMounted` | 頁面載入時自動取得學生名單 |
| Toast 通知 | 操作成功或失敗時顯示 3 秒後消失的提示 |

---

## 挑戰加分題

**初級**
- 加上「重新整理」按鈕，手動重新載入資料
- 在學生列表加上搜尋功能（用 `computed` 篩選 `students`）

**中級**
- 把成績以長條圖顯示（可以用 `<div>` + `width` style 模擬）
- 加上「匯出 CSV」功能（把成績資料轉成 CSV 格式讓使用者下載）

**進階**
- 加上分頁功能（每頁顯示 10 筆，加上上一頁 / 下一頁按鈕）
- 新增「班級篩選」，只顯示選定班級的學生

---

*Google Apps Script 官方文件：https://developers.google.com/apps-script*  
*Google Sheets API 說明：https://developers.google.com/sheets/api*
