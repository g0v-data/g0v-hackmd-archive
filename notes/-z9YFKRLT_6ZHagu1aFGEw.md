
# 消防找水小幫手
* 使用google助理(google actions)找水的小專案

---

## 緣由
* 參加義消常被"長官聊天"想寫個app
* 第一次聊天，快速找到消防栓位子的APP
* 第二次聊天，利用google my maps快速找到消防栓位子
* 第N次聊天，利用AI快速找到消防栓的APP
* 被一直聊天只好做個簡單好用的非APP應用

## g0v youtube 資料
* 當天提案https://www.youtube.com/watch?v=MCWpuAP4Jik
* 當天成果https://youtu.be/tMKjggEncnE?t=279

---

## 要解決的問題
* 協助消防員在第一時間，快速找到消防栓(含地下消防栓)

---

## 心中的消防栓
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_76bac352eb2d18fb87acf1157fe196e1)

---

## 現實中的消防栓
* 地下型消防栓
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_145a75dd4bebc6a3e1ca29e9553aa2fc)



---

## 預定使用者
* 消防員
* 義消
* 想知道附近消防栓的市民

---

## 預定功能
* 利用google助理(google actions)，快速詢找附近的消防栓。

---

## 現有類似專案

* 美國消防員的希望http://bit.ly/2UcPYgO
  (大都是利用google my maps)-國外
* 讚！基隆役男自建消防栓地圖app http://bit.ly/2ZXJRhK -國內
* 雲端定位消防栓提升打火速度 http://bit.ly/2ZRd39S -國內
* https://www.osmhydrant.org/en/　-國外，supaplex 提供

---

## 授權方式
* 程式碼 CC BY-NC 3.0 TW
* 專案 CC BY-NC 3.0 TW


---

## 使用資料
* 大臺北地區消防栓清冊1080627-http://bit.ly/2ZTE3pp
* 新版士林區水源地圖- http://bit.ly/2ZSzJXl    
* OpenStreetMap Overpass Turbo-https://overpass-turbo.eu/s/M7X (之後查詢osm及下載用)
* 台灣自來水公司-https://data.gov.tw/dataset/44642
    * 裡面的資料有包含了座標位置（但是用TWD97座標），以及型態
    * ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_7d2c191edf67fbf58a8c46c3b988b70c)

    * ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_7bfa85a1b9aee5a3724c1513a759e818)
    
* 臺中市政府-https://opendata.taichung.gov.tw/dataset/3ac85b2e-1a9f-11e8-8f43-00155d021202
    * 有GPS，之後可以串
* 內政部-https://data.moi.gov.tw/MoiOD/Data/DataDetail.aspx?oid=E2BD8536-B23B-4E87-B3FC-EF91A5F00789
    * 消防的水源訊息，沒有GPS訊息
* 嘉義市-https://data.chiayi.gov.tw/opendata/dataset/metadata?oid=f765487a-dd64-4374-b660-3f90f97e1a96
    * 消防栓的統計資料，沒有GPS
* 高雄市-https://data.kcg.gov.tw/dataset/fire-hydrant-up
    * 有gps (xml檔案), 很酷的是沒有地下消防栓（會不會就真的是沒有）
* 高雄市(地下)-https://data.gov.tw/dataset/86391
* 新竹市-http://opendata.hccg.gov.tw/dataset/hcfd-20150504-160311-0111
    * 這個資料只有路口的名字，沒有GPS
* 屏東縣-https://www.pthg.gov.tw/Cus_OpenData_Default1.aspx?n=481C53E05C1D2D97&sms=354B0B57F2762613
    * 沒有GPS資訊
* 臺北市-https://data.taipei/opendata/datalist/datasetByFormat;jsessionid=47A75A96401C668655926552993579F5?oid=odt
* 桃園市-https://data.tycg.gov.tw/opendata/datalist/datasetMeta?oid=3fd4a492-bcae-45be-8184-aa6fad506701
* 臺南市-https://data.tainan.gov.tw/dataset/fire-water-supply
    * 統計資料，只有每個區域的消防栓數量，沒有詳細位置
* NLSC 消防栓套疊地圖
    *  消防栓    [分類:災害潛勢圖層] 圖資說明：
依據 台灣自來水股份有限公司 及 臺北自來水事業處 於政府資料開放平臺的消防栓開放資料產製

---


## 構想
* 使用用google 我的商家功能 
* google 助理 搜尋附近地點
* Google Maps 遺漏的地點
* 推坑導航軟體


---

## 規劃
* 使用用google 我的商家功能-
  連絡過"google我的商家",非營業點不支援這用法
* google 助理(actions) 搜尋附近地點-開發程式
* Google Maps 遺漏的地點-需和管理地圖的社群溝通
* 推坑導航軟體-有熟的朋友歡迎一起推坑

---


## 利益揭露
* 目前無

---

## 徵求協作者

* NeedsWriter: 需要文案幫手（撰寫基本資訊、報導專案etc）
* NeedsData: 需要資料（擷取、清理）
* NeedsTech: 需要技術支援（程式、架站 etc)
* NeedsTalkingToRealPerson: 需要有人幫忙和其他機關聯絡

---

## END

---


## 實作細節（非技術背景可跳填）

* github repo：

* google drive 共用資料夾網址：

* OpenStreetMap API: Overpass API (待查)

---

## Scott Chang
* 支援app部份(android app 舊的)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_fa4cd486e2124bfad30444ffd857d780 =140x245) ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_7ac75f141cce7726c6a59d41b343bf87 =140x245)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_758a9a7b5bde551dd426876779f6028b =280x490)



---

## ChenJuilin
* 支援 osm部份及整理
* 參考 Overpass Turbo-https://overpass-turbo.eu/s/M7X 

---

## 進度與 to-do

* Scott Chang 支援app 2019-09-07會先出一版app
    * 希望之後可以有API可以接，這樣的話只要後台有更新，消防栓也可以直接在前台改變
    * [Github repository](https://github.com/ChingSheng/MyFireHydrantMap/tree/master)
        * 沒有把Google Map API Key release出來


---

## 討論

* 目前google我的商家不可行
* osm專家來協助 https://www.facebook.com/ChenJuilin
* osm專家協助 https://www.facebook.com/irvinfly
* android app開發者 Scott Chang 支援app http://bit.ly/2LvDWuR
* 好想工作室 Backend學員 g0v slack@Shiva

---

## 簡介

* osm  http://bit.ly/2tF9j0U
