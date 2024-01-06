---
title: "立院看門狗"
tags: hackpad
---

# 立院看門狗

> [點此觀看原始內容](https://g0v.hackpad.tw/r7bWv19xZYE)


> 接續[Jimmy Huang](https://g0v.hackpad.com/ep/profile/EcUrTWSKroj)在g0v-ly的立院訂閱器
> [name=TYLo]

- 發起人/拋磚人：[TYLo](https://g0v.hackpad.com/ep/profile/ENS06ylFWb8)
- **狀態**：
    - 目前事件/法條對應API完成
    - 8/10 完成polling機制，utilities
    - 前端卡在認證，需要熟OAuth機制的人指導
> 之前類似專案: [https://g0v.neticrm.tw](https://g0v.neticrm.tw)
> [name=TYLo]

- **訂閱對象：**
    - [x] 會議預報
    - [ ] 會議議程
    - [ ] 委員發言
    - [ ] 委員書面質詢、行政院回覆
    - [ ] 法案進度
- 簡介：連結gmail帳號 or Facebook帳號透過API發帳號透過API發送訊息
- 實現邏輯：
    - 訂閱
        - 使用者填入關鍵字(可以是事件/法條)直接訂閱。
        - 如果填入事件，能夠自動產生相對應法條(由一個月內新聞抽取)。
        - 可以選擇FB或是mail方式收到訊息
    - 發送
        - 以polling方式取得新的公報/議程，就觸發notify機制，發送email與Facebook通知。email發送使用gmail API，FB還需要寫APP。
- 資料來源:
    - 立法院(官方)：[http://www.ly.gov.tw/01\_lyinfo/0109\_meeting/meetingList.action](http://www.ly.gov.tw/01_lyinfo/0109_meeting/meetingList.action)
    - 預報api：[https://groups.google.com/forum/?hl=zh-TW#!topic/g0v-ly/VDaUzk9GJRI](https://groups.google.com/forum/?hl=zh-TW#!topic/g0v-ly/VDaUzk9GJRI)
    - 法令列表：[https://github.com/g0v/laweasyread-data](https://github.com/g0v/laweasyread-data)
- hackfolder：[http://hack.g0v.tw/ly-watchdog/r7bWv19xZYE](http://hack.g0v.tw/ly-watchdog/r7bWv19xZYE)
- github：[https://github.com/sweslo17/ly-watchdog](https://github.com/sweslo17/ly-watchdog)
- 目前完成：
    - 事件<==>法條對應api(example)：[http://gaisq.cs.ccu.edu.tw:9999/query?term=洪仲丘](http://gaisq.cs.ccu.edu.tw:9999/query?term=洪仲丘)
    - **系統架構**
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_818dd7cd1724f5f0f5a57c932d9526a7)
    - **Mockup**
![](https://dl.dropboxusercontent.com/u/14253954/ly-watchdog_mockup.png)
- 短期目標：
    - 完成介面、能夠對預報做訂閱。
- 支線任務：
    國會圖書館 立法院智庫 (npl)
    - 一大堆彼此稍微重疊的系統 (tts): [http://npl.ly.gov.tw/do/www/homePage](http://npl.ly.gov.tw/do/www/homePage)
        - 可以使用 [ly-crx extension](https://github.com/g0v/ly-crx) ([安裝](https://chrome.google.com/webstore/detail/%E7%AB%8B%E6%B3%95%E9%99%A2%E6%93%B4%E5%85%85/ingofalhkimajgdgaplblnkhpenjhmpo?hl=en)), 會增加一個 download-all 的 link
            - [ ] 需要一個 cli script 直接 download (該系統無 cookie, 所有 state 都是 serialize在 post request 中, 而且 form encoding 為 big5)
        - encoding: big5-2003 (iconv -f big5-2003 -t utf-8)
        - 然後用 [https://github.com/g0v/twlyparser/blob/master/parse-tts.ls](https://github.com/g0v/twlyparser/blob/master/parse-tts.ls) 做初步理處理產生 json
    - 主要有三部分：
        - 議案系統 (motions) 包含法律提案跟其他提案
        - 質詢系統 (書面+口頭)
        - 法律提案系統 (bill) [http://lis.ly.gov.tw/lgcgi/ttsweb?@0:0:1:lgmempropg08](http://lis.ly.gov.tw/lgcgi/ttsweb?@0:0:1:lgmempropg08)
            - [ ] 希望能 decode 「提案影像」link 那串 hex 的意義，以便能直接 link
            - 例如 [https://dl.dropboxusercontent.com/u/30657009/ly/08-bills.json](https://dl.dropboxusercontent.com/u/30657009/ly/08-bills.json) 中 [http://lis.ly.gov.tw/lgcgi/lgmeetimage?cfc7cfcccecdc8cdc5cccccad2cccbcf](http://lis.ly.gov.tw/lgcgi/lgmeetimage?cfc7cfcccecdc8cdc5cccccad2cccbcf) 為 08屆03期12次 議事日程 Page 0335-0340「1559政14576」
            - 這邊的進度其實就是前項議案系統的 query. 這兩個系統的「系統號」並非通用，所以必須用「提案代號」去查詢。
            - json: [https://docs.google.com/folder/d/0By7Ba0S6YJxNUS1ySG9kczdPTDA/edit?usp=sharing](https://docs.google.com/folder/d/0By7Ba0S6YJxNUS1ySG9kczdPTDA/edit?usp=sharing)
            - simple api: [http://twdata.cloudfoundry.com](http://twdata.cloudfoundry.com) (broken?)
            - TODO: dashboard
協作者:
[TYLo](https://g0v.hackpad.tw/ep/profile/ENS06ylFWb8),[Terces Tsai](https://g0v.hackpad.tw/ep/profile/xrSLRdDkACP)
- [x] NeedsTech: 需要技術支援：目前使用polling機制。需要FB app，mail module
> 如果預報的話，其實不適合使用公報當 source，因為會晚兩三週
> [name=Chia-liang K]

> 要不要參考一下 [github hook PSHB api](http://developer.github.com/v3/repos/hooks/#pubsubhubbub) 設計一下 subscribe api, 然後看如何在 api.ly.g0v.tw implement 這個部分？
> [name=Chia-liang K]

> 這裡有筆誤，其實是以立院預報為source，公報為法案追蹤部份，應該之後會追加
> [name=TYLo]

- [x] NeedsWriter: 需要文案幫手（撰寫提示訊息、Email的訊息範本）
- [x] NeedsDiscuss:
- [x] NeedsTest: 訂閱、發送流程需要測試

