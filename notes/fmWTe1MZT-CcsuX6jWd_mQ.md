---
title: Vue.js 入門講義：從零開始做動態網頁
tags: [114_下學期_互動程式設計]

---

# Vue.js 入門講義：從零開始做動態網頁

## 課程目標

學完本講義，你將能夠：
- 理解 Vue.js 的核心概念
- 建立一個有互動的動態網頁
- 動手完成一個「待辦事項清單」專案

---

## 第一章：什麼是 Vue.js？

Vue.js 是一個用來建立「動態網頁介面」的 JavaScript 框架。

傳統 HTML 網頁是靜態的，你改 HTML 才會改變畫面。但有了 Vue，當「資料」改變時，「畫面」會自動跟著更新，不需要你手動操作 DOM。

**傳統 JavaScript 做法（繁瑣）：**

```html=
<p id="msg"></p>
<script>
  let name = "小明"
  document.getElementById("msg").textContent = "你好，" + name
  // 每次資料改變都要手動更新畫面
</script>
```

**Vue 的做法（簡單）：**

```html=
<p>{{ message }}</p>
<script>
  // 只要改 message，畫面自動更新！
  data() {
    return { message: "你好，小明" }
  }
</script>
```

---

## 第二章：快速開始（CDN 版，不需安裝）

最簡單的方式：直接在 HTML 引入 Vue，不需要安裝任何東西。

新增一個 `index.html` 檔案，貼入以下內容：

```html
<!DOCTYPE html>
<html lang="zh-TW">
<head>
  <meta charset="UTF-8">
  <title>我的第一個 Vue 頁面</title>
</head>
<body>

  <div id="app">
    <h1>{{ title }}</h1>
    <p>目前計數：{{ count }}</p>
    <button @click="count++">點我 +1</button>
  </div>

  <!-- 引入 Vue -->
  <script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
  <script>
    Vue.createApp({
      data() {
        return {
          title: "Hello Vue！",
          count: 0
        }
      }
    }).mount("#app")
  </script>

</body>
</html>
```

用瀏覽器打開這個檔案，點按鈕，數字會自動增加！

---

## 第三章：四大核心概念

### 3.1 資料綁定（Data Binding）— `{{ }}`

用雙大括號把資料顯示在畫面上，資料改變畫面就自動更新。

```html
<div id="app">
  <p>姓名：{{ name }}</p>
  <p>年齡：{{ age }}</p>
  <p>自我介紹：{{ name }} 今年 {{ age }} 歲</p>
</div>

<script>
Vue.createApp({
  data() {
    return {
      name: "小華",
      age: 20
    }
  }
}).mount("#app")
</script>
```

### 注意沒有加入

```html=
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
```




### 3.2 事件處理（Event Handling）— `@click`

`@click` 是 Vue 的事件語法，當使用者點擊時執行函式。

```html
<div id="app">
  <p>你點了 {{ count }} 次</p>
  <button @click="addOne">點我</button>
  <button @click="reset">重設</button>
</div>

<script>
Vue.createApp({
  data() {
    return { count: 0 }
  },
  methods: {
    addOne() {
      this.count++
    },
    reset() {
      this.count = 0
    }
  }
}).mount("#app")
</script>
```

常見的事件：

| 語法 | 說明 |
|------|------|
| `@click` | 點擊滑鼠 |
| `@input` | 輸入文字時 |
| `@keyup.enter` | 按下 Enter 鍵 |
| `@mouseover` | 滑鼠移入 |

### 3.3 雙向綁定（Two-way Binding）— `v-model`

`v-model` 讓輸入框和資料保持同步——輸入框改，資料改；資料改，輸入框也跟著變。

```html
<div id="app">
  <input v-model="name" placeholder="輸入你的名字" />
  <p>你好，{{ name }}！</p>
</div>

<script>
Vue.createApp({
  data() {
    return { name: "" }
  }
}).mount("#app")
</script>
```

試著在輸入框打字，下方的問候語會即時更新。

### 3.4 條件與迴圈（v-if / v-for）

**v-if：根據條件顯示或隱藏元素**

