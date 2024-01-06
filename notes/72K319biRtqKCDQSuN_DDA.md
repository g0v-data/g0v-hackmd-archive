---
title: "選前選舉人口消長計算與地圖化"
tags: hackpad
---

# 選前選舉人口消長計算與地圖化

> [點此觀看原始內容](https://g0v.hackpad.tw/cMxpnj1roqw)


## 資料來源

### 政府資料

[http://data.moi.gov.tw/MoiOD/Data/DataDetail.aspx?oid=F4478CE5-7A72-4B14-B91A-F4701758328F](http://data.moi.gov.tw/MoiOD/Data/DataDetail.aspx?oid=F4478CE5-7A72-4B14-B91A-F4701758328F)

### .csv檔模板

[103年9月臺北市人口資料.csv](https://www.dropbox.com/s/pre7s09e82gtt05/103%E5%B9%B49%E6%9C%88%E8%87%BA%E5%8C%97%E5%B8%82%E4%BA%BA%E5%8F%A3%E8%B3%87%E6%96%99.csv?dl=0)

> 請問是這樣嗎 ? 是否要把區域別 (松山區 全部加在一起 ?)
> [name=Tom S]

> .CSV檔的底部有出現，是需要做這樣的資料一份
> [name=Chen C]

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_b460aff16498a9cbc27d206d59aa620b)

### 資料配對模式

#### 五都

2014/9 & 2010/11

#### 桃園市+其他縣市

2014/9 & 2009/12

## 完成資料回報區

### 2014/9

臺北市 [103年9月臺北市人口資料.csv](https://www.dropbox.com/s/pre7s09e82gtt05/103%E5%B9%B49%E6%9C%88%E8%87%BA%E5%8C%97%E5%B8%82%E4%BA%BA%E5%8F%A3%E8%B3%87%E6%96%99.csv?dl=0)
臺中市 [103年9月臺中市人口資料.csv](https://www.dropbox.com/s/3qefq50a0bi7259/103%E5%B9%B49%E6%9C%88%E8%87%BA%E4%B8%AD%E5%B8%82%E4%BA%BA%E5%8F%A3%E8%B3%87%E6%96%99.csv?dl=0)
[台南市 ](https://onedrive.live.com/redir?resid=77AD6FB473C923CA!14732&authkey=!AKVLowOrYnvCKjM&ithint=file%2ccsv) [103年9月臺南市人口資料.csv](https://onedrive.live.com/redir?resid=77AD6FB473C923CA!14732&authkey=!AKVLowOrYnvCKjM&ithint=file%2ccsv)


## 格式

### 整體模板架構

1.  資料採男女分列的方式
2.  列出村里級資料和鄉鎮市區級資料
3.  製作單一年齡組、五歲年齡組以及選舉人口世代資料，其中選舉人口世代區分如下：
    1.  青年 (20-34)
    2.  壯年 (35-49)
    3.  中年 (50-64)
    4.  老年I (65-79)   ※ Young Elderly 年輕老人
    5.  老年II (80-)       ※ Old Elderly 老老人

| **選舉人口世代資料** |  | **五歲年齡組** |  | **單一年齡組** |
| --- | --- | --- | --- | --- |
| **村里級資料** |  | **村里級資料** |  | **村里級資料** |
| 男性 |  | 男性 |  | 男性 |
| 女性 |  | 女性 |  | 女性 |
| 總和 |  | 總和 |  | 總和 |
| **鄉鎮市區級資料** |  | **鄉鎮市區級資料** |  | **鄉鎮市區級資料** |
| 男性 |  | 男性 |  | 男性 |
| 女性 |  | 女性 |  | 女性 |
| 總和 |  | 總和 |  | 總和 |
詳細格式請見[103年9月臺北市人口資料.csv](https://www.dropbox.com/s/pre7s09e82gtt05/103%E5%B9%B49%E6%9C%88%E8%87%BA%E5%8C%97%E5%B8%82%E4%BA%BA%E5%8F%A3%E8%B3%87%E6%96%99.csv?dl=0)

### 欄標示

1.  村里級資料
    ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_3a8df39fda172d32325626adcc2aaacb)
    上圖解說：
- AM欄：臺北市資料內建欄位
- AN欄：臺北市資料內建欄位
- AO欄：臺灣村里界圖\[TV_ALL\]欄位格式 (鄉鎮市區名+村里名)
> 方便QGIS軟體接合資料用的接頭
> [name=Chen C]

> 請問 AM+AN - AO 的對應檔在哪裡 ?  
> [name=Tom S]

> 我做了一個綜合檔 : 
> [name=Tom S]

> [http://nbviewer.ipython.org/github/t0mst0ne/Population/blob/master/City%20all%20age%20statistics.ipynb](http://nbviewer.ipython.org/github/t0mst0ne/Population/blob/master/City%20all%20age%20statistics.ipynb)
> [name=Tom S]

> 原始碼在這邊 : [https://github.com/t0mst0ne/Population](https://github.com/t0mst0ne/Population)
> [name=Tom S]

> 但是沒有'區域別'   +   '村里'   變成   '區村里名' 的對應, 才能做到 
> [name=Tom S]

> 村里級資料 的 merge
> [name=Tom S]


- AP欄：臺灣村里界圖\[TV_ALL\]欄位格式擴充版
> 製作全國地圖時，偶爾會遇到 (鄉鎮市區名+村里名) 有重複的情況，必須再冠上縣市名以區別
> [name=Chen C]


2.  鄉鎮市區級資料
    ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_3eff2989d8f8143cfcb7559cd10e2f5e)


### 列標示

1.  男性、女性與總和分開列表

### 資料作業撇步

1.  先開啟檔案
    ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_2268888082a32c94d1614f44cdd7e7ee)
2.  先開啟新的一頁工作表
    ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_bc89d87f0b2b36c2abab399b07e45811)
3.  在新工作表的表頭的第一欄第一列按下=，回頭點原資料頁的第一欄第一列
> _請留意本圖的函式列_ ==_='opendata-10309_age-63000!'A1_==
> [name=Chen C]

    ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_69b7e5dd94e0d4e20b31f3b5782c6cea)
4.  開始拖曳，拖曳範圍如下：行─往下拉拉到底；列─先拉到性別總和的地方
> 本圖已啟用行列凍結窗格
> [name=Chen C]

    ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_94fe090f4a0deb04f4ca380cf268c894)
5.  由於全台灣的人口資料表都是男女合表並列的，這種模板方便瀏覽，但是很不方便做資料處理，因此，我們需要將資料表中的各年齡層的男女欄位分離成各自的表格。技巧如下：
    1.  先清除女性資料
    ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_679537e5677d611334c679c90ff0d771)
    2.  選取男性資料並多選出一排空排
    ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_50bb84c9c882362bc880956fe5979a50)
    3.  開始拖曳
    ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_2dd2f8e7857291205c993fb7cdd77779)
    4.  ==注意！==如果中間拖曳有休息，休息後重拉的時候，==記得要墊一排空排==
    ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_f31bfafabbcdc29454ad9e81062ac3bb)
    5.  拖曳完之後的長相
    ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_8476cfcc774c7d88db02b39731fa4a8f)
    6.  消除空排的方法：用特殊目標尋找
    ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_5a1840a4f0eb4cf375358e437bf39145)
    7.  點選尋找空格
    ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_a23e2c71e3b551fdb6e45b2a4f3d6a1a)
    8.  選取所有的空格
    ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_088fe8016987696181bbb34a7559d0f3)
    9.  刪除空格
    ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_2c21a245ad78fa583e92574452bb1b0a)
    10.  刪除按下去，勾選==右側儲存格左移==
    ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_5ee8efcde516cb2cb6cecb0dd3b04e86)
    11.  資料分離完成
    ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_f4fe20f6babd3df4d07b9bc2752fbd8e)
    12.  女性也可以如法炮製，先刪除男性資料後拖曳
    ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_f0a71ae552281283d85364926cf84018)
