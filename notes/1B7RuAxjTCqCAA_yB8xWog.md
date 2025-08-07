---
tags: GIS
---

# 河流-濕地-湧泉-乾式滯洪空間-資料盤點
臺灣濕地地圖：http://u.osmfr.org/m/224438/
社團討論串：https://bit.ly/2Gw9L24

:::warning
文件目錄
[TOC]
:::


## 資料怎麼呈現、展示、記錄？

### 地圖試作
地圖網址，可共同編輯
http://u.osmfr.org/m/224438/
分類
【自然濕地】例：大鬼湖
【水庫】例：連江縣南竿鄉勝利水庫
【農業梯田濕地】例：吉哈拉艾水梯田
【湧泉環境】例：台東市湧泉運動公園
【市鎮濕地公園與埤塘】例：中都濕地公園
【乾式滯洪公共設施】例：林口東湖公園
【河濱濕地】例：社子島濕地
【漁塭地區】例：七股區篤加地區
【河口與海濱濕地】例：高美濕地

### 資料課題
考慮使用「時間地圖」來管理資料
TimeMapper 
http://timemapper.okfnlabs.org/
Spreadsheet 必備的欄位是Title還有Start。
如果只是建立地圖，Start可以不需要。 記得在TimeMapper使用的欄位之外，你可以加任意數量的其他欄位
使用 Google Spreadsheet / Airtable 建立協作資料集
不少濕地，本身有官方或民間所設立的專屬頁面，頁面網址應納入資料集內
頁面舉例
內政部網站，北門濕地：http://wetland-tw.tcd.gov.tw/WetLandWeb/wetland.php?id=174
民團建立網站，台南市水雉生態教育園區：http://www.tnbird.org.tw/jacana/
隨著濕地資料數量越來越豐富，開始會出現「多值屬性」的狀況，例如以下這個「筆電快篩」頁面，對於一個筆電有金額、重量、品牌等屬性（筆電快篩：http://muyueh.com/30/notebook/）。是否有支援【線上地圖 x 多值屬性】的工具可以使用呢？
高爾夫球場內的水體
位在大學或學校內的水體
...等

## 濕地資料在哪裡？
同步盤點官方是否有提供相應的開放資料 open data
20140801 曾有網友詢問，但官方仍沒有開放 https://data.gov.tw/node/8394
也筆記民間所盤點的資料

圖資
國際級重要濕地.json
https://github.com/kiang/eland.cpami.gov.tw/blob/master/json/%E5%9C%8B%E9%9A%9B%E7%B4%9A%E9%87%8D%E8%A6%81%E6%BF%95%E5%9C%B0.json
國家級重要濕地.json
https://github.com/kiang/eland.cpami.gov.tw/blob/master/json/%E5%9C%8B%E5%AE%B6%E7%B4%9A%E9%87%8D%E8%A6%81%E6%BF%95%E5%9C%B0.json
國家級重要濕地保護區.json
https://github.com/kiang/eland.cpami.gov.tw/blob/master/json/%E5%9C%8B%E5%AE%B6%E7%B4%9A%E9%87%8D%E8%A6%81%E6%BF%95%E5%9C%B0%E4%BF%9D%E8%AD%B7%E5%8D%80.json
地方級重要濕地.json
https://github.com/kiang/eland.cpami.gov.tw/blob/master/json/%E5%9C%B0%E6%96%B9%E7%B4%9A%E9%87%8D%E8%A6%81%E6%BF%95%E5%9C%B0.json
線上圖台無資料集：林務局濕地網 & 濕地地圖
http://wetland.e-info.org.tw/
線上圖台無資料集：內政部重要濕地地圖
http://wetland-tw.tcd.gov.tw/WetLandWeb/map.php
介接：http://gis.rchss.sinica.edu.tw/qgis/?p=3195
地段清冊資料：內政部-非重要濕地所在鄉鎮市區地段清冊
http://www.urbanplanner.org.tw/naup/upload/1040326-%E5%85%A7%E6%94%BF%E9%83%A8-%E9%9D%9E%E9%87%8D%E8%A6%81%E6%BF%95%E5%9C%B0%E6%89%80%E5%9C%A8%E9%84%89%E9%8E%AE%E5%B8%82%E5%8D%80%E5%9C%B0%E6%AE%B5%E6%B8%85%E5%86%8A.pdf
清單資料：內政部有公布他們所定義的濕地83處，但是沒給資料集
http://data.moi.gov.tw/moiod/Data/DataDetail.aspx?oid=155E015A-B3A9-4075-9E5D-3C735283724A
水庫
官方資料？

