---
tags: 資料申請小幫手
---

# 政府資料開放平台課題列舉 - 2021

政府資料開放平台：https://data.gov.tw/

課題目錄
:::warning
[TOC]
:::

---

# 平台課題列舉

## 政府其他資料平台並未整合

社會經濟資料服務平台
https://segis.moi.gov.tw/STAT/Web/Portal/STAT_PortalHome.aspx
GIS-T交通網路地理資訊倉儲系統
https://gist.transportdata.tw/gist_web/
TGOS 圖資
https://www.tgos.tw/TGOS/Web/MetaData/TGOS_Query_MetaData.aspx
提供限期免費的限量福衛二號及五號影像作為研究使用
https://scidm.nchc.org.tw/organization/narl-nspo

## 應整合呈現「已釋出資料」、「我想要更多」、「應用案例」
- 目前拆成兩邊，使用者要搜尋兩次
- 過去的發問，已開放資料的話，要提供最新的連結
- 情境舉例：於政府資料平台輸入「門牌」一詞，呈現以下
    - (1) 已開放資料集
        - 臺中市政府門牌 GIS https://data.gov.tw/dataset/152685
    - (2) 歷年詢問
        - 2019年7月30日 https://data.gov.tw/suggests/106384
        - 2018年5月5日 https://data.gov.tw/suggests/80423
        - 2017年7月18日 https://data.gov.tw/suggests/48493
        - 2017年7月6日 https://data.gov.tw/suggests/47769
        - 2015年9月12日 https://data.gov.tw/suggests/21721
        - 2015年6月26日 https://data.gov.tw/suggests/16440
        - 2015年1月7日 https://data.gov.tw/suggests/9980
    - (3) 歷年詢問的回答
        - 機關1 臺中市政府：已開放
        - 機關2 臺北市政府：無法開放
        - 機關3 臺南市政府：無法開放
        - …等
    - (4) 此資料集的民間專案
        - 運用已開放資料：臺中市門牌資料的應用服務
        - 雛形類：例爬臺北市門牌資料的民間資料應用等
    - (5) 此資料集的政府應用
        - …等

