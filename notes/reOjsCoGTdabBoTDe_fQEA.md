# 違章工廠回報系統第126次小聚

###### tags: `Disfactory` `違章工廠` `違章工廠舉報系統`

時間：20220511 19:30 (GMT+8)
地點：線上、實體hybrid
線上：https://meet.google.com/coc-vuaa-ykz
實體地點：地球公民基金會台北辦公室（北平東路28號9樓之2）
小聚共筆：
https://g0v.hackmd.io/@yukaii/Disfactory/%2FreOjsCoGTdabBoTDe_fQEA

## 參與者簽到
- deeper
- ael

### 線上
- swind
- dotsea
- oriyar
- guojim


## 議題近況
### 近期update
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
|2022. 1| 73|
|      2|114|
|      3|191|
|      4|141|
|      5| 13|

## 議程
- 19:30-20:00 disfactory.tw
    - Cluster
- 20:00-20:15 整體議題、跨網站
- 20:15-20:45 大家來找廠 SpotDiff
    - 答案檢查
    - [ga](https://datastudio.google.com/u/0/reporting/3210d668-89af-4b9a-9756-cdcabd69c21f/page/hxlrC?s=nsC6gopCK_g)看看
    - 地圖畫框框[issue](https://github.com/Disfactory/SpotDiffFrontend/issues/67)
    - before/after按鈕教學 [issue](https://github.com/Disfactory/SpotDiffFrontend/issues/106)
- 20:45-21:00 最後加點
- 21:00～ 自由討論

## 會議記錄
- 19:30-20:00 disfactory.tw
    - cluster
- 20:00-20:15 整體議題、跨網站
- 20:15-20:45 大家來找廠 SpotDiff
    - 截至18:30
        - answer_count:27111
        - location_is_done_count:4994
        - user_count:3631
    - 快辨識完了！
        - 打算讓使用者繼續玩
            - 提高location_is_done的門檻+1
            - 設計修改
                - user count
                - individual count
                - 我們正在double check
            - 圖資改2021
                - 假設5/11凌晨12:00改成2021年，但是有個問題是，5/11之前使用者存在瀏覽器的factory_id是2020年的，所以可能會有資料不對的情形。另一個問題是，假設後端給的factory_id是2020年的，但前端這時已經改成2021年，會出現「明明是2020年的id，送給後端的卻標記成2021年」，反之亦然。（已解決）
                - Factory_ID不會變～～但是2020年那欄要改成2021
    - 地號邊框
        - yukaii做好prototype
        - 下一版讓他上
    - [ga](https://datastudio.google.com/u/0/reporting/3210d668-89af-4b9a-9756-cdcabd69c21f/page/hxlrC?s=nsC6gopCK_g)看看
    - 看看目前收回來的資料
- 20:45-21:00 最後加點
- 21:00～ 自由討論

## 待辦&待討論事項

- 下次 check points

- 下次討論

- 累積待討論
    - [motion graphic腳本](/MmcrFV3AS4qnYESGCEvBug)
- 累積待辦事項
    - 寄東西給未曾謀面的捧油



## 總文件庫
- 「大家來找廠」project spot.disfactory.tw
    - [計畫整體樣貌](https://g0v.hackmd.io/@yukaii/Disfactory/%2F5QH2TlaXQR21wMo3UIKZug) 
    - [spec](https://github.com/Disfactory/satellite/issues/2#issuecomment-866704442)
    - [mockup](https://www.figma.com/proto/TVAEC28E3ojabGHc8BawbI/%E8%A1%9B%E6%98%9F%E7%A9%BA%E7%85%A7%E5%9C%96?node-id=776%3A140800&scaling=min-zoom&page-id=599%3A433&starting-point-node-id=635%3A885)
    - [期程](https://www.notion.so/agrifactory/cf057f3b46fe4a738523b500c967ef5d?v=987e3e087e114c679142dab0c36af702)
    - [前端測試](https://disfactory-spotdiff.netlify.app/)
    - [about 設計](https://www.figma.com/file/vnvt7JjXrRcXZlqLoW2vCZ/About.Disfactory?node-id=575%3A3533)