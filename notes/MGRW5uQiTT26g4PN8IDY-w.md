---
title: "[PPT] Mockup 與系統設計"
tags: Promise Tracker,hackpad
---

> [點此觀看原始內容](https://g0v.hackpad.tw/UhHyAukazZ4)


#### ＊專案上層 Hackfoldr：[http://beta.hackfoldr.org/ppt](http://beta.hackfoldr.org/ppt) ＊


系統的核心是「**針對單一執政者，呈現其承諾的實行進度**」，所以希望能先 focus 在討論這個部分的使用者體驗。究竟要呈現哪些執政者，是否要通通整合在一個網站，可以之後再說。

目標：使 editor 能易於更新新聞、使 audience 能快速判斷施政能力。

```
                    ↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓
```
Clickable Prototype 網址:  [**http://invis.io/9Z1TFRTFT**](http://invis.io/9Z1TFRTFT)
```
                    ↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑

```
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_12026907073e201bce1810ca3143345f)

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

[\[PPT\] Promise Tracker 使用 Wikipedia 之優劣分析](https://g0v.hackpad.com/ifmaZTkhksC#[PPT]-Promise-Tracker-使用-Wikipedia-之優劣分析)


## 實作細節（非技術背景可跳填）

### 協作工具

- github repo：[https://github.com/g0v/ppt](https://github.com/g0v/ppt)
- hackfoldr 工作資料夾網址：[http://beta.hackfoldr.org/ppt](http://beta.hackfoldr.org/ppt)
- google drive 共用資料夾網址：

### Solution stack

NodeJS + ReactJS [isomorphic web app](http://www.htmlxprs.com/post/20/creating-isomorphic-apps-with-react-and-nodejs).
API server with [loopback](https://speakerdeck.com/coodoo/why-loopback-rocks), which also takes care of database connection, ORM-like abstractions, etc.
> 請問，這個loopback, 是[strongloop](https://strongloop.com/) 的產品嗎? 看起來好像是付費的工具，還是您是用[loopback](https://github.com/strongloop/loopback/) , 這個有教學嗎?看到洋洋灑灑的的api清單(指API explorer:)，是用快速產生的指令列工具嗎? 我看到了，[快速啟動](http://loopback.io/getting-started/)，真的是一個欄位一個欄位設定名稱和型別，有別招嗎?
> [name=Ting L]

> loopback 是免費的開源專案～ [官方文件與教學在這裏](http://docs.strongloop.com/display/public/LB/LoopBack)。
> [name=Johnson L]

> slc loopback:model 指令背後做的事情其實就是修改 server/model-config.json 以及在 common/models 裡面生成設定的 json 這樣，所以也可以直接改檔案喲～！
> [name=Johnson L]

> 其實和 rails generate model 一樣，如果不用工具生，也可以自己蓋檔案。
> [name=Johnson L]


### API Server

[https://promisetw.herokuapp.com/](https://promisetw.herokuapp.com/)

### DB structure

參考[真度計的 ER Diagram](https://docs.google.com/drawings/d/1EGtlENxrRaW0bpdZnxlqV516nmoz8VtOhoIZpqnrG1Y/edit)  ，將上述 prototype 所需 database table 與關聯，繪製成下面的 ER Diagram：
> 上面連結已經 Not Found
> [name=Ting L]

> 真的耶 QQ 請問原作者 [John Lin](https://g0v.hackpad.com/ep/profile/xJOH0LkUNIk) 有沒有留存呢 ?
> [name=Johnson L]

> 我把連結補好了!
> [name=John L]

> John Lin ++
> [name=Johnson L]

[https://docs.google.com/drawings/d/1KLyjlC6B2ylx0X-OVLjifSrPmoZDiwdHZUhEbiYnQs4/edit?usp=sharing](https://docs.google.com/drawings/d/1KLyjlC6B2ylx0X-OVLjifSrPmoZDiwdHZUhEbiYnQs4/edit?usp=sharing)
（縮網址 [http://goo.gl/eDt7TZ](http://goo.gl/eDt7TZ) ）


