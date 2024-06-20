# 開發文件：使用 `grid-column-start` 屬性進行 CSS 網格佈局

## 概述
`grid-column-start` 是一個 CSS 屬性，用於指定網格項目在網格列中開始的位置。它通過指定一條線、跨度或自動模式來確定其起始位置。

## 語法
```css
/* 關鍵字值 */
grid-column-start: auto;

/* 自定義標識符值 */
grid-column-start: somegridarea;

/* 數字 + 自定義標識符值 */
grid-column-start: 2;
grid-column-start: somegridarea 4;

/* span 關鍵字 + 數字 + 自定義標識符值 */
grid-column-start: span 3;
grid-column-start: span somegridarea;
grid-column-start: span somegridarea 5;

/* 全局值 */
grid-column-start: inherit;
grid-column-start: initial;
grid-column-start: revert;
grid-column-start: revert-layer;
grid-column-start: unset;
```

## 每個值的意義
1. `auto`：表示屬性不對網格項目的定位貢獻任何內容。
2. `<custom-ident>`：如果存在名為 `<custom-ident>-start` 的命名線，那麼它會將這條線作為網格項目的位置。
3. `<integer> && <custom-ident>?`：指定第 n 條網格線。如果是負整數，則從顯式網格的結尾反向計數。
4. `span && [ <integer> || <custom-ident> ]`：用來貢獻一個網格跨度，使得網格區域的起始邊距離結尾有 n 條線。

## 正式定義
<table>
  <tbody>
    <tr>
      <th scope="row">初始值</th>
      <td><code>auto</code></td>
    </tr>
    <tr>
      <th scope="row">適用於</th>
      <td>網格項目和其包含塊為網格容器的絕對定位框</td>
    </tr>
    <tr>
      <th scope="row">是否繼承</th>
      <td>否</td>
    </tr>
    <tr>
      <th scope="row">計算值</th>
      <td>按照指定的計算</td>
    </tr>
    <tr>
      <th scope="row">動畫類型</th>
      <td>離散型</td>
    </tr>
  </tbody>
</table>

## 示例
### 設置網格項目的列開始位置

#### HTML
```html
<div class="wrapper">
  <div class="box1">One</div>
  <div class="box2">Two</div>
  <div class="box3">Three</div>
  <div class="box4">Four</div>
  <div class="box5">Five</div>
</div>
```

#### CSS
```css
.wrapper {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-auto-rows: 100px;
}

.box1 {
  grid-column-start: 1;
  grid-column-end: 4;
  grid-row-start: 1;
  grid-row-end: 3;
}

.box2 {
  grid-column-start: 1;
  grid-row-start: 3;
  grid-row-end: 5;
}

* {
  box-sizing: border-box;
}

.wrapper {
  border: 2px solid #f76707;
  border-radius: 5px;
  background-color: #fff4e6;
}

.wrapper > div {
  border: 2px solid #ffa94d;
  border-radius: 5px;
  background-color: #ffd8a8;
  padding: 1em;
  color: #d9480f;
}

.nested {
  border: 2px solid #ffec99;
  border-radius: 5px;
  background-color: #fff9db;
  padding: 1em;
}
```

#### 結果
您可以參考 [試試看](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-column-start#try_it) 來查看效果。

## 瀏覽器兼容性
請前往 [瀏覽器兼容性表](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-column-start#browser_compatibility) 獲取更多信息。

## 參見
更多相關信息請參閱 [CSS Grid 布局模塊](https://drafts.csswg.org/css-grid/#line-placement)。

希望以上的步驟和説明能幫助您更好地理解並使用 `grid-column-start` 屬性來進行網格布局操作。