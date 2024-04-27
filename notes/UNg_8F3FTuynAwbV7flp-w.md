# 全台防災/防空避難所大統整

防空/防水/防震 避難所都是不一樣的，希望能有一個統一整理的資料庫，讓之後離線防災資料庫可以納入

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