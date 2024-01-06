---
title: "視覺化分享會 1 (12/5) - 筆記"
tags: hackpad
---

# 視覺化分享會 1 (12/5) - 筆記

> [點此觀看原始內容](https://g0v.hackpad.tw/kdSkZHKiwT0)

## The Eyes Have It: A Task by Data Type Taxonomy for Information Visualizations / 欣穎

資料類型
- 1D / 2D / 3D / Temporal / Multi-dimensional / Tree / Network

互動類型
- Overview / Zoom / Filter / Details-on-demand / Relate / History / Extract

討論
- 以 foundi 房地資訊站為例與論文對話
- 資訊探索本身就是一個過程，所以保持歷史的行動、允許使用者折回是重要的。然而，大多數圖表未能提估這項要求（用戶、工程師權限問題）

小結
- 區分資料圖表的資料類型做分類
- 把資訊圖表中的功能，並陳述對這些功能的建議做法
- 放在當代檢視
    - 功能設計的不同考量：需求導向 or 資料、平台、技術導向的功能設計
- 研究資訊圖表原型的用意
    - 成功的商業產品：共同具備之功能
    - 產生吸引力：迅速提供資訊，並且允許使用者探勘（降低參與門檻）
    - 充分發揮效果：使用新型態的資料結構、高解析度螢幕、支援快速資料檢索、使用專門的資料結構和平行運算技術、使用者培訓

問題討論
- 作者有說為什麼這樣做比較好嗎？
    - 作者引用國外作品做為佐證。透過「找出共通點」的方式給出建議。

## How NOT to lie with Visualization / 妤庭

- [簡報在這裡](http://www.slideshare.net/HazelYutingWei/how-not-to-lie-with-visualization)
- 主要討論：顏色在複雜的資訊視覺化中會有什麼影響呢？如何善用「顏色」這個變因，讓資料更容易被理解？
- 1996，有點久以前的論文
- 慣用的顏色跟生理感官衝突

- PRAVDA：以認知為基礎的資料視覺清晰化架構
- 可以根據下列四項考量進行圖表與顏色的呈現
    - data type
    - data spatial frequency
    - visualization task
    - other design choices made by the user

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d3f096c455b4cef6c1ad0e24c001ef6a)
- 左上：紅色應該是最重要的，但是大家比較容易注意到綠色
- 左下：將區域勾勒出來

- 右上：呈現具可信度的資料架構
- 右下：吸引讀者目光在特定區域

圖表數據形式如何影響你的呈現結果？[ref](http://www.usablestats.com/lessons/noir)
- nominal data：refers to categorically discrete data such as name of your school
- ordinal data
- interval data：
- ratio data

Spatial Frequency [Figure 2](https://www.cs.ubc.ca/~tmm/courses/533-07/readings/pravda/figure2.jpg)
- 明度高低（黑 -  白）：適用 high spatial frequency
- 飽和度高低：適用 low spatial frequency
- 彩度高低：適用 low spatial frequency
- 傅立葉轉換：
    - 比較尖銳的 \- 高頻 high spatial frequency、細節多
    - 比較模糊的 \- 低頻 low spatial frequency、細節少

適當的數值分類設定很重要 [Figure 3](https://www.cs.ubc.ca/~tmm/courses/533-07/readings/pravda/figure3.jpg)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_a9a0f2cf33cfb261dd525f489bc4f8a5)
- low spatial frequency 呈現細緻數據
- high spatial frequency 太多會造成視覺混亂
    - 上面那張很像是下面那張的局部放大感

加上標記引導使用者看重要的地方 [Figure 4](https://www.cs.ubc.ca/~tmm/courses/533-07/readings/pravda/figure4.gif)

重視圖表的比較性 [Figure 5](https://www.cs.ubc.ca/~tmm/courses/533-07/readings/pravda/truevis.htm)

問題討論
- 演講一開始做的實驗（請會眾快速瀏覽一張颱風風速圖，瀏覽前並不知道圖片內容，並記下第一印象的顏色），對本文作者來說，會如何討論呢？
    - 他並沒有說什麼顏色是最適合的，討論的重點是太多的顏色會分散使用者的注意力


## Graphical Perception: Theory, Experimentation, and Application to the Development of Graphical Methods / Kirby

- "visual encoding"
- 就像一般的科學一樣，資料視覺化也需要科學的基礎。本篇探究資料覺化最基本的元素。

- elementary perceptual tasks
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_af6d0ca35be6c1257e16b53cb0518866)

常見的圖表有哪些元素？
- 散布圖：共同軸上的位置比較
- 圓餅圖：角度、面積
- 長條圖：長度、位置、面積
- 推積長條圖：最下面是比位置，上面是比長度


- 散布圖除了位置之外，還有「方向」，可以看出趨勢（e.g. 完全正相關）
- 體積圖的混淆：要用長度？還是面積？還是體積去判斷數據？


容易比較的順序（最容易 -\> 最難）
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_122ea60e19c09f9c86300b18e678d055)


- 有對齊的軸 位置
- 沒有對齊的軸
- 長度 length / direction / angle
    - why 沒有對齊的軸 比 長度更好比較？
        - 做一樣長的外框，即使位置不同也容易比較。Weber's Law 短的東西容易比較，外框會出現相對短的東西。
        - Stevens 1975：
            - （最精確）長度   面積   體積（最不精確）

- 在共同軸上，位置越近，越容易看得精確
- 圓餅圖的使用時機：只有兩個數值時
- 用推積長條圖不如用分組的點圖

- curve diff：用面積表示騙人騙很大
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c3c255e66dd062b580e2a01f09060f11)
> 驚
> [name=che l]

- 面積容易有 bias

- 網格：網格大的時候，會分不出來差異，覺得是同一群的，建議用長條圖或分組。我們對「一半/四分之一」的感受比較明顯

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_38c364639fec6fc4b4ae6161c241af95)

- 建議不要用長條圖的時機：減少圖表密度、不需要使用者看到很精確的數據差異，而是希望看到概觀的時候。例如如果左圖上的圈圈全部換成長條圖，可能會很擠。

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_e79721576ac14aacdabd80f81f0e5158)

- 總結各種元素：
    - （不精確）顏色 體積 面積 長度 位置（精確）
    - 有時後不一定是用最精確的，看設計需要跟目的



## Animated Transitions in Statistical Data Graphics / Annie

- 圖表的動態過場
    - 動態過場會讓使用者比較 engaging，但是也是雙面刃，用得太過，反而讓使用者分心
    - 大綱
        - 探究過場種類
        - 使用 DynaVis visualization framework
        - 結果: stage animation > animation ( 強硬的 ) > static ( ! )
- 什麼是 stage animation？
    - 一步一步來，例如：先換位置、再換形狀
    - 比較順的方式
    - 跟一般animation不同點在於視覺感受較不強烈

- 過場類型 ( Transition Types )
    - View Transformation / 視點的轉換 - 放大縮小平移
> 使用同一個 scale，看不同的 domain 
> [name=Muyueh L]

> [http://bl.ocks.org/mbostock/1667367](http://bl.ocks.org/mbostock/1667367)
> [name=Muyueh L]

    - Substrate Transformation
> 直接更改 scale 的方式，例如魚眼
> [name=Muyueh L]

> [http://bl.ocks.org/mbostock/3711652](http://bl.ocks.org/mbostock/3711652)
> [name=Muyueh L]

    - filtering / 過濾 ( 暗亮 / 消失出現 )
> [http://mbostock.github.io/d3/talk/20111116/iris-splom.html](http://mbostock.github.io/d3/talk/20111116/iris-splom.html)
> [name=Muyueh L]

    - Ordering/順序
> [http://bl.ocks.org/mbostock/3885705](http://bl.ocks.org/mbostock/3885705)
> [name=Muyueh L]

    - timestep - 隨著時間轉變
    - Visualization Change - 大變 ( 圓餅變長條 )
> [http://bl.ocks.org/mbostock/1256572](http://bl.ocks.org/mbostock/1256572)
> [name=Muyueh L]

    - Data Schema Change  \- 同樣的視覺呈現，但增加/減少呈現的資料
> [https://www.jasondavies.com/coffee-wheel/](https://www.jasondavies.com/coffee-wheel/)
> [name=Muyueh L]

- 設計需要考慮的東西
    - Congruce/ 一致性 and apprenshension (?)
        - (TBF)
        - max predictability
        - use simple transition
        - use staging for complex transitions ( 複雜的動畫要拆解 )
        - make transitions as long as need, but no longer ( 寧久也不複雜 )
    - DynaVis - C# \+ Direct3D製作的frame work
        - dynavis 針對上述設計了一些不同的實作方式，可以參考他怎麼做的
- 實驗
    - subject - 24 ( 10 F + 14 M ) 26 ~ 62 歲的受試者，會大量使用資料與圖表工作者
    - 方法
        - 看圖表 \+ Highlight 物體(三秒)，接著 Highlight 消失 & 發生動畫
        - 看受試者能否正確找到 Highlight 物體動畫過後的位置
    - 結果：
        - 動畫整體效果比較好，大多時候，stage animation的錯誤率低於animation
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_a7dd755f729f11f0278d8cbb1659c316)

- 結論
    - staged animation 較優，一般 animation 其次，直接跳轉最差。

- 利用這一個論文實作 d3.js transition 的案例：
    - pie chart
        - [http://bl.ocks.org/mbostock/4341417](http://bl.ocks.org/mbostock/4341417)
        - [http://bl.ocks.org/mbostock/1346410](http://bl.ocks.org/mbostock/1346410)
    - 不同種類
        - [http://bl.ocks.org/mbostock/1256572](http://bl.ocks.org/mbostock/1256572)



## Visualisation Techniques for Facilitating Decision Making in Urban Planning / 哲瑋

- 其他書籍分享
1.  Data-Driven Cities by a+u [https://www.japlusu.com/shop/product/au-201411](https://www.japlusu.com/shop/product/au-201411)
2.  《震災ビッグデータ ―可視化された“３・１１の真実” “復興の鍵” “次世代防災”》 [link](https://g0v.hackpad.tw/6R59i4HSsG8)
3.  台北原來如此 [https://g0v.hackpad.com/iAQIXPGNp4u](https://g0v.hackpad.com/iAQIXPGNp4u)

- [論文網址](http://www.ci-journal.net/index.php/ciej/article/view/264/404#sdfootnote1sym)｜[筆記專頁](https://abcd.hackpad.com/Visualisation-Techniques-for-Facilitating-Decision-Making-in-Urban-Planning-chswifYK9Gv)｜[摘要簡報](https://docs.google.com/presentation/d/1VpE_FTw47jt-N4-_jcMKRJC9K4nSk23n9vhcXyZy6-k/edit?usp=sharing)
- 怎麼樣的視覺化是比較容易促進討論的？
- PPGIS: 對社會的、質性的資料視覺化的探討工作
    - Public participatory geographical information systems
    - 利用視覺化小技巧在公眾參與的工作坊中 ( 主要在都市規畫 )
- Graphy Theory Representation: eg. 將實體街道納入居民使用節點的習性
    - 連結度, 交通可及性將道路著色 ( movement potentials )
    - 羅列街道相關議題做電訪 ( sense of place )
        - 將質性問題轉化成量化表，並以 1 ~ 5 (不同意 / 同意 )分級回答，例如:
            - 我住在這邊很滿意
            - 在這裡生活很安全
        - 也有 yes / no 類問題
        - 電訪結果，也著色呈現於道路底圖
    - 比較 movement & sense of place :
        - 囊底路雖然移動性差，sense-of-place 並不差
- 社會資料調查整合進地理資訊，轉換成直觀易懂的顏色序列呈現
- 由於審議場合中，討論過程中會有其他議題跳出，facilitator  能在回到資料庫抓取需要的資料，即時形成新的視覺資訊，讓與會者接續討論，進一步決策。
- 本文的書寫契機，一部分是來自於這篇論文
    - Bosworth, M. and J. Donovan (1998). "A Mapmakers Dream : Public Involvement Applications Utilization of GIS." NCGIA Specialist Meeting on "Empowerment, Marginalization, and Public Participation GIS"
    - 網址：[http://www.ncgia.ucsb.edu/varenius/ppgis/papers/bosworth.html](http://www.ncgia.ucsb.edu/varenius/ppgis/papers/bosworth.html)
- 類似社會意象與地理資訊的整合案例，介紹國內一篇災害資訊整合評估的論文
    - 《颱洪災害之**整合性脆弱度**評估－大甲溪流域之應用》洪鴻智、陳令韡，論文：[http://goo.gl/9XJbUc](http://goo.gl/9XJbUc)
    - 一般資訊 ( 淹水潛勢 etc ) 的呈現已有
    - 這篇論文進一步整合居民認知、敏感性 ( 風險知覺、資源取得力 ) 等資訊做「脆弱度」綜合評估
    - ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c4be7af8dc41d96d577db5c70eafc484)

問題討論
- 居民會不會害怕使用 PPGIS？
    - 要看部落的組成。如果是要跟耆老討論，或許用大地圖或實體模型會比較方便。
    - 如果是青壯年就沒什麼問題，而且 google earth 是由專門人操作，參與討論的人就看圖。

## Ending

Kirby：今天聚會的起源是這一篇文章
7 Classic Foundational Vis Papers You Might not Want to Publicly Confess you Don’t Know
[http://fellinlovewithdata.com/guides/7-classic-foundational-vis-papers](http://fellinlovewithdata.com/guides/7-classic-foundational-vis-papers)

如果大家有興趣請到  零傳媒  [http://](http://0media.tw)[0media.tw](http://0media.tw)


