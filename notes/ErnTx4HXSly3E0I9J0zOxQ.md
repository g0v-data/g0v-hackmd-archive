---
tags: GIS
---

# 好連街 - 連續型行人路徑繪製步驟
Continuous Pedestrian Pathway

:::success
歡迎加入交流討論社團：https://www.facebook.com/groups/295496753001414/permalink/355916826959406/
:::

:::warning
本文件目錄如下
[TOC]
:::

## 什麼是「跨街區連續型行人路徑」？

### 介紹

在街區內創造一條連續的行人路徑，且盡可能避免受到車道阻斷
阻隔部分路口，避免車輛直通穿越

#### 名稱發想

- 主軸是形塑出街區內，可以感到安心、放心、人走的路
- 動作：研擬、實踐
- 目標：街區內安心的行人路徑


### 參考案例

#### 國際巴塞隆納

<iframe src="https://docs.google.com/presentation/d/e/2PACX-1vSJ1EDIzKek2QdNWGR76oeA311ud1oTESIvSGj0-T7xdeuLPXKIgI2LTbemtFws8zYO_Bobdd9Gy2fO/embed?start=false&loop=false&delayms=3000" frameborder="0" width=100% height="470" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe>

另開簡報
https://docs.google.com/presentation/d/1MqY6TI4I1GgPUt4Mo05zHeg0A5DYIMlj35Rcej_X5cE/edit

待整理內容
https://www.facebook.com/share/9jkpUvRvNzEFkJbn/?mibextid=WC7FNe

#### 臺灣情境試作地圖
另開地圖：https://maps.app.goo.gl/X4C3X5fb5rMY1q5C6

<iframe src="https://www.google.com/maps/d/embed?mid=1lG4BxKyoiLXTIReVRpw8PPLpI81NU0E&ehbc=2E312F" width=100% height="480"></iframe>


## 繪製步驟

### 一、街廓在哪裡

(1) 定義：街廓是由「行人不得任意穿越的邊界」所界定的

(2) 「行人不得任意穿越的邊界」有哪些常見類型？
- 大型道路
    - 公路系統 https://www.thb.gov.tw/cp.aspx?n=430
        - 例如外環道 ...等
    - 一般來說，會設有紅綠燈，讓行人集中於特定位置才能穿越道路
- 軌道設施，例如地面鐵路、地面捷運
- 河道與堤防
    - 河川治理線
    - 水圳與排水渠道
- 坡地林地

(3) 街廓類型
- 類型研判原則
    - 街廓內部的路網結構，如果有十字棋盤架構，不論內部路網是直線的或是彎曲的，可以標記為棋盤街廓
    - 如果街廓外部，有一側基本上已經是都市邊界，通常這種街廓輪廓外型也會比較狹長
- 均質街廓：
    - 街廓邊界外的狀態，各方位面向都類似
    - 一開始取名為「棋盤街廓」
- 帶狀街區：
    - 街廓外部，有一側基本上已經是都市邊界，通常這種街廓輪廓外型也會比較狹長
- 帶狀街區-依山：
    - 有一側有明顯的山區
- 封閉地區：
    - 航空機場、大面積軍營...等
- 其他筆記
    - 建築群落
    - 建築+農地，也可以視為農機具動線延伸的產業腹地


#### 工作進度與筆記

2023.11 臺北市、新北市三蘆地區、高雄市高雄火車站地區
2023.12 臺南市新化區、臺南市後壁區 (地區環境分區比都市計畫範圍小)

- 均質街區漸變
    - 臺北市、新北市三蘆地區、高雄市高雄火車站地區
- 小街廓到廣域街廓，很快
    - 例如臺南市新化區 (地區環境分區比都市計畫範圍小)


### 二、跨街廓路徑

跨街廓路徑，通常是也是紅綠燈位置

### 三、街區資訊

- 學校大門位置，師生匯聚動線節點
- 公園與公共機構位置
- 街廓內的停車場出入口
- 單行道
- 雙向道
- 搭配土地使用分區：現況巷弄並非都市計畫道路、檢視未開闢道路 https://nsp.tcd.gov.tw/ngis/

### 四、繪製「街區內連續型行人路徑」

- 可以先嘗試參考「跨街廓路徑」的位置，來當作「街區連續型行人路徑」
- 考量街廓內的停車出入口需求
- 單行道
- 雙向道
- 找出有潛力改造為「禁行汽車或機車的巷弄」

## 效益與課題

回家的汽車與機車駕駛人

送貨的司機

使用巷弄內停車位的駕駛

行人，行走連續度提高

