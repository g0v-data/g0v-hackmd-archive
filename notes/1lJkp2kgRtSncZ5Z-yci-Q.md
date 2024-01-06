# 違章工廠回報系統第81次小聚
###### tags: `Disfactory` `違章工廠` `違章工廠舉報系統`

時間：20210616
地點：線上
線上：https://gather.town/app/4KcewWQLKPx6YPlV/Disfactory

## 參與者簽到：

線上：
- deeper
- swind
- ael
- caleb
- tin
- alan
- peii
- chewei
- lydia
- littlewhiteYA
- carmen
- yukai
- oriyar


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
|6|84|


## 待討論
- 空拍圖比對
    - spot API @littlewhiteYA
    - db & api @yeefun 下次
    - 發想
    - spec @deeper
- 維運
    - 前端
        - 幫助deeper看懂優先issueXD
    - 後端
        - easymap問題 @swind
        - 經濟部資料 @swind
        - factory status @littlewhiteYA
- 零時小學校合作
    - 對象：高中生
    - task：
        - 拍一個10-15分鐘的教學影片
        - 出一個20分鐘內可以完成的作業
    - 時程：七月前

## 會議記錄
### 空拍圖
- spot
    - 放大倍率現在不符合預期
    - 現在只能到17倍
    - openlayer可以加marker
    - 下一步
        - 改善地點誤差
        - 加個marker
        - 問來源能否提供更細的倍率 @deeper
- mapbox
    - 可以放到19倍
    - 
    - 或許可以用spot 2020取代
- 重新思考直接接api的方式
    - 有不能zoom in、zoom out的layer
    - 
### 維運
- security已升級
- easymap 已修改好
- factory status也好了
- 可以用地號搜尋了

### 零時小學校
- g0v揪松團希望把開源軟體介紹到校園
- ex: cofacts、wikipedia
- gis資料ronny和chewei有去教過
- 現在希望要線上化
- 比較介紹說：用googlemymap可以做成什麼地圖
- 各個專案如果可以的話，可以錄一個10-15分鐘的影片，介紹一個圖台上面的操作過程、任務的操作
- 出個作業給高中生20分鐘完成，他們因此可以取得時數
- 七月開始之後，給人報名
- 七月中前完成
- 整體disfactory是在新手村之後，地理資料課程的中段
- 衛星
- 涉及到UI、群眾協作，特別是這個專案可以凸顯給高中生的

## 下次待討論事項
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
