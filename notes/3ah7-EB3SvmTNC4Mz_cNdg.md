---
title: 違章工廠舉報系統第六次小聚
tags: Disfactory, 違章工廠, 違章工廠舉報系統
---

# 違章工廠舉報系統第六次小聚

- [上一次會議記錄](https://g0v.hackmd.io/1w_44QhqTWKi2dcyzCitkA?both)

時間：20190923
地點：地球公民基金會北辦
線上：

## 參與者簽到：
- shupo
- 小海
- 星翰
- yukai
- hubert
- simon read [DRF](https://www.django-rest-framework.org/) 說明文件
- 柏憲

之前紀錄
- 技術分工 >> 之前 IU 寫的[開發需求](https://g0v.hackmd.io/FZFghtuoQ0aaGIl9xXzuKw?both)
- wireframe >> [wireframe 2.0](https://www.dropbox.com/s/xlnllqrkljcqui9/%E9%81%95%E7%AB%A0%E5%BB%BA%E7%AF%89%E7%B6%B2%E9%A0%81%E8%A8%AD%E8%A8%88%EF%BC%88%E6%89%8B%E6%A9%9F%E7%89%88%EF%BC%89_%E7%AD%86%E8%A8%98.pdf?dl=0)
- [wireframe 3.0](https://www.dropbox.com/s/3pvteloaaw97cn6/%E9%81%95%E7%AB%A0%E5%BB%BA%E7%AF%89%E7%B6%B2%E9%A0%81%E8%A8%AD%E8%A8%88%EF%BC%88%E6%89%8B%E6%A9%9F%E7%89%88%EF%BC%89.pdf?dl=0) 


## 待討論

- Backend 技術分工
    - server
    - DB
    - Backend 框架
    - 圖資 API
- 開發 milestones 粗估

## 會議記錄

每年預估 3000 件
每年最多 8000 件中高污染

要拉舉報的事件 Log，reference 到地號上
ID 記在地號上面
工廠


### Backend

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_b6eba6c8d06a92b8b3bc7b0fddecdc2a)
這是最基本要完成的部份。如果後續有時間再加：
- DB backup: 寫 cron job 或用個 master-slave （但不確定怎麼在 middle2 上設定）
- cron job 打 Imgur：因為半年沒 query 就會刪掉
- asynchronous task queue: 座標轉地號和圖片上傳都可以在背景做掉，減低 blocking time。不過會有 data inconsistency 的問題，處理起來有點複雜。
- DB caching: 由於不會很常增加新的違章工廠，加上總資料量其實很小，可以有寫個 write-through 機制的 cache
- Image backup and self-hosting


1. Document 討論結果 + 開基礎架構：柏憲
    2. Unitest, pipenv
3. DB 文件： Andy
4. Survey Imgur API: Hubert
5. Survey PostGIS: Hubert
> [name=Po-Hsien Chu] 不知道有沒有幫助，不過我找到一個[超級簡化的 GeoDjango 範例](https://github.com/realpython/materials)
> [name=Po-Hsien Chu] 啊，官網就有[教學](https://docs.djangoproject.com/en/2.2/ref/contrib/gis/tutorial)...
6. 地號 API: 星翰


### GIS 的部分

- 反轉圖層、搭配 openlayer 判斷可放置圖釘的位置

TGOS: 圖層資訊豐富
TGOS long/lat -> epsg.io 轉換 -> 打開 OSM

https://map.tgos.tw/TGOSCloud/Web/Map/TGOSViewer_Map.aspx?addr=台北市忠孝東路二段30號

**請用 EPSG:3857**
https://epsg.io/3857

小數點位數要正確

https://github.com/proj4js/proj4js

## 下次討論




