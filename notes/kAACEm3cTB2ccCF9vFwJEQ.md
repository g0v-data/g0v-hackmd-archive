---
title: 【2021 年度獲獎團隊：CourseAPI 開放式課程資訊匯流學院】找開放課程如大海撈針， 國中生發起 API 架構 整合分散的課程資訊
tags: 開放式課程, edu, jothon
---
# 【2021 年度獲獎團隊：CourseAPI 開放式課程資訊匯流學院】找開放課程如大海撈針， 國中生發起 API 架構 整合分散的課程資訊
:::warning
📍 **[回首頁](https://g0v.hackmd.io/@jothon/sch001report)**
📍 **[了解零時小學校 2022 專案孵化競賽](https://sch001.g0v.tw/means/)**
:::
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ba605991664ca5a0263f28a75e76e9e6.png)


:::info
**CourseAPI 開放式課程資訊匯流學院 CourseAPI**

研提開放式課程的資料架構（schema）與資料交換方案、建立一站式開放課程查詢網頁雛形、與國內開放式課程營運單位、使用推廣單位交流。

Create the search engine for students and educators to find open resources.

:::

:::success

* 提案連結：https://sch001.g0v.tw/dash/prj/3Mgj9a0AGC054Y0C6J0y7XfG
* 專案網站：https://toedu.g0v.tw/
* 專案開源：文字和設計物 CC-BY／原始碼 MIT License
    * 開源資料：https://github.com/Open-Edu-Tw
* 團隊成員：呂顥天（@Ted 顥天）、劉哲瑋（@chewei）、朱庭宏（@did1335）、陳敏華（@陳敏華）、黃正龍（@黃正龍）、楊承昊（@tico88612）、許芸瑄（@mo hsu）、楊詠旭（@淺羽 SF）、王雅麗（@Elaine Wang）、潘奕濬（@pan93412）


:::

文／林冠廷

學術機構、學校與民間單位在過去幾年間推出許多開放式課程，幫助民眾輕鬆取得優質的學習資源。這些課程提供線上學習、降低學習門檻的機會，卻因為課程散落各平臺、不易查找，使提供者美意打了折扣。

專案發起人 Ted（呂顥天）回憶起自己在疫情遠距上課期間，想上網自學微積分，結果平臺太多，沒辦法輕鬆找到合適的開放課程。當時燃起一股「為什麼資料會這麼分散」的心情，決定發起開放式課程資訊匯流學院，試圖把各平臺殊異的資料欄位，整合成統一資料交換架構，讓學習者不需費心尋找課程。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_35a44471915d5b1195c39379a2a36f74.png)

 
### 從膽怯到推坑的「沒有人」養成之路
本專案成員年齡組成多元，過半數已畢業，另外一半則為大學、中學生。就讀永和國中的創辦人 Ted 現在 14 歲，是兩年來年紀最小的得獎者，被其他零時小學校參加者譽為技術能力超群的「電神」。他在 7、8 歲就聽過 g0v，不過當時不太清楚社群在做什麼。Ted 笑著回想：「加入前我對 g0v 有很多迷思，還以為他們在推無政府主義」。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_79659ca080903b9cdc9b9e57fc84ccbf.jpg)


直到 2021 年疫情升溫，大家留在家裡上課，Ted 發現了開放式課程平臺的分散問題。經社群夥伴豆腐解開疑慮後，他在 6 月初鼓起勇氣開啟專案共筆，找到劉哲瑋、朱庭宏等夥伴，成為 g0v 的「沒有人」坑主群。眾人積極招兵買馬、參與大松提案，團隊一路成長到 11 人，專長包含專案管理、設計、前端與後端開發。12 月開始負責前端的Amy，就是當時參加大松被 Ted 推坑，成為團隊一員。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_142e7b7e9fd0e8977f1a37176f9a980f.JPG)


### 資料化繁為簡，著重使用者經驗
目前市面上的開放式課程平臺，提供了臺大、政大與輔大等校課程，總數至少有 30 個網站。為了整合各家資料，Ted 與團隊分析每個平臺共通之處，找出六項各家皆有的資訊，作為開放課程資料交換的基本架構：課程名稱、講師、系所、學校、資料來源與網址。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_801604db164ca191e5400efd10b633f6.png)


Ted 說，每個網站系統邏輯不同，代表所有平臺都要獨立開發爬蟲流程，才能確保各來源都呈現相同結果。整理後的資料，團隊會開放機器可讀 API 給民間開發者。專案目前重心則是建立線上一站式查詢系統，讓使用者直接搜尋課程，不需在各個平臺之間迷航。他預告：「最近會著重後端開發，以及調查使用者想法，用量化問卷找到他們想要的功能。」

 
### 社群熱情貢獻，打破年齡歧視迷思
即使自主學習動力極高，但 Ted 卻常常因為年紀而不得其門而入——從學校開辦的進修課程，到網路資訊社群，都曾以年齡不足為由拒絕他參與。到了零時小學校，Ted 從陌生到成為坑主，深刻體會不一樣的氣氛：「實際參與跟加入前感覺完全不同。進入後才知道這裡很有趣、開放，大家都是想要貢獻、有熱忱的人。」Amy 看著 Ted 走過這段路，指出未來g0v社群將有更多國、高中生，建議大家多協助新成員組織想法與上臺提案。


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b29c4f8767f36b20d6fdb8a8ebdf21b6.png)

接下來，團隊成員將投稿社群研討會、進入校園宣傳；Ted 更期待，開放式課程資訊匯流學院有一天可走入國中，幫助他的同儕取得更好的教育資源。


