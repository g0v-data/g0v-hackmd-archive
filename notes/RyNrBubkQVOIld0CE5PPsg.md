---
tags: GIS
---

# 取得施工許可太陽光電案場

經濟部能源署有開放 [取得電業設置發電設備工作許可證太陽光電案場土地地號](https://www.moeaea.gov.tw/ECW/populace/content/SubMenu.aspx?menu_id=23059) 資料，~~不過是以 pdf 格式~~，在提出請求後已經釋出 Excel/ODS 格式，希望能夠整理成乾淨可用的圖資。

應用：
1. [太陽光電設施地圖](https://tainan.olc.tw/p/solar/)

目前狀態：
1. 發現 DoEnergy 已經有完整資料，去信詢問能否釋出(2025/01/03 仍未收到回應) - https://public.tableau.com/app/profile/doenergy/viz/1121001ver_17037355960920/2
2. [在 data.gov.tw 提出請求](https://data.gov.tw/suggests/136911)
3. 透過政府網站把地號清冊轉換為[座標資料點](https://github.com/kiang/moeaea.gov.tw/blob/master/processed/solar_points.csv)，初步呈現成果 [太陽光電設施地圖](https://tainan.olc.tw/p/solar/)
4. 也有透過 Ronny 的[地號查詢](https://twland.ronny.tw/)網站產出 [geojson 格式的圖資](https://github.com/kiang/moeaea.gov.tw/tree/master/processed/solar)，但因為資料比較舊，缺少的資料很多
5. 後來發現可以取得[漁電共生網站](https://www.sfea.org.tw/)的資料，搭配上述點位有產出一批漁電共生圖資放進設施地圖中

想要探討的問題（發想）：
1. 個別光電場有對應的承諾事項，只是資訊並未公開，比較直觀的大概就是確認一些名義叫農電共生、漁電共生的場址，現場是否常態存在農作物、養殖行為
2. 光電場建置過程常常帶有其他爭議作法，像是小二甲將光電場化整為零簡化申請、光電場填平過程埋入事業廢棄物、使用清水以外方式清潔，這些行為都會影響到鄰近區域其他農漁民，進而讓更多可耕作、可養殖土地被迫無法農作而轉為新的光電場
3. 有些光電場被撤銷執照後許多設置長期閒置在那裡，可以試著蒐集未在清冊中但看起來像是光電場的場址，避免閒置的場址隨著時間累積造成危害

資料說明：
1. [光電設施點位](https://kiang.github.io/moeaea.gov.tw/solar_points.csv) ，包含欄位 uuid,申請年度,項次,業者名稱,電廠名稱,施工取得日期,土地面積,裝置容量,縣市,鄉鎮區,地段,地號,Longitude,Latitude
2. [漁電共生區塊](https://kiang.github.io/www.sfea.org.tw/json/fishfarms.json) ，除上述欄位外併入來自 SFEA 的資料，範例：
```javascript=
"properties": {
    "fishfarm_id": 104304,
    "fishfarm_type": "先行區",
    "fishfarm_sid": "0",
    "fishfarm_dataid": "83C64647D79F5824CEE835C2B35FF55A",
    "fishfarm_county": "臺南市",
    "fishfarm_town": "學甲區",
    "fishfarm_daun": "學甲寮段",
    "fishfarm_parcel": "283-293",
    "fishfarm_name": "109",
    "fishfarm_area": null,
    "fishfarm_issue": " ",
    "fishfarm_remark": " ",
    "fishfarm_date_announce": null,
    "fishfarm_date_version": null,
    "fishfarm_center": "{\"lon\":120.224995,\"lat\":23.241658}",
    "fishfarm_geoarea": "3677.6968653202",
    "fishfarm_content": null,
    "solar_uuid": "c010fe70-7af6-48c9-a4d1-7e8bc038a961",
    "solar_year": "109",
    "solar_index": "12",
    "solar_company": "心忠電業股份有限公司",
    "solar_name": "心忠學甲第一型太陽電廠",
    "solar_date": "2020-06-15",
    "solar_area": "709796",
    "solar_capacity": "75969.6",
    "solar_county": "臺南市",
    "solar_town": "學甲區",
    "solar_section": "學甲寮段",
    "solar_parcel": "283-293",
    "solar_lon": "120.2249555878",
    "solar_lat": "23.241559746873"
}
```

其他已知政府端應用：
* [太陽光電案場資訊揭露](https://public.revo.org.tw/GraphicWeb)
* [漁電共生環社檢核](https://www.sfea.org.tw/SfeaMap/)