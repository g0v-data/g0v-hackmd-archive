---
title: 違章工廠舉報系統小聚 20200422
tags: Disfactory, 違章工廠, 違章工廠舉報系統
---

# 違章工廠舉報系統小聚 20200422

時間：20200422
地點：經濟民主連合辦公室
線上：https://zoom.us/j/7204449797

## 參與者簽到：
- yellowsoar
- oriyar
- yukai
- aaron
- ael
- cph
- sL
- J
- Looofy
- deeper

## 待討論

### 後台

- DB backup => 去 #general 要一個 Python 後端？
- cet_report_status
- ProcessRecord
- AdminPage 權限管理
- soft-delete

### 行銷與推廣

- about.disfactory.tw -> 加上 dashboard #前端
- Metric、GA、utm
- 推廣計畫與收集回饋 #地公 #設計
- 使用者問題回報 form #設計 #PM


### 前端
- [x] 座標
- [ ] imgur & exif =>
- [ ] 表單重構


### Retrospective meeting

5/6 可以嗎？


### 設計 2.0
- workflow
- sitemap

目標 5/20 可以有些東西先改。


## 會議記錄

- 5/6 retrospective meeting 回饋合作過程
- 後端
    - @yellowsoar 正在研究 DB -> spreadsheet at admin page
    - @IU 在 parse 立委、選區對照，在思考要不要做通用的
    - @cph
        - 去 #general 招募後端工程師，需要支援 Django template 和一些前端 customization。要給需求技能。
        - reportrecord 和 image 都要可以 dump csv
        - cet_report_status
        - ProcessRecord
        - Imgur API
        - admin page 權限管理
        - soft-delete
- 前端：
    - 向量圖磚
    - imgur 在等 API
    - about.disfactory.tw 可以用 VuePress，地公需要寫 Markdown。但還沒下結論。另一個選擇是 wordpress。
    - 表單重構 @yukai
    - 座標點點放大倍率不夠時選取困難 @yukai
- 設計：
    - 已經在 Figma 上做了 workflow 和分層，以及初步 wireframe
    - 週四早上九點了解地公處理流程，整理後臺流程之後再改善使用者介面
    - 分享介面訓練錄影檔給設計師
- 產品、行銷
    - Metric @deeper
    - GA & campaign 成效 @deeper
    - 使用者回報 bug Google 表單 @ael




## 下次待討論事項
Dashboard 和 about.disfactory.tw
retrospective meeting


## 後端人員需求文件

【徵人】Python 後端工程師
#disfactory 是個可以讓民眾回報農地上違章工廠的網站，上線已經收到 80 幾件回報，目前正在建置後台，給地球公民基金會進行後續向政府舉報，針對高污染與違法的工廠，即報即拆或斷水斷電。目前後端急需幫手，想邀請有興趣的人一起加入！（全台至少五萬多家違章工廠）

TechStack
- Web Server: Django 
- Database: PostgreSQL + PostGIS
- Async Framework: Django-Q with Database as Broker
- Image hosting: Imgur
- Deployment: Caddy + gunicorn

專案狀態:
- API 實做完成，且有 > 90% 的測試涵蓋率
- 基本的後台可供 NGO 管理員瀏覽資料
- 架設在 Digital Ocean 上
- 上線一個月，已經有 81 件工廠回報， 近 200 張照片上傳

希望新加入的人可以協助以下事項:
- 後台需要更多功能以支援 NGO 的舉報作業流程，可能需要一點 Django template 及簡單的前端技能
- 後台需要對不同的管理員有不同的權限控管
- 隨著用量變大，可能會需要增加一些 API Endpoint 來取得統計數據
- 資料庫備份需要有更完善的機制
- 程式碼重構

專案介紹：
https://about.disfactory.tw
專案網站：
https://disfactory.tw
GitHub:
https://github.com/Disfactory/Disfactory
