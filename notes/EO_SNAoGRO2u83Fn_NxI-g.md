---
title: "GIS(地理訊息系統)人力資源量產計畫暨自學手冊"
tags: GIS, 零時的學習不能等
---

# GIS(地理訊息系統)人力資源量產計畫暨自學手冊

> [點此觀看原始內容](https://g0v.hackpad.tw/YAuGma5fg7W)


## 緒論

### 緣起

在太陽花學運之後，有很多後續團體鎖定選舉相關事務進行運作，其中以割闌尾、小蜜蜂、大家來選里長為代表。
近年來，使用GIS投入選舉行為分析的頻率越來越高，常見於媒體於選舉過後的統計報導(繪製各陣營選上的地區，如圖一)。同理，也可以將GIS預先用於地區投票偏好以及社會因素的分析，預先補強支持度不足的地區，以達到勝選的目的。
由於，過去GIS的學習資源大多難以接觸且需要具備統計的背景知識，使得GIS的人力資源往往是所費不貲的，但是經由自學以投入相關的社會運動，可以創造出難以估計的效益。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6ac5f1b3e2343cc4dd76773941c75a70)
圖一 第八屆立法委員當選立委黨籍分布圖

### 應用範圍

1.  **割闌尾計畫**：找出各鄉鎮市區或村里的在野支持力量，並嘗試予以統整及動員，並於選區內開拓更多的在野支持力量。
2.  **小蜜蜂戰鬥隊**：找出各鄉鎮市區或村里對於社會議題的偏向性，並藉由地域上的連續性，以居民互傳的方式改變社區對社會議題的看法。
3.  **大家來選村里長**：對於青年投入村里長選戰的村里進行難度分級，並且在較挑戰性較高的村里投入更多的人力與資源，以協助勝選。
4.  **監票者聯盟**：將各村里及鄉鎮市區的開票結果地圖化，也可以用地圖化提高各投開票所分布監票員的人力管理效率。
5.  **在野勢力的年底參選**：對於公民陣營及在野黨欲提高各層級的佔有比例，也可以用此方式找出該選區的突破點，避強併弱，以迅速累積地方實力。

### 基礎知識

- 具備試算表的大量資料處理經驗及技巧者較易勝任。
- 處理過程要會使用試算表的篩選、排序等功能。

### 預期成效

- 培養出更多會使用GIS軟體的人投入選舉事務工作，並協助公民團體及在野勢力做選舉的戰略分析。
- 由於該計畫為目標導向，可學習與地域分析相關的繪圖法，但未必能全部學會GIS的功能。

### 相關軟體

