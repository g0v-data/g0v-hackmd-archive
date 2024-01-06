---
title: "檢視、分析、利用 data.gov.tw 全站資料集"
tags: hackpad
---

# 檢視、分析、利用 data.gov.tw 全站資料集

> [點此觀看原始內容](https://g0v.hackpad.tw/3RNgmmLFAzf)

## 專案簡介


### 緣由

data.gov.tw 有提供全站資料集的資料集
[http://data.gov.tw/node/6564](http://data.gov.tw/node/6564) 政府資料開放平臺資料集清單
有這份資料就可以做些有趣的分析

### 要解決的問題

以下是天馬行空的發想
- 分析類
    - 分析那些 metadata 是否有錯、漏
        - 已經有人反應該 dataset 很髒 [https://www.facebook.com/groups/odtwn/permalink/1621411874539891/?comment\_id=1624639327550479&comment\_tracking=%7B%22tn%22%3A%22R%22%7D](https://www.facebook.com/groups/odtwn/permalink/1621411874539891/?comment_id=1624639327550479&comment_tracking=%7B%22tn%22%3A%22R%22%7D)
> 很髒應該是過去式啦~~~XD
> [name=Leo C]

    - 定期掃描統計那些外連的 link 是否可用、網路速度如何
> 平台有這功能哦，不過目前只通知資料提供者
> [name=Leo C]

    - 檢查資料是否如宣稱的頻率更新
> 這項有檢核困難，因資料提供方式不一，若採抽換檔案型態將難以比對；API、SOAP等型態亦難以確認其更新頻率是否吻合
> [name=Leo C]

> 可以從易於檢核的開始做 :)
> [name=Kuang-che W]

    - 統計資料格式類別(big5? pdf/jpg? 網頁而非 structure data?)
> 目前會內立場是以UTF-8作為主要推廣格式，雖然我覺得這塊宣導要很久...
> [name=Leo C]

> 我完全理解且同意不強推 UTF-8, 只是仍透過統計來突顯、製造一點壓力
> [name=Kuang-che W]

    - 自動偵測或手動 label 哪些是 bad opendata practice?
        - 譬如 pdf 內是圖檔
            - [http://data.gov.tw/node/11040](http://data.gov.tw/node/11040) rar -> pdf -> 掃描圖檔
        - 譬如 csv 內放 html ([例](http://data.gov.tw/node/6935))
        - "資料公開" 也拿來當 "開放資料". 這例子太多了.
            - 只是若想全站檢視可能要定義怎麼不算開放資料, 我不確定是否有辦法明確界定
> 我個人想要用"資料集品質評鑑機制"把這塊殺光光...XD
> [name=Leo C]

> 但長官不允許orz 已經開好hackpad，再給我點時間整理...orz
> [name=Leo C]

    - 統計網站上 "我還想要" 的回覆速度及通過比例?
        - 不過這要另外 crawl 網站, 可能還要人工判讀
> 回覆速度這已有系統自動勾稽哦，不過回覆完怎麼處理真的就要靠人工了...
> [name=Leo C]

    - 針對特定資料類別, 可能可以作更細部的檢查
        - 譬如 [https://g0v.hackpad.com/oI2cydKYnYy](https://g0v.hackpad.com/oI2cydKYnYy) 檢查缺乏公司統編欄位
        - 電話、座標、時間等結構化欄位是否格式正確
- 增加更多功能, 提供其他 service
    - 全站 mirror 到 github ?
> 目前已有提供CSV格式可dump到github
> [name=Leo C]

> 希望是自動化定期備份, 而不只是單次 dump
> [name=Kuang-che W]

> 這樣感覺是需要API?
> [name=Leo C]

> 現在已經有固定 url 就夠, 所以不一定需要新的 API. 不過說到 API, 是否有提供得知資料上次更新時間?
> [name=Kuang-che W]

> 目前沒有orz 因為資料型態實在太多太雜，有整包更新含歷史資料的、有不斷追加新檔然後砍舊檔的、有只留最新版本其他通通砍掉的... API的話，若要提供前次更新時間.....hmm... 
> [name=Leo C]

> 聽起來要先在 metadata 多一個欄位標記該資料是上述哪一種 XD
> [name=Kuang-che W]

    - 提供 advanced search
> 現在搜尋結果可搭配左側機關、分類、檔案格式進行多重條件篩選，要怎樣更advanced歡迎提出哦~
> [name=Leo C]

    - 讓 user 自行加 label, 評分, star 等功能
> 已經有針對最高評價標籤投票的功能哦，不滿意可以自建，採投票權重制。
> [name=Leo C]

> 不過前提是要先登入帳號才有這個功能...XD
> [name=Leo C]

> 如果我是重度使用者的話, 我會想要設自己才能看到的 label, 有自己的分類方式(譬如有個 label 叫爛 data XD), 方便過濾. 不過這種功能使用率恐怕很低, 不見得真的值得做.
> [name=Kuang-che W]

> 相當客製化的功能... 我當初甚至有在想網頁瀏覽習慣要不要也要客製化一下，但被駁回XDrz
> [name=Leo C]

    - data.gov.tw 有「資料集統計」功能(page view, download count, etc) r及其他基本分類統計, 也許可以玩視覺化
> 這塊後臺做了不少... 感覺應該全開放才對，怕VM不夠力動不動就塞爆就是XDrz
> [name=Leo C]



### 預定使用者

（成品要給誰用、在什麼場合用、怎麼用）
1.  分析的結果可以讓大家了解現在資料品質, 也可反饋給 data.gov.tw 團隊作為改善目標
2.  也許可以做 data.gov.tw clone 提供額外的功能, 方便 data 使用者


### 預定功能

（成品要有哪些功能來滿足上述使用情境）

### 現有類似專案

（現成的是否可以直接使用？或者有什麼不足之處？國外專案可參考？）
- [https://github.com/g0v-data/](https://github.com/g0v-data/) 有些 data.gov.tw backup
- 之前 ronnywang 有做過類似 data.gov.tw clone, 我忘了網址
- [http://sheethub.com/](http://sheethub.com/)
- 之前已經不只一人抱怨甚至統計過 data.gov.tw 的資料品質, 不過似乎只有單次統計. 若能持續監控更好.
- 發現國發會已經有類似計畫了 [https://www.facebook.com/groups/odtwn/permalink/1599788303368915/](https://www.facebook.com/groups/odtwn/permalink/1599788303368915/)

### 相關專案

（衍生自某專案/衍生出某專案/API串接自某專案.）

### 授權方式

Apache 2

### 使用資料

[http://data.gov.tw/node/6564](http://data.gov.tw/node/6564)

### 專案目前狀態

構想


## 徵求協作者


發起人/拋磚人：kcwu
其實我只是丟丟想法, 大家可以繼續發想/撿去做


## 實作細節（非技術背景可跳填）


### 協作工具

- github repo：



## 成果展示（規劃文件、雛形/草稿、原型/初稿、正式發佈/完稿）