## 建立標籤系統 / 同義詞 / 權威字詞
- 相關的工作主題：[資料集與資料詢問 - 議題標籤](https://g0v.hackmd.io/uvFquIa9RQCWzOlXd5tmDA)
- 目前平台有開放讓使用者，針對已開放資料集，輸入關鍵字標籤
    - 詢問此資料，是否開放
- 平台使用者 過去搜尋過的關鍵字有哪些？
    - 詢問此資料，是否開放
- 
- 關鍵字同義詞 / 權威字詞
    - 樂詞網 https://terms.naer.edu.tw/
    - 立法院有放出「同義詞權威檔」，是國會圖書館整理的，方便委員在找法案時下關鍵字可以找到同義詞用的
    - https://data.ly.gov.tw/getds.action?id=321
- 平台目前沒有採用同義詞
    - 2022-12-15
        - 您好，有關臺端開放平臺「目前已採用的同義詞清單」，因政府資料開放平臺資料集搜尋機制並非採用同義詞比對機制，係以使用者輸入關鍵字精確查詢輔以布林邏輯演算法(and,&,or,|,not,-,空白視為&)，檢索詮釋資料欄位並找出匹配結果，若有與搜尋關鍵字比對符合之資料集，則顯示搜尋結果列表中，爰無「同義詞清單」相關資訊，敬請見諒。
        - https://data.gov.tw/suggests/136624

## 民間如何跟追已發問的資料需求申請
 - 目前我想要更多的發問，無法追問 !
 - [說明文件：什麼是一日資料申請小幫手？](https://docs.google.com/presentation/d/1DBcZPfyFUfBjZh4t4pUOkW_JaxpInyMAfe_y34_tsi8/edit#slide=id.g5d40c09f4c_0_16)	
## 「我想要更多-申請-API」
- 未來這個 API 若開放，不只是小幫手的網站，從整體社會來說，就有可以多增加一些詢問窗口，各式領域例如環境團體、社會經濟資料關注者，或者就是介面優化，更加強網站通用版本的資料申請機會，族裔語言的介面等
- 小幫手目前有建立一個「申請組合器」
    - https://dataopener.tw/application
- 目前支援的登入方式有 我的E政府 / Google / Facebook, 應該都可以用 OpenID / OAuth 的方式來處理。就是使用者還是要用相同方式登入，並同時同意 dataopener.tw & data.gov.tw 兩個網站的授權
- https://sayit.pdis.nat.gov.tw/2017-06-23-%E5%85%B1%E9%80%9A%E6%80%A7%E6%87%89%E7%94%A8%E7%A8%8B%E5%BC%8F%E4%BB%8B%E9%9D%A2%E8%A6%8F%E7%AF%84%E8%AA%AA%E6%98%8E%E6%9C%83


## 「不同意提供的理由」的爭點持續整理、相關案例、可能的對策，這類內容共筆整理與呈現
- 爭點分析與因應方案、申覆情勢判斷
- 文件：https://docs.google.com/spreadsheets/d/1-OGBdA5v00WueQYHFOQlyiJnV4B8bWcAiy5x-Rq7oWU/edit#gid=0
- 預計納入：
    - 對策方案：水利署水保局與 LASS 社群共同優化資料集內容
        - https://www.facebook.com/groups/LASSnet/posts/2870309479886310/
    - 內容類型：紓困措施訊息或資料
        - https://g0v.hackmd.io/2iYwwJMATOSFhl22Fh633g?view#%E7%B4%93%E5%9B%B0%E6%8E%AA%E6%96%BD%E7%9A%84%E9%96%8B%E6%94%BE%E8%B3%87%E6%96%99%E6%9E%B6%E6%A7%8B%E8%88%87%E7%99%BC%E4%BD%88%E6%B5%81%E9%80%9A%E8%AA%B2%E9%A1%8C
- 觀察：公文寫作、法律狀書，是紙本時代的「講清楚」的方式，使用的文學方法，有一些功用型字詞的創造如內文出現「爰」字，代表「因為」，通常用於否定的結果...等等用法；開放資料申覆，一開始也是文章寫作，現在雙邊都有趨向結構化的發言方式
- 機關：勾選情況
- 民眾：國發會提供給申請者的欄位架構、理由組合器
- 是否可以看成，問答雙方，都邁向結構化、論點化，但不採用公文&狀書語法，而是運用以資訊技術為基礎的「網頁勾選」，來 tag 自己的發言內容
    - 因為純文章寫作，再來斷詞再判斷此則文意，似乎是不容易 (?)
    - 另外，有了標籤，或發言內容提及明確法律條文（若可以的話，希望能協助發言者帶入正規化法律條文名稱），或許還可以 factcheck 一下大家的發言
    - 上述資料申覆的文意改善方向，對照來看，1999 通報，或其他種類的問答場域、通報場域，可否有些類同或差異點指認？
- 從單一標籤主題，應該是需要一起涵蓋「已釋出資料」以及「我想要更多」內容，來讓資料查找者概覽該主題的開放資料概況
    - 主題資料開放狀況檢視架構
       - 已開放什麼
       - 已詢問什麼
       - 詢問後不開放的是那些、原因是什麼
       - 可能的因應對策是什麼


 
## 未來是否開放民間法人上傳資料集？
- 國內平台案例：
    - 中研院資料寄存所 https://data.depositar.io/
    - TGOS 內政部地圖協作平台 https://www.tgos.tw/MapSites/Web/MS_Home.aspx
- 民間資料案例
    - 鄉民建資料：https://docs.google.com/spreadsheets/d/1IlK6XpIbnL6nW-UjGw363KcmzGNGmEAsAk0rs0qQuYc/edit
- 也有很多情況是，民間端，優化了政府開放的資料集
    - 放在 github 或 spreadsheet

## 蒐集 自然語言處理 應用於 申覆問答全文
- 討論：要解決什麼問題、什麼環節？
    - 以目前機關回答必須提供明確三選一答案的現況下
- Articut NLP 系統內建「法律文件工具包」的操作示範！加碼！Chrome/Firefox 的「法律文件助理」的操作示範。
    - https://www.facebook.com/369036703834596/posts/993329824738611/
- 斷詞方法應用於提問與回覆的實用可能
    - https://www.facebook.com/558939927483114/posts/2709068539136898/
- NLU 意圖分類工具，而且還有一個超酷的名字叫 Loki！不用大量語料，最少只要「一句」就會動！不用另外斷詞，我們幫你擷出關鍵字！
    - https://www.facebook.com/Articut/posts/641461006592163
    - https://www.facebook.com/558939927483114/posts/4527220437321690/
    - 關鍵句 https://www.facebook.com/369036703834596/posts/651689408902656/
