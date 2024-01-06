# 違章工廠回報系統第88次小聚
###### tags: `Disfactory` `違章工廠` `違章工廠舉報系統`

時間：20210804
地點：線上
線上：https://meet.google.com/coc-vuaa-ykz

## 參與者簽到：
線上：
- deeper
- tin
- yenchia
- lydia
- swind
- yukai

## 近期update
- 「大家來找廠」project
    - [計畫整體樣貌](https://g0v.hackmd.io/@yukaii/Disfactory/%2F5QH2TlaXQR21wMo3UIKZug) 
    - [spec](https://github.com/Disfactory/satellite/issues/2#issuecomment-866704442)
    - [wireframe](https://www.figma.com/proto/TVAEC28E3ojabGHc8BawbI/%E8%A1%9B%E6%98%9F%E7%A9%BA%E7%85%A7%E5%9C%96?node-id=50%3A2&scaling=min-zoom&page-id=0%3A2)
    - prototype
        - [一張圖](https://www.figma.com/proto/TVAEC28E3ojabGHc8BawbI/%E8%A1%9B%E6%98%9F%E7%A9%BA%E7%85%A7%E5%9C%96?node-id=637%3A1287&scaling=min-zoom&page-id=637%3A816)
        - [兩張圖](https://www.figma.com/proto/TVAEC28E3ojabGHc8BawbI/%E8%A1%9B%E6%98%9F%E7%A9%BA%E7%85%A7%E5%9C%96?node-id=457%3A331&scaling=min-zoom&page-id=457%3A331)
        - [圖片來源](https://drive.google.com/drive/folders/1Arq43rHY8wMBQbZGJ6C5QsOsIMoSpt4K)
- 回報數匯總

| 月份 | 回報件數 |
| ---- | ---- |
|2020.11|24|
|12|46|
|2021.1|49|
|2|55|
|3|53|
|4|110|
|5| 65|
|6|109|
|7|60|
|8|6|

## 待討論
1. [motion graphic腳本](/MmcrFV3AS4qnYESGCEvBug)
2. 新prototype邏輯確認
4. 既有issue


## 會議記錄
### motion graphic
- Stasia電腦故障，推遲討論
### prototype邏輯確認
- 暫定變成每題都double check
    - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_eabf1ab5df4bc41ba0e012b794778a6d.png)
    - 每個地點存兩個答案，一共有四種可能
        - YY
        - YN
        - NY
        - NN
    - 討論
        - 問題校正
        - 會不會太長？
            - 如何知道有多少人放棄
                - 某個table加上狀態，inprogress & complete
                - GA
        - 多數決判斷邏輯
            - 答案完全一致才算一致
            - 不管怎樣都給三個人標
        - 測試階段
            - troubleshooting
        - 出題邏輯
            - 100題 = 25組 = 1輪
            - 什麼區域優先
                - 台中、彰化、高雄
                - 台南、桃園、屏東
            - 正確答案題組
                - Ｏ
                - Ｘ
                - NA
        - 期程
            - 9/1設計稿完成
            - 10/13完成
### 既有issue
- 經濟部資料
    - swind再努力
    - 農委會[農業及農地結果查詢圖台](https://map.coa.gov.tw/farmland/survey.html)有做相似的事情，但只有放上11007的查處資料

## 待辦&待討論事項
- 累積待討論

- 累積待辦事項
    - GA
    - jiahe建議
        - GA/GTM排除坑友的數據
        - 線下活動宣傳的配合（含QRcode的實體和電子flyer用於流傳）實體 flyer++ 分類廣告？
            - peii負責
        - 怎麼做 LINE 行銷
    - 寄東西給未曾謀面的捧油
    - 都市計畫區可以改成填一個google表單