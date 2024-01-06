# 違章工廠回報系統第99次小聚
###### tags: `Disfactory` `違章工廠` `違章工廠舉報系統`

時間：20211020 20:00
地點：線上、實體hybrid
線上：https://meet.google.com/coc-vuaa-ykz

## 參與者簽到：
現場：
- deeper
- yukai
- ael
- peii
線上：
- Caleb
- Yenchia
- Lydia
- Oriyar
- Sour
- David

## 近期update
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
|8|90|
|9|59|
|10|83|

- 農委會最新公佈：新增農地疑似工廠面積，從前年新增2,759公頃，減少成去年新增1,221公頃

## 待討論與待解issue
1. about.disfactory.tw
    - 貢獻者區塊
    - 介紹修改
2. disfactory.tw
    - followups4user
3. SpotDiff
    - domain
    - db
    - server
    - 切版
    - [行銷企劃](https://docs.google.com/document/d/1VHvbYUyeb3N-fqUuPgB8uEoOyzh093A6LV6PPFgVQFw/edit?usp=sharing)
4. 100次小聚
    - [表單](https://forms.gle/b1qiKQqGYPtbcLYQ6)
5. 大松


## 會議記錄
1. about.disfactory.tw
    - 貢獻者區塊
        - 設計完成
            - [手機版](https://www.figma.com/file/vnvt7JjXrRcXZlqLoW2vCZ/About.Disfactory?node-id=462%3A499)
            - [電腦版](https://www.figma.com/file/vnvt7JjXrRcXZlqLoW2vCZ/About.Disfactory?node-id=404%3A452)
        - david優先做
    - 介紹修改
2. disfactory.tw
    - followups4user
3. SpotDiff
    - 已完成
    - 基礎架構已好
    - 待完成
        - task
            - location table
            - table definition
            - function
            - testing case
        - script
            - 撈資料
        - db
            - 到底要用query的還是要dump進spotdiff的DB
            - 決定用query的
    - domain
        - spot.disfactory.tw
        - cloudfare
    - db
    - server
    - 切版
        - svg完成
        - 初步成果：https://disfactory-spotdiff.netlify.app
    - 行銷
        - [行銷企劃](https://docs.google.com/document/d/1VHvbYUyeb3N-fqUuPgB8uEoOyzh093A6LV6PPFgVQFw/edit?usp=sharing)
        - 使用者分享畫面！
            - Lydia開始設計
            - 小班
                - 不用太客製化，以免工程浩大
                - 但目前本來就有「已經有多少完成的數字」
4. 100次小聚
    - [表單](https://forms.gle/b1qiKQqGYPtbcLYQ6)
    - 現場16人
    - 菜單：
        - 港點-添好運or吉星or紅磡
        - 川菜-佳佳小吃店
        - 炸雞-拿坡里
        - 水果-台灣
    - 節目（感謝sandra和小海）
        - 線上＋現場
            - 破冰：牆上列出Disfactory timeline，讓大家標示相遇點
            - 加溫：每個人輪流抽一個問題回答，如果有新參者可以讓他隨便發問
            - 放鬆＋遊戲：吃吃喝喝，畫畫猜謎，
            - 現場：Switch、Youtube卡拉OK
            - 表演：Jason、小海＋佳昇
            - 抽獎/賓果：大獎搬回家（地球公民周邊產品、農地阿伯感謝您好農產品）

5. 大松
    - disfactory.tw徵新後端
        - 對server架設、營運、維護比較有經驗的
    - SpotDiff
        - enhancement的issue都需要implement
        - 會寫python、flask，大概知道database是什麼東西，就可以了

## 待辦&待討論事項
- 百聚不如一見
    - 訂餐
    - 
- 架server @yenchia @swind
- 結束畫面設計 @tin
- deeper
    - 介紹再修正
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
