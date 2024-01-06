---
title: "除媒計畫相關進度 2014.07"
tags: hackpad
---

# 除媒計畫相關進度 2014.07

> [點此觀看原始內容](https://g0v.hackpad.tw/Yzfy0Yzpc0a)


公民曆：[https://www.google.com/calendar/embed?src=ptt.publicissue%40gmail.com](https://www.google.com/calendar/embed?src=ptt.publicissue%40gmail.com)

> 請各組自主上來更新情況喔，如果太久沒動的話我會追人~~
> [name=Rhozan]

> 大家不要覺得太緊迫, 保持了解彼此進度 互相激勵
> [name=Wilber C]

> feel free to share your progress and if any question contact anyone who you prefer
> [name=Wilber C]

> 如果不知道怎打的話, 可以參照我的格式, 
> [name=Wilber C]

> to-do list 就是列下計劃目標(1-2周) , 用checkbox(可打勾框框) 完成了就打勾
> [name=Wilber C]

> 已完成的可以用Done list 列出完成哪些, 加上說明
> [name=Wilber C]

> 謝謝! 這邊就~內部~用這樣，不用太正式
> [name=Rhozan]

### g0v 方面

    7/8新增了我們專案"全民除黴計畫" 在g0v 專案列表中, 大家可以在 [http://](http://hack.g0v.tw/projects)  [hack.g0v.tw/project](http://hack.g0v.tw/projects) 看到, 不過他的專案新增方式不太完整, 導致我新增好了都不知道成功, 而新增的資訊有點不完整, 後來在github的g0v.json補上完整資訊, 也還是沒有即時更新, 這部分有空再請教g0v內部成員...

### 後端Server

- Done(until 7/1)
    - 主機
        - 感謝麥克提供虛擬主機, 不過該主機有許多操作＋環境限制, 規劃APP4AM自己開新的AWS免費虛擬機先試run (一年免費,有流量 硬碟 cpu速度限制)
        - crawler server 還在努力, 聯繫上Newsdiff 榮尼王, 在請教中
- To do (until 7/6)
    - [x] 架設好aws+mongo+crawler
        - 架設好aws server, crawler 努力中(7/5)
        - AWS Server上已經開始定時抓自由新聞, 其他媒體的還沒測好, 會再陸續放上去(˙7/21)
        - 再者長時間跑下來有甚麼問題再觀察結果, 希望爬新聞程式在下次meeting前完成(7/21)
        - 跟News diffs榮尼王討教後,發現一些正規化問題要處理,crawler 程式還要再補強, (就是說完成時間還會往後延) (˙7/22)
        - Crawler 架構修改, 因為加入apple news的crawler, 發現各家新聞架構差異化有點大, 主要是把一些爬蟲參數從DB移到Code裡面, 然後把爬蟲功能再模組化適應各家新聞的差異化(7/27)
        - Crawler架構改好也加入了蘋果新聞的爬蟲功能, server正在抓蘋果網站的新聞了, 並持續進行coding 聯合+中時(˙7/30)
        - 增加udn 聯合新聞網Crawler , , 並持續進行coding 中時(˙8/2)
        - 已完成4家媒體的crawler ,也正常執行中, 不過現在的crawler有個問題, 沒辦法執行完就完全關閉, 導致占用server資源, debug中(問題出在平行處理上) (8/10)
        - 修改Crawler , 保留新聞文章的原始分段HTML Tag符號, 免得抓到存文字還得人工分段(10/3)
    - [ ] 進行新聞網址單一正規化作業
        - 這項工作是因為跟榮尼王討論過才發現同一篇新聞可以有不同網址可以連到, 所以在NewsDiff有做網址正規化, 不過要搞清楚各家新聞獨一網址的規則, 得一筆一筆人力去檢視, 等我把基礎四大家的Crawler寫好, 會請教榮尼王他找到的規則 , 並且進行正規化工程(7/30)
    - [x] 建好Mongo schema
        - 已建好News, Topic, Comment,  user accout schema 尚在規劃
        - 帳號系統基本上採用原Meteor內建的[http://docs.meteor.com/](http://docs.meteor.com/#meteor_users)[#meteor_users](https://g0v.hackpad.tw/ep/search/?q=%23meteor_users&via=Yzfy0Yzpc0a)
    - [x] 找大嘴討論前端議題分類(after mongo schema)
        - 7/4晚上跟大嘴共同討論過了
        - 已經訂好database schema, 相關資料在google drive/app project/database/schema.ppt
        - 後台讓新聞組分類介面已規劃好, 進行中
> 這邊在等待新聞資料，資料到位後一天內完成
> [name=mrbigmouth]

> 預計這周末會放上Crawler 開始抓資料測試
> [name=Wilber C]

> 7/14 進度有點delay, 因為臨時出了些bug卡住, 然後想搞清楚就花了點時間, 所以還沒上server去測試跑
> [name=Wilber C]

> 現在進度是可以抓 自由時報 網站, 其他媒體網站還沒測過
> [name=Wilber C]

> 因為用了平行處理跑Crawler, 有一些資料格式和連線錯誤要特別處理這周花了點時間去設計方法
> [name=Wilber C]

> 7/21 能長期跑的爬蟲程式, 還不穩定, 現在只有在主機上跑一次放幾天的新聞資料讓大嘴可以試著做前端
> [name=Wilber C]

> 繼續努力破關
> [name=Wilber C]

> 簡陋的後臺分類介面已完成，歡迎提改善建議
> [name=mrbigmouth]

> [http://ec2-54-92-40-63.ap-northeast-1.compute.amazonaws.com:3000/](http://ec2-54-92-40-63.ap-northeast-1.compute.amazonaws.com:3000/)
> [name=mrbigmouth]


### 規劃部份

- Done
    - 7/1 已找s5y釐清app相關設計流程及要點，之後同步產製評價系統流程及介面操作流程
    - 7/1 和同事的朋友iOS工程師聊聊，她對社運議題app有興趣，不過目前沒工作有可能先搞定再說
    - 7/5 霸道的定好了長久未決的app名稱
    - 7/6 初步和Wilber討論了團隊未來方向與域名相關事項，留待下次會議進一步報告與討論( 等開放授權確定後申請g0v網域，麻煩技術小組討論)
    - 7/6 名片用插畫上週拜託插畫家 [謝東霖](https://www.facebook.com/HsiehTungLin) 幫忙繪製，成品在此，幫他按個讚吧！[http://goo.gl/0kpFxd](http://goo.gl/0kpFxd)
- Running
    - 確認名片細節、UI/UX操作流程(進度緩慢，這禮拜假日會盡量衝)
- To do (7/6)
    - [ ] 寫評價流程 (系統端、使用者端、評論員端)
        - [x] 架構
        - [ ] 統計需要欄位
        - [ ] UI/UX評估
        - [x] 顯示方式 (區域、格式)
        - [ ] 數據計算概念
    - [ ] 以上確認沒大問題後更新UI並持續做細部優化
    - [ ] 設計名片
        - [ ] 確認資訊
        - [ ] 排版設計(背面完成,正面還沒)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_3c6732f66cf5c4d086f316d1ed05f7cb)
        - [ ] 定搞
        - [ ] 送印 (沒意外應該會給卡之屋印)
- TBD&Pending
    - [ ] 和一線記者合作的相關事宜，評估目前機制還沒完整，未免多次麻煩人家，故先暫緩

### 現有APP改善

- To do (7/6)
    - [ ] 開發環境改版成android studio。
    - [ ] 導入gson，加上部分mock data。
    - [ ] 修改目前版本，讓畫面接近6/28開會的樣貌。
> 我找不到圖檔放哪！
> [name=s5y]

> 路徑是： 0.成員、開會、進度\\第二次除黴會議 0628\
> [name=Rhozan]

- To do (7/13)
    - [ ] 版本更新提醒機制。

### APP改版方向

- 希望能改成[Cordova](http://cordova.apache.org/)，減少平台間移植的麻煩。
> JavaScript不喜歡我，歡迎推人填坑。
> [name=s5y]

> 這我試看看好了，有人能把現有的UI設計或是程式給我嗎?(我不要原始碼 XD)
> [name=mrbigmouth]

> 我把比較新的試做都放在 \\UIUX Design\\UI Mockup\ 了，不過昨天跟S5Y的討論結果應該會有些修正，之後會用hackpad編輯模式UI概念套用在有評論的單頁新聞上，主頁(News List)的設計修正還要等評價系統流程再確認  (你是要現在就先玩看看Cordova嗎?)
> [name=Rhozan]

> 現在正在研究沒錯，不過如果UI未定就還不急，我先來研究直接把meteor前端套到cordova上。
> [name=mrbigmouth]

### 市調

題目出來放上臉書了
### 評論員

目前沒音訊 可能有勞各位提供點子
有想過找前新聞局長姚文智
> 管中祥也是媒觀董事~~感覺這個圈子的知名學者都身兼多職，本身滿忙的@@
> [name=Rhozan]




