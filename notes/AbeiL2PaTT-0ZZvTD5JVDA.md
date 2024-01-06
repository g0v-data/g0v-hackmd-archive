---
title: "《河圖》資訊整合UI計畫"
tags: altlasofdao(河圖),hackpad
---

# 《河圖》資訊整合UI計畫

> [點此觀看原始內容](https://g0v.hackpad.tw/M7krouLdPYq)

## 1.計畫概念

河圖、和圖、何圖、合途
_這其實是一套《自定義行動指南》_

以提供一套完全開放、任何人皆可編輯、操作的UI，讓使用者能透過使用這份UI，自行歸納、整理出事件的脈絡，並且藉此反推出自身所能採取的相應行動。

使用過程除了讓使用者能用自己的方式去過濾雜亂的資訊，也能藉由這個「整理」過程，刺激使用者自己的獨立思考，便不易被大眾媒體所操作，每個人都能藉此找出自己參與社會議題的方法。

而只要有人持續關注，事件本身也較不會被特定的風向所掩沒，也就更有機會能被解決。


## 2.特色

- 具遊戲性、操作性、工具性
- 公平公開，不鎖定特定議題
- 個人化使用方式


## 3.計劃目標

- 本計畫目標以「公平」、「公開」、「公正」理念貫徹維護資訊「透明化」、「永續化」、「正確化」
- 保存重要議題資訊，使議題永續發酵，不被河蟹
- 資訊公開、方便檢閱、阻隔被稀釋的可能性
- 開放編輯
- 串聯各社運團體，增加互相合作機會
- 提供參與行動的管道及解決方法
- 長期經營，冀望成為指標性方便使用的「工具」


## 4.執行項目

### 架設網站：

ㄧ個主要UI（參考：[http://bl.ocks.org/zbryikt/10757106b3d87c4eefe4](http://bl.ocks.org/zbryikt/10757106b3d87c4eefe4)），包含以下功能：

#### UI介紹：

1.  由318事件作為起始點，每一"天"顯示為一個"圓"，會隨著日期前進自動向外擴展；每一個單獨事件顯示為一"點"。每一"點"會坐落在該事件所發生的日期的"圓"上。
2.  "點"會亂數、(間距)平均顯示在"圓"上，即每次進入網站所看到的分布皆不會一樣。
3.  "點"會依照分類而顯示為不同顏色（分類依據請參考**6..資料備份公式**）。

#### 功能：

1.  標籤按鈕整理功能：點選"標籤"，則同一類別的事件會自動集合成扇形以供檢視。
2.  自定義標籤按鈕整理功能：可自定義標籤內容，例如輸入"行政院"則所有包含"行政院"的"點"會自動集合成扇形以供檢視。
3.  樹狀連結功能：使用者可將任意的"點"和"點"之間連連看，可檢視各事件關係。
4.  報表／圖表輸出功能：使用者可將整理結果分享至個平台，或輸出成圖片儲存。
5.  儲存編輯功能：使用者可自行在線上編輯，也可留下自己的編輯結果在網站上供他人參考。

#### 附屬檢視功能：

1.  循環式捲軸：可於一個滾輪上顯示同一議題的所有事件，滾輪會不停滾動，讓使用者觀察事件時不會總是只觀察最新或者一開始的情形。
2.  落點分析圖：可顯示同一議題正反兩方的拉扯／操作狀態，例如：關鍵字「核電廠延役」這個議題會有民間和政府兩方的動作，即兩種顏色的標籤（可參照**6.資料備份公式**），即可形成落點分析圖，以檢視目前事件偏向何方及處理情形。
3.  政見時鐘：一個當政治人物提出政策的那天開始不斷計時的時鐘，直到政見兌現才會停止。
4.  影片牆：備份資料庫內的所有影片所形成的影片牆。

### 資料上傳機制：

設計一份表單開放給所有一般人，每個人可將自己認為重要得訊息依照格式填寫表單，回傳的表單內容會直接反應在UI上（目前預設為Google問卷）。

### 備份資料庫：

提供或連結可供查證的資料庫。


## 5.目前進度

自2014/03/18起至今，已收集了ptt八卦板上大量備份資料，可供使用。

### 號召網站釋出

[http://aod.tw/](http://aod.tw/)

### ptt爬蟲程式


回文篩選功能
1.增加層級式分類資料夾功能
20推以下建立一個資料夾
40推以下建立一個資料夾
60推以下建立一個資料夾
80推以下建立一個資料夾
100推以下建立一個資料夾
推爆建立一個資料夾

噓文也以同樣層級方式產生資料夾

母資料夾20150627
EX：20推以下建立一個資料夾
20like
40推以下建立一個資料夾
40like
推爆
likeBomb
20噓以下建立一個資料夾
20dislike
噓爆
dislikeBomb

推爆/噓爆
PTT有回應數顯示被關注程度
新增功能分層級篩選熱門文章

文章裡圖片、影片、超連結抓取

XP 32bit確認RUBY1.9版可正常運行



### 設計網站UI流程規劃

[https://drive.google.com/file/d/0B9bDFHChjWyHOXU2WFFsZkZtU1U/view?usp=sharing](https://drive.google.com/file/d/0B9bDFHChjWyHOXU2WFFsZkZtU1U/view?usp=sharing)
[https://drive.google.com/file/d/0B9bDFHChjWyHZ2dFQ2xmeWpSbkU/view?usp=sharing](https://drive.google.com/file/d/0B9bDFHChjWyHZ2dFQ2xmeWpSbkU/view?usp=sharing)

圖表參考網站：
[https://docs.google.com/document/d/1wMJd7z3zRU8fBP7U3MI57Qon1oz1NLOV7S3rzMrJk6Q/edit?usp=sharing](https://docs.google.com/document/d/1wMJd7z3zRU8fBP7U3MI57Qon1oz1NLOV7S3rzMrJk6Q/edit?usp=sharing)

UI參考模擬：
[https://drive.google.com/file/d/0B9bDFHChjWyHblNLMHpiSWItMTg/view?usp=sharing](https://drive.google.com/file/d/0B9bDFHChjWyHblNLMHpiSWItMTg/view?usp=sharing)
[https://drive.google.com/file/d/0B9bDFHChjWyHR2ZfTUNtbTZPdlU/view?usp=sharing](https://drive.google.com/file/d/0B9bDFHChjWyHR2ZfTUNtbTZPdlU/view?usp=sharing)

### UI視覺化DEMO


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_b6c74ea0e56702979b7b621cf94fd405)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_e85e79507839ab91409e4fc2d8b86bab)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_2c25a4edeca7a041691b5de81c64e8f5)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_3131d2993417bf7ec0bb3370aca5c667)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9f72cc909955e6f7e0f7f81addc8d7bb)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_09401f951082729e20fc7a7009fc94bb)
I.
顯示此UI目前呈現事件的時間區段
上下兩行起始/終點數字時間可自行輸入

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_2697273d84b7d74bf87b8bebd0af8213)
II.
收和/展開事件標題

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_1cea9a8fe396895efde95e8169bed4cb)
III.
自動分類顏色議題

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_1b988b9319004bc2b6ed2c9047e9a063)
IV.
自定義蒐尋對象顏色分類

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_b7141e670316b6d9a6347acfdda04f7e)
V.
開啟樹狀連結
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_e0b34b2b483ab4e85b81b2958c5b024d)
VI.
重整回到最初狀態
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6aabc7dc9f3d1a340353390a796ff393)
VII.
使用者自行上傳資料

