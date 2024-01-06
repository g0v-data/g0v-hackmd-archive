---
title: "OpenFood project"
tags: 食品,hackpad
---

# OpenFood project

> [點此觀看原始內容](https://g0v.hackpad.tw/jArtZeaeUeL)


###  Objective


    Provide an open platform to anlaysis, upload, search the ingridient of food to let users know the details of carcinogen in foods. openfood will also connect the food information with companies, consortiums and their reputation.

### Artwork

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_629542e7bb05f495eb990288171531f5)

### Architecture


#### Client Side Software


    Provide a software for users to upload the information, photos, ingredient of food. Or **by scanning the bar code on the package of food to search / view the details** on iOS or Android.

    iOS: [https://github.com/c9s/ToxinScanner](https://github.com/c9s/ToxinScanner)

    UI Improvements
    - Use an camera view overlay to display the search result without opening another view controller to break the user flow.
    - Hide the details (2nd important information)  in the second view controller.

#### Server Side Software


    Server: [https://github.com/c9s/openfood](https://github.com/c9s/openfood)
    License: GPL
    Used major components:
        Framework: [http://github.com/c9s/Phifty](http://github.com/c9s/Phifty)
        ORM: [https://github.com/c9s/LazyRecord](https://github.com/c9s/LazyRecord)
        SQLBuilder: [https://github.com/c9s/SQLBuilder](https://github.com/c9s/SQLBuilder)
        CLIFramework: [https://github.com/c9s/CLIFramework](https://github.com/c9s/CLIFramework)

###  Schema


- Consortiums
    - Companies
        - Locality
        - Foods (with revisions)
            - name
            - EAN13 barcode
            - has-many Ingredients
        - RelatedNews (Low priority)
- Carcinogens
- Ingredients
- Symptoms
    - has-many ingredients

### Some references

- Open receipt  data from gov - [https://hackpad.com/4FMSg4Fduxk](https://hackpad.com/4FMSg4Fduxk)
- Related open data - [https://sites.google.com/site/cfttestty/project-bookmarks](https://sites.google.com/site/cfttestty/project-bookmarks)
    - 之前有一時興起挖了工廠登記資料 \- [https://github.com/kiang/twfactory/tree/master/Console/Command/data](https://github.com/kiang/twfactory/tree/master/Console/Command/data) ，不過也許未來會在 [https://data.gcis.nat.gov.tw/od/datacategory](https://data.gcis.nat.gov.tw/od/datacategory) 出現吧
    - 公司登記資料可以從 [http://gcis.nat.g0v.tw/](http://gcis.nat.g0v.tw/) 挖
- [開放食庫](https://g0v.hackpad.tw/uRTlfG5CeIt) , 在 CFT 的[開放食庫資料](https://c4t.hackpad.com/Food-Open-Data-VdT2vesI7s7)
- 食品藥物開放資料平台 [http://data.fda.gov.tw/frontsite/data/DataAction.do?method=doList&groupType=rank](http://data.fda.gov.tw/frontsite/data/DataAction.do?method=doList&groupType=rank)
    - mirror: [https://github.com/kiang/data.fda.gov.tw-list](https://github.com/kiang/data.fda.gov.tw-list)
- [食品業者登錄資料查詢](https://fadenbook.fda.gov.tw/)

> 之前我參與開放食庫 spin-off 的 project - Open Eats 的時候，團隊成員有做類似的東西 [https://openeats.hackpad.com/r4o2OpMKGY6](https://openeats.hackpad.com/r4o2OpMKGY6)
> [name=Clement T]


