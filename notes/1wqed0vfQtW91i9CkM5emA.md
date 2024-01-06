# 違章工廠回報系統第79次小聚

###### tags: `Disfactory` `違章工廠` `違章工廠舉報系統`

時間：20210602
地點：線上
線上：https://gather.town/app/4KcewWQLKPx6YPlV/Disfactory

## 參與者簽到：

線上：

- 鉦寰
- yukai
- chewei
- SL
- swind
- yeefun
- ael
- deeper
- carmen


## 近期update
- 空拍圖比對計畫 [wireframe](https://www.figma.com/proto/TVAEC28E3ojabGHc8BawbI/%E8%A1%9B%E6%98%9F%E7%A9%BA%E7%85%A7%E5%9C%96?node-id=50%3A2&scaling=min-zoom&page-id=0%3A2) by tin

NHK 的 Disfactory 報導備份
https://www.dailymotion.com/video/x81ne3e

## 待討論
- gps比對
    - 新spec
    - 是否需要landing page
    - 行有餘力：拉期程
- 最近進展詢問
    - 前端
        - 地號圖層？
        - inernationalization
    - 後端
        - 經濟部資料匯入
        - factory status
    - 權限
        - 發展SOP讓志工幫忙審查、回覆案件
        - 切出志工使用django的權限 @deeper

## 會議記錄

- 感謝IU打好imgur
- [NHK國際新聞](https://www.dailymotion.com/video/x81ne3e?fbclid=IwAR1uLSJIpmhoFQwBvD63MpxM7bvuOF9remy9_2_NagjthKmk6bUrZX7avjo)已播出
- https://www.zooniverse.org/

### 空拍圖比對rough spec

> [name=ael] 之後寫成具體的 spec 最好需要 success criteria，就是定義怎樣才算是那個部分有做完，還有具體的資料欄位和動作有哪些，以及可以試試看用 User Story/Job Story 定義功能，去定義該功能的目的。
> As a XX
> When.....
> I want to ......
> So that......
> 

> 我之前寫的格式最完整的應該是這個
> https://github.com/Disfactory/Disfactory/issues/312

> 但最真的有用的應該是這個單一功能的 spec 
> https://github.com/Disfactory/Disfactory/issues/183

#### 圖資db @littlewhiteYA
- [ ]  找到對的圖資
    - 圖資需要的標準？目前已知資料來源： Google Earth 、 福衛
    > [name=chewei] 初步看起來有兩份 圖資
    > 新的時間的圖資，我初步是覺得使用 mapbox 的衛星圖可以介接，部分地區比 google map 底圖 新一點圖長[這樣子](https://api.mapbox.com/styles/v1/chewei/ckmlzyszk0l4d17o2lqx52f06.html?fresh=true&title=copy&access_token=pk.eyJ1IjoiY2hld2VpIiwiYSI6ImNrbTU2c3V4aTBhb3Iyb3cwZTNkdjRleGEifQ.VuezEfOOKjJP3ndX_kvlWg)
    > mapbox studio 介接地圖的[管道](https://www.mapbox.com/mapbox-studio)
    > 而舊的時間點的圖資，若 2016 之前，這個好像要盤一下
    > (1) mapbox 會不會有舊圖資可接，待確定
    > (2) 可能要找國內公部門的成果（農航所為主）
    > 不用再另外花錢是landsat、Sentinel，但解析度會太低
- [ ]  抓下四個時間點的圖資（2016.5.20之後最舊的的兩個時間點，2021.6之前最新的兩個時間點） 
- [ ]  根據「政府盤查」的經緯度，切出適當大小、遠近的地圖圖卡

#### 收資料&分析機制
- [ ] 設計結果檢核機制
    - 如何確定資料品質？如何標注該筆資料品質？
    - 多數決 vs 測驗資料
- [ ] 設計紀錄存回db的方式：有哪些欄位
    - [ ] 資料庫設計 db和api可以一起做
        - 需要有更完整的scenario @deeper @swind @SL
        - 優先欄位 
            - 縣市
            - 是否為新增
            - 已經比對次數
        - api研究 @yeefun
- [ ] GTM 追蹤，或是其他要埋追蹤碼的？
- [ ] 設計顯示在 disfactory map 的方式
    priority 後面

#### 操作教學
As a new user
When
I want to know how to play this game
So that I could finish the task
- [ ] 文案介紹
- [ ] 讓使用者按過比對畫面所有按鈕

#### 比對
- [ ] 顯示 before & after 地點空照圖
- [ ] 更換圖片按鈕
- [ ] 是、否、不確定按鈕
- [ ] 「回到教學」按鈕
> [name=ael] 不用指定按鈕沒有關係，但也許可以定義清楚在比對這個環節你想要讓使用者完成的事情是什麼
#### 結束畫面
- [ ] 再玩一次按鈕
- [ ] 參加抽獎按鈕
- [ ] 分享按鈕

### 最近進展詢問

- 前端
    - internationalization @caleb
    - yukai上上禮拜幫忙弄了污染圖資，或許可以變成適合放上圖台的一個圖層？
    - i18n Discussion: https://github.com/Disfactory/frontend/issues/83#issuecomment-853010168
    - Cluster: https://github.com/Disfactory/frontend/issues/73#issuecomment-853003907
- 後端
    - 經濟部資料匯入 @swind
    - factory status @littlewhiteYA
- 權限
    - 發展SOP讓志工幫忙審查、回覆案件
    - 切出志工使用django的權限 @deeper
## 下次待討論事項

- 本次待辦事項
    - 開好真的spec
    - 都市計畫區可以改成填一個google表單
    - deeper約api、db格式討論
    - deeper詢問授權事宜
    - littlewhiteYA負責google API
    - yeefun負責db、api製作
- 累積待討論
    - 地號辨識
- 累積待辦事項
    - GA
    - 找人聊空拍圖比對
        - chewei V
        - 高英勛 V
        - 中央大學
        - [臺灣大學朱子豪教授及張家豪組長](http://ncusec.ncu.edu.tw/news/press_content.php?P_ID=31036)
    - jiahe建議
        - GA/GTM排除坑友的數據
        - 線下活動宣傳的配合（含QRcode的實體和電子flyer用於流傳）實體 flyer++ 分類廣告？
            - peii負責
        - 怎麼做 LINE 行銷
    - 寄東西給未曾謀面的捧油