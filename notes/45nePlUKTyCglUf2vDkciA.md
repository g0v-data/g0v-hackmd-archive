---
tags : vTaiwan小松
---
# 20190417 vTaiwan 小黑客松

時間：2019-04-17 週三 19:00-21:00
地點：社會創新實驗中心 2F A9 會議室（地圖：https://goo.gl/maps/X65uN9PFXAo）
待辦事項區：[vTaiwan 待辦事項（歡迎認領工作）](https://g0v.hackpad.tw/vTaiwan--AuHFzoOJk7o)
出席：Ronny、子絜、peace、怡孜、仔魚、Wellson、Allen、知澔、雅雯、安平、au(線上)、Stephanie、Scott、PDIS 的筱婷

線上組：
Wifi：PDIS_Public_5G/ji394pdis、startup99/306306306

主持人(facilitator)：
Translation：[English ](https://translate.google.com/translate?hl=en&sl=auto&tl=en&u=https%3A%2F%2Fg0v.hackpad.tw%2Fep%2Fpad%2Fstatic%2FleY4KC9wlOL&sandbox=1)

預定流程
18:30-19:00 報到 Arrival and Registration
19:00-19:15 開場、自我介紹 
19:15-19:30 確認討論議程
19:30-21:00 討論&hacking
21:00-21:30 成果分享&決定下週主持人
下週主持人：

提案（自己的小松自己提案）
---
* 有點想就這些法規問問大家的意見（還有readr上提到的法規們）～　https://news.pts.org.tw/article/429021
    * [readr假訊息與它們的產地](https://www.readr.tw/project/disinformation?fbclid=IwAR2ptfkNb1flLljc3ZVO4JYrj3dg818lFII1Z2s-8687t04EWuL5ru-QNVM)
    * [vTaiwan的polis](https://polis.pdis.nat.gov.tw/8m7p5emh8m) (intro還沒填)
    * 用readr的polis還是vTaiwan自己的?
* 【插播】《鄉民看電視》http://tvnews-logger.g0v.ronny.tw/
    * 目前介面 demo
    * 請大家幫忙玩玩看
    * 防亂：Ronny 黑箱演算法大解密 引起外界討論
        * rule1: 如果超過 10% 沒處理就 -10，超過 30% 沒處理 -30，超過 50 % 沒處理 -50
        * rule2: 如果新聞區沒有加標題的話，一則 -2 分，最多 -20
        * rule3: 如果新聞區的量 < 50% ，直接 -30
        * 高於 90 分，就沒有警告，90-60 有警告，低於 60 不讓儲存
    * 需要：有人一起來寫腳本、拍 YouTube 教學影片、配音
        * 可能加上難判斷的例子
        * 腳本：https://g0v.hackmd.io/HFGOGx42Q--qrd49ayRCsA
    * 需要：有人幫忙試玩
    * 需要：小額 donate（現在一個月大概台幣300-400）
    * chihao> 當天出當天的新聞？
        * 3pm 完成午間新聞、9pm 完成晚間新聞
    * 下一步：tagger tag 每一段新聞
        * logger 可能可以有 api，tagger 可以去抓
    * 問題：一個畫面兩個新聞
        * 也許加一個按鈕：我不確定 / 這段有兩則消息
    * wellson: 很想全部按廣告
        * 「新聞」
* 【插播】與香港社會企業交流 by 筱婷 (g0v slack id: checrates)
    * 6/18 徵求g0ver和香港太平紳士[馬錦華](https://www.seinsights.asia/profile/128/1262)&香港社會企業好朋友們聊聊天(?)
    * [之前馬+au的聊天逐字稿](https://sayit.archive.tw/2019-02-20-%E7%A4%BE%E5%89%B5%E4%B8%AD%E5%BF%83-%E7%AC%AC%E5%9B%9B%E5%8D%81%E4%B8%89%E6%AC%A1-office-hour/%E9%A6%AC%E9%8C%A6%E8%8F%AF)
* 來申請個政治獻金專戶 by Ronny
    * https://sunshine.cy.gov.tw/News_Content.aspx?n=16&sms=8860&s=12442
        > [name=yitzuchen] dry run一下
    * pofeng: 剩下的錢不能直接捐基金會，可以委託
    * pofeng: 真的抵稅的部分很少
    * ronny: 募到 689 萬我就選立委
* 關於「公民監督、政府施壓（？）社交媒體處理不實消息、假帳號」這件事（用詞很不精準），vtaiwan 有興趣開討論嗎？也許可以變成一個 multi-stakeholder forum？ by chihao @slack
    * ronny: 記得歐盟有要求 Facebook 吐資料
    * ronny: NCC 之前有把 LINE 什麼的找來聊天
    * 用社群媒體的角度處理這問題
    * ronny:
        * 有主管機關的新聞
            * 電視新聞台
            * 廣播
        * 沒主管機關的新聞
            * 商譽
        * 消息
            * 長輩圖
            * 訊息
            * meme
    * 新聞vs非新聞學術定義: 
        * 狗咬人人咬狗
        * https://www.lawbank.com.tw/treatise/pl_article.aspx?AID=P000235843
    * 莫忘金孫共識! 
    * Peace：先討論網路公共性、公益性的問題：網路的理想
        * 自律
    * Peace：先討論新聞的目的性：新聞要解決什麼問題
    * Peace：公共媒體、公民媒體、非上述兩者三個分向來討論

分享（想跟大家分享的事情）
---
- 不知道有沒有人了解政府推行的勞資會議？
- 推薦 Blind App (Blind: Your Anonymous Workplace Community)
    - https://www.teamblind.com/articles/Topics
- 抗爭、遊行能不能改成坐下來做教育？
- 監察院 CSV 政治獻金資料整備中，預計六月初（或之前）上線（au）
- 沖繩黑客松
- 雨蒼
https://hackmd.io/s/rk_iMtN9E?fbclid=IwAR2E8QaXdyM7Hf1T9aMacDsTotvjNy42kfiGICAhjKw6j3ncaBkM8FyN5d0

todo（想在小松完成的事情）
---
- 想要證明「被中國統一」是非常糟糕的，要來給長輩看
    - https://hackmd.io/s/HkjidY4cV
    - 新疆集中營
    - 西藏被血洗
    - 香港特首被指派，無法民選。被迫一國無兩制。
    - 低端人口被驅逐
    - 

vtaiwan基金餘額
---
* 本日花費: 0 元
* 本日現場贊助:
    * Pizza: 科法所 655元（仔魚墊付）
    * 台啤18天 2手: Ronny 多少錢忘了，反正我自己喝了一手
* 捐款: 匿名 200 + 100 
* 餘額: 1718元