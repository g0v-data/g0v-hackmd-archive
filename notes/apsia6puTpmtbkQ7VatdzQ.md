---
title: "Debater | 辯論家"
tags: hackpad
---

# Debater | 辯論家

> [點此觀看原始內容](https://g0v.hackpad.tw/vjeJIZ8onSY)


## 2016/06 ~ 2016/08/21 COSCUP 演講準備區


### COSCUP 演講資訊


#### 時間

Day 2 下午 [http://coscup.org/2016/schedules.html](http://coscup.org/2016/schedules.html)
#### 投稿標題

Debater 辯論家：網路筆戰大亂鬥
#### 投稿內容

Debater 是一個架設在 Github Pages 上、純前端的網路服務，將散落各處的筆戰內容集中彙整，變成容易瀏覽的網頁。原始概念源自 g0v 動民主專案中的草根論壇紀錄頁面。這場短講將和大家分享 Debater 的設計方式、開發工具與流程，以及時代力量農損事件、FlyingV 事件、Wikimedia 解雇事件... 等應用案例。專案共筆： [Debater ](https://g0v.hackpad.tw/vjeJIZ8onSY)

### 演講內容


#### 整體方向

其實沒有一定要很技術面
講個故事也很棒
從頭到尾吧
發想到做出來
然後有什麼影響
#### 點

原本以為是個消費者導向的產品，人人可以編輯，結果發現跟維基百科一樣，會去編輯的人非常少
將來開發的產品，凡是牽涉到 user input ，都要考慮這樣的生態
就算是polis
參與提問的人還是少
對比 hackmd: 私有 大於 部分共用 大於 完全公開

### 梗收集


小編瓶頸
[https://twitter.com/momo\_zaza\_/status/753527344325767168](https://twitter.com/momo_zaza_/status/753527344325767168)


產品開發雙菱形
- [https://medium.com/@Jeremy_hsu/%E7%BF%BB%E8%AD%AF-%E5%A6%82%E4%BD%95%E6%87%89%E7%94%A8%E4%BA%BA%E6%9C%AC%E8%A8%AD%E8%A8%88-hcd-%E4%BD%BF%E7%94%A8%E8%80%85%E7%B6%93%E9%A9%97-ux-%E4%BB%A5%E5%8F%8A%E5%85%B6%E4%BB%96%E7%9A%84%E5%89%B5%E6%84%8F%E9%96%8B%E7%99%BC%E6%B5%81%E7%A8%8B%E5%BE%9E%E9%9B%B6%E5%88%B0%E4%B8%80-b8262cd70748#.sinhihe9j](https://medium.com/@Jeremy_hsu/%E7%BF%BB%E8%AD%AF-%E5%A6%82%E4%BD%95%E6%87%89%E7%94%A8%E4%BA%BA%E6%9C%AC%E8%A8%AD%E8%A8%88-hcd-%E4%BD%BF%E7%94%A8%E8%80%85%E7%B6%93%E9%A9%97-ux-%E4%BB%A5%E5%8F%8A%E5%85%B6%E4%BB%96%E7%9A%84%E5%89%B5%E6%84%8F%E9%96%8B%E7%99%BC%E6%B5%81%E7%A8%8B%E5%BE%9E%E9%9B%B6%E5%88%B0%E4%B8%80-b8262cd70748#.sinhihe9j)
- [http://myweb.fcu.edu.tw/~mhsung/Creativity/1_999/4D.htm](http://myweb.fcu.edu.tw/~mhsung/Creativity/1_999/4D.htm)

### 原型草稿區




### 20160806 學者回饋

情況：有人在臉書，有些人去別的地方吵，吵架方式會依平台而改變，依發言環境而改變，做下一步分析時要怎麼分析？如果不予回應之類，就整理不出東西。現在是 quote 有講出東西來的人。
平台可否==區分發言環境，context（多一層 menu，可以濾掉某個來源，md 檔可以有參數）==



## 2016/06/18 g0v hackath19n 提案區


### 範例一

[http://etblue.github.io/debater/?source=https://hackmd.io/GwQwxgjAJgrAZgTgLQQQFgEZLSADAJiQTByRgGY1hVQ1yQMg/download](http://etblue.github.io/debater/?source=https://hackmd.io/GwQwxgjAJgrAZgTgLQQQFgEZLSADAJiQTByRgGY1hVQ1yQMg/download)
感謝 hackmd 佛心開 api 給 gh-pages 養米蟲

### 範例二

[http://etblue.github.io/debater/?source=http://etblue.github.io/debater/file/npp-agricultural.md](http://etblue.github.io/debater/?source=http://etblue.github.io/debater/file/npp-agricultural.md)
感謝時代力量粉絲頁分享，雖然分享了以後也沒人看

### 範例三

[http://etblue.github.io/debater/?source=https://hackmd.io/CwUwJgZiDMAcsFowAYQEYHAJy2QgRsslgtMMVuQMZUBs+EQA/download](http://etblue.github.io/debater/?source=https://hackmd.io/CwUwJgZiDMAcsFowAYQEYHAJy2QgRsslgtMMVuQMZUBs+EQA/download)
感謝舜玲建議加上了 summary 功能

### 問題一

剪貼資料很苦力

### 問題二

著作權上不知道是否可以主張合理使用

### 問題三

許願人多，編輯人少（因為太苦力）

### 問題一的現況

目前的編輯小幫手，by tonyq，書於公館人行道旁

[https://gist.github.com/tony1223/478418a202e29fc16e17](https://gist.github.com/tony1223/478418a202e29fc16e17)

目前編輯小幫手的使用方式...
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_781c7444175987ab018cf394e7d124bd)

### 提案內容一

希望把透抽的編輯小幫手變成瀏覽器外掛，可以不用開 console 剪貼 XD

### 提案內容二

希望法律專家提供著作權上的意見

### 提案內容三

有沒有人要整理最近輔大心理的筆戰內容順便當編輯流程白老鼠？詳 [https://www.facebook.com/groups/597161320435546/](https://www.facebook.com/groups/597161320435546/)


以上有興趣請洽 ETBlue


人和：
有多角色、不確定資料來源，導致討論複雜。驚訝的點：有學生整理了完整的資料。
某種說法：社會學的跑去輔大佔據心理系，搞團體動力學，檢討會的形式就是團體動力的做法。
媒體的時效性 vs 求證
希望讓進來的人知道每件事情都不是單向的，可以知道事實，但是是誰講的事實？
時間軸、觀點
有小編的引言，我篩選的標準是什麼、感興趣的面向
發展多元性，而不是硬要客觀



## 暫時置頂分隔線


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9479f9ff8c396f0cf3a6a8c268a828b9)

## 專案資料


### 緣起

科技始終來自於八卦

### 目的

協助議題研究者收集分類彙整來自各地的網路吵架意見，形成初步的議題輪廓，以利後續的研究討論

### 授權

源碼：MIT
編輯：CC0

### 前身

動憲法

### 坑主

ETBlue
玄學

## 產品簡介


Debater is designed for data compulsive folks and hard working online facilitators, turning formatted discussion records into organised filterable web view. Designed by ETBlue. Source code available on [GitHub](https://github.com/ETBlue/debater). Documents on [Hackpad](https://g0v.hackpad.com/Debater--vjeJIZ8onSY). Community on [Facebook](https://www.facebook.com/groups/597161320435546/).

COSCUP 2016 投稿版
Debater 是一個架設在 Github Pages 上、純前端的網路服務，將散落各處的筆戰內容集中彙整，變成容易瀏覽的網頁。原始概念源自 g0v 動民主專案中的草根論壇紀錄頁面。這場短講將和大家分享 Debater 的設計方式、開發工具與流程，以及時代力量農損事件、FlyingV 事件、Wikimedia 解雇事件... 等應用案例。專案共筆： [Debater ](https://g0v.hackpad.com/vjeJIZ8onSY)


## 產品主要特色


### Filter


### 自由的資料來源

- 可彙整來自任何網路平台的發言，使用者可從每則發言的時間戳記可以追溯到原始發言網址，以便求證
- 可使用任何公開的文字編輯器製作資料檔，如 hackmd、gist、pastebin... 等，將資料檔網址匯入 Debater 即可瀏覽（推薦使用 hackmd 線上協作，編輯當下可即時更新，不需重新發佈資料檔。）
- 也可直接從本機匯入資料檔，此種方式不需將資料檔上傳到任何網路平台，不擔心資料外流

### 易於散播的議題網址

- 凡是來自公開網址的資料檔，皆擁有一個獨立的議題網址，可以直接分享給其他人
- 凡是同一台電腦同一個瀏覽器開過的議題網址，都會出現在 Recent 選單，方便使用者回來瀏覽新版資料

### 通用的編輯格式

- 資料檔使用 markdown 語法撰寫，不限軟體、不限作業系統，任何文字編輯器皆可直接編輯
- 只會抓取符合 markdown 語法的內容，其他會自動略過，因此資料檔中可使用任何不屬 markdown 語法的字元當作編輯註解，方便編輯團隊內部溝通

### 彈性的適用情境

- 特定對象參與的深入討論，編輯者可完整輸入發言人的背景資料，讓讀者更能掌握發言脈絡
- 不特定對象參與的廣泛討論，小編可省略發言人資料，單純依主題下標籤，發言人選單會自動隱藏
- 無法第一時間規劃好議題結構時，小編可省略主題結構樹，先就單則發言下標籤，無結構樹的頁面仍可正常顯示

### 不需連線也可使用

- [ ] 將 html 頁面下載到電腦後，可直接當成桌面程式，不需連上網路也可使用（開發中）
> 這是 Debater 不沿用 HackFoldr 的 404 作法而改採 query 的主因
> [name=ET B]



## 開發手札


### 各階段 Screenshots

[https://www.facebook.com/ETBlue/media_set?set=a.10206268572605935.1073741846.1014354995](https://www.facebook.com/ETBlue/media_set?set=a.10206268572605935.1073741846.1014354995)

### Tasks

- [x] ETBlue 受孤獨的 GH 啟發
- [x] 抄 Mr Bigmouth 的 code 建立以 es6 撰寫的 MVC 架構
- [x] 卡關在奇怪的地方問 tka 白癡問題，結果發現是 return deferred 物件的時間點弄錯了
- [x] 參考 godfat 跟 isabel 跟 ipa 的意見改善 UI
- [x] tka 完成單一議題網址分享
- [x] hackmd (jacky) 熱情提供編輯後台
- [x] LY 設定 livereload & 消除頁面閃爍 & 加入爭點黏人功能（且因此錯過 summit 議程組會議 XD）
- [x] 透抽製作小編專用瀏覽器外掛
- [x] 主題展開收合與階層標示功能
- [x] jacky 補上 RWD


## 目前成果


### demo

facebook groups docs [Debater 議題 & 編輯範例列表](https://www.facebook.com/notes/%E5%AD%A4%E7%8D%A8%E7%9A%84%E7%B7%A8%E8%BC%AF%E5%AE%B6-debater-%E5%B0%8F%E7%B7%A8-%E9%96%8B%E7%99%BC%E8%80%85%E7%A4%BE%E5%9C%98/debater-%E8%AD%B0%E9%A1%8C-%E7%B7%A8%E8%BC%AF%E7%AF%84%E4%BE%8B%E5%88%97%E8%A1%A8/597194360432242)
-

### 程式碼

- 網站（純前端） [https://github.com/ETBlue/debater](https://github.com/ETBlue/debater)
- 瀏覽器外掛（貼在 console 內使用） [https://gist.github.com/tony1223/478418a202e29fc16e17](https://gist.github.com/tony1223/478418a202e29fc16e17)
- 完整版的瀏覽器外掛 [https://github.com/MrOrz/debater-extension](https://github.com/MrOrz/debater-extension)

### 社團

- facebook groups [孤獨的編輯家—— Debater 小編 & 開發者社團](https://www.facebook.com/groups/597161320435546/)


## 使用說明


### 瀏覽議題

1.  點入 [http://etblue.github.io/debater/](http://etblue.github.io/debater/)
2.  匯入想呈現的資料，有三種匯入方式：
    1.  網路檔案：將文字檔 URL 複製貼上右上角檔案空格內，然後按 Enter （例： [http://etblue.github.io/debater/file/npp-agricultural.md](http://etblue.github.io/debater/file/npp-agricultural.md)）
    2.  曾瀏覽過的網路檔案：從 Recent 選單選取最近瀏覽過的網路檔案
    3.  電腦本機檔案：切換到 Local 後按 Choose file 從本機電腦硬碟中選擇檔案
3.  點左方標籤可看依主題分類瀏覽，點上方標籤可依發言人身份瀏覽

### 建立新議題

1.  點入 [https://hackmd.io](https://hackmd.io)
2.


### 編輯議題





### 編輯格式

```
// comments (will be ignored by Debater) (optional)
==\ author name==
\ profiles (optional, no use currently)
\- http://... (optional)
\ relations (optional, will show up in secondary navbar if presence)
\- relation 1 (optional)
\ backgrounds (optional, will show up in secondary navbar if presence)
\- background 1 (optional)
==\ articles==
==\ 2016/01/01 GMT0+8:00 http://...==
==\- content  tag==
_ (divider between main content and the tag tree settings. all data below are optional)
``` (block start, html supported)
<p>summary for all topics... blah blah</p>
<p>second paragraph</p>
``` (block end)
\- level 1 tag
  ``` (block start, html supported)
  summary for the tag above... blah blah
  ``` (block end)
  \- level 2 tag
    ``` (block start, html supported)
    summary for the tag above... blah blah
    ``` (block end)
    \- level 3 tag
      ``` (block start, html supported)
      summary for the tag above... blah blah
      ``` (block end)


```
## 工作流程與配套


### Step 1. 組織議題研究團隊

理想中，每個議題的 Debater 編輯團隊建議由以下成員組成：
- 對議題專業領域有基本知識的人 x 1
- 擅長大量閱讀快速歸納且熟悉電腦操作與文書處理的人 x 1
- 瞭解組織經營策略且可規劃會議流程的人 x 1 （optional，組織主導的專案才需要）

### Step 2. 建立議題架構

舉行編輯會議，確定議題方向與適合的下標籤原則，需要考量的事項：
- 下 tag 原則：盡量讓同一個 tag 底下可以呈現不同立場的人對同一件事情的歧見，以爭議點為核心下 tag，讓每個 tag 形成一個吵架串

### Step 3. 爭點歸類與收集標籤


### Step 4. 重構議題


### Step 5. 細部微調與完稿





### Step 6. 設計爭點故事線





### Step 7. 發佈公審問卷





### Step 8. 匯出公審統計與制訂後續策略






