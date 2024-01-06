---
title: "鄉民風水師 0.1.0 for Android"
tags: 地圖化,鄉民風水師,hackpad
---

# 鄉民風水師 0.1.0 for Android

> [點此觀看原始內容](https://g0v.hackpad.tw/0zZtHOsh7DJ)


## 平台

- Android (Google Play)
    - 載點：[https://play.google.com/store/apps/details?id=](https://play.google.com/store/apps/details?id=tacoball.com.geomancer)[**tacoball.com.geomancer**](https://play.google.com/store/apps/details?id=tacoball.com.geomancer)
    - GitHub：[https://github.com/OsmHackTW/Geomancer](https://github.com/OsmHackTW/Geomancer)

## 資料來源

- [x] OpenStreetMap
- [x] 台灣道路標誌 SVG
- [x] 台灣凶宅網
- [x] 台北市政府勞工局
- [x] 新北市政府勞工局

## 要填的坑

- Google Play 上架內容 (等待好心人)
    - [ ] 高解析度圖示：512x512 PNG32
    - [ ] 主題圖片：1024x500 PNG24
    - [ ] APP 小圖：96x96 PNG32

    ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6ec26c5e3b8e5fa2fd40200a2f0d7512)

- 圖資問題 (用圖客的原力解決)
    - [x] 完成海陸分離 2016-01-13 搞定
    - [x] 基隆河、淡水河沿岸某些地方泡在水裡 (捨棄 waterbank 就搞定了!)
    - [x] 高鐵站無法識別營運單位
> 我已經統一加上operator=台灣高速鐵路股份有限公司和network=台灣高鐵
> [name=Supaplex]

> 感謝 S 大大，我會儘快更新圖資
> [name=Raymond W]

- 三星手機無法進主畫面問題
    - [x] g0v Hackthon 23th 用 [Audrey Tang](https://g0v.hackpad.tw/ep/profile/DaKXhWfoD7Q) 的手機測試，問題是三星手機不能寫入 mtime。
    - [ ] Bugfix

