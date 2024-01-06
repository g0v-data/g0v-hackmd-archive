# 違章工廠回報系統第82次小聚
###### tags: `Disfactory` `違章工廠` `違章工廠舉報系統`

時間：20210623
地點：線上
線上：https://gather.town/app/4KcewWQLKPx6YPlV/Disfactory

## 參與者簽到：

線上：
- deeper
- 鉦寰
- ael
- yukai
- caleb
- swind
- chewei
- yenchia
- yeefun


## 近期update
- 空拍圖比對計畫
    - [計畫整體樣貌](https://g0v.hackmd.io/@yukaii/Disfactory/%2F5QH2TlaXQR21wMo3UIKZug) 
    - [wireframe](https://www.figma.com/proto/TVAEC28E3ojabGHc8BawbI/%E8%A1%9B%E6%98%9F%E7%A9%BA%E7%85%A7%E5%9C%96?node-id=50%3A2&scaling=min-zoom&page-id=0%3A2)
    
| 月份 | 回報件數 |
| --- | ---- |
|2020.11|24|
|12|46|
|2021.1|49|
|2|55|
|3|53|
|4|110|
|5| 65|
|6|99|


## 待討論
- 空拍圖比對
    - db & api @yeefun
    - 圖資
        - spot API @littlewhiteYA
        - 2021國土測繪圖資GIS競賽 @chewei
        - 3D資料 @chewei
    - [spec](https://github.com/Disfactory/satellite/issues/2#issuecomment-866704442) @deeper
- 本週六大松目標
- 維運
    - 前端
        - cluster @caleb
            - 解決效能問題
        - i18n
            - .
        - 地號辨識 @yukai
            - 問Ronny之後一起決定
    - 後端
        - 經濟部資料 @swind
    - 權限
        - 切出志工使用django的權限遭遇困難 @deeper
- 零時小學校合作
    - 對象：高中生
    - task：
        - 拍一個10-15分鐘的教學影片
        - 出一個20分鐘內可以完成的作業
    - 時程
        - 7/8前deeper寫腳本
        - 7/15完成拍攝
        - 7/21交出初版
        - 7/28交出成品

## 會議記錄
### 空拍圖
- db & api
    - user
        - 正確率的使用方式
            - 該ID正確率如果低於75%，就所有回答過的題組都不要記到資料庫
            - 如果中間低於75%，直到提升到正確率75%之前都不記到資料庫
    - factory
    - 要等設計完全確定，table才能確定
        - 首要要確認的：能否要到地號的形狀？
            - 問問看Ronny
        - 才能決定只要比對一張圖還是兩張圖？
    - 正確答案
        - 先不管，全存
        - 但要確保每個人都有回答到
- 圖資
    - 3D資料
        - maybe可以拿2018年建築框框，來比對
        - 資料來源
            - 衛星
            - 測繪
### 大松
- 任務
    - 問Ronny
    - 測試prototype
### 維運
- 後端
    - easymap
        - 可上production了
    - 經濟部
        - 缺時間
        - 
### 零時小學校
- 影片到時要請大家協助
- 作業教學
    - 前面qgis會教的
        - 匯入shp file到qgis
    - user新增的座標csv
        - 讓他們輸出放上googlemymap、qgis、或是biggis
        - 點開離你家的違章工廠
## 待辦&待討論事項
- 累積待討論
    - [地號辨識 issue 96](https://github.com/Disfactory/frontend/issues/96)
- 累積待辦事項
    - GA
    - 找人聊空拍圖比對
        - 中央大學
        - [臺灣大學朱子豪教授及張家豪組長](http://ncusec.ncu.edu.tw/news/press_content.php?P_ID=31036)
    - jiahe建議
        - GA/GTM排除坑友的數據
        - 線下活動宣傳的配合（含QRcode的實體和電子flyer用於流傳）實體 flyer++ 分類廣告？
            - peii負責
        - 怎麼做 LINE 行銷
    - 寄東西給未曾謀面的捧油
    - 開好真的spec
    - 都市計畫區可以改成填一個google表單
    - 問SPOT來源能否提供更細的倍率 @deeper
