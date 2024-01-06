# 違章工廠回報系統第83次小聚
###### tags: `Disfactory` `違章工廠` `違章工廠舉報系統`

時間：20210630
地點：線上
線上：https://gather.town/app/4KcewWQLKPx6YPlV/Disfactory

## 參與者簽到：

線上：
- deeper
- eric
- tin
- lydia
- stasia
- aaron
- yukai
- littlewhiteYA

## 近期update
- 空拍圖比對計畫
    - [計畫整體樣貌](https://g0v.hackmd.io/@yukaii/Disfactory/%2F5QH2TlaXQR21wMo3UIKZug) 
    - [spec](https://github.com/Disfactory/satellite/issues/2#issuecomment-866704442)
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
|6|109|


## 待討論
- 空拍圖比對
    - 比對邏輯決定 [討論用簡報](https://docs.google.com/presentation/d/1hyak0PdXA3CpxSC82T7ahmp0AbqjEJS2c3AcnhURpnw/edit?usp=sharing)
    - db & api @littlewhiteYA
    - 圖資
- 維運
    - 前端
        - cluster、i18n @caleb
        - 地號辨識 @yukai
    - 後端
        - 新issue
            - filter
            - 中高污染資料匯入（可晚點處理）
- 零時小學校合作
    - deeper寫的[企劃](https://www.notion.so/agrifactory/_gis_disfactory-27ee8b87e9e94e85bef7a0832bb8471c)

## 會議記錄
### 空拍圖
- db & api
    - 比對邏輯 -> 設計 -> table
        - 已經確定能要到地號的形狀，那到底要比對一張圖還是兩張圖？
    - 存 vs 外接api
        - 接api好處
            - +marker較簡單
        - 存好處
            - 速度較快
        - +marker之後再討論，先做出一個mockup來做使用者測試，看看是否必要
    - 一張圖還是兩張圖
        - 兩張圖
            - 好處：更明顯，不怕光線、其他難以辨識的情況
            - 壞處：怕一直看到新圖，疲勞時會被混淆、可能速度稍慢一些
            - 決定
                - 現狀：免費又不花力氣的狀況下，舊圖會清晰，新圖才清晰，最好還是兩張對照
        - 設計下一步
            - 強迫看教學
            - quit增加門檻
            - 有瀏覽紀錄者+跳過按鈕
            - 兩張圖
            - 教學時可以教，新圖一定有建物，請分辨舊圖是否有建物
### 維運
- 地號辨識
    - [更新](https://github.com/Disfactory/frontend/issues/96#issuecomment-871349791)
        - 另一個方法可以從 Ronny 的 API 拿到地段範圍，並繪製於目前座標的圖層上
            - 從 Easymap 拿到地段
            - 從 https://twland.ronny.tw/ 拿到圖資
            - 繪製到地圖上
            - 不過 1. 的 easymap 現在在後端是 async job，是否要開個 API、是否會增加後端負擔、速度表現，可能都需要再想

### 零時小學校
- 作業教學
    - 把工廠分佈位置的csv放上googlemymap，並找出離自己最近的一間工廠
    - 截圖
    - 計算它的面積，並以籃球場（420m^2^）當比例尺，計算他是幾個籃球場大
    - 在地圖上找出離這間工廠最近的消防隊，並計算他們之間直線距離
    - 回到disfactory，找出那間工廠現在的狀態，並補充照片期狀況描述
        - 有無照片？
        - 查處狀態如何？
- 介紹影片
    - 文稿 -> 設想畫面 -> 完整腳本
    - 給一段文字就能再切分成必要的畫面
        - 150字/分鐘
    - 素材
## 待辦&待討論事項
- 本次
    - tin畫prototype
    - deeper提供stasia motion graphic素材
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