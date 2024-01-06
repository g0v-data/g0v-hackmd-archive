---
title: 違章工廠舉報系統第 12 次小聚
tags: Disfactory, 違章工廠, 違章工廠舉報系統
---

# 違章工廠舉報系統第 12 次小聚

時間：20191106
地點：地球公民基金會北辦
線上：https://zoomtw.zoom.us
http://github.com/Disfactory/Disfactory

## 參與者簽到：
- simon 
- cph
- yukai
- 小海
- 小胖
- 星翰
- hubert
- IU
- Peace
- yellowsoar
- Andy
- 小班

## 待討論
- query http://34.80.197.40:8000/api/factories?lat=23.12&lng=121.5566&range=100
- test update http://34.80.197.40:8000/api/factories/82850aa4-9413-461f-b30e-ec8c0a3783c8

## 會議記錄
-
小海註冊了兩個Email信心
admin@disfactory.tw
hi@disfactory.tw

對進度（海海雖然聽不懂，但就是照打字喔）

前端
已完成：地圖弄出來了，圖層也弄得差不多了，確認會換新的圖層，
繼續中：刻原件，組起來
加舊有的舉報點，移到地圖上

yellowsoar
部署middle2，上線了，run server在跑，現在可以同時每秒處理50-100 request，目前在封測，等小海完成等domainname設cname..就可以blabla...
本來middle2有try，但ronny還在debug，所以等完整直接上去。

IU:之後第一個任務是把前端跟後端的CI弄起來

後端
5個API中，拿附近工廠的已經做好了。但新增（Andy）、更新屬性（修改工廠，simon)、上傳照片(星翰）、上傳特定照片（hubert）都分別處理。

1 GET /factories?lng={lng}&lat={lat}&range={km}
得到中心座標往外指定範圍的已有工廠資料

2 PUT /factories/{id}

3 POST /factories/{id}/images
上傳指定 id 的工廠圖片

4 POST /images
上傳圖片

5 POST /factories



## 下次待討論事項
- 後端開發環境安裝完了嗎？
- 前端：
    - 元件
    - 放置圖釘
- 後端：
    - table 串連: Andy
    - 圖片上傳: Hubert
    - 星翰：Create a Image referenced to the specific factory
    - Simon: Create a Image referenced to the specific factory
    - test_update_factory_attribute.py