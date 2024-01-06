---
title: 違章工廠舉報系統第18次小聚
tags: Disfactory, 違章工廠, 違章工廠舉報系統
---

# 違章工廠舉報系統第18次小聚

時間：2020/02/12 (三)
地點：地球公民基金會北辦
線上：https://zoom.us/j/650776487

## 參與者簽到：
- simon
- Aaron(鉦寰
- 小海
- 小胖
- 沅諭
- 佳昇
- 小班
- yukai
- yellowsoar
## 待討論

小海目前想到要討論的

* 使用者

使用者推廣：佳昇
政府面：小胖，跟縣市政府喊話、舉報
記者會：小海
法律、公文：環境權基金會（環境行政權訴訟）

* 網站完備上線
似乎網站還有一些部分未完成和希望更優化
1. 使用教學
2. 必填/選填辨別
3. 資料授權與使用者條款 (海)
4. 另外有一個網頁介紹本網站(海) => 用連結連到一頁式網站/HackMD/地公網站開新的一頁
5. Disfactory[簡介Blog文](https://g0v.hackmd.io/56e4eML7QyGo43u0Lg0nWg)（設定[HackMD筆記權限](https://hackmd.io/s/how-to-set-permissions-tw)）
6. 理論上第一批使用者可以回饋更多，讓網站整體給大眾時可以更完整

* 使用資料
等第一批使用者輸入的資料進來（這會回圈到第一題使用者）
CET需要何種資料如何提取呢

小班目前想要做的：

* 記者會期程（不確定疫情會影響多大）
火大米記者會：跟著國會開議的時間（2/25?） => push 公告母法
母法公告 => 違章工廠舉報記者會（3 月初）。母法公告後，政府就必須去拆。可能大眾不會知道，但是當地團體會知道。
* 推廣當地團體使用的進度與需要配合的資料和功能（需要有人去收集使用者反饋）
* 下次開發要走的方向：
3. 確認期程、分工（新的研究員 on board）
4. Review all existing issues and user feedback
5. 確認 deploy 方式 
    6. 前端 CI/CD 到 dev.disfactory.tw, production 那條 branch merge 時才會上正式版
    7. 後端需要人工手動 deploy， issue #203 middle2 keyholder: 要先 hard fix 到 Middle2.....
7. 聽小胖和使用者的回饋
8. 決定 3/1 記者會前要更新的項目：主要是回報介面優化
    - 使用者 feedback 	
    - new pop-up 	
    - log record 
    - csv 給地球公民
    - 撤掉誤報工廠的 procedure
9. 6/1 前要更新的項目：
可以給地球公民基金會操作的後台


## 會議記錄

盤點建置文件順序
* Page 資料授權＋使用者條款
小海跟CET法務溝通
* Page QA（使用者想知道的） about.disfactory.tw
小海＋佳昇準備文字內容
    - 這個網站要做什麼？
    - 我該如何使用（影片）
    - 有問題要怎麼聯絡（e.g. 網站壞掉、住家被誤報為工廠）
    - 想要參與更多可以去？
    - 我要怎麼追蹤舉報的成效？
    - 為何需要大家舉報（法規及CET倡議方式）
    - 個人資料會如何被使用
    - [ ] landing page 要架在哪裡？用什麼模板
    https://makeweb.io/
    https://cofacts.g0v.tw/
    
    
* HackMD 大廳文件（開源社群需要的）beta.hackfoldr.org/Disfactory
    - 我們是誰、要做什麼｜這個系統為何存在
    - 網站連結
    - 使用教學｜我該如何回報違章工廠
    - 小聚紀錄｜會議記錄
    - 技術討論｜Github、開發文件、資料來源、設計圖檔、開發筆記部落格（？）



    - [x] 要把 etherspreadsheet 改成 Google Spreadsheet 鎖權限 


遠端開會： ZOOM ＋ HackMD +sharedscreen


談論匿名社群性，也許可以對工廠鼓掌/拍手 => 知道熱區

### 期程
2/12 完備文件資料
2/20 核心使用者接觸：
    * 曾舉報：給誘因（呼籲3/20公告後可實質拆除）
    * 新鮮人：全新體驗檢視系統（以小旅行模式）
2/28 第一波開始使用
3/20 記者會 v1.2

環權會想要做電話舉報、法律訴訟
可以再討論一下 => 也許需要可以輸入 spreadsheet 的介面


接下來要做 utm 設定

研究員
小胖統籌
佳昇會負責跟 g0v 溝通
源諭處理與公部門往返

1.1 解目前的bug
1.2 核心使用者回饋後，解bug
2.0 公開推廣

### 待討論事項：

- 倡議推廣期程
- 使用者回饋：最近一個月該如何收集使用者回饋改善開發介面？
- review all issues
- 訂立 3 - 6 月 milestones
- 分工合作方式
    - 小聚頻率
    - 線上小聚可能性
    - 需要 recruit 新的人手嗎？


## 下次待討論事項

-


## 相關資料：

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_016bc54c72469eb321187fe66d193b28)



GA 分析：過去兩個禮拜適用的人數很少噢，甚至只有非常少數的人有成功新增工廠。（因為過年測試使用到測試網址，這是兩個網址相加的結果）

前面的人次應該是我們自己測試的
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_69ffe33787ad8f3b8c2f903151ab75d2)

只有 18 人次新增工廠
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_069edeae237d5ddb6aafb5ab9e725772)

給設計師和工程師參考的數字：
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_500adefc6e255304de30df8e4c6af912)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0cae90e81ec0aca1dde49ac2ab40addf)


複習一下環境設定: https://g0v.hackmd.io/@yukaii/r1r-zFEKS


