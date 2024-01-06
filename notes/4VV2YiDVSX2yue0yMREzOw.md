---
tags: 防災,EARTHQUAKE,SHELTER,hackpad
---

# 災害預防資訊平台

> [點此觀看原始內容](https://g0v.hackpad.tw/ml1Hdx1ZUeb)


### WHY?

    Summit 2016第一天才知道KNY介紹的[強震即時警報APP](http://kny.cc/post/140009881874/kny-app-taiwan-weather-eew-earthquake-early-warning)。同時，KNY也提到了消防署其實早就有製作好各縣市各鄉里的疏散避難地圖的[疏散指南](http://www.nfa.gov.tw/main/ftplist.aspx)。 如果能夠將疏散避難地圖做成一個傳送地理資訊並回傳即時的疏散方向及路線，就可以結合其它的警報APP，盡可能的降低傷亡。
    目前先著重在資訊整合。

### Respositories

- [WEB](https://github.com/jsgao0/Evacuation)
- [RESTful](https://github.com/jsgao0/EvacuationRESTful)

### TODO \[Website\] [https://evacuation-web.herokuapp.com/](https://evacuation-web.herokuapp.com/)

- [x] 收容所位置改以地圖區域性呈現
- [ ] 找出所有收容所marker的中心點
- [ ] 顯示不合格(收容所容納人數低於該里總人口數)的村里。

### TODO \[API\] [https://evacuation-restful.herokuapp.com/](https://evacuation-restful.herokuapp.com/)

- [x] 縣市列表 \[GET /counties\]
- [x] 鄉鎮列表 \[GET /:county_id/towns\]
- [x] 村里列表 \[GET /:town_id/villages\]
- [x] 村里長 \[GET /:town\_id/:village\_id/village-head\]
- [x] 村裡人口 \[GET /:town\_id/:village\_id/population\]
- [x] 收容所列表 \[GET /:town\_id/:village\_id/shelters\]
- [ ] 災害應變中心
- [ ] 消防單位
- [ ] 警察單位

### TODO \[JSON Data\]

- [x] [村里列表](https://evacuation-restful.herokuapp.com/data/villageList.json)  (更新於 2016/06/06)
- [x] [村里長列表](https://evacuation-restful.herokuapp.com/data/villageHead.json)
- [x] [村里人口列表](https://evacuation-restful.herokuapp.com/data/villagePopulation.json)
- [x] [村里預設避難收容所列表](https://evacuation-restful.herokuapp.com/data/villageFitShelterList.json)
- [ ] 消防單位列表
- [ ] 災害應變中心列表
- [ ] 警察單位列表

### TODO \[資料匯入\]

- [x] 匯入村里列表 \[已更新成[主計處資料](http://www.dgbas.gov.tw/public/data/open/stat/village.xml )\]  (更新於 2016/06/06)
- [x] 匯入[人口資料](http://data.moi.gov.tw/MoiOD/Data/DataDetail.aspx?oid=F4478CE5-7A72-4B14-B91A-F4701758328F)  \[7074\]
- [x] 匯入[避難收容所開設情形開放資料](http://data.gov.tw/node/12849) \[已補齊\] \[資料更新為上次災害，開放情形非現況\]
- [ ] 匯入[災民收容所資料](http://data.gov.tw/node/6943)
- [x] 匯入[村里長資料](http://data.gov.tw/node/7061)  \[7243\]
- [ ] 匯入[各地區消防單位及災害應變中心資料](http://data.gov.tw/node/5969) TBC: 消防分隊管轄、區域災害應變中心確認
- [ ] 匯入[各地區警察單位資料](https:// http://data.gov.tw/node/5958) TBC: 警察單位管轄範圍確認
- [ ] 新增資料表紀錄各個資料來源、更新日期

### TODO \[BUGs\]

- [ ] 人口、避難收容所、里長沒資料時，頁面資料不更新。

### TODO \[OTHERS\]

- [ ] 比較消防及警察單位與[為民服務通訊錄](http://data.gov.tw/node/gov/resource/2853)之差異。
- [ ] 疏散路線計算，[距離](http://www.movable-type.co.uk/scripts/latlong.html)、是否開設。
- [ ] 地震發生後最怕掉落物傷人，市區高樓建築多，震完馬上跑到戶外會不會反而造成民眾受傷? \[[LINK](https://www.facebook.com/groups/g0v.general/permalink/990110464398693/?comment_id=991910707552002&notif_t=group_comment&notif_id=1463637350194835)\]

## History

2016/06/07 更新村里資料，亂碼問題已解決「使用主計處[最新資料](http://www.dgbas.gov.tw/public/data/open/stat/village.xml)」

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_4ac26b1dfd0113158ee4b2661eb567be)

> 資料並非真的短缺，而是中文字的配對出問題，需要手動修正村里名稱罕見字的對應才有辦法順利匯入
> [name=kiang]

> 還在找看有沒有村里代碼的人口資料。 <<< 剛才更新村里資料，檢查了一下，所有的村里名稱應該沒有亂碼了...
> [name=Jia-Siang G]

> 有需要幫忙嗎  ？
> [name=黃耀德]

> 再麻煩你處理前端囉！
> [name=Jia-Siang G]

> 亂碼問題可以參考 [https://github.com/g0v/twhgis/releases](https://github.com/g0v/twhgis/releases) 的資料，但基本上都得進一步去配對就是了
> [name=kiang]

> 昨天更新了村里名稱，已經沒有亂碼問題。但現在因為最近行政區有調整（縣市及區鄉鎮），造成村里長、人口等資料的行政區名稱與最新的行政區名稱不一致。 找出問題的方法：目前在convert, import之間加上了verify做資料一致性驗證，資料數大致上沒問題；因此可以大致斷定是前面所述的問題。 找時間再來處理吧～  謝謝你唷！
> [name=Jia-Siang G]