1.  **QGIS** [http://www.q](http://www.q)  gis.org/en/site/ (現在最新版是2.6 "Brighton")
    免費且多功能模式的GIS軟體，支援多國語言，只要系統的語言設定為(繁體中文，臺灣)，系統即可以繁體中文介面運作。
> 請問在Mac系統只能選擇英文版（我時區沒選錯），‘會影響之後中文資料的輸入嗎
> [name=Xavier S]

2.  **Office 2003, 2007, 2010** (Access 2013不支援.dbf轉檔)
    在GIS中繪製地圖，有個很重要的零件是.dbf檔，是地圖上所有資料的存放處。
    Excel在選取所有檔案的情況下可讀取.dbf檔，但是轉存要在Access中匯入Excel檔後再匯出成.dbf檔。
    但Office 2013已經停止對.dbf檔的支援了，使用者要另尋替代方案。
3.  **LibreOffice**
    一個免費、可讀˙取.dbf檔的程式，但是若儲存格有過長數值時會出錯(容許19位數值)。
4.  **'DBF Commander**
    英文軟體，是可以編寫和儲存.dbf檔的程式。

### 相關資料

#### 圖資部分

1.  台灣村里界(含澎湖)修正村里屬性資料 [http://goo.gl/rbmHzv](http://goo.gl/rbmHzv)
2.  台灣行政區界資料\- 村里 [http://data.gov.tw/node/5968](http://data.gov.tw/node/5968)  (點選SHP下載)
                                        \- 鄉鎮[http://data.gov.tw/node/7441](http://data.gov.tw/node/7441)   (點選SHP下載)
> 鄉鎮市區界可以利用村里界Dissolve
> [name=Dongpo]

> Dissolve的技術我還沒學會，目前還有一個需求量大的是立委選區的.shp檔
> [name=Chen C]

> 我有將 MyServant 的立委選區資料轉為 json 格式使用 [https://github.com/kiang/MyServant/blob/master/myservant/json/data/legislator\_election\_district_list.json](https://github.com/kiang/MyServant/blob/master/myservant/json/data/legislator_election_district_list.json)
> [name=Finjon K]

> 鄉鎮的 shp file 有部分縣市前面會加上臺灣省，要小心處理 (現在用工人智慧 XD)
> [name=昕迪 李]

> 勘誤: 桃園縣楊梅鎮 和 苗栗縣峨嵋鄉 -\> 桃園縣楊梅市 和 苗栗縣峨眉鄉
> [name=昕迪 李]

> 圖資在MAC系統會亂碼，沒有UTF-8嗎？我不知道怎麼轉檔。
> [name=Jiyi N]

#### 資料庫部分

**選舉資料庫**  [http://db.cec.gov.tw/](http://db.cec.gov.tw/)
**人口資料**  [http://www.dgbas.gov.tw/ct.asp?xItem=15408&CtNode=4594&mp=1](http://www.dgbas.gov.tw/ct.asp?xItem=15408&CtNode=4594&mp=1) (主計處)
| 層級 | 資料 | 備註 |
| --- | --- | --- |
| 主計處 | 各縣市人口資料 |  |
| 縣市民政局 | 各鄉鎮市區人口資料 | 台北、新北、台中、彰化各村里人口資料 |
| 鄉鎮市區戶政事務所 | 各村里人口資料 | 新竹市不齊全、基隆市僅仁愛區有、桃園縣無 |

最理想的原始資料是各村里單一年齡組的資料，甚至有區分有原住民身分與非原住民身分的人口。(資料可貼近選舉資料庫的選舉人數，但是人口資料夠精細可以知道各行政區、甚至各村里的選民年齡結構)


## 預備知識

### GIS檔的檔案組合( ESRI Shapefile )

1.  **.shp檔**：圖形向量檔，也就是地圖的原圖。
2.  **.dbf檔**：資料屬性檔，圖形資料屬性的存放位置。
3.  **shx檔：**連結 空間向量shp檔案與資料屬性的dbf檔的關聯檔案
檔案複製或提供給其他使用者使用時至少需要上述三個檔案同時提供，其他檔案諸如.prj檔（ESRI 投影坐標系統檔案）、.qpj檔（QGIS 投影坐標系統檔）、.sbn檔，大家甚少會去動到，相關介紹可參考Wikipedia. [http://zh.wikipedia.org/zh-tw/Shapefile](http://zh.wikipedia.org/zh-tw/Shapefile)

### 試算表編輯技巧

#### 排序

將原本順序混亂的試算表排成我們想要的形式。
如表一左，原本的資料順序是依照ID排序，但是我們要加入的資料是依照地區、類別和數量由小到大的排序才能吻合的，我們可以使用排序功能，對後三行進行排序。
(Excel 可先進行全選後點篩選，以確保每筆資料的橫向連貫性一致，之後才進行排序)

由左表到右表：地區排序，內部資料也要排序
(1) 先對數量進行由小而大的排序
(2) 對類別進行由小而大的排序 (上一次排序的結果會在類別的內部被保留)
(3) 最後對地區進行排序 (前兩次的排序結果會在內部被保留)
(4) 完成

由右表到左表：加入資料後恢復原狀
(1) 對ID進行排序
(2) 完成
※ 在Excel中有時會出現恢復原狀時，沒有把新加入的資料帶到應該去的地方，建議可以取消篩選後，重新全選再篩選。如此，重新將資料做橫向連結後再排序

表一 多次排序解說用表
| ID | 地區 | 類別 | 數量 |  |  |  | ID | 地區 | 類別 | 數量 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | 南部 | C | 3 |  |  |  | 17 | 北部 | A | 1 |
| 2 | 南部 | A | 1 |  |  |  | 13 | 北部 | A | 2 |
| 3 | 北部 | B | 1 |  |  |  | 15 | 北部 | A | 3 |
| 4 | 南部 | A | 3 |  | **轉換成** |  | 3 | 北部 | B | 1 |
| 5 | 北部 | B | 3 |  | **→** |  | 7 | 北部 | B | 2 |
| 6 | 南部 | C | 2 |  |  |  | 5 | 北部 | B | 3 |
| 7 | 北部 | B | 2 |  |  |  | 11 | 北部 | C | 1 |
| 8 | 北部 | C | 2 |  |  |  | 8 | 北部 | C | 2 |
| 9 | 南部 | B | 2 |  |  |  | 10 | 北部 | C | 3 |
| 10 | 北部 | C | 3 |  |  |  | 2 | 南部 | A | 1 |
| 11 | 北部 | C | 1 |  |  |  | 12 | 南部 | A | 2 |
| 12 | 南部 | A | 2 |  | **轉換成** |  | 4 | 南部 | A | 3 |
| 13 | 北部 | A | 2 |  | ← |  | 14 | 南部 | B | 1 |
| 14 | 南部 | B | 1 |  |  |  | 9 | 南部 | B | 2 |
| 15 | 北部 | A | 3 |  |  |  | 16 | 南部 | B | 3 |
| 16 | 南部 | B | 3 |  |  |  | 18 | 南部 | C | 1 |
| 17 | 北部 | A | 1 |  |  |  | 6 | 南部 | C | 2 |
| 18 | 南部 | C | 1 |  |  |  | 1 | 南部 | C | 3 |

### 篩選

運用篩選功能，將所需的資料篩出。
在編輯.dbf檔時和繪製地圖˙時篩出目標項目時會有使用需求。
表二 篩選解說用表
| ID | 地區 | 類別 | 數量 |  |  |  | ID | 地區 | 類別 | 數量 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | 南部 | C | 3 |  |  |  | 1 | 南部 | C | 3 |
| 2 | 南部 | A | 1 |  |  |  | 2 | 南部 | A | 1 |
| 3 | 北部 | B | 1 |  |  |  | 4 | 南部 | A | 3 |
| 4 | 南部 | A | 3 |  |  |  | 6 | 南部 | C | 2 |
| 5 | 北部 | B | 3 |  |  |  | 9 | 南部 | B | 2 |
| 6 | 南部 | C | 2 |  |  |  | 12 | 南部 | A | 2 |
| 7 | 北部 | B | 2 |  | **篩選** |  | 14 | 南部 | B | 1 |
| 8 | 北部 | C | 2 |  | **條件** |  | 16 | 南部 | B | 3 |
| 9 | 南部 | B | 2 |  | **南部** |  | 18 | 南部 | C | 1 |
| 10 | 北部 | C | 3 |  | **→** |  |  |  |  |  |
| 11 | 北部 | C | 1 |  |  |  |  |  |  |  |
| 12 | 南部 | A | 2 |  |  |  |  |  |  |  |
| 13 | 北部 | A | 2 |  |  |  |  |  |  |  |
| 14 | 南部 | B | 1 |  |  |  |  |  |  |  |
| 15 | 北部 | A | 3 |  |  |  |  |  |  |  |
| 16 | 南部 | B | 3 |  |  |  |  |  |  |  |
| 17 | 北部 | A | 1 |  |  |  |  |  |  |  |
| 18 | 南部 | C | 1 |  |  |  |  |  |  |  |


## 實際操作

### 安裝程式

先在**QGIS**的網站  [http://www.qgis.org/en/site/](http://www.qgis.org/en/site/) 下載與安裝QGIS
QGIS是多語言系統，會自動偵測電腦的語言與地區設定，只要是語言設定為繁體中文，且地區為臺灣(地區若是香港或澳門，還是英文介面)，執行時會是繁體中文介面。

### 認識介面

在工具列上點右鍵，就會出現許多小工具列的開關(如下圖所示)，大家可以自己摸索，依照自己的需求排自己理想的工作環境。
在QGIS中，打「X」的框框表示被選取的項目。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_df074c5112c0ae88df4abc825d2f3c42)

### 載入圖層

\[圖層(L)\]→加入向量圖層(Ctrl+Shift+V)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_b0d25fcb80795a00896551a357a9f037)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ef6e93b41730117cdc697e874ea0b979)
> 政府提供的投影多為 EPSG:3826，若很龜毛需要特殊處理 [~http://snowdaily.pixnet.net/blog/post/56845692-proj4js-%E5%BA%A7%E6%A8%99%E8%BD%89%E6%8F%9B~](http://snowdaily.pixnet.net/blog/post/56845692-proj4js-%E5%BA%A7%E6%A8%99%E8%BD%89%E6%8F%9B)
> [name=昕迪 李]

> [http://gis-tech.blogspot.tw/2013/07/qgis-19-epsg.html](http://gis-tech.blogspot.tw/2013/07/qgis-19-epsg.html)
> [name=昕迪 李]

> 也可以參考 [https://github.com/kiang/cunli/blob/master/gen.sh](https://github.com/kiang/cunli/blob/master/gen.sh) 的指令，可以順利轉換出可以接受的版本
> [name=Finjon K]


可在左邊的工具列中拉出全覽圖，在瀏覽細部圖像時不至於迷失方向。
在圖層物件表上點右鍵，跳出的選單中會有\[在全覽圖中顯示(S)\]，按下後，全覽圖的位置會出現全圖的縮圖，紅框是瀏覽視窗當前的位置和大小。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_5e4ef76b827298d674bf592f93666b60)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_40500037fc9ad966ed88ef2f18514d12)

### 另存所需的圖層

在圖層上點右鍵所出現的表單中，會有\[開啟屬性工作表(O)\]，內容即為.dbf檔的資料，只是此處無法編輯資料內容。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_81f9188d91d8d2eef557969cb27557c9)

屬性工作表內容：
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_b48d00a08c55d26d7e1cecad62917446)

點選欄位表標題，可以將資料排序，以將資料排列成我們要處理的樣貌。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ab4ac9626dcd622563639dd63007bb03)

設定篩選條件TOWN (鄉鎮市區)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6c5b6c6eb7a479c98d4654d0c0e33cc9)

鍵入小港區，並將所有的村里選取(第一格是海域，故不選取)，選取整列時，點最左邊的行數。
**選取的技巧**包括「Ctrl+A (全選)」、選取時按第一個項目「+SHIFT按最後一個項目」(兩者間的項目全部選取)、「按住Ctrl做多重選取」。
※ 若要取消選取，在QGIS中再點選一次即可取消選取。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_5d3621108a9cf0f6a54a15f7f7fd3274)

地圖上小港區變成亮色
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ed1d4575cea508e52e9a2a00c9892bdf)

再加選前鎮區的里(除了復國里、竹中里、竹北里、興東里、竹西里、竹東里、竹內里、竹南里不選)。
此時，可以按住Ctrl將要選取的項目點擊選取。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_18febf16a19ded4dd64ca08e3db0779f)

