# 取得施工許可太陽光電案場

經濟部能源署有開放 [取得電業設置發電設備工作許可證太陽光電案場土地地號](https://www.moeaea.gov.tw/ECW/populace/content/SubMenu.aspx?menu_id=23059) 資料，~~不過是以 pdf 格式~~，在提出請求後已經釋出 Excel/ODS 格式，希望能夠整理成乾淨可用的圖資。

應用：
1. [太陽光電設施地圖](https://tainan.olc.tw/p/solar/)

目前狀態：
1. 發現 DoEnergy 已經有完整資料，去信詢問能否釋出(2025/01/03 仍未收到回應) - https://public.tableau.com/app/profile/doenergy/viz/1121001ver_17037355960920/2
2. [在 data.gov.tw 提出請求](https://data.gov.tw/suggests/136911)
3. 透過政府網站把地號清冊轉換為[座標資料點](https://github.com/kiang/moeaea.gov.tw/blob/master/processed/solar_points.csv)，初步呈現成果 [太陽光電設施地圖](https://tainan.olc.tw/p/solar/)
4. 也有透過 Ronny 的[地號查詢](https://twland.ronny.tw/)網站產出 [geojson 格式的圖資](https://github.com/kiang/moeaea.gov.tw/tree/master/processed/solar)，但因為資料比較舊，缺少的資料很多

想要探討的問題（發想）：
1. 個別光電場有對應的承諾事項，只是資訊並未公開，比較直觀的大概就是確認一些名義叫農電共生、漁電共生的場址，現場是否常態存在農作物、養殖行為
2. 光電場建置過程常常帶有其他爭議作法，像是小二甲將光電場化整為零簡化申請、光電場填平過程埋入事業廢棄物、使用清水以外方式清潔，這些行為都會影響到鄰近區域其他農漁民，進而讓更多可耕作、可養殖土地被迫無法農作而轉為新的光電場
3. 有些光電場被撤銷執照後許多設置長期閒置在那裡，可以試著蒐集未在清冊中但看起來像是光電場的場址，避免閒置的場址隨著時間累積造成危害