```html
<div id="app">
  <button @click="show = !show">切換顯示</button>
  <p v-if="show">👋 你看到我了！</p>
  <p v-else>（已隱藏）</p>
</div>

<script>
Vue.createApp({
  data() {
    return { show: true }
  }
}).mount("#app")
</script>
```

**v-for：用陣列資料產生列表**

```html
<div id="app">
  <ul>
    <li v-for="fruit in fruits" :key="fruit">
      {{ fruit }}
    </li>
  </ul>
</div>

<script>
Vue.createApp({
  data() {
    return {
      fruits: ["蘋果", "香蕉", "芒果", "草莓"]
    }
  }
}).mount("#app")
</script>
```

---

## 第四章：計算屬性（Computed）

`computed` 是根據現有資料「自動計算」出來的值，資料一改，計算結果也自動更新。

```html
<div id="app">
  <input v-model="price" type="number" placeholder="原價" />
  <p>原價：{{ price }} 元</p>
  <p>打八折後：{{ discounted }} 元</p>
  <p>含稅（5%）：{{ withTax }} 元</p>
</div>

<script>
Vue.createApp({
  data() {
    return { price: 100 }
  },
  computed: {
    discounted() {
      return Math.round(this.price * 0.8)
    },
    withTax() {
      return Math.round(this.discounted * 1.05)
    }
  }
}).mount("#app")
</script>
```

**computed vs methods 的差異：**

| 比較 | computed | methods |
|------|----------|---------|
| 觸發時機 | 資料改變時自動更新 | 每次呼叫都執行 |
| 有快取 | ✅ 有（效能較好） | ❌ 沒有 |
| 使用場景 | 衍生資料 | 執行動作 |

---

## 第五章：屬性綁定（v-bind / :）

`v-bind:` 可縮寫成 `:`，用來動態設定 HTML 屬性。

```html
<div id="app">
  <input v-model="color" placeholder="輸入顏色，如 red、blue" />
  
  <!-- 動態改變樣式 -->
  <p :style="{ color: color }">這段文字的顏色會改變</p>
  
  <!-- 動態切換 CSS class -->
  <p :class="{ big: isBig }">文字大小</p>
  <button @click="isBig = !isBig">切換大小</button>
</div>

<style>
  .big { font-size: 32px; font-weight: bold; }
</style>

<script>
Vue.createApp({
  data() {
    return {
      color: "black",
      isBig: false
    }
  }
}).mount("#app")
</script>
```

---

## 第六章：實作專案——待辦事項清單

把所有概念整合起來，做一個完整的 To-do List！

功能包含：
- 新增待辦事項（輸入框 + 按 Enter）
- 勾選完成/未完成
- 刪除事項
- 顯示剩餘未完成數量

