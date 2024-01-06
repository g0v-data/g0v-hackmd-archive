# 違章工廠回報系統第105次小聚
###### tags: `Disfactory` `違章工廠` `違章工廠舉報系統`

時間：2021201 20:00
地點：線上、實體hybrid
實體地點：地球公民基金會台北辦公室（北平東路28號9樓之2）
線上：https://meet.google.com/coc-vuaa-ykz

## 參與者簽到：
### 現場
- deeper
- peii

### 線上
- yukaii
- caleb
- oriyar
- dotsea
- sour biebie
- yenchia
- tai
- MG

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

## 待討論與待解issue
1. :hammer:Disfactory.tw @swind @yukai @LittleWhiteYA @tai
    - 把年底前要做完的 Issue 加入 2.2.6 milestone，沒有要做的往後丟
2. Disfactory Frontend
    - [Cache factories result in local storage](https://github.com/Disfactory/frontend/issues/134)
    - [三層 zoom in level 有不同的 cluster，取消隨機顯示 pin](https://github.com/Disfactory/frontend/issues/121)
    - Remove frontend from Disfactory/Disfactory

4. :eyes: SpotDiff
    - 前端ㄉ進度 @David Fu 

19:30-20:00 disfactory.tw
20:00-20:15 整體議題、跨網站
20:15-20:45 大家來找廠 SpotDiff
20:45-21:00 最後加點（？）
21:00～ 自由討論

## 會議記錄
- disfactory.tw
    - 前端issue檢視
        - zoom in issue assigned to Caleb
        - remove frontend files @deeper
        - cache factories @yukai
- 整體議題、跨網站
    - 最近地公忙公投，
    - 慢慢把followups4user的內容加上去
    - 下週第15波檢舉
- spotdiff
    - 酸酸的進度
    - api
        - 確認上週把「user個人已辨識多少」加入了status的api
    - 存answer的時間點
        - 從每兩題答完存一次變成每五題按了submit才存
    - gold_standard
        - 如果答錯，直接刪除該次題組的所有ans
        - Step 1: front-end returns 5 answers to the back-end, and one of them is the gold standard
        - Step 2: back-end checks if the gold standard is answered correctly
            - If not, discard all the answers
            - If yes, record the 4 non-gold standard answers to the database

    - yenchia 12/23-1/15會不在
- linebot

## 待辦&待討論事項
- 架server @yenchia @swind
- deeper
    - 給出完整正確題組
    - 發展行銷企劃
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
    - [前端測試](https://disfactory-spotdiff.netlify.app/)
