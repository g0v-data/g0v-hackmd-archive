# 取得施工許可太陽光電案場

經濟部能源署有開放 [取得電業設置發電設備工作許可證太陽光電案場土地地號](https://www.moeaea.gov.tw/ECW/populace/content/SubMenu.aspx?menu_id=23059) 資料，不過是以 pdf 格式，希望能夠整理成乾淨可用的圖資。

目前狀態：
1. 運用 tabula 轉換成文字格式 - https://github.com/kiang/moeaea.gov.tw/tree/master/raw/solar_tabula_csv
    * 因為原始資料大量使用合併儲存格，所以每一頁的第一行如果沒有上方框線就會被程式跳過，導致需要人工進行調整
    * 
2. 發現 DoEnergy 已經有完整資料，去信詢問能否釋出 - https://public.tableau.com/app/profile/doenergy/viz/1121001ver_17037355960920/2