---
title: "豪宅容積獎勵(開放空間)資訊開放"
tags: GIS, Open Data, 開放空間
---

# 豪宅容積獎勵(開放空間)資訊開放

> [點此觀看原始內容](https://g0v.hackpad.tw/P6O3O4vBgOe)


## 介紹

### 一、計畫緣起

我國實施「開放空間」的政策，用意在對大規模建築基地，鼓勵開發業者(建商)提供開放空間供公眾通行或休憩使用，以增加都市綠地面積及休憩活動空間，並給建商增加容積作為獎勵。公寓大樓社區的開放空間應視同公共財，供社會大眾使用。

開放空間的爭議在於，許多豪宅建商申請「蓋寬廣高樓的容積獎勵」後，卻”沒有依法開放、或將依規定應設立的開放空間告示牌藏匿於草堆中”，將依規定建築物之外，一樓周遭的步道、庭院綠地等依規定需對不特定人開放、其他的「非住戶」也都可以使用的「公共空間」，變成住戶專享的「私有庭院」(富貴路霸)。

開放空間各縣市規定互異，不過顧名思義，就是在社區規劃一處無阻礙、能夠自由通行的場域，通常是植栽綠化、人行步道，偶爾有遊憩等其他類設施，也曾包括最具爭議的『頂蓋型開放空間』（新北市一○一年改為原則不給予獎勵），例如新北市板橋區的國家世紀館，包含『沿街步道式』、『廣場式』、『頂蓋型（大廳）』，三種開放空間類型一次滿足，堪稱開放空間生活博物館（[導覽介紹圖文](https://www.facebook.com/media/set/?set=a.1515269332065179.1073741829.1511991325726313&type=1)）。

### 二、爭議案例

開放空間各縣市規定互異，不過顧名思義，就是在社區規劃一處無阻礙、能夠自由通行的場域，通常是植栽綠化、人行步道，偶爾有遊憩等其他類設施，也曾包括最具爭議的『頂蓋型開放空間』（新北市一○一年改為原則不給予獎勵）。

信義區豪宅「台北信義」 開放空間爭議
★爭議：跨年夜在開放空間的出入口處放三角錐
→北市政府回應：勸導改善，屢勸不聽再開罰
★爭議：民眾向建管處查報單位檢舉，官方卸責
→北市政府回應：因隸屬負責區域不同，才會有該現象發生，民眾只要撥1999接建管處，任一單位都會紀錄檢舉地址
★爭議：
．移動式植栽高度近300公分
．花台高度50公分
→設置灌木樹叢要低於100公分，花台高度要低於45公分，會要求管委會改善
資料來源：《蘋果》採訪整理

### 三、idea

但是知道的人不多，所以大部分的豪宅開放空間仍然很少有外人進入使用。所以，希望這些資訊能做成網頁(視覺化)或LBS APP達到真正的開放空間資訊開放。
而對這個網頁或App的想像是，可以看到就近的開放空間名稱、所在地、目前有多少民眾在那邊(在那邊的人可以用類似打卡的功能)、那個地點是否有舉辦活動(可在各地方建立活動資訊)。未來，一般民眾可以以這些法定的公共空間作為散步、野餐、靜坐、公民會議的地點。
> 4.26更新
> [name=Phoebe C]

> 轉貼到g0v後勤中心後，有人回覆以前有類似的提案與相關成果。Ronnywang 有把相關成果爬下來放到這了，感覺在稍加處理就可以做成App : [http://github.ronny.tw/](http://github.ronny.tw/ronnywang/taipei-open-space/blob/master/geojson.json)[ronnywang/taipei-open-space/blob/master/geojson.json](http://github.ronny.tw/ronnywang/taipei-open-space/blob/master/geojson.json)
> [name=Phoebe C]

> ronny 之前在hackathon 的提案: [http://ronnywang.pixnet.net/blog/post/31055893](http://ronnywang.pixnet.net/blog/post/31055893)
> [name=Phoebe C]


## TODO


### data

- [ ] ronny 已爬的資料 [https://github.com/ronnywang/taipei-open-space](https://github.com/ronnywang/taipei-open-space)
    - list.csv 來自 [臺北市建築管理工程處-開放空間專區](http://www.dba.tcg.gov.tw/lp.asp?ctNode=32471&CtUnit=17548&BaseDSD=7&mp=118021) 內 84年至99年間核發之建造執照涉有開放空間現已完工之建案名冊 的 CSV 版本
    - 討論
        - 其他年份的開放空間資料呢？
        - 其他地方政府的資料呢？
        - 開放空間：分成有涉及獎勵容積的開放空間，無涉及獎勵容積的開放空間。目前的臺北市建管處的資料，需要釐清如何認定資料中的建築物，當初有沒有涉及獎勵容積？
        - 審議的過程，相關會議記錄可能會在都市設計審議委員會會議記錄中。

### app


#### Features

- find all open spaces
- locate nearby open spaces
- check-in mechanism for each open spaces, then people could see how many people had been here, and how people use this place (photo uploading)


## 從建築「建造執照」、「使用執照」判斷的方法

台北市有將建築使用執照詳細資訊 open data ，這邊列出如何從使用執照中判斷出有包含開放空間：
(以下先從 [84年至99年間核發之建造執照涉有開放空間現已完工之建案名冊](http://dba.gov.taipei/public/Data/42610281471.xls) 找出哪些使用執照有開放空間，再去看內文是否有規則可以判斷)
- 依台北市土地使用分區管制規則第11章綜合設計放寬規定辦理
    - Ex: [https://github.com/ronnywang/tpe-building-license/blob/master/86/086使字第0006號.json](https://github.com/ronnywang/tpe-building-license/blob/master/86/086使字第0006號.json)
- 依台北市綜合設計公共開放空間管理維護執行計劃書辦理
    - Ex: [https://github.com/ronnywang/tpe-building-license/blob/master/86/086使字第0](https://github.com/ronnywang/tpe-building-license/blob/master/86/086使字第0190號.json)[1](https://github.com/ronnywang/tpe-building-license/blob/master/86/086使字第0190號.json)[9](https://github.com/ronnywang/tpe-building-license/blob/master/86/086使字第0190號.json)[0](https://github.com/ronnywang/tpe-building-license/blob/master/86/086使字第0190號.json)[號.json](https://github.com/ronnywang/tpe-building-license/blob/master/86/086使字第0190號.json)
- 使照沒有但是建照有..
    - [https://github.com/ronnywang/tpe-building-license/blob/master/86/086使字第0](https://github.com/ronnywang/tpe-building-license/blob/master/86/086使字第0317號.json)[3](https://github.com/ronnywang/tpe-building-license/blob/master/86/086使字第0317號.json)[17](https://github.com/ronnywang/tpe-building-license/blob/master/86/086使字第0317號.json)[號.json](https://github.com/ronnywang/tpe-building-license/blob/master/86/086使字第0317號.json)
        - 上面這個的建築執照是 84年建字43 ，建築執照內有寫到 "綜合設計放寬規定辦理”，看起來是使照未記錄到
        - [https://github.com/ronnywang/tpe-building-license/blob/build/84/084建字第0043號.json](https://github.com/ronnywang/tpe-building-license/blob/build/84/084建字第0043號.json)
            - 注意事項 "依台北市土地使用分區管制規則第十一章綜合設計放寬規定辦理 ."
    - [https://github.com/ronnywang/tpe-building-license/blob/master/86/086使字第03](https://github.com/ronnywang/tpe-building-license/blob/master/86/086使字第0388號.json)[8](https://github.com/ronnywang/tpe-building-license/blob/master/86/086使字第0388號.json)[8](https://github.com/ronnywang/tpe-building-license/blob/master/86/086使字第0388號.json)[號.json](https://github.com/ronnywang/tpe-building-license/blob/master/86/086使字第0388號.json)
        - 這個也是建照內有..
    -




## 參考資料

1.豪宅公共空間未開放 喊拆
[http://www.appledaily.com.tw/appledaily/article/headline/20091125/32114504/](http://www.appledaily.com.tw/appledaily/article/headline/20091125/32114504/)
2.新北6豪宅 霸地1365坪
[http://www.appledaily.com.tw/appledaily/article/headline/20130421/34967226/](http://www.appledaily.com.tw/appledaily/article/headline/20130421/34967226/)
3.〈中部〉假開放空間？ 議員要求全面清查豪宅
[http://news.ltn.com.tw/news/local/paper/627109](http://news.ltn.com.tw/news/local/paper/627109)
4.違規封開放空間　豪宅「拆玻璃、圍紅龍」 [http://news.tvbs.com.tw/entry/516510](http://news.tvbs.com.tw/entry/516510)
5.開放空間不開放 豪宅樹叢阻隔遭檢舉
[https://tw.news.yahoo.com/%E9%96%8B%E6%94%BE%E7%A9%BA%E9%96%93%E4%B8%8D%E9%96%8B%E6%94%BE-%E8%B1%AA%E5%AE%85%E6%A8%B9%E5%8F%A2%E9%98%BB%E9%9A%94%E9%81%AD%E6%AA%A2%E8%88%89-050023336.html](https://tw.news.yahoo.com/%E9%96%8B%E6%94%BE%E7%A9%BA%E9%96%93%E4%B8%8D%E9%96%8B%E6%94%BE-%E8%B1%AA%E5%AE%85%E6%A8%B9%E5%8F%A2%E9%98%BB%E9%9A%94%E9%81%AD%E6%AA%A2%E8%88%89-050023336.html)
- [https://www.facebook.com/rayscchu/posts/10203729493754203](https://www.facebook.com/rayscchu/posts/10203729493754203)
(4.27更新)
6.論 「失控」的都市容積，[http://www.twce.org.tw/twce/paper/pdf/693.pdf](http://www.twce.org.tw/twce/paper/pdf/693.pdf)
7.豪宅開放空間 圍3米植栽擋道擺三角錐封入口 民轟官方卸責
[http://www.appledaily.com.tw/appledaily/article/property/20140120/35590388/](http://www.appledaily.com.tw/appledaily/article/property/20140120/35590388/)
8.建商狠撈容積 開放空間偷走你我權益
[https://tw.house.yahoo.com/news/%E5%BB%BA%E5%95%86%E7%8B%A0%E6%92%88%E5%AE%B9%E7%A9%8D-%E9%96%8B%E6%94%BE%E7%A9%BA%E9%96%93%E5%81%B7%E8%B5%B0%E4%BD%A0%E6%88%91%E6%AC%8A%E7%9B%8A-011732825.html](https://tw.house.yahoo.com/news/%E5%BB%BA%E5%95%86%E7%8B%A0%E6%92%88%E5%AE%B9%E7%A9%8D-%E9%96%8B%E6%94%BE%E7%A9%BA%E9%96%93%E5%81%B7%E8%B5%B0%E4%BD%A0%E6%88%91%E6%AC%8A%E7%9B%8A-011732825.html)
9\. [自己的容積自己用](https://www.facebook.com/pages/自己的容積自己用/1511991325726313) fbpage
10.[【敬請開放獎勵容積之評定與核計等相關資料集】](http://data.gov.tw/node/9395)與回覆狀況
11.開放空間照片蒐集相簿：[https://goo.gl/photos/em6uqkPeAyKeZtej7](https://goo.gl/photos/em6uqkPeAyKeZtej7)
12\. 開放空間，群眾回報與 mapping 初步構想
- **mapping **
    -  已經有人開始在地圖上畫出開放空間的細節了！目前以新板特區為主，[參考 fb 貼文](https://m.facebook.com/1511991325726313/photos/a.1513482945577151.1073741828.1511991325726313/1532868566971922/?type=1&source=46)
    - 地圖：[https://www.google.com/maps/d/viewer?mid=zXWE07kTsISk.kf46Af5NEiAc](https://www.google.com/maps/d/viewer?mid=zXWE07kTsISk.kf46Af5NEiAc)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6554999ca7fd6c091d02d4b6fb9259d7)
- 拍照回報
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_da5680b98c8a4cfd0ab9bceba549cfe6)
- 地點：大安區復興南路一段303號 or 照片內的gps資訊
- 時間：20140711 上午 09：50 or 照片內的時間資訊
- 開放空間現況
- 建物名稱：道慈大樓
- 開放空間大小：@_@？不知如何估
- 能否進入：不能
- 原因：灌木圍籬阻隔
- 獎勵容積：_______%
- 經管單位：大樓管委會？
- 周邊特點：接近是大安捷運站
- 其他描述：
- 使用評論：照片裡的木座椅平台，被灌木圍起來了耶@@
- ...


都更條例修法前-前三名：△F5_1(與鄰地建物相互調和)、△F5_3(留設人行步道)、△F3(更新時程獎勵)
都更條例修法後-前三名：#14時程獎勵、#10綠建築標章之建築設計、#13建築物耐震設計
https://www.facebook.com/permalink.php?story_fbid=3746941128670845&id=100000649848605