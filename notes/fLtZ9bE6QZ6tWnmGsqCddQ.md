---
title: "開放都市-委員會會議記錄資料庫 API策劃"
tags: 開放都市計畫,hackpad
---

# 開放都市-委員會會議記錄資料庫 API策劃

> [點此觀看原始內容](https://g0v.hackpad.tw/QHArc116FJR)


上層 [開放都市計畫](http://hackfoldr.urbancode.tw/)

## 討論

### 使用者是誰?

> 民眾、
> [name=Richard H]

> 空間規劃設計專業者、
> [name=Richard H]

> 都市計畫專業者
> [name=Richard H]


### 使用者的需求是什麼?

> 找出特定的會議紀錄
> [name=Richard H]

> 找出特定的人相關的會議紀錄
> [name=Richard H]

> 找出有爭議的都市計畫案件
> [name=Richard H]


### 輸出的內容

> [https://www.facebook.com/groups/odtwn/permalink/1854771411203935/](https://www.facebook.com/groups/odtwn/permalink/1854771411203935/)
> [name=Richard H]

> whiski: 或許該去看一下國外關於會議記錄的慣例格式。例如，機關單位，應該不會是稱為 unit 吧
> [name=Richard H]

> 參考國外會議記錄用字，大多使用如下，可以寫在API中
> [name=Richard H]

> 會議記錄 minutes
> [name=Richard H]

> 出席的委員會成員 member in attendance // present
> [name=Richard H]

> 其他出席者 others in attendance // also present
> [name=Richard H]

> 地點 place of meeting
> [name=Richard H]


## 建置

- language: php
- framework: laravel
- GET only
- [RESTful principle](https://tw.twincl.com/programming/*641y)
    - [https://kcyeu.gitbooks.io/http-api-design-guide-tc/](https://kcyeu.gitbooks.io/http-api-design-guide-tc/)
    - [http://rettamkrad.blogspot.tw/2013/04/web-api.html](http://rettamkrad.blogspot.tw/2013/04/web-api.html)
    - [https://github.com/WhiteHouse/api-standards](https://github.com/WhiteHouse/api-standards)
    - [POST /EFF/YOU/THIS/IS/THE/RIGHT/URL - RESTFUL API DESIGN](http://blog.cloud-elements.com/post-effyouthisistherighturl-restful-api-design)
    - [418: I'M A TEAPOT, AND OTHER BAD API RESPONSES - RESTFUL API DESIGN](http://blog.cloud-elements.com/418-im-a-teapot-and-other-bad-api-responses-restful-api-design?__hstc=233546881.04b94356d08473ccd3ade1a31294bb33.1467054686266.1467835574463.1467989984747.6&__hssc=233546881.7.1467989984747&__hsfp=2578504226)
- database-end: [資料結構討論](https://g0v.hackpad.com/--CDUPc1zHil2)
- front-end: [前端策劃](https://g0v.hackpad.tw/--OukMJzcIYdy)
- 參考
```
1\. data.taipei
http://data.taipei/opendata/datalist/apiAccess?scope=resourceAquire&rid=201d8ae8-dffc-4d17-ae1f-e58d8a95b162
2\. 司法陽光網
https://5fpro.github.io/raml-api-console/?raml=https://5fpro.github.io/jrf-sunny/api/index.raml
https://api.jrf.org.tw/KSH/%E5%88%91%E4%BA%8B-106-%E4%B8%8A%E6%98%93-252/verdict

```
## 應有的key

- api version
- HTTP response code
- response message
- Headers
```
content type: application/json

```
## API

- **/api**
```
msg url to api文件
```
- /api**/minutes**
```
list minutes code & url (limited by 100?)
```
    - /api/minutes/**{admin}-{period}-{session}-{round}**
    - live example: [http://commission.urbancode.tw/api/minutes/TPE-O-702-1](http://commission.urbancode.tw/api/minutes/TPE-O-702-1)
```
    get minute information + cases code & url
    e.g. KHH-N-10-2
         where {admin} = KHH //高雄市
               {period} = N //改制後
               {session} = 10 //第10次
               {round} = 2 //續會
```
    - /api/minutes/{admin}-{period}-{session}-{round}/cases**/{case_code}**
    - live example: [http://commission.urbancode.tw/api/minutes/TPE-O-702-1/cases/7vBZ0h](http://commission.urbancode.tw/api/minutes/TPE-O-702-1/cases/7vBZ0h)
```
    get certain case in certain minute
```
- /api**/cases**
    - /api/cases**/{case_code}**
```
    get full progress for certain case