農塘 gis 資料
https://www.facebook.com/share/p/AzZ8qDi8Qo7svEJ2/

大學校園內的水體
https://www.facebook.com/share/p/zb4XpJ1vTDJ4BhfY/


## 學術研究資料
全球水體變遷地圖與資料 
https://global-surface-water.appspot.com/
遙測方式使用 Sentinel-1 可以篩出大多數水體範圍與區域  
https://appliedsciences.nasa.gov/sites/default/files/SAR%20Disasters%20Part%201.pdf


## 待登載資料
溫泉與地熱水體
全國溫泉區分布及公告地圖 
https://www.facebook.com/GeoHarvester/posts/1910251078993271
溫泉露頭調查資料
https://data.gov.tw/dataset/32504
小飛的臺灣溫泉與瀑布地圖
https://goo.gl/zAA5cQ
野溪溫泉
https://www.google.com/maps/d/viewer?ll=23.372015691310985,120.58094632544777&z=11&fbclid=IwAR26igHvGOTAxlcaEn91I9rDVCBHvImbDtpEVzrbFeSkwpFYFjrl66ZtbyI&mid=1WNRTtzE-eK-saM2qeptPd23sm2xGmig&mibextid=S66gvF
彙整主題網站
https://smiletaiwan.cw.com.tw/special/19
https://www.facebook.com/groups/138704166197633/
個案單點
陽明山龍鳳谷地熱水體
農塘，分析方法
https://www.facebook.com/284329422046435/posts/1298423200637047/
河流資料
大河小溪全民齊督工
https://www.youtube.com/watch?v=0c2Owl3xBIk
https://river-watcher.bambooculture.tw/map
有整理全國的河川地理資料

水利署釋出「河川河道」KML 檔案，約 70MB 放不上 umap
https://scidm.nchc.org.tw/dataset/313200000g-000171
水利署釋出「河川支流」KML，約 70MB 放不上 umap
https://scidm.nchc.org.tw/dataset/313200000g-000170
暫不考慮放「範圍類」圖資
水利署釋出「河川流域範圍圖」集水區範圍 KML 檔案
https://scidm.nchc.org.tw/dataset/riverbasinrange
臺北市集水區範圍圖
https://data.taipei/dataset/detail/metadata?id=d8085d88-0a07-4fe6-86ec-8910954342ac
「雨水下水道」圖資
臺北市有釋出


水庫
嘉義市蘭潭水庫 https://www.facebook.com/groups/solarpvgsa/permalink/2229126947319227/

大學校湖 78 處
https://www.facebook.com/100001766541390/posts/pfbid037USnRxz7pUdSnCpuuLaVTuSEptRXx5WpyR1dQJardR8seo6gCF5cQGEKdJpCEPw8l/

湧泉
持續將各種清冊資料整理至此線上文件中 https://bit.ly/2Jn88tc
來源
「臺灣湧泉50選」電子書 https://conservation.forest.gov.tw/0001789
桃園市宵裡 
https://www.facebook.com/share/p/h8g2Tf58oTxWZ97E/
台中市政府湧泉調查 
http://m.ltn.com.tw/news/life/breakingnews/2158779
找找看有沒有調查成果文件
台中
https://www.facebook.com/100000363068857/posts/2290327087656038/
高雄市內惟龍井里與鄰近社區 
https://www.facebook.com/springwater.chiuyw/posts/1524442714265329
台東市立湧泉公園
南庄鄉 大伯公 旁的 水井，算湧泉嗎?


