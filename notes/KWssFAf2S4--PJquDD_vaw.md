2018中選會資料
===
行政區、選區資料
* 直轄市長 => http://2018.cec.gov.tw/json/DistrictId/20182010001.json
* 直轄市議員 => http://2018.cec.gov.tw/json/DistrictId/20182020001.json
* 直轄市山地原住民區長 => http://2018.cec.gov.tw/json/DistrictId/20184030001.json
* 直轄市山地原住民區代表 => http://2018.cec.gov.tw/json/DistrictId/20184040001.json
* 縣(市)長 => http://2018.cec.gov.tw/json/DistrictId/20183010001.json
* 縣(市)議員 => http://2018.cec.gov.tw/json/DistrictId/20183020001.json
* 鄉鎮市長 => http://2018.cec.gov.tw/json/DistrictId/20184010001.json
* 鄉鎮市民代表 => http://2018.cec.gov.tw/json/DistrictId/20184020001.json
* 村里長 => http://2018.cec.gov.tw/json/DistrictId/20185010001.json

候選人資料
* 臺北市 => http://2018.cec.gov.tw/json/candidate/63000.json
* 新北市 => http://2018.cec.gov.tw/json/candidate/65000.json
* 桃園市 => http://2018.cec.gov.tw/json/candidate/68000.json
* 臺中市 => http://2018.cec.gov.tw/json/candidate/66000.json
* 臺南市 => http://2018.cec.gov.tw/json/candidate/67000.json
* 高雄市 => http://2018.cec.gov.tw/json/candidate/64000.json
* 新竹縣 => http://2018.cec.gov.tw/json/candidate/10004.json
* 苗栗縣 => http://2018.cec.gov.tw/json/candidate/10005.json
* 彰化縣 => http://2018.cec.gov.tw/json/candidate/10007.json
* 南投縣 => http://2018.cec.gov.tw/json/candidate/10008.json
* 雲林縣 => http://2018.cec.gov.tw/json/candidate/10009.json
* 嘉義縣 => http://2018.cec.gov.tw/json/candidate/10010.json
* 屏東縣 => http://2018.cec.gov.tw/json/candidate/10013.json
* 宜蘭縣 => http://2018.cec.gov.tw/json/candidate/10002.json
* 花蓮縣 => http://2018.cec.gov.tw/json/candidate/10015.json
* 臺東縣 => http://2018.cec.gov.tw/json/candidate/10014.json
* 澎湖縣 => http://2018.cec.gov.tw/json/candidate/10016.json
* 金門縣 => http://2018.cec.gov.tw/json/candidate/09020.json
* 連江縣 => http://2018.cec.gov.tw/json/candidate/09007.json
* 基隆市 => http://2018.cec.gov.tw/json/candidate/10017.json
* 新竹市 => http://2018.cec.gov.tw/json/candidate/10018.json
* 嘉義市 => http://2018.cec.gov.tw/json/candidate/10020.json

投開票所
* 臺北市 => http://2018.cec.gov.tw/json/VoterPollingStation/63000.json
* 新北市 => http://2018.cec.gov.tw/json/VoterPollingStation/65000.json
* 桃園市 => http://2018.cec.gov.tw/json/VoterPollingStation/68000.json
* 臺中市 => http://2018.cec.gov.tw/json/VoterPollingStation/66000.json
* 臺南市 => http://2018.cec.gov.tw/json/VoterPollingStation/67000.json
* 高雄市 => http://2018.cec.gov.tw/json/VoterPollingStation/64000.json
* 新竹縣 => http://2018.cec.gov.tw/json/VoterPollingStation/10004.json
* 苗栗縣 => http://2018.cec.gov.tw/json/VoterPollingStation/10005.json
* 彰化縣 => http://2018.cec.gov.tw/json/VoterPollingStation/10007.json
* 南投縣 => http://2018.cec.gov.tw/json/VoterPollingStation/10008.json
* 雲林縣 => http://2018.cec.gov.tw/json/VoterPollingStation/10009.json
* 嘉義縣 => http://2018.cec.gov.tw/json/VoterPollingStation/10010.json
* 屏東縣 => http://2018.cec.gov.tw/json/VoterPollingStation/10013.json
* 宜蘭縣 => http://2018.cec.gov.tw/json/VoterPollingStation/10002.json
* 花蓮縣 => http://2018.cec.gov.tw/json/VoterPollingStation/10015.json
* 臺東縣 => http://2018.cec.gov.tw/json/VoterPollingStation/10014.json
* 澎湖縣 => http://2018.cec.gov.tw/json/VoterPollingStation/10016.json
* 金門縣 => http://2018.cec.gov.tw/json/VoterPollingStation/09020.json
* 連江縣 => http://2018.cec.gov.tw/json/VoterPollingStation/09007.json
* 基隆市 => http://2018.cec.gov.tw/json/VoterPollingStation/10017.json
* 新竹市 => http://2018.cec.gov.tw/json/VoterPollingStation/10018.json
* 嘉義市 => http://2018.cec.gov.tw/json/VoterPollingStation/10020.json

注意事項：
* 候選人資料使用時需要注意， ElectionId = 20182010001 才是正確的資料，不確定為什麼裡面會有另外一個 ElectionId = 20182010002 的重複資料，而且資料看起來是有問題的
* 部份 json 檔案有 BOM (Byte Order Mark)，會造成部份程式解讀錯誤
* 有的欄位名稱並不一致，像是 voterTypeId 被打成 votesrTypeId
* 圖檔有時是 URI, 有時是 base64 encoded
* 資料並不完整，像是政見欄位闕漏嚴重，可以參考報表 - https://github.com/kiang/2018.cec.gov.tw/blob/master/reports/02_count.csv
* 政見欄位看起來放棄治療了，已經全部被清空（攤手）

選區對應表 - http://data.cec.gov.tw/107%E5%B9%B4%E5%9C%B0%E6%96%B9%E5%85%AC%E8%81%B7%E4%BA%BA%E5%93%A1%E9%81%B8%E8%88%89%E5%8D%80/
備份 - https://github.com/kiang/2018.cec.gov.tw

使用範例 - https://github.com/kiang/2018.cec.gov.tw/tree/master/reports

這個範例是搜尋所有候選人的政見，去找出特定關鍵字，然後產出報表，藉此展示資料之間的連結

因為還沒有太多時間整理，所以先製作這份摘要，歡迎接手 ( welcome fork )

已經匯入資料網站：
* http://2018.cec.gov.tw/
* http://elections.olc.tw/