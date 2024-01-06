---
title: "如何製作一本epub3電子書"
tags: hackpad
---

# 如何製作一本epub3電子書

> [點此觀看原始內容](https://g0v.hackpad.tw/9zQsGYYU1TG)


這則教學使用「電電轉換器」製作電子書。

如果您手邊沒有原始檔案，可參考使用「黨產解密」一書。

[https://github.com/billy3321/decipher\_kmt\_property](https://github.com/billy3321/decipher_kmt_property)

首先，先將書籍圖片編輯好，內文放置到完整的markdown檔案中。

Markdown檔案的語法可參考此，其中「註釋」和「換頁」與一般markdown比較不一樣，要注意一下。
[http://conv.denshochan.com/tw/markdown](http://conv.denshochan.com/tw/markdown)

Markdown檔案在此：

[https://github.com/billy3321/decipher\_kmt\_property/blob/master/full.md](https://github.com/billy3321/decipher_kmt_property/blob/master/full.md)

電電轉換器設定檔：

[https://github.com/billy3321/decipher\_kmt\_property/blob/master/ddconv.yml](https://github.com/billy3321/decipher_kmt_property/blob/master/ddconv.yml)

接著打開電電轉換器，網址：

[http://conv.denshochan.com/tw/](http://conv.denshochan.com/tw/)

他左上角的「上傳」可以一次選取多個檔案，請一次把所有的檔案都選好：markdown檔案、所有圖片、電電轉換器設定檔、封面（請命名為cover.jpg）。輸入欄位的書本標題隨意，之後會被電電轉換器的設定覆蓋。

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c7207c3c0c2e2fb4be9a5db4f23b35ed)


選好後，請點選「轉換」按鈕，下載一個epub。

接著，請把epub解壓縮。

解壓縮後，進入「OEBPS」資料夾。

首先移除「toc.ncx」檔案。接著，修改「content.opf」檔案

把這幾行

```
<item media-type="application/x-dtbncx+xml" href="toc.ncx" id="_toc.ncx" />
</manifest>
<spine page-progression-direction="ltr" toc="_toc.ncx">

```
修改成這樣：

```
</manifest>
<spine page-progression-direction="ltr">

```
然後把「style.css」修改為以下內容：

```
@charset "UTF-8";
/\ でんでんコンバーター縦書きデフォルト /
@namespace "http://www.w3.org/1999/xhtml";
@namespace epub "http://www.idpf.org/2007/ops";
html {
  -epub-writing-mode: horizontal-tb;
  -webkit-writing-mode: horizontal-tb;
  writing-mode: horizontal-tb;
}

body {
  text-align: justify;
  text-justify: inter-ideograph;
  font-family: source, serif, sans-serif;
  vertical-align: baseline;
  word-wrap: break-word;
}

@font-face {
  font-family: source;
  src: url(shs.otf);
}

h1, h2, h3, h4, h5, h6 {
  font-family: serif, sans-serif;
  font-weight: normal;
  color: inherit;
}

h1 {
  font-size: 2em;
  text-align: center;
  margin-right: 0.625em;
  margin-left: 0.625em;
}

h2 {
  font-size: 1.8em;
  text-align: center;
  margin-right: 0.83333em;
  margin-left: 0.83333em;
}

h3 {
  font-size: 1.5em;
  text-align: center;
  margin-right: 1.11111em;
  margin-left: 1.11111em;
}

h4 {
  font-size: 1.25em;
  margin-right: 1.25em;
  margin-left: 1.25em;
}

h5 {
  font-size: 1.125em;
  margin-right: 1.42857em;
  margin-left: 1.42857em;
}

h6 {
  font-size: 1em;
  margin-right: 1.66667em;
  margin-left: 1.66667em;
}

p {
  margin-right: 1.25em;
  margin-left: 1.25em;
  line-height: 1.8;
  text-indent: 2em;
}

li p {
  text-indent: 0;
}

p, li, dt, dd {
  line-height: 1.8;
}

b, strong, dt, caption, figcaption, th {
  font-family: sans-serif, serif;
}

strong, blockquote {
  font-family: "HelveticaNeue-Medium", "STKaiTi-TC-Regular", "DFKai-SB";
}

blockquote, ul,
fieldset, form,
ol, dl, menu {
  margin-right: 1.25em;
  margin-left: 1.25em;
  padding: 0;
}

blockquote blockquote, blockquote ol, blockquote ul, blockquote dl, ol blockquote, ol ol, ol ul, ol dl, ul blockquote, ul ol, ul ul, ul dl, dl blockquote, dl ol, dl ul, dl dl {
  margin-right: 0em;
  margin-left: 0em;
}

ol, ul, menu, dd {
  margin-top: 2em;
}

ol li ol {
  margin-top: 0em;
  margin-left: 2em;
}

ol li ul {
  margin-top: 0em;
  margin-left: 2em;
}

ul li ol {
  margin-top: 0em;
  margin-left: 2em;
}

ul li ul {
  margin-top: 0em;
  margin-left: 2em;
}

a {
  color: #0538b2;
}
a:hover {
  color: #b2058e;
}
a:active {
  color: #b27f05;
}

pre {
  white-space: pre-wrap;
}

img {
  width: auto;
  height: auto;
  max-width: 100%;
  max-height: 100%;
}

hr {
  margin-right: 1.25em;
  margin-left: 1.25em;
}

table {
  border-collapse: collapse;
  border-spacing: 0;
}

rt {
  font-family: serif, sans-serif;
}

.tcy {
  -epub-text-combine: horizontal;
  -webkit-text-combine: horizontal;
  text-combine-horizontal: all;
}

.sideways {
  -epub-text-orientation: sideways;
}

.upright {
  -epub-text-orientation: rotate-right;
  -epub-text-orientation: upright;
  -webkit-text-orientation: upright;
  -epub-text-combine: horizontal;
  -webkit-text-combine: horizontal;
  text-combine-horizontal: all;
}

.pagenum {
  color: gray;
  font-size: 0.8em;
}

.footnotes hr {
  margin-right: 1.25em;
  margin-left: 1.25em;
}
.footnotes ol {
  margin-top: 2em;
}
.footnotes li {
  font-size: 0.875em;
}

a.noteref {
  font-size: 0.75em;
  vertical-align: super;
}

navtoc, navlandmarks, navloi, navlot, navpage-list {
  margin-left: 2.5em;
}
navtoc ol, navlandmarks ol, navloi ol, navlot ol, navpage-list ol {
  margin-top: 1em;
}

table, tr, td, th{
  border: 1px 666 solid;
}

tr:nth-child(even) {
  background-color: #f2f2f2;
}

.-epub-media-overlay-active {
  background-color: yellow;
}

h2 {
  margin-top: 0.66667em;
}

h3 {
  margin-top: 1.77778em;
}

h4 {
  margin-top: 3em;
  font-family: sans-serif, serif;
}

blockquote {
  margin-top: 1em;
}

p {
  margin: 0;
}

a {
  text-decoration: none;
}

u {
  text-decoration: overline;
}

@media print {
  h1 {
    page-break-before: always;
  }

  h1, h2, h3,
  h4, h5, h6 {
    page-break-after: avoid;
  }

  ul, ol, dl {
    page-break-before: avoid;
  }
}

.pull-right {
  text-align: right;
}

```
要特別注意的是，其中有幾行是中文字型設定


```
body {
  font-family: source, serif, sans-serif;
}

@font-face {
  font-family: source;
  src: url(shs.otf);
}

```
如果要加上字型設定，請把字體放入「OEBPS」資料夾，然後在「content.opf」檔案中的這裡：

```
<manifest>
<item media-type="image/jpeg" href="cover.jpg" id="_cover.jpg" properties="cover-image" />

```
修改為這樣：

```
<manifest>
<item media-type="application/otf" href="shs.otf" id="font" />
<item media-type="text/css" href="template.css" id="_template.css" />

```
這邊字體名稱設定是「shs.otf」，你可以改成自己喜歡的名稱。

而關於書本目錄的設定在「nav.xhtml」檔案，可以把不要的目錄層級設定\`display: hidden\`

修改完成後，把這整個epub重新封裝起來即可。可以用epub檢查程式試試看有沒有問題。

之後，這就是一個可用的epub檔案了！