七彩湖 https://www.facebook.com/100000115283878/posts/5612899258723861/
高公局維護管理的人工濕地
國道1號高科交流道生態滯洪池
國道6號東草屯及愛蘭交流道生態池
國道3甲號西向0k+900～1k+100富陽公園人工濕地復育區
國道2號機場系統交流道濕地
經國七海文化園區
25.07864276537666 121.53623126952584
天和公園，水池與水井
https://moonheart930906.pixnet.net/blog/post/319620914
芝山岩
https://www.facebook.com/linhtlin/posts/10215247890811750
劍潭抽水站，攔汙池
25.081508, 121.518462
台北市政府 水域
https://photos.app.goo.gl/yNzJwNFm7ZodxhCe8
南港，麗山廣場生態池
https://www.facebook.com/community.taipei/photos/br.AbqKeuJNUGxXE6fCeP75sf9Dh5p33j2SB1umBoGABLIErFonElSDSNcUCedUP97Xh4-4dhlq9J1vDKEbkzPV4wn4dWANjnT849dWhgjjR7XoCDLHBIyqAgsPjmY5u5qTjuE/10156154980026517/
南港站中研院生技園區
https://www.facebook.com/100001517169120/posts/2688640217863191
內湖 
https://www.facebook.com/409175792496718/posts/2687043481376593
新北市抗旱水井
本市目前計有7口抗旱水井(管徑400mm)，為水利署91年度於本市樹林區所施作，有5口位於樹林省民公園，現由本府教育局體育處及水利署第十河川局管理，另有2口位於樹林河濱公園，為本府高灘地管理處管轄範圍。
https://data.ntpc.gov.tw/od/detail?oid=5D733E16-F779-4592-940B-D473E23D649D
漁塭
https://www.facebook.com/groups/600385406707053/permalink/1866203546791893/


滯洪公園類
公共政策網路參與平台： 如何強化水利署推動滯洪池建置及運作情形，審計部歡迎您來發表意見。https://cy.join.gov.tw/policies/detail/15ee5c9e-91e9-400f-8455-c87c5e7f8e41
文山區辛亥捷運站斜對面滯洪池（下方為滯洪池，上方為綠地公園）
https://www.facebook.com/photo/?fbid=4302700593141543&set=gm.4031754323580782
林口區內滯洪設施位置及用地面積
csv 資料
https://data.gov.tw/dataset/124227
林口滯洪池系統，還有許多塊還沒登載到地圖上
https://www.facebook.com/groups/urban.rivers.streams/permalink/1441198759303031/
https://www.facebook.com/groups/urban.rivers.streams/permalink/2433310936758470
台南南科特定區的滯洪公園
公滯4(南科特定區)
公滯10 (南科特定區)
https://photos.app.goo.gl/E9p8TPz6KyVGLKS17
臺南 樹谷 
https://www.facebook.com/100000066795897/posts/2012166388795568/
http://m.ltn.com.tw/news/life/breakingnews/2448303
仁化工業區，兩處滯洪池
https://photos.app.goo.gl/k1m2ksORqYiJvNs52
中部科學園區，八座滯洪池
http://iufm.cpami.gov.tw/case_a/30
公園用地(本和里滯洪)
南紡夢時代 滯洪
台南德東自辦市地重劃滯洪措施 https://www.facebook.com/1807530187/posts/10216377497309174/
大里草湖防災公園 https://www.facebook.com/517380721/posts/10165106482355722/

---

蜻蜓池
https://www.google.com/maps/d/viewer?ll=24.188062863498004%2C121.78844887054342&z=8&fbclid=IwY2xjawKMTJVleHRuA2FlbQIxMABicmlkETFvM2FDRGV2RmllNmlqTVBpAR6NmcDuNTWzYqsC_0e5XnUiKrsbHDBLEhLxVHPNX0nPuelEhwNfjsGvq32qpg_aem_WnxUtCgBdtZdvJy47HialQ&mid=1lLkzj4gQKFOZm7Tn3uR1EAtgej4

