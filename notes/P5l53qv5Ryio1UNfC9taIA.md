# 違章工廠回報系統第125次小聚

###### tags: `Disfactory` `違章工廠` `違章工廠舉報系統`

時間：20220504 19:30 (GMT+8)
地點：線上、實體hybrid
線上：https://meet.google.com/coc-vuaa-ykz
實體地點：地球公民基金會台北辦公室（北平東路28號9樓之2）
小聚共筆：
https://g0v.hackmd.io/@yukaii/Disfactory/%2FP5l53qv5Ryio1UNfC9taIA

## 參與者簽到
- deeper
- ael

### 線上
- swind
- oriyar
- 

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
    - about修改
- 20:00-20:15 整體議題、跨網站
- 20:15-20:45 大家來找廠 SpotDiff
    - gold standard [issue](https://github.com/Disfactory/SpotDiff/issues/30)檢查
    - [ga](https://datastudio.google.com/u/0/reporting/3210d668-89af-4b9a-9756-cdcabd69c21f/page/hxlrC?s=nsC6gopCK_g)看看
    - 地圖畫框框[issue](https://github.com/Disfactory/SpotDiffFrontend/issues/67)
    - 看看目前收回來的資料
    - before/after按鈕教學 [issue](https://github.com/Disfactory/SpotDiffFrontend/issues/106)
    - 擴建問題文案修正 [issue](https://github.com/Disfactory/SpotDiffFrontend/issues/107)
- 20:45-21:00 最後加點
- 21:00～ 自由討論

## 會議記錄
- 19:30-20:00 disfactory.tw
    - cluster
    - about修改
- 20:00-20:15 整體議題、跨網站
    - 桐花松，有人一次辨識了500家
- 20:15-20:45 大家來找廠 SpotDiff
    - @swind server耐受力研究
        - 測試的 script 是這樣設計
            1. 呼叫 spotdiff - /users/ 取得 token
            2. 呼叫 spotdiff - /location 取得題目
            3. 呼叫 disfactory - /factories/<factory_id> 五次 取得工廠座標
            4. 停止 30s ~ 60s 模擬使用者玩遊戲
            5. 呼叫 spotdiff - /user 取得 token
            6. 呼叫 spotdiff - /answer
            7. 停止 10s ~ 20s  再進行下一輪遊戲
        - 模擬人數 500 人
        - 每秒加入 10 直到同時有 500 人在線上
        - 目前發現
            - bottleneck 會在 disfactory 的 /factories/<factory_id> 這個 API 身上
            - 因為他會多取得 report record 等額外資訊，所以當同時有 500 人在線上玩遊戲時
            - 每個 request 平均回應時間會到 15 秒 以上
            - 也就是使用者進入 Game 頁面可能會需要等 15 秒 以上才能開始玩（很有可能更久）
        - 所以
            - 我先修改了 disfactory API 增加了 /factories/<factory_id>/location
        - 這個 API 指回傳位置資訊（有包括 spotdiff 前端要要的內容 lat , lng , townname ）
        - 因此
            - 前端應該只要修改 API URL 就可以了
        - 改成使用這個之後一樣的 500 人模擬
            - 每個 request 平均回應時間約 5 秒
            - 這應該已經快要超過使用者開一次遊戲可以等待的極限了吧 ...
        - 模擬 1000 人玩的話
            - 每個 request 平均回應時間會到 20 秒以上
            - 這應該是無法接受的，所以之前 deeper 提出的 60 秒 1000 人遊玩，目前的機器辦不到
        - 500 人應該是極限了
        - 所以
            - 想麻煩前端改一下使用的 Disfactory API
            - 新的 API staging 已經更新了，
            - Production 看討論今天好像還有人在用，我會在晚上比較晚的時候更新
        - 目前看起來最花時間的應該是 disfactory 的 query
        - swind想到的解決辦法除了用更貴的 server 之外，也可以把 staging server 加入使用
            - 因為只是需要 factory 的位置資訊
            - 所以 staging server 也可以提供
    - 地號邊框
        - yukaii來研究
    - gold standard [issue](https://github.com/Disfactory/SpotDiff/issues/30)檢查
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