整個「高雄市第九選區」的地圖形狀就浮現了。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_fc836d84d42a36839f2334b6d72b8f72)

這時候在圖層上點右鍵→\[另存已選取為......\]
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_89ce99831630628ef69e601b3625465e)

在\[另存為\]指定要儲存的位置與檔名
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_17cac471e74479c016c7dae7216c1b10)

重新\[載入向量圖層\]，選取剛剛儲存的.shp檔。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_2f844979cba1eaff2887ebee2a386a5c)
只有高雄市第九選區的地圖就會出現了。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_f9b9de16df1d43dfa06b83468fa9be98)

### 加入欲繪製的資料

#### 自動接合

> 有聽說QGIS有設定資料配對欄位、自動接合資料的功能，小的學藝不精，只能以手動的方式自行接合資料(QGIS 2.2的介面中找不到)，簡便方法有請各位高手補完，謝謝。
> [name=Chen C]

> 請到Layer properties中，找到Join，將表格資料匯入，然後把可以對應的欄位加入，資料表(.dbf)中就會自動join在一起
> [name=Dongpo]


> ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_03c044309887d30afd65b67de17428e4)
    
> [name=Dongpo]

> dongpo ++
> [name=昕迪 李]




#### 疊加文本數據


QGIS可以在圖層上疊加文本数据，不一定非要使用.dbf檔做為數據文件
以下示範一下如何操作。
假設我已經生成了臺北市各選區的shp文件如下圖：

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_656f23ff9934eafc64b6ed4dec4760fc)

