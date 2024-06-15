---
tags: 民防
---

# 全台防災/防空避難所大統整

防空/防水/防震 避難所都是不一樣的，希望能有一個統一整理的資料庫，讓之後離線防災資料庫可以納入

## 0615 - 遊說計劃
- 目標：遊說內政委員會的立委，請立委協助去督促內政部長將防災避難資訊進行大統整
- 本日行動：
    - 找哪些立委可以優先遊說（建議國民眾三黨都找 or 全找）
    - 建立說帖（建議用一個五分鐘可以說明完的投影片）
    - 查詢遊說的法定流程
- 推薦立委名單
    - [內政委員會名單](https://www.ly.gov.tw/Pages/Detail.aspx?nodeid=55099&pid=236907)：丁學忠(國)、麥玉珍(眾)、牛煦庭(國)、王美惠(民)、吳琪銘(民)(召委)、李柏毅(民)、徐欣瑩(國)、高金素梅(無)(召委)、張宏陸(民)、張智倫(國)、許宇甄(國)、黃建賓(國)、黃捷(民)、蘇巧慧(民)
        - 國民黨：
        - 民進黨：張宏陸（板橋人，Ronny可以直接拜訪，雖然選區不同）
        - 民眾黨：麥玉珍
- 說帖
    - 以五分鐘講完為目標
    - 先說明現在資料的分散（防空、防災、防洪、防震資料分散）
    - 再說明如果有統整的資料可以做到什麼事（目前數位韌性松的成果）
    - 目標希望由內政部統整所有資料，並且以開放資料型式定期更新釋出，讓大家可以用這資料來做各種離線 App
    - 其他
        - 防災避難收容所開放資料集有誤，由民間社群勘誤經緯度至少 200 筆資料，其地點經緯度位置標示錯誤 https://g0v.hackmd.io/@waytosafety/home/
- 遊說流程
- 找到的東西
    - [消防署消防防災e點通 app](https://play.google.com/store/apps/details?id=com.nfa.report&hl=zh_TW)
        - [web app](https://bear.emic.gov.tw/MY/)

## 0615 - 離線計劃
- 目標：平常可下載相關資料儲存，在飛航模式開啟後手機仍可查看
    - 相關資料：防災避難知識，防空避難所位置...

## 0525 討論
- 完成基本功能：
    - 根據現在 GPS location 找到所在經緯度村里
    - 顯示該村里資訊
    - repo:  https://github.com/g0v/evacuation-map-viewer
    - 網址規則：https://ronnytest.ronny-s3.click/simple-evacuation-map/html/{village_id}-{type}/page-html.html
    - 今日成果：https://g0v.github.io/evacuation-map-viewer/
## 0427 討論
- 本日目標
    - 製作一個網頁功能，可以根據裝置的經緯度（[Geolocation API](https://developer.mozilla.org/en-US/docs/Web/API/Geolocation_API)) ，然後查到這個經緯度附近的村里，並且回傳該村里的相關防災地圖
    - 已有資料
        - [台灣村里列表](https://gist.github.com/ronnywang/aa8011b9bd09d18faae398ef55991ee3)
        - [已有避難圖村里](https://github.com/ronnywang/simple-evacuation-map/blob/main/village-log.csv)
- 本日成果：
    - E 處理苗栗資料: https://docs.google.com/spreadsheets/d/10mkZhe8VB0CfkcC3wq4cDkXA5fGOlKOO5ncebU68VJ0/edit#gid=2060256247
    - Super 在研究利用 Geolocation 抓出對應村里 https://github.com/Super1115/getTownCodeTW
    - Ronny 處理台北市更多村里資料
## 目前進度：
- [簡易避難地圖整理](https://github.com/ronnywang/simple-evacuation-map)
    - 各縣市品質不一
    - 有的中英文都有，有的只有中文
    - 大部份都有提供村里圖片下載，並且有疏散方向
    - 有的會把水災震災分出來
    - Ex: https://dpcwh.chfd.gov.tw/assets/upload/info/埤頭鄉村里簡易疏散避難圖.pdf
    - 以各村里簡易避難地圖整理為目標（有的圖會有避難方向等資訊）
- [WaytoSafety 隨時隨地知道避難場所位置
Shelter Map (Taiwan, Japan, Korea)](/SdlX05_hS4e_eeierjkxyQ)
    - 以避難點位整理為目標（有經緯度）
    - 透過經緯度可直接做出全台灣的版本
    
    
20240323 成果
- 追加彰化縣
- https://ronnytest.ronny-s3.click/simple-evacuation-map/page/
- 