---
title: "20140614 前端教學松：ly zorro 教學 / ve 學習筆記"
tags: 零時的學習不能等, hackpad
---

# 20140614 前端教學松：ly zorro 教學 / ve 學習筆記

> [點此觀看原始內容](https://g0v.hackpad.tw/jhSpK4hkyAH)


非正規安裝 zorro 強大 sublime plugin

IE 8~9 之間有很大變動，不是作給老人家看的，往下支援到 IE9 就好

table 流網站演示跟它的問題

[http://codepen.io/](http://codepen.io/) 可以看到很厲害的作品。雖然要大家安裝本機環境，但初期學習可以多利用線上環境


Display: 控制 element 的排版顯示方式
[http://www.w3schools.com/cssref/pr\_class\_display.asp](http://www.w3schools.com/cssref/pr_class_display.asp)
常用的是 block（很像 <div>） / inline（一排，只會對齊底部） / inline block（一排有多個元素對齊上方）
也可以用 float，但沒有高度，需要指定一個有高度的 div 或 element /
[http://www.w3schools.com/html/html_blocks.asp](http://www.w3schools.com/html/html_blocks.asp)

查詢
[https://developer.mozilla.org/en-US/docs/Web/HTML](https://developer.mozilla.org/en-US/docs/Web/HTML)（比較新）
[http://www.w3schools.com/](http://www.w3schools.com/)（比較穩定）

reset CSS
不同瀏覽器實際呈現方式不同，用 reset 可洗掉預設樣式，自己指定要幾 px....


沒有背 element 名稱沒關係，用 chrome inspect element 然後隨打即搜！（好強大！）


## CSS format 疊層樣式表

ly：HTML 雖然是敘述性的，但表達能力其實不太好（木訥）
CSS 每一條都是一個 rule
敘述範本 {color: yellow;}
這樣還不會有用，還要有個選擇器 selector（早期HTML叫 tag，現在叫 element 居多）
body
{color: yellow;}

CSS reference

相容性最好：chrome > firefox > safari > IE，寫完要去 IE 測

## ly 講課 Part

selector
- id 唯一元素
    - [#XXX](https://g0v.hackpad.tw/ep/search/?q=%23XXX&via=jhSpK4hkyAH){...}
- class 群類，可以有很多個。用空格分開，即可套用多個不同 class
    - .XXX{...}

套用位階：後 class > 前 class；specific > general; id > class; class > element name
大魔王別亂用： !important

新手錯誤：取很多 ID

[CSS Diner](http://flukeout.github.io/) (CSS selector互動教學)

不建議用 Dreamweaver / frontpage：因為會產生冗餘程式碼

下堂課再講 CSS 佈局

Chrome Element Inspector - network 看網頁載入速度

建議習順序
- HTML 寫個自介靜態網頁（要放進哪些內容）
- CSS 開始排版
- jQuery 加入動態效果

