# CSS & Html tag



CSS
---

##### 屬性設定 : 避免屬性重複，先瀏覽過所有figma，找出常用的顏色、字體大小...等，將之設置為變數
eg.
```css
:root {
  --color-text: #878787;
}
.text-color {
  color: #878787;
}
```

##### 避免命名太通用，也許是用組合的方式
```html
<img class="photo buyer__photo" />
```
```css
.photo {
}
.buyer__photo {
}
.seller__photo {
}
.admin__photo {
}
```
##### 避免樣式之間的關係不明確，可嘗試以下命名規則
```html
<div class="sheets">  
	  <h1 class="sheets__title"></h1>  
	  <ul class="list">  
	    <li class="list__item list__item--active"><a href="#"></a></li>  
	    <li class="list__item"><a href="#"></a></li>  
	  </ul>  
</div>
```

其他可使用的技巧
```css
div p {
  margin: 0;
  padding: 1em;
}

div p + p {
  padding-top: 0;
}
div p, #id:first-line {background-color: red; border-radius: 3px;}
div p {margin: 0; padding: 1em;}
div p + p {padding-top: 0;}
```

#### 選擇器
```html
<div>
	<span></span>
	<p>
	<p>
</div>
```
**加號 +**  
選擇「位在同一層跟在後面的第一個元素」(選擇一個跟在後方的兄弟姊妹)
```css
div + p {}
```

**連接號 ~**  
選擇「位在同一層的所有符合指定名字的元素」(選擇所有符合指定名字的兄弟姊妹)
```css
span ~ p{}
```
**大於符號 >**
選擇「位在下一層”**內**”所有符合指定名字的元素」(所有所有符合指定名字的兒子，不會選到孫子輩)
```css
div > p {}
```


#### 「前綴（Prefix）」
- **-webkit-**
  Chrome、Safari; 用於 Chrome、Safari、較新版本的 Opera 、 Edge，以及幾乎所有 iOS 的瀏覽器，包括 Firefox for iOS；基本上，泛指任何基於 WebKit 或 Chromium 的瀏覽器。
- **-moz-**
  Firefox
- **-o-**
  Opera; 指舊的 WebKit 之前的 Opera 版本瀏覽器。
- **-ms-**
  Internet Explorer; 用於 Chromium 之前的 Internet Explorer 和 Microsoft Edge 瀏覽器。

ps. **WebKit**是一個開源的Web瀏覽器引擎(Web browser engine)。它被用於Apple Safari。其分支Blink被用於基於Chromium的網頁瀏覽器，如Microsoft Edge與Google Chrome。

#### 動畫  Animations
- @keyframes
- animation-name
- animation-duration
- animation-delay
- animation-iteration-count
- animation-direction
- animation-timing-function
- animation-fill-mode
- animation
```css
/* The animation code */  
@keyframes example {  
  from {background-color: red;}  
  to {background-color: yellow;}
  
  /*
  0%   {background-color:red; left:0px; top:0px;}  
  25%  {background-color:yellow; left:200px; top:0px;}  
  50%  {background-color:blue; left:200px; top:200px;}  
  75%  {background-color:green; left:0px; top:200px;}  
  100% {background-color:red; left:0px; top:0px;}
  */
}  
  
/* The element to apply the animation to */  
div {  
  width: 100px;  
  height: 100px;  
  background-color: red;  
  animation-name: example;  
  animation-duration: 4s;
}


/* 範例二 - 轉圈lading效果 */
.spinner {
  border: 5px solid rgba(0, 0, 0, 0.1);
  border-top: 5px solid #3498db;
  border-radius: 50%;
  animation: spin 1s linear infinite;
}

@keyframes spin {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}

/* 範例三 - skeleton 載入由左至右漸層效果，類似youtube */
.skeleton-container {
    height: 100%;
    width: 100%;
    background: linear-gradient(-90deg, #e0e0e0 25%, #f0f0f0 50%, #e0e0e0 75%);
    background-size: 400% 400%;
    animation: shimmer 1.2s ease-in-out infinite;
}

@keyframes shimmer {
    0% {
        background-position: 100% 0;
    }
    100% {
        background-position: -100% 0;
    }
}
```

