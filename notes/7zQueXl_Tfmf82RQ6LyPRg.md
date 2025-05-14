---
tags: 糖鐵
---

# 待拆分內容

## 20201206 g0v Summit Unconf 議程討論《糖業鐵路與綠道 Taisugar Railway Greenway》

主要工作目標，能夠彙整「路線的最新情報」

- (1) 民間關注者的踏查內容, 位置化
    - 包含一手踏查
    - 二手內容的
- (2) 台糖與公部門的決策
    - 決策關係人，包含產權，以及再利用規劃權，例如：
        - 蒜頭糖廠與高鐵嘉義站之間的路線，正在評估復駛
        - 烏樹林糖廠 - 有觀光轉型，營運事業處、遊憩事業部
        - 新營糖廠 - 台南區處在管理，土地開發處  

### 踏查內容位置化

架構討論
https://photos.app.goo.gl/A7WwCNudPJML8tmz8

欄位資料架構：
- 從地理範圍來了解該範圍內有沒有與糖鐵相關的人事物，可能採用「鄉鎮區」尺度，村里有點太小
- 從特定的路線名稱來查找，例如「安平線」、「長短樹線」、「長短樹側線」、「長短樹信號所」
- 從特定內容類型來查找，例如 GISdata、新聞、素材蒐集、論文與專書、標案、法人團體、踏查內容類型
- 地圖試作：糖鐵 - 踏查與訊息彙整地圖
    - https://goo.gl/maps/PMgha916sMnfRaMw8
- 地理資料
    - 希望找到可以有單筆地理資料獨立網址的線上地圖服務，但目前沒有找到可以有單筆地理資料獨立網址
    - GoogleMyMap：優點方便協作、展示穩定、疊其他圖層、提供衛星與地標地名底圖
        - 課題：無法將文字欄位與 Airtable 資料庫整合起來
        - 構想：
            - GoogleMyMap 繪製路線之後，欄位內輸入相對應的 Airtable 素材卡片公開瀏覽網址
            - 這個方案是便利於「踏查圖層 KML」的完整度，但對於 Airtable 踏查素材來說似乎沒有解決其踏查內容對應的踏查路徑地理資料
    - Geojson.io
        - 課題：無法將文字欄位與 Airtable 資料庫整合起來
    - Airtable + mapfiddle
        - mapfiddle 紀錄單筆形狀: http://mapfiddle.org；使用說明：http://bit.ly/2YxBjSw
        - 課題：平時無法即時地圖化呈現以登載的資料，且真的要地理化的話必須透過寫程式進行文字整合
    - Airtable 本身給定 點座標
        - 課題：
            - (1) 無法記載線或面資料
            - (2) Airtable2sheet2map 要手動更新

製糖產業文化地景．行動地圖構想 
- 圖層：路線車站糖廠圖層
- 圖層：已行動的案例
- 圖層：照片、影片、踏查成果
- 圖層：行動空間指認，對接協助地方政府爭取營造資源
    - 文資保存
    - 閒置空間與綠地
    - 在地可以使用的綠廊
- 縣市範圍：台中、彰化、雲林、南投、嘉義縣、嘉義市、台南、高雄

盤點歷年，屬於支持糖鐵地景行動，的公私部門資源種類
- 社區營造政策措施：
- 林務局社區林業保育：
- 地景藝術節
- ..