並在Excel中利用樞紐分析表已經整理好了對應選區的數據
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_83866dcbb67e95020dfd72f1140a48d6)
第一豎列是選區名字，需要和地圖文件中的名字一致，這樣QGIS才知道把哪一行放到什麼位置。其中D_Rate表示得票率，Diff表示得票率之差

接下來將所有數據選中，粘贴到記事本程序内

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6f0492815702090d8932cbb500992cbf)
保存爲UTF-8編碼的文本文件：
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_8a567bd376ef7ad6412ce1fd739d18b1)

接下來在QGIS中，選擇圖層選單中的「添加文本數據圖層」（繁體中文應該叫做「加入分隔文字圖層」）
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_24540ed81a3dec062f69800c68fa5e5f)

在新視窗中選擇剛剛保存的文本文件以及設置編碼爲UTF-8，由於我們是從Excel黏貼出來的數據，所以「文件格式」選擇「自定義分隔符」裏面的「制表符(繁體中文版呈現：Tab)」，由於文本文件裏面不包括圖形訊息，所以「幾何圖形定義」選擇「無幾何圖形」：
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_e79898eaf1b732561dc57fbe441fba4b)
確定後就可以看到多了一個文字圖層：
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_2d406eb396b3ebbc1918a6217b3a7ce4)

