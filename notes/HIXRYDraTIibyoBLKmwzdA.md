# 違章工廠回報系統第102次小聚
###### tags: `Disfactory` `違章工廠` `違章工廠舉報系統`

時間：20211110 20:00
地點：線上、實體hybrid
實體地點：地球公民基金會台北辦公室（北平東路28號9樓之2）
線上：https://meet.google.com/coc-vuaa-ykz

## 參與者簽到：
### 現場
- deeper
- peii
- yukai
- sandra
- ael
- dotsea

### 線上
- swind
- sourbiebie

## 近期update
- 回報數匯總

| 月份 | 回報件數 |
| ---- | ---- |
|2020.11| 24|
|     12| 46|
|2021. 1| 49|
|      2| 55|
|      3| 53|
|      4|110|
|      5| 65|
|      6|109|
|      7| 60|
|      8| 90|
|      9| 59|
|     10|104|
|     11| 20|

## 待討論與待解issue
1. SpotDiff
    1. bounding box 到底要前後端誰記、怎麼記
    2. 這代表我們可以聊前後端接的 API 了嗎？
    3. SpotDiff 從 Disfactory.tw 拿資料是單次dumped csv 還是 API?
2. about.disfactory.tw
    1. 希望有人幫忙解掉嘉義市回報率50%這個[issue](https://github.com/Disfactory/about.disfactory.tw/issues/52)
3. disfactory.tw
    1. 打imgur
    2. 照片備份
    3. issue508 @littlewhiteYA
4. 諮詢、閒聊、開工

## 會議記錄
1. SpotDiff
    1. bounding box 到底要前後端誰記、怎麼記
    2. 這代表我們可以聊前後端接的 API 了嗎？
    3. SpotDiff 從 Disfactory.tw 拿資料是單次dumped csv 還是 API?
        1. 直接dump就好 @deeper給
        2. 請IU再跑一次ronny的爬蟲code
        3. 只要給factory ID
            - 每次大家來找廠的前端去跟disfactory的api拿
    4. 下禮拜來開api
2. about.disfactory.tw
    1. 希望有人幫忙解掉嘉義市回報率50%這個[issue](https://github.com/Disfactory/about.disfactory.tw/issues/52)
3. disfactory.tw
    1. 打imgur
        1. 自動化script，
            1. 要再寫撈出所有imgur網址的程式 要再分別
            3. 接上IU本來寫好的
        3. 頻率
            1. 一個月一次
            5. or每天100筆
    3. 照片備份
        1. 現在server還剩38G
    5. issue508 @littlewhiteYA
    6. cluster
        1. 分層級取api
            1. 層級如zoom in level
            2. 決定取的api 
3. disfactory.tw
    1. 針對萬年解不完 UI enhancement 的 issue＃417，做了三個設計上的小更動，Figma頁面[在此](https://www.figma.com/file/dFuJKpdDcmHNDqdj1011Zo/Disfactory_UI_design_2021?node-id=2097%3A8774)。:japanese_ogre:
        - 前端｜讓使用者知道現在正在看哪個PIN → 更改 active pin的外觀（多加一個框）
        - 前端｜讓使用者看得出來自己到底是上傳了到哪個PIN → 三天以內（７２小時）有被EDIT過資訊的PIN，上頭加一個「NEW」
        - 後端｜讓使用者認知到那個 PIN 還差照片 → 像是「已處理：{詳細狀態}」一樣，「未處理」的詳細狀態也可以分已經有照片或沒有照片兩種狀態。
        - 以上為設計師的丟球，求工程師們接球 :upside_down_face:
5. 諮詢、閒聊、開工

## 待辦&待討論事項
- 架server @yenchia @swind
- deeper
    - 給出完整正確題組
- 累積待討論
    - [motion graphic腳本](/MmcrFV3AS4qnYESGCEvBug)
- 累積待辦事項
    - GA
    - jiahe建議
        - GA/GTM排除坑友的數據
        - 線下活動宣傳的配合（含QRcode的實體和電子flyer用於流傳）實體 flyer++ 分類廣告？
            - peii負責
        - 怎麼做 LINE 行銷
    - 寄東西給未曾謀面的捧油



## 總文件庫
- 「大家來找廠」project spot.disfactory.tw
    - [計畫整體樣貌](https://g0v.hackmd.io/@yukaii/Disfactory/%2F5QH2TlaXQR21wMo3UIKZug) 
    - [spec](https://github.com/Disfactory/satellite/issues/2#issuecomment-866704442)
    - [mockup](https://www.figma.com/proto/TVAEC28E3ojabGHc8BawbI/%E8%A1%9B%E6%98%9F%E7%A9%BA%E7%85%A7%E5%9C%96?node-id=776%3A140800&scaling=min-zoom&page-id=599%3A433&starting-point-node-id=635%3A885)
    - [期程](https://www.notion.so/agrifactory/cf057f3b46fe4a738523b500c967ef5d?v=987e3e087e114c679142dab0c36af702)