其他資料登載平台
- wikidata
- wikicommons, [shootme 企劃，鼓勵貢獻者補充尚缺的內容](https://meta.wikimedia.org/wiki/WikiShootMe)
- OSM


---
# 資料蒐集

## 歷史資料


社團
https://www.facebook.com/groups/TSRTPCR/


- GIS dataset 產業地景的資料集：路線、生產設施、建物、交通設施...等

台湾 臺糖鐵道 廃線跡 配線図式路線図
https://goo.gl/maps/A573xDMLcejm3pX39
- 待確認：圖資來源、車站數量

手押台車
https://www.facebook.com/groups/tcmcu.rail/permalink/6209024002546037/

1927
https://www.facebook.com/groups/boo15212004/permalink/3597512696929813/

1934 年地圖
https://www.facebook.com/193577570812069/posts/1590294037807075/

1953年 1：150000台糖鐵道網圖
https://www.facebook.com/groups/TSRTPCR/posts/9759692370733306/
https://gis.sinica.edu.tw/showwmts/index.php?s=tileserver&l=TM150K_1953&fbclid=IwY2xjawKRTKhleHRuA2FlbQIxMABicmlkETFoWDM0dUIwZWdxTU1wQURLAR4pSRVxf8010qLPfNFluJiIymvmU-F4RVun0Ywf4PgME2YbdOhzkN908p2sCQ_aem_bygKmK3pNvcfp5TliMN4rQ

1978 年臺糖鐵道平面、分佈圖
https://www.facebook.com/100000140451245/posts/1974497915898204/

日治時期製糖廠分布圖
https://data.depositar.io/dataset/rd15-09142

https://data.gov.tw/dataset/41592

台灣製糖工場百年文史地圖
http://map.net.tw/taisugar/

台灣歷史文化地圖
https://thcts.sinica.edu.tw/view.php
* rd15-09141	經濟產業	日治時期	大正八年(1919)製糖場原料採取區域圖	大正八年(1919)製糖場原料採取區域
* rd15-09142	經濟產業	日治時期	日治時期製糖廠分布圖	臺灣地形圖糖業相關點
* rd15-09143	經濟產業	日治時期	日治時期糖鐵分布圖	臺灣地形圖西部平原糖業鐵道
* rd15-09143-1	經濟產業	日治時期	日治時期糖鐵營業線分布圖	大正四年(1915)糖鐵營業線起迄點、大正四年(1915)糖鐵營業線

日治時期糖鐵分布圖
https://data.depositar.io/dataset/rd15-09143

日治時期糖鐵營業線分布圖
https://data.depositar.io/dataset/rd15-09143-1

大正八年(1919)製糖場原料採取區域圖
https://data.depositar.io/dataset/rd15-09141

台湾製糖鉄道，台湾中部から南部にかけてナローの線路が網の目のように張り巡らされていた
http://762mm.world.coocan.jp/sepiaironosyashintyou.html

老照片【糖廠類】【鐵道類】【文物類】【地圖類】
https://www.tmitrail.org.tw/work-content/1460

日治時期(明治年間)糖業政策對區域重組的影響-以台灣南部鳳山廳、蕃薯藔廳及阿緱廳為例；辻原万規彦, 今村仁美(2022) 明治期台湾における糖業政策が地域の再編成に与えた影響−台湾南部の鳳山庁，蕃薯藔庁，阿緱庁を対象に，日本建築学会計画系論文集87巻(2022)797号p.1395-1406
https://doi.org/10.3130/aija.87.1395


臺灣故事島，要再查找相關內容
https://storytaiwan.tw/default.html

國家文化記憶庫，要再查找相關內容
https://www.facebook.com/groups/odtwn/permalink/3890906557590400/

糖業文化資產
https://www.taisugar.com.tw/chinese/CP3.aspx?n=10053

- 影音

youtube，以「糖鐵」、「糖業鐵」(糖業鐵路、糖業鐵道) 作為關鍵字
https://www.youtube.com/results?search_query=%E8%87%BA%E7%B3%96%E9%90%B5


## 研究與探討：產業地景與文化路徑

2004 研討會
https://www.facebook.com/groups/481564058685542/

臺灣糖業鐵道文化路徑人才培訓工作坊
https://event.culture.tw/BOCH/portal/Registration/C0103MAction

台糖簡報
https://www.facebook.com/844567332586544/posts/1212288195814454/

台灣糖業公司_五分車營運資料
目前台糖公司僅留存虎尾糖廠製糖運輸甘蔗原料路線及五處文化園區短程載運遊客導覽參觀路線。主要欄位說明：據點名稱、路線名稱、起訖站、營運路線長度單程公里數、交通部核准文號、通車營運日期
https://data.gov.tw/dataset/30043

台灣糖業鐵路經營之研究(1946─1982)
https://hdl.handle.net/11296/whud3y

南北平行預備線文化資產體系與價值研究
https://www.grb.gov.tw/search/planDetail?id=12986007

《臺灣糖廠與社宅街變遷圖集》
https://www.facebook.com/889701534373509/posts/2955597331117242/

台灣南部糖廠「會社住宅」布局規畫與盛行風向之關係
https://www.airitilibrary.com/Publication/alDetailedMesh?docid=10251464-201412-201503230015-201503230015-17-34

萬華糖廍文化園區
https://zh.wikipedia.org/wiki/%E8%87%BA%E5%8C%97%E8%A3%BD%E7%B3%96%E6%89%80
1942年興建一條長25公里連接製糖所所在的萬華與林口的原料線鐵道https://www.facebook.com/YangMingSt.studio/posts/2882177851837228

日治時期臺中州糖業與糖鐵之研究（1920~1945）
https://hdl.handle.net/11296/8e53nx

台中帝國製糖場

臺中 月眉糖廠
https://www.facebook.com/LEF.1992/posts/3245846148817069

南投牛運堀
https://www.facebook.com/share/p/E7eCctoCLUHsr6SQ/


彰化縣和美鎮
https://www.facebook.com/1335556088/posts/10216480439546933/

彰化
https://www.facebook.com/story.php?story_fbid=pfbid02RxTZbYTfgHd5C7PGUxvSEEdcrjPC47hTy7X59zY9Qn1XEzEx5uE7P3YY9vBHCD9Vl&id=680154561&mibextid=tejx2t

溪洲
https://www.facebook.com/share/p/q5yxhHLxmSUzPuhQ/

二林
https://www.newsmarket.com.tw/blog/162542/

濁水溪下游的糖業鐵道之興衰(1907-1970)
https://hdl.handle.net/11296/rm228n

雲林地區糖業鐵道營業線的發展與再利用（1908～2017）
https://hdl.handle.net/11296/7p2q53

北港糖廠、虎尾糖廠文化路徑
https://www.facebook.com/100005693567030/posts/1743891402477295/
雲林縣北港鎮天空之橋
https://www.twarchitect.org.tw/works/%e5%a4%a9%e7%a9%ba%e4%b9%8b%e6%a9%8b-%e7%b3%96%e9%90%b5%e7%b6%a0%e5%bb%8a/
23.57238429628925, 120.30474329584787

虎尾糖廠
https://www.facebook.com/story.php?story_fbid=pfbid0AsSLi4NGZsXDCd2EJi5FvGqmn3gkDQD9KnjBwzqudBtQbS4b5C96dhQrP2JmbVY8l&id=100002217764583&mibextid=qC1gEa
https://www.facebook.com/story.php?story_fbid=pfbid0ktRkTTQgVV4MK5W2faSzijMQEqPsb1wKwPsD3muvUAqupXKgKpYXUD3HURnGCnmyl&id=100002217764583&mibextid=qC1gEa
https://www.facebook.com/story.php?story_fbid=pfbid0imaS8DgNJqpNpGKzYPcYtV9GuCSXerTq3hv51GFoJqokVEAHeDzkko7mqC3r6nKql&id=1431886495


烏樹林
https://www.facebook.com/share/p/d6Xmj4H3Sx7vYgmA/

蒜頭糖廠的原料區與糖業鐵道之運作與發展
https://hdl.handle.net/11296/553gtv

斗南車站有糖鐵火車頭裝置

南靖糖廠
https://www.facebook.com/permalink.php?story_fbid=10215965909571914&id=1572837408

嘉義板頭社區
https://www.facebook.com/119767/posts/pfbid035uNuxHZyhYLj4ibMtLQBp4Pok43RUxScvraGmoEpW12ZaDKWm5xo4DeQZDTZzPTPl/

嘉義糖廠，光電，薯光計畫
https://www.facebook.com/groups/solarpvgsa/permalink/3566357663596142/

甘蔗渣堆肥販售
https://www.facebook.com/story.php?story_fbid=pfbid0367AWbo9PNezvj39PB9K7mLXdRasyiXXB4SG8HDeaHLQyM9NqeBD14Gy47fycM4c6l&id=164564180266981&mibextid=tejx2t

蕭壠文化園區前身係臺南佳里糖廠倉庫群
https://soulangh.tnc.gov.tw/page/aboutsl/1.php

臺南市仁德區十鼓仁糖文創園區
https://www.twarchitect.org.tw/works/%e5%8d%81%e9%bc%93%e4%bb%81%e7%b3%96%e6%96%87%e5%89%b5%e5%9c%92%e5%8d%80%e5%a4%a9%e7%a9%ba%e6%ad%a5%e9%81%93%e8%88%87%e7%b3%96%e8%9c%9c%e4%b8%89%e9%80%a3%e7%bd%90/
仁德，臺糖車路墘製糖所彌陀堂
https://www.facebook.com/groups/176223359193164/permalink/1849750825173734/

台南台糖循環聚落，有使用到糖廠糖鐵材料
https://www.facebook.com/1669923855/posts/10216706116639865/

農村型糖鐵振興案例：（2020/05/26報導）台南水土保持局補助，可望重現玉井善化線（台南左鎮五分車站）
糖鐵台南玉井和善化線中間的左鎮五分車車站，幾乎被拆殆盡，只有少數月台遺址及一間早年車站的廁所
透過糖鐵（玉善線）舊鐵道文化再現，串聯左鎮化石文化園區及左鎮老街，更可進一步連結山上水道博物館、玉井噍吧哖事件園區，擴大連結偏鄉區域的觀光資源
https://news.housefun.com.tw/news/article/724256255637.html

嘉南大圳
https://m.facebook.com/story.php?story_fbid=pfbid034xTDNS2iNCLbcWkW5fNoRa1DxB6pGmSxS9edQwH7yvB79r7KYkf8jSRa7ZfuY4yJl&id=100000126638407

隆田chacha文化資產教育園區Culture Heritage Area
https://udn.com/news/story/7208/6016088

麻豆糖廠，文學基地
https://news.ltn.com.tw/news/life/breakingnews/3803543

麻豆 龍泉月臺
https://www.facebook.com/archiblurlab/posts/2648327368716980
https://solomo.xinmedia.com/archi/183882-ArchiBlurLab

新營糖廠
https://www.taiwanhot.net/news/887382/%E7%B3%96%E9%90%B5%E8%87%AA%E8%A1%8C%E8%BB%8A%E9%81%93%E8%88%87%E5%9C%B0%E6%99%AF%E5%85%AC%E5%9C%92%E7%8D%B2%E7%8D%8E%E9%80%A3%E9%80%A3+%E5%B0%87%E6%96%BC12-27%E9%96%8B%E5%9C%92

社子
https://www.facebook.com/104064960947000/posts/429326671754159/


https://www.facebook.com/100000066795897/posts/5590536717625166/

台南東山
https://times.hinet.net/news/23245271

岸內糖廠，影視基地
https://siow3033.wixsite.com/austronesiaformosa/post/%E5%8F%B0%E5%8D%97%E9%B9%BD%E6%B0%B4%E5%B2%B8%E5%85%A7%E5%BD%B1%E8%A6%96%E5%9F%BA%E5%9C%B0-%E5%BE%A9%E5%88%BB%E6%97%A5%E6%B2%BB%E6%99%82%E6%9C%9F%E5%8F%B0%E5%8C%97%E6%A6%AE%E7%94%BA%E8%A1%97%E6%99%AF-%E7%AC%AC%E4%B8%80%E6%9C%9F%E5%BB%BA%E9%80%A0-%E6%96%AF%E5%8D%A1%E7%BE%85-%E6%B8%85%E4%BB%A3%E6%BC%A2%E4%BA%BA%E5%B8%82%E8%A1%97%E7%89%87%E5%A0%B4-%E9%87%8D%E7%8F%BE%E6%98%8E%E6%B8%85%E6%99%82%E6%9C%9F%E5%8F%B0%E7%81%A3%E5%BA%9C%E5%9F%8E%E8%A1%97%E5%9D%8A-2022-03-18

糖業鐵道遊客旅遊動機、滿意度與重遊意願之研究 – 以烏樹林糖廠觀光五分車為例
https://hdl.handle.net/11296/tpxbjp
烏樹林糖廠
https://www.facebook.com/liuzhongriver/posts/2070596476430771

高雄新興製糖株式會社之糖鐵路線
http://gis.rchss.sinica.edu.tw/mapdap/?p=5505&lang=zh-tw

橋頭糖廠
https://m.facebook.com/story.php?story_fbid=pfbid02zZZhAsdeW3tfZEzv58p6PqBiqWVboXTRLC7MTTW89SrNLQimRypg7VVAG16iHu1Gl&id=100002217764583
高雄縣橋仔頭糖廠的空間型塑與再造
https://hdl.handle.net/11296/g63245

旗尾線
https://www.facebook.com/138322769540284/posts/3200398146666049/

旗山糖廠，1921年畫作
https://www.facebook.com/groups/boo15212004/permalink/4044721048875640/
老照片
https://www.facebook.com/story.php?story_fbid=pfbid02z9vYGsrFEEz8ZkWuc5Ad6p4WNJqYfYv1Fnk332ecNosm633gL7sN8hGHQAEsvesql&id=1397171762&mibextid=qC1gEa

屏東縣台糖縣民公園，舊糖廠與紙漿廠的遺址
https://www.facebook.com/fangyi.lin/posts/10164610790055231

研究論文：明治40年代から大正期の台湾卑南渓流域における製糖業が地域開発に与えた影響（1910~1925年間臺灣卑南溪流域新式製糖業對於區域發展之影響）
https://www.facebook.com/asgis/posts/4920941587916130

台東糖廠
https://www.hakkatv.org.tw/news-detail/1669091541688357


糖鐵文化路徑，行動架構
https://www.tmitrail.org.tw/work-content/1457

台糖公司土地開發處文資暨綜合經營組
https://solomo.xinmedia.com/archi/170904-trw

以「糖鐵」、「糖業鐵」("糖業鐵"路、"糖業鐵"道)、「糖文化」、「糖業文化」作為關鍵字，搜尋歷年政府標案採購網，網頁：
https://ronnywang.github.io/pcc-viewer/search.html?query=%E7%B3%96%E9%90%B5

### 綠道

國發會「建構綠道網絡之策略規劃」計畫
立法院 108年3月6日 國家綠道法 草案，內容中有提到七條國家綠道
https://www.lawbank.com.tw/news/NewsContent.aspx?NID=158883.00

綠道與基礎設施/產業遺址的關係：
- 綠道 與 水路
- 綠道 與 糖鐵 
- 時而並行，時而交匯，有時重疊，主要是藉由綠道親近河川、走近糖鐵與產業地景

## 台糖資產資料

台灣糖業公司_資產公告主檔
https://data.gov.tw/dataset/101668
台灣糖業公司_資產公告土地明細資料
https://data.gov.tw/dataset/101669
台灣糖業公司_土地招標設定地上權資訊
https://data.gov.tw/dataset/25746
地段地號
台灣糖業公司_土地標租資訊
https://data.gov.tw/dataset/25749
地段地號
台灣糖業公司_可供出租土地資訊
https://data.gov.tw/dataset/25754
鄉鎮名稱、段號名稱、小段名稱、母號、子號、分號
台灣糖業公司_不動產標售資訊
https://data.gov.tw/dataset/25752
地段地號
台灣糖業公司_房屋及設備標租資訊
https://data.gov.tw/dataset/25760
地段地號


台灣糖業公司 可供出租土地資訊
https://kiang.github.io/taisugar_lands/

## 其他發想

談甘蔗園的隱蔽性與伏兵
https://www.facebook.com/tsiankok/posts/pfbid0W7aVTwSqjTCNWLsJtqqij7A3VZVmzgWin2uLSP9nomYTHYPPNMj5AUbkuvYCDzhnl

糖廠副產物應用於土壤加勁及穩定方案 
https://www.facebook.com/ch2532/posts/pfbid02fni6iaWU3nkCosqTYU2sLEeecvRMr4fwni6Sfeuty9TU1uHngFRmnriMKDK8rfQXl

觀光化，光電車輛的可行性？
https://fb.watch/c-ulohd8oB/
人力車

物質流通
盆種農業的輸送帶
防火帶，線型分佈的機能或營造需求

水泥產業的鐵路，竹東
https://www.facebook.com/story.php?story_fbid=pfbid0fVBfrgcQWvAdt2LWCzFG3hW1stge6DZzUEFXKZvARUFooLgrfeZAPqfz9nGukiDml&id=1335556088