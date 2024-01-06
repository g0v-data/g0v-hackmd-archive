---
title: "開放政治獻金 at 還我土地 hackath9n"
tags: event,CY 零時監察院,hackpad
---

# 開放政治獻金 at 還我土地 hackath9n

> [點此觀看原始內容](https://g0v.hackpad.tw/Luax4CXQgio)


## 目前成果

技術
- 葉隊長縮印術
- 榮尼王切圖術
- 鄉民肉眼OCR
網站
- kiang 任務認領區 [http://campaign-finance.g0v.olc.tw/](http://campaign-finance.g0v.olc.tw/)
- ctiml x ronnywang OCR 網站 [http://campaign-finance.g0v.ctiml.tw/](http://campaign-finance.g0v.ctiml.tw/)
- lackneets 政治獻金資料庫 [http://campaign-finance.g0v.lackneets.tw/](http://campaign-finance.g0v.lackneets.tw/)
- fuyei 政治獻金視覺化 [http://fuyei.github.io/cf-viz/viz.htm](http://fuyei.github.io/cf-viz/viz.htm)
- hackfoldr 集成 [http://hack.g0v.tw/g0v-cy](http://hack.g0v.tw/g0v-cy)
資料
- 圖檔 [http://bit.ly/ScanPoliticalContribution](http://bit.ly/ScanPoliticalContribution)（待補最初五六辦公室掃描連結）
- API [http://campaign-finance.g0v.ronny.tw/](http://campaign-finance.g0v.ronny.tw/)
- 資料下載 [https://github.com/ronnywang/GovCash](https://github.com/ronnywang/GovCash)
文件
- SOP：[純文字版](http://bit.ly/PoliticalContribution)、[圖文版](http://campaign-finance.g0v.olc.tw/sop.html)｜[SOP 2.0 即將上線](https://g0v.hackpad.tw/-SOP-dmcLmLXxXyw)
- [查閱辦法修改芻議](https://g0v.hackpad.tw/SfbYGspW4V0)
媒體
- [沃草 x 蘋果報導](http://www.appledaily.com.tw/realtimenews/article/new/20140419/382011/)（雨蒼++）
- PTT 鄉民關注：[一爆](http://www.ptt.cc/bbs/Gossiping/M.1397882086.A.6A1.html)、[二爆](http://www.ptt.cc/bbs/Gossiping/M.1398007914.A.A9F.html)、[三爆](http://www.ptt.cc/bbs/Gossiping/M.1398343408.A.1C6.html)、[四爆](http://www.ptt.cc/bbs/Gossiping/M.1399428588.A.754.html)
- 開放政治獻金粉絲頁 [http://fb.me/cy.sunshine](http://fb.me/cy.sunshine)
子龍、俞Yu 的圖像設計 [https://drive.google.com/?](https://drive.google.com/?#folders/0B0jawSySD8E3RUExTnVQdlhnMjQ)[#folders](https://g0v.hackpad.tw/ep/search/?q=%23folders&via=Luax4CXQgio)[/0B0jawSySD8E3RUExTnVQdlhnMjQ](https://drive.google.com/?#folders/0B0jawSySD8E3RUExTnVQdlhnMjQ)
- logo、標準字、icon
- facebook cover
- 監察娘
同場加映
- 監委履歷表
- 下週二公督盟記者會

## 挖坑願望

攻城獅
- 欄位內搜尋功能（參考台灣公司資料）
- 數額排序及基本計算
    - 專戶總金額、總筆數、最大額捐贈/支出、最小額捐贈/支出平均每人 / 單位 / 每筆捐贈⋯⋯
- 搜尋結果前端呈現（mockup）
    - 搜政治人物 -\> 專戶（連結該次選舉 wiki） ->
    - 搜公司 -\> 曾捐給哪些專戶
    - 結合目前視覺化成果
    - 結合台灣公司資料？搜商人 -> 持股哪些公司 -\> 曾捐給哪些專戶（個人捐贈目前有馬賽克）
    - 結合認領機制？有專戶但尚無圖檔者，直接連去認領區？
- 選區點選功能
設計師
- 搜尋結果前端美化
- SOP 2.0 圖像版文宣
言靈媒
- SOP 2.0 修潤完稿
- 芻議修改辦法文案（面向公民）
- 新任監察院

## 本日填坑

- ihower: [https://github.com/ihower/dcf](https://github.com/ihower/dcf)（後端資料，第一次填坑就上手++）
    - 基於榮尼王的原始資料，進行資料正規化、分析及提供 JSON API 應用，包括根據捐贈者和廠商查詢、捐贈和支出排序....etc
- ~mrbigmouth:~ [~http://campaign-finance.meteor.com/~](http://campaign-finance.meteor.com/) ~（前端，第一次填坑就上手++）~
    - ~將~ ~lackneet~~s~ ~政治獻金資料庫~~的網站去掉非關版面的程式碼~
    - ~準備配合ihower的後端程式，重建正規化的搜尋機制~
    - ~程式碼由於現在還要等~ ~v~~enev的~ ~mockup~ ~設計，現在等於沒有，就先不放上github了~
    - 棄用了，照venev計劃之後改成架到github上的純靜態網站
    - [http://mrbigmouth.github.io/campaign-finance/](http://mrbigmouth.github.io/campaign-finance/)
    - 新的網站設計還沒到手，先弄一下架構，把搜尋跟資料表排序、圓餅圖等功能弄了出來（其實就是套套件而已）
    - 目前完全沒有美工！ XD　等待網站設計中
- venev（推坑、版面設計、TXT）
    - 開始首頁 mockup，分「人物 / 公司名搜尋」、「選區搜尋」、「依不同層級選舉瀏覽」三種進路
    - review 列印 SOP，葉隊長 3x3 縮印術確認 OK，今晚前可完稿，考慮跟 OCR 豆腐一起發
        - 揪～竟 3x3 縮印術可以[省多少錢＆時間](https://g0v.hackpad.tw/-SOP-dmcLmLXxXyw#:h=列印速度、成本估計)呢？
- ronnywang（切豆腐）
    - 開放政治獻金 \- 資料蒐集
    - 處理最近一批豆腐，最近可以開始 OCR
- Timothy（OCR）
    - 聽說帳號系統 ready 了 ^O^
        - _需要個人成就頁面設計 <\- 視覺設計師！_

###  前後端討論

- 可能查詢用API需求
    - 輸入：無　回傳：所有目前已有資料的政治人物
    - 輸入：政治人物名稱　回傳：該政治人物名稱下的所有專戶
        - 輸入：政治人物名稱　回傳：該政治人物名稱下的概略資料(專戶總金額、總筆數、最大額捐贈/支出、最小額捐贈/支出平均每人)
    - 輸入：專戶名稱　回傳：該專戶下的概略資料(專戶總金額、總筆數、最大額捐贈/支出、最小額捐贈/支出平均每人)
        - 輸入：專戶名稱　回傳：該專戶下的每一筆資料
    - 輸入：專戶名稱、第幾筆、第幾列　回傳：該筆資料的原始圖檔網址
    - 輸入：公司名稱或商人名稱　回傳：該公司或商人捐贈的所有資料
    - 輸入：無　回傳：所有政治獻金資料，以一筆為單位，包含該筆資料的專戶名稱、政治人物名稱，兩百筆（暫定）為一頁，回傳頁數。
        - 輸入：所有政治獻金資料的所在頁數　回傳：該頁數的所有資料
        - 讓使用者大規模檢索、統計分析時使用
- 可能UPDATE API需求（？）
    - 輸入：更新人、更新政治人物、專戶名稱、資料行列數　執行：檢查權限，新增或更新資料

### JSON API


- LIsts
    - /politicians
    - /donators
    - /accounts
    - /codes
- Transactions
    - /politicians/{id}/transactions
    - /accounts/{id}/transactions
    - /donators/{id}/transactions
    - ?xxx_id=xxx  (filter)

### JSON API Example


- 政治人物列表 [http://dcf.ihower.tw/](http://dcf.ihower.tw/politicians)[politicians](http://dcf.ihower.tw/politicians)
- 政治人物 獻金明細 [http://dcf.ihower.tw/politicians/119/transactions](http://dcf.ihower.tw/politicians/119/transactions)
- 賬戶列表 [http://dcf.ihower.tw/accounts](http://dcf.ihower.tw/accounts)
- 賬戶 獻金明細 [http://dcf.ihower.tw/accounts/121/transactions](http://dcf.ihower.tw/accounts/121/transactions)
- 支出廠商排名 [http://dcf.ihower.tw/](http://dcf.ihower.tw/entities?order=payout_amount)[entitie](http://dcf.ihower.tw/entities?order=payout_amount)[s?order=payout_amount](http://dcf.ihower.tw/entities?order=payout_amount)
- 捐贈廠商排名 [http://dcf.ihower.tw/](http://dcf.ihower.tw/entities?order=income_amount)[entitie](http://dcf.ihower.tw/entities?order=income_amount)[s?order=income_amount](http://dcf.ihower.tw/entities?order=income_amount)
- 廠商獻金/支出明細 [http://dcf.ihower.tw/](http://dcf.ihower.tw/entities/19604/transactions)[entitie](http://dcf.ihower.tw/entities/19604/transactions)[s/19604/transactions](http://dcf.ihower.tw/entities/19604/transactions)

> 106.187.36.122 dcf.ihower.tw
> [name=ihower C]


## 修改請求 / 新坑發現

- lackneets：資料請不要接最新的、接 review 過的
- clkao：立委認領進度坑（ref. 葉隊長任務包，併入網站設計）
- ronnywang: 群眾外包切線檢查機制
- 需要比對總額 / 細目加總：例如黃昭順沒印支出細目
- 「個人成就頁面」需要版面設計（目前有 e-mail、輸入筆數）
- 採用立委投票指南 \> 政治獻金既有成果