北藝大
卯澳山區
https://www.facebook.com/story.php?story_fbid=pfbid0xAdUq1oekSChQWu1vhyAAjB1ShJYPEFF6ke9wwfpeeFvoy8yA2uREdjvmyCdszXcl&id=1190665661061444&mibextid=tejx2t
基隆砂灣生態公園
汐止 
https://www.facebook.com/groups/urban.rivers.streams/permalink/2472876779468552
中研院附近國家生技園區人工濕地 
https://www.facebook.com/groups/urban.rivers.streams/permalink/2073730829383151
美堤河濱公園內的自然親水彎
25.0753970, 121.5584773
松山區錫口人口濕地
https://www.peopo.org/news/377769
https://memory.culture.tw/Home/Detail?Id=292681&IndexCode=Culture_Place

雙溪河濱公園範圍的蜿蜒水路
https://www.facebook.com/photo?fbid=23888155174112309&set=a.175852862435873&locale=zh_TW

臺北車站忠孝西路造景水池
逸仙公園
臺北賓館
台北植物園

臺北市客家 文化主題公園
臺北市客家文化公園
https://www.facebook.com/Taipei.Hakka.Farm/posts/2416941115036218
師大環教所旁的水域營造
文山景美運動公園
http://tcgwww.taipei.gov.tw/ct.asp?xItem=48241&CtNode=5277&mp=100021
文山森林公園
https://www.facebook.com/story.php?story_fbid=pfbid02L4cVi5dknGTBq53Dno4LWzSq6PSD64URGH8cEWz6RA5ApJJuhdjfCDVV5ugT5UTpl&id=100002049330136&mibextid=qC1gEa
228紀念公園西北側水域
動物園內的水域
國立教育廣播電臺旁的水域
https://www.facebook.com/644557612/posts/10156236796607613/
四海園區
https://www.facebook.com/story.php?story_fbid=pfbid034tQ5ieGvzHApxg8HMeGooeFYoZKrcko6vAeNJdYEacjLoYoHDezEochUWsSsM1iHl&id=1723943044&mibextid=tejx2t
國防醫學院醫澤園
https://www.facebook.com/ndmc.fireflyrecovery/
三重校園生態池
https://www.facebook.com/share/p/8px6Mbr83ehv6JM8/
板橋
25.000193, 121.456021 
https://www.facebook.com/groups/urban.rivers.streams/permalink/1974456059310629/
板橋新北圖書總館附近地面開放式滯留(洪)池
https://www.facebook.com/groups/urban.rivers.streams/permalink/2003060619783506/
浮洲
https://www.facebook.com/111259046900571/posts/742048117154991/
林口長庚湖
坪林的仁里板濕地
https://www.facebook.com/100000813811322/posts/4098095776894176/
汐止翠湖
https://www.facebook.com/chunghsin.yang/videos/2541731042567354/
金山濕地
https://www.facebook.com/SatoyamaJinshan1
宜蘭
https://www.facebook.com/permalink.php?story_fbid=1467481433401083&id=100004177208592
羅東
https://www.facebook.com/story.php?story_fbid=pfbid032rDaRez4Rwk6Bt1M4xjwoSABGwtbTDHGHvRLZJpaiXkr5rxHobxj1mv4TG4mmVtdl&id=100057700861112&mibextid=qC1gEa
員山鄉：龍潭湖、望龍埤、大湖、雙連埤、太陽埤。
三星鄉：長埤湖
冬山鄉：梅花湖
深溝水源生態園區
宜蘭科學園區
https://www.facebook.com/munch999/photos/a.10152413397300619/10156647063375619/
宜蘭大湖
https://www.facebook.com/722923086/posts/10156202846353087/
宜蘭礁溪龍潭湖
https://tw.appledaily.com/new/realtime/20181202/1476975/
宜蘭礁溪「望龍埤」又名軟埤
http://www.lanyangnet.com.tw/ilpoint/ys12/
宜蘭草湳湖
http://www.harmony-arch.com/portfolio_page/%E8%8D%89%E5%8D%97%E6%B9%96/
宜蘭太陽埤
宜蘭員山鄉 羌仔連埤 
https://www.facebook.com/1759108699/posts/10206364250742653
宜蘭內城鄰近山邊一帶，有些田區被農民稱為「破布田」
https://www.facebook.com/192664375618/posts/10157362760395619
花蓮松園別館
https://www.facebook.com/story.php?story_fbid=pfbid0QkshwnjAUcwp1zvdAqrCMmshL4LDjdZtZBy2T89Mgcd8DvxMPpoLnR24kqxwE3m2l&id=545788167&mibextid=qC1gEa
桃園員樹林
https://www.facebook.com/100000194449105/posts/5632773693405723/
桃園楊梅中華汽車生態池
https://www.facebook.com/1233886895/posts/pfbid0TQSxXarAaaC7yqVWJkK71QG5BF4AhKnByeFRom3BKNWzn4wTfkdawqd8Bfqs73nnl/
新竹
https://www.facebook.com/950487731798296/posts/1019418714905197/
鈴木埤
https://yingtingshih.pixnet.net/blog/post/197095557-%E7%AC%AC0579%E7%AF%87%5B%E8%8B%97%E6%A0%97%E7%AB%B9%E5%8D%97%5D%E9%88%B4%E6%9C%A8%E5%9F%A4%E7%94%9F%E6%85%8B%E6%B0%B4%E5%B2%B8%E4%BC%91%E6%86%A9%E5%85%AC%E5%9C%92%EF%BC%8F
南園
http://nanyuan.theonestyle.com/index.asp?aas=38
新竹綠園道食物森林的池塘
https://www.facebook.com/100000192830591/posts/3524938174189242/
清華大學成功湖
https://www.facebook.com/story.php?story_fbid=pfbid0238n7BuLGFrAABbys3MNaVfaEhNRc2UDyUzZUWKKegSsjXcGQTfibn8BDs6eyNadTl&id=100064388243802&mibextid=qC1gEa
新竹縣東興國小公共藝術案
https://www.facebook.com/rayscchu/posts/10208984112996400
新竹縣 范朝燈故居
https://www.facebook.com/100064592233058/posts/376180331211705/
新竹縣峨眉湖
https://www.facebook.com/groups/urban.rivers.streams/permalink/2722934907796070/
苗栗三聯埤
http://j28ah.pixnet.net/blog/post/418511965-%E8%8B%97%E6%A0%97%E4%B8%89%E7%81%A3%E4%B8%89%E8%81%AF%E5%9F%A4
苗栗 八甲
https://www.facebook.com/1807530187/posts/10213900507505977/?d=n
頭城
https://www.facebook.com/groups/urban.rivers.streams/permalink/2322929554463276
新山夢湖
https://www.facebook.com/chunghsin.yang/posts/2002581066482357
七彩湖
https://www.facebook.com/100000784566673/posts/2203825606320237?s=700484037&v=i&sfns=mo
二仁溪流域濕地
https://www.facebook.com/dajaiwetland/
苗栗後龍，園區開發後水體
https://www.facebook.com/100003381485309/posts/1858587177597314/
苗栗龍昇湖
https://www.facebook.com/profile.php?id=100067635559250
臺中花博外埔園區
台中西區的茄苳公園內的水域
https://www.facebook.com/1287055933/posts/10213709073022885/
https://www.facebook.com/1723943044/posts/10205024900218555/
台中市烏日區光明社區水域營造
https://www.facebook.com/shihyunchu/videos/1916299538423645/
台中
http://m.ltn.com.tw/news/life/breakingnews/2675473
台中
24.196326, 120.651954
臺中中央公園
臺中歷史建築帝國製糖廠臺中營業所
https://www.facebook.com/atsugarstudio/
中台湖
太平區大潭仔
臺中市仁化工業區
https://photos.app.goo.gl/xjaydFEK92Cks5Tj8
彰化 成美
https://www.facebook.com/cmcp1885/
南投埔里草湳濕地
https://www.facebook.com/草湳濕地-Miss-firefly-1419330235039343
埔里鎮桃米社區休憩空間
23.941060 120.926373
https://youtu.be/R6e4IFTXYXM
圓林園公園
https://udn.com/news/story/7325/3230548
https://www.facebook.com/permalink.php?story_fbid=1769481753163177&id=652299864881377&__tn__=C-R
宜梧滯洪池
https://www.facebook.com/100000212960177/posts/5592169307466779/
南投鹿谷 https://www.facebook.com/100004177208592/posts/1350867141729180
水里 明潭電廠鉅工分廠將閒置土地活化善加利用，也為南投水里打造出「綠能新祕境」
https://www.facebook.com/groups/solarpvgsa/permalink/2988767194688528/
雲林斗六溪旁的人工濕地與滯洪池
https://www.facebook.com/groups/urban.rivers.streams/permalink/1909016425854593/
澄霖沉香味道森林館
https://www.facebook.com/1472906576357484/posts/1933241586990645/
嘉義市南興國民中學第二校區-自然探索教室
23.472854951470552, 120.46806547560635
臺南市漁光島濕地
https://www.facebook.com/100000151492509/videos/2146629128685449/
22.9748973,120.1570483
巴克禮公園
https://www.facebook.com/623939544444778/posts/1481508442021213/
鹿耳門夢幻湖
臺南市 溪尾滯洪池
https://www.facebook.com/jacana.home/posts/2625498334129034
23.133665, 120.252481
臺南市國立臺灣歷史博物館
https://www.facebook.com/share/p/2vuPUcvUE1yhQgVD/
台南 安順 滯洪池
https://www.facebook.com/100000066795897/posts/4012036525475201/
北港滯洪池
https://www.facebook.com/351368342088363/posts/850264795532046/
臺南市水萍塭公園內水體
22.985893, 120.192895
臺南市 吳園 水體
22.994941, 120.206031
臺南市 國立成功大學成功湖
23.000147, 120.217325
八田與一紀念園區
23.213531, 120.365212
https://today.line.me/tw/pc/article/%E7%83%8F%E5%B1%B1%E9%A0%AD%E6%96%B0%E6%99%AF%E9%BB%9E+%E5%85%AB%E7%94%B0%E8%88%87%E4%B8%80%E6%88%B6%E5%A4%96%E6%99%AF%E8%A7%80%E5%9C%92%E5%8D%80%E5%AE%8C%E5%B7%A5%E5%95%9F%E7%94%A8-yyZnQz
嘉南埤圳重要濕地，多處
範圍： 本濕地分布於嘉南平原上，大大小小的埤圳可供灌溉面積約78,000公頃。
簡介： 埤塘是嘉南平原的重要地景，它不僅反映先民水利灌溉發展的過程，同時也呈現人類與自然互動共存的例證。平原小溪的中上游常被築壩截水用於灌溉農田，壩址以上部份被稱為埤或堤塘，而不再是溪。包括加走埤、九芎埤、牛挑灣埤、將軍埤、上茄苳埤、馬稠後頂埤、馬稠後蓮埤、林初埤、太平圳埤、埤寮埤、菁埔埤、洗布埤、烏樹林埤、北廍埤、番子田埤(葫蘆埤)、鹽水埤下游埤池、冷水埤、大潭埤。這些低窪處，常被洪水淹沒，農民種植菱角與蓮花，或作為養魚池，或養鴨養鵝，提供另一類型的生態環境，造就水雉的棲地。此外，縱橫整個嘉南平原的灌溉渠道，也是許多水生動植物流動的生態廊道。
嘉義縣水上鄉南鄉村東天湖坑及材柴埤頭生態公園
https://www.facebook.com/photo.php?fbid=2321388947873309&set=a.467275229951366&type=3&theater
嘉義滯洪池
https://m.ltn.com.tw/news/local/paper/1291431
曾文人工濕地
https://www.facebook.com/jacana.home/posts/2450743564937846