單車使用者，騎乘連續度提高

車用道路養護面積可以下降

人車衝突路口數量下降


2023.11 臺北市大安區大學里交通改善問卷中，有提到「阻隔部分路口，避免車輛直通穿越」這項改善措施
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_aa273de9870855c8384ba143e8ae0583.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8b6f54c98ce840e1576753cd92443230.png)

## 發想筆記

一些留存至今的聚落範型
- 五營
    - 掌潭村 https://eyesonplace.net/2021/01/27/16247/
- 《台灣傳統都市空間之研究》

道路網格的起源
- 日治時期臺灣總督府土木技師濱野彌四郎對臺灣城鄉發展近代化影響之研究 https://hdl.handle.net/11296/6arwby
- 一些針對路網結構發展歷程的地區研究 https://g0v.hackmd.io/NvOW-IGPR3aXjD4g1NHMoQ?view

路的轉型
- 街區空間調整的創意方案，似乎是來自於特殊情境，例如 西門町徒步街源自於日治時期市區計畫劃設的街廓通常為 100 公尺；大園區內部開始推動無車巷弄與軸線，即臺灣大學校園規劃、科教館園區基河路無車化；捷運設站並且改變街區道路系統，南京復興站與慶城街，以上的經驗，其實都可以形成通用原則
- 不過台灣都市普遍街區，可能都還是需要參考 巴塞隆納 車道系統調整以便挪用道路用地，轉化成開放空間，並且創造街區內連續且不被車道阻斷的的行人路徑
- 近年道路標線改造 https://g0v.hackmd.io/X8mWlCWIRkOfCIhTjp1oLA
- 街區開放空間
    - 都市永續轉型與韌性建構-「街區開放空間」都市永續轉型與因應氣候變遷之機會與挑戰 —使用者面向(子計畫五)
        - https://www.grb.gov.tw/search/planDetail?id=14511537
    - 蔡育新*;徐嘉信;林家靖, 2023.06, '「街區開放空間」之氣候變遷規劃綜效與共效益- 建物重建對主次要道路之驅動, ' 都市與計劃, pp.已接受.(TSSCI)(*為通訊作者)
        - https://landeconomics.nccu.edu.tw/PageStaffing/Detail?fid=4486&id=1688
    - 蔡育新*;徐嘉信;王絢;林家靖, 2021.03, '因應氣候變遷之都市街區規劃設計策略與永續「共效益」--建物重建階段, ' 都市與計劃, Vol.48, No.1, pp.27-49.(TSSCI)(*為通訊作者)
        - https://landeconomics.nccu.edu.tw/PageStaffing/Detail?fid=4486&id=1688
    - 都市「街區開放空間」「以自然為本(Nature-based Solutions , NBS)」規劃設計之氣候變遷綜效、權衡、共效益－社區道路
        - https://hdl.handle.net/11296/74u6f6
    - 綠色基礎設施於都市「街區開放空間」對氣候變遷減緩與調適之綜效、權衡與共效益
        - https://hdl.handle.net/11296/279a64
    - 氣候變遷導向街區開放空間規劃的挑戰與機會－臺北市經驗
        - https://hdl.handle.net/11296/8xxrzj
    - 都市街區開放空間之空間設計效率-活動行為導向
        - https://hdl.handle.net/11296/4sbjk4

發想
- 界定出街廓後
    - 假設這個大街廓單一產權，單一土地使用機能
    - 可能會變成重複
    - 以實際街廓狀態來看，產權分佈與決策傾向、對於機能的設定，視為能創造街廓特色的來源


溝通文宣
- 一起來當「街區設計師」「街區連結師」「生活連結師」
- 一條「社區慢跑路線」不用封街... 

財政
- 各個重劃區基金，名稱待查
- 都更基金，街區地區

無號誌路口
- https://www.facebook.com/share/p/Uxv3rD4GaR9cGfpE/?mibextid=WC7FNe


### 名稱發想

英文
- Continuous Pedestrian Pathway
- Crossing 
    - Crossing Intersections Safely
- Intersection

中文
- 主軸是形塑出街區內，可以感到安心、放心、人走的路
- 人行道 不間斷 連續
- 拼出一條安心路
- 走出一條安心路
- 街區安心回家路
- 找好路
- 好街
- 街起來
- 接 街
- 連接
- 行 好 街
- 連好街
- 好連街
- 用散步連接美好、不受車道干擾
- Good Path
- 「連街指數」，檢視不同街廓的「連續型行人路徑完整度」
- 路上觀察學院
- 好街創造學院
- 好街研造 好街營造
- 街大歡喜
