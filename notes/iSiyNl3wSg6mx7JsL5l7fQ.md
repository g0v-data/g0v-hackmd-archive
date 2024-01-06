# 違章工廠回報系統第101次小聚
###### tags: `Disfactory` `違章工廠` `違章工廠舉報系統`

時間：20211103 20:00
地點：線上、實體hybrid
線上：https://meet.google.com/coc-vuaa-ykz

## 參與者簽到：
### 現場
- deeper
- yukai
- dotsea
- jchans (老翰)

### 線上
- Lydia
- littlewhite
- yenchia
- 酸酸的
- mglee
- oriyar
- slayer

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
|10|104|
|11|7|

## 待討論與待解issue
1. about.disfactory.tw

3. SpotDiff
    - domain
    - server
    - db
        - @sour 目前狀況
    - 前端
        - @david 目前狀況
4. 其他諮詢
    - @slayer會來嗎XD 接續一下上週的話頭
    - @tai 有什麼問題會想要來問ㄉ嗎～

## 會議記錄
1. about.disfactory.tw
    - [新設計](https://www.figma.com/file/vnvt7JjXrRcXZlqLoW2vCZ/About.Disfactory?node-id=575%3A3533)OK了
    -  
3. SpotDiff
    - domain
        - account沒有sudo，不能裝東西
    - server
        - 開digital ocean權限給yenchia
    - db
        - @soursour @yenchia 目前狀況
            - 大概完成了一半
        - 困難
            - year的資訊
            - zoom level
                - data model不用存這個欄位
        - answer table
            - IsRight -> Integer
    - 前端
        - @david 目前狀況
            - 剩最後一頁和api
        - 困難
            - inner bounding box計算
                - 後端會直接傳兩個端點的api
                - async，自己傳給自己
        - on board
            - 老翰
                - 
4. 其他諮詢
    - @slayer會來嗎XD 接續一下上週的話頭
        - 會收到什麼資料
            - line帳號
            - email
            - 地點和照片直接串api給disfactory
        - 管理者頁面
            - 馬上回覆會有pushing communication
                - 柯批停掉的原因就是太貴
                - 算一則一則
        - 免費推播用量
            - 500則
            - line bot自動推播不會算在那個額度裡
        - 考慮問題
            - 隱私問題
                - 法院可以取得line資訊
                    - 是可設計的，如post之後就直接銷毀
            - 壞資料
                - 社群問題社群解決：
                    - 找人幫忙review資料
                    - 推播：有新資料要review唷
                    - 也可以ban掉某些帳號
                - 刪除資料
                    - 既有的問題
            - 有人一直想問問題
                - QA頁
                - 帶你使用去看操作教學
        - cost
            - 到一個規模之前，是希望參與這個公民活動
            - 當他變成一天兩萬則就頭痛了
        - 
    - @tai 有什麼問題會想要來問ㄉ嗎～
        - 小白直接去黑熊那邊～

## 待辦&待討論事項
- 架server @yenchia @swind
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