然後右键選擇圖形圖層的属性-連接（Joins）頁，點擊绿色的加號圖標鏈接兩個圖層。連結圖層選擇剛才添加的文本圖層，连接字段選擇文本圖層中的TV_ALL（村里名），目標字段是圖形圖層中的TV_ALL（村里名）：

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_4209bfefe010c14597df07cfb5ebe35d)
連結好之後在樣式頁中可以設置將數據檔中的字段顯示在地圖上
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9583ab0303433bb8abc0627457d53105)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_b0981cd03b05e5ee427da7edb0b94c94)
這樣就繪製出了按照里分布的得票率地圖，越綠的地方代表越高的得票率，越白的地方表示得票率越低。

QGIS在樣式設置中可以進行各種計算（列選擇旁邊那個花體e按鈕），但是要計算除法時要先用toreal函数將整數轉換爲實數再計算，否則比率的結果一定是0。例如計算投票率的公式爲
```
 toreal(  "taipei\_Vote")  / toreal( "taipei\_Reg" )

```
#### 手動接合

.dbf檔是可以用Excel、LibreOffice和DBF Commander開啟的。
以下，以大家常用的Excel來做介紹。

Excel\[開啟舊檔\]，檔案類型選\[所有檔案\]或\[dBase檔案\]
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_706fc0cfdd488b96d8f6ec26e3205036)
開啟後.....
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9d108bb57b4830cac458259d52f9d9da)
- 這個檔案是全台灣村里的資料庫  ，事實上，如果要編輯這麼大的資料庫並非易事，建議可先將自己所需的地區先挑選出來，另存一個.shp檔(該檔的.dbf檔也會同時生成)。小檔案編輯時也較為容易。
- 在編輯時，自己可先用排序和篩選的功能，把資料整理成我們要的形狀。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_acdab1d0d5dccbe658818ab903b08933)

準備開始排序 (筆者先開篩選功能)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ab834573a95a4dea616f6b34aec8bc79)

因為其他整理過的資料來源大多是縣市依筆畫排序，內部的鄉鎮市區也依筆畫排序，最內部的村里名也是依筆畫排序。
我們也可以用Excel的排序，將資料排成這個形式，以便於之後接合資料。
1.  先把VILLAGE做\[從A到Z排序\] (中文字是依筆畫排序)
2.  再把TOWN做\[從A到Z排序\]  (先前的VILLAGE在的排序在同一個鄉鎮市區內會被保留)
3.  最後再把COUNTY做\[從A到Z排序\]
4.  完成
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c207970b2c438a415e9840b8b2154f82)
要恢復原狀，對OBJECT ID進行\[從A到Z排序\] ，即可恢復原狀。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_a6d26b64630d969cd0b6b724781e5d35)

以下為**示範資料操作**
以本圖引用的資料：林國正得票率
[http://db.cec.gov.tw/hist](http://db.cec.gov.tw/histFile?voteCode=20120101T1A2&resourceCode=R1)[File?voteCode=20120101T1A2&resourceCode=R1](http://db.cec.gov.tw/histFile?voteCode=20120101T1A2&resourceCode=R1) (第八屆立委選舉資料，大家可抓下來自行把玩)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_eb7ba2c671211275e97f542e674797b9)
從鄉鎮市區拖曳整行，填滿整個鄉鎮市區行，讓每個村里資料的第一欄非空白
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_fb3f3828862f5109b86ccae051c228d4)

