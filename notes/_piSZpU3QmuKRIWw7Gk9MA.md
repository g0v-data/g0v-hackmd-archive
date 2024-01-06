---
title: "全國重度級急救責任醫院急診即時訊息"
tags: hackpad
---

# 全國重度級急救責任醫院急診即時訊息

> [點此觀看原始內容](https://g0v.hackpad.tw/vtLwiUfYgcc)

源頭 : 衛服部網頁
URL: [http://www.mohw.gov.tw/CHT/DOMA/DM1\_P.aspx?f\_list\_no=608&fod\_list\_no=4680&doc\_no=43081](http://www.mohw.gov.tw/CHT/DOMA/DM1_P.aspx?f_list_no=608&fod_list_no=4680&doc_no=43081)
資料來源 : 各醫院網頁

## 問題

> 抱歉我從來沒有使用過這類型的網路服務，因此誤刪了原來該項的標題。請見諒。
> [name=余天佑]

> 我的問題是，從 3/29 開始\[全國重度級急救責任醫院急診即時訊息\]就無法使用了，請問還有機會修復嗎？我目前是醫療改革基金會的工作人員，該網頁資訊非常有幫助，如果能夠修復就太感謝了！
> [name=余天佑]

> fixed, influxdb 有時候會當掉，若有在使用的話可以上 [slack](http://join.g0v.today/) 通知一下XD
> [name=lanfon]

> 我真的是太感動了！多謝你們的幫助！
> [name=余天佑]


> 抱歉，又不能用了，我有嘗試連上slack 但是我寄出邀請信後沒有收到，我也不知道 頁面下方留的「沒有收到請聯絡 g0v 的 LY 」要怎麼聯絡，請問可以教我怎麼處理嗎？
> [name=余天佑]

> 另外，我在懷疑是不是我把influxdb 弄壞？（抱歉我真的外行），因位兩次當掉都發生在我按了多次zoom out以後，請問有這個可能嗎？
> [name=余天佑]

> 邀請信每十分鐘會寄一次，可以稍待一下 :)
> [name=johnny]

> 了解，不過我已經申請超過五小時，期間也換過ＥＭＡＩＬ申請，也沒有收到確認信，請問我該如何處理呢？多謝指點。
> [name=余天佑]

> 呃 是XD，一直點 zoom out 的話伺服器會有點承受不住XD...
> [name=lanfon]

> 如果需要看前幾日( or 整個月) 的資料的話，zoom out 右邊點下去可以直接選 last 7d or last 30d
> [name=lanfon]

> 真是抱歉了，造成困擾。另外請問，我可以在別的場合使用這張圖表嗎？有著作權的問題嗎？
> [name=余天佑]

> 授權是 [CC0 1.0 universal](http://creativecommons.org/publicdomain/zero/1.0/) 噢
> [name=lanfon]

> 對不起，又被我弄壞了，我真的只有按一個選單中的 last 6hour ，就開始轉圈圈了....
> [name=余天佑]

> 為了避免影響別人使用，我不會再次造成伺服器負擔（不會再亂按任何功能），請問方便再重整一次嗎？
> [name=余天佑]

> 還是抱歉。
> [name=余天佑]

> 不會XD 因為我剛好在修東西所以有可能當掉.... 不穩的部份算是需要解決的問題~
> [name=lanfon]

> 您好!我是童綜合醫院的工程師,近日發現 "全國重度級急救責任醫院急診即時訊息" 的網站童醫院消失在清單內,因本院的網站資料連線正常,所以想詢問一下是否有甚麼方法可以讓童醫院顯示於清單上.感謝!
> [name=潘郁棻]



## 目前進度

Dashboard: [http://er.mohw.g0v.tw/](http://er.mohw.g0v.tw/)
> Q1:怎樣可以save modified as default ?
> [name=Tom S]

> 現在不行，先用 export
> [name=Chia-liang K]

> Q2: hospital_sn 要改為醫院名嗎? 或者要提供對應?
> [name=Tom S]

> 我先加了一個 hack, 現在應該只剩下左上角沒有對應到名稱
> [name=Chia-liang K]

> Q3: 可否將醫院依地區或縣市排列或分組？
> [name=Dino]


## 功能許願池（許願時請盡量提供可用的資料來源）

> 10/14, 我把許願的「．」改成了 checkbox 「囗」(以方便認確該功能是否完成)
> [name=lanfon]

> 若有 github 帳號的可以逕行於[本專案的 repo](https://github.com/g0v/er.mohw) 開issue.
> [name=lanfon]

- [ ] 顯示他院轉診、老人留觀、重症急救、急症急救、一般病人等資訊（原始建議連結 [http://on.fb.me/1nHz1l9](http://on.fb.me/1nHz1l9)）

- [ ] 建議新增「急救與重症床已滿」
> 請問有哪修醫院有提供此資訊？是否有範例？
> [name=Chia-liang K]

> 應該沒有醫院會公布醫護比唷，因為評鑑的時候為了滿足評鑑要求都會「調整」。如果去看病的時候發現整層病房突然裝修或關閉，通常代表評鑑要到了。剛想到醫策會辦理的醫療評鑑的資料裡面可能會有，但是好像沒有考慮開放。
> [name=Clement T]

> 了解 急救與重症床已滿的資訊應該是政府資訊那邊才有 我再找找
> [name=蘇頌揚]


- [ ] 不知道能否顯示「急診壅塞度指標」(NEDOCS)[http://hsc.unm.edu/emermed/nedocs_fin.shtml](http://hsc.unm.edu/emermed/nedocs_fin.shtml)
    [**Mu Hsueh**](https://www.facebook.com/mu.hsueh.3)**\>** 【選中的曲線 高亮顯示】
    預設　　　：全亮
    選中(複選)：暗>>>\> 改成 亮
    未選中　　：亮>>>\> 改成 暗
    **想看清要參考的醫院，需點選多次才能關掉其他曲線>>>改成 可以直接顯示想看的曲線
> 可能要等 [Grafana opensource projet](http://grafana.org/) 增加儲存個人化dashboard 比較可以滿足大家的需求 !
> [name=Tom S]

> **想看清要參考的醫院，需點選多次才能關掉其他曲線>>>改成 可以直接顯示想看的曲線 ++
> [name=尤理衡]

> 上次跟不認識g0v的人介紹的時候 就有提到這個問題
> [name=尤理衡]

> 不知道調成這樣ok嗎, 左二就是個別醫院查詢, 可點選左上醫院代號更換
> [name=Tom S]

> ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_20649c33086c7cc5dd1613eadd707b0a)
    
> [name=Tom S]

> 我用13'的MBPR 個別會被放在第三行 有點難看到 
> [name=尤理衡]

> 然後我覺得主要應該是直覺的問題吧?
> [name=尤理衡]


- [ ] [**Mu Hsueh**](https://www.facebook.com/mu.hsueh.3)**\>** 【醫院排序 依縣市 再依人數】 點選縣市名，可顯示此區醫院情況
    例如：選取"臺北市"
    臺北市---(亮)    國泰  3(亮)    臺大  5(亮)    榮總 15(亮)
    新北市---(暗)    聯合  1(暗)   三總  2(暗)

- [ ] 急診資訊地圖 (WIP): git repo: [https://github.com/g0v/er-map](https://github.com/g0v/er-map)
    status: early development stage
    concept: 顯示最近的急診等待病床狀況
    concept: 如果結合各大醫院的急診科別資料(急診是有分科別的，不是到了急診什麼病都能看)，以及Google Map的地理圖資路程計算資料，我覺得可以進一步將資料化約成民眾可以使用的服務："急診去哪裡"，輸入需要看的科別(如果知道的話)，以及所在位置，就能提供最近距離還有病床的急診醫院推薦

> 印象中救護車有緊急醫療的相關系統在管理，建議從那邊先著手？但這塊我不熟。
> [name=Clement T]

> 如果是透過119 , 會有地區緊急醫療網負責, 所以在這個專案  等床數 vs 時間 比較重要;  但是安養中心(nursing home) 如果能有地圖顯示,  可能可以方便民眾選擇( 交通,  地理位置, 環境 etc)
> [name=Tom S]

```
如果要顯示地圖, 也許可以考慮使用這種方式看看各縣市急診待床嚴重程度
http://technicaltidbit.blogspot.tw/2013/07/choropleth-in-d3js-and-pandas-ipython.html


```
## InfluxDB 使用範例


全部醫院急診等普通病房變化 ( 病房是否持續滿床)
"select  difference(pending_ward) from /ER.+/ where  time > now() - 24h     group by time(20m)  order asc"
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ce7bcbe33118b99ea450940af1d1f953)

單一醫院查詢
"select  last(pending_ward) from "ER.0601160016" where  time > now() - 24h     group by time(1h)  order asc"
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_272e61d555fb244e9847b1ee3afe8dc2)

北區醫院待床總覽
> 是不是要弄個各區(或縣市)待床總覽 ?  另外我覺得default 用bar , stack(individual) 會比線圖要醒目, 並且左側有累積總人數, 是否突然爆滿一目了然
> [name=Tom S]

> 因為有人抱怨資料太多不易辨認，是否能增加查詢介面讓使用者選擇地點，以較近距離的醫院優先列出呢?    (像人在高雄的話，基本上不會跑到台北的醫院急診)
> [name=Chen C]

"select  last(pending_ward) from /ER\\.( 1101020018|1101100011|1301200010|0501110514|0601160016|0401180014|1101150011)/  where  time > now() - 24h     group by time(1h)  order asc"
Display  Styles:  Multiple Seres : Stack 打勾,  Stacked values "individual"  => 鼠標移到顏色區域會顯示單一醫院數值
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_3594072e88629a2209db4d58c6b1d78f)

## 使用資料

influexdb SQL語法參考文件: [http://influxdb.com/docs/v0.8/api/query_language.html](http://influxdb.com/docs/v0.8/api/query_language.html)

REST API:
[最近 24hr 等待住院狀態](http://api-beta.ly.g0v.tw:8086/db/twer/series?u=guest&p=guest&q=select%20last(pending_ward)%20as%20ward,%20DIFFERENCE(pending_ward)%20as%20ward_diff%20from%20ER%20group%20by%20hospital_sn,%20time(1h)%20where%20time%20%3E%20now()%20-%2024h): select last(pending\_ward) as ward, DIFFERENCE(pending\_ward) as ward\_diff  from ER group by hospital\_sn, time(1h) where time > now() - 24h

手動選取資料：
[http://api-beta.ly.g0v.tw:8083/](http://api-beta.ly.g0v.tw:8083/), 登入guest/guest   twer 資料庫，執行 influxdb query (SQL-like):

\[SQL 語法\]
指定醫院
- 等普通病床變化
    - select  difference(pending_ward) from "ER.1142100017" where  time > 1407542794s and time < 1407560867s     group by time(1h)  order asc
- 等加護病床變化
    - select  difference(pending_icu) from "ER.1142100017" where  time > 1407542794s and time < 1407560867s     group by time(1h)  order asc
- 普通病床等床
    - select  last(pending_ward) from "ER.0421040011" where  time > 1407542794s and time < 1407560867s     group by time(1h)  order asc
- 指定區域 (北區)
    - select  last(pending_ward) from /ER\\.(
    1101020018|1101100011|1301200010|0501110514|0601160016|0401180014|1101150011)/  where  time > now() - 24h     group by time(1h)  order asc
> 請問區域有詳細清單嘛？ex:北區有哪幾家
> [name=Bunny L]

> 見下↓ **crawler 填表**
> [name=lanfon]

> 感謝
> [name=Bunny L]





## 原始資料處理

Aggregator: [http://github.com/g0v/er.mohw](http://github.com/g0v/er.mohw), grafana branch for local changes

資料每 20 分鐘塞入 influx db, 可以如此取得：

crawler 填表：[https://ethercalc.org/twer](https://ethercalc.org/twer)
> 開始寫請先填表認領，卡關再到 irc 上求救
> [name=Chia-liang K]


請幫忙確認，並在檢驗人處填上自己 id。
- crawler 產出格式(stdout)
- 若 commandline 執行外還需要特別安裝其他東西也請註明。
> python libs: requests ((其他應該可以直接import
> [name=lanfon]

- 若醫院提供欄位有多或少也請註明
> 台大醫院有「等待掛號人數」
> [name=Chia-liang K]

### 格式應為：

```
{
  full_reported : true,        // (bool) 向119通報滿床, null 表示未提供
  hospital_sn   : "0439010518" // (string) 醫院代號 length = 10
  pending_doctor: 0,           // (integer) 等待看診人數
  pending_bed   : 0,           // (integer) 等待推床人數
  pending_ward  : 0,           // (integer) 等待住院人數
  pending_icu   : 0,           // (integer) 等待加護病床人數
  update_time   : 1407206929   // (timestamp) null 表示原始資料未提供
}

```
資料格式 : (很多都不是JSON, 而是單純HTML table)
    醫院代號 : 1434020015   ( ~integer~  string )
    更新日期 (update_time)： 2014/08/03 23:44:14 (~Date~ timestamp)
    向119通報滿床 (full_reported): 是/否 ( bool )
    等待看診人數 (pending_doctor) : ( integer )
    等待推床人數 (pending_bed): ( integer )
    等待住院人數 (pending_ward) : ( integer )
    等待加護病床人數 (pending_icu): ( integer )

## layout

### 產出預期成效:

1.  讓民眾得知目前各重症醫院 "擁塞" 程度
2.  重大疾病爆發時間時, 各重症醫院承受程度

## issues and talks

FB g0v 討論區 [https://www.facebook.com/groups/g0v.general/660961490646927/?notif_t=like](https://www.facebook.com/groups/g0v.general/660961490646927/?notif_t=like)

capture\_time: ( or named grab\_time ?)
> 還是應該是叫 crawling time XDDD or needn't this key(?
> [name=lanfon]

> repo 開在 [https://github.com/lanfon72/twER_liveboard](https://github.com/lanfon72/twER_liveboard) (小更新要edit 1x 個 gist 網頁實在是太痛苦了...)
> [name=lanfon]

> 目前有問題的是 print 的 json 要用\[{ key:value }\] , 還是直接 { key:value } ? ((感覺是直接用{}....
> [name=lanfon]

> fix as {...}
> [name=lanfon]


Hospital_sn:
> Hosptial_SN(醫院代號) 有數字 0 開頭, 先用 str 了
> [name=lanfon]

> 資料應該還有個 hospital_sn.. 補上去
> [name=CornGuo]

> SN or sn ? QQ, and I use uppercase ICU QQQQQ ( bcz it's means " Intensive Care Unit " .
> [name=lanfon]

> 其實我也不確定大小寫有沒有慣例.. Orz
> [name=CornGuo]

> 看來是都用小寫XD 只好改小寫了QQQ
> [name=lanfon]


> 醫院代號對照表及地址或座標？
> [name=Chia-liang K]

> [http://www.nhi.gov.tw/webdata/webdata.aspx?menu=20&menu\_id=712&webdata\_id=660](http://www.nhi.gov.tw/webdata/webdata.aspx?menu=20&menu_id=712&webdata_id=660), 當中的 [http://www.nhi.gov.tw/Resource/webdata/8568\_1\_hospbsc.zip](http://www.nhi.gov.tw/Resource/webdata/8568_1_hospbsc.zip) 可能要extract , 裡面格式 (分局別,醫事機構代碼,醫事機構名稱,機構地址,電話區域號碼 ,電話號碼,特約類別,型態別,醫事機構種類,終止合約或歇業日期)
> [name=Tom S]

> "重度" 醫療院所, 都是通過醫院評鑑, 所以變動大約一年一次
> [name=Tom S]

> 醫事機構代碼 = 代號 (exp :"1","1434020015","財團法人羅許基金會羅東博愛醫院","宜蘭縣羅東鎮南昌街８１、８３號及站前南路６１、６３號","03","9543131","2","01","A","") 
> [name=Tom S]

> [http://data.gov.tw/node/6143](http://data.gov.tw/node/6143) 只有地址電話，沒有代號
> [name=Chia-liang K]

> 請問 [昕迪 李](https://g0v.hackpad.com/ep/profile/A93H5P2uBrp) 是不是有處理過這份資料？
> [name=Chia-liang K]

> 剛剛砍到 有用到工人智慧 [https://gist.github.com/mcdlee/a3a7d55767e6f26fec44](https://gist.github.com/mcdlee/a3a7d55767e6f26fec44)
> [name=昕迪 李]

> 從 nhi.gov.tw parse 出來的醫院名稱和代號 [http://cornguo.nlplab.tw/temp/hospital/parsed.txt](http://cornguo.nlplab.tw/temp/hospital/parsed.txt)
> [name=CornGuo]

> 光田醫療社團法人光田綜合醫院 只查得到一個代號
> [name=CornGuo]

> 有些 wiki 有 ((呃啊不過都填完了....
> [name=lanfon]

> 醫院代號有 0 開頭和英文字母開頭，也有中間夾英文的，或許定成 string 比較好 (?)
> [name=CornGuo]

> 咦咦咦咦?! (((完全沒注意
> [name=lanfon]

> btw, 榮總的網站有點妙 →→ [http://www.vghtpe.gov.tw/ser.html](http://www.vghtpe.gov.tw/ser.html) ←←
> [name=lanfon]

> 怎麼個妙法 @@?
> [name=CornGuo]

> 無法理解包兩次  iframe 的用意XD... btw, 因為沒時間可以爬所以...update_time = ' per ten mins '
> [name=lanfon]

> 喔喔.. 我看到的好你拆出來的 iframe url，原來要看原始網頁 XD
> [name=CornGuo]

> 我猜大概是所有 content 都用 iframe 包 html，然後剛好那一頁又放了另外一個 iframe 指到別的地方去 ww
> [name=CornGuo]

> 表格怪怪的... 三總我剛沒爬........(au 說起來要爬就以就跳過惹..) 但格子裡面有東西QAQQQ
> [name=lanfon]

> 表格歪掉了.. Orz
> [name=CornGuo]

> 用工人智慧整理一下好了
> [name=CornGuo]

> 看來只有幾格歪掉，現在應該正常了?
> [name=CornGuo]

> fixed~ hackpad 的表格果然不能太期待(X)
> [name=lanfon]

> 又歪掉了..  啊啊啊啊啊啊 Orz
> [name=CornGuo]

> 有種做錯動作會爆炸的感覺 QQ，已修正表格
> [name=CornGuo]

> 準備來去吃早餐惹XDDD ((留點坑給別人填 lol
> [name=lanfon]

> 剛剛發現長庚的寫一次可以用好幾次.. 囧
> [name=CornGuo]

> 我要去睡覺了 Q___Q (← 睡前看到坑就跳下去)
> [name=CornGuo]

> 應該很容易 port 到其他語言，因為幾乎都是用 regExp 硬幹..
> [name=CornGuo]

> regexp 超快XD
> [name=lanfon]

> 真的，本來在想是不是用 shell script 就可以打完收工了 XD
> [name=CornGuo]

> 好啦晚安 (?) (趴床)
> [name=CornGuo]

> 北榮網頁是敝公司多年前 (超過五年) 用 JAVA 寫的，但是架構超爛 (當年的 PM 跟 PG 也都不在了所以無從問起)，然後因為北榮都沒簽任何維護費所以那個 iframe 是他們資訊室自己自幹的樣子 XD... 
> [name=Clement T]

> 超過五年感覺很神祕..
> [name=CornGuo]

> Cornguo parse 的醫院名稱&SN 備份到 gist 上了(as [HSN.csv](https://gist.github.com/lanfon72/7eeba0344bac294664fd)) ((前面的網址用browser開會有編碼問題QQ
> [name=lanfon]


update_time:
> 有的似乎是直接顯示現在時間，所以應該要存 date retrieved & display
> [name=Chia-liang K]

> 有的沒有顯示現在時間, 反而出現"下次更新時間"
> [name=Tom S]

> 啊.. 我剛剛才發現要用 date，我的 script 是輸出 timestamp Q__Q
> [name=CornGuo]

> 來改一下貼上 gist 的 code.. QQ
> [name=CornGuo]

> timestamp is better actually
> [name=Chia-liang K]

> Hmm.. 所以要改成 timestamp 嗎?
> [name=CornGuo]

> 自問自答，看到表格上其他 commit 改成了 timestamp，那就從善如流吧
> [name=CornGuo]

> 請問有都修正成timestamp了嗎？ 我用[最近 24hr 等待住院狀態](http://api-beta.ly.g0v.tw:8086/db/twer/series?u=guest&p=guest&q=select%20last(pending_ward)%20as%20ward,%20DIFFERENCE(pending_ward)%20as%20ward_diff%20from%20ER%20group%20by%20hospital_sn,%20time(1h)%20where%20time%20%3E%20now()%20-%2024h)這個範例抓出來的timestamp超迷的...
> [name=Bunny L]

> 自問自答：timestamp看來好像是毫秒單位，所以除以1000就對了
> [name=Bunny L]


pending_icu:
> 是否有以上欄位的正式英文說法？好像有點長，我改一下簡短的
> [name=Chia-liang K]

> 好像沒有, 可能要再查看看
> [name=Tom S]

> 業內人士直接發明說法吧!
> [name=Chia-liang K]

> 業內人士先走過留下痕跡，晚些時候來補。(不好意思我是高雄人，剛交班，目前累死...請先讓我睡，明天再說..........)
> [name=淑華]

> ps.事實上可以直接從衛服部的資料庫調資料，只是我對這部分的資料後續處理完全不懂，所以還需要請資訊人才加以協助。
> [name=淑華]

> "衛服部的資料庫調資料" : 是open data 嗎 ?
> [name=Tom S]

> open data...對醫院來說是，我們內部看到的就是一個表格，上面有所有的資料。(畢竟真的出事醫院人員也沒時間去各醫院網頁看資訊啊！但重點是那個系統得登入到衛服部才看的到)
> [name=淑華]

> 但對外就是各醫院網頁所揭露的資訊這樣...所以我不知道這樣算不算是open data？
> [name=淑華]

> 對~攻城獅~工程師來說...如果是 excel 表格的話轉成 csv 就可以算是 open data (? 但重點是要開放出來....(csv算是好用格式
> [name=lanfon]

> 然後，我不知道那資料是csv還是html還是啥.....(我沒能力分辨，抱歉。)
> [name=淑華]

> 如果是登入才要的到的資料 =\> 不如直接抓網站上的, 日後還可以統計
> [name=Tom S]


iOS (native app):
ongoing: 不過遇到的第一個難題~是influxDB丟回來的json格式不對啊....~ library的問題正在查
> select all : [http://api-beta.ly.g0v.tw:8086/db/twer/series?u=guest&p=guest&q=select%20](http://api-beta.ly.g0v.tw:8086/db/twer/series?u=guest&p=guest&q=select%20)*%20from%20ER
> [name=lanfon]

> ↑ ( select * from ER
> [name=lanfon]

> or others, try on [http://api-beta.ly.g0v.tw:8083/](http://api-beta.ly.g0v.tw:8083/)
> [name=lanfon]

> 可以了，on going
> [name=Bunny L]

> ++
> [name=lanfon]

> 先這樣，其它就睡醒再說![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_edc4c21059b9badc000a07ea50e7a5fa)
    
> [name=Bunny L]


> Beta version [https://github.com/hearther/erMohw.iOS](https://github.com/hearther/erMohw.iOS)
> [name=Bunny L]





## QA（貼粉絲頁前先社群訪問共筆一下）

> 大家慢慢寫，截稿先設定週一晚間吧～
> [name=ipa c]

### 請問 Tom 發起砍柴的動念是？

tom\> 好像有一天看到醫院網站可以顯示急診等床狀況(一年前), 感覺好像可以收集起來做些什麼事.... 之後直到最近高雄氣爆事件, 發現如果能將急診塞車(塞人)的情形記錄下來, 應該很有幫助

tom> 社群在氣爆事件發生之後提了幾個有趣的問題, 並引用當時各大醫院急診待床訊息的截圖 ( [http://www.chihchih.net/2014/08/blog-post.html](http://www.chihchih.net/2014/08/blog-post.html) ).  這當中顯示出急診在平時就已經非常忙碌, 遇到重大災難, 很難有更好的機制解決問題.

### 急診資訊整合透明對現階段台灣醫療狀況的幫助？會有什麼應用？

tom\> 當重大災情(高雄氣爆)發生後,醫院急診室第一時間反應的單位. 當醫療人力不足是常態, 而急診大量傷病進入時, 就應該把資源留給緊急的病患; 不是太急的病人, 可以避開這個時段.  讓有限的醫療資源留給緊急需要的災民, 也是協助受災民眾的一種行動!  雖然衛福部已將各醫院等待住院人數的資訊聯結放在網頁上, 但使用上非常不便, 也無法讓民眾理解當下各醫院擁塞程度. 如何平時就讓民眾知道醫院負荷情形, 並且明白是否急診在特定時刻是擁擠的, 需要更好的方式呈現.

###  社群回應 (opendata 後, 拋磚引玉, 大家怎麼看?)

1\. [https://www.facebook.com/sillyduck.radiology/posts/850463091630701](https://www.facebook.com/sillyduck.radiology/posts/850463091630701) : [**I-Chen Tsai**](https://www.facebook.com/sillyduck.radiology?fref=ufi)**>** 對政策規劃者應該是個很好的工具，可以看出目前的醫療資源投入，造成患者流的哪些環節有明顯的阻滯。如果有一年四季的變化，以及各種突發事件的分析，就更深入的可以理解目前台灣醫療體系的負載。當然，前提是規劃者真的有想解決這些問題。

[**Edward Chao-Chun Kao**](https://www.facebook.com/edcckao?fref=ufi)**>** 這個網站最大的優點就是增加基礎資訊的能見度，對醫療領域不熟悉的人可能不知道這些數據的用途，但巷內人從這網站就應該能看出很多端倪，然後就可以再去尋找原因並採取行動。(ex.林口長庚的等待住院人數為何一直居高不下，等待推床人數為何突然爆增...)其次，台灣的新聞也好，政策也好，幾乎都習慣不給資料來源，一般民眾根本無法確認真偽。這樣的基礎數據除了可以提供媒體可靠且方便的資訊外，也可以讓每個人都多一個工具去查核新聞、政策、以及意見領袖的發言是否真的奠基在事實之上，還是有其他的目的。


### 有什麼進一步想像?

tom> 1. 如果醫院能提供更直接的資料, 如單一病人"急診待床時間" ([http://www.nursingcenter.com/lnc/journalarticle?Article_ID=1125043](http://www.nursingcenter.com/lnc/journalarticle?Article_ID=1125043) by [https://www.facebook.com/SuLing.Ya](https://www.facebook.com/SuLing.Ya) ) 可能可以更精確得知病床turnover 的情形, turnover 慢, 病床不夠, 護理人員不夠 都是直接影響民眾就醫權益
tom> 2. 如果可以加上 “在地" "即時" "氣溫" 的統計, 應該可以讓民眾了解, 天氣突然變化對心血管疾病的影響
tom>3. 如果政府在策略上, 把 民眾需要的 data 一直放出來, 會有事半功倍的效果. 舉個例子, 如果臺北的病人中風一段時間, 該出院了, 需要安養機構長期照顧, 如果能提供合法立案的機構即時床位資訊, 以及相關介紹, 家屬就可以很快評估到底哪一家安養中心最適合, 加快出院速度. 只要上網查就可以,略知一二, 醫院出院轉介僅提供專業照會. 而安養中心業者也必須主動加把勁提升照護品質....(而不是降低價格, 虛應評鑑)

antoniocarlos> 感謝 [Tom Shih](https://m.facebook.com/tom.shih.6?refid=52&ref=bookmark&__tn__=%2As)的發起，醫界資訊能人和g0v仙人們的協助，架構了這麼一目瞭然的全國重度急救責任醫院即時網站。

所以咧，真的再度呼籲這個政府（還有想要成為下一任政府的），高手真的都在民間，政府只要充分的開放資料，剩下的民間自己來就行。我們不會奢望要求政府部門裁員減薪，眾爺兒們您繼續喝茶看報紙看了電視才知道都無妨，只要別盡搞些有的沒的來惹麻煩就好。

### 有些人會說「作這個也沒用，反正都滿床，醫生還是動輒得咎」，對這樣的說法可以怎麼回應？（許多 open data 應用初期都會有類似評語，可以累積一些想法 XD）

> [動輒得咎](http://www.moedict.org/#動輒得咎) 的解釋
> [name=Jimmy H]

lanf0n> 單一資料或許會有此類的問題，但在資料長期累積之後，可藉由數據統計出各院急診滿床的時段和頻率，以救護車送院時的參考。避免到院時剛好處於滿床的尖峰，而因轉院延誤治療時間。
mcdlee> 求公佈各種檢傷級別的就診人數
tom> 是否可以讓含急診的區域醫院也提供即時就診人數
jimyhuang> 現在30-50歲的人，就是老人的家屬，也就是需要被廣泛知道現在醫療問題的對象，才不會自己之後沒醫療系統使用。抓bug常常並非一蹴可及，醫改也非藥到病除，何來沒用之說？

### 醫療團體有相關的改革訴求嗎？可否列舉。

ipa> （自問自答）醫勞盟曾提出訴求，呼籲政府「不應該只公布「重度級」的醫院，而是全國的急救責任醫院都該公開「急診即時訊息」！」[https://www.facebook.com/TMAL119/photos/a.118547204943363.20053.118446058286811/427292877402126/?type=1](https://www.facebook.com/TMAL119/photos/a.118547204943363.20053.118446058286811/427292877402126/?type=1)

### 是否有國外案例？

[http://www.dmc.org/ERWait/](http://www.dmc.org/ERWait/)

### 政府該做什麼協助醫療資訊公開以及促進真正的開放資料?


我覺得這個專案很有意思，其中一個可以討論的面向是"公開資訊"的影響。
舉例來說，有篇很有趣的paper討論"report cards"對病人跟醫院的影響。結論是公開資訊會讓醫院選擇醫治狀況比較好的病人，間接的使得病重的病人無法得到良好的治療。
([https://www.kellogg.northwestern.edu/faculty/satterthwaite/Research/2003-0520%20Dranove%20et%20al%20re%20Report%20Cards%20(JPE).pdf](https://www.kellogg.northwestern.edu/faculty/satterthwaite/Research/2003-0520%20Dranove%20et%20al%20re%20Report%20Cards%20(JPE).pdf))
另外，想請教一下所有的資訊都是即時的嗎，還是有歷史累積的資料呢？
(剛加入g0v，請問平時是怎麼討論的呢？)
> 多數時間都會在 irc 上討論, 可從 [這裡](http://hack.g0v.tw/irc) 登入，或是使用 irccloud 。
> [name=lanfon]

> 資料的部份，在 [http://er.mohw.g0v.tw/](http://er.mohw.g0v.tw/) (右上) 可以選擇要觀看的時間區隔，歷史資料都存在雲端XD
> [name=lanfon]

> 目前這個專案做到的部分應該還沒有到 report card (中文應該是醫療品質報告卡) 的程度。我同意如果 report card 資訊公開可能又會面臨到民眾醫療選擇時解讀資料的問題，也可預見一定會影響醫院執行醫療行為的決策。我沒仔細研究過，不知道醫策會是否已經有把醫療服務品質指標相關資料公布？若有，應該可以另開專案討論了。
> [name=Clement T]

> 不見得僅是report card的問題，我覺得所有g0v的專案都面臨著一個問題，怎麼總結專案的成效？成效本身至少能帶來兩個效果，對開發者的鼓勵跟檢示方向的正確性。
> [name=CheWei L]

> 這問題之前應該有討論過，不過目前 g0v 給我的感覺比較傾向於發現問題後先實作再說，成效是之後的事情。或許 g0v 往後會有類似 PM / QA 或比較策略性的小組 (或人) 去做一些目前成果的成效研究或規劃。然而目前應該挖坑填坑就很多事情可以做了，哈哈。
> [name=Clement T]


各位好，網站是否掛掉了，開不出來?
> backend crash, fixing.
> [name=lanfon]

> fixed.
> [name=lanfon]