#### D3參考Sample

事件呈現運轉
[http://bl.ocks.org/mbostock/6226534](http://bl.ocks.org/mbostock/6226534)
[http://bl.ocks.org/mbostock/3007180](http://bl.ocks.org/mbostock/3007180)
[http://bl.ocks.org/mbostock/5415941](http://bl.ocks.org/mbostock/5415941)
[http://bl.ocks.org/mbostock/1371412](http://bl.ocks.org/mbostock/1371412)
[http://bl.ocks.org/mbostock/1169680](http://bl.ocks.org/mbostock/1169680)
[http://bl.ocks.org/mbostock/d8b1e0a25467e6034bb9](http://bl.ocks.org/mbostock/d8b1e0a25467e6034bb9)
[http://bl.ocks.org/mbostock/19168c663618b7f07158](http://bl.ocks.org/mbostock/19168c663618b7f07158)
[http://bl.ocks.org/mbostock/fe3f75700e70416e37cd](http://bl.ocks.org/mbostock/fe3f75700e70416e37cd)
[http://bl.ocks.org/mbostock/981b42034400e48ac637](http://bl.ocks.org/mbostock/981b42034400e48ac637)
[http://bl.ocks.org/mbostock/11463507](http://bl.ocks.org/mbostock/11463507)
[http://bl.ocks.org/mbostock/9078690](http://bl.ocks.org/mbostock/9078690)
[http://bl.ocks.org/mbostock/4343214](http://bl.ocks.org/mbostock/4343214)
[http://bl.ocks.org/mbostock/1313857](http://bl.ocks.org/mbostock/1313857)
[http://bl.ocks.org/mbostock/910126](http://bl.ocks.org/mbostock/910126)

放大縮小區段
[http://bl.ocks.org/mbostock/6140181](http://bl.ocks.org/mbostock/6140181)
[http://bl.ocks.org/mbostock/2983699](http://bl.ocks.org/mbostock/2983699)
[http://bl.ocks.org/mbostock/1071269](http://bl.ocks.org/mbostock/1071269)

議題分類
[http://bl.ocks.org/mbostock/3151228](http://bl.ocks.org/mbostock/3151228)
[http://bl.ocks.org/mbostock/45943c4af772e38b4f4e](http://bl.ocks.org/mbostock/45943c4af772e38b4f4e)
[http://bl.ocks.org/mbostock/3887193](http://bl.ocks.org/mbostock/3887193)
[http://bl.ocks.org/mbostock/f098d146315be4d1db52](http://bl.ocks.org/mbostock/f098d146315be4d1db52)
[http://bl.ocks.org/mbostock/5100636](http://bl.ocks.org/mbostock/5100636)
[http://bl.ocks.org/mbostock/910126](http://bl.ocks.org/mbostock/910126)
[http://bl.ocks.org/mbostock/4063550](http://bl.ocks.org/mbostock/4063550)
[http://bl.ocks.org/mbostock/1306365](http://bl.ocks.org/mbostock/1306365)
[http://bl.ocks.org/mbostock/4341574](http://bl.ocks.org/mbostock/4341574)
[http://bl.ocks.org/mbostock/4341417](http://bl.ocks.org/mbostock/4341417)
[http://bl.ocks.org/mbostock/31ec1817b2be2660c453](http://bl.ocks.org/mbostock/31ec1817b2be2660c453)
[http://bl.ocks.org/mbostock/32bd93b1cc0fbccc9bf9](http://bl.ocks.org/mbostock/32bd93b1cc0fbccc9bf9)
[http://bl.ocks.org/mbostock/4348373](http://bl.ocks.org/mbostock/4348373)
[http://bl.ocks.org/mbostock/5944371](http://bl.ocks.org/mbostock/5944371)
[http://bl.ocks.org/mbostock/31ec1817b2be2660c453](http://bl.ocks.org/mbostock/31ec1817b2be2660c453)
[http://bl.ocks.org/mbostock/5944371](http://bl.ocks.org/mbostock/5944371)
[http://bl.ocks.org/mbostock/5872848](http://bl.ocks.org/mbostock/5872848)
[http://bl.ocks.org/mbostock/5682158](http://bl.ocks.org/mbostock/5682158)
[http://bl.ocks.org/mbostock/4063550](http://bl.ocks.org/mbostock/4063550)
[http://bl.ocks.org/mbostock/1305111](http://bl.ocks.org/mbostock/1305111)

樹狀連結
[http://bl.ocks.org/mbostock/1212215](http://bl.ocks.org/mbostock/1212215)
[http://bl.ocks.org/mbostock/4600693](http://bl.ocks.org/mbostock/4600693)
[http://bl.ocks.org/mbostock/950642](http://bl.ocks.org/mbostock/950642)
[http://bl.ocks.org/mbostock/1062288](http://bl.ocks.org/mbostock/1062288)
[http://bl.ocks.org/mbostock/2706022](http://bl.ocks.org/mbostock/2706022)
[http://bl.ocks.org/mbostock/81443f83a3e342f9ab2f](http://bl.ocks.org/mbostock/81443f83a3e342f9ab2f)
[http://bl.ocks.org/mbostock/1080941](http://bl.ocks.org/mbostock/1080941)
[http://bl.ocks.org/mbostock/1093130](http://bl.ocks.org/mbostock/1093130)
[http://bl.ocks.org/mbostock/1129492](http://bl.ocks.org/mbostock/1129492)
[http://bl.ocks.org/mbostock/1138500](http://bl.ocks.org/mbostock/1138500)

來源網站
[http://bl.ocks.org/mbostock/](http://bl.ocks.org/mbostock/)





## 6.資料備份公式

1.  以各種顏色做標籤分類整理：
桃紅 (Fuchsia) - 值得散播的資訊
藍色 (Blue)      - 政府
橘色 (Orange) - 反動方
綠色 (Green)   - 實際的戰略方法
黃色 (Yellow)   - 是模糊地帶(有可能有用或沒用或超出定義範圍或本身定位太高階)

2.  同一個事件可以有兩種以上標籤


## 7.<<網路黑市 lololol x Internet Yami-ichi>>參展 (網路後巷 - 國際非網路藝術展 開幕活動)


### 關於網路黑市

The Internet  Yami-Ichi* (Internet Black Market) is a flea market which deals  "Internet-ish" things, face-to-face, in actual space. Both flea markets  and the Internet are fanatical and chaotic mixes of the amazing and  useless. In the Internet Yami-Ichi both the wills and desires which  brought us to create the Internet, and the wills and desires we picked  up once we got there, are salvaged to be shared in a social space.

#### IDPW

來自日本的IDPW是一個傳說中有一百年歷史的網路團體，其作品曾獲得日本文化廳媒體藝術季新人獎。 近年來IDPW最具代表性的實驗性市集“網路黑市（Internet Yami-ichi）”是一個面對面瀏覽內容的平台，實驗網路文化在實體交易場所的可能性。網路黑市活躍於國際藝術機構，2013-2014間在柏林，阿姆斯特丹，比利時，東京，札幌舉辦且收到當地的熱烈迴響。今年夏天，網路黑市也將計劃在紐約、首爾、聖保羅、奧地利林茲、巴西、台灣台中舉行，台中場由 [lololol.net](http://l.facebook.com/l.php?u=http%3A%2F%2Flololol.net%2F&h=VAQGD0NJC&enc=AZN_cjof5yeslDSRUukpgs9D4jpgIX-V2fUPe57UCXpC8RAJ4UcyJmdeEcuUsWCw5hU&s=1) 合作企劃。希望能引發台灣參與人和民眾對無所不在的網路文化深入的思考。
[http://idpw.org/](http://idpw.org/)
[http://yami-ichi.biz/](http://yami-ichi.biz/)


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_b58cbf19e524ee05d228fea8113d00ba)

### 河圖@網路黑市


販售各種與學運、抗爭相關物品的X光片，象徵<河圖>透視資訊的概念，並招攬成員

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_4847ba6fb9df71bf739aabaa57fd9a59)




網路後巷 \- 國際非網路藝術展 [#INTERNET](https://g0v.hackpad.tw/ep/search/?q=%23INTERNET&via=M7krouLdPYq) IMPLOSIONS
▁ ▂ ▃ ▅ ▆ ▇ ▉ ▁ ▂ ▃ ▅ ▆ ▇ ▉ ▁ ▂ ▃ ▅ ▆ ▇ ▉ ▁ ▂ ▃

 網路後巷 \- 國際非網路藝術展
 2015.8.29 - 11.15
 @國立台灣美術館 數位方舟

近十年來，網路已進駐我們的日常生活裏，它無所不在，無論是工作上或休閒時，人人手持智能手機，被訓練地無時無刻在數據和類比文化之間轉換自如。網路的介入帶給我們許多新的可能，同時也造成了許多焦慮。我們長期處於上線狀態，而網路也改變了我們的觀看世界的方式，我們已習慣後製景象，碎片式的資訊，便利的數據搜尋，和社交網站裏的相處模式。 如今我們生活於一個現實和虛擬交錯的空間中，offline和online的界限已模糊，而我們如何看待這個新的現實，我們身為人是如何存在於其中？網路是如何影響人與人在現實和虛擬世界裏相處方式和社會構造？

策展人：lololol

參展藝術家
 金姆‧阿森多夫 Kim Asendorf
 安東尼‧徹尼里歐 Anthony Cerniello
 格雷戈里‧夏通斯基 Gregory Chatonsky
 快樂虛擬朋友 Happy Virtual Friend
 傑森‧費門 Jason Freeman
 IDPW
 谷口曉彥 Akihiko Taniguchi
 應蔚民 Ying Wei-min

開幕式
 時間：8.29 2:30 pm
 地點：國立台灣美術館  數位方舟

開幕活動 網路黑市
 時間：8.29 11:00am - 5:30pm
 地點：國立台灣美術館  下凹庭園

藝術家座談會
 時間：8.30 2:00-4:30 pm
 地點：國立台灣美術館 演講廳
 對談人：lololol，快樂虛擬朋友，IDPW，谷口曉彥

指導單位：文化部     主辦單位：國立台灣美術館

展覽網站：[http://www.lololol.net/](http://www.lololol.net/action.html)[action.html](http://www.lololol.net/action.html)




## 7.當前目標

確立資料庫來源
確立／完備資料分類方法
完成上傳機制
改善視覺呈現，更親近人更易操作
宣傳／企劃團隊


## 8.徵求人才

網路工程師
設計師
律師
圖資管理師
企劃宣傳人員
翻譯人員
校錯人員
資料備份人員
網站維護人員
Liveleak / Youtube / Twitter / Facebook / Tumblr / Pinterest 等平台版主 / 維護人員


## 9.聯絡方式

atlasofdao@gmail.com
[http://aod.tw/](http://aod.tw/)

