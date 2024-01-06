---
title: "企業資料與汙染資料的鏈結"
tags: hackpad
---

# 企業資料與汙染資料的鏈結

> [點此觀看原始內容](https://g0v.hackpad.tw/rInrPBeYd5I)

發起人：Torrent

## 專案目的

深刻地認識企業廠場與各類汙染源之間的關係。

## TODOs

- 砍污染源資料，「列管污染源資料查詢系統」環保署：[http://prtr.epa.gov.tw/](http://prtr.epa.gov.tw/)
    - 另外找到 [https://github.com/swilsonian/pollutionscraper](https://github.com/swilsonian/pollutionscraper)
    - 已經自己寫爬蟲拉了一份下來 [https://github.com/kiang/prtr.epa.gov.tw](https://github.com/kiang/prtr.epa.gov.tw)
- Torrent已經用R寫出爬蟲程式，雖然效率有待加強，但已經可以抓下全部資料。~用excel macro寫了一個簡單的污染裁罰資料擷取程式，需要有人進一步改進及用更適合的程式達到更好的功能：~[~https://www.dropbox.com/s/0c6lgrdap6kwpak/%E7%AE%A1%E5%88%B6%E7%B7%A8%E8%99%9F%E6%B1%82%E8%A3%81%E7%BD%B0.xlsm?dl=0~](https://www.dropbox.com/s/0c6lgrdap6kwpak/%E7%AE%A1%E5%88%B6%E7%B7%A8%E8%99%9F%E6%B1%82%E8%A3%81%E7%BD%B0.xlsm?dl=0)
> 搭配企業名單與關係資料：[http://hackfoldr.org/gxv/jtG0viyVzPl](http://hackfoldr.org/gxv/jtG0viyVzPl)；公司登記資料、統一編號、上市櫃股票代碼
> [name=che l]

> 已經用R比對出統編，過一陣子上傳程式及結果。
> [name=torrentpien]

- 研讀與分析，例如日月光與污水排放事件：[http://blog.roodo.com/torrent/archives/26045216.html](http://blog.roodo.com/torrent/archives/26045216.html)
- 查詢系統資料不完備的整理與判讀：該列管未列管、已列管沒資料的統計。
- 工廠地址與google地圖的整合與彙整
- [工廠登記公示資料](http://gcis.nat.gov.tw/Fidbweb/index.jsp)
    - 爬蟲 & 資料 \- [https://github.com/kiang/twfactory/tree/master/Console/Command/data](https://github.com/kiang/twfactory/tree/master/Console/Command/data)
> 雖然有寫出爬蟲，但是要爬很久，所以已經改用 [http://data.gov.tw/node/6569](http://data.gov.tw/node/6569)
> [name=Finjon K]

    -

## 呈現 idea pool

廠場汙染源時序圖 (TimeMapper)
企業汙染大戶排行榜 ...
各種產業的污染狀況及特徵
不同地區主管機關、河川流域的工廠污染源狀況



## 汙染源資料特點

- 「列管污染源資料查詢系統」是2012年10月開放民眾查詢台灣企業各工廠的各種污染源排放狀況。
- 主要的問題在於，這裡登錄的資料是廠場為單位，例如台積電就有十幾個廠，就要彙整為同一個「台積電」，但資料庫最好也要保留個別廠場的資料，以利做更複雜的多層分析，例如新竹科學園區裡有各個半導體公司的工廠，如果資料只彙整成台積電，就沒辦法做地區、河川流域、上下風等分析。
- 資料是從各縣市包括園區管理局彙整的。污染資料如空污、水污、毒化物的數據，也需要了解採樣監測的過程與科學方法本身，盡信資料不如無資料。目前空污、水污、毒化物的資料非常粗糙，許多有列管但沒資料的現象，這個情況在美國的TRI剛設立時也是如此，後來經過社會運動的要求才慢慢完備、可信，所以現階段「列管污染源資料查詢系統」除了將污染資料下載下來，也需要整理出資料不完備的統計，以利日後監督政府。_是否能夠分析哪些資料是可信度較高，比如產品與產出污染物和現有資料做比對，然後從可信度高的下手？或是與農業區相鄰的企業著手分析_

## 需要參考企業資料的理由

- 從企業特徵瞭解污染的成因與問題，例如是否規模越大、集團結構越複雜的公司越容易污染、有國民黨黨產投資的公司是否污染程度越高等等。
- 了解企業之間的子公司、孫公司、集團關係。
- 企業之間有同名的問題。

## 其他

- USA Toxics Release Inventory (TRI) Program：[http://www2.epa.gov/toxics-release-inventory-tri-program](http://www2.epa.gov/toxics-release-inventory-tri-program)
- Find a toxic waste dump near you! ：[http://www.onearth.org/earthwire/where-art-thou-superfund?utm\_source=fb&utm\_medium=post&utm_campaign=socialmedia](http://www.onearth.org/earthwire/where-art-thou-superfund?utm_source=fb&utm_medium=post&utm_campaign=socialmedia)