6.  先將要套入的資料分離出來，用插入列和刪除列的方式將==最右上側==的==單一年齡組資料表==的空間調整好，將資料貼入，經過公式連動，可以生成村里層級的三個資料表。
7.  參考村里層級資料表的區域別名稱，在鄉鎮市區級資料更改區域別名稱，即可將資料連動，並生成鄉鎮市區級的三個資料表。

### 公式連結概念

1.  總和表係由男性表+女性表而得的
2.  ==五歲年齡組==係由SUM(**,**)函數自==單一年齡組==將指定年齡組加總而得
3.  ==選舉人口世代==表係由SUM(**,**)函數自==五歲年齡組==將指定年齡組加總而得
4.  ==鄉鎮市區級資料==係由SUMIF(**,**)函數自==村里級資料==的對應資料表由電腦自行檢測符合條件的資料加總而得。
> 記得定義域的部分在行和列上都要打上=="$"==做固定，以便於拖曳時資料不會亂跳
> [name=Chen C]


## GIS地圖製作

### 現今選舉人口

1.  製作==村里級==和==鄉鎮市區級==
2.  年齡層區分為==青年 (20-34)==、==壯年 (35-49)==、==中年 (50-64)==、==老年I (65-79)==、==老年II (80-)==與==總和==
    計算指標：
    - 總和是呈現人數
    - 各年齡層為\[年齡層人口/總和\]的百分比
3.  一個縣市共製作11張地圖，解析度200dpi即可
4.  以目前戰況較關鍵的縣市優先 e.g.臺北市和臺中市

### 人口消長差異

1.  製作==村里級==和==鄉鎮市區級==
2.  年齡層區分為==青年 (20-34)==、==壯年 (35-49)==、==中年 (50-64)==、==老年I (65-79)==、==老年II (80-)==
    計算指標：
    - \[人口差/2014年人口\]的百分比
3.  一個縣市共製作11張地圖，解析度200dpi即可
4.  以目前戰況較關鍵的縣市優先 e.g.臺北市和臺中市