高雄

茄萣高雄海洋科技產業創新專區三中心
https://www.facebook.com/golden.park.71/posts/pfbid0XVbFLZjgWEtQmGaV1Df4moarLLPonh3Bhoz4DLFgE41UJTdWJF2gMwKZLzv1PuDml
高雄台泥廠區鼓山滯洪池(柴山滯洪公園)
22.645684, 120.274373
柴山滯洪池
https://www.facebook.com/112344990188853/posts/130718541684831?d=n&sfns=mo
102年10月完工啟用的小型濕式滯洪池，位於高雄鳳山南華路、鳳頂路交岔口東側，鳳翔國中附近。
https://www.facebook.com/groups/urban.rivers.streams/permalink/1650203915069180/
左營原生植物園
https://www.facebook.com/1177850278/posts/10223884855407445/
大東濕地公園
右昌森林公園
https://pwbgis.kcg.gov.tw/youchang/
金獅湖
https://www.facebook.com/pages/Jinshi-Lake/1529152587343591
棧伍庫
https://www.facebook.com/pages/%E6%A3%A7%E4%BC%8D%E5%BA%ABW5/918638758260032
美濃湖
https://e-info.org.tw/node/217228
https://www.facebook.com/1716906750/posts/10207678053505495/
軌道技術研究暨驗證中心園區配置，本園區基地位於高雄市燕巢區境內高鐵燕巢總機廠旁，該基地內有角宿溪(典寶溪支線)流經，因應使用機能區劃為生態保育區、行政辦公區、測試研發區等三大部分，並以寬度達15公尺的林蔭大道，南北向串聯生態棲地、滯洪池、休憩中庭、中央活動廣場等空間，創造與自然地景相呼應的生態意象，建置生態綠網及人車動線。搭配各種廣場系統，水平串連建物，讓園區工作者穿梭於廠區建築之間，感受工作環境中充滿自然綠意及生氣。 
https://www.facebook.com/permalink.php?story_fbid=504889083374353&id=331851447344785
典寶溪B區滯洪池
https://www.facebook.com/kunhai.lin/posts/10209656308000070
路竹區鴨寮 埤塘
https://www.facebook.com/1700391184/posts/10209391220173040/?d=n

