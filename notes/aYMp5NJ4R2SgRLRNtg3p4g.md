---
title: "新聞，聞異文 (wp2014s_Team8)"
tags: hackpad
---

# 新聞，聞異文 (wp2014s_Team8)

> [點此觀看原始內容](https://g0v.hackpad.tw/WP8sUFwcqlH)


## 緣起

2011年3月31號，「NewTalk新頭殼」出現一篇題為【躲不掉！ 台灣南北均測到微量碘131】的報導；隔天，「中國時報」出現一篇題為【台灣測到碘131 極微量 不傷身】 。在台灣，對於同一個事件，我們能看見多元的觀點、聽見不同的聲音。然而，當人們養成固定的視聽習慣之後，很容易會只關注特定幾家媒體，進而減少接觸不同聲音的機會，甚至最後容易對特定媒體產生成見。

就如同專案名稱，我們要打造的是一個新聞平台，針對核四存廢的議題，蒐集、整理不同來源、不同角度的新聞。使用者若想快速瀏覽一個社會議題的不同見解，不用再到各大新聞網。透過我們的平台，就能快速的看見不同觀點的新聞。透過我們的推薦系統，有更多機會瀏覽與自己立場相左的新聞，更能了解議題正反方的各自論點。摒去心中成見，使真理越辯越明！


## 專案介紹

簡單的說，這個專案要做的是「新聞分類整理」+「新聞推薦」這兩大功能。

一般人很容易只瀏覽特定的新聞網站，因此有關聯、或相關推薦文章的來源也都是同樣的媒體，只看到一種觀點聲音。有別於一般新聞網站，我們要做的重點在推薦「大家都認為值得看的新聞」、還有「使用者較少選擇的新聞來源」。透過簡單的使用者回饋機制，讓使用者除了能快速瀏覽相關新聞，也能給予回饋，幫助更多使用者來分辨新聞的公正與否。

> 這是一個好題目，可進一步思考，不同媒體或不同立場的內容擺在一起時，應突顯哪些資訊可吸引讀者閱讀多元觀點？
> [name=jones f]

> 另外媒體本身也是一個 core object，標示出其色彩，讓讀者閱讀內容前先了解
> [name=jones f]

> 或者惡行重大，長期有偏頗的媒體，應該直接列入黑名單？
> [name=jones f]

> 我們會透過內文重點標示的方式，像是加粗或上色，讓讀者可以快速瀏覽新聞重點。
> [name=廖祥佑]

> 而會認為有所偏頗，其實也是因為加進個人的主觀意識，我想這個專案的目的，就是提供一個管道，讓大家有更多機會接觸與自己立場相左的新聞資訊；如果媒體本身惡行重大，也能讓更多人揭發惡行所在
> [name=廖祥佑]

> ===2014/5/13新增
> [name=廖祥佑]

> 我們在新聞的分類上，有幾個分頁可做選擇。除了熱門新聞以外，剛好當前的社會議題，對立的兩面常常是人民與政府。因此我們有"人民"與"官方"這兩個新聞分類標籤，可以算是一種快速分類立場的方法
> [name=廖祥佑]



## 要解決的問題


１.現今每日新聞資訊量不小，蒐集與快速分類"相同事件"的新聞會是個考驗
> 這是最重要的部分，請思考如何網羅並整理同一議題、不同來源的資料（中時、自由、UDN、蘋果...）
> [name=jones f]

> 使用自動化程式或者開放群眾編輯？
> [name=jones f]

> 目前我們的構想是以人工蒐集新聞為主，有考慮增加“投稿”的功能，若有讀者發現其他與主題相關的新聞，可以提供新聞來源，經過審核後再更新上網站，也可以免去完全自由編輯下，可能出現濫發文章或惡意洗板等問題
> [name=廖祥佑]

> 除了提供不同來源的新聞報導，可再增加「深入評論」或「名家專欄」，增加讀者觀看一件事時以多元角度來了解議題。
> [name=jones f]

> Utimate goal: 如何幫助讀者以多元觀點看事件: 思考呈現方式、相關可並呈的資訊、使用者可做哪些互動功能（在閱讀新聞時，call to action: 新增多元觀點 --> 轉貼其它平衡報導連結...）這些是你們需好好做好的功課。
> [name=jones f]

> ===2014/05/13新增
> [name=廖祥佑]

> 我們目前的構想是，先蒐集一定數量的新聞當作database，配合我們的新聞推薦功能，會逐漸有更多使用者認為值得分享的新聞補進我們的新聞庫，在日後出現在專案平台的頁面上。
> [name=廖祥佑]

> 另外，我們會設計簡單的機制，讓使用者參與議題的分類過程。除了有公正與否的評分機制，也有人民、官方等立場等選項，並在累積一定數量後，成為系統自動分類依據
> [name=廖祥佑]


２.如何做到與各大新聞網站的文章連結，提供使用者從外部連結進我們網站的管道

３.我想，其他就讓我們從實做中發現問題，從問題中學習突破吧！

4.個人頁，瀏覽紀錄如何記錄？

5.後台建置、如何導入各大新聞網站的新聞文字。

6.分類頁跟新聞內文的頁面的連結問題。



## 現有類似專案或網站


### _智博簡報資料庫↓_

[http://www.iampd.com.tw/](http://www.iampd.com.tw/)
    優點：將大量新聞以剪報方式儲存，做成E化的雲端剪報資料庫，方便使用者快速搜尋
    缺點：內容與社會議題關連性小、使用者需付費

### _新聞小幫手↓_

[http://newshelper.g0v.tw/](http://newshelper.g0v.tw/)
    優點：透過公民力量即時回報有問題之新聞內容
            與各大瀏覽器、以及Facebook綁定整合，回報方便速度快
    缺點：僅針對有問題之新聞內容做回報，並非對現有新聞做蒐集與整合
            在新聞是否有問題的認定上，容易受個人主觀看法影響

### _MoneyDJ 理財網-新聞頁↓_

[http://www.moneydj.com/](http://www.moneydj.com/KMDJ/News/NewsHome.aspx)[KMDJ/News/NewsHome.aspx](http://www.moneydj.com/KMDJ/News/NewsHome.aspx)
    優點：整合經濟、財政、金融市場等相關主題的多方資訊，匯集成獨立的新聞網
    缺點：與一般金融理財網的功能類似，並無特別之處
            新聞範圍較窄，幾乎不會有社會議題的新聞出現

### _Google新聞↓_

[https://news.google.com.tw/](https://news.google.com.tw/)
    優點：與本專案之理念類似，除了有一般入口網站之新聞頁功能，更整合相同議題之不同來源新聞
    缺點：僅提供新聞之網頁連結，要閱讀仍需要點擊後外連
            設計上並無吸引使用者點擊非自己習慣來源之新聞網站
            沒有獨立的回覆、評論功能，依然要依靠各自新聞網做設計之回覆功能



## 分工與成員

    廖祥佑｜內文頁、推薦頁Mockup&HTML；Parse分類頁
    李元銘｜首頁、個人頁Mockup&HTML；Parse建置
    陳宥丞｜分類頁Mockup&HTML；登入功能FB綁Parse
    蔡旻芸｜內文頁、推薦頁Mockup&HTML；CSS設計；Parse內文頁
    洪緻崴｜分類頁Mockup&HTML；資料新聞蒐集
    劉 璞｜首頁、個人頁Mockup&HTML；Hackpad更新；海報製作




## 實作細節（非技術背景可跳填）

協作工具
- github repo：[https://github.com/NCCU-DifferentNews/DifferentNews](https://github.com/NCCU-DifferentNews/DifferentNews)
- hackfoldr 工作資料夾網址：
- google drive 共用資料夾網址：[https://drive.google.com/folderview?id=0BzFIwJF2TyaQTkVHeXdnS2dHM2s&usp=sharing](https://drive.google.com/folderview?id=0BzFIwJF2TyaQTkVHeXdnS2dHM2s&usp=sharing)

進度與 to-do
    僅供參考
- [x] product planning
    - [x] strategy
    - [x] scope
    - [x] structure
    - [ ] wireframe
    - [ ] visual
- [ ] web front-end
- [ ] web back-end
- [ ] ui / visual design
- [x] 5/14 完成所有頁面設計 (Html + CSS)
- [ ] 6/11作品完成 (js+cloud DB)，進行beta測試


## 成果展示（規劃文件、雛形/草稿、原型/初稿、正式發佈/完稿）


### 期中內容需包含

- core and path sheet
- structure
- mockup


### Structure


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_43bc80bb882ef9ddd8e3246e6b113f19)

我們將針對核四議題做新聞整理與蒐集。
虛線連結出去的五個分頁，雖然沒有實體頁面，但因為是本網站的特色之一，所以以此形式表現。
另使用者推薦新聞其實也非實體頁面，是存在新聞內文頁面的一個功能。



> 為何分為這七大類別？考量為何？
> [name=jones f]

> 我們參考報紙的版面分類，將與民生議題較有關係，或政策方面有關聯作為分類依據。
> [name=廖祥佑]

> 其他方面的新聞仍可以考慮放上網站，歸類在其他類。
> [name=廖祥佑]

> ===2014/05/13新增
> [name=廖祥佑]

> 新增新版本structure
> [name=廖祥佑]



### Core and Path Sheet && Mockup


### 首頁：

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_98b81a93d59c668274cc7c7954e83c4d)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6206fc2f454f0ae999ddea589833184d)


### 分類頁：

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_34524e1e34189ef180754297974eb546)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_f78b883fec4e007ad7ef4bee7dbe7d1c)


### 新聞社論頁：

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_fdbcb15e66be68cb4a765bb5d9f26cc4)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9e3eff6018b56a755ae6f63354261b00)


