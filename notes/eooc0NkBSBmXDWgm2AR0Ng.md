---
tags: g0v-summit, 2020
---

# 0609 前端交流

共筆： https://g0v.hackmd.io/@ddio/0609-summit-f2e

## 今天會聊：

1. 怎麼用 pug + tachyons + BEM 做出適合 vue component 的好維護的 html + css
   - [Pug](https://pugjs.org/api/getting-started.html) - HTML preprocessor, no closing tag, shorter class syntax
     - `.agenda` === `<div class="agenda"></div>`
   - [BEM](http://getbem.com/) - naming convention for CSS
     - ex: `agenda__item`, `agenda__item--active`
   - [Tachyon.io](http://tachyons.io/) - css tooltip for customized && responsive UI
     - `.agenda.flex.items-center.justify-between` === 
       ```scss
       .agenda {
         display: flex;
         align-items: center;
         justify-content: center;
       }
       ```
   - 一般用途： Pug + Tachyon
   - 細部調整或客製化元件： BEM
2. 未來待作
   - shared scss using webpack loader
   - 議程試做
   - 測試版、正式版發佈流程、宣傳流程
   - 想要嘗試、改進的地方？

## 本日共筆


自我介紹

在美國的一家新創做前端
專注於用「非資本主義: 一手交錢一手交貨」的方式解決住的問題

平常很少講技術分享，這次做 g0v 的官網的經驗來分享
這次使用 vue、sass、HTML，因為有設計師的，所以 CSS 是自己寫的

也來分享自己習慣用的東西
尤其是在客制化網站的情境

## Pug

### 簡介
- 是一個讓你少寫一點 HTML 的 pre processor(前置處理器)
    
    `.navber` === `<div class="navbar"></div>`

- class寫起來像css選擇器
- 不用寫 close html tag
- 省下找關閉 tag 的時間
- [補充：Pug 的介紹](https://pugjs.org/api/getting-started.html)

---

## BEM
### 簡介
- 一種 CSS 的命名邏輯。
- [命名原則](http://getbem.com/naming/)
- 概念比較是用 component 架構來命名：
    - Block （區塊）: 名詞
    - Element （元素/元件）: 名詞
    - Modifier (狀態): 形容詞
- 優點，寫 CSS 的時候具備 Scope
    可以清楚知道 程式碼的架構

---


## Tachyon.io
### 簡介
- 類似 Boorstrap 的 CSS liberary
- 但是在這一套的概念，並不是提供元件

ex: (上面的例子)
`.agenda.flex.items-center.justify-between` === 
```css
.agenda {
 display: flex;
 align-items: center;
 justify-content: center;
}
```
- 等級制，例如：pv4
```css
.pv4{
    padding-top:2rem;
    padding-bottom:2rem;
}
```
```
/*

  FLEXBOX

  Media Query Extensions:
   -ns = not-small
   -m  = medium
   -l  = large

*/
```
> 14:35 開始 Live Coding 
> 



{%hackmd jfvbUuzyQtOVjnWUOW1peQ %}