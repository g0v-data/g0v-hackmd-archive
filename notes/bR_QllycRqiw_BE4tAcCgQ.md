---
title: "內政部及財政部國有財產署經管公有土地資料"
tags: 公有地,hackpad
---

# 內政部及財政部國有財產署經管公有土地資料

> [點此觀看原始內容](https://g0v.hackpad.tw/BYjLYyPI0ya)


資料網址： [http://data.moi.gov.tw/MoiOD/Data/DataDetail.aspx?oid=7EFCAF0A-F102-4E85-9B79-6B4F4A70B0A7](http://data.moi.gov.tw/MoiOD/Data/DataDetail.aspx?oid=7EFCAF0A-F102-4E85-9B79-6B4F4A70B0A7)
專案： [https://kiang.github.io/pub_lands/](https://kiang.github.io/pub_lands/)

問題蒐集：
- 在開放資料平台上的資料集名稱，會讓人誤以為這包含全部的公有地資料，應該要寫明是內政部與國有財產署管理公有土地
- XML 資料使用 big5 編碼，鄉鎮市區沒有代號可以配對，轉換編碼後使用文字比對會有部份錯誤
    - 嘉義市的鄉鎮市區欄位一樣填嘉義市，新竹市一樣情況
    - 屏東縣鹽埔鄉的鹽使用了罕見字無法順利轉換
    - 台與臺的混用
- 如果 XML 的資料無法併入 KML 顯示，也許可以考慮在 KML 的 ExtendedData 加入段號對應的段名等資訊，方便在資料配對時進行驗證
- 2515 筆 KML 資料找不到對應的 XML meta data ，清單： [https://gist.github.com/kiang/97a0a7eec14402a8d5ae842e7cb73d50](https://gist.github.com/kiang/97a0a7eec14402a8d5ae842e7cb73d50)
-

