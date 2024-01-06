# 違章工廠回報系統第80次小聚

###### tags: `Disfactory` `違章工廠` `違章工廠舉報系統`

時間：20210609
地點：線上
線上：https://gather.town/app/4KcewWQLKPx6YPlV/Disfactory

## 參與者簽到：

線上：
- deeper
- yenchia
- chewei
- swind
- SL
- littlewhiteYA
- yeefun
- yukai

## 近期update
- 空拍圖比對計畫
    - [計畫樣貌](https://g0v.hackmd.io/@yukaii/Disfactory/%2F5QH2TlaXQR21wMo3UIKZug) 
        - 目的
        - 圖資來源討論
    - [wireframe](https://www.figma.com/proto/TVAEC28E3ojabGHc8BawbI/%E8%A1%9B%E6%98%9F%E7%A9%BA%E7%85%A7%E5%9C%96?node-id=50%3A2&scaling=min-zoom&page-id=0%3A2)
- 第11波檢舉寄出，檢舉數+38，現在是346家
    

| 月份 | 回報件數 |
| --- | ---- |
|2020.11|24|
|12|46|
|2021.1|49|
|2|55|
|3|53|
|4|110|
|5| 65|


## 待討論
- 空拍圖比對
    - db & api @deeper @SL @swind @yeefun
    - 圖資來源 @chewei @littlewhiteYA
- 維運
    - 前端
        - 幫助deeper看懂優先issueXD
    - 後端
        - 經濟部資料 @swind
        - factory status @littlewhitYA
    - 權限
        - 切出志工使用django的權限遭遇困難 @deeper

## 會議記錄
### 空拍圖
- 圖資
    - chewei survey成果在[空拍圖比對計畫](https://g0v.hackmd.io/@yukaii/Disfactory/%2F5QH2TlaXQR21wMo3UIKZug)
    - 確定為SPOT（2015、2017）、Mapbox（2020）
    - 小白ㄉ下一步
        - 研究spot API
- 流程需求盤點
    - [連結](https://docs.google.com/spreadsheets/d/1ejtowBcaAEW-fpX0ZObHgUAKZOshcqOvlU-0pYp8GPE/edit#gid=0)
- db & api
    - 資料應用方式
        - 前端需要
            - 給確定新增的一個明顯的顯示
            - 在disfactory map上顯示新增熱區
        - 使用者
            - 挑選特定縣市標注
        - 地公需要(或是任何非開發者)
            - 任何人都可以放上gis軟體做地理資訊分析
            - 確定的新增數字
    - DB table與欄位
        - 使用者
            - cookie session IS
            - 辨識工廠數
            - 正確率
        - 照片
            - 照片ID
            - 檔案名
            - 被辨識次數
            - 年份
            - 工廠ID
        - 答案
            - 答案
            - 與正確答案比對結果
            - 回答的使用者
            - 對應照片
            - timestamp
        - 工廠
            - 工廠編號
            - 經緯度/地號
            - 地點資料
            - 照片ID
            - 正確答案
    - 下一步
        - yeefun先開table
### 維運
- 前端
- 後端
    - easymap問題 @swind
    - 經濟部資料匯入 @swind
- 權限
    - 切出志工使用django的權限遭遇困難
### 零時小學校
- 帶高中班級學會一個g0v專案相關的專長
    - nice to cover：g0v新參者
- 一個pack是
    - 專案介紹 10-15min
        - 可介紹議題
        - 這個專案有多少不同的角色一起促成
    - 然後再出一個作業 （估20分鐘內可以完成）
- 其他的安排
    - 跟地理資料應用相關的專案一起
    - 匯入google、carto、biggis（NDVI）+ disfactory
    - 要確保有成果的證明，方便班級老師操作、學生紀錄學習歷程
- 期程
    - 七月初會公布，讓老師報名
    - 上slack #edu-sch001ing 繼續追蹤
- disfacory負責事項
    - 拍一個10-15分鐘的教學影片
    - 出一個20分鐘內可以完成的作業
## 下次待討論事項
- 累積待討論
    - 地號辨識
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
    - deeper詢問授權事宜