> 這裏可以直接用 Trim(A1)&B1來删除空格和拼接
> [name=laoyang]


複製前兩行，在記事本中貼上
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_257f90e2e7f532b3165f1b14568fed21)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9b2e1ed57bdf3f6974ad311e4b1b7781)


將表示\[換列的空白區段\]，以不輸入任何文字的取代方式，去除\[換列的空白區段\]
用\[全部取代\]，將整個檔案的\[換列的空白區段\]去除
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_19e689cc5c429cdcd27fcca9d9722982)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_e5de5580cbeba291aa17c22584489dc8)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_31076739f45d35203927ded04a896f33)

前排的小空白也可以用此方法除去
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_5540fd84cbb519bbb1c58ed2d76c2056)
貼回到Excel中「村里別」的欄位，如此就有一個可以跟地圖資料庫的\[TV_ALL\]一樣的欄位可以對應
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_2cc1e6d5bcba2ab2c4edc036952bcae3)
要做破壞性的編輯前，要養成備份資料的好習慣
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_43a93736353ac6827fd59ad75a7ac280)
因為很多村里都不只一個投開票所，因此我們要用樞紐分析表整理成一個村里一筆資料
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_3595e1c8ef79fc000a96f8cd92512229)

先把變項列選取起來，解除合併儲存格
※ **真正的資料庫格式是不能出現合併儲存格的**
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_40639bff879556bd2f95150c4e1351f2)
解除合併儲存格後自行整理一下畫面，就可以準備用\[樞紐分析表\]處理了
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9381d3d0857d49c46df8341a2a08debf)

插入\[樞紐分析表\]
※ 要先刪除高雄市第九選區的\[總計\]列、\[小港區\]列和\[前鎮區\]列，因為它們屬於較高的層級，非本次示範要使用的「村里層級」。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0799bd793a92c0dcb6fe8415764ef2ba)
開始進入\[樞紐分析表\]，選取範圍後並輸出
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_57e0f79ec55fa68150261550fb2528d0)
開始選擇自己需要的變項
※ 留意\[村里別\]的排列順序，它是依照筆畫數排序的
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_3645c1864e199e7ee4353de43e0d3059)

將所得到的樞紐分析表全選複製，以\[貼上值\]的方法在空白處貼上，以便進行進一步的公式運算。
> 因為樞紐分析表的內容似乎無法直接應用於後續運算，因此用貼上值的方式洗掉原本的公式
> [name=Chen C]

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_650260b0a189d699ac8c1bb1e42057f5)

把表格整理好後，再進行運算
我們設定了四個欄位：
1.  Lin_Vote (林國正得票數)：E2=B2
2.  N\_Lin\_Vote (非林國正票數)：F2=C2-B2
3.  Lin_Rate (林國正得票率)：G2=B2/D2
4.  N\_Lin\_Rate (非林國正得票率)：H2=(C2-B2)/D2
※ 由於.dbf檔只接受變數名稱是英文，中文會出現亂碼，因此之後要使用的變項都用英文命名
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_8b3329cc92c60d235ff92bd3896e9c1e)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_26b2b6a30902b9ed489036b6bde14f69)
整行的自動演算
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_86e1c96e246be3dec328aa67991d7921)
整理到需要的小數位數(建議保留小數點以下四位)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_924c993f2db3b5bbcfcd00385971f5de)

可以準備進行資料接合了。
開啟高雄市第九選區的.dbf檔
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_2381c2c35dec9cd2ec94c370a263c03e)
先準備排序工作：全選→篩選→對\[TV_ALL\]的欄位進行\[由A到Z排序\]
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_fb77d0f25e7c810fa9e0a4530a23af50)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_df63a6a8093ca1a82f8ddb972a2c77f5)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_5dab0fb634493d89ba041a788c09cb2c)

將畫面移到尾端，把資料貼上(原有的\[總計欄\]不要貼過來)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_7e9de1a053af5d0d0ae88092c49d14e3)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_62352454c5864d4c4cf9d5f9dc435093)

解除現有篩選，重新全選、再次篩選
(確保後面四欄跟前面的資料是接合的)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_8ca3c93aca1ae129f2d5d19439dc6b9f)

