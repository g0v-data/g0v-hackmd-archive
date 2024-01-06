# 違章工廠回報系統第98次小聚
###### tags: `Disfactory` `違章工廠` `違章工廠舉報系統`

時間：20211013 20:00
地點：線上、實體hybrid
線上：https://meet.google.com/coc-vuaa-ykz

## 參與者簽到：
線上：
- deeper
- tin
- swind
- littlewhiteYA
- 酸酸
- 典洋
- swind
- sandra
- peii
- ael

## 近期update
- 明天開記者會
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
|10|61|

## 待討論與待解issue
1. about.disfactory.tw
    - 貢獻者區塊
    - 介紹修改
2. disfactory.tw
    - followups4user
3. SpotDiff
    - data model
    - 結束畫面設計
    - 切版進度
4. 100次小聚
    - [表單](https://forms.gle/b1qiKQqGYPtbcLYQ6)


## 會議記錄
1. about.disfactory.tw
    - 貢獻者區塊
        - tin今天再修一下，即可交給典洋
        - 10/27前做好～
    - 介紹修改
        - deeper有更多要修的
2. disfactory.tw
    - followups4user
        - 上staging先
        - swind做好，小白review
        - deeper測試
3. SpotDiff
    - [data model](https://docs.google.com/presentation/d/1hyak0PdXA3CpxSC82T7ahmp0AbqjEJS2c3AcnhURpnw/edit?pli=1#slide=id.gf5e3502c4a_2_0)
        - 重新思考data model > location的欄位
        - database要跟既有的分開還是合併
        - user table
            - 必要性
                - 需要看一整組答案的可信度
                - 希望user不要回答到重複的題組
            - 新增IP欄位來看有沒有人亂弄
        - soursour想問yenchia會建到什麼程度
    - 結束畫面設計
    - 切版進度
        - 還在切～也要等api弄完才能更有進度
        - 問題
            - svg不完全載入問題
                - 不同瀏覽器不同問題
                - solution：有進度就上傳到github，讓其他人幫忙看
            - frontend和backend的repo要分開來嗎？
                - swind建議分開
        - 禮拜五前做個進度
4. 100次小聚
    - [表單](https://forms.gle/b1qiKQqGYPtbcLYQ6)
    - 紅布條！
    - 節目
        - 若有線上＋現場參與
            - 破冰：每個人輪流抽一個問題回答。
            - 放鬆：現場有東西吃＆喝，開一個遊戲區跟線上的人玩畫畫遊戲。
            - 吉他演奏會直播。
        - 若只有現場參與
            - 破冰：每個人輪流抽一個問題回答。
            - 放鬆：現場有東西吃＆喝，我們可以玩switch嗎？（但我沒有，有人有嗎？）
            - 不夠嗨的話請小海or Jason 表演，夠嗨的話youtube卡拉OK。
5. 大松
    - 邀請典洋來～～～
    - 提案deeper做

## 待辦&待討論事項
- 百聚不如一見
    - 準備食物、小遊戲
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
