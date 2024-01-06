---
title: "台灣人口統計資料整理"
tags: hackpad
---

# 台灣人口統計資料整理

> [點此觀看原始內容](https://g0v.hackpad.tw/xqnTZmdXJW5)

kirby 提議的坑

目標：人口是常用資料，希望蒐集歷史 / 即時人口統計數據，行政區愈細愈好
> 我覺得性別跟年齡結構也蠻重要的
> [name=Richard H]

> 是的，性別和年齡維度會是下一波優先調查重點，下列資料庫部分檔案就有包含這些欄位，有興趣的話要不要點進去一起清查？
> [name=venev]

> [https://g0v.hackpad.com/p6mANPV1Bb7](https://g0v.hackpad.com/p6mANPV1Bb7)
> [name=Chen C]

> 我之前有提出以里為基礎、各級行政區用運算的方式做全台人口計算平台
> [name=Chen C]

1.  放上 data.g0v.tw 作為其他專案的基礎建設或參考資料
2.  希望做成台灣人口時空變化的視覺化圖表

todos
1.  先清點目前政府已提供資料，找出質量較好的來源或合併既有資料
2.  詢問 data.gov.tw 或要求地方政府提供資料

## 政府已提供

> 註明：最小區劃 \- 資料統計頻率 \- 檔案格式 \- 歷史區間
> [name=venev]

### 中央

==內政部==人口資料庫 [http://www.ris.gov.tw/zh_TW/346](http://www.ris.gov.tw/zh_TW/346)
- 全國 \- 年度 \- xls - since 1946：01 村里鄰戶數及人口數(35)
> 人口數是 \*\* **全國 ****
> [name=Kirby W]

- 全國 \- 單月 \- xls - 近三年：01 戶籍人口統計速報
- 縣市 \- 年度 \- xls - since 1974：01 縣市人口按性別及五齡組(63)
- 區市鄉鎮 \- 單月 \- xls - 近一年：03 鄉鎮戶數及人口數
- 另外有提供完整資料購買方式
    - [http://www.ris.gov.tw/191](http://www.ris.gov.tw/191)
> 沒魚蝦也好...
> [name=Kirby W]


內政部統計查詢網 [http://statis.moi.gov.tw/micst/stmain.jsp?sys=100](http://statis.moi.gov.tw/micst/stmain.jsp?sys=100)
- 縣市 \- 單月 \- web / xls - since 1990（[google drive 備份](https://drive.google.com/open?id=0B4W4blozmO71SktrOWRKVkZ3cHM&authuser=0)）

內政資料開放平台 [http://data.moi.gov.tw/MoiOD/Data/DataDetail.aspx?oid=F4478CE5-7A72-4B14-B91A-F4701758328F](http://data.moi.gov.tw/MoiOD/Data/DataDetail.aspx?oid=F4478CE5-7A72-4B14-B91A-F4701758328F)
- 村里 \- 單月 \- xls - 近一年

行政院==主計處== \- PC-Axis 總體統計資料庫 - 人口統計資料夾
[http://ebas1.ebas.gov.tw/pxweb/Dialog/statfile9L.asp](http://ebas1.ebas.gov.tw/pxweb/Dialog/statfile9L.asp)
- 全國 \- 年月 \- web 表格 - since 2001

### 地方

#### 行政院==主計處== \- 縣市政府統計資料庫 -\> 點選各縣市

[http://ebas1.ebas.gov.tw/pxweb/Dialog/statfile9.asp](http://ebas1.ebas.gov.tw/pxweb/Dialog/statfile9.asp)
- 縣市 \-  年度 \- web 表格 / xls / PC-Axis - 起始年如後附（缺竹縣、苗、屏、花、澎）
    - [台北市](http://163.29.37.101/pxweb2007-tp/Dialog/varval.asp?ma=PP00016YA&ti=%A4H%A4f%A1B%B1K%AB%D7%A4%CE%A9%CA%A4%F1%A8%D2&path=/PXfile/CountyStatistics&lang=9&strList=L)（since 1968）[新北市](http://ebas1.ebas.gov.tw/pxweb2007P/Dialog/varval.asp?ma=Po0201A1A&ti=%B2{%A6%ED%A4%E1%BC%C6%A1B%A4H%A4f%B1K%AB%D7%A4%CE%A9%CA%A4%F1%A8%D2-%A6~&path=../PXfile01/County01&lang=9&strList=L&strCC=01)（1998）[基隆市](http://ebas1.ebas.gov.tw/pxweb2007P/Dialog/varval.asp?ma=Po0201A1A&ti=%B0%F2%B6%A9%A5%AB%B2%CE%ADp%A6~%B3%F8(%A6~)&path=../PXfile17/County17&lang=9&strList=L&strCC=17)（2003）
    - [桃園市](http://ebas1.ebas.gov.tw/pxweb2007P/Dialog/varval.asp?ma=Po0201A1A&ti=%B2{%A6%ED%A4%E1%BC%C6%A1B%A4H%A4f%B1K%AB%D7%A4%CE%A9%CA%A4%F1%A8%D2&path=../PXfile03/County03/&lang=9&strList=L&strCC=03)（前桃園縣，2002）新竹縣（缺）[新竹市](http://ebas1.ebas.gov.tw/pxweb2007P/Dialog/varval.asp?ma=Po0201A1A&ti=%B7s%A6%CB%A5%AB%B2%CE%ADp%B8%EA%AE%C6%AEw(%A6~)&path=../PXfile18/County18&lang=9&strList=L&strCC=18http://ebas1.ebas.gov.tw/pxweb2007P/Dialog/varval.asp?ma=Po0201A1A&ti=%B7s%A6%CB%A5%AB%B2%CE%ADp%B8%EA%AE%C6%AEw(%A6~)&path=../PXfile18/County18&lang=9&strList=L&strCC=18)（2000）
    - [南投縣](http://sta.nantou.gov.tw/pxweb/Dialog/varval.asp?ma=Po0101A1A&ti=%B2{%A6%ED%A4%E1%BC%C6%A1B%A4H%A4f%B1K%AB%D7%A4%CE%A9%CA%A4%F1%A8%D2&path=../PXfile/Nantou/Abstract/&lang=9&strList=L)（1999）
- 縣市 \- 單月 \- web 表格 / xls / PC-Axis - 起始年如後附
    - [台北市](http://163.29.37.101/pxweb2007-tp/Dialog/varval.asp?ma=PP00002M&ti=%A4g%A6a%A4H%A4f%B7%A7%AAp&path=/PXfile/CountyStatistics&lang=9&strList=L)（1998）
    - [嘉義縣](http://townweb.cyhg.gov.tw/pxweb/Dialog/varval.asp?ma=Po0301A1M&ti=%B9%C5%B8q%BF%A4%AD%AB%ADn%B2%CE%ADp%B8%EA%AE%C6%AEw%ACd%B8%DF%A8t%B2%CE&path=../PXfile/CountyStatistics&lang=9&Flag=Q)（2012/7）
    - 其他縣市從缺，但可參考內政部統計查詢網資料
- 區鄉鎮市 \- 年度 \- web 表格 / xls / PC-Axis
    - [台北市](http://163.29.37.101/pxweb2007-tp/Dialog/varval.asp?ma=PP00016DA&ti=%A4H%A4f%A1B%B1K%AB%D7%A4%CE%A9%CA%A4%F1%A8%D2&path=/PXfile/CountyStatistics&lang=9&strList=L)（since 1990）[新北市](http://ebas1.ebas.gov.tw/pxweb2007P/Dialog/varval.asp?ma=Po0201A1A&ti=%B2{%A6%ED%A4%E1%BC%C6%A1B%A4H%A4f%B1K%AB%D7%A4%CE%A9%CA%A4%F1%A8%D2-%A6~&path=../PXfile01/County01&lang=9&strList=L&strCC=01)（1998）[基隆市](http://ebas1.ebas.gov.tw/pxweb2007P/Dialog/varval.asp?ma=Po0201A1A&ti=%B0%F2%B6%A9%A5%AB%B2%CE%ADp%A6~%B3%F8(%A6~)&path=../PXfile17/County17&lang=9&strList=L&strCC=17)（2003）
    - [桃園市](http://ebas1.ebas.gov.tw/pxweb2007P/Dialog/varval.asp?ma=Po0201A1A&ti=%B2{%A6%ED%A4%E1%BC%C6%A1B%A4H%A4f%B1K%AB%D7%A4%CE%A9%CA%A4%F1%A8%D2&path=../PXfile03/County03/&lang=9&strList=L&strCC=03)（前桃園縣，2002）新竹縣（缺）[新竹市](http://ebas1.ebas.gov.tw/pxweb2007P/Dialog/varval.asp?ma=Po0201A1A&ti=%B7s%A6%CB%A5%AB%B2%CE%ADp%B8%EA%AE%C6%AEw(%A6~)&path=../PXfile18/County18&lang=9&strList=L&strCC=18http://ebas1.ebas.gov.tw/pxweb2007P/Dialog/varval.asp?ma=Po0201A1A&ti=%B7s%A6%CB%A5%AB%B2%CE%ADp%B8%EA%AE%C6%AEw(%A6~)&path=../PXfile18/County18&lang=9&strList=L&strCC=18)（2000）苗栗縣（缺）
    - [大台中市](http://pxweb.taichung.gov.tw/taichung/dialog/varval.asp?ma=DPO001A&ti=%BBO%A4%A4%A5%AB%A4H%A4f%A1B%B1K%AB%D7%A4%CE%A9%CA%A4%F1%A8%D2%2D%A6%7E&path=../PXfile/D/&search=%A4H%A4f&lang=9)（2013）[前台中市](http://pxweb.taichung.gov.tw/city/dialog/varval.asp?ma=Po0201A1A&ti=%B2%7B%A6%ED%A4%E1%BC%C6%A1B%A4H%A4f%B1K%AB%D7%A4%CE%A9%CA%A4%F1%A8%D2%28%B6m%C2%ED%29%2D%A6%7E&path=../PXfile/CountyStatistics/&search=%A4H%A4f&lang=9)（1993-2010）[前台中縣](http://pxweb.taichung.gov.tw/county/dialog/varval.asp?ma=Po0201A1A&ti=%B2%7B%A6%ED%A4%E1%BC%C6%A1B%A4H%A4f%B1K%AB%D7%A4%CE%A9%CA%A4%F1%A8%D2%28%B6m%C2%ED%29%2D%A6%7E&path=../PXfile/CountyStatistics_old/&search=%A4H%A4f&lang=9)（1996-2008）[彰化縣](http://gas.chcg.gov.tw/pxweb2007p/dialog/statfile9l.asp)（缺） [南投縣](http://sta.nantou.gov.tw/pxweb/Dialog/varval.asp?ma=Po0101A1A&ti=%B2{%A6%ED%A4%E1%BC%C6%A1B%A4H%A4f%B1K%AB%D7%A4%CE%A9%CA%A4%F1%A8%D2&path=../PXfile/Nantou/Abstract/&lang=9&strList=L)（1999）
> 彰化縣完全沒有連結？可參考以下彰化縣各鄉鎮市村里鄰戶口數
> [name=venev]

    - [雲林縣](http://pxweb.yunlin.gov.tw/Pxweb2007/Dialog/varval.asp?ma=Po0201A1A&ti=%B2%7B%A6%ED%A4%E1%BC%C6%A1B%A4H%A4f%B1K%AB%D7%A4%CE%A9%CA%A4%F1%A8%D2%2D%A6%7E&path=../PXfile/CountyStatistics/&search=%A4H%A4f&lang=9)（2002）[嘉義縣](http://townweb.cyhg.gov.tw/pxweb/Dialog/varval.asp?ma=Po0201A1A&ti=%B9%C5%B8q%BF%A4%AD%AB%ADn%B2%CE%ADp%B8%EA%AE%C6%AEw%ACd%B8%DF%A8t%B2%CE&path=../PXfile/CountyStatistics&lang=9&Flag=Q)（2000）[嘉義市](http://www.chiayi.gov.tw/pxweb2007P/Dialog/varval.asp?ma=Po0201A1A&ti=%B2%7B%A6%ED%A4%E1%BC%C6%A1B%A4H%A4f%B1K%AB%D7%A4%CE%A9%CA%A4%F1%A8%D2%2D%A6%7E&path=../PXfile/CountyStatistics/&search=%A4H%A4f&lang=9)（2000）[大台南市](http://database.tainan.gov.tw/pxweb2007/dialog/varval.asp?ma=Po0203A2A&ti=%B2%7B%A6%ED%A4H%A4f%A4%A7%A6%7E%C4%D6%A4%C0%B0t%2D%A6%7E&path=../PXfile/CountyStatistics/Po%A4H%A4f/&search=%A4H%A4f&lang=9)（2011）[前台南縣](http://pxweb.tainan.gov.tw/Dialog/varval.asp?ma=Po0201A1A&ti=%B2%7B%A6%ED%A4%E1%BC%C6%A1B%A4H%A4f%B1K%AB%D7%A4%CE%A9%CA%A4%F1%A8%D2%2D%A6%7E&path=../PXfile/CountyStatistics/&search=%A4H%A4f&lang=9)（1999-2010）[前台南市](http://ebas1.ebas.gov.tw/pxweb2007P/Dialog/varval.asp?ma=Po0204A1A&ti=%B2%7B%A6%ED%A4H%A4f%A4%A7%A6%7E%C4%D6%A4%C0%B0t%2D%A6%7E&path=../PXfile21/County21/&search=%A4H%A4f&lang=9)（1999-2010）
> 大台南市及前台南市連結資料為「**現住人口之年齡分配**」，多了性別與年齡維度
> [name=venev]

    - [大高雄市](http://kcgdg1.kcg.gov.tw/pxweb2007p/Dialog/varval.asp?ma=Po010402A&ti=%B0%AA%B6%AF%A5%AB%A4%E1%C4y%B5n%B0O%A4H%A4f%A4%A7%A4%E1%B6q&path=../PXfile/CountyStatistics/%B0%AA%B6%AF%A5%AB/%A8%CC%A6~%A7O%ACd%B8%DF/%A8%CC%A6%E6%ACF%B0%CF%A7O%ACd%B8%DF/%A4H%A4f%A6%A8%AA%F8/&lang=9&strList=L)（2011）前高雄市（缺）前高雄縣（缺）屏東縣（缺）
> 高雄市不像台南、台中有改制前後的連結，直接跳到改制後
> [name=venev]

    - [宜蘭縣](http://ebas1.ebas.gov.tw/pxweb2007P/Dialog/varval.asp?ma=Po0201A1A&ti=%B2{%A6%ED%A4%E1%BC%C6%A1B%A4H%A4f%B1K%AB%D7%A4%CE%A9%CA%A4%F1%A8%D2&path=../PXfile02/County02&lang=9&strList=L&strCC=02)（1999）花蓮縣（缺）[台東縣](http://ebas1.ebas.gov.tw/pxweb2007P/Dialog/varval.asp?ma=Po0201A1A&ti=%BBO%AAF%BF%A4%BF%A4%A5%AB%B2%CE%ADp%B8%EA%AE%C6%AEw(%A6~)&path=../PXfile14/County14&lang=9&strList=L&strCC=14)（2001-2012）
    - 澎湖縣（無）[金門縣](http://www.kinmen.gov.tw/Layout/sub_A/News_NewsListAll.aspx?frame=3&DepartmentID=1&LanguageType=1&CategoryID=16)~（有連結但搜不到）~
> 金門縣是放在民政處的公告裡，已更新連結。
> [name=Chiahua W]


#### 縣市主管機關：民政局 or 民政處 -> 主計處

> 優先找中央主計處查不到的縣市主計處 -\> 主計處沒有往上游找民政局處
> [name=venev]


新竹縣主計處
- [統計年報](http://stat.hchg.gov.tw/abstract.asp)：鄉鎮市 \- 年 \- xls - 2007

苗栗縣主計處
- [統計年報](http://www.miaoli.gov.tw/accounting/normalIndex.php?frontTitleMenuID=3324&frontTitleMenuID=3324&pn=1&ps=10&pf=1)：鄉鎮市 \- 年 \- xls - 2002
- 2012年份必須要下載整份年報的zip檔

彰化縣主計處
- [各鄉鎮市村里鄰戶口數](http://www.chcg.gov.tw/accounting/07static/static01.asp?cate_id=26)：鄉鎮市 \- 月 \- xls - 2001

屏東縣
- 主計處（無相關資料）[http://www.pthg.gov.tw/planfas/index.aspx](http://www.pthg.gov.tw/planfas/index.aspx)
- 屏東縣民政處：主類別選「業務統計」（資料不全且 outdated）
    [http://www.pthg.gov.tw/plancab/PublicInfo_List.aspx?n=11070](http://www.pthg.gov.tw/plancab/PublicInfo_List.aspx?n=11070)

花蓮縣主計處
- [人口統計資料](http://static.hl.gov.tw/files/11-1054-2294.php)：鄉鎮市區 \- 單月 \- xls - 一年內


## 有點參考價值的縣級人口資料處理說明

花蓮縣歷年各鄉鎮市人口資料說明
- 本項資料係因應各界對資料需求所建立，資料來源依據花蓮縣歷年統計要覽人口資料建檔，供大眾參考使用。
- 因本縣35年統計要覽僅記載十二鄉鎮市，無光復鄉，因此無該鄉人口資料；又限於39、41、42、43、49年統計要覽格式，無法找出當年各鄉鎮市戶數。
> 這樣看起來應該有民國 35 年以來的資料（雖然光復鄉哭哭）但沒釋出？
> [name=venev]

- 本項資料僅供參考，請勿對外發表。

花蓮縣人口統計月報說明
- 資料來源：本府民政處公務統計報表「花蓮縣村里鄰戶口數與戶籍動態登記數按性別登記項目及區域分」(表號1200-00-01-2)、花蓮縣現住人口數按性別及原住民身分分(表號：1222-02-01-2)
- 人口統計資料的產生係於當月份過後，由本府民政處彙集上個月份本縣十三鄉鎮市人口資料後產生，報表產生的日期約為次月的七日左右，再交由本府主計處審核後繕打成資料檔刊載於網上供各界參考。
- 本項資料僅供參考，請勿對外發表。
> XDDDD
> [name=venev]


