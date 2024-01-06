---
tags: jothon
---

g0v 成就機制資料規劃
=================

目標
----
希望設計一個資料結構，可以把 slack, hackmd, hackpad, kktix, github ... 等 g0v 社群有在使用的協作工具的成就機制整合起來，希望能有以下幾個條件：
- 不需要透露個資（如 E-mail）
- 可以區分個別人，讓社群成員可以認領自己的成就
- 除了過去的舊成就，希望也能包含未來的新成就
- 成為社群內的開放資料，人人皆可串接使用

資料成果
-------
- slack
    - https://docs.google.com/spreadsheets/d/12z0yAy5YJschqyeg8gDrPhRXi99XOnFPKYj0iSAPdwM/edit
- hackmd
    - https://aws.ronny.tw/hackmd/
- hackpad
    - [展示](https://aws.ronny.tw/hackpad/)
    - 
- kktix
    - https://g0v.hackmd.io/66Z_D6zlT_GsDtoBfg3x9g?view
- github
    - [匯出 github 成就程式](https://github.com/ronnywang/g0v-badge-github-data)

資料格式規劃
----------
- 三種檔案
  - list.csv
      - 列出有哪些服務
      - 欄位：service,name
          - service: 服務代碼，指哪個服務，Ex: slack, hackpad
          - name: 服務名稱，給人閱讀用
  - {service}-id.csv
      - 欄位: uid,name,hash_ids
          - uid: 使用者在該服務上的代碼（如不方便公布原代碼，可用 hash 過的代碼）
          - name: 使用者在該服務的顯示名稱
          - hash_ids: hash 過後的一些可以連結到真實身份的字串
              - 統一採用 md5('真實身份' + 'g0vg0v') 加密
                  - Ex: ronnywang@gmail.com => c58d4146a081dd1944c1487465dbf478
              - 真實身份格式
                  - email
                  - github://{github 帳號}
                  - facebook://{id}
              - 用 ; 分離多個身份
              - Ex: U038DCDRC,Ronny Wang,c58d4146a081dd1944c1487465dbf478
- {service}-badge.jsonl
      - 欄位: uid,time,brief,extra
          - uid: 與 {service}-id.csv 對應的 uid
          - time: 該成就取得時間，可以是 2019-04-24 或 2019-04-24 13:33:00 兩種格式
          - brief: 一句話的成就簡述，Ex: 「使用 emoji 1000次」
          - extra: 更詳細的其他補充資料（例如是在哪一篇文章、哪一個看板...）
              - url: the link of the badge
              - title: the title of the badge
          - Ex: {"uid":"c58d4146a081dd1944c1487465dbf478","time":"2016-07-23","brief":"發言200次","extra":{"board":"general","url":"https://xxx","title":"the badge data from"}}



待作事項
-------
1. 將 hackpad, hackmd, slack 的成就用以上格式釋出
2. 依照上面格式建立網站，可以查詢各種 hash_id 對應的成就
3. 透過 openid ，讓使用者可以認領自己 hash_id 的成就
4. 將 github 的成就也做整理
5. 建立自動化成就更新的機制


相關資料
------
- [20220820大松提案簡報](https://docs.google.com/presentation/d/1RIerafuSOShS7KRC9anquuKDbAA6MGQyHA7x2vEFuso/edit?usp=sharing)
- 其他參考 [FB 社團的貢獻機制](https://g0v.hackmd.io/bg6cscgyR2-zscyQEeXSCA?view)