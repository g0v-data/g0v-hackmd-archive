---
title: "2017/3/8 無人機演習"
tags: hackpad
---

# 2017/3/8 無人機演習

> [點此觀看原始內容](https://g0v.hackpad.tw/NGRHifROx6m)

## Meta

### Summary

> why: 要解決什麼問題、為什麼要開發這個東西 (一段文字)
> [name=ET B]

災區通訊中斷的問題

### High Level Scope

> how: 要怎麼做才能解決上面說的問題 (幾句話)
> [name=ET B]

使用無人機背載無線網路AP，飛到無通訊的災區上空，提供該區域的臨時無線網路環境

### Sample Use Case

> 誰會來怎麼用 (幾句話)
> [name=ET B]



### Prerequisites

> 要先具備什麼條件才能做這個 (optional)
> [name=ET B]

-

### Estimated Efforts

> 時間估算 (optional)
> [name=ET B]

-

## Spike

> 這是什麼東西？ QAQ
> [name=ET B]

> 就是之前已做過的單純測試可行性但不能直接重用的小規模成品連結
> [name=Audrey T]


### 前期提要：臺北市如何實現城市無人機救災  [http://www.ithome.com.tw/news/109062](http://www.ithome.com.tw/news/109062)


#### 無人機設備(經緯航太)

- 設備規格：
- 操作說明：

#### 網路設備(訊舟科技)

- 設備規格：[http://www.edimax.com/edimax/mw/cufiles/files/download/datasheet/EW-7478AC\_Datasheet\_English.pdf](http://www.edimax.com/edimax/mw/cufiles/files/download/datasheet/EW-7478AC_Datasheet_English.pdf)
- 操作說明：[http://www.edimax.com/edimax/mw/cufiles/files/download/QIG/EW-7478AC/EW-7478AC\_QIG\_English_EN.pdf](http://www.edimax.com/edimax/mw/cufiles/files/download/QIG/EW-7478AC/EW-7478AC_QIG_English_EN.pdf)

## Mockup

> wireframe / mockup 抓圖，如果有互動功能，在圖片上面指出來
> [name=ET B]


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_85ec678c31434d6da90cbde132f7f768)

## Dev Background


###  演習簡介

- 演習名稱：臺北市106年全民防衛動員(民安3號)暨2017臺北世界大學運動會災害防救及金華演習(土石流災害警戒疏散及收容安置演練)
- 日期:2017/3/8
- 地點:士林區 溪山國小
- 設備:會有多台無人機做空中的通訊連接（超英趕美的...聽說一次可30分..）
- 無人機參與部分：於收容安置處所(溪山國小)，啟動無人機災害通訊備援機制提供暫時的網路通訊，讓該區民眾可對外通訊。

###  期程

- 2017/1/24(週二)：溪和宮與溪山國小場勘
- 2017/3/3(週五)：演習流程演練
- 2017/3/8(週三)：預演與正式演習(預錄)
- 2017/3/29(週三)：大型演習(現場演練世大運項目，本演練項目採預錄播出)

###  參與單位

收容處所無人機通訊備援演練參與單位：
- 臺北市政府資訊局
- 中華電信
- 經緯航太
- 訊舟科技
- AirMP4 鼎基空勤
- g0v無人機應用小組

整體演習參與單位：
- 臺北市政府消防局第四救災救護大隊暨所屬士林中隊
- 臺北市政府警察局士林分局
- 臺北市政府資訊局
- 臺北市政府社會局
- 臺北市政府工務局公園路燈管理工程處
- 士林區公所
- 士林區健康服務中心
- 士林區戶政事務所
- 士林區清潔隊
- 溪山國小
- 溪山里辦公處
- 中華電信

> 由於本次災害情境設定為土石流，致災條件通常為地區連續強降雨；建議邀請流域內的其他單位，以及上游段相關單位參與或知會告知：
> [name=che l]

> (1) ==「臺北市工務局大地工程處」==。土石流災害相關主管機關，亦為溪山里避難地圖製作單位 [http://www.geo.gov.taipei/public/Data/6641753371.pdf](http://www.geo.gov.taipei/public/Data/6641753371.pdf)。溪山里內有一處==「列管邊坡：萬山煤礦至善路3段336巷66號附近」==若考量到土石流觸發情境，則該列管邊坡也可能有不穩定的狀況，參考大地處頁面 [http://www.geomis.gov.taipei/GEOINFO/NormalPage/MudslideStream.aspx](http://www.geomis.gov.taipei/GEOINFO/NormalPage/MudslideStream.aspx)。
> [name=che l]

> (2) ==「內雙溪自然中心」==。大地處委託人禾基金會經營的實體中心，可預期會有旅客甚至外籍訪客避難對策等議題。地址：臺北市士林區至善路三段150巷27號；網站：[http://neishuangxi.blogspot.tw/](http://neishuangxi.blogspot.tw/) 。
> [name=che l]

> (3) ==「士林區農會 / 陽明山分部」==。該地區屬於士林區農會範圍，農會對於農戶名單、個別農戶生活起居特性、通訊聯絡方式等經驗，或可補充災時保全避難等目標落實。
> [name=che l]

> (4) ==「首都客運小18、首都客運市民小巴1路(士林線)」==。一方面避免送入更多潛在受災人車；再者，或許可作為疏散接駁合作單位。
> [name=che l]

> (5) ==「陽明山國家公園管理處」==。一方面溪山里北側已位於陽明山國家公園範圍內，國家公園範圍也可能同時成災或受災；再者，國家公園管理處對於範圍內的遊客人流與國籍組成較了解，應可以協助制定針對旅客應變機制與對策。
> [name=che l]

> (6) ==「新北市萬里區公所 / 汐止區公所」==。溪山里東北側即為新北市萬里區，東側為汐止區。若「至善路三段」中斷無法通行，可考慮由萬里「萬溪右線產業道路」與汐止「五指山產業道路」接近土石流潛勢溪流與保全戶地區。甚至針對溪山里北側編號 DF024 潛勢溪流鄰近的保全戶，特定情境下亦可考慮跨區避難，例如前往萬里區溪底里、汐止區長青里內的避難場所。
> [name=che l]



###  演習腳本(2017/1/24暫定)

#### 劇本一：空拍搜尋尚未撤離的民眾

1.  演練地點：溪和宮
2.  演練情境：模擬為山區民宅區，因土石流，擬進行預防性撤離
3.  演練內容：無人機裝載空拍機，即時將空拍影像回傳至觀禮台之電視(觀禮台在溪和宮)，供參與長官檢視空拍機搜索尚未撤離民眾之畫面。

> 補充該地區坡地防災避難地圖，來源：[http://www.geo.gov.taipei/lp.asp?ctNode=30639&CtUnit=14307&BaseDSD=7&mp=105041](http://www.geo.gov.taipei/lp.asp?ctNode=30639&CtUnit=14307&BaseDSD=7&mp=105041)
> [name=che l]

> ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_cd48bb9f4f7197328fba36ff95d06a04)
    
> [name=che l]

> ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6499c55b006facfd959520c4a4db817f)
    
> [name=che l]


#### 劇本二：無人機臨時搭建通訊環境

1.  演練地點：溪山國小
2.  演練情境：模擬為收容處所，民眾均已安置於本處所，但該處所附近通訊中斷，訊息無法外送
3.  演練內容：無人機共三部，均配有無線網路AP，依序於距離溪山國小約300~400公尺處飛行，其中一架於溪山國小收容處所上空，另一架距離約100~200公尺，最後一架距離再隔100~200公尺，將4G轉Wifi的通訊訊號送至收容處所
4.  演練通訊之配合：**請收容處所參與的志工團體使用具EOC災情案件通報功能的單一陳情系統Web版，傳送災區資訊至消防局EOC。**
> 該功能為單一陳情系統的新版功能，將於本次演習同時發布~~~
> [name=楊世鈺]

> 這次是否會使用如:ssid:00000Taiwan(用來宣導急難時使用可識別SSID)及無人機上wifi ssid用 00000UAV
> [name=Passerby]


### 新想法與塗鴉區

想做出什麼不一樣的救災應用可留下你的想法.
> 目前我預計會現場"正射"  and  "3d建模"
> [name=Passerby]

> 條件ok 時會直接"用無人機投送設備"
> [name=Passerby]

> 直播.這是一定要的.其它請要加入動手的自己填
> [name=Passerby]

> 好奇能否做到相當消耗人力的 "地毯式搜索" ，主要就是在指定範圍內做規律性自動的拍照建檔，並且計算圖片涵蓋範圍避免重複，理想上能夠自動拼湊多張圖片成為正射影像讓後勤人員進行圖像的搜索與標記
> [name=kiang]

> 正射功能很成熟.正常接案都是飛手拍完直接交給單位。
> [name=Passerby]

> 看如何規劃，正常可結合 google earth。
> [name=Passerby]

> 也可運用 Google tour builder 做細部的任務規劃.
> [name=Passerby]

> 進階一點 可結合正射及720環景做出現場的圖資及介紹網頁.
> [name=Passerby]

> 國外搜救的的做法.參考>\> [https://www.youtube.com/watch?v=0l4MLWJxxy0](https://www.youtube.com/watch?v=0l4MLWJxxy0)
> [name=Passerby]

> 動作快飛一區域(約15分),後把圖上傳請大量志工人工看或是用AI來處理.（非樹多區域實測過)
> [name=Passerby]

> 但需考慮到山區多樹.(建議山區結合*8channel 對講機")才可快速定位.
> [name=Passerby]

> 打屁時想的東西，來推行救災用的 專用wifi ssid 00000taiwan 請參考 google 00000japan
> [name=Passerby]

> 是不是台北市救災 ssid 都統一用00000taiwan 發新聞稿有爆點吧.
> [name=Passerby]

> 救災幾個方向 提供大哥參考一下  
> [name=鼎基科技]

> 1--> 無人機救難平台 [https://mp4.ccky0316.com/index.php/2016/09/05/page-20/](https://mp4.ccky0316.com/index.php/2016/09/05/page-20/)
> [name=鼎基科技]

> 2-->無人機★空中傳遞★ 專利套件 [https://mp4.ccky0316.com/index.php/product/yahoo-68/](https://mp4.ccky0316.com/index.php/product/yahoo-68/)
> [name=鼎基科技]


劇本一相關：尋找尚未撤離民眾
> ．如何選擇搜尋範圍標的：
> [name=che l]

> (1)「中華電信」能否提供該地區的手機訊號來源位置，輔助確認人員是否已避難？以此訊號分布狀況，優先找出可能尚未撤離民眾的地區以便無人機進行搜尋。但沒有訊號的地區不代表沒有尚未撤離的民眾，建議這部分需綜合士林區農會、里辦公處、收容單位掌握已避難名單、陽明山國家公園旅客狀況、內雙溪自然中心旅客狀況等作為判斷依據。
> [name=che l]

> (2) 由於本里幅員較大，且各戶通往避難據點都必須使用「至善路三段」，建議可以搜尋這個重要的避難動線沿線。一方面可以透過無人機確保道路是否持續保持步行、車行可用；再者，若保全戶已離開家戶，動身前往避難據點，通常也可以在至善路三段沿線上拍攝到步行或開車等影像。
> [name=che l]

> ．設想劇本一情境的氣象與地理環境：
> [name=che l]

> (1) 若災害設定為土石流，多半當時的氣象條件屬於持續降雨，且時雨量應有一定強度，不曉得這樣的降雨條件，對於無人機運作是否會造成條件限制或其他需要考量的事項。例如必須防水、影像視線能見度等。
> [name=che l]

> (2) 若操作者並不熟悉該地區地理與環境，本身也可能並非專職於救災領域人員，好奇如何確保無人機操作者本身的安全？操作者距離無人機最遠距離為何？若先以溪山里來說，能否先規劃出操作者的安全範圍地圖？是否需要搭配熟悉在地的救災人員全程陪同？...等。主要目的是避免操作者成為受災對象。
> [name=che l]

> 您提的問題應該是和演習的劇本訂定有關的。
> [name=Passerby]

> 正常有經驗使用無人機救災大都不是用走的。(拍攝不是在現場，可能是幾公里外找穩定的地形和地點)
> [name=Passerby]

> 主要都是先空中偵查和空拍正射地圖(說白一點就是做一份現場的小區域衛星地圖)
> [name=Passerby]

> 提供給救災單位參考後，才有其它的部份。
> [name=Passerby]

> 其實演習的目地就是給相關單位及救災人員了解無人機及比較先進的無人機應用方法。
> [name=Passerby]

> 所以目前應該是預想無人機操作者，於災時所設置的==「前進指揮所」==，操作空中偵查囉？會這樣提問主要是希望可以與災時應變的現有機制做一些初步試探性整合。
> [name=che l]

> 這部份要問製作劇本的人 笑，說真的政府單位對"無人機應用"還在了解階段
> [name=Passerby]


劇本二相關：透過社群推播災害訊息
> 溪山社區目前有一些社群粉絲頁或是社團：
> [name=che l]

> (1) 溪山社區 台北天空之城 [https://www.facebook.com/taipeifarm/](https://www.facebook.com/taipeifarm/)
> [name=che l]

> (2) 臺北市士林區溪山國小Taipei Municipal XiShan Elementary School [https://www.facebook.com/臺北市士林區溪山國小Taipei-Municipal-XiShan-Elementary-School-181238598576648/](https://www.facebook.com/臺北市士林區溪山國小Taipei-Municipal-XiShan-Elementary-School-181238598576648/)
> [name=che l]

> (3) 台北市雙溪溪流生態廊道合作平台 [https://www.facebook.com/groups/437332386461359/](https://www.facebook.com/groups/437332386461359/)
> [name=che l]

> (4) 陽明山國家公園 [https://www.facebook.com/YMSNP.tw/](https://www.facebook.com/YMSNP.tw/)
> [name=che l]

> 討論：
> [name=che l]

> (1) 是否有其必要在保全對象已經身處於安置場所期間，於粉絲頁或社團張貼災時訊息？是否有實質效益？
> [name=che l]

> (2) 該地區鄰近陽明山國家公園與故宮博物院，災害發生期間是否會有外籍遊客身處該地區？或是仍有旅客前來此地區？
> [name=che l]

> (3) 是否有其必要通知行駛至善路三段的公車業者停駛，避免送入更多潛在受災人車，例如 首都客運小18、首都客運市民小巴1路(士林線)
> [name=che l]


劇本二相關：開放街圖社群描繪災後地圖
> Open Street Map 人道救援開放街圖小組 (Humanitarian OpenStreetMap Team, HOT) 
> [name=che l]

> 討論：
> [name=che l]

> (1) 如何確認是否需要聯繫並啟動 HOT 機制？
> [name=che l]



實做
- 直播(這沒什麼難度，會先確定現場那一家4G比較好)
- 正射(會公開做法)
- 3D建模(會公開做法)
- 熱影像(這會公開做法,但設備貴)
-
## Dev Journal

> 這個我也不知道是什麼… QAQ
> [name=ET B]

> 就是實作日誌，和 Spec 不連動
> [name=Audrey T]


###  1.事先申請與注意事項

- 禁航區查詢：**機場禁止施放有礙飛安物體範圍查詢系統**
松山機場(海拔5公尺)：[http://web-gis2000.caa.gov.tw/caaPublic/(S(hdcjh1cajfni4zksch04yskl))/TaipeiObject.aspx](http://web-gis2000.caa.gov.tw/caaPublic/(S(hdcjh1cajfni4zksch04yskl))/TaipeiObject.aspx)
- 演習場地為溪山國小([111台北市士林區至善路三段199號](http://maps.google.com.tw/maps?rls=com.microsoft:en-US&oe=utf8&rlz=&redir_esc=&um=1&ie=UTF-8&q=111%E5%8F%B0%E5%8C%97%E5%B8%82%E5%A3%AB%E6%9E%97%E5%8D%80%E8%87%B3%E5%96%84%E8%B7%AF%E4%B8%89%E6%AE%B5199%E8%99%9F&fb=1&gl=tw&hnear=%E8%90%AC%E8%8F%AF%E5%8D%80&cid=0,0,3889216515507644361&ei=ix5BTPCrAY7evQO0y_DnDA&sa=X&oi=local_result&ct=image&resnum=1&ved=0CBcQnwIwAA))，海拔186公尺，依規定需要跟民航局進行申請
- 申請表格:[https://drive.google.com/open?id=0ByZ0qpvoEVQvNmx3SVRMb1NoXzA](https://drive.google.com/open?id=0ByZ0qpvoEVQvNmx3SVRMb1NoXzA)
注意:除了民航局申請，建議加保第三責任險。

有關空拍保險部份
個人可保"富邦 新十全大補方案" 有附加"富邦產物家庭成員意外責任保險" 個人部份
(非廣告可去電你喜歡的產物保險公司說要類似"十全大補"的方案）
執行業務和空拍公司需保 "營繕承包人意外責任保險"(請自行google)
(一樣大部份產物保險公司都有，但都是按需訂做。參考新光產險)

有關申請表格的座標
我的經驗
用[https://flylitchi.com/hub](https://flylitchi.com/hub)
先設定好中心點在分別設好四點座標
座標 csv 如下:
溪山國小[https://drive.google.com/open?id=0ByZ0qpvoEVQvdmxReEgtSGItTGc](https://drive.google.com/open?id=0ByZ0qpvoEVQvdmxReEgtSGItTGc)
溪合宮[https://drive.google.com/open?id=0ByZ0qpvoEVQvQ21DTFNMU0lDTEk](https://drive.google.com/open?id=0ByZ0qpvoEVQvQ21DTFNMU0lDTEk)
取到座標後在用[http://tools.freeside.sk/geolocator/geolocator.html](http://tools.freeside.sk/geolocator/geolocator.html)  轉換
WGS84數值              WGS84座標 (參考[https://goo.gl/OmrZae](https://goo.gl/OmrZae)[)](https://goo.gl/OmrZae)
121.73816              121度44分17.376秒
0.73816*60=44.2896
0.2896*60=17.376

### 2.限航區申請注意事項


 本次申請場域：





###  3.1/24 場地勘查

- 士林溪和宮
中華電信4G訊號比較弱(約1-2格)；台哥大4G訊號不錯。
附上台哥大訊號圖:[https://drive.google.com/open?id=0B2vV0jW1ZlU8TzZxNXVlcEJSczA](https://drive.google.com/open?id=0B2vV0jW1ZlU8TzZxNXVlcEJSczA)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_371d8a84178644b02f95e2456471c06b)
附上現場gps定位圖:[https://drive.google.com/open?id=0ByZ0qpvoEVQvcHRNR2VfYWplaEU](https://drive.google.com/open?id=0ByZ0qpvoEVQvcHRNR2VfYWplaEU)
定位正常沒有位移現象

- 士林溪山國小
中華電信4G訊號很好；台哥大4G訊號很好。
附上台哥大訊號圖: [https://drive.google.com/open?id=0B2vV0jW1ZlU8MExYenltNjV2U2M](https://drive.google.com/open?id=0B2vV0jW1ZlU8MExYenltNjV2U2M)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_16b64d5ddd3347abdcad947c7901431c)
如中華電信有支援，可加強溪和宮訊號。方便這個點的直播。(或是要由溪山國小 打wifi訊號.開玩笑勿當真)
附上現場gps定位圖: [https://drive.google.com/open?id=0ByZ0qpvoEVQvbHpGX1NrajZGdzg](https://drive.google.com/open?id=0ByZ0qpvoEVQvbHpGX1NrajZGdzg)
國小和google maps 有位移：[https://drive.google.com/open?id=0ByZ0qpvoEVQvZGhhYnB0Ml9lbms](https://drive.google.com/open?id=0ByZ0qpvoEVQvZGhhYnB0Ml9lbms)
(使用定位功能請小心)
二點直線距離：1.21km [https://drive.google.com/open?id=0ByZ0qpvoEVQvamY5SWRkOVlYMWs](https://drive.google.com/open?id=0ByZ0qpvoEVQvamY5SWRkOVlYMWs)
> google 地圖有考慮高度落差嗎？
> [name=che l]

> google 地圖應該不用考慮高度落差.
> [name=Passerby]

> 如是有關地點的問題?應該是問問相關的地點選擇部份?
> [name=Passerby]

> 這個只是單純抓直線距離來參考。
> [name=Passerby]

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_3f39a1294ddab17d71f641f4ede1f760)


###  4.實作紀錄

直播網址:


正射資料公開網址:


3d建模資料公開網址:(現場地形，如失敗就不會放)



## Spec

> 由 high level scope 衍生出的對話樹，寫使用者做一件事情的每個步驟 (使用者跟系統的互動) 
> [name=ET B]

> dev 開發完以後在行首加上 :ok: ( : 後面打  ok 再打 : )
> [name=ET B]

> qa 測完以後加上 :+1: ( : 後面打 +1 再打 : )
> [name=ET B]

> pm 驗收完以後整行打勾
> [name=ET B]

> deploy 後…如果全部 ~像這樣劃掉~ 會不會很爽？ XD
> [name=ET B]

> qa 發現不在 scope 內的新問題時，如果沒有這個真的沒辦法上線，則自己加 checkbox，不然就等下一階段的開發再說
> [name=ET B]


- [ ] ...
    - [ ] ...
    - [ ] ...
- [ ] ...
- [ ] ...







