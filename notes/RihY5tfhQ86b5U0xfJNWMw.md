---
title: "g0v project hub 資料收集處"
tags: hackpad
---

# g0v project hub 資料收集處

> [點此觀看原始內容](https://g0v.hackpad.tw/l1W5Cw53OyI)


本文件屬於 g0v 基礎建設的一部份，目的是補完 [新 g0v project hub](http://g0v.github.io/project-hub-mockup/) 所需的資料，方便大眾搜尋專案成果，也方便社群夥伴找坑來跳。專案資料寫到這個 hackpad 後，會有小精靈不定期整理到網站上，整理完畢的專案資料會從這個 hackpad 刪除，需要的話可以翻 edit history 找到它。

## 專案資料空白模版

請複製這個空白模版，貼到下方的共筆編輯區，然後開始編輯專案資料（修改粗體螢光部分即可）。文件底下附錄有詳細的填表說明。
```
\ id: "project-id"  _optional_
  name:
 zh: "專案中文名稱"_  required._
 en: "project name in english"  _optional_
  logo: "url for project icon"  _optional_
  intro:
    zh:
   short: "專案中文簡介"  _optional_
    en:
   short: "project intro in english"  _optional_
  category: <[ 開放資料 開放政府 社會參與 新媒體 政策共筆 g0v基礎建設 其他 ]>_  required._
  tag: <[ 關鍵字1 關鍵字2 關鍵字3 ]>  _optional_
  tool: <[ 工具語言框架1 工具語言框架2 工具語言框架3 ]>  _optional_
  license: <[ 授權1 授權2  ]>_  required._
  homepage: "url for project landing page"  _optional_
  achievement:
    [{
   type: "第一項專案成果以什麼形式呈現"_  required._
   phase: "第一項專案成果開發到什麼階段"  _optional_
   url: "第一項專案成果的網址"_  required._
    }]
  workspace:
    [{
   type: "第一項專案工作區的類型"  _optional_
   name: "第一項專案工作區的名稱"  _optional_
   url: "第一項專案工作區的網址"_  required._
    }]
  resource:
    [{
   type: "第一項資料來源的類型"  _optional_
   name: "第一項資料來源的名稱"  _optional_
   url: "第一項資料來源的網址"  _optional_
    }]
  story:
    [{
   title: "第一則專案介紹文或介紹影片的標題"  _optional_
   url: "第一則專案介紹文或介紹影片的網址"  _optional_
    }]
  related: <[ 相關專案1 相關專案2 相關專案3 ]>  _optional_

```
## 專案資料共筆編輯區

如果你正在看 hackpad 靜態頁面，請連到可編輯版本： [g0v project hub 資料收集處](https://g0v.hackpad.tw/l1W5Cw53OyI)




```

\ id: "project-id"  _optional_
  name:
 zh: "零時黑板"_  required._
 en: "hacker's goban"  _optional_
  logo: "!
```
[**http://goban.tw/bower\_components/goban/Goban\_19x19_vide.png**](http://goban.tw/bower_components/goban/Goban_19x19_vide.png)" _optional_
```
  intro:
    zh:
   short: "零時黑板，適合在二分鐘用別人的電腦，跟完全不熟的人，介紹一件新事物的背景知識和相關脈絡"  _optional_
    en:
   short: "hacker's goban is a good tool to intrOduce anything to a stranger within 2min use her computer."  _optional_
  category: <[ 新媒體 g0v基礎建設 ]>_  required._
  tag: <[ 教育, 背景, 知識 ]>  _optional_
  tool: <[ jade,sass,  angularJS, gobanJS ]>  _optional_
  license: <[ CC0  ]>_  required._
  homepage: "**http://goban.tw/**"  _optional_
  achievement:
    [{
   type: "Web"_  required._
   phase: "Beta"  _optional_
   url: "**http://goban.tw/**"_  required._
    }]
  workspace:
    [{
   type: "goban"  _optional_
   name: "goban"  _optional_
   url: "**http://goban.tw/**"_  required._
    }]
  resource:
    [{
   type: "collaborative"  _optional_
   name: "Ethercalc"  _optional_
   url: "https://etherclac.org"  _optional_
    }]
  story:
    [{
   title: "零時黑板:不只是翻轉教室"  _optional_
   url: "**https://docs.google.com/presentation/d/1Usyb\_XjvchBWB5DdNzrRSLkNGX\_2gQQyL1Re-jRLSE0/edit**"  _optional_
    }]
  related: <[ hackfoldr ]>  _optional_


















```
## 附錄：填表欄位說明

```
\ id: "project-id"  _optional，通常取專案上線網址中的關鍵字，或者 hackfoldr id。如果留空，程式會自動以流水號代替_
  name:
 zh: "專案中文名稱"_  required._
 en: "project name in english"_  optional，將來做英文版才會用到，不過如果先填入的話就可以被搜尋_
  logo: "url for project icon"_  optional，用來顯示為專案的縮圖。如果留空，程式會自動以第一個專案成果網址的網頁抓圖代替_
  intro:
    zh:
   short: "專案中文簡介"_  optional，通常專案共筆或 github readme 裡面找到的專案說明文字可以拿來當作專案簡介_
    en:
   short: "project intro in english"_  optional，將來做英文版才會用到，不過如果先填入的話就可以被搜尋_
  category: <[ 開放資料 開放政府 社會參與 新媒體 政策共筆 g0v基礎建設 其他 ]>_  required. 請在這 7 種分類裡面選 1 個填，雖然可以多選，但盡量只選 1 個就好，頂多 2 個，中間以空白隔開。_
  tag: <[ 關鍵字1 關鍵字2 關鍵字3 ]>_  optional，隨意填寫想被搜尋到的關鍵字，中間以空白隔開。_
  tool: <[ 工具語言框架1 工具語言框架2 工具語言框架3 ]>_  optional，解釋想跳坑的人要會使用哪些工具才能接手編輯目前的檔案或程式，如 Illustrator, Photoshop, Sass, Jade, Django, Rails, PHP, Angular JS, React JS... 等，中間以空白隔開。_
  license: <[ CC0 CC-By BSD MIT WTFPL ]>_  required. g0v 專案必須是 OSI (程式) 或 CC (一般著作) 授權，如果專案中有多種授權可一起列出，中間以空白隔開。雖然是必填，但如果不幸遇到沒寫授權的專案，跟坑主確認前也只能先留空 XD _
  homepage: "url for project landing page"_  optional，按下專案縮圖會打開的網址。如果留空，程式會自動以第一個專案成果的網址代替_
  achievement:
    [{
   type: "第一項專案成果以什麼形式呈現"_  required，這個成果要在什麼地方使用（程式）、或屬於什麼性質（非程式）。應用程式類包括：Web, Android / iOS / Firefox OS / WP, Linux / Mac / Windows, Chrome / Firefox / Safari, 底層程式或資料包括：Code, API, Data, 非程式類的包括：Document, Media, Artwork …等。_
   phase: "第一項專案成果開發到什麼階段"_  optional，程式類包括： Wireframe, Mockup, Demo, Prototype, Alpha, Beta, Production。非程式類包括： Research, Draft, Finished, Published…等，如反黑箱服貿插圖。已經過時不再適用的話則是 Memory，如萌典啄木鳥這種有時效性的網站。_
   url: "第一項專案成果的網址"_  required. _
    }
    {
   type: ""  _optional，_如果有多項成果網址，_就接著第二、第三個…寫下去。_
      phase: ""
      url: ""
    }
]
  workspace:
    [{
   type: "第一項專案工作區的類型"_  optional，如果留空，程式會自動抓取網址來判定最常用的幾種工作區，包括 Hackfoldr, Hackpad, Github, Google Drive, Google Groups, Facebook。_
   name: "第一項專案工作區的名稱"_  optional，如果有多個 Github，導致需要特別用命名區分每個工作區是幹嘛的、跟另一個有何不同，則可以填寫這欄，不然就留空。_
   url: "第一項專案工作區的網址"_  required. _
    }
    {
   type: ""  _optional，_如果有多個工作區，_就接著第二、第三個…寫下去。_
      name: ""
      url: ""
    }
]
  resource:
    [{
   type: "第一項資料來源的類型"_  optional，如果有多筆相似的資料來源，需要註明分類以便區隔，可以利用這個欄位，不需要的話則留白。_
   name: "第一項資料來源的名稱"_  這個連結要顯示的名稱。如果這個專案完全沒有資料來源，則此欄位 optional。如果有，則此欄位 required。_
   url: "第一項資料來源的網址"_  網站、程式碼、繪圖檔案……的網址，目的是讓其他人能夠追溯到上游的檔案或資料。如果這個專案完全沒有資料來源，則此欄位 optional。如果有，則此欄位 required。_
    }
    {
   type: ""  _optional，_如果有多個資料來源，_就接著第二、第三個…寫下去。_
      name: ""
      url: ""
    }
]
  story:
    [{
   title: "第一則專案介紹文或介紹影片的標題" _如果這個專案完全沒有介紹文章或介紹影片，則此欄位 optional。如果有，則此欄位 required。_
   url: "第一則專案介紹文或介紹影片的網址" _如果這個專案完全沒有介紹文章或介紹影片，則此欄位 optional。如果有，則此欄位 required。_
    }
    {
   title: ""  _optional，_如果有多則介紹文章或_介紹_影片，_就接著第二、第三個…寫下去。_
      url: ""
    }
]
  related: <[ 相關專案1 相關專案2 相關專案3 ]>  _optional，相關專案的名稱或 id，填進來以後搜尋這些相關專案時也會被列出，另，將來會使用這個欄位做 project jump 功能。有多個相關專案時，中間以空白隔開。_

```
## 問答、建議與討論


### 專案合併與拆分


#### 合併

- hackfoldr 合併到另一個專案變成工作區：在 20141009 這份資料裡，通常我會把成果產出是 hackfoldr 的，合併到另一個對應的專案，且從成果欄位移到工作區欄位。
- chrome / firefox / iOS / Android / Mac / Windows 合併為跨平台：同主題同作者不同平台，目前也是會合併到一個專案內，例如求職小幫手的 chrome 跟 firefox 版都掛在同一個專案底下。

#### 拆分

當填寫 achievement 欄位時，覺得這個專案有多項不同性質的成果需要加註額外說明，導致預設的 type - phase - url 格式不敷使用，那麼就表示該拆分成不同的專案了。例如：動民主 1.0、動民主 0.5、動民主 2.0、動民主 1.337，彼此之間關連鬆散，成果網站也完全不同，如果全部合併在一個叫做「動民主」的專案底下，那成果欄位會顯示成「Web、Web、Web、Web」，完全看不出來哪個連結會是什麼。所以各自設定成獨立的專案，只是利用 tag 跟 related 欄位註明彼此的關連。p.s. 將來會用這個 related 欄位來讓專案以群組方式顯示，變成 g0v 專案關係圖

#### meta 專案

超農域




