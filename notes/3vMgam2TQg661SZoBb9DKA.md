---
title: Shoutout
tags: web3, shoutout
---

# Shoutout bot 開發


## github
https://github.com/girofu/Epic-slack-app


## 後端與資料庫問題
我一開始和Noah提出這個需求是兩個，一個是需要有更資深的人可以給予我意見或是review我的code，因為我是去年開始自學程式，還沒有太多的實際經驗，所以現在的程式架構就是自己摸索出來的，需要有人來幫我精進架構或是給予意見。另一個是想找一起做的人，我想這個就是另外的需求了～

所以就聚焦在第一個需求，目前遇到的不是太實際遇到的功能問題，反而是架構上的問題：
1. server架構問題
目前是直接將程式與資料全部上傳到heroku server，我讓程式每10分鐘自動執行，但是這樣我無法檢查上面新的資料，是否有更好的做法？
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4319fa0b8f0baa735331e5cfa8d7477a.png)
2. 產生中間文件的流程
如上圖，目前會產生許多的中間文件，然後再擷取彙整成一份資料，是否有更好的流程想法？
3. 如何去檢查或是知道每步驟產出的資料是什麼
因為常常在處理資料的過程中，會不知道資料處理到什麼程度，有沒有什麼工具可以更具現化的讓資料的處理過程一步一步的呈現出來

## issue
1. 讓程式發生錯誤的時候，不會輸出空白檔覆蓋掉原本的輸出檔案
2. userListWithRawEpic.json 到 userListWithEpic.json 之間，沒辦法再一次執行程式中就完成，都要執行兩次才會產生新的userListWithEpic.json
3. 目前在過濾已經篩選過的訊息的方式是建立tsSelectedJson.json 這個文件，只要有被選入的ts就不再進行篩選，但是如果有人去編輯過去的訊息，會導致因為這個訊息已經被篩選過，而不會去篩選？或是編輯過的訊息會有新的ts所以沒問題？
4. 編輯過後的shoutout發文，會被聽取事件的功能重複聽取而作出反應
5. 要把資料的部分與執行程式的部分分開存放的不同server

## To-do list

- [x] 新增thread_ts for link
- [x] 篩掉重跑userSelectedConversation002
- [ ] conversationSelected的tsSelected需要確認是否需要修改
- [ ] ==編輯對話後的重複發送bot conversation==
- [x] modifyEpic的方式確認
- [x] 修改api
- [x] 新增thread_ts欄位在userSelectedConversation002
- [x] gif api
- [ ] shoutout bot 首頁
- [x] shoutout bot 按鈕連結更新
- [x] shoutout bot 大頭貼
- [ ] 新增網站上的shoutout連結原訊息
- [ ] 自己可以看到自己發出的shoutout的總結
- [x] ==4/1 以後沒有抓到 shoutout==
- [x] ==shoutout 中有名字消失的問題==
- [x] ==更改api中的channel name and user name==
- [x] 網站上shoutout照時間排列

## 接下來想做的功能
- 後端：
    - 送出與收到的SO紀錄，包含時間、地點（例如slack, discord, hackmd…）、場合（線下活動例如大松、線上活動例如da0-learning）可做到
    - 承上，同時結合POAP或是NFT增強其共有感或是紀錄的強度 -> 未做過，技術上可能有難度
    - 承 a. ，特定場合專用連結，從這個連結進去所發送的SO可以證明是在這個場合中發送的 -> 未做過，技術上可行
- 資料庫：
統一的資料庫，讓未來所有人在不同平台使用的SO能夠互通且取得資料，是否使用分散式仍需要考量 -> 未做過，技術上可能有難度
- 儀表板：
    - 呈現獲得與送出SO的趨勢、來自誰的SO數量排序、與其他人的SO的網狀連結，並且可以有選單的方式篩選顯示 a. 中的各種類資訊 -> 適合前端製作
    - ==slack內儀表板，在app首頁的顯示功能更新==
    - ==每週推送關於本週的SO整理消息==
- 可操作介面：slack內的選項，可能包括以下項目：
    - ==選擇gif的種類==
    - ==選擇自己送出shoutout時是否同時傳到頻道內==
    - ==做出可填寫的shoutout modals，這樣就可以同時包含以上功能(https://api.slack.com/surfaces/modals)==
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_dffedc4b99b512fcf5b8c0f004a51d98.png)

- 連結：
與其他真人帳戶連結的方式，利用gitcoin passport -> 未做過
- 插件：
    - 讓不同的網站插入使用的方式 -> 未做過，技術上可能有難度
    - app上架，讓slack, discord等其他軟體的其他社群可以使用 -> 未做過，技術上可行
- 開源：
讓其他人可以來完善功能或是開發屬於他們的fork -> 可做到


## 時程

* 5/12 現有bug修正，包含使用者編輯後會重複發文，以及有看到SO包含到bot發送的訊息
* 5/16 database工具選擇確定
* 5/20 開始建立database
* 5/20 收集shoutout方式變更有兩種可行方式：
    * 改為使用slack內可操作的介面，可能會轉為使用modals讓使用者來輸入shoutout https://api.slack.com/surfaces/modals
    * 只抓mention bot的訊息內容
* 5/31 database建立完成
* 6/07 建立操作手冊
* 6/10 開放給其他坑來使用


## changelog
- 4/14 
    - 改變bot回覆的連結，將社群功德值去掉
- 5/15
    - 修改編輯之後會重複發文的bug (本地server可執行，雲端server遇到問題仍未解決)
    - 修改會抓到SOB會抓到自己發文的bug
    - SO計算有誤的問題目前不知道底層原因，推測是因為只抓7天的訊息，但是每次執行功能都只會依照最早deploy上去的資料版本進行更新，因此超過7天之後就會開始漏掉SO。暫時的解決方法先把更新訊息設定為90天份量的訊息，暫時不會有訊息漏掉的問題，實際解決問題我認為直接建制database會比較適合
    - databse部分，redis and azure cache for redis設定完成，接下來要將過去的資料放進去，並且修改未來之後抓取SO的邏輯，利用mention bot直接將訊息送進資料庫


---
## 後臺抓的api
shoutout的資料格式更新好了，包含以下：
text: 原本的shoutout
user: 這句shoutout來自誰
ts: 這句shoutout發出的timestamp
channel: 這個shoutout出現在哪個channel
(https://i.imgur.com/NksxNUq.png)

**還可以考慮抓:** emoji、url?

---

# SO PAGE
- [5/23會議列出SOP項目](https://g0v.hackmd.io/@noahyeh/HyPnZQqrn)
- [SOB & SO Page Spec](https://hackmd.io/Itq-jpxCS8qB9xqyK4mv0Q?view)



# 豆腐UI
==**豆腐的儀表板：考慮把 dashboard 跟shoutout 分成兩個頁面？**==
![](https://i.imgur.com/1fjwJjV.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c9dc040607876b75b250a6a46817f67c.png)

* 尚待排時程

###### tags: `web3` `shoutout`
