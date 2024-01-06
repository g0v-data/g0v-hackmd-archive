---
title: "d|Bootcamp Taipei 共筆 - 資料在哪裡？"
tags: Open Data,hackpad
---

# d|Bootcamp Taipei 共筆 - 資料在哪裡？

> [點此觀看原始內容](https://g0v.hackpad.tw/s2k5iFQAS33)

時間：2015/08/21 13:00 - 14:00
講師：王向榮 / SheetHub.com 共同創辦人
##

slide: [https://docs.google.com/presentation/d/1Vj0sAq3Pe-XasfiK-Qs5hpkN9fHqy8zDU1Aokrprtr8/edit?usp=sharing](https://docs.google.com/presentation/d/1Vj0sAq3Pe-XasfiK-Qs5hpkN9fHqy8zDU1Aokrprtr8/edit?usp=sharing)
- 找資料是第一步，也是最重要的一步。之前台大新聞社的同學還帶了攜帶式的掃瞄器進中選會蒐集選舉的數據，因為這些數據網路上找不到(?)。
- 資訊公開 vs 開放資料 差別在哪呢？
    - 資訊公開：政府把資料拿出來，讓民眾看得到（但不一定適合進行後續的資料處理）
    - 開放資料：政府把資料用特定方式，使民眾可以運用資料處理技術處理資料
eg. 內政部實價登錄網站
資訊：已經做好的菜，沒有辦法選擇菜色
資料：原料，可以做出任何菜
（以肉絲炒飯及肉絲炒麵為例）
google search 可以”site:gov.tw" 只搜尋政府網站

JSON的優點：可存放較複雜的資料
缺點：檔案較大(但一定比XML小)


連結:
- 政府資料開放平台 [http://data.gov.tw/](http://data.gov.tw/)
- Google Public Data [http://www.google.com/publicdata/directory](http://www.google.com/publicdata/directory)
    - Google: "google public data"
- World Bank [http://data.worldbank.org/](http://data.worldbank.org/)
    - Google: "world bank data"
- 主計總處 [http://www.dgbas.gov.tw/mp.asp?mp=1](http://www.dgbas.gov.tw/mp.asp?mp=1)
    - Google "主計處"
- 社會經濟資料庫 [http://segis.moi.gov.tw/STAT/](http://segis.moi.gov.tw/STAT/)
    - Google "社會經濟資料庫"  --\> 社會經濟資料庫共通平台 (需註冊)
    - （這個網址才能成功註冊）[http://210.65.89.57/STATManager/Web/AccountCenter/STATManager\_AccountRegister.aspx?ProAppID=355AE105F908B29E&RedirectURL=http://210.65.89.57/STAT/Web/Platform/STAT\_PlatformHome.aspx](http://210.65.89.57/STATManager/Web/AccountCenter/STATManager_AccountRegister.aspx?ProAppID=355AE105F908B29E&RedirectURL=http://210.65.89.57/STAT/Web/Platform/STAT_PlatformHome.aspx)
    - 密碼是用明碼記
- 中選會選舉資料庫 [http://db.cec.gov.tw/](http://db.cec.gov.tw/)
    - Google "中選會資料庫"

練習範例1:
- 不動產實價登錄: [http://data.gov.tw/node/6213](http://data.gov.tw/node/6213)

練習範例2:
- [http://konklone.io/json/](http://konklone.io/json/)
    - Google 搜尋 "json to csv"
> From storymap:
> [name=Jimmy H]

> [https://s3.amazonaws.com/uploads.knightlab.com/storymapjs/bff1064d48b81f4b43a33f948cc1875d/example/published.json](https://s3.amazonaws.com/uploads.knightlab.com/storymapjs/bff1064d48b81f4b43a33f948cc1875d/example/published.json)
> [name=Jimmy H]

> from 政誌
> [name=Jimmy H]

> [http://fact.g0v.tw/wikipedia/%E8%87%BA%E7%81%A3%E9%AB%98%E4%B8%AD%E6%AD%B7%E5%8F%B2%E8%AA%B2%E7%B6%B1%E5%BE%AE%E8%AA%BF%E6%A1%88.json](http://fact.g0v.tw/wikipedia/%E8%87%BA%E7%81%A3%E9%AB%98%E4%B8%AD%E6%AD%B7%E5%8F%B2%E8%AA%B2%E7%B6%B1%E5%BE%AE%E8%AA%BF%E6%A1%88.json)
> [name=Jimmy H]

練習範例3:  擷取分析PDF文件資料
- [http://tabula.dbootcamp.taipei:8](http://tabula.dbootcamp.taipei:8)
- [080/](http://tabula.dbootcamp.taipei:8080/)
- 下載安裝 Tabula [http://tabula.technology/](http://tabula.technology/)
    - 用來把 pdf 裡面的表格資料轉化成CSV
    - 選取表格時，範圍一定要大於表格。
    - Reapeat Selection（Reapeat this Selection）功能（在選取範圍的右下角會出現），用於若每一頁表格的範圍/位置都是一樣時，可以重複選取範圍。





