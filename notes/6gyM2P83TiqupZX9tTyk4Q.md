---
title: "高雄氣爆和登革熱爆發地圖視覺化"
tags: Issue-Mapping,hackpad
---

# 高雄氣爆和登革熱爆發地圖視覺化

> [點此觀看原始內容](https://g0v.hackpad.tw/NpPQ1UZc3Up)


### Method (proposal)

原始資料： [http://khd.kcg.gov.tw/Attachment/000001\_000401\_000001/files/1031112-%E7%99%BB%E9%9D%A9%E7%86%B1%E7%96%AB%E6%83%85%E5%BF%AB%E8%A8%8A.pdf](http://khd.kcg.gov.tw/Attachment/000001_000401_000001/files/1031112-%E7%99%BB%E9%9D%A9%E7%86%B1%E7%96%AB%E6%83%85%E5%BF%AB%E8%A8%8A.pdf)
    還有1031111....pdf  diff 兩個檔可以找到 日變化 :p
    哈: google site search : 登革熱疫情快訊 site:[http://khd.kcg.gov.tw/](http://khd.kcg.gov.tw/)
> 今天有以里為單位的數據了 只有總量沒有時序 (until 2014/11/12)
> [name=昕迪 李]

> 確診數有在下降, 不過得看看是否能將到0過冬
> [name=Tom S]

> machine readable data (csv)
> [name=昕迪 李]

> 徵求伐木工
> [name=昕迪 李]

> [http://dengue.kcg.gov.tw/KCGDengue/Mobile.aspx](http://dengue.kcg.gov.tw/KCGDengue/Mobile.aspx) 出現這個
> [name=昕迪 李]




- 欄位：district (區)、 village (里) 、病例數 、時間 (time)
> eg: 鳳山區, 一甲里, 43, 2014
> [name=昕迪 李]

- 視覺化工具：
    - leaflet，模仿立委選票地圖 [http://blog.yurenju.info/mlymap/#/](http://blog.yurenju.info/mlymap/#/)
> [https://github.com/yurenju/mlymap/tree/master/app](https://github.com/yurenju/mlymap/tree/master/app)
> [name=昕迪 李]

> 徵求 javascript 高手
> [name=昕迪 李]

> [Yuren Ju](https://g0v.hackpad.com/ep/profile/uvP2SEprc2r)  很 nice 的整理出每個里的 geojson
> [name=昕迪 李]

    - QGIS
Issue:
- data update?
- 人口資料 [http://cabu.kcg.gov.tw/cabu2/statis61B3.aspx](http://cabu.kcg.gov.tw/cabu2/statis61B3.aspx)

名詞 (待完善):
- 預警值: 由過去一段時間的病例數的平均值(3年、5年......)。視疾病特性可能需排除流行期的資料。超過此數值代表疫情進入流行期。
- 流行閥值:由平均值(預警值)加上一定比例的標準差。超過此值代表疫情進入高峰期。
- 範例: [腸病毒疫情週報](https://www.cdc.gov.tw/list.aspx?treeid=1F07E8862BA550CF&nowtreeid=42B3FB03A6172EF0)
> 現階段希望有疾管局針對疫情的所訂定的門檻值資料，如果能有計算方式更好。資料範圍需特別注意，例如是全國/縣市/區/鄉里，還有時間範圍。
> [name=荔枝]

> 或用相似的方式自定門檻值，會與官方不同，但至少也是種依據。
> [name=荔枝]


## 預期產出 : 作成以下 timeline 地圖

範例 : [healthmap.org/ebola/](http://healthmap.org/ebola/#timeline)[#timeline](https://g0v.hackpad.tw/ep/search/?q=%23timeline&via=NpPQ1UZc3Up)
每週定期抓資料, 含各種不同法定傳染病

有沒有辦法找到 高雄水溝蓋的map ?  如果能做水溝蓋的map 再對比 病例發生 , 不知道會不會有相關 ?
例: 高雄地下管線圖 [http://zbryikt.github.io/visualize/kh-pipe/](http://zbryikt.github.io/visualize/kh-pipe/)

#### 20141109 unconf lighting talks

- 簡報投影片: [https://www.dropbox.com/s/she63s86jv79hi5/1%E9%AB%98%E9%9B%84%E6%B0%A3%E7%88%86%E7%99%BB%E9%9D%A9%E7%86%B1.pdf?dl=0](https://www.dropbox.com/s/she63s86jv79hi5/1%E9%AB%98%E9%9B%84%E6%B0%A3%E7%88%86%E7%99%BB%E9%9D%A9%E7%86%B1.pdf?dl=0)
- video: [https://www.youtube.com/watch?v=gdANo3LrWyk&feature=youtube\_gdata\_player](https://www.youtube.com/watch?v=gdANo3LrWyk&feature=youtube_gdata_player)


## Fact

### 2014 高雄氣爆事故

2014年高雄氣爆事故（又稱高雄石化氣爆事件），是2014年7月31日23時至8月1日凌晨間，發生在臺灣高雄市前鎮區與苓雅區的多起石化氣爆炸事件，經初步調查，應為丙烯爆炸所致。截至9月2日，已知有32人死亡、308人受傷，其中包括7月31日晚上約9點，接受民眾報案疑似有瓦斯洩漏而前往援助、調查的消防隊員和環保署毒災應變隊員，並造成至少包括三多一、二路、凱旋三路、一心一路等多條重要道路嚴重損壞。臺灣中油有安管中心可監測高雄市所有石化管線是否有問題（壓力變化）、中油也確實早知道管線有問題，但當高雄市政府消防局119勤務中心多次詢問管線破損的相關狀況時，中油安管中心卻未告知，使原本可能可以阻止的氣爆發生。

### 2014 登革熱

Wikipedia [http://zh.wikipedia.org/wiki/%E9%AA%A8%E7%97%9B%E7%86%B1%E7%97%87](http://zh.wikipedia.org/wiki/%E9%AA%A8%E7%97%9B%E7%86%B1%E7%97%87)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_e686aa35f308a1b26f638bb7c304bb79)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_dd07f22e677f761220cbdf5f5eb3e8fb)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_1a4925eba36e6db123973429ff0f5a7c)
###  Question: 到底氣爆和登革熱有沒有關係 ?


> 今年東京原宿也罕見地出現登革熱病例，細節與資料待補
> [name=che l]

> [http://news.tvbs.com.tw/entry/545541](http://news.tvbs.com.tw/entry/545541)
> [name=che l]

> 國立感染症研究所檢驗後發現，代代木公園與新宿中央公園的患者，體內病毒的DNA排列是一樣的，專家認為不排除是人在擴散病毒。國立感染症研究所所長：「DNA的排列是100%一致的，我們認為是最初發生在代代木公園的(人)，把病毒帶到了新宿中央公園。」
> [name=che l]

> 公視有話好說中，與會者說日方有在研究是否因為一場大型的東南亞演藝活動，許多東南亞人員入境，而產生疫情
> [name=che l]


## Data:

###  登革熱 歷年趨勢 : 2014 特別多

[http://nidss.cdc.gov.tw/SingleDisease.aspx?pt=s&Dc=1&Dt=2&disease=061&d=1&s=determined_cnt&i=all&RK=Y](http://nidss.cdc.gov.tw/SingleDisease.aspx?pt=s&Dc=1&Dt=2&disease=061&d=1&s=determined_cnt&i=all&RK=Y)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_2b3d09fedb607b883c1a982cd1a0dca0)


### Open data: 疾管局 (每週 vs 地區)  "excel data 需要周周更新"


#### 今年趨勢 [http://nidss.cdc.gov.tw/Nidss\_Report\_Timer.aspx?Pt=s&dc=1&dt=2&disease=061&d=1&i=all&s=determined_cnt&rk=W&Y1=2014&Y2=2014&MW1=1&MW2=46&Area=07&City=07&Town=0&Q=H&mr=1](http://nidss.cdc.gov.tw/Nidss_Report_Timer.aspx?Pt=s&dc=1&dt=2&disease=061&d=1&i=all&s=determined_cnt&rk=W&Y1=2014&Y2=2014&MW1=1&MW2=46&Area=07&City=07&Town=0&Q=H&mr=1) (excel檔)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_2262cb3adaae7f6f6c598da64b0f0fdc)

CDC 已經畫了地圖 靜態地圖 (但看不出時序變化)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_541c998af7a7df0753a639da8e8e78a4)
但是民眾不容易追蹤時間和地區的變化
需要 Better map ! by @Chewei such as "google map" or "Open street map"
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ed1c77b089a7e47b0cc0f2d2b1a2c63e)

### 高雄登革熱疫情防治整合系統

資料來源 : [http://dengue.kcg.gov.tw/KCGDengue/Mobile.aspx](http://dengue.kcg.gov.tw/KCGDengue/Mobile.aspx)
    有每日每區/每里 更新資料
    問題: 用crawler 一天一天爬, data 都可以抓得下來; 但是用官網查, 只要日期拉長, 很快就當掉 server error , 不知道是怎樣 ??

#### Crawler

[isacloud](http://logbot.g0v.tw/channel/g0v.tw/2014-11-25/447)  [https://gist.github.com/youchenlee/bb3e4449b5268e1eec83](https://gist.github.com/youchenlee/bb3e4449b5268e1eec83)
mcdlee : [https://gist.github.com/mcdlee/8cf459fa3b3c490dc67d](https://gist.github.com/mcdlee/8cf459fa3b3c490dc67d)
tomstone: [https://gist.github.com/t0mst0ne/019ec211dffb954ddf6a](https://gist.github.com/t0mst0ne/019ec211dffb954ddf6a)

#### CSV 格式

mcdlee : [https://gist.github.com/mcdlee/d550b485b1684e3c33a1](https://gist.github.com/mcdlee/d550b485b1684e3c33a1)
tomstone :[https://github.com/t0mst0ne/dengue.kcg](https://github.com/t0mst0ne/dengue.kcg)   data 放在這個 Repositories中

#### Data mining

tomstone : (ipython + nbviewer) [http://nbviewer.ipython.org/github/t0mst0ne/dengue.kcg/blob/master/t0mst0ne.dengue.kcg.ipynb](http://nbviewer.ipython.org/github/t0mst0ne/dengue.kcg/blob/master/t0mst0ne.dengue.kcg.ipynb)

以下為2014 至今各里的趨勢圖: (縱軸:單日確診 , 橫軸:日期, 顏色:508個里)
    2 個peak : (1) 7月底~ 8月中   (2) 9月底 ~ 11月初
    其中 2014-07-31 ~ 2014-08-31 單日超過 6 位的里 看起來,都在氣爆附近
    - 福康里 10
    - 福人里 9
    - 瑞昌里 10
    - 福隆里 7
    - 福地里 7
    - 山明里 8 => (這個不在氣爆附近, 並且高峰在7/29 就有, 所以這個跟氣爆無關)

    2014.7.1 往後 100 days 累積個案 > 100 位的里
    以下大多不在氣爆區 , 可能跟 9月底到10約初 另一波 疫情 有關
    - 中厝里 148
    - 菜公里 119
    - 福人里 130
    - 瑞華里 108
    - 高松里 125
    - 南成里 115
    - 山明里 207

\[每日 每里 新確診\]

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_3895a32039f8c2e98873259f19dc59da)

\[每日 每里 累積確診\]

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6a4c1a1da3fbaf073b1118b661e308be)
\[ 按區域 , time series, plotly \]
[https://plot.ly/~iamtomstone/2](https://plot.ly/~iamtomstone/2)

#### Visualization : Trend + Map on server

[lycheetw](http://lycheetw.github.io/KaohsiungDengueMap/) : [http://lycheetw.github.io/KaohsiungDengueMap/](http://lycheetw.github.io/KaohsiungDengueMap/)


## Discussion

高雄氣爆時序圖 [http://timemap.kuansim.com/hychen/kaohsiung-gas-explosion](http://timemap.kuansim.com/hychen/kaohsiung-gas-explosion)
> 可是沒有data ?  還是用這個標就可以 ?
> [name=Tom S]

今天有以里為單位的數據了 只有總量沒有時序 [http://khd.kcg.gov.tw/Attachment/000001\_000401\_000001/files/1031112-%E7%99%BB%E9%9D%A9%E7%86%B1%E7%96%AB%E6%83%85%E5%BF%AB%E8%A8%8A.pdf](http://khd.kcg.gov.tw/Attachment/000001_000401_000001/files/1031112-%E7%99%BB%E9%9D%A9%E7%86%B1%E7%96%AB%E6%83%85%E5%BF%AB%E8%A8%8A.pdf)
#### 視覺化目的:

- 使用 timeline 模式 讓民眾了解今年登革熱爆發和氣爆有關係
> 看來卡關的是時序資料 是以區域為基礎  (現有的 timemap 不適合直接使用)
> [name=昕迪 李]

> [http://blog.yurenju.info/mlymap/#/](http://blog.yurenju.info/mlymap/#/) 想學這個 再加上 timeline 資訊
> [name=昕迪 李]

> 和氣爆有沒有關係可能不那麼容易判斷，因為前鎮也是往年盛行的區域
> [name=昕迪 李]

> 通報數據本身是否看的到，是由那個機構所通報，以此來 mapping ?
> [name=che l]

> 在時序圖中呈現時，通報病例會需要消失嗎？例如伊波拉的網頁就是一直加疊上去，舊的病例不會消失
> [name=che l]

> 不知道有了里的圖, 是否可以畫更細的圖 , 慕約在excel 上有按cases 多寡把顏色分深淺; 如果也是用streep map 細分然後著色(深淺 => 多寡) 也許也可以; 
> [name=Tom S]

> 可以考慮用 leaflet 畫圖，以 OpenStreetMap 作為底圖 (不過這裡底圖用什麼其實都可以)，另一個方案是用 QGIS 產生點陣圖
> [name=昕迪 李]

> [https://github.com/yurenju/mlymap/tree/master/json/twVillage1982](https://github.com/yurenju/mlymap/tree/master/json/twVillage1982) 縣市合併後的 geojson
> [name=昕迪 李]

> 要怎麼定義顏色，例如說 綠->黃->紅->紫 代表疫情由輕到重，但是threshold要怎麼定？有沒有標準可以follow
> [name=荔枝]

> 顏色如果按照疾管局 ([http://nidss.cdc.gov.tw/NIDSS\_DiseaseMap.aspx?Pt=s&dc=1&dt=2&disease=061&d=3&i=all&s=determined\_cnt&a=07](http://nidss.cdc.gov.tw/NIDSS_DiseaseMap.aspx?Pt=s&dc=1&dt=2&disease=061&d=3&i=all&s=determined_cnt&a=07)) 是有建議
> [name=Tom S]

> 0, 1-5, 6-50, 51-150, >151
> [name=Tom S]

> 仔細看過疾管局的網頁，發現他會依照地理區域or時間區間的不同而改變，推測它的顏色只是依照資料範圍內最高值&最低值做一個比例的轉換，例如把畫面轉到北區，即使人數不多也是紅色的。
> [name=荔枝]


> 我剛剛看到有2個名詞"預警值"&"流行閥值"，這比較符合我所想的，例如說黃色=預警，紅色=流行
> [name=荔枝]

> 是否能找到這2個值各是多少？此外未來也可以套用到其他疾病
> [name=荔枝]

> 這個我來問一下 CDC
> [name=Tom S]


> 做了一個概念頁面，不知道大家覺得如何？
> [name=荔枝]

> [http://lycheetw.github.io/KaohsiungDengueMap/](http://lycheetw.github.io/KaohsiungDengueMap/)
> [name=荔枝]

> 還想到了一些問題，如前面提的著色問題、或是要不要除以人口數or區域面積、如果要導入里的資料或是每日的資料，是否會因為單位資料量太小反而無法呈現效果
> [name=荔枝]

> ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c252eb9e129156a0f86c22c951104ed7)
    
> [name=荔枝]

> 超棒!, 如果點選地圖區域(區or里), 下方histogram 圖跟著變(那一區的統計), 也許可以更方便比較, 那一區的趨勢!  官網的都不會有趨勢圖(時間)
> [name=Tom S]

> 如果可以縮到 "里" , 那應該就可以結案了 !!!  
> [name=Tom S]

> 目前是可以點選每個長條來選擇時間點，也就是由histogram 區域控制map區域
> [name=荔枝]

> 如果map可以反過來控制histogram ，那麼要如何回到上一個層級(由'里'回到'區')？
> [name=荔枝]

> 學立委選票地圖新增一個回到上一層的按鈕是一種解法，但是我不太喜歡就是了
> [name=荔枝]

> 如果只做區的層級(區 目前正確性高 ; 里的名字有重複, 還不確定在哪裡可以確認) , 點 map 然後下面histogram 可以限定點的區的data, 應該就可以解決官網無法看長時間趨勢的問題;  
> [name=Tom S]

> 不知為何, CDC 和 這個網站, 地理和時間(time series) 總是湊不在一個頁面, 都得花一些工夫才能找到) 如果可以做到這樣, 那CDC 的所有疾病data 都可以clone 過來 !!
> [name=Tom S]

> 新增檢視區的histogram
> [name=荔枝]

> 超強 ++
> [name=Tom S]

> 以這個版本為基礎延伸了[台南版](http://kiang.github.io/TainanDengueMap/) 與[全台版](http://kiang.github.io/TainanDengueMap/taiwan/)
> [name=Finjon K]

- 搭配不同資料集, 協助找到疾病控制方法
    - 地下管線資料集
    - 地區雨量資料集
    - etc
- 民眾可以 "很方便" 追蹤後續發展 (疾管局網站不好查)
- 需要更明確的氣爆地圖標示
- 民眾為什麼要追蹤 ?
- 登革熱病毒4種subtype, 中2種即可發展為出血性登革熱, 死亡率非常高,目前無解藥（[疾管局登革熱介紹頁面](http://www.cdc.gov.tw/diseaseinfo.aspx?treeid=8d54c504e820735b&nowtreeid=dec84a2f0c6fac5b&tid=77BFF3D4F9CB7982)）
- 冬天通常疫情可以控制, 但今年還在上昇
- 冬天疫情若無控制, 到隔年會更嚴重
- 利用此網站呈現, 協助民眾意識
- 此模板可應用於其他疫情議題（時間＋地理分佈）

**人口密度與疫區比較** 2014/12/2
高雄的友人跟我聊到，登革熱最嚴重的是三民區，而氣爆是在苓雅區，兩者無關係。
所以就嘗試以人口密度與蚊疫地理分布區做對比，請參考下圖。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ce05bd11977863979d4d4ba2d4e799a5)
圖片中顯示出人口集中的地區以及病例分佈圖是重疊的，
列舉病例人數最高的三民、鳳山、前鎮、苓雅，以及小港五區，
可得出這五區緊密相鄰，並且人口密集，也有捷運相連接的共通點。
最後一點就是，友人稱因大量投藥的關係，高雄的蚊子抗藥性非常強，一般投藥已無效。
> 人口密度會直接影響登革熱的散波速度是一定的，所以也有稱作都市型疾病，三民區病例遠高於其他區可能是因為在該區"工作"人口密度高，所以散播的也快。另外雖然說蚊子有抗藥性，就算再加上今年碰到4~5年為週期的流行期，總覺得今年還太誇張了點([1998~2014](http://nidss.cdc.gov.tw/OutPutPic/20141202/199801201412HD050000061D2R2L1M.gif))。人口密度、抗藥性等都是長久存在的原因，無法解釋突然大爆發的現象。氣爆造成病媒蚊孳生環境變多是種可能的解釋，即使氣爆區並非最嚴重區域，但也可能是病人再把登革熱帶到三民區散播。或是說，今年是否有什麼原因造成政府無法準確投藥等???
> [name=荔枝]

> 我還想到了一個東西是今年的氣溫很高，不過還沒做到那麼多，另一個對比的提案就是當地氣溫與感染人數的時間比。我有做過氣爆管線與紅色區塊的重疊圖，管線就跟捷運線一樣；但是早在氣爆發生以前，感染人數就很多了。另外有一個很重要的原因也是我朋友說的，高雄的流氓議長率領KMT議員們將高達57億的預算砍掉了!但是我無法直接確定這兩件事的關連就是了。
> [name=Huiwen Y]

> 有一個問題還是無法解釋: 為何今年大爆發? 
> [name=Tom S]

> 1\. 如果是氣候, 那是否有證據顯示今年氣候和以往不同; 若真的有差, 為何只有在高雄? 
> [name=Tom S]

> 2\. 如果是社區老舊, 那為何過去數年滅蚊方式幾年無效?
> [name=Tom S]

> 3\. 如果是蚊子抗藥, 那可能要等CDC 研究結果才能確認
> [name=Tom S]

> 4\. 我比較擔心是地下水道/管路有新的變化讓蚊子滋生, 剛好以往滅蚊無法滅到; 如果灌海水有效, 那就更值得擔心, 因為灌海水可以一般藥物打不到的地方都填滿; 但是一旦明年連續暴雨, 又變成淡水時, 那整個地下管路又將成為新的培養環境; 
> [name=Tom S]

> 我倒是有一個比較不同的想法: 因為氣爆區域下水道被破壞，讓蚊子的棲息地改變，使得往年(可能有針對下水道噴藥)的滅蚊方式成效不彰?
> [name=荔枝]

####

**![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_b05e4d274a40bed95c21376713647de9)

**
資料來源:
1\. wiki高雄人口分布示意圖2009：
[http://zh.wikipedia.org/wiki/%E9%AB%98%E9%9B%84%E5%B8%82#mediaviewer/File:Population\_density\_map\_of\_Kaohsiung_%28Dec_2009%29.svg](http://zh.wikipedia.org/wiki/%E9%AB%98%E9%9B%84%E5%B8%82#mediaviewer/File:Population_density_map_of_Kaohsiung_%28Dec_2009%29.svg)
2\. 疾管署傳染病統計：
[http://nidss.cdc.gov.tw/NIDSS\_DiseaseMap.aspx?Pt=s&dc=1&dt=2&disease=061&d=3&i=0&s=determined\_cnt&a=07](http://nidss.cdc.gov.tw/NIDSS_DiseaseMap.aspx?Pt=s&dc=1&dt=2&disease=061&d=3&i=0&s=determined_cnt&a=07)
3\. 高雄人口數量：[http://zh.wikipedia.org/wiki/高雄市](http://zh.wikipedia.org/wiki/高雄市)
4\. 高雄行政區規劃圖：[http://upload.wikimedia.org/wikipedia/commons/9/90/Kaohsiung\_City\_Districts.png](http://upload.wikimedia.org/wikipedia/commons/9/90/Kaohsiung_City_Districts.png)

### 氣候變遷及今年氣象與發病時間的比對

依據氣象局的資料做了一些整理，溫度變化的部分是5月到6月瞬升5度，雨量部分也是5、6月比去年明顯增加，濕度部分今年4~5月是最高點。
接著看疾管局發病日的表格，在第20年週(5月)的時候發病人數開始持續出現，在第24年週(6月)開始增加。目前資料並不多，希望可以陸續增加。
- 各人假設先天因素是由於5月起的氣溫驟升以及雨量多致使濕度出現歷年最高，人為因素就是特定五區居住和工作人口密集，最後加上地理因素--即管線老舊遇上高溫多雨潮濕等。人口密集、高溫潮濕、管線老舊三種因素重疊可得出指定區域發病人數居高的假設。
- 關於管線爆炸與疫情擴散的關係是可以成立的，爆炸時間是2014/7/31，也就是第31年週，在第33年週時感染人數由137增至233人，以苓雅區居冠，往後有可能在鄰近地區交叉繁衍。可以注意的是在9月份雨量驟減加上濕度下降，在第38年週前後感染人數開始倍數成長。以上是個人推論，希望可以找出一些原因。
- 數據統計: [https://docs.google.com/spreadsheets/d/1AyGPLZ9xJcBCnieDjzJw9pXvuVbAmGkakffOtDprK0I/edit?usp=sharing](https://docs.google.com/spreadsheets/d/1AyGPLZ9xJcBCnieDjzJw9pXvuVbAmGkakffOtDprK0I/edit?usp=sharing)
> 根據 HUIWEN 的氣候資料, 2012-2014 年的溫度和雨量差異不大, 因此氣候條件相同, 但2014發病特多, 這一點就值得思考; 是否有其他因素造成2014大爆發?  如果以蚊子生態來思考, 應該是2014出現了非常適合蚊蟲繁殖的環境, 並且之前的滅蚊方式無法解決
> [name=Tom S]

> 如果CDC能提供歷年來蚊蟲抗藥性的資料會更有趣 ( CDC 都會定期抓蚊子, 這件事我以前幹過), 假使歷年來抗藥程度比率都一樣 , 那抗藥性也就不能解釋今年大爆發,  剩下就要去找為什麼多了這樣多適合蚊子滋生的環境....
> [name=Tom S]

> 有沒有可能跟去年日月光排汙水改變生態有關呢? 雖然工廠是在楠梓區，並不在三民區旁邊。
> [name=Huiwen Y]

> 若以境外移入的觀點看，三民等五區人口中外勞比例占多少?或者該區人口去東南亞國家旅遊受感染再回來?
> [name=Huiwen Y]

> 我會想深入的可能就是三民五區域，因為那五個區域的發病人數是最高的，可能研究人口分布吧。前提是要有資料。
> [name=Huiwen Y]

> 再回到日月光工廠汙水事件，汙水排進後勁溪並影響地下水，如果捷運管線與地下燃氣管線是交叉的，有可能受汙染的水就這樣擴散，或者蚊蟲生物產生變化。晚點再來做圖片。 
> [name=Huiwen Y]

公視訪問諸位專家:
part 1 [https://www.youtube.com/watch?v=mXpK6jV5YpI#t=1942](https://www.youtube.com/watch?v=mXpK6jV5YpI#t=1942)
        今年6月底以前, 因為容積獎勵終止, 所以大型建案開工;外圍都已經清乾淨, 但因為建案多, 地下室鋼管積水 !
part 2 [https://www.youtube.com/watch?v=mXpK6jV5YpI#t=2240](https://www.youtube.com/watch?v=mXpK6jV5YpI#t=2240) 氣爆有關?
part 3 [https://www.youtube.com/watch?v=mXpK6jV5YpI#t=2548](https://www.youtube.com/watch?v=mXpK6jV5YpI#t=2548) Defense : 澄清無關
part 4 [https://www.youtube.com/watch?v=mXpK6jV5YpI#t=3088](https://www.youtube.com/watch?v=mXpK6jV5YpI#t=3088) 新加坡經驗: Evidence based policy making , task force
Finally : 公共衛生教育失敗 , 需改進
筆記區：[有話好說：登革熱大爆發！海水真能鹹死孑孓？](https://1.51.84.56/)

### 高雄大型建案與工地資料

1.  需要釐清：公共建設、建築工地、空地，與登革熱病媒蚊孳生的實質關聯性，是什麼？
2.  與登革熱病媒蚊相關的工地與空地，初步歸納有以下可能：
- 尚未申請建照，也就未開工，可能就是一片空地、養地、等待拆除...
- 已申請建照，未開工
- 已申請建照，已開工，或因故停工
- 已申請建照，施工完成，尚未申請使用執照
- 已申請建照，施工完成，已申請使用執照，實際上尚未使用，呈現為空屋、閒置狀態
3.  [高雄市政府建築執照存根查詢](http://163.29.241.127/bupic/preLoginFormAction.do;jsessionid=7713B24087D541DC046D64383999EECA)
4.  國外類似主題地圖：[https://buildingeye.com/](https://buildingeye.com/) 正在營造中的建築物的資訊，美國部分城市。

## Big Data in infectious disease

1.  Using Web Search Query Data to Monitor Dengue Epidemics: A New Model for Neglected Tropical Disease Surveillance [http://www.plosntds.org/article/info%3Adoi%2F10.1371%2Fjournal.pntd.0001206](http://www.plosntds.org/article/info%3Adoi%2F10.1371%2Fjournal.pntd.0001206)
 2\. Big Data Opportunities for Global Infectious Disease Surveillance
[http://www.plosmedicine.org/article/fetchObject.action?uri=info%3Adoi%2F10.1371%2Fjournal.pmed.1001413&representation=PDF](http://www.plosmedicine.org/article/fetchObject.action?uri=info%3Adoi%2F10.1371%2Fjournal.pmed.1001413&representation=PDF)
  簡單講, 就是利用分析歷史資料 \+ 即時資料 =\> 即時更新 risk map => 找到新病源聚集區 => 找到為何聚集 => 趕緊採取措施 ; 然後讓以上過程自動化

## Open data in infections disease

1.  提供即時資料下載, 供市民皆可使用
2.  讓更多人可以分析研究提供對疾病控制更有用的方式

[Forecast of Dengue Incidence Using Temperature and Rainfall](http://www.ncbi.nlm.nih.gov/pmc/articles/PMC3510154/)

待整理
與登革熱病例間具顯著意義的氣候因子:
當週及前一週之平均相對溼度、平均溫度
當週之降雨百分比、平均日照率
摘自

\[吳佩芝、陳佩綉、郭浩然、龍世俊，2004，氣候變遷對台灣居民傳染性流行性疾病健康風險之影響，成功大學環境醫學研究所、中央研究院地球科學研究所研究計畫報告\]
\[ 張筱玲、賴淑寬，2006，氣象資料於疾病監測之應用，行政院衛生署疾病管制局95年度科技研究發展計畫報告\]
\[中央氣象局 MOTC -CWBCWBCWB-99 -2M -13 計畫報告\]


