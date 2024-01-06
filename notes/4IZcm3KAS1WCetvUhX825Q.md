---
tags: GIS
---

# 交通道安資料、交通事故、肇事、碰撞構圖資料

:::warning
資料在哪裡？檢視各單位資料誰比較詳細？
社群討論串：https://www.facebook.com/groups/odtwn/permalink/5739847046029666/

目錄
[TOC]
:::

## 中央：即時交通事故資料 by 內政部警政署

資料
- 即時交通事故資料 (A1類)
    - A1類：造成人員當場或24小時內死亡之交通事故。
    - 有經緯度
    - json格式：https://data.gov.tw/dataset/57023
    - csv格式：：https://data.gov.tw/dataset/12818
    - 每週一下午 5 點左右更新
- 即時交通事故資料 (A2類)
    - A2類：造成人員受傷或超過24時死亡之交通事故。
    - 有經緯度
    - json格式：https://data.gov.tw/dataset/57024
    - csv格式：https://data.gov.tw/dataset/13139
    - 每個月 1 & 15 日下午 5 點更新資料
- 即時交通事故資料(A3類)
    - https://data.gov.tw/dataset/87495
    - 只有地點描述，沒有經緯度

### 運用「即時交通事故資料」民間製作的資料地圖與探討
- https://commusidewalk-app.vercel.app/accident
- 關於「即時交通事故資料」資料集的探討文件
    - https://g0v.hackmd.io/uLLiATcoTOeBYbLeSvkeQQ
    - 村里事故統計地圖：https://kiang.github.io/NPA_TMA/
- 20230107 READr 全面檢視車禍事故死亡資料：臺灣如何成為行人地獄？
    - https://www.readr.tw/post/2931

## 中央：歷史交通事故資料 by 內政部警政署
- 提供近 9 年A1類及A2類交通事故之發生時間、發生地點、死傷人數及車種等資料，依各年份釋出
- csv 資料集網址：https://data.gov.tw/dataset/12197
- 有經緯度
- 資料欄位：發生時間、發生地點、死亡受傷人數、車種、經度、緯度
    - 有 A1類：造成人員當場或24小時內死亡之交通事故。 
    - 有 A2類：造成人員受傷或超過24時死亡之交通事故。
    - 沒有 A3類 (指僅有車輛財物受損之交通事故)
    - 本項資料集每半個月更新一次。 
- 資料課題：
    - 無詳細事故內容
    - 有經緯度
    - 不確定死亡與受傷欄位的數字，是對應到該次事故中的哪一個車種
        - 歡迎至該資料集頁面提問 
            - https://data.gov.tw/dataset/12818
            - https://data.gov.tw/dataset/13139
- 資料勘誤
    - 「111年傷亡道路交通事故資料」A1與A2的事故資料，新北市許多橋梁上發生的事故，經緯度被定位到新北市政府
        - https://www.facebook.com/100064543938480/posts/pfbid02doGGf3G2pHgG51TugX3EJp8HLcLoxUsmCYSDnQ6dnsNP4bgwM1Ai5wjZQFKUvrVLl/?app=fbl

### 運用「歷史交通事故資料」民間製作的資料地圖

https://commusidewalk-app.vercel.app/accident

2020 全國交通事故地圖 by dubidub
- 地圖網址：https://dubidub.github.io/traffic_accident_2020/zh_tw
- 製作說明：https://dubidub.github.io/blog/road-safety-data-visualization-taiwan-2020/

資料地圖試作：109年度A1與A2類交通事故資料
- 全國 A1 類交通事故地圖(死亡人數1851人)：https://app.awesome-table.com/-Mt2iOcvmjQ5Lyqqyxyp/view
- 宜蘭花蓮臺東 A1 與 A2 交通事故地圖109年度：https://app.awesome-table.com/-NBrZjiSeu1XWr0v2lWq/view
- 基隆臺北新北桃園 A1 與 A2 交通事故地圖109年度：https://app.awesome-table.com/-NBrj_Mq3V1eOU5STH_c/view
- 新竹苗栗臺中 A1 與 A2 交通事故地圖109年度：https://app.awesome-table.com/-NBrueYOuhYkg6wQBzas/view
- 臺中彰化雲林南投嘉義 A1 與 A2 交通事故地圖109年度：https://app.awesome-table.com/-NBrsJtrZ2_sUJoefzPJ/view
- 臺南高雄屏東 A1 與 A2 交通事故地圖109年度：https://app.awesome-table.com/-NBrPYrXRNBCgc7ZcsA4/view
- 澎湖金門連江 A1 與 A2 交通事故地圖109年度：https://app.awesome-table.com/-NBrmRcYU3po3iSe8agj/view

2020年涉及單車的A1與A2交通事件的地圖
- bit.ly/3AH2hsh
- 討論串 https://www.facebook.com/groups/criticalmasstw/posts/6154781267872717/

