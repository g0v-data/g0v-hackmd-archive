---
title: 用 Vue 做一個計算機
tags: [114_下學期_互動程式設計]

---

# 練習專案：用 Vue 做一個計算機


> 難度：★★☆☆☆  
> 前置：已完成《Vue.js 入門講義》或《Vue.js 進階入門講義》  
> 完成後：一個長得像手機計算機的網頁，能加減乘除，並上傳到 GitHub

---
https://cfchengit.github.io/20260423_1/
![image](https://hackmd.io/_uploads/Byl9m8w6Wl.png)


## 學習地圖

這份講義把計算機分成 **6 個階段**，每個階段都能在瀏覽器看到結果：

```
階段一：只有按鈕，點了會顯示數字
   ↓
階段二：加上顯示幕，看到輸入的算式
   ↓
階段三：加上 computed，即時顯示計算結果
   ↓
階段四：加上運算子按鈕（+ - × ÷）
   ↓
階段五：加上等號和清除，變成可用的計算機
   ↓
階段六：美化外觀，變成像手機計算機的樣子
   ↓
上傳 GitHub Pages，用網址分享給朋友
```

> 💡 **學習方式建議**：每個階段做完就在瀏覽器測試，確認功能正常再繼續下一階段。

---

## 開始前：建立專案

### 方法 A：本地安裝（有 Node.js 的環境）

```bash
npm create vite@latest my-calculator
cd my-calculator
npm install
npm run dev
```

瀏覽器開啟 `http://localhost:5173`

### 方法 B：StackBlitz 線上版（電腦教室推薦）

1. 前往 **https://stackblitz.com**
2. 點 **New Project** → **Vue**
3. 左側可以看到 `src/App.vue`，直接編輯就好

### 清空預設內容

不管哪個方法，先把 `src/App.vue` 的內容**全部清空**，換成這個最基本的骨架：

```vue
<template>
  <div class="calculator">
    <p>計算機來了</p>
  </div>
</template>

<script setup>
// 等一下在這裡寫邏輯
</script>

<style scoped>
/* 等一下在這裡寫樣式 */
</style>
```

存檔後，瀏覽器應該顯示「計算機來了」這幾個字。確認沒問題後繼續。

---

## 階段一：讓按鈕出現，點了有反應

### 目標

做出幾個數字按鈕，點了之後用 `alert` 彈窗顯示你按了什麼。

### 先想清楚計算機要有什麼

一個基本計算機需要：
- 數字按鈕：0 ~ 9
- 運算子按鈕：+ - × ÷
- 小數點：.
- 等號：=
- 清除：AC

我們先做最簡單的版本：**三個數字按鈕**，點了彈出提示。

### 修改 App.vue

```vue
<template>
  <div class="calculator">
    <h2>我的計算機</h2>

    <!-- 先做三個按鈕試試 -->
    <button @click="pressButton('1')">1</button>
    <button @click="pressButton('2')">2</button>
    <button @click="pressButton('3')">3</button>
  </div>
</template>

<script setup>
function pressButton(value) {
  alert('你按了：' + value)
}
</script>

<style scoped>
button {
  width: 60px;
  height: 60px;
  font-size: 20px;
  margin: 4px;
  cursor: pointer;
}
</style>
```

### 存檔，測試看看

點 1、2、3 這三個按鈕，應該會分別彈出「你按了：1」、「你按了：2」、「你按了：3」。

> ✅ **成功了嗎？** 代表 `@click` 和函式呼叫都沒問題，可以繼續。

### 這個階段學到什麼

- `@click="pressButton('1')"` — 點擊時呼叫函式，並傳入參數 `'1'`
- 函式接到 `value`，就可以知道使用者按了哪個按鈕
- 所有數字按鈕共用同一個函式，靠傳入不同的參數來區分

---

## 階段二：把輸入的內容顯示在畫面上

### 目標

不用 `alert` 了——改成把按下的按鍵**串接**起來，顯示在畫面上的「顯示幕」區域。

### 需要新增的概念

**`ref`**：用來儲存「目前輸入的算式」，每次按按鈕就把字元加進去。

```
使用者按 1 → expression 變成 "1"
使用者按 2 → expression 變成 "12"
使用者按 + → expression 變成 "12+"
使用者按 3 → expression 變成 "12+3"
```

### 修改 App.vue

```vue
<template>
  <div class="calculator">

    <!-- 顯示幕：顯示目前輸入的算式 -->
    <div class="display">
      <p class="expression">{{ expression || '0' }}</p>
    </div>

    <!-- 按鈕區（先只做 1、2、3 確認效果）-->
    <div class="keypad">
      <button @click="pressButton('1')">1</button>
      <button @click="pressButton('2')">2</button>
      <button @click="pressButton('3')">3</button>
    </div>

  </div>
</template>

<script setup>
import { ref } from 'vue'

// expression：記錄使用者目前輸入的算式
// 例如使用者按了 1、2、+、3，expression 就是 "12+3"
const expression = ref('')

function pressButton(value) {
  // 把新按的字元加到算式的後面
  expression.value = expression.value + value
}
</script>

<style scoped>
.display {
  background: #222;
  padding: 16px;
  margin-bottom: 8px;
  border-radius: 8px;
  text-align: right;
}
.expression {
  color: white;
  font-size: 28px;
  margin: 0;
  min-height: 40px;
}
button {
  width: 60px;
  height: 60px;
  font-size: 20px;
  margin: 4px;
  cursor: pointer;
}
</style>
```

### 測試看看

按 1、2、3，顯示幕應該依序顯示 `1`、`12`、`123`。

> 💡 **`expression || '0'` 是什麼意思？**  
> `||` 是「或」的意思。當 `expression` 是空字串（還沒按任何按鈕）時，顯示 `'0'`；一旦有內容就顯示內容。這樣畫面上永遠不會是空白的。

### 這個階段學到什麼

- `ref('')` — 建立一個初始值為空字串的響應式資料
- `expression.value = expression.value + value` — 把新字元串在後面
- `{{ expression || '0' }}` — 有值就顯示值，沒值就顯示 `'0'`

---

## 階段三：加上 computed，即時計算結果

### 目標

讓顯示幕同時顯示：上方是「輸入的算式」，下方是「即時計算的結果」。

使用者每按一個按鍵，結果就自動更新，不需要按等號。

### computed 的概念複習

`computed` 是「自動計算的屬性」：當它依賴的資料（這裡是 `expression`）改變時，computed 的值就自動重新計算。

```
expression = "12+3"   → result 自動計算 → 顯示 15
expression = "12+30"  → result 自動計算 → 顯示 42
expression = "12+3*"  → result 計算失敗 → 顯示 "..."
```

### 修改 App.vue

```vue
<template>
  <div class="calculator">

    <!-- 顯示幕：上方算式，下方即時結果 -->
    <div class="display">
      <p class="expression">{{ expression || '0' }}</p>
      <p class="result">= {{ result }}</p>
    </div>

    <div class="keypad">
      <button @click="pressButton('1')">1</button>
      <button @click="pressButton('2')">2</button>
      <button @click="pressButton('3')">3</button>
      <button @click="pressButton('+')">+</button>
      <button @click="pressButton('-')">-</button>
    </div>

  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const expression = ref('')

// computed：只要 expression 改變，result 就自動重新計算
const result = computed(() => {

  // 如果還沒輸入任何東西，顯示 0
  if (!expression.value) return '0'

  try {
    // Function() 可以執行一段 JavaScript 字串
    // 例如：expression 是 "12+3"，Function 就執行這個計算
    const value = Function('"use strict"; return (' + expression.value + ')')()

    // 避免出現 0.1+0.2=0.30000000000000004 這種浮點數問題
    return Math.round(value * 1e10) / 1e10

  } catch {
    // 如果算式還沒輸入完整（例如 "12+"），計算會失敗
    // 用 try...catch 捕捉錯誤，顯示 "..." 表示還在輸入
    return '...'
  }
})

function pressButton(value) {
  expression.value = expression.value + value
}
</script>

<style scoped>
.display {
  background: #222;
  padding: 16px;
  margin-bottom: 8px;
  border-radius: 8px;
  text-align: right;
}
.expression {
  color: white;
  font-size: 28px;
  margin: 0 0 4px;
  min-height: 40px;
}
.result {
  color: #aaa;
  font-size: 18px;
  margin: 0;
}
button {
  width: 60px;
  height: 60px;
  font-size: 20px;
  margin: 4px;
  cursor: pointer;
}
</style>
```

### 測試看看

- 按 `1`、`2`、`+`、`3` → 上方顯示 `12+3`，下方顯示 `= 15`
- 按到 `+` 時下方顯示 `= ...`（算式還沒完成，正常的）

> 💡 **`Function('"use strict"; return (' + expression.value + ')')()` 怎麼理解？**  
> 把它想成一個「把文字變成真正計算的翻譯機」。  
> 你傳進去 `"12+3"` 這個字串，它回傳數字 `15`。  
> `try...catch` 則是說「嘗試計算，如果失敗就不要讓整個程式當掉，改回傳 `'...'`」。

### 這個階段學到什麼

- `computed(() => {...})` — 依賴的資料改變時自動重新執行
- `try...catch` — 「嘗試執行，失敗時有備案」，讓程式更穩定
- `Math.round(value * 1e10) / 1e10` — 處理浮點數精度問題的慣用寫法

---

## 階段四：加上全部的數字和運算子按鈕

### 目標

把 0 ~ 9 的數字全部加上去，加上 × ÷ 運算子，還有小數點。

### 重要觀念：顯示符號 vs 計算符號

計算機顯示給使用者看的是 `×` 和 `÷`，但 JavaScript 只認識 `*` 和 `/`。

解決方式：**存入 `expression` 時用 `*` 和 `/`，顯示時還是顯示 `×` 和 `÷`**。

不過這樣做的話，顯示幕顯示的算式會有 `*` 和 `/`，不夠好看。

更好的解法：存入時就存 `×` 和 `÷`，計算前再換回 `*` 和 `/`。

```javascript
// 計算前：把顯示符號換成 JS 認識的符號
const jsExpr = expression.value
  .replace(/×/g, '*')
  .replace(/÷/g, '/')
```

### 修改 App.vue

```vue
<template>
  <div class="calculator">

    <div class="display">
      <p class="expression">{{ expression || '0' }}</p>
      <p class="result">= {{ result }}</p>
    </div>

    <div class="keypad">
      <!-- 第一行 -->
      <button @click="pressButton('7')">7</button>
      <button @click="pressButton('8')">8</button>
      <button @click="pressButton('9')">9</button>
      <button @click="pressButton('÷')" class="op">÷</button>

      <!-- 第二行 -->
      <button @click="pressButton('4')">4</button>
      <button @click="pressButton('5')">5</button>
      <button @click="pressButton('6')">6</button>
      <button @click="pressButton('×')" class="op">×</button>

      <!-- 第三行 -->
      <button @click="pressButton('1')">1</button>
      <button @click="pressButton('2')">2</button>
      <button @click="pressButton('3')">3</button>
      <button @click="pressButton('-')" class="op">-</button>

      <!-- 第四行 -->
      <button @click="pressButton('0')">0</button>
      <button @click="pressButton('.')">.</button>
      <button @click="pressButton('%')">%</button>
      <button @click="pressButton('+')" class="op">+</button>
    </div>

  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const expression = ref('')

const result = computed(() => {
  if (!expression.value) return '0'
  try {
    // 把 × 和 ÷ 換回 JavaScript 認識的 * 和 /
    const jsExpr = expression.value
      .replace(/×/g, '*')
      .replace(/÷/g, '/')

    const value = Function('"use strict"; return (' + jsExpr + ')')()
    return Math.round(value * 1e10) / 1e10
  } catch {
    return '...'
  }
})

function pressButton(value) {
  expression.value = expression.value + value
}
</script>

<style scoped>
.display {
  background: #222;
  padding: 16px;
  margin-bottom: 8px;
  border-radius: 8px;
  text-align: right;
}
.expression { color: white; font-size: 28px; margin: 0 0 4px; min-height: 40px; }
.result     { color: #aaa; font-size: 18px; margin: 0; }

.keypad {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 8px;
}
button {
  height: 60px;
  font-size: 20px;
  border: none;
  border-radius: 8px;
  background: #444;
  color: white;
  cursor: pointer;
}
button.op { background: #ff9500; }
button:hover { opacity: 0.8; }
</style>
```

### 測試看看

- 按 `3`、`×`、`5` → 顯示 `3×5`，下方顯示 `= 15` ✅
- 按 `1`、`0`、`÷`、`4` → 顯示 `10÷4`，下方顯示 `= 2.5` ✅

> 💡 **`grid-template-columns: repeat(4, 1fr)` 是什麼？**  
> 這是 CSS Grid 的語法，意思是「分成 4 欄，每欄等寬」。  
> 我們放了 16 個按鈕，4 欄自動換行，就會變成 4×4 的格子。

---

## 階段五：加上等號和清除按鈕

### 目標

加上最重要的兩個功能：
- **AC（全部清除）**：清空算式
- **= （等號）**：把計算結果當作下一次的起點

### 等號的邏輯

按下等號時，我們希望：
1. 如果目前的計算結果是有效數字（不是 `'...'`），就把 `expression` 設成計算結果
2. 之後可以繼續在這個數字後面接著算

```
按 3 × 5 =   → expression 從 "3×5" 變成 "15"
繼續按 + 2 =  → expression 變成 "15+2" → 結果是 17
```

### 修改 App.vue

在 `<template>` 裡，把第一行改成有 AC 和等號的樣子：

```vue
<template>
  <div class="calculator">

    <div class="display">
      <p class="expression">{{ expression || '0' }}</p>
      <p class="result">= {{ result }}</p>
    </div>

    <div class="keypad">
      <!-- 第一行：AC 佔兩格、% 、÷ -->
      <button @click="clear" class="ac" style="grid-column: span 2;">AC</button>
      <button @click="pressButton('%')">%</button>
      <button @click="pressButton('÷')" class="op">÷</button>

      <!-- 第二行 -->
      <button @click="pressButton('7')">7</button>
      <button @click="pressButton('8')">8</button>
      <button @click="pressButton('9')">9</button>
      <button @click="pressButton('×')" class="op">×</button>

      <!-- 第三行 -->
      <button @click="pressButton('4')">4</button>
      <button @click="pressButton('5')">5</button>
      <button @click="pressButton('6')">6</button>
      <button @click="pressButton('-')" class="op">-</button>

      <!-- 第四行 -->
      <button @click="pressButton('1')">1</button>
      <button @click="pressButton('2')">2</button>
      <button @click="pressButton('3')">3</button>
      <button @click="pressButton('+')" class="op">+</button>

      <!-- 第五行：0 佔兩格、.、= -->
      <button @click="pressButton('0')" style="grid-column: span 2; text-align: left; padding-left: 20px;">0</button>
      <button @click="pressButton('.')">.</button>
      <button @click="calculate" class="op">=</button>
    </div>

  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const expression = ref('')

const result = computed(() => {
  if (!expression.value) return '0'
  try {
    const jsExpr = expression.value
      .replace(/×/g, '*')
      .replace(/÷/g, '/')
    const value = Function('"use strict"; return (' + jsExpr + ')')()
    return Math.round(value * 1e10) / 1e10
  } catch {
    return '...'
  }
})

function pressButton(value) {
  expression.value = expression.value + value
}

// 清除：把算式歸零
function clear() {
  expression.value = ''
}

// 等號：把計算結果設成新的算式起點
function calculate() {
  // result.value 就是 computed 計算出的結果
  // 如果是 '...' 代表算式不完整，不執行
  if (result.value !== '...') {
    expression.value = String(result.value)
  }
}
</script>

<style scoped>
.display {
  background: #222;
  padding: 16px;
  margin-bottom: 8px;
  border-radius: 8px;
  text-align: right;
}
.expression { color: white; font-size: 28px; margin: 0 0 4px; min-height: 40px; }
.result     { color: #aaa; font-size: 18px; margin: 0; }

.keypad {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 8px;
}
button {
  height: 60px;
  font-size: 20px;
  border: none;
  border-radius: 8px;
  background: #444;
  color: white;
  cursor: pointer;
}
button.op { background: #ff9500; }
button.ac { background: #636366; }
button:hover { opacity: 0.8; }
</style>
```

### 測試完整功能

| 操作 | 預期結果 |
|---|---|
| 按 `5` `×` `8` `=` | 顯示 `40` |
| 接著按 `+` `10` `=` | 顯示 `50` |
| 按 `AC` | 顯示 `0` |
| 按 `1` `÷` `3` | 下方顯示 `0.3333333333` |
| 算式不完整時按 `=` | 什麼都不發生（`...` 時不執行）|

> ✅ 到這裡，計算機的核心功能已經完成了！接下來只是讓它更好看。

---

## 階段六：美化成手機計算機的外觀

### 目標

把計算機改造成深色背景、圓形按鍵的風格，接近 iPhone 計算機的感覺。

### 調整重點

- 整體背景深色（`#1c1c1e`）
- 數字按鍵用深灰（`#3a3a3c`）
- 運算子用橘色（`#ff9500`）
- AC 用中灰（`#636366`）
- 按鍵做成圓形（`border-radius: 50%`）
- 顯示幕字體放大

### 完整的最終版 App.vue

```vue
<template>
  <div class="calculator">

    <!-- 顯示幕 -->
    <div class="display">
      <p class="expression">{{ expression || '0' }}</p>
      <p class="result">= {{ result }}</p>
    </div>

    <!-- 按鍵區 -->
    <div class="keypad">
      <!-- 第一行 -->
      <button @click="clear"               class="btn gray wide">AC</button>
      <button @click="pressButton('%')"    class="btn gray">%</button>
      <button @click="pressButton('÷')"   class="btn orange">÷</button>

      <!-- 第二行 -->
      <button @click="pressButton('7')"   class="btn">7</button>
      <button @click="pressButton('8')"   class="btn">8</button>
      <button @click="pressButton('9')"   class="btn">9</button>
      <button @click="pressButton('×')"  class="btn orange">×</button>

      <!-- 第三行 -->
      <button @click="pressButton('4')"   class="btn">4</button>
      <button @click="pressButton('5')"   class="btn">5</button>
      <button @click="pressButton('6')"   class="btn">6</button>
      <button @click="pressButton('-')"   class="btn orange">－</button>

      <!-- 第四行 -->
      <button @click="pressButton('1')"   class="btn">1</button>
      <button @click="pressButton('2')"   class="btn">2</button>
      <button @click="pressButton('3')"   class="btn">3</button>
      <button @click="pressButton('+')"   class="btn orange">＋</button>

      <!-- 第五行 -->
      <button @click="pressButton('0')"   class="btn wide-left">0</button>
      <button @click="pressButton('.')"   class="btn">.</button>
      <button @click="calculate"           class="btn orange">=</button>
    </div>

  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const expression = ref('')

const result = computed(() => {
  if (!expression.value) return '0'
  try {
    const jsExpr = expression.value
      .replace(/×/g, '*')
      .replace(/÷/g, '/')
    const value = Function('"use strict"; return (' + jsExpr + ')')()
    return Math.round(value * 1e10) / 1e10
  } catch {
    return '...'
  }
})

function pressButton(value) {
  expression.value = expression.value + value
}

function clear() {
  expression.value = ''
}

function calculate() {
  if (result.value !== '...') {
    expression.value = String(result.value)
  }
}
</script>

<style>
/* 全域：讓頁面背景也是深色 */
body {
  background: #000;
  margin: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
}
</style>

<style scoped>
/* 計算機外殼 */
.calculator {
  width: 320px;
  background: #1c1c1e;
  border-radius: 40px;
  padding: 24px 20px 32px;
  box-shadow: 0 30px 80px rgba(0, 0, 0, 0.8);
}

/* 顯示幕 */
.display {
  padding: 12px 8px 20px;
  text-align: right;
  min-height: 110px;
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
}
.expression {
  color: white;
  font-size: 48px;
  font-weight: 200;
  margin: 0;
  line-height: 1.1;
  word-break: break-all;
}
.result {
  color: #636366;
  font-size: 22px;
  margin: 6px 0 0;
}

/* 按鍵區 */
.keypad {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 12px;
}

/* 基本按鍵 */
.btn {
  height: 72px;
  border: none;
  border-radius: 50%;
  font-size: 28px;
  font-weight: 300;
  color: white;
  background: #3a3a3c;
  cursor: pointer;
  transition: opacity 0.1s;
}
.btn:active { opacity: 0.6; }

/* 橘色運算子 */
.btn.orange { background: #ff9500; }

/* 灰色（AC、%） */
.btn.gray { background: #636366; }

/* 寬版按鍵：AC 和 0 */
.btn.wide {
  grid-column: span 2;
  border-radius: 36px;
  text-align: left;
  padding-left: 28px;
}
.btn.wide-left {
  grid-column: span 2;
  border-radius: 36px;
  text-align: left;
  padding-left: 28px;
}
</style>
```

### 存檔，看看成果

深色背景、圓形按鍵、橘色運算子——計算機完成了！

---

## 階段六補充：加上退格鍵（進階選項）

如果按錯了，可以加一個退格鍵（⌫）讓使用者刪掉最後一個字元。

在 `<script setup>` 加上這個函式：

```javascript
function backspace() {
  // slice(0, -1) 的意思：取字串從開頭到「倒數第一個字元之前」
  // 例如 "123+" → "123"
  expression.value = expression.value.slice(0, -1)
}
```

在 template 裡，把 AC 按鈕改成佔一格，旁邊加上退格鍵：

```html
<button @click="clear"     class="btn gray">AC</button>
<button @click="backspace" class="btn gray">⌫</button>
<button @click="pressButton('%')" class="btn gray">%</button>
<button @click="pressButton('÷')" class="btn orange">÷</button>
```

> 💡 **`slice(0, -1)` 怎麼理解？**  
> 想像一條繩子，`slice(開始位置, 結束位置)` 是剪取一段。  
> `0` 代表從頭，`-1` 代表「不包含最後一個字元」。  
> 所以 `"hello".slice(0, -1)` 的結果是 `"hell"`。

---

## 上傳到 GitHub，讓作品上線

### 步驟一：建立 GitHub 倉庫

1. 前往 **https://github.com**，登入帳號
2. 點右上角 **+** → **New repository**
3. Repository name 填：`my-calculator`
4. 選 **Public**
5. **不要**勾選任何 Initialize 選項
6. 點 **Create repository**

### 步驟二：設定 Vite 的路徑

打開 `vite.config.js`，加上 `base`：

```javascript
import { defineConfig } from 'vite'
import vue from '@vitejs/plugin-vue'

export default defineConfig({
  plugins: [vue()],
  base: '/my-calculator/',   // ← 加這行，和倉庫名稱一樣
})
```

### 步驟三：建立自動部署設定

在專案根目錄建立資料夾結構：`.github/workflows/deploy.yml`

內容貼上：

```yaml
name: 部署計算機到 GitHub Pages

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

### 步驟四：推送到 GitHub

在命令提示字元（確認在 `my-calculator` 資料夾裡）：

```bash
git init
git add .
git commit -m "完成計算機專案"
git branch -M main
git remote add origin https://github.com/你的帳號/my-calculator.git
git push -u origin main
```

> 推送時詢問密碼，請輸入 GitHub 的 **Personal Access Token**（不是帳號密碼）  
> 取得方式：GitHub 右上角 → Settings → Developer settings → Personal access tokens → Generate new token → 勾選 repo → 複製

### 步驟五：開啟 GitHub Pages

1. 進入 GitHub 倉庫頁面
2. 點 **Settings** → 左側 **Pages**
3. **Source** 選 **GitHub Actions** → Save
4. 點上方 **Actions** 頁籤，等綠色勾勾出現
5. 回到 **Settings → Pages**，看到：

```
Your site is live at https://你的帳號.github.io/my-calculator/
```

把網址分享給朋友，他們就能用你做的計算機了！🎉

### 之後更新只需三行

```bash
git add .
git commit -m "更新說明"
git push
```

---

## 回顧：這個專案用到了哪些 Vue 概念

| 概念 | 在計算機裡怎麼用 |
|---|---|
| `ref` | 存放使用者輸入的算式 `expression` |
| `computed` | 根據 `expression` 自動計算結果 `result` |
| `@click="函式(參數)"` | 每個按鍵點擊時呼叫 `pressButton`，傳入對應的字元 |
| `{{ 資料 \|\| 預設值 }}` | 沒輸入時顯示 `'0'` |
| `v-if` | （可擴充）輸入錯誤時顯示提示 |
| CSS Grid | `grid-template-columns: repeat(4, 1fr)` 讓按鍵自動排成 4 欄 |
| `grid-column: span 2` | 讓 `0` 和 `AC` 佔兩格寬 |

---

## 挑戰加分題

完成基本版之後，試試看自己加上這些功能：

**初級**
- 加上退格鍵 ⌫（已在第六階段補充說明）
- 讓計算機在小螢幕（手機）上也好看（CSS `max-width`）

**中級**
- 防止連續輸入兩個運算子（例如 `3++5` 應該阻止第二個 `+`）
- 防止數字開頭多個 `0`（例如 `007` 應該只顯示 `7`）

**進階**
- 加上鍵盤支援（按鍵盤上的數字鍵也能輸入）
  - 提示：用 `window.addEventListener('keydown', fn)` 搭配 `onMounted` 和 `onUnmounted`

---

*完成了嗎？把你的 GitHub Pages 網址貼到作業區！*
