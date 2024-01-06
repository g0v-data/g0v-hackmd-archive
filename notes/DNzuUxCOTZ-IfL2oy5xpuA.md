---
title: 違章工廠舉報系統第19次小聚
tags: Disfactory, 違章工廠, 違章工廠舉報系統
---

# 違章工廠舉報系統第19次小聚

時間：20200219
地點：地球公民基金會北辦
線上：

## 參與者簽到：
- simon
- 小海
- 小班
- 佳昇
- 沅諭
- yellowsoar
- yukai
- Andy
- cph
- 

## 待討論
- 文件 
about.disfactory.tw
跳坑指南
- GA

- 單一工廠的分享連結
需要跟山爪討論

## 會議記錄
1. about.disfactory.tw 使用者介紹頁面
設定about頁面在 g0v hackMD文件下，yukai do sth. 就可以更新到網頁上唷

2. 後端： 3/20 前進度
    * refer to csv file from ronnywang on README
    * logger
    * last updated (已做完，已發 PR)
    * record history (已做完，已發 PR)
    * 每一間工廠 human readable 編號
    * 每間工廠 unique url 方便 share
    * 需不需要 search
    * admin page (nice to have)
4. GA & GTM
    * 「更新」的不同欄位要可以變成 label
    * PV 怎麼設定 /, /create, /edit
    * Click Text and Click ID 
6. 2/23 使用者測試
    * 訪綱：
        * 舉報的情境， 擔心憂慮的點
        * Search：會想用什麼搜尋？
        * Share：在什麼情境下分享？
    * 錄影和螢幕錄影
    * Usability
        * 表格印出來=> Deeper
    * 
7. 未來設計 (Sandra)
    * Share
    * Search
    * Admin page
        * 需要額外輸入什麼資訊嗎？
        * Spreadsheet view
        * Doc View
        * Dashboard for admin and users
            * 已舉報多少件
            * 熱點鄉鎮
            * 送件/行動時間表


## 下次待討論事項
後端已裝好開發環境：
- https://docs.docker.com/install/linux/docker-ce/ubuntu/
- sudo curl -L "https://github.com/docker/compose/releases/download/1.25.3/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose #https://docs.docker.com/compose/install/
- sudo chmod +x /usr/local/bin/docker-compose
- sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
- sudo service docker start
- git clone https://github.com/Disfactory/Disfactory
- cd Disfactory/backend
- vi gis.../setting.py allowedhost
- vi docker-comose.ym del python -m 
- vi guinico.config.py mv 127.0.0.1 --> 0.0.0.0
- docker-compose up


代辦事項
- logger 補足週全度
- 研究有無現有套件 連結Django logger to postgresql
- 研究postman測後端api