| Property                                                                                            | Description                                                                                                    |
| --------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| [@keyframes](https://www.w3schools.com/cssref/css3_pr_animation-keyframes.asp)                      | Specifies the animation code                                                                                   |
| [animation](https://www.w3schools.com/cssref/css3_pr_animation.asp)                                 | A shorthand property for setting all the animation properties                                                  |
| [animation-delay](https://www.w3schools.com/cssref/css3_pr_animation-delay.asp)                     | Specifies a delay for the start of an animation                                                                |
| [animation-direction](https://www.w3schools.com/cssref/css3_pr_animation-direction.asp)             | Specifies whether an animation should be played forwards, backwards or in alternate cycles                     |
| [animation-duration](https://www.w3schools.com/cssref/css3_pr_animation-duration.asp)               | Specifies how long time an animation should take to complete one cycle                                         |
| [animation-fill-mode](https://www.w3schools.com/cssref/css3_pr_animation-fill-mode.asp)             | Specifies a style for the element when the animation is not playing (before it starts, after it ends, or both) |
| [animation-iteration-count](https://www.w3schools.com/cssref/css3_pr_animation-iteration-count.asp) | Specifies the number of times an animation should be played                                                    |
| [animation-name](https://www.w3schools.com/cssref/css3_pr_animation-name.asp)                       | Specifies the name of the @keyframes animation                                                                 |
| [animation-play-state](https://www.w3schools.com/cssref/css3_pr_animation-play-state.asp)           | Specifies whether the animation is running or paused                                                           |
| [animation-timing-function](https://www.w3schools.com/cssref/css3_pr_animation-timing-function.asp) | Specifies the speed curve of the animation                                                                     |

#### 偽元素
* ::-webkit-scrollbar
* ::-moz-progress-bar
* ::after

#### CSS **虛擬類別**（pseudo-class）的元素
* :active
* :hover
* :last

#### FlexBox
* [Flexbox 是甚麼 - Flex 基礎教學 | W3HexSchool](https://w3c.hexschool.com/flexbox/2186a786
* Flexbox 測試工具: [Flexbox Playground (codepen.io)](https://codepen.io/peiqun/pen/WYzzYX)

### 變數搭配 RWD！ [原生 CSS 變數運用技巧（CSS Variables） - 客座投稿 | W3HexSchool](https://w3c.hexschool.com/blog/21985acb)

相對於 Sass 的變數來說，CSS 的變數是可以再次改變的，且改變的方式也是依據 CSS 「後者覆蓋前者」的特性，以下就使用 “中斷點” 做為條件來使後者的樣式覆蓋前者吧。

製作響應式時，因為螢幕大小的不同通常會需要調整文字大小來符合需求，最常見的方式就是透過選取器一一覆蓋字體大小，如果透過變數的方式就可以統一切換整體文字大小，不需要一一的調整每個選取器。

```css
:root {
  --font-size: 14px;
}

/* 使用變數定義文字大小 */
p {
  font-size: var(--font-size);
}
/* 除此之外，還可以透過 calc 用相同變數做運算，讓特定的文字更大獲更小 */
h1 {
  font-size: calc(var(--font-size) * 1.5);
}
```

接下來只要調整中斷點內的變數，上段的 `p`、`h1` 選取器就會套用新的變數值。

```css
@media (min-width: 480px) {
  :root {
    --font-size: 18px;
  }
}
```

本範例可透過縮放畫面看到不同結果，建議到範例中觀看，範例網址：[https://codepen.io/Wcc723/pen/JjodQVJ](https://codepen.io/Wcc723/pen/JjodQVJ)

### JavaScript 操作 CSS 變數

除了使用覆蓋的方式外，萬能的 JavaScript 也同樣能夠調整 CSS 變數，此方式也就幾乎跳脫所有的限制可自由運用 CSS 變數。

此範例中先預訂了一個變數 `--size`，並且給予值 200px。

```css
:root {
  --size: 200px;
}
```

設定 CSS Variables 與設定一般 CSS 屬性方式是相同的，先選取 `document.documentElement.root` 就能在下方的 style 設定屬性 `{ '--變數名稱', '值' }`。

```js
const root = document.documentElement;
root.style.setProperty('--size', `${this.value}px`)
```




#### 瀏覽器自動填入樣式 browser autofill html input css
[:autofill | CSS-Tricks](https://css-tricks.com/almanac/selectors/a/autofill/)
```css
/** 客製化瀏覽器自動填入 input style */
input:autofill,
input:-webkit-autofill,
input:-webkit-autofill:hover,
input:-webkit-autofill:focus {
   -webkit-text-fill-color: #d4d4d4;
   -webkit-box-shadow: 0 0 0px 40rem #000 inset;
}
```




---
HTML
---


#### HTML Tag
```html

<wbr> 元素代表換行機會，即文本中的位置，瀏覽器可以選擇在該位置斷行，儘管其斷行規則在該位置本身不會創建斷行
<div id="example-paragraphs">
  <p>Fernstraßenbauprivatfinanzierungsgesetz</p>
  <p>Fernstraßen<wbr />bau<wbr />privat<wbr />finanzierungs<wbr />gesetz</p>
  <p>Fernstraßen&shy;bau&shy;privat&shy;finanzierungs&shy;gesetz</p>
</div>


<section> 元素代表文件中的通用獨立區段，它沒有更具體的語義元素來代表它。區段應始終具有標題，幾乎沒有例外。

<section>
  <h2>Introduction</h2>
  <p>This document provides a guide to help with the important task of choosing the correct Apple.</p>
</section>
```

