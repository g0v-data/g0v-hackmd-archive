---
tags: planning,
---

# 空間計畫書圖與都市計畫書資料三星化｜方法討論

:::warning
文件目錄
[TOC]
:::

## 文本試作

- [開放都市計畫-南港區都市計畫通盤檢討](https://g0v.hackmd.io/xT8KXxEqTfeBsBGQsqZZVQ)
- [內湖都市計畫(主要計畫)通盤檢討(公開展覽版本)](https://g0v.hackmd.io/d7-mlkxGQY2zWGOX0F4Ptw?view)
- [中興新村整體規劃](https://g0v.hackmd.io/Pa6Dqb5xRGKxAzA4qnRhDw)

## 探討

各級都市計畫委員會組織規程第十二條之一修正條文
- 第十二條之一　　內政部、各級地方政府及鄉（鎮、市）公所應將都市計畫委員會之委員名單、會議議程及會議紀錄等相關資訊，公開於網際網路。
- https://www.facebook.com/100000050611688/posts/2148801475131519/

摘自 Dongpo：TimBL 的開放資料五顆星所著重的點在於資料的開放性，因此第一顆星的開放資料就要是以開放授權釋出，若這資料還是結構化資料(非圖片，機器難以處理的)，那滿足二顆星，如果進一步是非專屬格式，如 CSV，則滿足三顆星，若資料可以開放到，資料集中每一筆資料本身在網路中都有一個 URI 來指涉，就滿足了第四顆星的開放資料，一般做法就是以 RDF 的格式，因為有了URI，所以資料集中的資料可以透過語意相互連結，這就是五顆星等級開放資料，也就是常說的Linked Open Data。

摘自 [au](https://www.facebook.com/photo.php?fbid=10153780069039928&set=a.124614179927.102488.728309927&type=3)：在心態上，只要還是「先有資料 → 再來開放」，發佈變成產出的下游，中間的描述資料（metadata）就會流失，或是參差不齊。

“Context matters”: a framework to help connect knowledge with policy in government institutions
https://blogs.lse.ac.uk/impactofsocialsciences/2017/12/19/context-matters-a-framework-to-help-connect-knowledge-with-policy-in-government-institutions/

摘自王祖修：我個人認為都市計畫書和圖應該分開處理。一來都市計畫書應該開始思考怎樣結構化，畢竟裡面充滿著跟全民有關的資訊，而卻用很不資訊結構的方式撰寫，二來都市計畫圖則是看其來源母圖資訊，有的是透過都市計畫樁和都市計畫區地形圖展繪，有的是與地籍圖套繪，而地籍圖卻又不全部都是數值重測區，這部分是可以好好討論一番。最後才是怎樣把都市計畫書中特殊的資訊和土管要點、限制連結到都市計畫圖，過去研究過並不是不能結構化，而結構化的好處更可以讓這部分資訊透明公開。

針對一張工程計畫位置地圖，使用 AI 工具轉為地理資料 https://www.facebook.com/share/p/17t72nuxKr/

Richard Hsieh> 進行到現在對於書籍的資料結構化大概就是幾點需要克服
1. 每一本書的章節編排不同，是要統一，還是保持獨特性?
2. 表格的結構每個都不同，不能用單一個parser去處理

以下影片 2:45:30 講者卓易霆，提到都市計畫書圖應該更開放! 演講場次直播連結：
https://www.facebook.com/104177642015294/videos/278830100848743/

摘自 Whiski Tajfun：我覺得在談這些東西與資料之間的關係時，應該要想到一個重點 : 為什麼要這樣做？第一個好處當然是搜尋時能更容易找到我們要的東西（不是靠全文檢索，然後靠不同的演算法去推論）。而第二個好處是，很多報告其實是綜合了更多其他的資料/資訊後彙整而成。那我們有沒有機會，透過這樣的拆解，讓一份報告只保留他核心的東西，剩下其他所有引用的數據，資料等，都可被視為模組後。只是在這邊被組合起來產生我們要的結果而已？
然後進一步，我們是否有機會，以後就只須要把模型建立好，各個不同模組（資料集）各自準備好，就可自動產生許多 routine 型的報告？例如外交部每年都會出的年報？
- 來源：[https://www.facebook.com/groups/odtwn/permalink/1766653240015753/](https://www.facebook.com/groups/odtwn/permalink/1766653240015753/)

chewei>
- 正面表列一些都市計畫書圖中，必定會出現的內容，例如：
    - 每一本「都市計畫通盤檢討案計畫書」，都會整理「歷年都市計畫案發布實施情形」，通常都是用表格的方式呈現，或許可以成為一個表格開放資料項目。
    - 「人民陳情意見綜理表」
    - ...
- 主辦單位應該同時提供計畫書內的各種「ＯＯＯＯ現況示意地圖」的原始資料集或資料網址。
- 換個角度來說，書圖資料開放，也是「都市計畫知識體系」的知識管理課題。
- 所以什麼是三顆星等級的都市計畫書圖？
    - 一本都市計畫書=內文文字資料+地理範圍資料+人口推估資料+特定議題的表格+cc授權圖片...
    - 等號右邊各項資料皆符合開放資料三顆星等級，並且容易獨自抽出；各項資料或圖文的排版順序或之間的前後文位置也可以被機器所察覺；如此一來，民間可以較方便地重製都市計畫書圖，並且容易製成展示性、互動性高的書圖呈現方式，也可以依照民間觀點混搭更多資料來討論都市計畫內容，或是更多應用。
- 「活」都市計畫書
    - 都市計畫內容中的援引資料，能否以「即時動態資料」、「依據開放資料來做計算」等方式呈現？例如人口資料、環境資料。
    - 分析程式碼可以考量釋出
    - 都市計畫通盤檢討原則自動化、定期演算...
    - 群眾通報與意見討論
- 書圖內容中，若提到各種實體應有獨一無二的 id 可指涉 (像是縣市代碼、里、公共設施...)
- 結構化的書圖資料，提供 API
- [提問] 如果想要知道一個地理範圍內，(從古至今) 各種大大小小的空間變動事件，可以參考什麼樣的公部門資料來源？
    - https://www.facebook.com/groups/470451239772824/permalink/743070939177518/

【協作】都市計畫書應該有什麼內容?
都市計畫書記載了對於一個都市區域的規劃概念以及相關必要的知識。在<都市計畫法>裡，規定了至少必須有的內容。但 #光是法律規定的一定不夠阿 ，這個投票活動讓大家票選「你認為一個好的都市計畫，報告書裡應該要有什麼內容?」
預設選項是法規的內容，歡迎加入自己的選項! 對於現在的選項有其他意見? 歡迎在留言串和大家分享你的想法!投票結果在未來會嘗試運用在專案的內容中!
https://www.facebook.com/groups/470451239772824/permalink/1123867904431151/

## 開放資料實作參考

- [五星等開放資料標準](https://g0v.hackpad.com/imlFqCxzU1f)
- 二星等級的「[內湖區都市計畫書](https://g0v.hackpad.com/--pJUQ0AGRCO1)」
- 針對水利流域規劃的典禮地圖圖片，運用資料再製出數位檔案 https://www.facebook.com/groups/LASSnet/permalink/3077227455861177/
- 論文：[建構資料欄位關係之知識本體–以空氣品質、國土利用、人口統計資料為例](http://hdl.handle.net/11296/xwn462)
- 研討會文章：[知識本體架構下的實務設計—以智慧型都市計畫審議系統為例](https://www.naer.edu.tw/ezfiles/0/1000/attach/54/pta_1787_6036179_54806.pdf)
- [看起來最簡單就是對的](https://speakerdeck.com/clkao/lao-dong-bu-yan-xi?slide=70&hc_location=ufi)
    - 一個資料集若有多個報表，每一個[報表應該獨立抽出](https://speakerdeck.com/clkao/lao-dong-bu-yan-xi?slide=66&hc_location=ufi)
    - 不要額外標頭
    - 不要小計
    - 不要合併儲存格、不要標頭拆欄
- [Excel 資料轉換工具 (將 Excel 同格式的各分頁合成一個 CSV 的工具)](https://g0v.hackpad.tw/jkpco57DjJH)
- [公務員開放資料Lesson 1](https://hackpad.com/Lesson-1-ver1.0-XdDvvmJJ6Zf)
- 既有 PDF 內容開放化的方法蒐集
    1.  PDF 內的文字：PDF 將報告書變成 markdown
    2.  PDF 內的表格：PDF tables extractor：[https://ronnywang.github.io/pdf-table-extractor/](https://ronnywang.github.io/pdf-table-extractor/)
    3.  PDF 內的圖片：？
    4.  PDF 內的地理資料示意圖片：將有地圖表達內容的 JPG 定位於電子地圖上
- 文章結構化
    - clkao \[7:11 PM\] 這個可以用 gitbook, 我寫過一個 gitbook-toc-styles 的 plugin；[https://g0v-tw.slack.com/archives/general/p1476702693001306](https://g0v-tw.slack.com/archives/general/p1476702693001306)
    - mrorz \[11:15 PM\] 如果需要把「壹、一、(一)、1、(1)、a、i⋯」轉換成格式化資料的話，可以參考這個 [https://github.com/g0v/ppt-commitment-parser](https://github.com/g0v/ppt-commitment-parser)；[https://g0v-tw.slack.com/archives/general/p1476803719001335](https://g0v-tw.slack.com/archives/general/p1476803719001335)
    - Archie Markup Language [http://archieml.org/](http://archieml.org/)
- 判決書結構化
    - [https://approachfusion.wordpress.com/2017/03/08/%E8%A6%AA%E8%BF%91%E4%BA%BA%E6%B0%91%E7%AC%AC%E4%B8%80%E6%AD%A5%EF%BC%9A%E5%88%A4%E6%B1%BA%E6%9B%B8%E7%9A%84%E8%B3%87%E8%A8%8A%E7%B5%90%E6%A7%8B/](https://approachfusion.wordpress.com/2017/03/08/%E8%A6%AA%E8%BF%91%E4%BA%BA%E6%B0%91%E7%AC%AC%E4%B8%80%E6%AD%A5%EF%BC%9A%E5%88%A4%E6%B1%BA%E6%9B%B8%E7%9A%84%E8%B3%87%E8%A8%8A%E7%B5%90%E6%A7%8B/)


## 其他書圖開源化展示構想參考案例

- 字體應用與文字視覺化
    - 只有文字的簡報，也能賞心悅目！2個步驟讓文字型簡報清楚易懂
        - [http://www.managertoday.com.tw/articles/view/51842](http://www.managertoday.com.tw/articles/view/51842)
    - 如何選擇簡報的字體？17張圖片說給你聽 [http://tesa.today/article/734?utm\_source=pnn&utm\_medium=pnn\_post&utm\_campaign=pnn](http://tesa.today/article/734?utm_source=pnn&utm_medium=pnn_post&utm_campaign=pnn)
    - 曾將文字視覺化過嗎？這個網頁蒐集分類了 254 種不同的文字視覺化作品，讓我們能快速篩選出有興趣的主題，裡面也不乏許多特別的視覺化方式，有時間要多找幾篇來學習！網址：[http://textvis.lnu.se/](http://textvis.lnu.se/)
    - Typography Manual 10 Tips To Improve Your Type. [https://www.facebook.com/theFuturisHere/videos/539891576208566/](https://www.facebook.com/theFuturisHere/videos/539891576208566/)
    - 設計與視覺效果的決定性因子：字型學奧義 [https://www.stockfeel.com.tw/%E8%A8%AD%E8%A8%88%E8%88%87%E8%A6%96%E8%A6%BA%E6%95%88%E6%9E%9C%E7%9A%84%E6%B1%BA%E5%AE%9A%E6%80%A7%E5%9B%A0%E5%AD%90%EF%BC%9A%E5%AD%97%E5%9E%8B%E5%AD%B8%E5%A5%A7%E7%BE%A9/](https://www.stockfeel.com.tw/%E8%A8%AD%E8%A8%88%E8%88%87%E8%A6%96%E8%A6%BA%E6%95%88%E6%9E%9C%E7%9A%84%E6%B1%BA%E5%AE%9A%E6%80%A7%E5%9B%A0%E5%AD%90%EF%BC%9A%E5%AD%97%E5%9E%8B%E5%AD%B8%E5%A5%A7%E7%BE%A9/)
    - 字卡 [https://uxdesign.cc/design-better-cards-c0d12ab581c4#.u7kth1cli](https://uxdesign.cc/design-better-cards-c0d12ab581c4#.u7kth1cli)
- 簡報
    - 轉貼：前一陣子「前瞻基礎建設計畫」新聞簡報特別熱門，經過我們實際動手改造之後，發現真正值得著墨的不僅是設計，更應該是「資訊強化的手法」，包括進度列的應用、跨頁資訊整合，以及比較資訊凸顯 [https://youtu.be/on9BPJqa1Ss](https://youtu.be/on9BPJqa1Ss)
    - 如何處理簡報中的長篇文字
        - [https://www.youtube.com/watch?v=-BYLEQaYLGg](https://www.youtube.com/watch?v=-BYLEQaYLGg)
- 與手機裝置結合的書圖內容設計
    - [https://www.facebook.com/viner.omer/posts/10216499112772664](https://www.facebook.com/viner.omer/posts/10216499112772664)
- AR
    - 認識土石流AR
        - [https://www.facebook.com/246.swcb/posts/885586204834076](https://www.facebook.com/246.swcb/posts/885586204834076)
    - 計畫內容採用擴增實境方式呈現，參考 環境地質災害教育開放平台APP 擴增實境(AR)
        - [https://www.youtube.com/watch?v=M2OGvkT-OM4&feature=youtu.be](https://www.youtube.com/watch?v=M2OGvkT-OM4&feature=youtu.be)
    - コミュニティの防災と復興にICTツールを活用
        - [https://www.facebook.com/WorldBankTokyo/photos/a.263977476982025.62248.262970030416103/867100286669738/?type=3&theater](https://www.facebook.com/WorldBankTokyo/photos/a.263977476982025.62248.262970030416103/867100286669738/?type=3&theater)
    - HERE Reality Lens is the next big thing in GIS
        - [http://geoawesomeness.com/here-reality-lens/](http://geoawesomeness.com/here-reality-lens/)
    - [https://www.facebook.com/EuropeanResearchCouncil/posts/866400026793939](https://www.facebook.com/EuropeanResearchCouncil/posts/866400026793939)
    - 蔣渭水文化行 [https://www.facebook.com/tavar.tw/videos/1321743067850240/?hc_ref=NEWSFEED](https://www.facebook.com/tavar.tw/videos/1321743067850240/?hc_ref=NEWSFEED)
    - [http://www.techbang.com/posts/47238-first-google-tango-phones-finally-went-on-sale-augmented-reality-into-reality-now](http://www.techbang.com/posts/47238-first-google-tango-phones-finally-went-on-sale-augmented-reality-into-reality-now)
    - [https://www.facebook.com/eyejackapp/](https://www.facebook.com/eyejackapp/)
    - AR×印刷實作 講座 [https://www.facebook.com/events/125925077912126/](https://www.facebook.com/events/125925077912126/)
    - [https://www.coco-ar.jp/tw/cocoar/page03.html](https://www.coco-ar.jp/tw/cocoar/page03.html)
    - [http://www.psfk.com/2016/02/augmented-reality-book-kinect-projection.html](http://www.psfk.com/2016/02/augmented-reality-book-kinect-projection.html)
    - [https://www.facebook.com/verge/videos/1085105428192466/](https://www.facebook.com/verge/videos/1085105428192466/)
    - [https://share.america.gov/virtual-tour-white-house/](https://share.america.gov/virtual-tour-white-house/)
    - [https://www.facebook.com/streetartglobe/videos/2295606753996071/](https://www.facebook.com/streetartglobe/videos/2295606753996071/)
- Holographic technology
    - [https://www.facebook.com/techinsider/videos/754036748128017/](https://www.facebook.com/techinsider/videos/754036748128017/)
- 紅藍立體影像
    - 3D立體成像技術就是紅藍立體影像，專有名稱是Anaglyph image，需搭配紅藍濾片眼鏡使用。Anaglyph Maker是一款免費的小工具，可以將兩張視差照片輕鬆製作成紅藍立體影像。 [https://www.facebook.com/asgis/posts/1832950736715246](https://www.facebook.com/asgis/posts/1832950736715246)
- gif
    - 實際案例
        - [http://makeagif.com/i/Dan2qr](http://makeagif.com/i/Dan2qr)
        - [http://www.spaceandmatter.nl/de-ceuvel](http://www.spaceandmatter.nl/de-ceuvel)
        - [http://yle.fi/uutiset/3-8607731](http://yle.fi/uutiset/3-8607731)
        - [http://lenagroeger.com/datagifs](http://lenagroeger.com/datagifs)
        - 河流流動 [https://www.facebook.com/abesdn/posts/1079002765574569](https://www.facebook.com/abesdn/posts/1079002765574569)
        - 空間綠化方案 [https://www.facebook.com/greaterlondonnationalparkcity/videos/1715562771789936/](https://www.facebook.com/greaterlondonnationalparkcity/videos/1715562771789936/)
    - 工具
        - Gifs.com 輕鬆將 YouTube 影片轉為 Gif 動態圖片，可產生鏈結用於 Facebook 塗鴉牆 [https://free.com.tw/gifs-com/?utm\_content=buffer3a4de&utm\_medium=social&utm\_source=facebook.com&utm\_campaign=buffer](https://free.com.tw/gifs-com/?utm_content=buffer3a4de&utm_medium=social&utm_source=facebook.com&utm_campaign=buffer)
        - [https://free.com.tw/google-data-gif-maker/](https://free.com.tw/google-data-gif-maker/)
        - Geogif with Qgis [https://urbandemographics.blogspot.tw/2017/12/making-geogif-with-qgis.html](https://urbandemographics.blogspot.tw/2017/12/making-geogif-with-qgis.html)
- 滑鼠與圖片切換效果。例如以下網頁中有 Mouse-over 的圖片
    - [http://fairbanksfodar.com/understanding-fodar](http://fairbanksfodar.com/understanding-fodar)
- 「前後對照」的工具。例如以下網頁
    - [https://www.wired.com/2016/10/klinenberg-transforming-communities-to-survive-climate-change/](https://www.wired.com/2016/10/klinenberg-transforming-communities-to-survive-climate-change/)
    - [http://brickcitylive.com/promoted/newarkarts/before-after-murals-public-art-transformed-newark-streetscapes/](http://brickcitylive.com/promoted/newarkarts/before-after-murals-public-art-transformed-newark-streetscapes/)
- 今昔照片對照
    - [http://www.gjtaiwan.com/~Prince/ttm/?id=46](http://www.gjtaiwan.com/~Prince/ttm/?id=46)
- 衛星圖變遷
    - [https://www.facebook.com/steven.ho.7/posts/1950593764951453](https://www.facebook.com/steven.ho.7/posts/1950593764951453)
- Cinemagraph 單張動畫圖
    - [https://flixel.com/products/mac/cinemagraph-pro/](https://flixel.com/products/mac/cinemagraph-pro/)
    - [https://www.facebook.com/flixelphotos/videos/810832755690151/](https://www.facebook.com/flixelphotos/videos/810832755690151/)
- 環景影像
    - [http://eyehouse.pixnet.net/blog](http://eyehouse.pixnet.net/blog)
- 視覺圖像 / Graphic Recording / Graphic Facilitation
    - [http://www.videoscribe.co/](http://www.videoscribe.co/)
    - [https://www.facebook.com/RaeChooou/videos/1607159759535588/](https://www.facebook.com/RaeChooou/videos/1607159759535588/)
    - [https://www.facebook.com/cmalapitan/videos/10156140950725453/?hc\_ref=PAGES\_TIMELINE](https://www.facebook.com/cmalapitan/videos/10156140950725453/?hc_ref=PAGES_TIMELINE)
    - [https://www.facebook.com/niemanlab/posts/10154548506393654](https://www.facebook.com/niemanlab/posts/10154548506393654)
- 用色議題
    - [https://www.facebook.com/groups/718089658359103/permalink/737226316445437/](https://www.facebook.com/groups/718089658359103/permalink/737226316445437/)
    - [https://g0v.hackpad.com/PeIJH77AjNt](https://g0v.hackpad.com/PeIJH77AjNt)
- 表格
    - [https://uxdesign.cc/design-better-data-tables-4ecc99d23356](https://uxdesign.cc/design-better-data-tables-4ecc99d23356)
- 事件新聞時間軸工具
    - [https://medium.com/mirrormedia/%E5%BE%9E-%E8%A1%97%E9%A0%AD%E9%81%8B%E5%8B%95%E4%B8%80%E5%B9%B4%E5%9B%9E%E9%A1%A7-%E7%9A%84%E6%99%82%E9%96%93%E8%BB%B8%E8%AB%87%E6%96%B0%E8%81%9E%E4%BA%8B%E4%BB%B6%E8%B3%87%E6%96%99%E5%BA%AB-a878205d8ccb](https://medium.com/mirrormedia/%E5%BE%9E-%E8%A1%97%E9%A0%AD%E9%81%8B%E5%8B%95%E4%B8%80%E5%B9%B4%E5%9B%9E%E9%A1%A7-%E7%9A%84%E6%99%82%E9%96%93%E8%BB%B8%E8%AB%87%E6%96%B0%E8%81%9E%E4%BA%8B%E4%BB%B6%E8%B3%87%E6%96%99%E5%BA%AB-a878205d8ccb)
- 線上資料展示與網站
    - [http://www1.nyc.gov/site/planning/plans/east-new-york/east-new-york-1.page](http://www1.nyc.gov/site/planning/plans/east-new-york/east-new-york-1.page)
    - 長照 2.0 政策核定本
        - 官方文件：[https://www.facebook.com/mohw.gov.tw/posts/717856648380756](https://www.facebook.com/mohw.gov.tw/posts/717856648380756)
        - 民間 github repo：[https://github.com/OpenData-TW/Long-term-Care](https://github.com/OpenData-TW/Long-term-Care)
    - 報告書內容同時摘要成網頁版或簡要版
        - [https://www.facebook.com/pg/FarmingUrbanismNetwork/photos/?tab=album&album_id=671589712992720](https://www.facebook.com/pg/FarmingUrbanismNetwork/photos/?tab=album&album_id=671589712992720)
        - [https://deltaprogramma2017.deltacommissaris.nl/viewer/publication/1/1-deltaprogramma-](https://deltaprogramma2017.deltacommissaris.nl/viewer/publication/1/1-deltaprogramma-)
        - [http://atavist.creatgood.com/atavist-tutorial](http://atavist.creatgood.com/atavist-tutorial)
    - 衛生福利統計 \- 互動式指標查詢系統
        - [https://www.facebook.com/mohw.gov.tw/posts/622153297951092?qsefr=1](https://www.facebook.com/mohw.gov.tw/posts/622153297951092?qsefr=1)
    - 英國《金融時報》與氣候變遷知識創新體（Climate-KIC）共同製作了有趣的氣候變遷互動圖表，清楚顯示各國的減碳承諾對於全球氣溫的影響
        - [https://www.facebook.com/twreporter/videos/1660398940874638/](https://www.facebook.com/twreporter/videos/1660398940874638/)
    - [https://projects.propublica.org/graphics/rockisland](https://projects.propublica.org/graphics/rockisland)
    - Interactive Maps
        - [http://www.dvrpc.org/Mapping/Webmaps/](http://www.dvrpc.org/Mapping/Webmaps/#googtrans/en/zh)[#googtrans](https://g0v.hackpad.tw/ep/search/?q=%23googtrans&via=2qR2Pzdu95W)[/en/zh](http://www.dvrpc.org/Mapping/Webmaps/#googtrans/en/zh) DVRPC has developed several interactive mapping applications as part of our continuing effort to support planning and improve decision-making in our region. Within each application, you can view geographic features, query selective data sets, create your own custom map and access detailed reports about certain features. These web mapping applications allow DVRPC to present geospatial information to the public without the need of special GIS software. DVRPC will continue to add mapping applications in the future so check back frequently. For more information regarding DVRPC's full GIS services or to order custom maps, contact the Office of GIS.
        - Climate Adaptation Atlas [http://www.ruimtelijkeadaptatie.nl/en/climate-adaptation-atlas](http://www.ruimtelijkeadaptatie.nl/en/climate-adaptation-atlas)
        - [http://www.3di.nu/](http://www.3di.nu/)
    - [http://foodstrategyblueprint.org/](http://foodstrategyblueprint.org/)
    - MAPPING INEQUALITY Redlining in New Deal America
        - [https://dsl.richmond.edu/panorama/redlining/](https://dsl.richmond.edu/panorama/redlining/#loc=4/36.71/-96.93&opacity=0.8)[#loc](https://g0v.hackpad.tw/ep/search/?q=%23loc&via=2qR2Pzdu95W)[=4/36.71/-96.93&opacity=0.8](https://dsl.richmond.edu/panorama/redlining/#loc=4/36.71/-96.93&opacity=0.8)
    - 先讓大家自己畫出心中的感受，再來看看你跟真實數據的差異有多少吧！
        - [https://musou.watchout.tw/draw/tsai-first-year/](https://musou.watchout.tw/draw/tsai-first-year/)
        - [https://bl.ocks.org/1wheel/07d9040c3422dac16bd5be741433ff1e](https://bl.ocks.org/1wheel/07d9040c3422dac16bd5be741433ff1e)
        - [https://www.nytimes.com/interactive/2017/01/15/us/politics/you-draw-obama-legacy.html](https://www.nytimes.com/interactive/2017/01/15/us/politics/you-draw-obama-legacy.html)
        - [https://www.nytimes.com/interactive/2017/04/14/upshot/drug-overdose-epidemic-you-draw-it.html](https://www.nytimes.com/interactive/2017/04/14/upshot/drug-overdose-epidemic-you-draw-it.html)
        - [https://www.nytimes.com/interactive/2015/05/28/upshot/you-draw-it-how-family-income-affects-childrens-college-chances.html](https://www.nytimes.com/interactive/2015/05/28/upshot/you-draw-it-how-family-income-affects-childrens-college-chances.html)
    - 可以讓操作者知道自己選擇的這些事情方案的後果想像
        - [http://my2030.twenergy.org.tw/](http://my2030.twenergy.org.tw/)
        - 預算分配遊戲 [Cases Study](https://g0v.hackpad.tw/FoVI6xhJJ32)
    - Planetizen 推薦的空間規劃網站
        - [Top 10 Websites - 2014](http://www.planetizen.com/websites/2014)
        - [Top 10 Websites - 2013](http://www.planetizen.com/websites2013)
        - [Top 10 Websites - 2012](http://www.planetizen.com/websites/2012)
    - [https://www.facebook.com/groups/hackshackerstaipei/permalink/949575255178390/](https://www.facebook.com/groups/hackshackerstaipei/permalink/949575255178390/)
    - What can a technologist do about climate change?
        - [http://worrydream.com/ClimateChange/](http://worrydream.com/ClimateChange/)
    - [https://www.facebook.com/groups/datasci.tw/permalink/1259839204093467/](https://www.facebook.com/groups/datasci.tw/permalink/1259839204093467/)
- 內容互動引導
    - [http://worrydream.com/#!2/LadderOfAbstraction](http://worrydream.com/#!2/LadderOfAbstraction)
    - [http://worrydream.com/#!/ExplorableExplanations](http://worrydream.com/#!/ExplorableExplanations)
    - 用視覺化來學機率和統計
        - [http://students.brown.edu/seeing-theory/index.html](http://students.brown.edu/seeing-theory/index.html)
    - Tools to Monitor and Visualize Microservices Architecture
        - [https://www.facebook.com/groups/DevOpsTaiwan/permalink/1516300381790336/](https://www.facebook.com/groups/DevOpsTaiwan/permalink/1516300381790336/)
        - Vizceral Open Source [https://medium.com/netflix-techblog/vizceral-open-source-acc0c32113fe](https://medium.com/netflix-techblog/vizceral-open-source-acc0c32113fe)
- A note about "The Humane Representation of Thought"
    - [http://worrydream.com/TheHumaneRepresentationOfThought/note.html](http://worrydream.com/TheHumaneRepresentationOfThought/note.html)
    - [https://vimeo.com/115154289](https://vimeo.com/115154289)
- 人口資料呈現方式
    - [https://www.facebook.com/data.visualize/posts/556397781197335](https://www.facebook.com/data.visualize/posts/556397781197335)
    - 2017 Revision of World Population Prospects
        - [https://esa.un.org/unpd/wpp/](https://esa.un.org/unpd/wpp/)
- 地圖
    - 紐約市，由民間建立的都市計畫圖臺，形成對於公部門的都市計畫資料文件應進一步公開的參考
        -    https://www.facebook.com/photo.php?fbid=10157200835434038&set=gm.1240488282769112&type=3&theater&ifg=1
    - 台大校園規劃小組會議記錄的查詢系統運用地圖介面
        - [http://homepage.ntu.edu.tw/~cpo/search_map.html](http://homepage.ntu.edu.tw/~cpo/search_map.html)
        - 把各個計畫項目，落到地圖上
   - 新界東北地圖
        - https://hongkongnt.wordpress.com/2014/07/20/%E6%96%B0%E7%95%8C%E6%9D%B1%E5%8C%97%E5%9C%B0%E5%9C%96-%E8%AB%8B%E7%94%A8%E6%95%B8%E6%93%9A%E4%BE%86%E8%AA%AA%E6%9C%8D%E6%88%91/    
    - 納入歷史地圖 [http://tpstation.com.tw/](http://tpstation.com.tw/)
    - 地號轉地圖：[Land No. Mapper](https://g0v.hackpad.com/uhB6qAwYXe5)
    - [https://mapstory.org/](https://mapstory.org/)  the atlas of change that everyone can edit
    - [http://mapfiddle.org/](http://mapfiddle.org/)
    - Real-time Collaborative GIS [https://www.gislounge.com/real-time-collaborative-gis/](https://www.gislounge.com/real-time-collaborative-gis/)
    - StoryMapJS [http://blog.infographics.tw/2015/05/tell-story-with-storymapjs/](http://blog.infographics.tw/2015/05/tell-story-with-storymapjs/)
    - Top 19 geovisualization tools, APIs and libraries that will let you create beautiful web maps
        - [http://geoawesomeness.com/top-19-online-geovisualization-tools-apis-libraries-beautiful-maps/](http://geoawesomeness.com/top-19-online-geovisualization-tools-apis-libraries-beautiful-maps/)
    - 用地圖查詢人口 New tool to get population estimates for any user-defined area
        - [https://urbandemographics.blogspot.com.br/2018/02/new-tool-to-get-population-estimates.html](https://urbandemographics.blogspot.com.br/2018/02/new-tool-to-get-population-estimates.html)
- 3D 地形建物地圖
    - [https://www.facebook.com/esri.tw/posts/2122531571096939](https://www.facebook.com/esri.tw/posts/2122531571096939)
    - QGIS + Threejs 立體地圖
        - [https://www.facebook.com/data.visualize/posts/551072538396526](https://www.facebook.com/data.visualize/posts/551072538396526)
        - [https://anitagraser.com/2014/03/15/3d-viz-with-qgis-three-js/](https://anitagraser.com/2014/03/15/3d-viz-with-qgis-three-js/)
        - [http://www.statsmapsnpix.com/2016/12/interactive-terrain-mapping-in-qgis.html](http://www.statsmapsnpix.com/2016/12/interactive-terrain-mapping-in-qgis.html)
        - [http://bl.ocks.org/infographicstw/c434624afe673a173d7959049a666f71](http://bl.ocks.org/infographicstw/c434624afe673a173d7959049a666f71)
    - [http://vizicities.com](http://vizicities.com)
        - github
        - see your city in 3D
    - ArcGIS for Developers
        - [http://bit.ly/1BFElBL](http://bit.ly/1BFElBL)
    - sketchup
        - 單機版 [https://www.facebook.com/SaveNangangBottleCapFactory/posts/543191265861342](https://www.facebook.com/SaveNangangBottleCapFactory/posts/543191265861342)
        - 3D warehouse（分享檔案）
        - online sketchup app
            - 似乎還不能多人協作？
    - 3D模型免安裝直接看網站
        - [http://inplus.tw/archives/773](http://inplus.tw/archives/773)
        - P3D [https://p3d.in/](https://p3d.in/)
        - Sketchfab [https://sketchfab.com/](https://sketchfab.com/)
            - [https://sketchfab.com/ChunliangChen](https://sketchfab.com/ChunliangChen)
        - Verold [http://inplus.tw/archives/773](http://inplus.tw/archives/773)
    - Web Geological Modeling in 3D with Geomodelr. View what’s changed with a new tutorial.
        - [https://www.facebook.com/groups/openwebgis/permalink/697701923724419/](https://www.facebook.com/groups/openwebgis/permalink/697701923724419/)
    - This app turns your doodles into 3D-printable designs.
        - [https://www.facebook.com/circuitbreaker/videos/1385411161495223/](https://www.facebook.com/circuitbreaker/videos/1385411161495223/)
    - 主題型企畫案例
        - Morningside Heights Historic District Explorer
            - [https://nyclpc.maps.arcgis.com/apps/webappviewer3d/index.html?id=abd5f6ae90f049bd9359681c9ac1402d](https://nyclpc.maps.arcgis.com/apps/webappviewer3d/index.html?id=abd5f6ae90f049bd9359681c9ac1402d)
            - This 3D web map allows users to learn more about the Morningside Heights Historic District, which the New York City Landmarks Preservation Commission designated on February 21, 2017.
        - 「Pottermore」將哈利波特中的霍格華茲魔法學院以 3D 互動式視覺化方式重現於網頁之中，並在學院中藏了 100 個故事中事件的熱點，你能否把全部的熱點找齊呢？
            - [https://www.facebook.com/data.visualize/videos/730184203818691/](https://www.facebook.com/data.visualize/videos/730184203818691/)
- 地殼尺度的變動
    - 台北盆地變遷 [https://g0v.hackpad.tw/960UZCNn91G](https://g0v.hackpad.tw/960UZCNn91G)
    - Here is a great animation by Dr. Tanya Atwater showing the general evolution of southern California and the formation of the Channel Islands. [https://www.facebook.com/IRISEarthquake/videos/10156421768214974/](https://www.facebook.com/IRISEarthquake/videos/10156421768214974/)
- 實體展現
    - 地理實體動態展現
        - [https://g0v.hackpad.tw/UKuLtU2KoKf](https://g0v.hackpad.tw/UKuLtU2KoKf)
    - Dynamicland is an authoring environment, and everyone is an author. People make what they need for themselves. They learn through immersion. The true power of the dynamic medium — programmability — is for everyone.
        - [https://dynamicland.org/](https://dynamicland.org/)
- 施工動畫
    - [https://m.youtube.com/watch?feature=share&v=TE6s9MTSHUI](https://m.youtube.com/watch?feature=share&v=TE6s9MTSHUI)
- 手繪線稿立體化
    - [MentalCanvas (Drawing in the third dimension)](https://www.facebook.com/US.NSF/videos/10153417392322900/)
        - [https://www.microsoft.com/zh-tw/store/p/mental-canvas-player/9nblggh5794n?ocid=\_soc\_omc\_\_fb\_photo\_no\_fbmc&utm\_source=facebook.com&utm\_medium=referral](https://www.microsoft.com/zh-tw/store/p/mental-canvas-player/9nblggh5794n?ocid=_soc_omc__fb_photo_no_fbmc&utm_source=facebook.com&utm_medium=referral)
- Holographic Displays
    - [https://www.facebook.com/circuitbreaker/videos/1627954684164021/](https://www.facebook.com/circuitbreaker/videos/1627954684164021/)
    - [https://www.facebook.com/GIGadgets.Fans/videos/1268088253270461/](https://www.facebook.com/GIGadgets.Fans/videos/1268088253270461/)
- 多元描述空間的方法
    - [https://twstreetcorner.org/2016/08/16/min-jay-kang/](https://twstreetcorner.org/2016/08/16/min-jay-kang/)
    - 魚眼圖 [https://www.facebook.com/mao.isle/posts/1088780487806261](https://www.facebook.com/mao.isle/posts/1088780487806261)
    - [時間週期](https://g0v.hackpad.tw/--ijOviYoN0qC)
- 360 影像分享工具平台
    - [https://site.vizor.io/products](https://site.vizor.io/products)
- VR
    - 從奇點到眾點
        - [https://www.facebook.com/notes/%E5%94%90%E9%B3%B3/%E5%BE%9E%E5%A5%87%E9%BB%9E%E5%88%B0%E7%9C%BE%E9%BB%9E/1360357927326757](https://www.facebook.com/notes/%E5%94%90%E9%B3%B3/%E5%BE%9E%E5%A5%87%E9%BB%9E%E5%88%B0%E7%9C%BE%E9%BB%9E/1360357927326757)
    - VR 促進空間規劃協作審議的可能性說明 [https://www.facebook.com/audreyt.org/posts/10154371791049928](https://www.facebook.com/audreyt.org/posts/10154371791049928)
    - Engaging Mobility [http://www.fcl.ethz.ch/research/responsive-cities/engaging-mobility.html](http://www.fcl.ethz.ch/research/responsive-cities/engaging-mobility.html)
    - Virtual Reality for Civic Deliberation [https://youtu.be/EynGwOoxlSE](https://youtu.be/EynGwOoxlSE)
    - [https://www.facebook.com/dwshift/videos/1335164806537172/](https://www.facebook.com/dwshift/videos/1335164806537172/)
    - EXPERIENCE A JOURNEY DOWN THE LA RIVER IN VIRTUAL REALITY [http://larivervr.org/](http://larivervr.org/)
    - Google Earth VR版上線，支援HTC Vive
        - [https://www.facebook.com/story.php?story_fbid=1370466182963706&id=889701534373509](https://www.facebook.com/story.php?story_fbid=1370466182963706&id=889701534373509)
    - 來玩VR吧──免費軟體大集合 [http://www.makezine.com.tw/make2599131456/makers-introduction-vr-best-software-tools-free](http://www.makezine.com.tw/make2599131456/makers-introduction-vr-best-software-tools-free)
- MR=VR+AR
    - [https://www.facebook.com/unwirehk/videos/10157550466890495/](https://www.facebook.com/unwirehk/videos/10157550466890495/)
    - [http://3d4medical.com/category/support/complete-anatomy/updates](http://3d4medical.com/category/support/complete-anatomy/updates)
    - [https://www.facebook.com/humansofthefuture/videos/777788065712208/](https://www.facebook.com/humansofthefuture/videos/777788065712208/)
- Fact Check
    - 技術講解 NPR 如何即時 fact-check 美國總統辯論
        - [https://www.facebook.com/groups/XinMeiTi/permalink/1858831684350651/](https://www.facebook.com/groups/XinMeiTi/permalink/1858831684350651/)
    - 預測落空的都市計畫內容檢視
        - [https://g0v.hackpad.com/rKIJb9vys5k](https://g0v.hackpad.com/rKIJb9vys5k)
- 內容中若提及「歷年都市計畫」
    - 附上當年的計畫圖 [https://www.facebook.com/asgis/posts/1101994936477500](https://www.facebook.com/asgis/posts/1101994936477500)
- 審議過程
    - 「在英國開發案同樣會面對許多人的反對，艾奕康公司也提出一個在 Cirencester開發住宅的案例，討論過程跟委員的意見都清楚地呈現在網路上，可看出審議過程耗時極久，網站上也看出 各委員是否支持開發案」
        - [http://www.wiltsglosstandard.co.uk/news/15830345.The\_big\_decision\_take\_two\_Bathurst\_plan\_for\_2\_350\_homes\_in\_Cirencester/](http://www.wiltsglosstandard.co.uk/news/15830345.The_big_decision_take_two_Bathurst_plan_for_2_350_homes_in_Cirencester/)
    - 中文文字來源：[https://bit.ly/2JqEJir](https://bit.ly/2JqEJir)
- 爭點思路、意見蒐集
    - sli.do [https://www.sli.do/home](https://www.sli.do/home) 活動提問線上蒐集與投票功能
    - pol.is [https://pol.is/home](https://pol.is/home) 立場趨向
    - Argument [http://ch.arguman.org/](http://ch.arguman.org/) 「反向推論」思路開展與瀏覽者支持意見
    - Debater 辯論家 [Debater ](https://g0v.hackpad.tw/vjeJIZ8onSY) 內容彙整平台
    - 各種時間軸呈現平台 [http](https://g0v.hackpad.tw/cjdeZ8orXk4)[s://g0v.hackpad.tw/cjdeZ8orXk4](https://g0v.hackpad.tw/cjdeZ8orXk4)
- 與數學演算相關
    - Desmos 的「Function Carnival」利用互動圖表引導學生繪圖，並試著重現一次示範影片的砲彈人軌跡，藉以學習函式的概念。網址: [https://teacher.desmos.com/carnival](https://teacher.desmos.com/carnival)
    - 城市與數學 [https://g0v.hackpad.com/nMQKLwW23pn](https://g0v.hackpad.com/nMQKLwW23pn)
- 開源文本構想
    - [開源出版 / 開源取向的知識內容構成方法](https://g0v.hackpad.com/--SBFSdruovNE)
- 遊戲化 [Gamification](https://g0v.hackpad.tw/FM4rSNL725L)


