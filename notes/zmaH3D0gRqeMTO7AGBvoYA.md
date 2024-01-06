# 違章工廠回報系統第112次小聚
###### tags: `Disfactory` `違章工廠` `違章工廠舉報系統`

時間：20220126 19:00
地點：線上
線上：https://meet.google.com/coc-vuaa-ykz
共筆：
https://g0v.hackmd.io/@yukaii/Disfactory/%2FzmaH3D0gRqeMTO7AGBvoYA

## 參與者簽到：


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
|     11| 82|
|     12|144|
|2022. 1| 68|

## 議程

## 會議記錄
- disfactory.tw
- 整體議題、跨網站

**SpotDiff**

ael: 作為 PM，我關心
1. API 串接的進度（才可以評估過年後要做什麼）
2. 測試完成的進度（才可以評估穩定度）Unit Test
3. Server 目前好像常常是 blocker，我們該怎麼避免？
年後大家的時間


sour 先去設定 CORS
sour: 我要怎麼測試知道有沒有 take effects


User token 的問題：
user token -> location -> POST answer (user token 過期的話怎麼辦)
=> 先去開 issue 

第一題回答不知道（0），還是可以進第二段回答「有無擴建」

Is_done： 不知道（0），如果兩個人都覺得是 0 ，要算 is_done 嗎？
=> expansion 要可以收不知道（0）=> 請設計加圖
=> 後端 is_done 判斷式不用改，即便兩個人都回答 [0,0]，之後有時間有人氣的話再拉出來再做一輪

user token 三段，只有第一段一樣，後端會算成同一個 user 嗎？

後端有打包環境設定的 docker 嗎？

前端還沒有寫 testing => 需要請教資深前端
寫出來的 function 有對應的 Unit Test


## 待辦&待討論事項
- 下次討論
- deeper
    - 發展行銷企劃
    - GA研究
- 累積待討論
    - [motion graphic腳本](/MmcrFV3AS4qnYESGCEvBug)
- 累積待辦事項
    - GA資料分離
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
    - [前端測試](https://disfactory-spotdiff.netlify.app/)
    - [about 設計](https://www.figma.com/file/vnvt7JjXrRcXZlqLoW2vCZ/About.Disfactory?node-id=575%3A3533)



# 一些新意見統整