### 推薦頁：(會以跳窗方式呈現)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9bf4b6609f90d8019a6780fb97ed5126)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_1cb4f4cd5e32c728efef788d773b5b0c)


### 個人頁：

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6bb62440d5c486dc767e106b539257e7)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_f63c6b58543142cd2f8c67d816a8414e)



> elements of core會從 core content中選出最重要的內容
> [name=jones f]

> home page的 outward path應該是進入議題分類或閱讀熱門議題
> [name=jones f]

> 這幾份sheet中的 outward path與 call to action都請再思考
> [name=jones f]

> 已更新worksheet
> [name=廖祥佑]


> Title 指的是？
> [name=jones f]

> 網站圖示需要佔這個大版面嗎？圖片內容為何？
> [name=jones f]

> core and path中的core content有熱門新聞與最新消息，但mockup中只有熱門，沒有最新？！
> [name=jones f]

> 熱門頭條下方的兩欄是何種新聞內容？指正反新聞嗎？
> [name=jones f]

> 網站圖示此欄位，除特別設計符合主題之圖片內容，並加上簡潔的文字說明，用來說明此網站(專案)的理念
> [name=廖祥佑]


> 分類頁的目標是列出所有議題， core content應該不需要列出新聞內文吧？若要列出，是列哪一方的說法？
> [name=jones f]

> outward path: 新聞文章 / call to action: 深入閱讀
> [name=jones f]

> 老師不好意思，我們之前把分類頁跟內頁的worksheet放反了(Sorry)
> [name=廖祥佑]

> core object 保留「新聞」就好，刪除「照片」、「討論區」( --> 與 user's goal關係較遠)
> [name=jones f]


> 支持率如何計算？
> [name=jones f]

> 我們會設計一個支持率bar，類似於Youtube影片下方的喜歡/不喜歡統計條
> [name=廖祥佑]

> ===
> [name=廖祥佑]

> 2014/05/13 新增新版worksheet + mockup
> [name=廖祥佑]

### 成果海報

[http://nccu-differentnews.github.io/DFNs/index.html](http://nccu-differentnews.github.io/DFNs/index.html)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_eb9831563b802f34b2ce2b3e4bf9e38a)



