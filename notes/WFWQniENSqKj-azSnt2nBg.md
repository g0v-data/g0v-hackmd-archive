---
title: "台灣 參與預算提案與追蹤 地圖"
tags: Participatory Budgeting,預算,hackpad
---

# 台灣 參與預算提案與追蹤 地圖

> [點此觀看原始內容](https://g0v.hackpad.tw/8bv7Ygr5wKr)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_e9c1b5658304561c3e108d3094b8260b)
[https://goo.gl/K82xfl](https://goo.gl/K82xfl)

## 專案簡介


### 緣由

一堆縣市政府（或說政治人物）在推參與預算，但是呢？到底人民提案有哪些？後續的狀況又是如何？其實並沒有一個“所在”可以讓大家來看或是後續follow或觀察。
↓↓
也就是呢！看似==**_提案遍地開花，卻不知道到底開了哪些花？_**==

### 要解決的問題

1.  讓各個縣市（即便是不同層級的）參與式預算提案，透過視覺化呈現台灣整體的提案地圖
    1.  需要有各縣市提案可能的欄位
    2.  push各縣市把參與預算提案的開放資料釋出
2.  同時希望可以對應、追蹤政府的後續回應或是民間的施作

### 預定使用者

→ 任何想知道、follow台灣各地民眾的參與預算提案與政府回應狀況者
→ 提供個案計畫執行資料與訊息的人

### 預定功能

- 可用程式寫自動產生全台最新參與預算計畫數與提案數
> 也許可追蹤提案編入市府預算的後續
> [name=ipa c]


### 使用資料

各縣市政府相關民眾提案資料
例如↓
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_4a73d2358a429cb6c45d54e48a889b43)

- 台中2015民眾預算提案：[http://2015taichungivoting.weebly.com/25552266963533630059.html](http://2015taichungivoting.weebly.com/25552266963533630059.html) ； 投票獲選提案 [http://2015taichungivoting.weebly.com/](http://2015taichungivoting.weebly.com/)
- 台北2016民眾預算提案：[http://pb.taipei/ct.asp?xItem=189721910&ctNode=89150&mp=100012](http://pb.taipei/ct.asp?xItem=189721910&ctNode=89150&mp=100012)
- 新北參與預算網站：[http://www.pb.ntpc.gov.tw/](http://www.pb.ntpc.gov.tw/)
- 文化部參與預算網頁：[https://2015cepb.com/](https://2015cepb.com/)
- 高雄市：
    - 高齡與婦女議題，政策型參與式預算
    - 〈濱線文化廊道〉參與式預算實驗計畫，哈瑪星十個里與鹽埕區八個里，票選出五萬，一案 20 萬，提案不設限 [https://www.facebook.com/KPB2016/](https://www.facebook.com/KPB2016/)

#### 資料欄位構想

- 地圖呈現人民提案的資料欄位如下
    1.  ==提案名稱==
    2.  ==提案對應的行政區（市 / 行政區 / 鎮 / 里)==
    3.  ==提案的範圍（位置）==
        1.  單點
        2.  範圍 polygon
    4.  ==提案的內容簡述==
    5.  提案案件的網頁
    6.  提案人/團體
    7.  預算金額或項目
    8.  該提案所屬的年度計畫或特定主題計畫，例如「2015 永和區的提案屬於新北市節電計畫」
    9.  該計畫的執行計畫團隊，例如「中山大學ＯＯＯＯ團隊」
    10.  機關的回應與評估
    11.  計畫後續狀況 / 發包或是落實環節的訊息
    12.  此資料來源 / 文件產製者：官方或是執行單位，或是計畫參與者
    13.  其他資訊

#### 討論

- 各地執行機制不同，基本的提案體檢型項目為何？以及，如何掌握可以看出門道的資料內容（例：公務人員在什麼環節中參與、扮演什麼積極或消極角色等）？
- 每個提案是否能打散？例如新北市節電提案與台中市豐原區提案，適合並置嗎？


### 現有類似專案

[http://backend.pbnyc.org/maps/?d=0&display_type=winners](http://backend.pbnyc.org/maps/?d=0&display_type=winners)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_548c7c2655ee15f56c30da35dc8f6a0f)
- 紐約市：[http://ideas.pbnyc.org/12/40.79575/-73.90623](http://ideas.pbnyc.org/12/40.79575/-73.90623)
- 馬德里：[https://decide.madrid.es/proposals/13105-control-del-spam-en-madrid-decide](https://decide.madrid.es/proposals/13105-control-del-spam-en-madrid-decide)

#### 資料欄位

- 資料標籤
    - 政策面向
        - 紐約市
            - 學校
            - 公園和娛樂
            - 文化和社區設施
            - 街道及交通運輸
            - 住房
            - 銀髮族
            - 安全
            - 青年
        - 馬德里
            - 協會
            - 文化
            - 體育
            - 社會權利
            - 區
            - 經濟
            - 僱用
            - 公平
            - 環境
            - 媒體
            - 流動性
            - 參與
            - 健康
            - 安全與應急
            - 可持續性
            - 透明度
            - 城市規劃
    - 全部提案 / 投票獲選提案
- 政府回應
    - ...


### 相關專案

- 台中2016參與式預算團隊有委託TonyQ幫忙他們案子做台中參與式預算提案的地圖  [http://](http://210.69.115.29/areas/map)[210.69.115.29/areas/map](http://210.69.115.29/areas/map)
- [台北市歷年社造地圖](https://www.google.com/maps/d/u/0/viewer?hl=en_US&mid=1hHG2kZNKo5w-yiCnUl7fvczNdKc)
- [參與式預算資料收集共筆](https://g0v.hackpad.tw/rsn8O1wiDyk)
- 台北市政府的系統網站 https://pb.taipei/Default.aspx

### 授權方式

- 程式碼：
- 文件：
    - 各個參與式計畫本身的文件與各類內容產出之授權為何？依照官方網站的公開資訊原則嗎？

### 專案目前狀態

- 蒐集各個計畫形成清單名目
- 探討「如何展現一個參與式預算計畫」所必要的資料欄位與文件有什麼？
- 蒐集可能的工具與方案：
    - 城市提案與募資平台 [https://g0v.hackpad.com/VpijNWeYhps](https://g0v.hackpad.com/VpijNWeYhps)
    - google my map


### 利益揭露




## 徵求協作者


發起人/拋磚人：
- [ ] NeedsWriter: 需要文案幫手（撰寫基本資訊、報導專案etc）
- [ ] NeedsDesigner: 需要介面設計
- [ ] NeedsData: 需要資料（擷取、清理）
- [ ] NeedsTech: 需要技術支援（程式、架站 etc)
- [ ] NeedsProcess: 需要幫忙設計作業流程
- [ ] NeedsTalkingToRealPerson: 需要有人幫忙和其他機關聯絡


## 實作細節（非技術背景可跳填）


### 協作工具

- github repo：
- hackfoldr 工作資料夾網址：
- google drive 共用資料夾網址：

### 進度與 to-do

> 僅供參考
> [name=ET B]

- [ ] product planning（recommanded procedure from justin lee / 李易修）
    - [ ] strategy
    - [ ] scope
    - [ ] structure
    - [ ] wireframe
    - [ ] visual
- [ ] web front-end
- [ ] web back-end
- [ ] ui / visual design


## 成果展示（規劃文件、雛形/草稿、原型/初稿、正式發佈/完稿）



