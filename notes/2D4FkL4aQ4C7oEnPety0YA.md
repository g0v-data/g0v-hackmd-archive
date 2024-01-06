# 違章工廠回報系統第87次小聚
###### tags: `Disfactory` `違章工廠` `違章工廠舉報系統`

時間：20210721
地點：線上
線上：https://meet.google.com/coc-vuaa-ykz

## 參與者簽到：
線上：
- deeper
- tin
- swind

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
|7|54|

## 待討論
1. [motion graphic腳本](/MmcrFV3AS4qnYESGCEvBug)
2. 新prototype
    - [一張圖](https://www.figma.com/proto/TVAEC28E3ojabGHc8BawbI/%E8%A1%9B%E6%98%9F%E7%A9%BA%E7%85%A7%E5%9C%96?node-id=637%3A1287&scaling=min-zoom&page-id=637%3A816)
    - [兩張圖](https://www.figma.com/proto/TVAEC28E3ojabGHc8BawbI/%E8%A1%9B%E6%98%9F%E7%A9%BA%E7%85%A7%E5%9C%96?node-id=457%3A331&scaling=min-zoom&page-id=457%3A331)
    - 問題：
        - 幾乎都是建物，選到農地的很少很少，所以依照我們現在的邏輯，他都會被問兩次。
        - 有看到不少 2020 是農地、2017 也是農地的，所以我們不能依照 2017 是農地就判斷為可以送檢舉？


## 會議記錄
1. Swind修正之前factory存不進DB的問題
    - 之後如果新增之後馬上刪除，要記得去改display number
3. 新prototype確認
    - 要變成每題都double check嗎
    - 暫定變成每題都double check
    - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_eabf1ab5df4bc41ba0e012b794778a6d.png)
    - 每個地點存兩個答案，一共有四種可能
        - YY
        - YN
        - NY
        - NN


## 待辦&待討論事項
- 累積待討論
    - [地號辨識 issue 96](https://github.com/Disfactory/frontend/issues/96)
- 累積待辦事項
    - GA
    - jiahe建議
        - GA/GTM排除坑友的數據
        - 線下活動宣傳的配合（含QRcode的實體和電子flyer用於流傳）實體 flyer++ 分類廣告？
            - peii負責
        - 怎麼做 LINE 行銷
    - 寄東西給未曾謀面的捧油
    - 都市計畫區可以改成填一個google表單