---
title: "固定污染源管制地圖"
tags: hackpad
---

# 固定污染源管制地圖

> [點此觀看原始內容](https://g0v.hackpad.tw/ndUPo4GAK5N)


網址： [http://kiang.github.io/chimney_map/](http://kiang.github.io/chimney_map/)

這個計畫起源於高雄市研考會邀請 [Tonyq Wang](https://g0v.hackpad.tw/ep/profile/CJ5aesK98AN) 協助安排針對市府人員的開放資料研習營，在兩天的研習營結束後研考會透過 [Tonyq Wang](https://g0v.hackpad.tw/ep/profile/CJ5aesK98AN) 邀請參與活動的講師群一起研究他們計畫開放的固定污染源監測資料，在行政程序確認後就逐步提供了相關資料範例，目前暫時是將最新資料推送到 [Finjon Kiang](https://g0v.hackpad.tw/ep/profile/G4yGGowBe3x) 設置的 FTP ，然後透過程式自動推送到 Github 上面備份，視覺化處理則是另外開專案引用最新的資料

資料集中 repo: [https://github.com/ks-opendata-community/chimney/tree/gh-pages](https://github.com/ks-opendata-community/chimney/tree/gh-pages)
視覺化之一: [https://github.com/kiang/chimney_map](https://github.com/kiang/chimney_map)

- 目前是每小時更新一次，包含 2015/11/16 迄今的歷史資料，後續希望納入更多縣市提供的資料
- 高雄資料： [https://github.com/ks-opendata-community/chimney/tree/gh-pages/data/daily](https://github.com/ks-opendata-community/chimney/tree/gh-pages/data/daily) 的 2015 / 2016 資料夾
- 2015-12-11 加入台中的資料 - 來自 [http://220.130.204.202/program/menu/maintainhomepp2.asp](http://220.130.204.202/program/menu/maintainhomepp2.asp)
- 2016-01-01 加入宜蘭資料，來自 [http://data.gov.tw/node/25493](http://data.gov.tw/node/25493)
- 2016-01-16 加入台南與嘉義的資料，分別來自 [http://60.248.54.72/opencems/](http://60.248.54.72/opencems/) & [http://118.163.252.55/opencems/](http://118.163.252.55/opencems/)
- 2016-01-21 加入雲林資料，來自 [http://218.161.81.10/epb/CemsEPB.asp](http://218.161.81.10/epb/CemsEPB.asp)
- 2016-01-23 加入彰化資料，來自 [http://163.29.76.141/](http://163.29.76.141/)
- 2016-02-18 加入桃園資料，來自 [http://data.tycg.gov.tw/TYCG_OPD/opendata/datalist/datasetMeta?oid=5a17deb8-eb08-45a0-98e9-199e53ea7a61](http://data.tycg.gov.tw/TYCG_OPD/opendata/datalist/datasetMeta?oid=5a17deb8-eb08-45a0-98e9-199e53ea7a61)
- 2016-02-18 加入新北資料，來自 [http://data.ntpc.gov.tw/od/detail?oid=D7330AE1-5869-4EE7-8821-03B1D7D13822](http://data.ntpc.gov.tw/od/detail?oid=D7330AE1-5869-4EE7-8821-03B1D7D13822)
- 2016-02-18 加入台北與新竹資料，分別來自 [http://61.221.35.151/](http://61.221.35.151/) & [http://60.248.81.223/](http://60.248.81.223/)

### 操作簡介

[http://k.olc.tw/2015/12/%e5%9b%ba%e5%ae%9a%e6%b1%a1%e6%9f%93%e6%ba%90%e7%ae%a1%e5%88%b6%e5%9c%b0%e5%9c%96-%e4%b8%8a%e7%b7%9a/](http://k.olc.tw/2015/12/%e5%9b%ba%e5%ae%9a%e6%b1%a1%e6%9f%93%e6%ba%90%e7%ae%a1%e5%88%b6%e5%9c%b0%e5%9c%96-%e4%b8%8a%e7%b7%9a/)

### 檔案說明

- [工廠清單.csv](https://github.com/ks-opendata-community/chimney/blob/gh-pages/data/%E5%B7%A5%E5%BB%A0%E6%B8%85%E5%96%AE.csv)/ [工廠清單.json](https://github.com/ks-opendata-community/chimney/blob/gh-pages/data/%E5%B7%A5%E5%BB%A0%E6%B8%85%E5%96%AE.json)
- [項目代碼.csv](https://github.com/ks-opendata-community/chimney/blob/gh-pages/data/%E9%A0%85%E7%9B%AE%E4%BB%A3%E7%A2%BC.csv)/ [項目代碼.json](https://github.com/ks-opendata-community/chimney/blob/gh-pages/data/%E9%A0%85%E7%9B%AE%E4%BB%A3%E7%A2%BC.json)
- [警戒值.csv](https://github.com/ks-opendata-community/chimney/blob/gh-pages/data/%E8%AD%A6%E6%88%92%E5%80%BC.csv)
- [數值代碼.csv](https://github.com/ks-opendata-community/chimney/blob/gh-pages/data/%E6%95%B8%E5%80%BC%E4%BB%A3%E7%A2%BC.csv)
- [每日數值資料](https://github.com/ks-opendata-community/chimney/tree/gh-pages/data/daily)
    - 檔案會依據日期拆分到對應日期的檔案，其中高雄最新的資料會持續覆蓋 latest.csv
    - 檔案第一行會寫入該檔案代表的日期，接著則是該日對應的 unix timestamp
    - 檔案一行有五個欄位（高雄即將增加為六個），分別是 工廠管制編號、管制點代號、管制項目代號、時間與數值，高雄加入的第六個欄位則是個別數值的解讀（參考 數值代碼）

### 數據解讀(來自高雄市衛生局)


1.  高雄煙囪排放圖的氮氧化物及二氧化硫部份，每小時一次，顯示一天的濃度（ppm）。
2.  其他有用的呈現方式
    1.  累積排放量，譬如從1月1日開始到年底累積排放X公噸。
    2.  一個月或一年的排放曲線，較容易抓出有沒有在深夜偷偷排放。
3.  要計算累積排放量就需要將瞬時排放濃度（ppm）轉換成累積排放量（公斤）的轉公式，提供如下。
4.  二氧化硫（公斤/小時）=2.86×10-6*小時平均濃度（ppm）*小時平均流量（Nm3/hr）
5.  氮氧化物（公斤/小時）=2.05×10-6 *小時平均濃度（ppm）*小時平均流量（Nm3/hr）
6.  只要將一個小時、一個小時加起來即可。（中間可能有停機校正時段，應該扣除即可）
7.  119根煙囪分屬38家公司。可以用煙囪為單位，或以公司為單位，將其累積排放量做條狀圖比較。看誰是大戶，會很有趣。
8.  註：二氧化硫，SO2是酸雨的來源。氮氧化物包括二氧化氮NO2、一氧化氮NO，是工廠及汽機車的主要排放物。

參考資料：
- [硫氧化物與氮氧化物之檢測作業及計算規定](http://www1.hl.gov.tw/webplaw/data/%E9%99%84%E9%8C%84%E7%A1%AB%E6%B0%A7%E5%8C%96%E7%89%A9%E8%88%87%E6%B0%AE%E6%B0%A7%E5%8C%96%E7%89%A9%E4%B9%8B%E6%AA%A2%E6%B8%AC%E4%BD%9C%E6%A5%AD%E5%8F%8A%E8%A8%88%E7%AE%97%E8%A6%8F%E5%AE%9A.htm)

### 延伸資訊

官方新聞稿
[http://www.kcg.gov.tw/CityNews_Detail.aspx?n=F71DD73FAAE3BE82&ss=C25801ABACE4D8875D945F264220B533BF680BCC9968D082B95B4382004713D707CEBA6F56C6C93F](http://www.kcg.gov.tw/CityNews_Detail.aspx?n=F71DD73FAAE3BE82&ss=C25801ABACE4D8875D945F264220B533BF680BCC9968D082B95B4382004713D707CEBA6F56C6C93F)

相關報導
[http://news.ltn.com.tw/news/life/breakingnews/1532924](http://news.ltn.com.tw/news/life/breakingnews/1532924)
[http://www.chinatimes.com/realtimenews/20151208003259-260405](http://www.chinatimes.com/realtimenews/20151208003259-260405)
[http://www.cna.com.tw/news/ahel/201512080243-1.aspx](http://www.cna.com.tw/news/ahel/201512080243-1.aspx)
[https://video.udn.com/news/408614](https://video.udn.com/news/408614)
[http://ctee.com.tw/mobile/NowNews.aspx?ch=new&nid=20151208003259-260405](http://ctee.com.tw/mobile/NowNews.aspx?ch=new&nid=20151208003259-260405)
[http://www.peoplenews.tw/news/00cc39f4-3602-4e5e-98f0-aab010d3864c](http://www.peoplenews.tw/news/00cc39f4-3602-4e5e-98f0-aab010d3864c)
[http://newtalk.tw/news/view/2015-12-08/67711](http://newtalk.tw/news/view/2015-12-08/67711)
[http://udn.com/news/story/9/1364153](http://udn.com/news/story/9/1364153)
[http://www.cdnews.com.tw/cdnews_site/docDetail.jsp?coluid=108&docid=103484299](http://www.cdnews.com.tw/cdnews_site/docDetail.jsp?coluid=108&docid=103484299)
[http://www.tynews.com.tw/news.php?action=show&nid=157725](http://www.tynews.com.tw/news.php?action=show&nid=157725)
[http://www.chinatimes.com/realtimenews/20151209000954-260405](http://www.chinatimes.com/realtimenews/20151209000954-260405)
[http://www.bcc.com.tw/newsview.2709381](http://www.bcc.com.tw/newsview.2709381)
[http://ctee.com.tw/mobile/NowNews.aspx?nid=20151209000954-260405&ch=ch](http://ctee.com.tw/mobile/NowNews.aspx?nid=20151209000954-260405&ch=ch)
[http://www.twtimes.com.tw/index.php?page=news&nid=535605](http://www.twtimes.com.tw/index.php?page=news&nid=535605)
[http://news.ltn.com.tw/news/local/paper/939191](http://news.ltn.com.tw/news/local/paper/939191)
[http://www.tynews.com.tw/print.php?action=news&id=157742](http://www.tynews.com.tw/print.php?action=news&id=157742)
[http://udn.com/news/story/3/1363562](http://udn.com/news/story/3/1363562)

延伸
[http://www.chinatimes.com/realtimenews/20151208005308-260405](http://www.chinatimes.com/realtimenews/20151208005308-260405)

報紙報導
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_4a71bdedc3a047dba56fa76555f4ae51)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_009e0b3342cf4a31e2da1415690e36b5)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_26b395218f7f43f0399e3887d0296c2f)