對\[OBJECT_ID\]做\[由A到Z排序\]恢復原狀後，儲存檔案
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_2d69c1d1ad1b09f4daccd92964ba3362)
儲存˙時會出現下圖，就按下\[確定\]，先儲存成.xls檔
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ea4128e5b5a48ac429a139152936a273)

儲存完畢之後，開啟Access建立空白資料庫。(進入後，資料表可先關掉)
※ 由於Office 2013停止對.dbf匯入和匯出的支援，若您是Office 2013的使用者，建議用DBF Commander編輯。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ad0b900308ec4c4c691a1d38abf59d87)
匯入剛剛編輯的.xls檔
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_81db64ccc0747919cbd33e8c063d9160)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d1da5112945487b98b4b70a86a1f4a8e)
游標左右拉一下，確定這是我們要的資料 (最右側有看到我們新編入的四行資料)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_2162204bd0eb50d890246fc2bd866dcf)
(是的，我們第一列是「欄名」)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6e3caf27000e7a30eee4872735313238)
資料微調(看個人需要)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_e53af15103e7c9a00496cc1f1d8706ba)
不要主索引鍵。 (表格中已經有\[OBJECT_ID\]扮演這個角色了。)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_5264a137a0e3881f57aba53801636faa)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_38f1568158fb13c18c842db9a4dc48d7)
匯入成功，左側多出一個「高雄市第九選區」
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d4df5b67cbdca85528262cc6952d77b2)

匯出成.dbf檔
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_08f7a13d5683bca1df25c9c073ad385f)
如果您已經備份檔案了，直接\[確定\]蓋過檔案即可。
如果還沒備份檔案請記得備份。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_02a05ed3fb159a0e17fcbd92710dd0cd)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_3bd97aec44f9131290a42b1e1690fe25)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_67f3eeba5cd84160c3343af013c67831)

用QGIS的屬性工作表檢視，後面四行資料確實被加進來了。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_936dbdd09191e20a4f7a037720b7ad13)


### 設定屬性(上色)

繪製資料地圖時，常常需要隨˙區域上色。這部分可以從屬性中修改。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_44086062b903565feb87edf387c73853)

讀入時的預設值是\[單一符號\]
\[分類設定\] 適合類別變項
\[漸進設定\] 適合連續變相
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_13e30c13cf1e39f903732e5040ff4be3)
#### 分類設定

舉例來說，如果我們想要生成一個各里顏色都不同的地圖。
我們可以把目標變項設定成\[VILLAGE\](村里)，並且按下方的\[分類\]
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_75999f5742122479379d34131f6514f3)
分類後的樣子
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_fa38ab925dff181eb76ce43ca461d3bb)
點下\[確定\]，五顏六色的地圖就出現了
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_cb9e223617acdc2d2a362990bf62226b)

#### 漸進設定

在變項的地方選\[LIN_RATE\](林國正得票率)。

p.s. 筆者自製資料，不包含在原本台灣村里界全圖的檔案中。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c80cd4d7295b2dc7d7cd721c7a1e7a16)
在色彩的地方可以自由選擇顏色組合，右側的\[Invert\]是反轉的意思，若顏色bar不合乎自己的需求，可以按\[Invert\]來反轉方向。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_dd957dd5f0698dd07771bc3972697614)
設定好了之後，按下\[確定\]，我們需要的資料地圖(林國正得票率)就會出現了。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9c7adf5cd93d6b8eee912d691ec8c6b6)

### 資料標記

按下圖層資料標記選項的按鍵。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9669b8e65f244920c5882386d63d3b63)
※ 工具列上沒看到這個按鍵怎麼辦？工具列上點右鍵，確定\[標記\]是被打開的。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_cc0d796a922f16894fb27f16b2f48d59)
我們進入後開始標記里名(VILLAGE)，格式就看大家的喜好自行設定。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_17d89b596c59591e50bdc66207ad11ab)
字形：微軟正黑體、大小：12號字、加上白色1mm輪廓。
得到以下的地圖。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_51c928909555f6f52e50630274994055)
即使是地圖局部放大，標註的大小依然會維持。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_bc58b2def345cd066b9e363ddaa1628a)

### 地圖出圖

#### 直接輸出影像

\[專案(r)\]→另存為影像......
輸出圖面上當時所見的畫面。(以.bmp檔儲存)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_89af9bcf27152bf9dab5dbfdf5a9da38)

#### 地圖出版設計

