---
title: 違章工廠舉報系統第四次小聚
tags: Disfactory, 違章工廠, 違章工廠舉報系統
---

# 違章工廠舉報系統第四次小聚

時間：20190918
地點：地球公民基金會北辦
線上：https://zoomtw.zoom.us/j/362938896

參與者簽到：
- ael
- 星翰
- Hubert
- Yukai
- 小海
- 小胖
- IU
- Simon


## 待討論

- 專案名稱
    - factory-index
    - Pollutory
    - faketory:heart: :heart:🌹
    - Disfactory   :heart: :heart: :heart:  🍎  :heart:  :heart: :heart:✔
        - > (還可以模仿 Discovery logo :laughing:)
    - geofactory 
    - cet-pickout 
- 技術分工 >> 之前 IU 寫的[開發需求](https://hackmd.io/ockOrC1VRfWyOwV8fvMF2w?view)
- wireframe >> [wireframe 2.0](https://www.dropbox.com/s/xlnllqrkljcqui9/%E9%81%95%E7%AB%A0%E5%BB%BA%E7%AF%89%E7%B6%B2%E9%A0%81%E8%A8%AD%E8%A8%88%EF%BC%88%E6%89%8B%E6%A9%9F%E7%89%88%EF%BC%89_%E7%AD%86%E8%A8%98.pdf?dl=0)
- [wireframe 3.0](https://www.dropbox.com/s/3pvteloaaw97cn6/%E9%81%95%E7%AB%A0%E5%BB%BA%E7%AF%89%E7%B6%B2%E9%A0%81%E8%A8%AD%E8%A8%88%EF%BC%88%E6%89%8B%E6%A9%9F%E7%89%88%EF%BC%89.pdf?dl=0) 
 
## 會議記錄

### 要有帳號登入嗎？
- 第一版先不做，保留未來擴充登入系統
- 第一版採用可選填手機號碼、email，直接填在表單


還缺使用後臺 wireframe、送公文

### 工廠分類

1. 金屬
2. 機械
    2-1 沖床、銑床、車床、鏜孔
    2-2 焊接、鑄造、熱處理
    2-3 金屬表面處理、噴漆
3. 塑膠加工、射出
4. 橡膠加工
5. 非金屬礦物（石材、瀝青）
6. 食品
7. 皮革
8. 紡織
9. 其他

### 確定專案名稱： Disfactory
https://github.com/yoyo930021/Disfactory
 

## 確定技術架構
後端：node.js or django?
需要有人可以負責規劃後端:
後端是 Python，負責人是 Simon

GitHub 資料夾：一個 server 一個 client

資料庫
PostgreSQL：有內建強大的地理查詢能力

## API

- 工廠資料
    - 使用者上傳
    - 國土舊有資料 (ronny wang 資料)
- 詳細參看[開發需求](https://hackmd.io/ockOrC1VRfWyOwV8fvMF2w?view)

## Features

- 顯示違章工廠地圖：圖層疊合
    - 農地圖層：國土測繪圖資服務雲的 API
    - GIS 座標處理
    - GPS 座標轉地段地號
        - 國土測繪圖資服務雲的 API
        - ronnywang 自己刻的 API
- 新增違章工廠
    - GPS 定位轉成地號
    - 表單填字
    - 圖片上傳（multiple）
- 地球公民基金會編輯後台：
    - 送件狀態
    - 公文上傳（要用圖檔還是 pdf 還是 url）
- 使用須知、關於（最後做）

### wireframe 補齊

1. 電腦頁面版本：大概，不需要重新畫流程
2. 手機頁面
3. 後台（可以再下一次）

### 補開 spec 去確認規格

最小：經緯度＋照片



### 開發 milestone

1. 需要問有經驗的 python 的人幫忙嗎？（實體會議）可以估算時間。
2. 小海和小胖需要想最低限度
3. Frontend 估一下時間
4. 去開 Slack
5. 約下次會議時間（週一晚上）


2 week/10 week
1. ==now== 建立蒐集資料系統

backend
- 開資料庫結構
- 專案架構
    - Django 產生專案
- 研究與撰寫座標轉地號
    - ronny wang
        - http://twland.ronny.tw/
        - [地號轉地圖 Land No. Mapper](https://g0v.hackmd.io/uFhBRHrnR-yvvFD4ZEn3XA)
    - [國土地段轉地號](https://maps.nlsc.gov.tw)
- 研究 postgresql GIS 地理查詢系統
- 五個 API
    - ==1== 得到中心座標往外指定範圍的已有工廠資料
    - ==2== 新增編輯指定 id 的工廠欄位資料
    - ==3== 上傳指定 id 的工廠圖片
    - ==4== 上傳圖片
    - ==5== 新增工廠

frontend
- 專案架構
- 研究 openlayers
- 地圖 弄出反向農地圖層
- 地圖 顯示所有工廠的座標們
- 查看工廠資料
- 修改工廠資料
- 新增工廠資料


12/01 alpha 完版

2. 匯入已知的違章工廠資料


3. 提供給地球公民基金會使用的後臺(12/31)
4. 背後轉換成公文
5. 串接 Bot 做到完全匿名


## 下次待討論事項
1. j


電腦主畫面設計（Sandra）