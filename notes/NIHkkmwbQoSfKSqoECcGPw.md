---
tags: vTaiwan
---
# 20251119 小松

時間 Time ：19:00 - 20:00
地點 Location ：線上 Online
參與者 Participants： Bestian, Anan阿南,Tim,Josh,Yi-Ting,

 ![](https://g0v.hackmd.io/_uploads/BJK3xEjxZl.png)
https://www.vtaiwan.tw/jitsi
(請用Google登入以參與視訊並啟用轉錄功能)

![](https://g0v.hackmd.io/_uploads/SkrClNsg-x.png)


::: success
## 專案儀表板：目前 vTaiwan 社群在進行的事情 
以下是 vTaiwan 目前正在進行的幾個不同的專案！如果有興趣，可以在取得共筆編輯權限後+1，或者是
1. [vTaiwan議題小聚](/GUe0KXMsQBC-6KTIUPBVnA)
    - 適合對審議、公共討論有興趣的人加入
    - 活動咖的最愛
    - 如果有公民團體與組織想要合作也可以看過來！
    - 目前也在進行 [AI 用於數位公民參與經驗](/nJUYukWFSWuEsG-XQalHcA) 的收集！
2. [vtaiwan x Tech for Good Asia 合作](/PdvNjkLlSd-WytXN_otWbQ) 計畫
    - 預計會討論人工智慧相關議題
    - 需要研究與分析人才
    - 想要貢獻議題或意見這邊請
3. [vTaiwan 網站改版，啟動！](/Q3_hgovyRHusEq8-3nomPQ)
    - 目標是打造新的 vTaiwan 網站
    - 結合 blog、媒體資源、活動發佈、建立線上活動與討論等功能
    - [vTaiwan 網站更新後的治理機制](/HxWF11d4Tz-AfHb3yjwQKg)也在建立中
    - 讓不會寫程式的人也可以加入貢獻者！
4. [vTaiwan 主視覺更新](/UqGh6pAUTwuNFr1RE21Rtw)
    - 目前已經設計完成！
    - 會發佈到新的網站，並在社群媒體上完成更新！
5. [Frankly 測試](/HVEdPVQqQHqVwvFECg7sRg)
    - 目前正在測試一個新的線上會議
6. 如果想要提案怎麼辦？
    - 目前的 vTaiwan 很歡迎與數位工具相關的公共討論！
- 如果想要成為協作者或者是貢獻者，我們正在努力讓說明更清楚，介面更友善！
:::

## 小小的分享：




## 上週議題延續

* [vTaiwan網站blog連medium的可能性](https://github.com/g0v/vue.vTaiwan-neo/issues/116)

* sensemaker web UI前端專案
https://github.com/g0v/sensemaker-frontend
https://github.com/g0v/sensemaker-frontend/issues



## 1123g0v費波那契數列黑客松

https://jothon.g0v.tw/


## 上週會議記錄與AI大綱

https://g0v.hackmd.io/@Pno233SAS8G5UfL5OvSRmA/Bkxd93ZeZl#%E8%BD%89%E9%8C%84%E9%80%90%E5%AD%97%E7%A8%BF%E8%88%87AI%E5%A4%A7%E7%B6%B1

## 人工逐字稿（不負責任紀錄）

Bestian:上週的議題延續，Josh提到可以把 vtaiwan連到 Medium，這週還沒有新的進展，沒有關係，我先把這個議題記錄下來。另外是，上次Peter有提到說 那個SenseMaker的Web UI前端專案 可以在費波那契數列黑客松，11月23號黑客松的時候來一起改良這樣子 那我也把這個專案的網址先貼上來 到時候黑客松的時候我應該是會帶那個機器過去 如果遇到就可以一起來改這樣。


Bestian:那今天上線的都是工程端的，那我提一下 sensemaker 。
那這個SenseMaker的前端專案 我已經把它加到那個G0B的V Taiwan Team了https://github.com/g0v/sensemaker-frontend 所以大家現在都可以有編輯寫入權限 如果是Clone到盡端的話 就編輯之後就可以直接Push上去 然後它會自動部署這樣子。


Bestian:那我現在導覽一下 sensemaker的 UI。

:::success
![](https://g0v.hackmd.io/_uploads/HkfsSQoebe.png)
:::

Bestian:（講解中...)就不紀錄了。
註解：Github本專案開票處 https://github.com/g0v/sensemaker-frontend/issues
 
 
Tim:可以從 github page的頁面稍微說明一下他的使用流程嗎？

Anan:現在sensemaker的後端是不開放的對嗎？ 

Anan:Josh 上上次Josh 您demo的 ai agent對話程式碼可以上傳到 g0v github嗎？ 

Josh :＠anan 抱歉我一直拖😅 因為當時是為了在local跑實驗，沒有很user friendly，agent分配工作的方式很陽春，我想辦法這週來整理code，先放個陽春版 😄 

Tim:上下文功能是什麼？

Bestian:實際操作查找程式碼：上下文功能是否有作用？
:::success
![](https://g0v.hackmd.io/_uploads/B1bBVoXixbe.png)

:::

Josh:請問通常polis下載的 csv是否不會包含提問和主題說明等資料？

Bestian:對

Josh：因為提問和主題說明等資料做報告很重要，所以建議可以強調說明上下文這個功能可以額外補充「提問和主題說明等資料」。

Bestian:對，很好，我把它新增文 issue.


Josh:

Tim:可以在 polis的 csv就包含缺乏的主題說明嗎？

Bestian:不行噎，可能告訴使用者，額外的脈絡要自行增加在上下文。

Josh:目前Bestian做的算是蠻好操作的。若以後可以只要貼polis該主題的網頁資料，讓ＡＩ自動幫忙抓主題資料，加入現在 意見綜整器的分析

Bestian:好像不會很難。用爬蟲方式抓polis report網頁上的 csv和主題資料。

Josh:已經做很多了，不一定要馬上做。

Bestian：但可以先記錄為議題。（紀錄在哪裡？

Tim:raw data 要在哪裡上傳？可否放前面一點？

Josh:我覺得已經做得非常完善了，如果有一個很友善的 readme，一點點的敘述，理論上使用者應該知道怎麼做。

Bestian:也可以，UI設計蠻快的，11/23來做的話蠻快的。

Josh:沒有說要這樣或那樣，主要是說...

Tim:Josh是說應該要有一個說明頁面嗎？類似導引的動畫...

Bestian:螢幕截圖標注一二三步驟，對圖像操作者會比較容易。

Josh:最基本上是讓不知道sensemake的人，進來後，不管我們用哪種方式導引，甚至是幾句話，就讓人進來可以使用。

Tim:比較難的應該是 openrouter的申請吧...


Josh:不是openrouter 的 api key，其他地方的模型 api可以嗎？

Bestian:目前能橋接前後端的只有 openrouter 的 api key，例如 google 的模型 api目前還不行用在這裡。

Josh:假設有 open AI的 Key可以用？不可以對接的原因是什麼？

Bestain:橋接的模型可以跑的地方.....我確認一下

Josh：謝謝 Bestian做那麼多，因為我不能待太久，在我離開之前，今天還有什麼要處理的嗎？另外 Yiting有沒有要分享的？


Yi-ting:目前只剩行政的事，大家不用擔心。另外 Bestian這個東西很棒，期待。
Twnic有表達很希望可以繼續跟vtaiwan合作。


Josh:因為我們有再提一個 proposal嗎？他們是想跟vtaiwan還是 Teach for Taiwan合作？


Yi-Ting:TFT的部分我不太清楚，不過TWnIC grant各種不同專案是各自獨立的，不會互相影響

Josh:接下來的議題小聚要再提出來了，不然空檔好像有點久。有兩次討論的過程...

Yi-ting:5/23 ，8/1 之前兩場的討論...

Josh:之前好有心得，但沒有馬上寫下來都忘記了


Yi-Ting：沒關係我可以把當時的紀錄找出來你就會記得了。

（大合照時間）





## 轉錄逐字稿與AI大綱


### 轉錄逐字稿詳情

https://www.vtaiwan.tw/transcription_detail/20251119


### AI大綱
> 這次AI有點幻覺，手動校正了不少[name=Bestian]

## 1️⃣ 會議小結  
| 時間 | 主要議題 | 結論 / 待辦 |
|------|----------|-------------|
| **V‑Taiwan → Medium API** | Josh 先前提過把 V‑Taiwan 網站的內容以 Medium API 把文章轉發。 | 已取得共識，先把需求寫到 Issue，暫時不急於開發。 |
| **SenseMaker 前端 (Vue 3)** | 介紹 repo 結構、i18n、路由、部署流程（push → Vercel 自動部署）。 | 已給 Team 讀寫權限，大家可以直接 clone、edit、push。 |
| **UI 小毛病** | 1️⃣ 按鈕文字顏色（白底白字）<br>2️⃣ 檔案上傳按鈕顏色/文字不易辨識<br>3️⃣ 上傳成功後的狀態提示（灰底）<br>4️⃣ 缺少 **OpenRouter 註冊說明** 連結 | 把對應 issue 建好，標上 `good first issue`，讓新手先練手。 |
| **API 金鑰設定流程** | 需要先去 OpenRouter 註冊 → 取得 API‑Key → 填入設定頁面。 | 需求：在首頁（或設定頁）加上 **「OpenRouter 註冊教學」** 超連結。 |
| **黑客松（11/23）** | 目標：<br>・修正 UI 小問題<br>・新增使用說明（OpenRouter 註冊、API Key 輸入）<br>・把 repo 佈署到 cloudFlare（已自動） |  |


---

## 2️⃣ 目前卡片（Issues）概覽
| Issue # | 標題 | 類別 | 優先度 | 提議者 |
|---------|------|------|--------|-----------|
| 1 | **檔案上傳按鈕樣式/文字**（灰底看不見檔名） | UI | 高 | Bestian |
| 2 | **文字與截圖導覽 | Docs | 中 | Tim |
| 3 | **首頁加上 OpenRouter 註冊說明連結** | Docs | 中 | Josh |


---

## 3️⃣ Model‑Adapter 設計 (固定用OpenRouter，因實務障礙，暫不考慮開發切換Open AI KEY的功能延伸)

### 3.1 為什麼要抽象化？  
- **可插拔**：未來想換模型（例：Claude、Gemini）不需要改前端邏輯。  

### 3.2 主要障礙  

| # | 主要障礙 | 影響範圍 | 
|---|------|----------|
| 1 | **gpt‑oss‑120b 無法直接使用 OpenAI Chat Completion** | 後端 API 呼叫 | 


---

## 總結與下一步

1. **UI 小毛病**（顏色、上傳提示）也同樣列在 Issue，先把 `src/components/` 的 CSS 改成 Tailwind `bg-primary-600` 等，確保所有文字在亮色背景上可見。  
2. **文件/說明**：在 `README.md` 加入 **OpenRouter 註冊教學** (link + 步驟圖)；在首頁 `Home.vue` 加 `OpenRouter 註冊說明` 超連結。  
3. **黑客松**：在黑客松上協作修UI

