六龜
22.887918884176596, 120.61212533928816
新埤建功森林親水公園
https://www.facebook.com/1742607076/posts/10206476332144068
五溝水
https://www.facebook.com/SiipTiHokGau/
潮州
https://www.facebook.com/887579934632769/posts/2604131146310964

花蓮和平港環境教育場域
https://www.facebook.com/yang.yi.ru.266226/posts/pfbid02vYZWWE5V8845tDYTeyYVUyWWFLM75PCTZ7zpBMaEa2Uynh3HBrDWtpDh1evNVXRZl
玉里 啟模濕地
https://www.facebook.com/1173992110/posts/10222871936124968/
池上大波池
https://www.facebook.com/100000247176754/posts/2512129268805288
知本濕地
https://www.facebook.com/守護知本濕地-1339337302827821
台東縣延平鄉鸞山湖
https://zh.wikipedia.org/wiki/%E9%B8%9E%E5%B1%B1%E6%B9%96%E6%BF%95%E5%9C%B0
達蘭埠部落天池
https://www.facebook.com/100003756039660/posts/1590858351049351?sfns=mo
台東市民宅
https://www.facebook.com/aling.life/posts/10164053972360472
金門
https://www.facebook.com/kunhai.lin/posts/10204587508523251
https://www.facebook.com/photo.php?fbid=10214870838497611&set=pcb.10214870841817694&type=3&__tn__=HH-R&eid=ARDNfO8msCT5JxxvPYOJ4IPf_xLHJhUgBlb9bkDJ1SnO8jJbJNBV5JUOFKp2JvrF8AEbyvpBkb2KcqcT
金門 蓄水池
https://www.facebook.com/100000247176754/posts/2190967260921492/

