---
title: "[PPT] 簡介與預定功能"
tags: Promise Tracker,hackpad
---

> [點此觀看原始內容](https://g0v.hackpad.tw/9l8mrCKIUJM)

> PPT?
> [name=Shelling F]

> ?
> [name=Johnson L]

> Acronym: "P"olitical "P"romise "T"racker 施政簡報的意味
> [name=Shelling F]

> GJ!
> [name=Johnson L]


> Hackfoldr：[http://beta.hackfoldr.org/ppt](http://beta.hackfoldr.org/ppt)
> [name=Johnson L]


## 專案簡介

一個列出特定當選人 or 團隊之公開承諾的網頁，在任期間由公民朋友自發提供新聞連結、更新承諾進度，作為公民評估此執政者 / 團隊之執行力的工具。

以臺北市長為例，這個網頁會列出柯文哲在競選期間的所有政見（附當初的柯P新政影片），上任前會顯示目前的整體完成度是 0%。整體完成度是由個別政見的完成度組成。網頁提供公民 update 政見進度的功能，update 進度的時候，要提供相關新聞連結。

**發起人/拋磚人**：  [Johnson Liang](https://g0v.hackpad.com/ep/profile/z4JarLrJBea)

## 要解決的問題

執政者競選連任時，選民若想評估其執行力，需要做很多功課；但是：
1.  當初的執政者競選時政見已是 3、4 年前的資料，很難 google 得到。
2.  即使找回當初的政見，要憑一己之力整理 3、4 年來的新聞、逐一比對，門檻不低。
3.  新聞媒體或網友整理的資訊，若得知整理者和自己的立場相反，自己也不容易採信；且他人無法更新「新聞」或其他網友的整理的資訊。

我們認為，政治承諾的追蹤，需要一個長期且開放編輯的「共筆」。左邊 Related Work 會提到其他國家的例子。

## 預計解法之目標與功能


### 預定使用者


網站的預定使用者為全體公民，但依照公民們來到這個網站的目的，可以將使用者分成下面的兩種人：

1.  **Audience 一般閱聽人**：關心公共事務的選民，想了解目前的執政者的整體施政情形，隨時上網站來看施政進度。
> 雖然設計是希望大家能持續關注，不過我猜大部分 audience 都只會在選舉前才想找相關資料 XD|||
> [name=Johnson L]

> 我想要問，這邊是否要包含問政？兩者都是廣義政府的一部分，若是要追蹤議員承諾，像是公督盟等團體提出的[議會改革承諾書](http://www.observers.tw/ccw/)，是要開分支或是合併到這邊呢？
> [name=nchild]

> 目前沒有想到要把議會與民代納入耶，受監督的角色想要集中在執行的執政者這樣。
> [name=Johnson L]

> 美國則是有媒體在追蹤[在野黨](http://www.politifact.com/truth-o-meter/promises/gop-pledge-o-meter/)做過的承諾。
> [name=Johnson L]

> 所以對象是柯p 而已？那跟之前的市長承諾差別是？
> [name=nchild]

> 目前對象是地方或中央執政者喲，不過想先做地方執政者這樣。prototype 裡頭左邊的抽屜裡面有預留「[新增施政單位](http://invis.io/9Z1TFRTFT)」的空間。
> [name=Johnson L]

2.  **Editor 編輯**：願意主動更新施政進度的人，應為該執政者的支持者，或是本專案的編輯義工 (?)
> 我覺得執政者的支持者會比較有意願更新，但是會流於太主觀；而編輯義工可能比較缺乏動力去持續地調查更新。我建議採用混和的方法：執政者 and/or 執政支持者提出草稿，在經過本專案的編輯義工編改，確保施政進度的公正客觀再正式發布。
> [name=Meng-Fu S]

> 您的 insight 很棒！我認為如果我們按照[這份 prototype](http://invis.io/9Z1TFRTFT)，將「提供承諾更新的出處」以及「看著出處，設定承諾完成度」兩個 task 分開，那麼應該就不用讓義工審稿了。大家都可以評定完成度，且評定完成度這個步驟為非匿名的（綁 FB 帳號）、評分者需為自己評定的完成度負責，這樣的機制，應該能夠沖淡支持者的偏頗或是亂板者惡意拉低分數造成的影響**，**同時也能給予執政者的支持者足夠的信任（沒有審查情事），鼓勵執政者的支持者多多提供新的消息出處、讓大家一起來評定完成度。
> [name=Johnson L]

> 另一方面，不設立把關的編輯義工，同時也能讓這個網站與其他公民監督的粉絲頁（柯Ｐ進度條、市民監督林智堅⋯⋯等）做出區隔，讓社會上能同時存有多元的監督方式。
> [name=Johnson L]

> Cool~ 我喜歡這個protoype!
> [name=Meng-Fu S]

> 建議各縣市可設一名義務性的區域負責人，負責該縣市的版面管理、不良文章篩除。我可協助桃園部分的。
> [name=Yi W]

```

```
> 我也可以負責台東的部分!!! 
> [name=fang j]

> 感謝大家的熱心 m(_ _)m 未來會有各縣市的政見、白皮書要整理成承諾，有大家一起努力合作了！
> [name=Johnson L]


### 預定目標

- 提供足夠資訊（進度視覺化、資訊鏈結），協助 audience 下價值判斷（當前執政者執行力好壞）
- 降低 editor 編輯更新施政進度的門檻

### 額外功能（Idea Pool！）


#### 鼓勵編輯系列

此專案的本質類似 Wikipedia，主要價值來自於 editor 自發性回報之進度。
有什麼方法可以鼓勵 editor 作出貢獻，或是讓受益者 audience 也能著手開始編輯呢？

- 除 editor 手動新增新聞外，網站也可以主動爬取可能與政策相關的新聞，在適當時機將新聞呈現給 audience，並要求 audience 作出「和承諾無關」「未開始」「進行中」「已完成」的 tagging。
- Gamification 遊戲化：建立操作型制約的 token system（經驗值，等級，頭銜等）


#### 輔助資訊

網站的核心功能是「政治承諾的兌現進度」，在這個核心功能之外的都算是輔助資訊。

- 任期倒數
- 除了和進度有關的新聞之外，也收集執行時的爭議相關新聞（像【[柯Ｐ勞動局長遴選辦法 工運人士批為難勞工](http://www.stormmediagroup.com/opencms/news/detail/cc90b754-788f-11e4-870c-ef2804cba5a1/?uuid=cc90b754-788f-11e4-870c-ef2804cba5a1)】等）\-\- 新聞與資料分成「進度更新」與「執行爭議」兩種
- 政策負責單位／聯絡方式／相關壓力團體連結（誰來更新 outdated info?）
- 讓 editor 能新增當初提的政見之外的「多做的」政見。
- 可以新增行政機關（不只是地方政府，還有中央政府），讓焦點團體可以追蹤任何機關的特定承諾，例如性別相關壓力團體，可以替行政院性平會開新的頁面，追蹤「落實消除對婦女一切形式歧視公約計畫」的實行進度。
- 記名討論，讓大家公開討論個別政見完成度，像 Google Play 的評分（不把評分與人綁一起、單純留言的話，那 FB / Disqus 就好）
- 自動備份資料來源（[http://archive.org/help/json.php](http://archive.org/help/json.php)）

#### 議題型承諾

- ex 柯P
    - [柯文哲對《台北市市民文化宣言》的回應：以文化建立台北的城市價值](https://citizensculturalmenifesto.wordpress.com/%E6%9F%AF%E6%96%87%E5%93%B2%E5%9B%9E%E6%87%89/)
    - [柯文哲簽署《都市農耕四大訴求》by 都市農耕網](http://hackfoldr.org/Taipei-Urban-Agri/Hn3FneI5JL1)
    - 文化資產個案 (南港瓶蓋工廠、...)
    - 《[校園營養午餐非基改](https://www.facebook.com/nogmolunch/photos/a.808649359186566.1073741831.806856912699144/817356101649225/?type=3&theater)...》
- 其他如南部縣市空汙自治條例 ... 航空城 ...


### 使用資料

[2014 臺北市長承諾一覽表](https://docs.google.com/document/d/1ewQ0aKlY4sYU7qSLa8ydVbToJKSVcInTFtfIhHeMjzg/edit)
[觀政見](https://www.visionplatform.tw/)平台
[~選舉黃頁~](http://k.olc.tw/elections/)~（候選人及現任參政者的過往政見有被列出，並且評星數）~（記錯了，應該是，）真度計（但是真度計目前的政見兌現星號是假數據）
> [http://data.cec.gov.tw/](http://data.cec.gov.tw/) 可以找到一些過去的選舉公報檔案
> [name=Finjon K]




