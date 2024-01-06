# 違章工廠舉報系統第43次小聚

###### tags: `Disfactory` `違章工廠` `違章工廠舉報系統`

時間：20200805
地點：地公北辦
線上：https://meet.google.com/egx-zvjk-ouv


## 參與者簽到：

* deeper
* yukai
* oriyar
* swind
* yukai
* IU
* yellowsoar
* cph
* jsaon92
* william
* X lin
* LizBeth

線上
* Jenny


## 待討論
- 議題面
    - deeper更新一下違章工廠議題的進度（感覺多出很多），還有是不是又多出新的資料。

- 後端
    - 新的違章工廠的資料要怎麼併進來？還是重新爬爬看？
    - User Model
    - 自動產生舉報公文文號
    - 後面紀錄公文回報進度的 table
    - 工廠編號 PR 需要 review
    - 上週倒資料 csv 都還順利嗎？
    - 要建 staging 嗎？
    - 一種隱然不知道怎麼讓後台維護比較容易的不安
- 前端：
    - 我有看到在重構和做元件，但是我找不到你們的分工 QQ

- 設計：
    - 我覺得我今天沒有能量看，請 @deeper @X Lin @RAY @J 自己延續討論喔!

- 進度面
    - 需要的東西是公文處理流程的確切欄位

- 新人 on board 就是要多了解議題和受眾

    

## 會議記錄
- 本週GA數據
    - 使用者數量：196 -> 237
    - 新使用者數量：163 -> 196
    - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_00fbda56a9b65d6c27afb69da1e91213.png)



    - 相較上週

| 使用者 | 新使用者 | 跳出率 |
| ----- | ------ | -------|
| +41   |   +33  | +0.5% |


- 來源
- ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_933fb2cec929036f6b981a29de8185da.png)

- 前端


- 後端
    - Darren 的 print out 公文的部分， swind 會接手
    - 先處理 staging 和 Server management， DB auto backup 先 pending
    - jsaon 想先做測試的 refactor
    - Swagger PR 和 README 在進行當中

- 設計
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_19385334c1430f48a73298fccce61435.jpg)
    - 計畫要素
        - 目的、目標
        - 評估用的人物誌
        - 時程
        - 場所
        - 負責人員
        - 受測者
        - 預算
        - 測試工具
    - persona
        - 範例
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1037ee6297b626827a0f58d2aa3ff59e.jpg)
        - 我們自己的分類
            - 對科技產品的熟悉程度
                - 不會用手機接電話的阿婆
- 初步成果
    - 訂出目標、想問的問題
    - [文件](https://docs.google.com/spreadsheets/u/1/d/1Ae2oy7hn9_aNoa0-YnhbMp0nhPUpcfq3W-cy2prmuVk/edit#gid=0)
- 期程規劃
    - 8/19前完成研究計畫
    - 9/9前完成研究設計評估（使用狀況、任務、動線、觀察點、時間分配）
    - 9/12.13現地測試

## 前端和後端專案分 repo
分開了，避免一起 deploy 上 production
issue 仍然統一開在 Disfactory，前後端 repo 再 refer 過去


## 前端 2.0 切 task

合進 `frontend-2-0` branch

- 建立工廠
    - WIP: 手機版 #1 @Yukai
        - [ ] 顯示設定手機版按鈕 component 化
        - [ ] 顯示經緯度手機版
        - [ ] 新增工廠成功 modal
    - 電腦版
        - 桌面版 navigation bar
            - [ ] 三步驟顯示
            - [ ] 取消新增工廠按鈕
        - 經緯度
            - [ ] 搜尋經緯度表單
            - [ ] 打開/關閉經緯度介面
- 檢視工廠
    - 手機版
        - 工廠詳細資料 Bottom Sheet
            - [ ] 詳細資料半開/全開切換
            - [ ] 詳細資料顯示
            - [ ] 分享選單
        - [ ] 工廠篩選按鈕（navbar 下面那排）
        - [ ] 顯示設定按鈕
        - [ ] 詳細資料顯示時隱藏篩選按鈕、顯示設定
        - [ ] 分享按鈕
            - [ ] 點擊分享按鈕複製連結
            - [ ] 顯示通知
    - 電腦版
        - [ ] 電腦版顯示設定按鈕 popover menu
        - [ ] 工廠詳細資料 Sidebar
        - [ ] 工廠詳細資料 Sidebar 收合
        - [ ] 分享按鈕已複製提示
- 補充工廠
    - 手機版
        - [ ] 補充照片按鈕
        - [ ] 上傳圖片表單串接
        - [ ] 補充描述按鈕
        - [ ] 補充描述表單串接
        - [ ] 補充工廠成功 modal
    - 電腦版
        - [ ] 補充描述 modal

## 加入農委會新增的圖資

https://github.com/Disfactory/Disfactory/issues/372

```bash
curl -k 'https://map.coa.gov.tw/portal/sharing/servers/bdfbd5edc5c243ff929d61853997d58f/rest/services/Farmland_survey/L21_%E6%96%B0%E5%A2%9E%E5%B7%A5%E5%BB%A0106Q4/MapServer/0/query?objectIds=1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30,31,32,33,34,35,36,37,38&outFields=*&outSR=4326&returnGeometry=true&f=json' -H 'Content-Type: application/x-www-form-urlencoded'


https://map.coa.gov.tw/portal/sharing/servers/bdfbd5edc5c243ff929d61853997d58f/rest/services/Farmland_survey/L21_新增工廠106Q4/MapServer/legend?f=json

https://map.coa.gov.tw/portal/sharing/servers/bdfbd5edc5c243ff929d61853997d58f/rest/services/Farmland_survey/L21_新增工廠106Q4/MapServer/queryLegends?f=json


https://map.coa.gov.tw/portal/sharing/servers/bdfbd5edc5c243ff929d61853997d58f/rest/services/Farmland_survey/L21_新增工廠106Q4/MapServer/legend?f=json&dynamicLayers=[{"id":0,"name":"新增工廠","parentLayerId":-1,"defaultVisibility":true,"subLayerIds":null,"minScale":0,"maxScale":0,"source":{"type":"mapLayer","mapLayerId":0}}]


https://map.coa.gov.tw/portal/sharing/servers/bdfbd5edc5c243ff929d61853997d58f/rest/services/Farmland_survey/L21_新增工廠106Q4/MapServer/tile/8/112/214

https://map.coa.gov.tw/portal/sharing/servers/3e1f0873e5924a0b825a0678864e1c37/rest/services/Farmland_survey/Farmland_農地盤查總覽圖106Q4_newfactory/MapServer/tile/8/112/214
```

https://developers.arcgis.com/rest/services-reference/legend-map-service-.html

## 下次待討論事項
- [ ] 公文回覆追蹤 table 欄位確定 @deeper @cph @yellowsoar @swind @toby @ael
    - [ ] cross-table fields
    - [ ] document tag
- [ ] Digital Ocean Team
- [ ] 跟小白討論工廠編號