```html
<!DOCTYPE html>
<html lang="zh-TW">
<head>
  <meta charset="UTF-8">
  <title>待辦事項清單</title>
  <style>
    body {
      font-family: sans-serif;
      max-width: 500px;
      margin: 40px auto;
      padding: 0 20px;
      background: #f5f5f5;
    }
    h1 { color: #333; }
    .input-area {
      display: flex;
      gap: 8px;
      margin-bottom: 16px;
    }
    input[type="text"] {
      flex: 1;
      padding: 8px 12px;
      border: 1px solid #ccc;
      border-radius: 6px;
      font-size: 16px;
    }
    button {
      padding: 8px 16px;
      background: #4a90e2;
      color: white;
      border: none;
      border-radius: 6px;
      cursor: pointer;
      font-size: 16px;
    }
    button:hover { background: #357abd; }
    .todo-item {
      display: flex;
      align-items: center;
      gap: 10px;
      background: white;
      padding: 12px;
      margin-bottom: 8px;
      border-radius: 6px;
      box-shadow: 0 1px 3px rgba(0,0,0,0.1);
    }
    .done-text {
      text-decoration: line-through;
      color: #aaa;
      flex: 1;
    }
    .normal-text { flex: 1; }
    .delete-btn {
      background: #e74c3c;
      padding: 4px 10px;
      font-size: 13px;
    }
    .delete-btn:hover { background: #c0392b; }
    .summary {
      color: #666;
      font-size: 14px;
      margin-top: 12px;
    }
  </style>
</head>
<body>

<div id="app">
  <h1>📝 待辦事項</h1>

  <!-- 輸入區 -->
  <div class="input-area">
    <input
      v-model="newTodo"
      @keyup.enter="addTodo"
      type="text"
      placeholder="輸入待辦事項，按 Enter 新增"
    />
    <button @click="addTodo">新增</button>
  </div>

  <!-- 待辦清單 -->
  <div
    v-for="todo in todos"
    :key="todo.id"
    class="todo-item"
  >
    <input type="checkbox" v-model="todo.done" />
    <span :class="todo.done ? 'done-text' : 'normal-text'">
      {{ todo.text }}
    </span>
    <button class="delete-btn" @click="removeTodo(todo.id)">刪除</button>
  </div>

  <!-- 空清單提示 -->
  <p v-if="todos.length === 0" style="color:#aaa">還沒有待辦事項，新增一個吧！</p>

  <!-- 統計 -->
  <p class="summary" v-if="todos.length > 0">
    共 {{ todos.length }} 項，待完成 {{ remaining }} 項
  </p>
</div>

<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
Vue.createApp({
  data() {
    return {
      newTodo: "",      // 輸入框的文字
      nextId: 1,        // 用來產生不重複 id
      todos: [
        { id: 1, text: "學習 Vue.js 基礎", done: true },
        { id: 2, text: "完成待辦清單專案", done: false },
        { id: 3, text: "繼續學習 Vue 進階功能", done: false }
      ]
    }
  },
  computed: {
    // 計算未完成的數量
    remaining() {
      return this.todos.filter(todo => !todo.done).length
    }
  },
  methods: {
    // 新增待辦事項
    addTodo() {
      const text = this.newTodo.trim()
      if (!text) return          // 空白就不新增
      this.nextId++
      this.todos.push({
        id: this.nextId,
        text: text,
        done: false
      })
      this.newTodo = ""          // 清空輸入框
    },
    // 刪除待辦事項
    removeTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id)
    }
  }
}).mount("#app")
</script>

</body>
</html>
```

---

## 第七章：概念複習速查表

| 語法 | 功能 | 範例 |
|------|------|------|
| `{{ }}` | 顯示資料 | `{{ name }}` |
| `v-model` | 雙向綁定 | `<input v-model="text">` |
| `@click` | 點擊事件 | `<button @click="fn">` |
| `@keyup.enter` | Enter 鍵事件 | `<input @keyup.enter="fn">` |
| `v-if` | 條件顯示 | `<p v-if="show">` |
| `v-else` | 否則顯示 | `<p v-else>` |
| `v-for` | 迴圈渲染 | `<li v-for="i in list">` |
| `:key` | 迴圈唯一識別 | `<li :key="item.id">` |
| `:class` | 動態 class | `<p :class="{ active: isOn }">` |
| `:style` | 動態樣式 | `<p :style="{ color: c }">` |
| `computed` | 自動計算屬性 | `computed: { total() {...} }` |
| `methods` | 定義函式 | `methods: { doSomething() {...} }` |

---

## 第八章：下一步學什麼？

掌握本講義後，建議繼續學習：

**Vue 進階主題：**
- **元件（Components）**：把 UI 拆成可重複使用的積木
- **Vue Router**：做多頁面的單頁應用（SPA）
- **Pinia**：全域狀態管理（多個元件共享資料）
- **Vue 3 Composition API**：更彈性的程式組織方式

**搭配工具：**
- **Vite**：快速的開發環境建置工具
- **Tailwind CSS**：快速樣式框架
- **Axios**：呼叫後端 API 取得資料

**練習專案建議：**
1. 計算機（練習 computed）
2. 天氣查詢（練習 API 呼叫）
3. 簡易購物車（練習元件 + 狀態管理）
4. 本講義延伸的點餐系統（實際應用）

---

*Vue.js 官方文件（中文）：https://cn.vuejs.org*
