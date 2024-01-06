---
title: "環境資訊公開與監督專案"
tags: hackpad
---

# 環境資訊公開與監督專案

> [點此觀看原始內容](https://g0v.hackpad.tw/cAbxJt2yt94)

by 綠色公民行動聯盟

### 資料欄位

[https://docs.google.com/spreadsheets/d/1XaU4R6EtzCMZmKN6CdHurvMINdOYQkkbgbLJT5SQgQ8/edit#gid=0](https://docs.google.com/spreadsheets/d/1XaU4R6EtzCMZmKN6CdHurvMINdOYQkkbgbLJT5SQgQ8/edit#gid=0)

高雄市政府煙道連續監測opendata欄位：
[https://docs.google.com/spreadsheets/d/1My4nux9wZ6\_v7I\_lL8NZrSwp4ECWXa6UPl-kRGGuPDQ/edit?usp=sharing](https://docs.google.com/spreadsheets/d/1My4nux9wZ6_v7I_lL8NZrSwp4ECWXa6UPl-kRGGuPDQ/edit?usp=sharing)
> 這個格式還待確認，以高雄最後給出來為準
> [name=Tonyq W]


11月opendata工作坊記錄：
[http://beta.hackfoldr.org/1VxkIpLVa4ZK-MIFcTy7DH-Oqson14N9j2QqjlsnGYao](http://beta.hackfoldr.org/1VxkIpLVa4ZK-MIFcTy7DH-Oqson14N9j2QqjlsnGYao)

馬軍NGO分享
[https://hackpad.com/2015.09.10--lGAFJzYZmrU](https://hackpad.com/2015.09.10--lGAFJzYZmrU)



### 參考資料


中國環境團體的資料：
- [公众环境研究中心（IPE）](http://www.ipe.org.cn/pollution/corporation.aspx)
- [绿色江南公众环境关注中心（PECC）](http://www.pecc.cc/index.php/content/ent?eid=242)

公司基本資料：
- [上市櫃公司赴中國大陸投資事業名錄(1991-2013)](https://sheethub.com/ronnywang/%E4%B8%8A%E5%B8%82%E6%AB%83%E5%85%AC%E5%8F%B8%E8%B5%B4%E4%B8%AD%E5%9C%8B%E5%A4%A7%E9%99%B8%E6%8A%95%E8%B3%87%E4%BA%8B%E6%A5%AD%E5%90%8D%E9%8C%84%281991-2013%29)

其他關於企業網絡的資料：
- [https://g0v.hackpad.com/hxJBK9v7frt](https://g0v.hackpad.com/hxJBK9v7frt)
- [GuanXi ](https://g0v.hackpad.tw/5gygVb26WId)

卞中佩企業污染的資料整理：
- [http://hackfoldr.org/gxv/rInrPBeYd5I](http://hackfoldr.org/gxv/rInrPBeYd5I)

公開資訊觀測站：
[http://mops.twse.com.tw/mops/web/index](http://mops.twse.com.tw/mops/web/index)

經濟部工廠資料：
[http://gcis.nat.gov.tw/Fidbweb/index.jsp](http://gcis.nat.gov.tw/Fidbweb/index.jsp)
[Finjon Kiang](https://www.facebook.com/finjonkiang?fref=ufi): [https://wdc.gov.tw/syi.idb/](https://wdc.gov.tw/syi.idb/)

開罰紀錄：
- [http://prtr.epa.gov.tw/FacilityInfo/Data?search=False](http://prtr.epa.gov.tw/FacilityInfo/Data?search=False)
    - 拉了一份下來 [https://github.com/kiang/prtr.epa.gov.tw](https://github.com/kiang/prtr.epa.gov.tw)
- [http://prtr.epa.gov.tw/Penalty/Statistics](http://prtr.epa.gov.tw/Penalty/Statistics) (offline)
- 日月光 sample:

污染情況與即時監測：
- [需求相關已公開資料.docx](https://www.dropbox.com/s/ro2kbh6q0cxra4e/%E9%9C%80%E6%B1%82%E7%9B%B8%E9%97%9C%E5%B7%B2%E5%85%AC%E9%96%8B%E8%B3%87%E6%96%99.docx?dl=0)

### Tools / Code:

[http://docs.casperjs.org/en/latest/quickstart.html#now-let-s-scrape-google](http://docs.casperjs.org/en/latest/quickstart.html#now-let-s-scrape-google)

GIT Repo:
[https://github.com/swilsonian/pollutionscraper](https://github.com/swilsonian/pollutionscraper)



**Questions**:
- How to get keywords to search for to our script - pass in a textfile with one keyword per line?
- How to prevent duplicate data - for example, one keyword in the keywords textfile is "日月光" and another is "新日月光"?
    - This will cause duplicate rows in our csv
    - We could keep track of Entity IDs for factories in a hash table - each factory has an Entity ID
    - Before opening a factory page, check if that factory's entity ID is in our list -- If it is, don't open the factory page again
- Besides the one table, What other data needs to be retrieved from each factory page?
- Should we add a CSV row for a factory that doesn't have any table data?
- How many CSV files do we want to create? One per keyword, or one per search?
- How do the CSV(s) we create get uploaded to the final storage repo?