## 中央：道安資訊查詢網 by 交通部道路交通安全督導委員會

圖台網址：https://roadsafety.tw/
- 沒有釋出資料 !
    - 歡迎至政府資料專區提問 ! https://data.gov.tw/suggests
- 爬蟲 by Kiang：https://github.com/kiang/roadsafety.tw

圖台資料有缺漏，討論串：
- 華江橋橋上事故未顯示 https://www.facebook.com/100057184730470/posts/400350281881126/
- 沙鹿區向上北路七段與自立路與屏西路叉路口，資料下架https://www.facebook.com/story.php?story_fbid=pfbid029JJTAWH9HpuMtsiqStaazapQhTdqfnvkU3nCYenyYwETTF3HMMm41hubNrNZeAbUl&id=100044309925245&mibextid=tejx2t

## 中央：道路交通安全資料整合與分析平台
同樣由交通部道路交通安全督導委員會所建置的系統，只是提供內部使用為主，包含警政署建置系統的大部分資料，去識別化後在這個系統提供各縣市道安會議研究使用。也因為已經完成去識別化，所以過去有提出希望釋出全部資料，但無疾而終

2020.03 資料需求詢問網址：https://data.gov.tw/suggests/115971
- 事故欄位：警察局名稱, 轄區分局名稱, 編號, 總編號, 發生時間, 處理編號, 交通事故類別, 發生地點, 死亡人數, 受傷人數, 天候, 光線, 道路類別, 速限, 道路型態, 事故位置, 路面狀況, 柏油, 乾燥, 無缺陷, 快車道或一般車道間, 快慢車道間, 路面邊線, 道路障礙, 無障礙物, 良好, 號誌種類, 號誌動作, 車道劃分設施-分向設施, 事故類型及型態, 座標X, 座標Y
- 關係人欄位： 事故編號, 性別, 受傷程度, 主要傷處, 保護裝備, 行動電話持有情形, 車輛用途, 駕駛資格情形, 當事者區分(類別), 當事者行動狀態, 駕駛執照種類, 飲酒情形, 車輛撞擊部位, 肇因研判, 肇事逃逸, 職業, 旅次目的

## 中央：優先改善 1000 處行人事故熱點

交通部依事故嚴重度及頻率盤點優先改善1000處行人事故熱點
發布單位：路政及道安司
新聞稿網址：https://www.motc.gov.tw/ch/app/news_list/view?module=news&id=14&serno=32de7207-1cf4-47f3-bf19-f256ed25cc02
PDF 文件釋出網址：https://www.motc.gov.tw/ch/app/multimessage_list/view?module=doan&id=10035&serno=372d096c-d004-4b61-9223-fa338cf479cf
注意：只有 PDF，沒有資料集＠＠"

### 民間製作的資料地圖

Kiang 製作民間版地圖：https://tainan.olc.tw/p/1000/

## 各縣市釋出資料

資料開放平台，建議使用關鍵字：交通事故、肇事
https://data.gov.tw/
TODO：預計檢視各縣市釋出資料集的內容程度，並貼到下方對應的段落
- 有詳細事故內容，有經緯度
- 無詳細事故內容，有經緯度
- 無詳細事故內容，無經緯度
- 僅熱點或部分內容
- 完全沒有額外釋出交通事故資料

### 有詳細事故內容，有經緯度：桃園市、臺中市、臺南市
有釋出進一步的事故內容 (事故類型及型態、主要肇因等，搭配調查報告代碼對照表)

#### 110年桃園市交通事故資料表-含第二當事人
- 1.提供桃園市交通事故資料彙整，資料包含事故現場環境及相關肇事因素等。
- 2.資料包含所有當事人，可使用當事人順位欄位進行篩選。
- 3.交通事故資料表自106年起更新格式，整合經緯度及代碼對照。
- 4.107年起新增當事人性別及年齡欄位。
- csv，有經緯度
- 資料位置：https://data.gov.tw/dataset/143048


#### 臺中市政府警察局110年10月份交通事故資料
- 用月份釋出資料
- 欄位：年、月、日、時、分、縣市、區、死、受傷、2-30、天候、光線、道路類別、速限、道路型態、事故位置、路面鋪裝、路面狀態、路面缺陷、障礙物、視距、號誌種類、號誌動作、分向設施、快車道或一般車道間、快慢車道間、路面邊線、事故類型及型態、主要肇因、受傷程度、主要傷處、保護裝備、行動電話、當事者區分、車輛用途、當事者行動狀態、駕駛資格情形、駕駛執照種類、飲酒情形、車輛撞擊部位最初、車輛撞擊部位其他、肇事因素個別、肇事因素主要、肇事逃逸、職業、旅次目的、車種、GPS緯度、GPS經度、事故類別
- 搭配「調查報告代碼對照表」https://www.police.taichung.gov.tw/traffic/home.jsp?id=55&parentpath=0,5,53&mcustomize=multimessages_view.jsp&dataserno=202006110001&t=Download&mserno=201801260055)
- 資料位置：https://data.gov.tw/dataset/147029