\[專案(r)\]→\[地圖出版設計(N)\]
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_45c91a857861a74ffe195f4ee39ad81f)
輸入出版設計標題(之後會在視窗的標題˙列出現)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_405d3fb58495f7f612ecfd49ea560a13)
地圖設計介面的初始畫面
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_4803394f3b80aedaeceb7df325d2726e)
介面介紹
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c9db43fbd3d9db90ece4c21774467afc)

按\[加入地圖\]後，在畫面上拖曳出方塊。
在\[移動元件\]的模式下可以拖曳調整畫面大小。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_72d80c021bf728908edad1ad3cab3afe)
右側窗格可以做更多詳細參數的編輯，例如**地圖的顯示比例**
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ab481ac22ff1e3296739783bcb03f18c)

在\[移動內容\]的模式下可以調整地圖的位置，原本地圖在前鎮區和小港區的交界，現在被調整到小港區。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d44ef49018e02789446bd8df1b59c61f)
加入圖例
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_620335a78b2c90483e2ee79f8aaf7b95)

加入標題 (在右側工作欄位編輯標記文字)
※ 初始預設都是─內文：QGIS, 10號字, 字體：Agency FB。自己可以自行編輯。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_8a5f7736541a2777e6affb5be0fda2f6)
在出圖設計這裡可以選擇輸出成影像檔(.bmp)或是.pdf檔。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_8c613fa62b74a2ce7421a15dd8ebdb3c)

### 圖層疊加

一個地圖檔是可以有好幾層的地圖疊加起來。
以下圖為例，同時載入「台灣全圖」和「高雄˙市第九選區」的地圖。
方框內打「X」表示顯示的地圖，若勾選掉則會隱藏。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_511c133ba4234a8e0cf591a6ed2ade8d)
圖層的排列順序可以在「圖層順序」中做次序的調整，以將呈現效果達到最好。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_4ff1d69823d82f3a18c97b14ed4268a5)
※ 找不到「圖層順序」怎麼辦？工具欄上點右鍵，找到\[圖層順序\]的選項，將其勾選即可。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d8a473a139d5128912bc4e388b0e8994)
![](https://g0v.hackpad.tw/static/img/pixel.gif)


### 替代方案


GIS雖然很強效，如果要輕量快速畫出地圖，或可使用一些替代工具?
- google map: 不必寫程式
    - [https://www.google.com.tw/maps/preview](https://www.google.com.tw/maps/preview)
- leaflet+shackhand : 要寫一點前端
    - 應用: 農學地圖[http://g0v.github.io/farmer/](http://g0v.github.io/farmer/)
    - 簡略說明: [https://github.com/bestian/shackhand/](https://github.com/bestian/shackhand/)

內政部應該也有一些工具和資料可以參考使用?
- 國土資訊系統-社會經濟資料庫
    - 社會經濟GIS系統(可繪製統計地圖) [http://moisagis.moi.gov.tw/moiap/gis2010/Pro/Logged/MapPro/index.cfm?WORK=statistics##](http://moisagis.moi.gov.tw/moiap/gis2010/Pro/Logged/MapPro/index.cfm?WORK=statistics##)
    - 統計區比對服務 (但是需要申請帳號) [http://moisagis.moi.gov.tw/moiap/match/system_common.cfm](http://moisagis.moi.gov.tw/moiap/match/system_common.cfm)

### 遠期計畫

建置圖資檔(.shp)與資料庫檔(.dbf)的共享與交流平台。
> 可以用R統計軟體連結圖資檔和資料庫檔鋪設平台，使用者只要能夠整理出有TV_ALL(鄉鎮市區+村里名)的欄位和資料欄位的.csv檔，丟入檔案後就能出圖。
> [name=Chen C]

> 其實在村里級的分析時，會遇到很多問題，因為村里增修還蠻頻繁的，而有時鎮會升格為市，因此需要確定資料及是哪個時間點的。在 [https://github.com/g0v/twhgis/releases](https://github.com/g0v/twhgis/releases) 有列出每個不同時間點的所有村里列表，因此一個選擇是把統計資料的區域先對應到 ivid
> [name=Chia-liang K]

> 不過跨時分析還有很多問題待解決，例如跨越直轄市改制就相當複雜，還有若一個里分隔成兩個，之前的就沒有資料，但可以用面積計算出估計值並註記之。
> [name=Chia-liang K]


