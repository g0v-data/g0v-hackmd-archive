---
title: "臺灣的用電著色地圖，或是雷同的運用。"
tags: 地圖化,電力,hackpad
---

# 臺灣的用電著色地圖，或是雷同的運用。

> [點此觀看原始內容](https://g0v.hackpad.tw/iTzLaacxmov)

### 序

2014-08-14_04:24:37 <[Michael_LI](https://www.irccloud.com/#%21/ircs://irc.freenode.net:6697/Michael_LI)\> 我在維基百科看到一句話　　觀察台電用電量就能得知全台灣的空屋率一樣
我們能夠有類似像氣象局的天氣雲圖，這樣的系統嗎？
（概念圖１）
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0f1fbdac17d1e5d83de61bb840f35291)

（概念圖２－１）
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_a122ec7d58b5e1a64651c079cd79f319)


（概念圖２－２）
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_1d57f3dbd51541516fe0d6685bbb52c5)



（概念圖３）
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_f9fd92144656a14120b28aa85ab2c685)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ac9c2e411a090212eb51a7ebc4b381d3)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_25a167e9fd0db79b4ccfb60b36092cd5)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_59a1cc4e629a970cdc75f472f6ee7830)



g0v.tw 後勤中心
[https://www.facebook.com/groups/g0v.general/permalink/666195263456883/](https://www.facebook.com/groups/g0v.general/permalink/666195263456883/)

［挖坑］臺灣的用電著色地圖，或是雷同的運用。

主旨：臺灣的用電著色地圖，或是雷同的運用。

說明︰
1.我在維基百科看到一句話，觀察台電用電量就能得知全台灣的空屋率一樣。

　其實在更早幾年前在別人文章中，描述美國大學開放式課程，也有研究過美kill me please各地的「用電量跟經濟成長」的關係。

2.順帶一提昨晚的新聞
　總統：核四封存　給後代保留選擇權（20140813公視晚間新聞）
　（文字）[http://news.pts.org.tw/detail.php?NEENO=276714](http://news.pts.org.tw/detail.php?NEENO=276714)
　（影片）[https://www.youtube.com/watch?v=9BDJDDPsu74](https://www.youtube.com/watch?v=9BDJDDPsu74)

3.雷同的運用，可能是「全台灣的醫院病床數量」、「人口分布」、「緊急疏散計畫、之前與之後人口分布」、「工業區、商業區、住宅區，土地面積」……等等。

　只要有固定的資料結構（甚至是辦公室文書軟體試算表），直接讓軟體系統圖讀取就能畫出來。

4.已經開好Hackpad了，請大家自己跳進來吧！
[https://g0v.hackpad.com/iTzLaacxmov](https://g0v.hackpad.com/iTzLaacxmov)

以上約略說明

Michael_LI
2014-08-14

\-\-\-\-
梁啟源：核四封存有感衝擊（本文是中華經濟研究院董事長梁啟源口述） \- 中華經濟研究院
資料來源：2014-04-29/經濟日報/A3版/話題
[http://www.cier.edu.tw/ct.asp?xItem=22134&ctNode=52&mp=1](http://www.cier.edu.tw/ct.asp?xItem=22134&ctNode=52&mp=1)
\-\-\-\-


## ＝＝以下開始＝＝

＊　 chewei 目前理解這個 project 想建構的是：
- 地理 \+ 資料：各自有許多種呈現的規格
| ［地理位置］ | ［某個描述］ |
| --- | --- |
| 1.經緯度 | 1.數值，例如降雨量，例如夜間光亮程度 |
| 2.地址 | 2.二選一，例如空屋或是，不是空屋 |
| 3.地號 | 3.一個範圍形狀，例如一筆土地地號的形狀，例如一塊濕地的邊界形狀 |
| 4.公路標示 | 4.一段圖文敘述，例如Ushahidi新聞，例如顧客對於餐廳店家評價 |
| 5.GSM (?) | 5.帶有估算基礎的描述，例如森林喬木數量，會是某單位面積多少顆，這樣的描述 |
| 6.其他地理位置的表達方式 | 6.移動方向，例如車流方向 |
|  | 7.必須經過計算之後的結果，例如一筆土地的價格必須要從地價與面積甚至土地的更多社會資料來計算出來 |
|  | 8.顏色 |
|  | 9.判別，例如用衛星圖判斷農田是否休耕與種植的作為種類 |
- ［地理+資料］複合屬性，來提供繪圖程式與出
- 圖成果，例如使用者選擇以「地號」+「複合型描述(該地號形狀、面積數值、產權描述...等等)」，這個情境可以初步參考：[DZ1984天龍特公地製作過程文章](http://dz1984.info/articles/Taipei_POP/)
- 考量時間維度，會不會有什麼樣貌？案例：[海平面上升未來預測](http://flood.firetree.net/)
- 考量資料協作系統，會不會有什麼樣貌？案例：[城市修理站](https://maps.google.com.tw/maps/ms?msa=0&msid=217100401029752166110.0004d9c794ba8af50962d&dg=feature)、[路殺社](https://www.facebook.com/groups/roadkilled/)
- 考量遊程化建構，會不會有什麼樣貌？案例：[裨海紀遊](https://www.youtube.com/watch?v=lcMntFlk6LU)
- [http://www.synthicity.com/urbancanvas/](http://www.synthicity.com/urbancanvas/)
- 使用者的介面，希望能夠以非程式專業者，也可以大量批次操作的介面，來設計與呈現
- 上述種種，令我這個非程式專業的人，回想起一個心願：[土地議題資料再思考](http://hackfoldr.org/POPonFire/inGknR6JoZW)

名稱發想
- Issuemap 一休地圖 / 議題製圖器，[形象參考](http://attachment.van698.com/forum/201109/29/071503u8ribfpfz8ybuurc.jpg) / Mapping Issue
- 伊能圖（伊能忠敬所繪之日本地圖）
- Demomap / m and p /
- EverMap / Evermapper
- DataMapper
- 情境 / scenario / pop up












## 資源：相關研究

（１）
臺灣地區空屋狀況變遷與原因分析 An Analysis of High Housing Vacancy Rates in Taiwan
論文作者：彭建文 Peng, Chien-Wen
[https://db1n.sinica.edu.tw/textdb/tssci/listsrchpr.php?_op=?paperID:8675](https://db1n.sinica.edu.tw/textdb/tssci/listsrchpr.php?_op=?paperID:8675)
　　本研究透過臺電用電不足底度戶數資料推估各縣市歷年的空屋率以彌補每十年一次住宅普查的不足，發現三次住宅普查時各縣市空 屋率雖已明顯偏高，但大多並非該縣市空屋率的最高峰，且在過去二十年間各縣市空屋率均有相當明顯的波動趨勢。就房價與空屋率聯立模型的實證結果來看，房價 是影響空屋率最重要的變數，但其對於空屋率的影響為負，且在1990年之後房價仍呈現穩定上升的趨勢，應不是造成1990年之後空屋率大幅上升的主因。遷 徙率的相對影響力在1990年之後較家戶所得與住宅充裕度為低，且其水準值在1990年之後大效呈現小幅下降的趨勢，至於住宅異質性的水準值在1990年 之後雖呈現上升，但其係數值與相對影響力相當小，故本文推測1991～2001年間國內住宅市場空屋率大幅上升的現象，並非由於自然空屋率上升所造成，家 戶所得的增加使得其更有能力負擔住宅閒置成本或購置第二屋，加以政府宣告實施容積管制引發建商搶建，造成各縣市的住宅供給充裕度明顯上升，可能才是造成空 屋率大幅上升的主因。

（２）
[臺灣地區空屋調查分析](http://www.realestate.com.tw/duckhouse/paper/44.%E5%8F%B0%E7%81%A3%E5%9C%B0%E5%8D%80%E7%A9%BA%E5%B1%8B%E8%AA%BF%E6%9F%A5%E5%88%86%E6%9E%90.pdf) （1995/06）
作者：彭建文 陳永森 張金鶚 林秋瑾





## 資源：圖資系統

### （１）群眾的力量：開放街圖OpenStreetMap

文 / 雲端技術與系統整合組 常若愚
[http://www.nchc.org.tw/tw/e\_paper/e\_paper\_content.php?SN=134&SUB\_SUBJECT_ID=431&cat=industry](http://www.nchc.org.tw/tw/e_paper/e_paper_content.php?SN=134&SUB_SUBJECT_ID=431&cat=industry)
[OpenStreetMap](http://www.openstreetmap.org/#map=8/23.611/120.768)
[http://www.openstreetmap.org/](http://www.openstreetmap.org/#map=8/23.611/120.768)[#map](https://g0v.hackpad.tw/ep/search/?q=%23map&via=iTzLaacxmov)[=8/23.611/120.768](http://www.openstreetmap.org/#map=8/23.611/120.768)

OpenStreetMap 十週年簡報，原來可以這樣用Overpass Turbo!
[https://docs.google.com/presentation/d/1ey85IHqupj7aWxq92RzqHa2wzurFQLxJPg\_wXIwrGyY/edit#slide=id.g39309296d\_0124](https://docs.google.com/presentation/d/1ey85IHqupj7aWxq92RzqHa2wzurFQLxJPg_wXIwrGyY/edit#slide=id.g39309296d_0124)


### （２）用 cesium 做個一個簡易 3D 動態雨量圖

[https://www.facebook.com/photo.php?fbid=10152531256840668&set=a.443101975667.251316.713795667](https://www.facebook.com/photo.php?fbid=10152531256840668&set=a.443101975667.251316.713795667)

Chia-liang Kao

demo: [http://env.g0v.tw/3drain/](http://env.g0v.tw/3drain/)

我國氣象局上週納入水利署 143 座無人雨量站資料，並隨即以 xml 格式提供十分鐘雨量資料！

為了表示肯定，用 cesium 做個一個簡易 3D 動態雨量圖（雖然還沒用到新資料，但這是正規氣象站的每小時資料，顯示上週台南大雨當天動畫）

(cesium 超強，可以切換 2d, 2.5d, 3d 模式, ctrl-捲動可以改變視角.... )

接下來可以加上累積雨量呈現、瞬間雨量顏色（或動畫）、chart、即時十分鐘雨量，歡迎跳坑。

有興趣的朋友，也可以研究一下 cesium 開發團隊 AGI 提出的新標準 CZML, 和 KML 相比主要是增加可以描述歷史的空間資訊，讓這類跨時的視覺化可以用表述的，而不需要寫程式。

source: [https://github.com/g0v/env.g0v.tw/tree/current/src/3drain](https://github.com/g0v/env.g0v.tw/tree/current/src/3drain)


(3) [http://issuemapping.net/Main/Tools](http://issuemapping.net/Main/Tools)
(4) [http://gis.rchss.sinica.edu.tw/google/?p=2107](http://gis.rchss.sinica.edu.tw/google/?p=2107)



### （３）氣候監看地圖

村長：講個秘訣：[http://env.g0v.tw](http://env.g0v.tw) 週末由 [Ricky Chou](https://www.facebook.com/choupi.tw) 升等成 Kriging 平滑演算法，漸層地圖看起來更自然了，可以直接拿去畫各個時間點的，應該會比 cluster 均價要漂亮

（來源）[https://www.facebook.com/groups/g0v.general/permalink/673922016017541/?comment\_id=674439305965812&offset=0&total\_comments=14](https://www.facebook.com/groups/g0v.general/permalink/673922016017541/?comment_id=674439305965812&offset=0&total_comments=14)





## 資源：資料視覺化（資訊圖表（infographics））

關鍵字：資訊視覺化（Information and Data Visualization）
　　　　資訊圖表（infographics）

a-1.漢斯·羅斯林（Hans Rosling 1948年7月27日-- ）[演講錄影整理表](https://zh.wikipedia.org/zh-tw/%E6%B1%89%E6%96%AF%C2%B7%E7%BD%97%E6%96%AF%E6%9E%97#.E6.BC.94.E8.AC.9B.E9.8C.84.E5.BD.B1)

a-2.David McCandless：資料視覺化的美麗（2010年7月TED演講）
[（TED網站）](http://www.ted.com/talks/david_mccandless_the_beauty_of_data_visualization?language=zh-tw)（[YouTube](https://www.youtube.com/watch?v=aK0Y_jNdXRM)）
　　（[介紹文](http://tedxtaipei.com/2012/12/the-beauty-of-data-visualization/)）David McCandless：資訊視覺化，橫跨美感和理解力的設計

a-3.[20140505 為什麼­需要資料視覺化：漢堡、核四、車禍­ by 李慕約](https://www.youtube.com/watch?v=jGOYK-kkNEY) (MLDM Monday)
　　　　（[MLDM Monday 節錄／10分鐘／](https://www.youtube.com/watch?v=11kg1O2QBu0)）
講者：Muyueh Lee/李慕約 ( [http://muyueh.com/1314/](http://muyueh.com/1314/) )


a-4.[製作視覺資訊圖表（infographic）的三大要素及相關工具](http://www.inside.com.tw/2011/04/29/infographic-how-to)／2011年4月29日／

[Rapid Web Visualisations with d3plus](https://popluscon.hackpad.com/Rapid-Web-Visualisations-with-d3plus-Grey-Room-last-session-Wednesday-XEsMMe0y0tC)

[http://dataviva.info/](http://dataviva.info/)

## 資源：Open Data

（１）
--->
[https://groups.google.com/forum/embed/?place=forum/g0v-general#!topic/g0v-general/xTIZAWHJaiU](https://groups.google.com/forum/embed/?place=forum/g0v-general#!topic/g0v-general/xTIZAWHJaiU)

所有資料皆取自行政院原子能源委員會Open Data

大家好，我是Debra
有個朋友何雲咸一自己作了一個report 系統
[http://wd-nuclear.azurewebsites.net/](http://wd-nuclear.azurewebsites.net/)
目前版本功能：
1\. 可以看6座核能機組的現況
2\. 可以確認輻射測站的監測

不知道各位大大有什麼建議，請多多指教～


（２）
--->
[https://www.facebook.com/groups/g0v.general/permalink/717213428355066/](https://www.facebook.com/groups/g0v.general/permalink/717213428355066/)

Faryne Hsieh
以前曾經爬過台電贊助的一些活動資料，不知道合不合大家胃口？

資料來源主要是從這裡來的：[http://info.taipower.com.tw/php/main\_4\_6\_d\_new.php?kind=04&valu=](http://info.taipower.com.tw/php/main_4_6_d_new.php?kind=04&valu=)\[YYYY%2FMM\]&bg=1

資料時間則是從2003年開始


Faryne的實驗室 台電用電量、各能源發電量及敦親睦鄰等資料
[http://ha2.tw/energy/neighbor](http://ha2.tw/energy/neighbor)









## 資源：？








## 附錄Ａ：正在建造中的資訊系統

１）[2014-08-22／民間救災系統交流小聚／台北場／](https://g0v.hackpad.tw/2014-08-22-WMaKLjBljub)
２）[防災開放資料應用典範](https://osmtw.hackpad.com/LKgdTOFMlpD)
３）[高雄氣爆和登革熱爆發地圖視覺化（登記日2014-11-09）](https://g0v.hackpad.tw/NpPQ1UZc3Up)
４）[地震資訊的視覺化](https://g0v.hackpad.tw/zEoZ8BiWkEE)
５）
６）
７）






