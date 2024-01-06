---
tags: hackmd
---

# Hackmd Cheatsheet

這篇文章是 Hackmd 語法的 Cheatsheet，修改自 [Markdown Cheatsheet 中文版](https://gist.github.com/billy3321/1001749662c370887c63bb30f26c9e6e)。

這篇文章旨在作為快速參考與展示。要更多完整的資訊，請見 [John Gruber 原本的規格](http://daringfireball.net/projects/markdown/)與 [Github 偏好的 Markdown（Github-flavored Markdown，簡寫為GFM）資訊頁](http://github.github.com/github-flavored-markdown/)。

如果你正在找 Markdown Here 的小抄（Cheatsheet），[這裡](https://github.com/adam-p/markdown-here/wiki/Markdown-Here-Cheatsheet)也有一篇。你也可以看看更多 Markdown 的工具。

譯註：可以參考這份[中文版文件](http://markdown.tw/)，有更詳盡的 Markdown 語法說明；如果需要可以練習的線上編輯器，可以試試看[HackMD](https://hackmd.io/)。

##### 目錄  

[Headers](#headers)  
[Emphasis](#emphasis)  
[Lists](#lists)  
[Links](#links)  
[Images](#images)  
[Code and Syntax Highlighting](#code)  
[Tables](#tables)  
[Blockquotes](#blockquotes)  
[Inline HTML](#html)  
[Horizontal Rule](#hr)  
[Line Breaks](#lines)  
[Youtube videos](#videos)  

<a name="headers"/>

## 標題

```no-highlight
# H1
## H2
### H3
#### H4
##### H5
###### H6

你也可以使用下劃線的方式標記 H1 與 H2：

Alt-H1
======

Alt-H2
------
```

# H1
## H2
### H3
#### H4
##### H5
###### H6

你也可以使用下劃線的方式標記 H1 與 H2：

Alt-H1
======

Alt-H2
------

<a name="emphasis"/>

## 重點

```no-highlight
重點，又被稱為斜體，在兩邊加上 *星號* 或是 _下劃線_ 。

更強的重點，又稱為粗體，在兩邊加上 **兩個星號** 或是 __兩個下劃線__ 。

也可以用 **星號與 _下劃線_** 結合重點。

刪除線使用兩個波浪符號。 ~~刪除這個。~~
```

重點，又被稱為斜體，在兩邊加上 *星號* 或是 _下劃線_ 。

更強的重點，又稱為粗體，在兩邊加上 **兩個星號** 或是 __兩個下劃線__ 。

也可以用 **星號與 _下劃線_** 結合重點。

刪除線使用兩個波浪符號。 ~~刪除這個。~~


<a name="lists"/>

## 列表

（在這個例子裡，前置與後面的空白以點的方式顯示：⋅）
(In this example, leading and trailing spaces are shown with with dots: ⋅)

```no-highlight
1. 第一個有序列表項目
2. 另一個項目
⋅⋅⋅* 無序子列表 
1. 實際數字不重要，只要它是一個數字
⋅⋅⋅1. 有序子列表
4. 與其他項目

⋅⋅⋅要在列表項目下加入段落，只要縮進就好了。注意前面的空白行，以及前置的空白（至少要一個空白，不過我們在這裡會使用三個空白以剛好對齊原始的文字）。

⋅⋅⋅要使文字段行而不會成為新的段落，你只需要在後面加上兩個空白。⋅⋅
⋅⋅⋅注意這行已經分開了，不過還是在同樣的段落中。
⋅⋅⋅（如果不要求後面的兩個空格，就為伴了典型的 GFM 斷行格式。）

* 無序列表可以使用星號
- 或減號
+ 或加號
```

1. 第一個有序列表項目
2. 另一個項目
   * 無序子列表 
1. 實際數字不重要，只要它是一個數字
   1. 有序子列表
4. 與其他項目

   要在列表項目下加入段落，只要縮進就好了。注意前面的空白行，以及前置的空白（至少要一個空白，不過我們在這裡會使用三個空白以剛好對齊原始的文字）。

   要使文字段行而不會成為新的段落，你只需要在後面加上兩個空白。  
   注意這行已經分開了，不過還是在同樣的段落中。
   （如果不要求後面的兩個空格，就為伴了典型的 GFM 斷行格式。）

* 無序列表可以使用星號
- 或減號
+ 或加號

<a name="links"/>

## 連結

有兩個方法可以建立連結

```no-highlight
[這是一個行內樣式的連結](https://www.google.com)

[這是一個加上標題的行內樣式連結](https://www.google.com "Google 的首頁")

[這是一個引用樣式的連結][任意不區分大小寫的文字]

[以相對的文件路徑引用其他文件](../blob/master/LICENSE)

[可以用數字來宣告一個引用樣式的連結][1]

或讓他空白並使用[連結文字本身]。

網址，或是尖括號中的網址會自動轉換成連結。
http://www.example.com 或 <http://www.example.com> 甚至有時候 example.com 也可以（只是舉例，Github上無效）。

引用連結可以在一些文字後面。

[任意不區分大小寫的文字]: https://www.mozilla.org
[1]: http://slashdot.org
[連結文字本身]: http://www.reddit.com
```

[這是一個行內樣式的連結](https://www.google.com)

[這是一個加上標題的行內樣式連結](https://www.google.com "Google 的首頁")

[這是一個引用樣式的連結][任意不區分大小寫的文字]

[以相對的文件路徑引用其他文件](../blob/master/LICENSE)

[可以用數字來宣告一個引用樣式的連結][1]

或讓他空白並使用[連結文字本身]。

網址，或是尖括號中的網址會自動轉換成連結。
http://www.example.com 或 <http://www.example.com> 甚至有時候 example.com 也可以（只是舉例，Github上無效）。

引用連結可以在一些文字後面。

[任意不區分大小寫的文字]: https://www.mozilla.org
[1]: http://slashdot.org
[連結文字本身]: http://www.reddit.com

<a name="images"/>

## 圖片

```no-highlight
這是我們的 Logo（把游標指向 Logo 可以看到標題文字）

行內樣式：
![alt 文字](https://raw.githubusercontent.com/adam-p/markdown-here/master/src/common/images/icon48.png "Logo 標題文字 1")

引用樣式: 
![alt 文字][logo]

[logo]: https://raw.githubusercontent.com/adam-p/markdown-here/master/src/common/images/icon48.png "Logo 標題文字 2"
```

這是我們的 Logo（把游標指向 Logo 可以看到標題文字）

行內樣式：
![alt 文字](https://raw.githubusercontent.com/adam-p/markdown-here/master/src/common/images/icon48.png "Logo 標題文字 1")

引用樣式: 
![alt 文字][logo]

[logo]: https://raw.githubusercontent.com/adam-p/markdown-here/master/src/common/images/icon48.png "Logo 標題文字 2"

<a name="code"/>

## 程式碼與語法高亮

程式碼區塊是 Markdown 規格的一部分，不過語法高亮不是。無論如何，許多渲染器──如 Github 和 *Markdown Here* ──支援語法高亮。每個渲染器支援的程式語言，以及程式語言的名字寫法都不一樣。*Markdown Here* 支援幾十種語言（以及不一定是真的程式語言，像 diffs 與 HTTP headers）的語法高亮；要看完整的列表，以及語言的名稱，請見 [highlight.js 的示範頁](http://softwaremaniacs.org/media/soft/highlight/test.html)。


```no-highlight
行內的 `程式碼` 用 `反引號` 包圍起來。
Inline `code` has `back-ticks around` it.
```

行內的 `程式碼` 用 `反引號` 包圍起來。

程式碼區塊可以用只有三個反引號<code>```</code>的一行圍起來，或是以四個空格縮排。我建議用三個反引號的方式圍起來 ── 這比較簡單，而且只有這個方式支援語法高亮。

<pre lang="no-highlight"><code>```javascript
var s = "JavaScript 語法高亮";
alert(s);
```
 
```python
s = "Python 語法高亮"
print s
```
 
```
沒有指定程式語言，所以沒有語法高亮。
不過，我們可以放進一個 <b>標籤</b>。
```
</code></pre>



```javascript
var s = "JavaScript 語法高亮";
alert(s);
```

```python
s = "Python 語法高亮"
print s
```

```
沒有指定程式語言，所以 Markdown Here 沒有語法高亮（在Github 上可能不一樣）。
不過，我們可以放進一個 <b>標籤</b>。
```


<a name="tables"/>

## 表格

Markdown 的核心標準沒有表格，不過表格是 GFM 的一部分，而且 *Markdown Here* 支援表格。這是在電子郵件中加入表格的好方法 － 本來是需要從其他應用程式複製貼上的工作。

```no-highlight
冒號可以用來標示欄位的對齊方式。

| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| 第三欄        | 靠右對齊      | $1600 |
| 第二欄        | 置中對齊      |   $12 |
| 斑馬條紋      | 是整齊的      |    $1 |

每個標頭元件都要用至少三個破折號分隔開來。
最外面的豎線可以省略，你也不需要讓原始的文字排列整齊。你也可以使用行內樣式的 Markdown。

不 | 漂亮 | 的文字
--- | --- | ---
*依然* | `渲染的` | **很好**
1 | 2 | 3
```

冒號可以用來標示欄位的對齊方式。

| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| 第三欄        | 靠右對齊      | $1600 |
| 第二欄        | 置中對齊      |   $12 |
| 斑馬條紋      | 是整齊的      |    $1 |

每個標頭元件都要用至少三個破折號分隔開來。
最外面的豎線可以省略，你也不需要讓原始的文字排列整齊。你也可以使用行內樣式的 Markdown。

不 | 漂亮 | 的文字
--- | --- | ---
*依然* | `渲染的` | **很好**
1 | 2 | 3

<a name="blockquotes"/>

## 引用文字

```no-highlight
> 在電子郵件中，引用文字可以很方便的模擬回應的文字。
> 這行也在同樣的引用區塊。

引用區塊結束

> 就算這行很長，只要包裹的好，依然可以很好的被引用。哦，我們繼續寫以保證每個人都確實的被包在裡面。喔，你也可以在引用文字中 *放入* 其他 **Markdown** 語法。
```

> 在電子郵件中，引用文字可以很方便的模擬回應的文字。
> 這行也在同樣的引用區塊。

引用區塊結束

> 就算這行很長，只要包裹的好，依然可以很好的被引用。哦，我們繼續寫以保證每個人都確實的被包在裡面。喔，你也可以在引用文字中 *放入* 其他 **Markdown** 語法。

<a name="html"/>

## 行內 HTML

你也可以在 Markdown 裡面撰寫原始的 HTML，這些 HTML 一樣大多數運作的很好。

```no-highlight
<dl>
  <dt>定義列表</dt>
  <dd>有時候，人們偶爾會用到。</dd>

  <dt>在 HTML 中撰寫 Markdown</dt>
  <dd>*無法* 運作的 **非常** 好。改用 HTML<em>標籤</em>。</dd>
</dl>
```

<dl>
  <dt>定義列表</dt>
  <dd>有時候，人們偶爾會用到。</dd>

  <dt>在 HTML 中撰寫 Markdown</dt>
  <dd>*無法* 運作的 **非常** 好。改用 HTML<em>標籤</em>。</dd>
</dl>

<a name="hr"/>

## 水平線

```
三個或更多個……

---

連字符

***

星號

___

下劃線
```

三個或更多個……

---

連字符

***

星號

___

下劃線

<a name="lines"/>

## 斷行

如果你想要學習斷行如何運作，我基本上建議最好就是實驗看看 ── 按<Enter>一下（也就是，插入一個換行符號），接著再按一次 (也就是，插入兩個換行符號)，看看會發生什麼。你很快就會得到你想要的。「Markdown Toggle」是你的好朋友。

你可以試試看這裡的一些方式：

```
我們從這一行開始。

兩個換行符號分開了這行和前面那一行，所以這會變成 **分開的段落** 。

這行也是個分開的段落，不過……
只有一個換行符號分開這行，所以這是 *同段落* 中的分開兩行。
```

我們從這一行開始。

兩個換行符號分開了這行和前面那一行，所以這會變成 **分開的段落** 。

這行也是個分開的段落，不過……
只有一個換行符號分開這行，所以這是 *同段落* 中的分開兩行。

（技術提示: *Markdown Here* 使用 GFM 的換行，所以不用使用 Markdown 原先的兩個空格換行法。）

<a name="videos"/>

## Youtube 影片

Youtube 影片在 hackmd 可以被直接加入：

```no-highlight
{%youtube xvDZZLylNSk %}
```

{%youtube xvDZZLylNSk %}

---

License: [CC-BY](https://creativecommons.org/licenses/by/3.0/)

翻譯自 [adam-p](https://github.com/adam-p/) 的 [wiki](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)

本文短網址： [bit.ly/mdcheat](https://bit.ly/mdcheat)