#### 臺南市道路交通事故原因傷亡統計
- https://data.tainan.gov.tw/dataset/policedata016
- 欄位：
    - _id: 41
    - 案件編號: 11007AC191B0368
    - 發生日期: 20210707
    - 發生時間: 105200
    - GPS經度: 120.22006
    - GPS緯度: 22.977641
    - 案件類別名稱: 交通事故
    - 地址類型名稱: 交叉路口
    - 發生縣市名稱: 臺南市東區崇明路段崇學路口巷弄號
    - 24小時內死亡人數: 0
    - 2-30日內死亡人數: 0
    - 受傷人數: 1
    - 天候名稱: 晴
    - 速限-第1當事者: 50
    - 道路型態大類別名稱: 交岔路
    - 事故位置大類別名稱: 交叉路口
    - 號誌-號誌種類名稱: 行車管制號誌(附設行人專用號誌)
    - 事故類型及型態大類別名稱: 車與車
    - 肇因研判子類別名稱-主要: 未依規定讓車
- 民間製作線上地圖：臺南市道路潛藏危機地圖
    - https://www.facebook.com/355650727953853/posts/656866094498980/
    - 涵蓋時間從2016年6月~8月，總計2932件交通事故

### 無詳細事故內容，有經緯度：臺北市

#### 臺北市道路交通事故斑點圖
- 提供臺北市道路交通事故發生時間、處理別(1類指造成人員當場或24小時內死亡之交通事故；2類指造成人員受傷或超過24小時死亡之交通事故；3類指僅有車輛財物受損之交通事故)、肇事地點、座標點位資料。
- csv，有經緯度，但沒有說明事故內容細節
- 有部分資料經緯度明顯錯誤，大概 10 筆
- 資料位置：https://data.gov.tw/dataset/136123
- 整理後資料：https://docs.google.com/spreadsheets/d/1SnOITsi15g4JupcGMxqEmoG9QIlxNS-JPJyc0cgJges/edit#
    -  手動微調錯誤經緯度
- 線上地圖試作
    -  https://app.awesome-table.com/-MsySXqgZNFOWBN5hppp/view

### 無詳細事故內容，無經緯度

- ?縣市

### 僅熱點或部分內容

- ?縣市

### 完全沒有額外釋出交通事故資料

- ?縣市

## 肇事碰撞構圖 Collision Diagram

資料平台上有網友詢問「地方政府肇事碰撞構圖」
https://data.gov.tw/suggests/96658
- 網友提到：已知目前高雄市(104/106 年高雄市易肇事路口改善委託研究案)以及台中市(智慧系統)有建構相關的系統或有相關資料，相關資料對於人民分析路口之事故有很大的幫助。thanks。
- 各單位回覆狀況：
    - 僅 臺中市政府 回覆：您好，有關您來信關於「地方政府肇事碰撞構圖」，目前本府仍在持續進行碰撞構圖之應用分析與系統功能建構精進作業中，等到功能開發完成後將對外公開。
    - 可能是因為製作人力不足，例如新竹縣政府是這樣回覆的：查製作交通事故肇事碰撞構圖目前仍需要人力製作，本局交通隊負責交通事故業務僅2人，目前每月須審核約500件交通事故初判表，人力不足，故暫無法提供肇事碰撞構圖，且本轄道路路口不計其數，提供肇事碰撞構圖勢必需增加人力，請諒察。
- 社團討論串：https://www.facebook.com/groups/2819127468115692/posts/3653803231314774/

## 資料應用發想

- 針對行人傷亡事故，每一個事件
    - 製作一個獨立網址頁面
    - 現場凸顯方式
        - 方案一：附近找一個可安全閱讀公告的位置；採用視差裝置（手法案例待補）
        - 方案二：至事發地點經緯度，採用自然塗料，塗鴉出現場視覺可見的標記；但也要考慮避免造成「陷阱」效果，讓人們更逗留在該地點
            - 202305 https://www.facebook.com/story.php?story_fbid=pfbid02t2kERYegKRrAqh6vKRkwPo57Jd4kysbb33qrqmh2Y9gLW3Sn9yo7HzCcvahhMXsFl&id=100000276664426&mibextid=qC1gEa
- 車禍熱圖
    - https://g0v.hackmd.io/lzPZea_9Q1uZ3mv2ihY3PQ

## 政府單位運用資料的方式

苗栗縣政府「苗栗縣轄區易肇事地點委外規劃設計、工程改善計畫」決標案件
- 基於 A1 A2 熱點、交通部道安觀測指標，挑選改善位置
- 招標文件與案件追蹤共筆：https://g0v.hackmd.io/f7BJ5a2qQxmKDDyuTyCJrQ?view