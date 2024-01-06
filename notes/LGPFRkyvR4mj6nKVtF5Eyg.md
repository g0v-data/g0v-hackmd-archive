---
tags: 電視松
---

20190428 第零次電視松 hackatv0n
====================
時間：2019-04-28 週日 14:00-18:00
地點：群島 archipiélago / 圓山花博爭艷館 [地圖](https://i.imgur.com/HZVYDzF.png)
報名連結：https://g0v-jothon.kktix.cc/events/hackatv0n
直播連結：https://meet.jit.si/hackatv0n
出席：Ronny, 丁新一, Paul, 懷碩, chihao, yoyosoco, 仔魚

預定流程：
14:00 - 14:10 報到
14:10 - 14:30 自我介紹
14:30 - 15:00 提案
15:00 - 17:30 hacking
17:30 - 18:00 成果

提案
---
* Ronny: 鄉民看電視
    * https://tvnews-logger.g0v.ronny.tw/
    * [youtube list](https://github.com/ronnywang/twtvnews/blob/master/youtube.csv)
    * [成果JSON](https://tvnews-logger.g0v.ronny.tw/index/result/ctitv/2019032818/sgh881U3xh)
    * [成果CSV](https://tvnews-logger.g0v.ronny.tw/index/result/ctitv/2019032818/sgh881U3xh?format=csv)
    * [資料](https://tw-tvnews.s3.amazonaws.com/reports/set/2019042518/data.json)
    * [短片腳本規劃](https://g0v.hackmd.io/HFGOGx42Q--qrd49ayRCsA)
* 問題回報：
    * https://tvnews-logger.g0v.ronny.tw/index/edit/ctitv/2019031812
* ipa: [鄉民看電視介紹與文案](https://g0v.hackmd.io/ygAUri2uToGbyvM-Elxu7w)
* 分數計算方式：
    * rule1: 如果超過 10% 沒處理就 -10，超過 30% 沒處理 -30，超過 50 % 沒處理 -50
    * rule2: 如果新聞區沒有加標題的話，一則 -2 分，最多 -20
    * rule3: 如果新聞區的量 < 50% ，直接 -30
    * 高於 90 分，就沒有警告，90-60 有警告，低於 60 不讓儲存


* 功能 TODO:
    * 可以切割一區段含多新聞
    * 可以合併已經有的結果
    * 登入機制

* Join平台提案
    * 標題：
        * 立即修法！Rundown 公開，全民監督新聞
        * 新聞台應公開每日新聞 Rundown
        * 修法公開新聞 Rundown，讓新聞業配文無所遁形
    * 說明：
    * 文案：

## 文獻回顧
* https://theinitium.com/article/20190424-taiwan-remote-control-war/
* [端傳媒FB版韓國瑜統計圖](https://bit.ly/2Vzssh1)
* [NCC選舉期間資料圖表](https://www.facebook.com/ncc.gov.tw/photos/a.1614467792120903/2370161096551565/?type=3&theater) 
* [沃草視覺化NCC發布107年地方公職人員選舉競選期間電視新聞報導觀察統計委託研究案](https://www.facebook.com/watchout.tw/photos/a.276078935883660/1271046333053577/?type=3&theater)


## 專案運用與活動企劃

* 舉辦FB活動：本日爛新聞大獎
    * 玩「鄉民看電視」，找出你覺得當日最荒謬的新聞
* 新聞台美食地圖
    * 玩「鄉民看電視」，ping 出每個在新聞台買業配文的餐廳
* 舉辦FB活動：本日超有國際觀大獎
    * 玩「鄉民看電視」，找出每天播報最多國家新聞的電視台
* 舉辦FB活動：最有Guts電視台獎
    * 玩「鄉民看電視」，找出什麼新聞是其他台都有報但只有一台沒報的


分享
---
* 切錯時間點：2019041012/37:21-39:24
* 開播畫面播完之後主播快速帶過「本節重點」，算「開播畫面」
* 「ending」也算「開播畫面」or「開播片頭或片尾」
* 建議：一個小時先切完、辨識完，再回去補標題
* 沒切開的話在最前面加上[多新聞]
* 

世界各地24/7 live 新聞直播

卡達半島電視台Al Jazeera
https://www.youtube.com/watch?v=fiW31uWgD2U

ABC News 24 (Australia Broadcasting Corporation)
https://www.youtube.com/watch?v=rQSwh3bgs5k

France 24 
FRANCE 24 en Direct – Info et actualités internationales en continu 24h/24
https://www.youtube.com/watch?v=3kcOfJijp3o

FRANCE 24 Live – International Breaking News & Top stories - 24/7 stream
https://www.youtube.com/watch?v=IBlUM-0NZZU

Fox News Channel(需登入)
https://www.foxnews.com/go

MSNBC
http://www.msnbc.com/msnbc-live

ABC news(網站)：American Broadcast Channel News Live
https://abcnews.go.com/Live


成果
---
### UI brainstorming
[半成品](http://172.104.104.133:5000/)
- [x] 列表
- [x] 編輯介面
    - [x] 拆分 group
    - [x] 合併 group
    - [x] header
    - [ ] 拆分 section
    - [x] 分數計算
    - [ ] 送資料到後端
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_69b98fc2e2f731c5380ebbbedc066d29)

* 目標：
    * 5/25 做好教學影片
    * 