民間的濕地網
http://wetland.e-info.org.tw/map.html

內政部濕地資料，劃線代表已標註
http://wetland-tw.tcd.gov.tw/WetLandWeb/wetland.php?ctid=17
無尾港重要濕地
南澳重要濕地
五十二甲重要濕地
雙連埤重要濕地
蘭陽溪口重要濕地
淡水河流域濕地-大漢新店重要濕地
淡水河流域濕地-五股重要濕地
淡水河流域濕地-打鳥埤人工重要濕地
淡水河流域濕地-挖子尾重要濕地
淡水河流域濕地-城林人工重要濕地
淡水河流域濕地-浮洲人工重要濕地
淡水河流域濕地-淡水河紅樹林重要濕地
淡水河流域濕地-鹿角溪人工重要濕地
淡水河流域濕地-新海人工重要濕地
淡水河流域濕地-臺北港北堤重要濕地
淡水河流域濕地-關渡重要濕地
夢幻湖重要濕地
桃園埤圳重要濕地
許厝港重要濕地
新豐重要濕地
竹北蓮花寺暫定重要濕地 https://www.facebook.com/jinghong.lee.79/posts/10155554625669562
竹安暫定重要濕地
香山重要濕地
頭前溪生態公園暫定重要濕地
鴛鴦湖重要濕地
http://wetland-tw.tcd.gov.tw/WetLandWeb/wetland.php?ctid=19
椬梧暫定重要濕地        
七家灣溪重要濕地        
大肚溪口重要濕地        
大湳湖暫定重要濕地        
向天湖暫定重要濕地        
竹南人工暫定重要濕地
西湖重要濕地        
名間新街冷泉暫定重要濕地        
成龍暫定重要濕地        
東勢人工暫定重要濕地        
草坔暫定重要濕地        
高美重要濕地
草湳暫定重要濕地        
頭社盆地暫定重要濕地 
http://wetland-tw.tcd.gov.tw/WetLandWeb/wetland.php?ctid=21
大坡池重要濕地        
小鬼湖重要濕地        
六十石山暫定重要濕地        
卑南溪口重要濕地        
花蓮溪口重要濕地        
金龍湖暫定重要濕地
馬太鞍重要濕地        
新武呂溪重要濕地        
關山人工暫定重要濕地        
鸞山湖暫定重要濕地
http://wetland-tw.tcd.gov.tw/WetLandWeb/wetland.php?ctid=20
七股鹽田重要濕地        
八掌溪口重要濕地        
八掌溪中游暫定重要濕地        
大鬼湖重要濕地        
大樹人工暫定重要濕地        
永安鹽田暫定重要濕地
北門重要濕地        
四林格山暫定重要濕地        
白河國小人工暫定重要濕地        
半屏湖暫定重要濕地        
四重溪口暫定重要濕地        
四草重要濕地
布袋鹽田重要濕地        
朴子溪河口重要濕地        
好美寮重要濕地        
官田重要濕地        
武洛溪人工暫定重要濕地        
林園人工暫定重要濕地
東源暫定重要濕地        
南仁湖重要濕地        
洲仔重要濕地        
屏東科技大學人工暫定重要濕地        
茄萣暫定重要濕地        
海生館人工暫定重要濕地
崁頂暫定重要濕地        
高雄大學暫定重要濕地        
鳥松暫定重要濕地        
援中港暫定重要濕地        
曾文溪口重要濕地        
楠梓仙溪重要濕地
鳳山水庫暫定重要濕地        
嘉南埤圳重要濕地        
嘉南藥理科技大學人工暫定重要濕地        
龍鑾潭重要濕地        
彌陀暫定重要濕地        
鰲鼓重要濕地
麟洛人工暫定重要濕地        
鹽水溪口重要濕地
http://wetland-tw.tcd.gov.tw/WetLandWeb/wetland.php?ctid=22
青螺重要濕地
清水重要濕地
菜園暫定重要濕地
慈湖重要濕地



## 資料應用

### 蒐集各種應用觀點與推論方法

公園生態化，公園內的水域生態復育
http://taipei-ecopark.sow.org.tw/#dev
https://sites.google.com/view/ecopark/%E8%A8%88%E7%95%AB%E7%B7%A3%E8%B5%B7

滯洪池濕地生態功能評價指數建立及應用
https://bit.ly/2k8PuH9
本研究提出濕地狀況指數(IWC)進行滯洪濕地生態功能的評價，並選擇以下四處滯洪池進行IWC 的評價應用：
1.臺北市大溝溪滯洪池 + 大湖滯洪池；
2.嘉義縣新塭滯洪池南池 + 北池。

摘：利用 #SWMM 在都市滯洪池進行懸浮沉積物（TSS），氮（N）和磷（P）水質推估
https://www.facebook.com/100000212960177/posts/4338154589534930/

國際級及國家級重要濕地範圍內公有土地委託民間經營管理實施辦法
https://bit.ly/3b28qkx
https://bit.ly/2JdfOPg





