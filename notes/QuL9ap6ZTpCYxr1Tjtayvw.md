---
title: "政治獻金 / 政商關係搜尋介面 mockup"
tags: CY 零時監察院,hackpad
---

# 政治獻金 / 政商關係搜尋介面 mockup

> [點此觀看原始內容](https://g0v.hackpad.tw/FbTZjGOYRUK)


＠ [8 月萌典松: moed5ct (含直播及文字轉播)](https://g0v.hackpad.tw/8-moed5ct)

## 資料來源

- 金錢報 [http://sunshine.cy.g0v.tw/](http://sunshine.cy.g0v.tw/)
    公務人員財產申報，現任或曾任[公職人員](http://law.moj.gov.tw/LawClass/LawSingle.aspx?Pcode=I0070005&FLNO=2)，目前有 2009 年以後有數位資料，1993 年以後有 pdf 檔案
- 政治獻金專戶總額 csv 檔 [https://github.com/kiang/sunshine.cy.gov.tw](https://github.com/kiang/sunshine.cy.gov.tw)  的 report2csv.csv
- 政治獻金專戶明細
    - [https://github.com/ronnywang/GovCash](https://github.com/ronnywang/GovCash)
    - [http://campaign-finance.g0v.ronny.tw/api/gettables](http://campaign-finance.g0v.ronny.tw/api/gettables)
    - [https://github.com/ihower/dcf](https://github.com/ihower/dcf)（後端資料）
        - 基於榮尼王的原始資料，進行資料正規化、分析及提供 JSON API 應用，包括根據捐贈者和廠商查詢、捐贈和支出排序....etc

## Mockup

[https://moqups.com/venev/G5De0dit/p:a592be5e1](https://moqups.com/venev/G5De0dit/p:a592be5e1)

### Home

\- 右上捷徑：SOP  -> 認領 -> 上傳 -> OCR - > 粉絲頁
- 文字搜尋框 -\> 人名、公司名
> ！通同字比對，例如 台 vs. 臺
> [name=venev]

> 萌典的全文檢索只有特例做這一對字，其他的通同字相比之下很不常見...
> [name=Audrey T]

    - 快速輸入排行榜
        - 人名：最近熱門政治人物
        - 公司名：捐贈金額排行榜？
- --
- 選單式
    - 年份：專戶年份
> 利用 [wikipedia](https://zh.wikipedia.org/wiki/Category:2013%E5%B9%B4%E5%8F%B0%E7%81%A3%E9%81%B8%E8%88%89) 對應選舉屆數與年份，例如第八屆立委與第十三屆總統副總統，同為 2012 年 / 民國 101 年大選
> [name=venev]

> ref. [wikipedia 解嚴後主要台灣選舉](http://zh.wikipedia.org/wiki/%E5%8F%B0%E7%81%A3%E9%81%B8%E8%88%89#.E8.A7.A3.E5.9A.B4.E5.BE.8C.E7.9A.84.E4.B8.BB.E8.A6.81.E8.87.BA.E7.81.A3.E9.81.B8.E8.88.89)
> [name=venev]

    - 地區：全國性 / 縣市
> 雖然有有里長、縣轄市民代表等專戶，但金額都太低；考慮最細到「縣市」即可？
> [name=venev]

    - 職務：depends on 年份、地區
        - 全國性，顯示：總統、副總統 / 立法委員
        - 縣市，顯示：
            - 縣市長 / 縣市議員
            - 鄉鎮市長 / 鄉鎮市民代表
            - 里長
> 不分區立委沒有政治專戶
> [name=venev]

- --
- footer：本專案完整連結

###  搜尋結果頁（選單）

-  擬參選人姓名作為首欄 / 考慮加入照片？
    - 年份 \- 屆數 \- 選舉層級

### 搜尋結果頁（人名）

- 資料庫無此人名（無財產申報或政治獻金專戶）-\> 查無結果，繼續搜尋
- 有此人名 ex: 丁守中
    - 公職人員財產申報
        - 有：url
        - 無 -\> 未曾申報財產
    - 參選政治獻金專戶
        - 無 -\> 未曾申請專戶
        - 有：列出歷次專戶彙總 table
            - 有專戶明細：末欄 link
            - 無專戶明細：末欄 調查兵團，我要認領 link

###  搜尋結果頁（公司名）

- 資料庫無此公司（非明細中捐贈來源、支出對象；非申報資料中股票公司、投資事業）
> 股票名稱與公司全名不一致問題？
> [name=venev]

- 有此公司名，
    - 捐出政治獻金：$______  to whom
    - 賺到政治獻金：$______  from whom
    - --
    - 股東（if上市櫃公司）事業投資人：who
> ！公職人員財產申報的股票是登記縮寫 ex: 1314 中石化 ，但政治獻金是登記全名 [中國石油化學工業開發股份有限公司](http://www.cpdc.com.tw/)
> [name=venev]

> 考慮撈證交所公開資訊觀測站「公司名 / 股號 / 公司名縮寫」對應資料
> [name=venev]

> Johnny 撈到資料了喔耶！
> [name=venev]

> [excel資料](https://github.com/thewayiam/cy/blob/master/data/xlsx/stock_symbol.xlsx)，目前一萬四千筆股票申報可辨別出一萬兩千筆，未辨識出的包含未上市櫃、以及國外的股票，以及一些比較難的，例如：台灣積電=?台積電、台塑化=?台灣塑化、中美晶...等等，可能須手動加入這些俗稱
> [name=johnny]


### 專戶明細頁

參考[目前成果](http://campaign-finance.g0v.lackneets.tw/view/%E5%90%B3%E8%82%B2%E6%98%87/%E9%9B%9C%E6%94%AF%E6%94%AF%E5%87%BA/65) ，但翻頁方式更友善（橫向的上一頁、本頁、下一頁）
往下滾動時自動載入下一頁列數


