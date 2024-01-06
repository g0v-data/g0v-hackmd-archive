---
title: "政府公開通訊錄"
tags: kuansim,hackpad
---

# 政府公開通訊錄

> [點此觀看原始內容](https://g0v.hackpad.tw/g6v6MpyacFb)


## 來龍去脈


### 主旨

有問題要回報或是要聯絡單位的時候，提供查詢電話或地址功能

源起是[鄉民關心你](https://g0v.hackpad.com/mynkDCEAXgc)，在想要找到對的窗口的時候，需要有電話聯絡方式。後來發現其實沒有人有整理這方面的資訊，就把政府機關的聯絡方式整理成聯絡人，提供大家使用

### 牽涉領域

公家機關 | 通訊錄 | 聯絡人

### 相關組織單位

政府機關、立法委員、縣市議員

### 相關專案

- [鄉民關心你](http://hack.g0v.tw/kuansim)
- [我打了電話](http://hack.g0v.tw/kuansim/HM8MBTIU8Pp)
- [政府公開通訊錄 iOS App](http://hack.g0v.tw/kuansim/MEZ33mTjHB9)

### 授權方式

資料部份使用 CC-0 授權
程式碼部份同鄉民關心你

### 使用資料

- 政府機關單位列表 [http://oid.nat.gov.tw/infobox1/personmain.jsp](http://oid.nat.gov.tw/infobox1/personmain.jsp)
    結構解析參考 [http://data.g0v.tw/questions/11/](http://data.g0v.tw/questions/11/)
- 各地派出所 [http://data.gov.tw/opendata/Details?sno=301000000A-00001](http://data.gov.tw/opendata/Details?sno=301000000A-00001)
- 政府機關名錄 [http://www.gov.tw/orginfo/ORPF-GOV-01.aspx](http://www.gov.tw/orginfo/ORPF-GOV-01.aspx)
- 內政部消防署防救災入口網 [http://portal.ndppc.nat.gov.tw/portal/chinese/user/selectouoid.jsp](http://portal.ndppc.nat.gov.tw/portal/chinese/user/selectouoid.jsp)
- GCA [http://gca.nat.gov.tw/07-01-06.html](http://gca.nat.gov.tw/07-01-06.html)
- OID [http://oid.nat.gov.tw/OIDWeb/chmain.html](http://oid.nat.gov.tw/OIDWeb/chmain.html)
> 消防單位 ?
> [name=Superbil]

- 公文電子交換地址簿 [http://data.gov.tw/node/7617](http://data.gov.tw/node/7617) \[點CVS的超連結可以下載\]
    （之前做公文簽核系統有用到，它是應用在政府機關電子公文交換的通訊錄，其實就是個CVS檔）
- 立法委員 [g0v/addressbook.parser#3](https://github.com/g0v/addressbook.parser/issues/3)
- 國會議員 [g0v/addressbook.parser#16](https://github.com/g0v/addressbook.parser/issues/16)

> 目前要處理的需求放在 [https://github.com/g0v/addressbook.parser/issues?state=open](https://github.com/g0v/addressbook.parser/issues?state=open)
> [name=Superbil]


### 專案目前狀態

處理需求中

## 目標與功能


### 預定使用者

- 想發起人們打電話或 E-mail 給政府單位或立法委員
- 想打電話或 E-mail 給政府單位或立法委員

### 預定功能

-  資料輸入
    - Google 表單工人輸入
> 主要的資料處理完後才有可能需要
> [name=Superbil]

    - [政府機關列表](http://oid.nat.gov.tw/infobox1/personindex.jsp)
    - json
-  資料輸出
    - json 交換使用
    - vCard ?
    - 用 cardDAV 連接，即時更新資料庫
- 不提供
    - 不提供查詢電話號碼功能
    - 不提供代繳電話費
    - 不提供自動播號功能

### 使用方式

TBD

## 實做細節


### 使用技術與工具

- data
    - [parsed raw data](https://github.com/g0v/addressbook.parser)
    - [data convert from data.gov.tw](https://github.com/g0v/addressbook-data-converter)
Server
- jsDAV(webDAV only) or Radicale

PgRest Server
- parse sourcer: github.com/addressbook.parser
- backend server source: github.com/g0v/api.addressbook
- api server: [http://pgrest.io/hychen/api.addressbook/v0/collections/organizations/](http://pgrest.io/hychen/api.addressbook/v0/collections/organizations/)

### 產出檔案格式

- ~格式 (用 dictionay 儲存)~
    - ~OID~
    - ~中文名稱~
    - ~電話 *~
    - ~公司 *~
        - ~電話~
        - ~郵遞區號~
        - ~地址~
    - ~傳真~
    - ~英文名稱~
    - ~網址~
    - ~Email~
    - ~報案系統/Issue Tracking System(如果有的話)~
> 報案系統的話～可以之後再結合喲 [1.0 Citizen Police Radio CPR](https://g0v.hackpad.tw/poC9Ox6QDfB)
> [name=Ymow W]

- 格式使用 [popolo.organization](http://popoloproject.com/specs/organization.html)
> popolo 不夠用，需要再整理細項
> [name=Superbil]

    [extend popolo](https://g0v.hackpad.tw/4FYtOSv9vl6#extend-popolo)

### 資料庫

- CardDAV
- ~Database backend~
    - [~Firebase~](https://www.firebase.com/)
    - ~vCard~
    - [~pgRest~](https://github.com/clkao/pgrest)

### Mockup

- [通訊錄Mockup](https://g0v.hackpad.tw/PbgdGwk3ppL)

### 進度與 to-do

- [x] 確認現有資料來源
    - [x] 爬資料，存成 json
        - [x] 解析網址 big5 -> utf8
        - [x] 解析網址，成 dictionary
        - [x] 發出 request 解析結果，成 dictionary
        - [x] 解析儲存結果成 json
- [ ] 提供人工智彗輸入 (Google 表格)
> 在準備好現有資料來源後再準備
> [name=Superbil]

- [x] 放入資料庫
- [ ] 實作(餵給)產生 CardDAV

資料輸出
- [x] json 輸出
- [ ] ~vCard 輸出~

### 現有成果


## 開發者


### 技術指導

[HisnYi Chen](https://g0v.hackpad.tw/ep/profile/pgKgmUWKew6GVUKgrhRX7)

### 分工與成員

[Superbil](https://g0v.hackpad.tw/ep/profile/moc6aptbPH9)

## 介面

 支援 cardDAV 的 client
> 參考資料：[https://itunes.apple.com/us/app/reach-network/id570134451?mt=8](https://itunes.apple.com/us/app/reach-network/id570134451?mt=8)
> [name=Ymow W]

> iPhone iOS 6 以上都可以支援 cardDAV, OS 內建
> [name=Superbil]


