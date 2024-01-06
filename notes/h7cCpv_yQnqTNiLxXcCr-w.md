# 違章工廠舉報系統第51次小聚

###### tags: `Disfactory` `違章工廠` `違章工廠舉報系統`

時間：20201007
地點：地公北辦
線上：https://meet.google.com/egx-zvjk-ouv


## 參與者簽到：
- deeper
- ael
- yukai
- IU
- X Lin
- SL

線上：
- cph


## 待討論
- 議題面
    - 9/29半年報、10/7聲明稿
    - 10/8見經濟部次長、中辦主任
    - 10/14講座
    - 10/21竹北社大演講
    - 
- 前端

- 後端
    - @cph @deeper @yellowsoar 我們來設定 Digital Ocean
    - [搬移步驟](https://www.digitalocean.com/docs/images/snapshots/how-to/migrate-droplets/):
        - 關機（？）
        - 做 snapshot
        - 搬 snapshot 到另一個帳號
        - 用這個 snapshot 做一個新的 droplet
    - 啟動步驟 （tmux: server）
        - caddy
        - django server
        - django q worker
        - postgresql (應該開機就開了)
    - 啟動步驟二（tmux: staging-server）
        - django server
    - 新 server IP: `64.227.82.117`

- 設計
    - @X Lin @RAY @deeper @SL 跟大家簡介訪談結果，以及下階段會想要做什麼


## 會議記錄
- 本週GA數據
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_46854209a8083486153d27b9a2d2ab31.png)


    - 這兩週相較上上週（上週太跳，沒有參考價值）

| 使用者 | 新使用者 | 跳出率 |
| ----- | ------ | -------|
| +607 | +587 | -45.6% |


- 來源
    - disfactory.tw
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b4645ee6c980ea2d6116efcec8502f2d.png)


    - about.disfactory.tw
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9e7a046785025249b48a3ec40c3aa9e4.png)


- 前端
    - 持續給大家測試
    - 找出了一些bug！
- 後端
    - 轉移了digital ocean
- 設計
    - [訪談結果](https://docs.google.com/document/d/1wHwaya5AbWQlvqVmpj9QXu7grLVVQBP099RCcLoiWlY/edit)
    - 待開發
        - dashboard
        - display status

- 專案方向
    - 10/7 migration&user need research report
    - 10/14 break
    - 10/21 bug fixing
        - 10/24 g0v hackathon
    - 10/28 bug fixing
    - ??/?? stakeholders discussion
    - 11/4 retro
    - 11/11 issue solving
    - 11/18 project goal calibration
- 推廣策略
    - 關鍵字：「拆工廠」

## 下次待討論事項
- 