---
title: "政治承諾追蹤網 Political Promise Tracker (~2015/4/18 留存)"
tags: Promise Tracker,hackpad
---

# 政治承諾追蹤網 Political Promise Tracker (~2015/4/18 留存)

> [點此觀看原始內容](https://g0v.hackpad.tw/4a31UkdBItq)

##


↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓
### 本 hackpad 已關閉編輯，敬請移駕 Hackfoldr

### [http://beta.hackfoldr.org/](http://beta.hackfoldr.org/)  ppt

↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑
##



- Github: [https://github.com/g0v/ppt](https://github.com/g0v/ppt)
> 此 pad 由原 g0v unconference 2014 之提案 [<progress>市長承諾</progress>](https://g0v.hackpad.tw/progressprogress-g0v-unconference-2014-6oAR9BlZDoH) 整理而來，接續其討論。
> [name=Johnson L]

> PPT?
> [name=Shelling F]

> ?
> [name=Johnson L]

> Acronym: "P"olitical "P"romise "T"racker 施政簡報的意味
> [name=Shelling F]

> GJ!
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

我們認為，政治承諾的追蹤，需要一個長期且開放編輯的「共筆」。下面 Related Work 章節會提到其他國家的例子。

## Related Work


### 動民主 \- 真度計 / 長鼻尺

> 嗯，基本上就是同一個專案（紺） 嗚嗚現在才看到
> [name=Johnson L]

> 以名字來說 UI 好像滿多可以調整，之前 tisa 的 progress bar 還不錯看
> [name=Shelling F]

- [Hackpad](https://g0v.hackpad.tw/--lzGKZQAwe7e) / [討論](https://g0v.hackpad.tw/--lzGKZQAwe7e) / [Prototype](http://johnlin.tw/nose-meter/candidate.html#朱立倫)
- Prototype 階段
> 是個 Python 專案，不是 Flux/React 喔
> [name=Shelling F]


### 對智利總統的 Promise Tracker


[http://deldichoalhecho.cl/](http://deldichoalhecho.cl/) by lfalvarez @ Chile
- 開發與維護：[Ciudadano Inteligente 基金會](http://ciudadanointeligente.org/)
- 資料來源與更新：不開放眾人編輯，網頁背後是 view only 的 [google spreadsheet](https://docs.google.com/spreadsheets/d/1XN3GxGzK0YRLvcTf9I0dSI1cPsYShu4MHw0EvZqfhm8/edit#gid=196760107)。
- 追蹤對象：僅有總統
- 使用者互動：僅有一個留言板，最後提供 email 讓人聯繫
- 個別政見與整體執行率計算百分比，以 progress bar 呈現
- Source code: [https://github.com/ciudadanointeligente/check-it](https://github.com/ciudadanointeligente/check-it) (django app,)

智利的這個專案相當成熟，他們的公開報告（[西班牙原文](https://docs.google.com/document/d/1nQuNV0y0eyZRRStK-B744OHkM12ixrof7EZWiOOXAkY/edit) / [Google 翻譯成英文](https://docs.google.com/document/d/1-w6h4p3FQzCtDwK239UdhJ71FctvrW1MRfssllgYud4/edit) \[建議閱讀此版\] / [Google 翻譯成中文](https://docs.google.com/document/d/1Yf9RHNeYZiRZ069VymUIwYX1S-FdbeuJoiRqdHKSftk/edit) \[x_x\]）將這個專案交代得非常完整。

他們計算完成度的公式是： (C\*0.5 + V\*0.5) * 100
其中 C 是 consistency variable，V 是 verification variable
> 求助 QQ 我看不懂 3.1 Consistency 與 3.2 Verification 的意思是什麼 QQ
> [name=Johnson L]

> 3.1ㄧ致性：政見與履行政策手段的ㄧ致性  如果ㄧ個工作可以達成政見就評分為1, 如果只能達成其中ㄧ部份就0.5, 如果政見只有在方法裡看到ㄧ點邊就給0.1, 如果不能驗證的就不給分。每個政見會有一個評分方法，給分方式經討論修正。
> [name=May K]

> 我發現他們的分數算法，好像無法處理「政見跳票」這回事，例如說當我們看了[這則新聞](https://tw.news.yahoo.com/%E8%AA%AA%E5%88%B0%E5%81%9A%E4%B8%8D%E5%88%B0-%E8%83%A1%E8%87%AA%E8%A1%8C%E8%BB%8A%E9%81%93%E6%94%BF%E8%A6%8B%E8%B7%B3%E7%A5%A8-202900033.html)，好像沒辦法幫胡市長打這個一致性分數 XD"
> [name=Johnson L]

> 應該可以喔, 大台中交通一六八」計畫是政策, 完成這個政策的方法, 建構五百公里通勤型及休閒型自行車道, 光這兩個就夠嗎? 那就要回頭去看這個計畫的實質內涵是什麼, 只要腳踏車就夠嗎? 有包含公車, 捷運, 機車等等嗎? 如果只有一個面向, 而這個面向是有完成部分政策, 那應該就是0.5分吧, 所以才會說, 評分標準也是需要修正的
> [name=May K]


> 3.2 可驗證：政見能否有標準可勾稽，如果檢查的欄位完整就給1分，不完整0.5,沒有檢查給0分。(這邊的標準就是3.1所說的評分方法)
> [name=May K]

> 「可以勾稽」這裡，好像是看是否有證明文件 (supporting document) 這樣嗎？ 如果未釋出政見實現的證明就 0 分；若有釋出文件但文件僅能證成部分的政見實現，就是 0.5 分；若釋出的文件們可以完整驗證此政見已經完全兌現，就是1分。
> [name=Johnson L]

> 你是對的, 可驗證是以提交出來文件是否可以證明實現政策的方法是否有完成, 3.2有提到, 但看到政策文件是不可能的, 所以只能從宣傳或新聞中來驗證
> [name=May K]

> 文件([這則新聞](https://tw.news.yahoo.com/%E8%AA%AA%E5%88%B0%E5%81%9A%E4%B8%8D%E5%88%B0-%E8%83%A1%E8%87%AA%E8%A1%8C%E8%BB%8A%E9%81%93%E6%94%BF%E8%A6%8B%E8%B7%B3%E7%A5%A8-202900033.html))-->施行方法(建構五百公里通勤型及休閒型自行車道)-->政策(「大台中交通一六八」計畫 )
> [name=May K]

> 只有一致性跟可驗證是不是不太夠啊，為了讓這分數衝高，我都挑簡單的政策來實行就好啦。我在想要不要加個重要性或是影響性之類的評估。
> [name=Wei-Zhi L]

> 所以每個政策應該要有權重之分嗎？
> [name=Johnson L]

> 我自己是覺得還好耶，有達成就是有達成，而且我相信不會有執政者會為了衝高在我們網站的數字， 而專門提出簡單的政見或只挑簡單的做。尤其平台會列出他在各項政見的個別完成度，是衝數字還是真的在做事，大家應該看得出來。
> [name=Johnson L]



### 歐巴馬 ＆ 共和黨 Promise Tracker


[http://www.politifact.com/truth-o-meter/promises/obameter/](http://www.politifact.com/truth-o-meter/promises/obameter/)
- 資料來源與更新：不開放眾人編輯，由媒體 Tampa Bay Times 更新
- 追蹤對象：[歐巴馬](http://www.politifact.com/truth-o-meter/promises/obameter/)，[共和黨](http://www.politifact.com/truth-o-meter/promises/gop-pledge-o-meter/)
- 使用者互動：無
- 分成 Not Yet Rated / In the Works / Stalled / Promise Kept / Compromise / Promise Broken.

### 澳洲 The Abbott Government


[http://www.abc.net.au/news/factcheck/promisetracker/](http://www.abc.net.au/news/factcheck/promisetracker/)
- 資料來源與更新：由媒體 ABC 更新
- 追蹤對象：Tony Abbott
- 分成 Broken, stalled, in-progress, delivered
- 呈現上以時間進行為主要經緯，用線把單一承諾的進度連起來。


### Facebook 監督型粉絲頁


[柯p新政進度條](https://www.facebook.com/kpmeter)  [http://www.facebook.com/kpmeter](http://www.facebook.com/kpmeter)
市民監督林智堅 [https://www.facebook.com/HsinChuMayorSupervision](https://www.facebook.com/HsinChuMayorSupervision)
林佳龍施政進度條 [http://on.fb.me/1rWbjdW](http://on.fb.me/1rWbjdW)
新北市施政監督專區 [https://www.facebook.com/NewTaipeiCitySupervise](https://www.facebook.com/NewTaipeiCitySupervise)

- 資料來源與更新：粉專管理人。柯Ｐ進度條的管理人，似乎是做民調的 NGO 開的專頁？
> 「[利益揭露：本粉絲頁接受政府與人民團體委託進行民意調查](https://www.facebook.com/kpmeter/info)」
> [name=柔慕 余]

> sorry，不小心消除連結，已補上。
> [name=柔慕 余]

- 追蹤對象：柯文哲、林智堅、林佳龍、朱立倫。
- 使用者互動：Facebook page 上留言討論、私訊管理人
- 管理人負責匯整項目。柯Ｐ進度條管理人還有訂定重要突破點
- 柯Ｐ進度條除了一般的進度條外，「數量」相關政見也有視覺化（如 1400 名社區輔警），非「數量」相關者則加入民調數字（如文化咨議委員會的支持度）。
- 可以用 "市政監督聯盟" 當作關鍵字去找，還蠻多相關群組的，只是這些群組政治鬥爭性質比較高，所以不見得需要參考 XD, ex. [https://www.facebook.com/groups/tainangogo/](https://www.facebook.com/groups/tainangogo/)

### [政誌](http://fact.g0v.tw/)


### [成為市政府的影子，如影隨行地監督](https://g0v.hackpad.tw/39pf0Milpkz)


### [大台中市政監督網](https://www.facebook.com/taichungcivicwatch)


### [各地類似組織](http://www.coolloud.org.tw/node/80571)

> via  \_slack\_bot1 on IRC
> [name=nchild]


蘋果日報 [柯文哲百日監督條](http://www.appledaily.com.tw/realtimenews/article/new/20150212/559084/)

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
[觀政見](https://www.visionplatform.tw)平台
[~選舉黃頁~](http://k.olc.tw/elections/)~（候選人及現任參政者的過往政見有被列出，並且評星數）~（記錯了，應該是，）真度計（但是真度計目前的政見兌現星號是假數據）
> 我上面有列，目前打算和他們合併，畢竟完全是同一個專案 xd
> [name=Johnson L]


## System Design


系統的核心是「**針對單一執政者，呈現其承諾的實行進度**」，所以希望能先 focus 在討論這個部分的使用者體驗。究竟要呈現哪些執政者，是否要通通整合在一個網站，可以之後再說。

目標：使 editor 能易於更新新聞、使 audience 能快速判斷施政能力。

```
                    ↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓
```
Clickable Prototype 網址:  [**http://invis.io/9Z1TFRTFT**](http://invis.io/9Z1TFRTFT)
```
                    ↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑


```
> 這個專案是 RWD 的「網頁」，只是先做 mobile 版的 prototype 比較能專注在呈現核心功能。
> [name=Johnson L]

> Sketch source file: [https://dl.dropboxusercontent.com/u/3813488/promise.sketch.20141206.zip](https://dl.dropboxusercontent.com/u/3813488/promise.sketch.20141206.zip)
> [name=Johnson L]

> Sketch 版本: 3.2。CC-BY-NC-SA 4.0 授權。開啓 sketch 檔前請自行下載 Adobe 思源黑體。
> [name=Johnson L]

> 請問Sketch是什麼軟件?官網在那?
> [name=Ting L]

> 是這一款唷 [http://bohemiancoding.com/sketch/](http://bohemiancoding.com/sketch/)
> [name=Johnson L]

> 另外有需要的話，我可以輸出成 pdf 或 eps 檔
> [name=Johnson L]

#### 使用情境

**Editor**：在看到了某則新聞之後，覺得這篇新聞好像可以來更新進度，所以就複製了網址，一進站之後就按右上角的「+」，在「出處」貼上新聞網址，選好這是誰的哪一個承諾之後，就可以來為這個承諾評達成率。

**Audience**：進站之後，可以直接從左邊的 menu 裏面選擇要看的執政者的目前進度。首頁則有全站的最新更新。

#### Design choice

- 3 個大流程：1. 看承諾、2. 新增出處網址、3. 評比完成度。3 個流程彼此獨立，沒有說一定要誰先誰後。
- 達成率的評斷方式還可以再討論，prototype 裡面的「還沒做」「還在做」「已完成」是之前 unconference 討論的一個評分方式。
- 「使用者登入」這個步驟，被往後延遲到使用者的評分存進網站之前。這裡設計成「新增出處網址不用登入，但評比完成度與留言卻需要登入」的原因是，我認為「評比完成度」的門檻太低，需要記名發言與評完成度；然而，新增出處網址的門檻比較高，為了鼓勵大家提供出處，因此省去登入流程。
> 這個設計是參考 [CHI2007 的一篇研究 Wikipedia 衝突調解的 Paper](http://www-users.cs.umn.edu/~echi/papers/2007-CHI/2007-Wikipedia-coordination-PARC-CHI2007.pdf)。該研究將兩個作者在一個 wiki entry 裡不斷 revert 彼此變更的狀況定義為「衝突」。作者發現，Wikipedia 上面的文章，匿名編輯者越多，越不會有衝突；但如果有越多人匿名討論（在討論頁面），那麼文章的衝突就會越多。
> [name=Johnson L]

> 套用到 promise tracker 裡，「提供承諾更新的出處網址」的人就像是編輯 wiki 文章的人，但「幫承諾評進度」的人比較像是討論者。後者或許比較需要記名來減少 valdalism。
> [name=Johnson L]


#### Challenges 會遭遇的挑戰 --- 歡迎大家補充意見！

1.  「評比完成度」界面（「進度大家評」）會顯示當初提供出處的人所填寫的資訊摘要，audience 不見得會真的點進去出處連結看，可能只看那個資訊摘要就評定政見進度了。
> 這個問題有兩個解決方式：
> [name=Johnson L]

> 1\. 解決「觀眾傾向只看標題」的問題，可能要想辦法吸引使用者點進去佐證出處連結看文章、以及降低使用者看原始出處的門檻（原始出處如果是新聞還算簡單，政府公告那種就會比較困難。）
> [name=Johnson L]

> 2\. 讓大家可以編輯別人付的資訊摘要，就像是 Wikipedia 大家都可以修改內文那樣。
> [name=Johnson L]


> 2 是從比較消極的層面來解決問題，但是 1 是個大哉問（和網路行銷的難點重疊呀 XD），所以可以朝 2 去解決。不知道會不會遇到像是 Wikipedia 或新聞小幫手那樣，網友槓上之後互相改對方文字的狀況，是不是該在編輯動作加上個 Facebook login？
> [name=Johnson L]

> \[2015/2/14 update\] 已經規劃「進度回報」可以被[舉報與撤回](https://docs.google.com/drawings/d/1KLyjlC6B2ylx0X-OVLjifSrPmoZDiwdHZUhEbiYnQs4/edit) ，如果新貼的新聞其實比上一篇還來得舊，那管理者可以撤掉這個「進度回報」。界面中仍然會顯示被撤掉的進度回報，但進度條會以沒被撤掉的進度回報為主。
> [name=Johnson L]


2.  平台的核心價值是對各執政者的良好進度更新。雖然完全開放編輯，但這並不代表就會有人來編輯；如果都沒有人貼出處、沒有人評進度，那麼就不會有觀眾來看；沒有觀眾來看，那就更不會有人來更新。或許幾次黑客松可以在網站上衝出一些內容（例如把 2014 所有縣市長政見整理放進平台）、但如果沒有凝聚一個編輯社群，或營造一個類似 Wikipedia 的氛圍，似乎很難讓貢獻持續下去。
> 本來想說靠 gamification 之類的方式來吸引大家做編輯，但目前沒有具體方案 orz
> [name=Johnson L]

> 這其實也屬於一個大哉問，如果解決的話那 social 型的網路創業就超輕鬆呀。
> [name=Johnson L]

> 目前我的想法是，在平檯架起來之後如果編輯狀況真的不理想，那麼我就在每次的 g0v 大松招集編輯，把過去 2 個月的新聞整理進平台裏，最後的報告就幫全台灣的縣市長做過去 2 個月的施政進度報告 XDDD
> [name=Johnson L]

> 我覺得使用的人應該有兩種，一種是積極追蹤或維護政策的人，一種是潛水只想看狀態和表達滿不滿意的人
> [name=Obelai c]

> \-\- 對於積極追蹤或維護的人，提供容易增加內容的使用方式
> [name=Obelai c]

> 增加積極者使用性的方式，可以是減少輸入與智慧導入資訊(比如網址會帶入新聞圖片和標題如FB)、預測顯示文字等
> [name=Obelai c]

> --對於潛水只看狀態的，也提供滿意認同的工具(比如五顆星這類東西)來表達對該狀態進度意見
> [name=Obelai c]

> 如果很多人都不滿意進度，那也等同充分表達對該政策的承諾的人民意見或感受
> [name=Obelai c]

> 對政策民意低落不滿意的政策維護者，如果想要說服民意，就會被迫積極來維護或增添有利政見實現的新聞或文章
> [name=Obelai c]

> 不過政策內容一開始還是得先主動積極去製造，先讓潛水民意覺得這個東西容易表達意見與瀏覽內容為優先。
> [name=Obelai c]

> 輸入很多東西不是大多數人會想去做的事情。(簡化簡化簡化:D)
> [name=Obelai c]

> 套一句查理蒙格的話，OBELAI講的很好，我沒甚麼要補充了。我覺得版主的構想已經很完整，所以期待趕快上架，邊觀察使用者的回饋，一邊版本升級!
> [name=Jiro L]

> 歐北來\+\+ 「完成度」之外的「滿意度」這個 idea 不錯，本來是想要開放送出和進度無關的「爭議」來源，例如說報導政策執行時發生的抗議新聞等等。
> [name=Johnson L]

> 總之該開始嗡嗡嗡了～
> [name=Johnson L]


### 其他討論


#### 權重

權重可以由全部的閱覽者提供。以瀏覽器為人次單位，每當閱覽人初次造訪時，可以隨機詢問他對於這一位政治代理人所關心的面向。提供給閱覽人一組神奇拉桿，可以調出一組權重向量。全部閱覽者的權重向量加總起來，總和的權重向量就是面向A、面向B等等的比值。而政治代理人的每一項政見，可各自歸類為哪一個面向，或者哪幾個面向，這個歸類是由站方預設的。

#### 多人協作 Promise Tracker 另一個實現法

[\[PPT\] Promise Tracker 使用 Wikipedia 之優劣分析](/ifmaZTkhksC#[PPT]-Promise-Tracker-使用-Wikipedia-之優劣分析)

## 徵求協作者


發起人/拋磚人：  [Johnson Liang](https://g0v.hackpad.com/ep/profile/z4JarLrJBea)
分工與成員
- [x] NeedsWriter: 需要文案幫手（撰寫基本資訊、報導專案etc）
- [x] NeedsDesigner: 需要介面設計
- [x] NeedsData: 需要資料（擷取、清理）
- [x] NeedsTech: 需要技術支援（程式、架站 etc)
> My turn
> [name=Shelling F]

- [x] NeedsProcess: 需要幫忙設計作業流程
- [x] NeedsTalkingToRealPerson: 需要有人幫忙和其他機關聯絡
> 設定成 project registry 中的 tags，需要幫忙的會自動 promote 到 g0v project hub
> [name=ET B]

> 需要界面流程設計的部分我可以幫忙
> [name=Obelai c]


### 六都資料來源整理（2015/2/14 & 2015/4/18）

Google spreadsheet： [http://goo.gl/FVAM8c](http://goo.gl/FVAM8c)

#### 選舉承諾

> 選舉黃頁其實有將大部分的公報抓下來，可以參考個別縣市長的頁面
> [name=Finjon K]

> 請問在哪裡呢？昨天點進[選舉黃頁的公報區](http://k.olc.tw/elections/bulletins)，但是沒有看到公報 QQ
> [name=Johnson L]

> 以台北市為例，可以直接找到個別候選人或選區（像是台北市長 \- [http://k.olc.tw/elections/candidates/index/53c0207b-32e8-4ba0-a87c-5c5aacb5b862](http://k.olc.tw/elections/candidates/index/53c0207b-32e8-4ba0-a87c-5c5aacb5b862) ），在畫面右邊中間靠上可以看到 "本頁API" 與 "選舉公報" 兩個按鈕，點選選舉公報後可以進一步看到 "原始檔案" 、 "備份檔案" 與 "網頁格式" 三個按鈕，原始檔案是中選會的連結，備份檔案是把同樣檔案備份到 github 的連結，網頁格式則是透過程式將 PDF 轉為網頁型態的版本。
> [name=Finjon K]

> 公報的資料不算完整，但基本上除了比較偏遠的區域（因為區域選委會提供資料動作比較慢），大概都有備份到了
> [name=Finjon K]

- \[承諾來源\] 中選會選舉公報 [http://103bulletin.cec.gov.tw/103/](http://103bulletin.cec.gov.tw/103/)
    - 台北市：[http://](http://goo.gl/itzRPg)[goo.gl/itzRPg](http://goo.gl/itzRPg)/ [https://www.gitbook.com/@doctorkowj](https://www.gitbook.com/@doctorkowj)
    - 新北市：[http://goo.gl/3Yr4aM](http://goo.gl/3Yr4aM)
    - 桃園市：[http://goo.gl/ETgvrF](http://goo.gl/ETgvrF)
    - 台中市：[http://goo.gl/3o05Ud](http://goo.gl/3o05Ud)
    - 台南市：[http://goo.gl/i8nRBQ](http://goo.gl/i8nRBQ)
    - 高雄市：[http://goo.gl/258q6a](http://goo.gl/258q6a)
- \[承諾來源\] 六都施政白皮書
- \[進度更新來源\] 六都施政報告（四月、八月開議的市長報告與會議記錄）
    - 台北市：[http://](http://goo.gl/itzRPg)[goo.gl/itzRPg](http://goo.gl/itzRPg)
    - 新北市：[http://goo.gl/HFNiNH](http://goo.gl/HFNiNH)  [http://goo.gl/3Tafe0](http://goo.gl/3Tafe0)
    - 桃園市：[http://goo.gl/0wCKJv](http://goo.gl/0wCKJv)
    - 台中市：[http://goo.gl/NQh9l9](http://goo.gl/NQh9l9)
    - 台南市：[http://goo.gl/KOlNPl](http://goo.gl/KOlNPl)
    - 高雄市：[http://goo.gl/kPLWxe](http://goo.gl/kPLWxe)

#### 追蹤報導

- 新聞資料庫
- 各局處公告 (?)


## 實作細節（非技術背景可跳填）

Solution stack: NodeJS + ReactJS [isomorphic web app](http://www.htmlxprs.com/post/20/creating-isomorphic-apps-with-react-and-nodejs).
API server with [loopback](https://speakerdeck.com/coodoo/why-loopback-rocks), which also takes care of database connection, ORM-like abstractions, etc.
> 請問，這個loopback, 是[strongloop](https://strongloop.com/) 的產品嗎? 看起來好像是付費的工具，還是您是用[loopback](https://github.com/strongloop/loopback/) , 這個有教學嗎?看到洋洋灑灑的的api清單(指API explorer:)，是用快速產生的指令列工具嗎? 我看到了，[快速啟動](http://loopback.io/getting-started/)，真的是一個欄位一個欄位設定名稱和型別，有別招嗎?
> [name=Ting L]

> loopback 是免費的開源專案～ [官方文件與教學在這裏](http://docs.strongloop.com/display/public/LB/LoopBack)。
> [name=Johnson L]

> slc loopback:model 指令背後做的事情其實就是修改 server/model-config.json 以及在 common/models 裡面生成設定的 json 這樣，所以也可以直接改檔案喲～！
> [name=Johnson L]

> 其實和 rails generate model 一樣，如果不用工具生，也可以自己蓋檔案。
> [name=Johnson L]


協作工具
- github repo：[https://github.com/](https://github.com/g0v/ppt)[g0v/ppt](https://github.com/g0v/ppt)
- hackfoldr 工作資料夾網址：
- google drive 共用資料夾網址：

### Roadmap / TODO

    - [x] Livereload to make developing a happy process
    - [x] Combine React.js mockup with mock data directly in React
    - [x] Add React.router
    - [x] Add Flux
    - [x] Move mock data into in-memory database, serve from API.
    - [x] flux actions that fetch data from api and put data in stores -- 改成用 React-transmit，已可以從 DB 撈資料顯示。
    - [ ] 外觀重新調整：決定是否要留著 semantic-ui 還是改用 [material-ui](http://material-ui.com/)、[調顏色](http://paletton.com/#uid=33i0u0kw0oUmHvDtLuRBPkmKtf3) （或[亮一點的版本](http://paletton.com/#uid=33i0u0kCfw8lTF2r+CiEdpnIzjN)

### API Server (Currently down QQ)

[https://promisetw.herokuapp.com/](https://promisetw.herokuapp.com/)
API explorer: [https://promisetw.herokuapp.com/explorer](https://promisetw.herokuapp.com/explorer)

### DB structure

參考[真度計的 ER Diagram](https://docs.google.com/drawings/d/1EGtlENxrRaW0bpdZnxlqV516nmoz8VtOhoIZpqnrG1Y/edit)  ，將上述 prototype 所需 database table 與關聯，繪製成下面的 ER Diagram：
> 上面連結已經 Not Found
> [name=Ting L]

> 真的耶 QQ 請問原作者 [John Lin](https://g0v.hackpad.tw/ep/profile/xJOH0LkUNIk) 有沒有留存呢 ?
> [name=Johnson L]

> 我把連結補好了!
> [name=John L]

> John Lin ++
> [name=Johnson L]

[https://docs.google.com/drawings/d/1KLyjlC6B2ylx0X-OVLjifSrPmoZDiwdHZUhEbiYnQs4/edit?usp=sharing](https://docs.google.com/drawings/d/1KLyjlC6B2ylx0X-OVLjifSrPmoZDiwdHZUhEbiYnQs4/edit?usp=sharing)
（縮網址 [http://goo.gl/eDt7TZ](http://goo.gl/eDt7TZ) ）



